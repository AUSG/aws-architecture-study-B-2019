## 고가용성의 표준 아키텍쳐 구축하기

<img src="./구현 희망 가상 아키텍쳐.jpeg">

### 목표:

1. 서로 다른 가용 영역에 ec2를 배치, AutoScaling
2. VPC 내부의 MongoDB 서버를 PSS 구조의 Replica Set으로 구성하고 이를 Sharded Cluster 적용
3. (희망) PSA 구조로 이루어진 Replica Set 클러스터
