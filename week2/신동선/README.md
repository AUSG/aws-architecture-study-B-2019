# 2019 AWS Architecture Study B Group

### 2주차

## CloudWatch

EC2 인스턴스: CPU 사용률, 데이터 전송량, 디스크 사용량 등을 모니터링할 수 있다. 
측정치와 연계하여 알림(Notification), 자동 횡적 확장(Auto Scaling), EC2 인스턴스 제어 액션을 사용할 수 있다.
실제로 EC2 인스턴스를 모니터링 해본 결과이다. 인스턴스를 선택하여 모니터링할 수 있었다.

![image](https://user-images.githubusercontent.com/52663248/68109229-52d7db00-ff2d-11e9-9758-6a6e183f6c4e.png)

## S3

S3는 인터넷 스토리지 서비스이다. 용량에 관계 없이 파일을 저장할 수 있고 웹(HTTP 프로토콜)에서 파일에 접근할 수 있다.
S3는 무제한 저장소라고 처음에 배웠던 기억이 난다.
각 객체에 대해 객체URL을 제공한다. 

## CloudFront

CloudFront는 전 세계에 파일을 빠른 속도로 배포하는 CDN 서비스이다.
EC2나 S3의 데이터에 접근을 했을 때 CloudFront 서비스를 사용하지 않는다면 해당 리전에서 데이터를 직접 가져오므로 해당 리전이 멀리 떨어져 있다면 아무래도 비교적 지연 시간이 있을 수 밖에 없다.
CloudFront는 오리진 서버에 위치한 원본 파일을 전세계에 위치한 edge 로케이션으로 배포하고 edge 로케이션은 이 데이터를 캐싱하며 사용자는 자신의 위치와 가까운 에지 로케이션에서 캐싱된 데이터를 제공 받으므로 지연 시간을 줄일 수 있다.

## RDS

현재 Amazon Aurora에서도 사용 가능
이점: 관리 용이성, 뛰어난 확장성, 가용성 및 내구성, 빠른 속도, 보안, 저렴한 비용

## DynamoDB

DynamoDB는 리전별로 생성할 수 있으며 성능과 가용성을 위해 데이터를 3곳의 가용 영역AZ에 복제하여 저장한다.
가용 영역이 장애가 발생하여 정지하더라도 DB를 정상적으로 사용할 수가 있다. 
학교에서 RDBMS를 배우고있는데, DynamoDB는 nosql이지만 partition key가 존재한다고 한다.
하지만 내부 동작 방식이 달라, row들의 유일한 값(RDBMS의 primary key 처럼)을 지정하는데 쓰이기도 한다.
RDBMS에서도 partitioning이라는 기능이 있지만 DynamoDB에서 partition key는 공식 문서 best practice(Uniformity 가 Good인 부분의 사례)에서 언급했다 시피 RDBMS의 primary key같은 유일한 값을 partition key로 설정해도 괜찮다고 한다.
(출처: https://velog.io/@drakejin/DynamoDB%EC%97%90-%EB%8C%80%ED%95%B4%EC%84%9C-%EC%95%8C%EC%95%84%EB%B3%B4%EC%9E%90-1)

## ElastiCache

ElastiCache는 분산 인 메모리 캐시In-Memory Cache를 손쉽게 생성하고 확장할 수 있는 서비스이다.
읽기 중심의 서비스(소셜 네트워크, 게임, 추천 엔진 등)를 제공해야 하는 환경, 고속으로 데이터를 분석해야 하는 환경에 적합하다. 
데이터베이스의 부하를 줄이고자 할 때, 대용량 분산 캐시 환경을 자체적으로 운영하기에는 부담이 있을 때 유용하다.
인 메모리 캐시는 모든 데이터를 메모리(RAM)에만 올려놓고 사용하는 데이터베이스의 일종이다.
