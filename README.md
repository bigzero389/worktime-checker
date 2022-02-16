# Worktime checker app Architecture in AWS 
<img width="1273" alt="image" src="https://user-images.githubusercontent.com/16658223/154238478-5a050885-a860-4616-a089-003f6951d44f.png">

## AWS outside 
### User Client 
* aOS, iOS, Web(Angular)
* SSO : private SSO
### In-house system interface
* Oracle DBMS interface : Worker working time data interface
### Mobile push
* Firebase : Mobile push notification

## AWS inside
### Front-end
* Cloudfront + WAF + S3(worktime.co.kr) : Front-end CDN + Static source
* S3(app-download) : ipa & apk deployment
### API Gateway
* API Gateway + X-ray enabled
### Monitoring
* OpenSource Java APM
* Cloudwatch
* X-ray : App Mesh, Cloud Map
### PaaS Solution
* AWS SES : eMail 
### Networking
* VPC
* NLB
* NAT
* internet gateway
### Data
* DynamoDB 
* Lambda : DynamoDB data interface to oracle in-house system
* ElasticSearch
* Aurora
* ElastiCache : Session, Data cache
### Container
* ECS + x-ray : App Mesh , side-car pattern
* Fargate(Docker) : springboot
### CI/CD
* BitBucket -> CodeCommit(Repository sync), CodeBuild, CodeDeply and Code Pipeline
* Build monitoring : google-chat