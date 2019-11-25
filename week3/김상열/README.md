## Developing Kubernetes Services with MSA

### Goals
Airbnb의 [Developing Kubernetes Service at Airbnb Scale](https://www.slideshare.net/awskorea/airbnb-kubernetes-melanie-cebula-airbnb-aws-summit-seoul-2019) 발표 자료를 바탕으로 대규모 서비스에서 Kubernestes를 이용해 배포하는 방법을 공부하고, Solution 과제를 중점으로 직접 쿠버네티스 환경 구축하기

### Why Kubernetes?
- Evolution of configuration management
- Automate configuration and orchestration of containerized applications with Kubernetes
- Kubernetes + Docker + YAML

### Why MicroServices?
- Scaling Continuous Delivery (Develop, Build, Test, Deploy, Release)

### Challenges with Kubernetes
- Complex configuration
- Complex tooling
- Integrating with your current infrastructure
- scaling

### Solutions?
- Abstract away Kubernestes configuration
- Generate service boilerplate
- Version + Refactor configuration
- Opinionated kubectl
- Custom CI/CD + Validation

### References
- https://www.slideshare.net/awskorea/airbnb-kubernetes-melanie-cebula-airbnb-aws-summit-seoul-2019