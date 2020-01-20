## 방향

뭘 만들지는 여전히 모르겠으나

CI/CD는 CodePipeline을 이용하기로.

ELB의 ALB를 이용.

CodePipeline으로 단순히 EC2 에 배포하기보다는

ECS와 ECR을 이용해 클러스터링을 해볼 예정

아마 ELB를 이용하면 redis를 안써도..? 알아서 자기 session을 갖고있는 서버로 또 다시 요청을 보낸다는데, 맞는지...?

만약에 자동으로 ELB가 알아서 원래 session이 있는 instance로 가는 거면 redis 나 elastic cache를 써볼 겸 session을 쓰겠는데, 그게 아니면 그냥 jwt로 할까 생각 중..



## 해본 거

며칠 간 CodeDeploy와 CodePipeline과 씨름하며 CodeBuild 약 2시간을 돌파해버림 ㅜㅜ... 삽질의 시간들아...

* CodeDeploy로 GIthub, S3 를 통해 EC2에 배포하기
* CodeBuild에서 cache를 이용해 build 시간 단축하기
* ECR에 이미지 푸시하기
* ECS 구성하고 업데이트하기
* CodePipeline으로 Github을 통해 EC2에 배포하기
* ~~CodePipeline으로 ECS에 배포하기~~ 
  -> 곧 해결할 수 있기를 바래봄.... 갑자기 설정해야할 게 너무 많아짐;;;🥺

그 결과물들...

[AWS CodeDeploy와 Github 이용해서 배포하기](https://senticoding.tistory.com/89)

[AWS CodeDeploy와 S3 이용해서 배포하기](https://senticoding.tistory.com/90)



# ❔궁금한 거 

* ELB 요금 체계가 좀 복잡한데, 그냥 안 쓰고 설정만 해놓을 경우에는 얼마정도 나가는지, 대충 얼마정도 나가는지?

* mongoDB를 이용하는데 mongoose 같은 ODM을 안 쓰는 경우도 있는지? 아마 거의 없을 듯

  그럼 js로는 mongoose를 이용하다가 python으로 mongothon을 이용하는 경우 크게 손실이 없는지?

* IAM Role vs IAM User
  Role은 주로 AWS Service에 부여되고, User는 aws cli의 configure에 부여되는 듯한데 Role이 정확히 뭐하는 건지..?

