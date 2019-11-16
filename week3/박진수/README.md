주로 제가 관심있는 사이트를 하면 좋지 않을까 싶었는데....

마이리얼트립, 오늘의집, 미디엄 셋 중 고민하다가

기술적인 내용은 마이리얼트립이 가장 많을 것 같아서 마이리얼트립으로 하겠습니당.

(각 서비스들의 공통된 내용은 예를 들면 이미지 리사이징, CRUD, 업로드 등등 근데 마이리얼트립은 좀 더 글로벌한 서비스이기도 하고

특가 이벤트 등을 하면 서버에 갑자기 요청이 늘어나는 경우도 있을 것 같고 하여서!)



[AWS service 정리]([https://medium.com/harrythegreat/aws-%EC%95%84%EB%A7%88%EC%A1%B4%EC%9B%B9%EC%84%9C%EB%B9%84%EC%8A%A4-overview-1-4cc3ffdd6b59](https://medium.com/harrythegreat/aws-아마존웹서비스-overview-1-4cc3ffdd6b59))를 참고함.

## 필요 기술로 생각되는 것들.

* 특가 이벤트 시 요청이 늘어나는 것 -> CloudWatch를 통한 감시, 개발팀 Slack으로 알림. Auto scaling, LoadBalancing,  ECS를 쓸 수 있을까?

* 로그를 저장할 땐 Glacier 이용.

* 사진, 영상을 업로드 할 땐 S3, 다양한 Image의 preivew를 만들어야함 -> API Gateway와 Lambda이용.

* **어떤 DB를 사용할까?**는 잘 모르겠음..

* 글로벌한 서비스이기때문에 AWS CloudFront 등의 CDN 기술이 필요할 듯.

* 도메인

myrealtrip.com,flights.myrealtrip.com 등이 존재하는데 route53을 이용하면 좋을까?

다른 호스팅에 비한 route53의 장점은?

* 1대1 채팅서비스 존재. 

* 채팅서비스에 굳이 API Gateway+Lambda 같은 다른 서비스를 이용할 필요가 있을까? 그냥 있는 서버에 router 하나만 더 달면 되지않을까? 

-> 그럼 따로 AWS 서비스 이용안해도 될듯?



## 넣고싶은 기능

AWS CodePipeline을 이용한 CI/CD를 통해 빠른 개발

메모리 캐시(Elastic Cache)->날아가도 되거나 자주 접근하는 데이터는 뭐가 있을까?

: 내가 최근 본 여행상품, 핫한 여행상품.

예약에 대한 트랜잭션? 근데 트랜잭션이 자세히 뭔지 궁금함!



## 기본적인 내용들 말고 마이리얼트립만의 특징을 살릴 AWS service가 있을까?

Global->CloudFront 밖에 떠오르지 않음...

