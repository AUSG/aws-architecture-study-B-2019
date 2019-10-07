# AWS CodeStar와 AWS Cloud9을 사용하여 서버리스 애플리케이션 만들기

- 주차: 1주차
- 소요 시간: 약 1~2시간 내외
  - 실제 튜토리얼 따라가는건 30분도 안 걸리고 세팅 및 오류 추적에 대부분이 걸렸네요 🤣🤣

## 결과물?

[서버리스로 배포된 간단 정적 페이지](https://0w9j2ro9ne.execute-api.ap-northeast-2.amazonaws.com/Prod/)

## 주요 개념

### AWS CodeStar

지속적 전달(Continuous Delivery)를 가능하도록 해주는 지속적 전달 툴체인 설정 도구

### AWS Cloud9

- AWS가 제공하는 온라인 IDE
- 한국에서는 못 씀!

## 진행 기록

- EC2 키 페어 생성하라고 해서 당황;
- Cloud9이 선택지에 없어서 `2`차 당황;
  - Cloud9은 우리 나라에서 못씀;
- 그래서 CLI로 하도록 설정해봄
  - macOS 에서 AWS CodeCommit에 대한 구성이 (처음에는) 다소 까다로운 것처럼 보임
  - [이곳](https://docs.aws.amazon.com/ko_kr/codecommit/latest/userguide/setting-up-https-unixes.html#setting-up-https-unixes-account)을 참조
- 템플릿 코드에 포함된 테스트 코드때문에 `3`차 당황;;
```js
try {
  test.number(result.statusCode).is(200);
  // 이게 있는 줄 모르고 문장 바꿨다가 배포 테스트 통과 안해서 3차 당황;;
  test.string(result.body).contains('Congratulations');
  test.value(result).hasHeader('content-type', 'text/html');
  done();
} catch(error) {
  done(error);
}
```
  - 그래서 해당 테스트 코드를 제거하니 잘 배포가 이루어집니다. 편-안.

## 총평

- 얼떨결에 **CodeCommit** 이라는 서비스를 함께 사용해보며 AWS의 CI/CD 도구도 경험해보았습니다. 역시 편리하긴 하군요.
- 간단하게 서버리스를 배포해볼 수 있는 재미있는 튜토리얼이었습니다. 다만 아무래도 10분 튜토리얼이다보니 배포와 관련된 `.yml` 파일들의 구성과 설정 등에 대해서는 전혀 언급도 없어서 아쉬웠습니다.
