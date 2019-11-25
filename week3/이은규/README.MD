## 주제: Toss Lab(JANDI)

### 당면 과제

- 서비스 운영의 안전과 신속
- 메시지와 파일을 서비스에 업로드할 때 여러 사용자가 동시에 공유하고 액세스 가능
- 사용자가 특정 채팅룸에 참여할 때 채팅 룸의 이전 메시지와 파일에 엑세스 가능

### AWS 선택 이유

- 편의성과 안정성
  - 전 세계 여러 국가, 지역에서 액세스 해야하기 대문에 다수의 글로벌 SaaS 참조가 있는 AWS 적합
  - 연중 무휴, 합리적 비용
  - Auto Scaling, 다양한 스토리지 및 해외 서비스를 위한 인프라 구축에 필요한 Content Distribution을 고려

### AWS 활용 부분

1. ELB와 ALB를 함께 사용하여 대규모 트래픽을 처리

2. EC2 인스턴스에 자동으로 분산

3. 고객이 업로드한 파일은 S3에 저장되며 CDN 서비스 활용을 위해 S3에 연결되고, 컨텐츠 전송 속도 향상을 위해 CloudFront 사용

4. 메신저 특성 상 특정 이벤트나 문제 발생했을 때 트래픽이 급증하기 때문에 인스턴스의 자동 확장 기능이 필요하여 AutoScaling 사용하여 비용 효율성 실현

5. 메시지 창에 하이퍼링크를 입력했을 때 RSS 형식으로 미리보기 정보를 가져올때 Lambda 사용

6. 안정성, 가용성을 위해 ElastiCache for Redis에 의한 자동 장애 조치 사용

7. 확장성 보장위하여 각 할당된 서버가 SQS기반 메시징을 통해 데이터 증가 시 안정성을 개선하도록 구현

### 메시지 스트리밍 플랫폼의 전체적인 흐름

1. 사용자가 API를 통해 클라이언트를 호출한다.

2. DB에 저장, Search Engine, Socket 대화창 사용

3. 초기에는 고객의 메세지 db를 바로 저장했지만 이제 확장성 이슈에 대비하여 중간에 메시지나 사용자의 요청들을 처리하는 플랫폼을 추가

4. Kafka는 메모리 큐 저장 서비스로서 api에서 들어온 모든 트래픽을 저장하고 배포하는 서비스

5. Rabbit MQ는 DB에 저장전에 DB의 성능에 따라 장애가 나지 않도록 버퍼 역할

6. SQS는 se를 위해서 q서비스를 제공하는데 대량의 데이터가 실시간으로 들어가는 경우 indexing 실패가 나지 않도록 버퍼역할을 같이 하게 된다.

7. Connect는 JANDI에서 웹훅, 구글 캘린더, 트렐로 같은 서비스를 연동하는 서비스(서드파티를 위한)

8. Message Cache 사용

9. Auth Cache 고객이 api를 호출할 때 권한이 있어야 하는데 db에서 읽어오는건 또 시간이 걸리기 때문에 cache로 처리

<img src="https://d1.awsstatic.com/International/ko_KR/Customer%20Reference/Picture1.649c1b02e29aa7ae61a6f4b301b72aa90dffbb12.jpg">

참조:

> https://aws.amazon.com/ko/partners/success/tosslab/

> https://www.youtube.com/watch?v=IHAEz4o253A&did=ta_card&trk=ta_card

> https://d1.awsstatic.com/whitepapers/aws-web-hosting-best-practices.pdf?did=wp_card&trk=wp_card

--- 카프카 개념

> https://epicdevs.com/17

> https://tosslab.github.io/backend/2017/07/18/aws_instance_scheduler.html

> https://jack-vanlightly.com/blog/2017/12/4/rabbitmq-vs-kafka-part-1-messaging-topologies

> https://ellune.tistory.com/29
