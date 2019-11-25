## 주제: 웅진 COWAY

AWS IoT Core를 처음 접했을 때에도 웅진 코웨이가 AWS IoT Core를 사용하는 가장 대표적인 기업이라고 들었습니다.
IoT Core 와 Amazon Kinesis 를 사용하여 효율적인 관리 시스템을 만들었는데, 이 점이 눈에 들어왔습니다.
[https://aws.amazon.com/ko/solutions/case-studies/coway/]

### 기존 문제점
- 글로벌 서비스 확장 대응
- 비용 효율화 추진 
- 개발 리소스 부족 (단기간 개발 인력 확보 어려움)
- 기존 제품 지원 유지 필요
- 제품 H/W Spec 이슈

### AWS 활용부분
[https://www.slideshare.net/awskorea/io-t-customer-case-in-manufacturing-joonhyung-kim]
[https://www.slideshare.net/awskorea/io-t-projectcowayfinal]

- 기존 TCP 기반 연결 제품 유지를 위해 Gateway 유지(EC2로 TCP 연결 후 MQTT연결)
- 신규 제품 MQTT연결
- Kinesis 통해 N:1 형태의 메세지 처리
- Kinesis 예외처리 및 디버깅용 데이터 수집 
- 서버에서 디비 연결시 Lambda의 stateless 특성으로 인해 Connection Pooling 불가 "RDBMS"최대 연결 갯수 초과 => DynamoDB 활용, 큐의 활용

### 만약 구현해본다면?
사실 data를 직접 수집하기는 불가능하다. 
불과 몇달전만 해도 IoT에 관심이 100중 90이었는데, 여러가지 이유로 웹개발자를 해야겠다고 느꼈다. 그래서 일단 기회가 된다면 수집한 혹은 가상의 data를 사용자가 쉽게 웹을 통해 접근할 수 있는 간단한 웹 서비스를 만들어보고 싶다. 
현재 웹 개발 입문자여서 모르는게 많지만 AWS서비스를 활용하여 만들어보고 싶다.(Amazon DynamoDB, Amazon IoTCore, Amazon SNS 등 사용)