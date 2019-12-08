## 고가용성의 표준 아키텍쳐 구축하기

<img src="./구현 희망 가상 아키텍쳐.jpeg">

### 목표:

1. 서로 다른 가용 영역에 ec2를 배치, AutoScaling
2. VPC 내부의 MongoDB 서버를 PSS 구조의 Replica Set으로 구성하고 이를 Sharded Cluster 적용
3. (희망) PSA 구조로 이루어진 Replica Set 클러스터

참고:

- [How to Make High Availability Web Applications on Amazon Web Services - Betsol](https://betsol.com/2018/01/how-to-make-high-availability-web-applications-on-amazon-web-services/)

- [EC2 Instance에 MongoDB 인스톨하기 | COSMIC LATTE](http://cmlatte.com/cmlatte/blog/2014/12/28/ec2-instance%EC%97%90-mongodb-%EC%9D%B8%EC%8A%A4%ED%86%A8%ED%95%98%EA%B8%B0/)
- [Deploy a MongoDB Replica Set in a DevOps fashion style (Infrastructure as Code with Terraform)](https://medium.com/@cramirez92/deploy-a-mongodb-replica-set-in-a-devops-fashion-style-infrastructre-as-code-f631d7a0ad80)
- [How to Setup Three Member Replica Set on Amazon Ec2: MongoDB](https://medium.com/@greeshu.renu/how-to-setup-three-member-replica-set-on-amazon-ec2-mongodb-60f0aaddcf32)
- [아키텍처 - AWS의 MongoDB](https://docs.aws.amazon.com/ko_kr/quickstart/latest/mongodb/architecture.html)
- [AWS 클라우드의 MongoDB: Quick Start 레퍼런스 배포 - AWS의 MongoDB](https://docs.aws.amazon.com/ko_kr/quickstart/latest/mongodb/welcome.html)
- [Install MongoDB on Amazon EC2 — MongoDB Manual](https://mongodb-documentation.readthedocs.io/en/latest/ecosystem/tutorial/install-mongodb-on-amazon-ec2.html)
- [Deploy a Highly-Available MongoDB Replica Set on AWS](https://eladnava.com/deploy-a-highly-available-mongodb-replica-set-on-aws/)
- [MongoDB Shard cluster - 아키텍처](https://sarc.io/index.php/nosql/1639-mongodb-shard-cluster)
- [설명서](https://docs.ncloud.com/ko/database/database-10-3.html)
