# NoSQL 테이블 생성 및 쿼리
## AWS CLI를 통한 Dynamo DB 접근 및 쿼리

1. 테이블 생성하기
![](&&&SFLOCALFILEPATH&&&create-select-nosql1.632300f6c11874ff2d8285f424722d855b14fd7a.png)
([NoSQL 테이블을 생성 및 쿼리하는 방법 – AWS](https://aws.amazon.com/ko/getting-started/tutorials/create-nosql-table/?trk=gs_card))에서 테이블 생성하는 법 참고

해당 튜토리얼은 AWS 콘솔에서 작업하는 법을 다루었기 때문에, awscli로 작업하는 방법을 다루도록 하려고 한다.

2. aws-cli 설치 
`pip3 install awscli --upgrade --user`

3. IAM 사용자 생성
![](&&&SFLOCALFILEPATH&&&%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202019-10-07%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%204.37.05.png)
![](&&&SFLOCALFILEPATH&&&%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202019-10-07%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%204.37.35.png)

DynamoDB의 권한을 허용하고(편의상 모두 허용), 추후 데이터 파이프라인을 사용하기 위해 DataPipeline 권한들을 허용하여 사용자를 만든다.

4. `aws configure`
위에서 생성된 Access key, Secret Access Key, Region name, output name으로 알맞게 설정해준다.

5. 생성한 테이블에 데이터 한 번에 추가하기
`aws dynamodb batch-write-item --request-items file://music.json`

::<awscli로 DynamoDB를 조작하는 명령어>::
::* aws dynamodb create-table : 테이블 생성::
::* aws dynamodb describe-table : 테이블 조회::
::* aws dynamodb put-item : 데이터 추가::
::* aws dynamodb get-item : 데이터 조회::
::* aws dynamodb update-item : 데이터 수정::
::* aws dynamodb delete-item : 데이터 삭제::
::* aws dynamodb batch-write-item : 여러 데이터 추가/삭제::
::* aws dynamodb query : 데이터 쿼리::
::* aws dynamodb scan : 데이터 스캔::
::* aws dynamodb delete-table : 테이블 제거::

![](&&&SFLOCALFILEPATH&&&%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202019-10-07%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%205.11.12.png)


6. 추가한 데이터 조회하기
`aws dynamodb scan`

![](&&&SFLOCALFILEPATH&&&%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202019-10-07%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%205.11.55.png)


- - - -
## 총평
콘솔로 작업하는 것보다 cli를 사용하는 것을 선호하는 편이라 10분 자습서를 그대로 따라하지는 않았지만, 처음 DB를 작업한다면 눈으로 볼 수 있는 콘솔 작업도 좋을 것 같다.
하지만 콘솔로 작업하려면 데이터를 하나하나 추가해야된다는 불편함이 있다.