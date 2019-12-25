주제는 마이리얼트립의 아키텍쳐 구현이었지만,

_마이리얼트립에 특화된 서비스를 구현한다기보다는_ **다양한 AWS 서비스를 간단하게나마 이용하고 연동**시켜보는데에 초점을 맞춰보겠습니다.

## 주로 구현하고 싶은 기능

![architecture](architecture_dia.png)

* **CI/CD, 지속적 통합 및 배포 **
  AWS의 Code Deploy를 이용하면 될 것 같은데, CI/CD 에 대한 개념이나 CI 방법에 대한 부분은 미숙함. travisCI를 써보긴했는데, travisCI나 CircleCI 등을 이용해야하는지, AWS CodeCommit 을 이용하면 되는지 알아봐야할듯.
* **ELB를 이용한 load balancing 및 scaling**
  ELB를 한 번도 안 써봐서 어떤 식으로 사용하는 서비스인지 궁금함.
  aws instance scaling 도 한 번도 안 해봐서 시도해보고싶음.
* CloudFront, S3 를 이용해 신속하게 global한 정적 파일 제공
  S3를 써보긴 했는데, 그냥 간단하게만 갖다 써본 게 다라서 어떤 policy등이 있는 지도 자세히 알아보고싶긴함.

_뒷순위.._

* Lambda 와 S3 를 이용한 Image Resizing 등의 Serverless 작업.
  딱히 어렵거나 새로울 거 없을 것 같아 뒷순위
* SNS나 cloud watch를 이용한 slack으로의 알림
  전에 했던 거라 뒷 순위.



## 구현해나갈 방식

주로 CI/CD 와 ELB 사용에 초점을 맞출 것이라, 서비스 자체에 대한 구현을 자세히 하진 않을 것임.

그냥 mongoDB 이용해서 간단하게 여행상품을 보여주면서 CI/CD 작업을 통해 server의 배포 버전 별로 다르게 동작하는 것을 확인해보고, Lambda를 통해 image crop 및 resizing을 수행하는 정도.