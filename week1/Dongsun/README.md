#지속적 배포 파이프라인 설정
:star2: 간단한 배포 파이프라인 travisCI와는 조금 느낌이 다르다. AWS에 다 맡겨라! 느낌이다. elastic beanstalk이 모든걸 다 알아서 해준다.

###1. docker-codepipeline 이라는 폴더 생성 

![image](https://user-images.githubusercontent.com/52663248/66267990-40f21200-e873-11e9-8cde-64a747b3cf97.png)

Dockerfile과 간단한 server.js작성
 
 ```Dockerfile
 #Dockerfile
FROM node:4.4
COPY server.js .
EXPOSE 8080
CMD ["node","server.js"]
```

```javascript
var http = require('http');
var handleRequest = function (request, response) {
  response.writeHead(200);
  response.end('Hello World!');
};
var www = http.createServer(handleRequest);
www.listen(8080);
```

###2. ElasticBeanstalk 생성 

![image](https://user-images.githubusercontent.com/52663248/66268100-d510a900-e874-11e9-9b76-17ae8c91009b.png)

###3. 생성완료

![image](https://user-images.githubusercontent.com/52663248/66268105-e8237900-e874-11e9-9176-289c5ea850b2.png)




###4. Codepipeline 생성

![image](https://user-images.githubusercontent.com/52663248/66268107-f2457780-e874-11e9-9965-a43ccb3e8e68.png)

###5. Codepipeline 배포 소스 공급자 - Github

![image](https://user-images.githubusercontent.com/52663248/66268110-fffafd00-e874-11e9-8b7f-e044c30b7a7b.png)

###6. 빌드 파이프라인 없음

###7. 파이프라인 생성 완료

![image](https://user-images.githubusercontent.com/52663248/66268127-24ef7000-e875-11e9-9eb3-c953ce782ee4.png)

###8. beanstalk의 url을 누르면 배포 완료

![image](https://user-images.githubusercontent.com/52663248/66268134-35074f80-e875-11e9-9588-193ed3ef2115.png)

###9. 수정후 파이프라인이 다시 돌아가는지 확인해봅시다.

![image](https://user-images.githubusercontent.com/52663248/66268143-4e100080-e875-11e9-88f7-95b746504548.png)

![image](https://user-images.githubusercontent.com/52663248/66268155-64b65780-e875-11e9-9a80-6fe01089d7cf.png)

![image](https://user-images.githubusercontent.com/52663248/66268157-713ab000-e875-11e9-9120-fbb5685a87f2.png)
####다시 돌아가네요

###10. 바뀐 내용 확인

![image](https://user-images.githubusercontent.com/52663248/66268162-89123400-e875-11e9-80bc-e4dd6b36c3fb.png)

* TravisCI는 .travis.yml에 빌드 설정 및 테스트 환경등에 대한 모든 설정을 기록해야 했다. 그런데 CodePipeline은 확실히 편하다. 다른 CI/CD툴들에 대해 더 사용해보고싶다. Jenkins는 아직 다뤄보지 못했는데 Jenkins를 이용해서 파이프라인을 구성해보고싶다. 
