## 2019 AWS Architecture Study B Group

### Week2

## CloudWatch

https://docs.aws.amazon.com/ko_kr/AmazonCloudWatch/latest/monitoring/AlarmThatSendsEmail.html

책의 내용 중 Period 설정 범위가 최소 1minute인데, 현재 10second 까지 가능

but 1day 이하의 간격은 전부 정확성이 떨어질 수 있다는 warning이 발생

whenever this alarm 조건을 쉽게 설명하면

period : 1 minute
is : >= 30;
for : 3 out of 3

1분 간격 동안이
세번 반복될 때
즉 3분이 지났는데 각 간격에서 설정한 측정치가 3번이상 넘겼을 때

whenever this alarm에 설정한 조건 실행

실습해볼 아키텍쳐:

https://galid1.tistory.com/369

## S3, Cloud Front

[s3 정적 웹사이트 호스팅](http://www.pyrasis.com/book/TheArtOfAmazonWebServices/Chapter11/03/03)

[s3 cloudfront 연동](http://www.pyrasis.com/book/TheArtOfAmazonWebServices/Chapter12/02)

[Invalidation으로 Cloudfront 콘텐츠 갱신](http://www.pyrasis.com/book/TheArtOfAmazonWebServices/Chapter12/05)

[s3, cloudfront 배포 과정 실습](https://react-etc.vlpt.us/08.deploy-s3.html)

배포시에
cloudfront의 origin domain 수정 필요

## RDS

책의 내용에선 mysql만이 Read Replica를 지원한다고 되어 있지만 현재 기점으로 Amazon RDS for MySQL, MariaDB, PostgreSQL 및 Oracle뿐만 아니라 Amazon Aurora에서도 사용 가능
