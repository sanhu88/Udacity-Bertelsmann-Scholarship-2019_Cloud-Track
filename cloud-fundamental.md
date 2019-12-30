# Udacity-Bertelsmann-Scholarship-2019_Cloud-Track

Bertelsmann Tech Scholarship Challenge Course - Cloud Track on Udacity.com

## Chapter Cloud Fundamental 

****

## 云计算 Cloud Computing

包含：

* Database 数据库
* Computer Power 计算力
* Application 应用
* Security 安全

特点：

1. Pay-as-you-go 即用即付 无长期合同
2. Auto scaling 自动伸缩 自动增减
3. Sever-less 无主机 cloud运营商提供管理主机服务；分工

## 云计算类型 Types of Cloud Computing

1. ### Infrastructure-as-a-Service (IaaS) 基础架构服务

   The provider supplies virtual server instances, storage, and mechanisms for you to manage servers.

   虚拟机，存储，机器（AWS/阿里云/Linode/Digital Ocean）

2. ### Platform-as-a-Service (PaaS)

   A platform of development tools hosted on a provider's infrastructure.

   开发工具在他们的基础架构上，服务商管理硬件和系统，使用者只关注管理和开发应用（Godady/ salesforce）

3. ### Software-as-a-Service (SaaS)

   A software application that runs over the Internet and is managed by the service provider.

   提供某种软件来使用（Gmail / Office 365）

Did you know that Amazon Web Services (AWS) provides a mix of infrastructure as a service (IaaS), platform as a service (PaaS) and packaged software as a service (SaaS) offerings?

## 云部署模型  Cloud Deployment Models

1. 公有云 Public Cloud

   A public cloud makes resources available over the Internet to the general public.

   资源包括 服务器、数据库、应用开发服务

   AWS是最大公有云提供商

2. 私有云 Private Cloud 

   A private cloud is a proprietary(专属) network that supplies services to a limited number of people.

   On-premises 内部部署  best describes a private cloud.

3. 混合云 Hybrid Cloud

   A hybrid model contains a combination of both a public and a private cloud.

   *he hybrid model gives organizations the flexibility to slowly migrate to the cloud.*

   PII(personally identifiable information) 和网页服务搭配使用时

## 可见好处 Common Benefits

- ability to innovate quickly

- ability to fail fast

  fail-fast就是在做系统设计的时候先考虑异常情况，一旦发生异常，直接停止并上报

  对两个整数做除法的方法，在divide方法中，我们对被除数做了个简单的检查，如果其值为0，那么就直接抛出一个异常，并明确提示异常原因。这其实就是fail-fast理念的实际应用。
  这样做的好处就是可以预先识别出一些错误情况，一方面可以避免执行复杂的其他代码，另外一方面，这种异常情况被识别之后也可以针对性的做一些单独处理。

- Stop guessing about capacity.

- Avoid huge capital investments(投资) up front.

- Pay for only what you use.

- Scale globally in minutes.

- Deliver faster.

## Cloud 服务商

* AWS - Amazon Web Services
* GCP- Google Cloud Platform 
* Microsoft Azure 

## AWS 服务预览

1. Analytics 分析

   Amazon Quicksight

2. Application integration 应用集成

   SQS- simple queue service

   SNS- simple notification service

3. AWS cost management / Budgets (预算)

4. Compute services

   * EC2 -Elastic(弹性) Cloud Compute 虚拟机
   * Lambda 拉姆达 无主机服务
   * Elastic Beanstalk 网页服务

5. 数据库 Database

   * MySQL
   * Oracle
   * SQL Server
   * NoSQL - Dynamo DB
   * Document-based Database -MongoDB

6. Developer Tools

   * AWS Cloud 9 -Cloud IDE
   * Code Pipeline -continue integration 持续集成

7. Security services 安全服务

   * KMS -  key management service for data encryption
   * AWS shield - DDoS protection
   * IAM -Identity and Access Management 

8. Additional Services

   - Blockchain
   - Machine Learning
   - Computer Vision
   - Internet of Things (IoT)
   - AR/VR

将会学习到：

popular storage、content delivery services 、networking 、security and messaging services

## 全球基础架构 Global Infrastructure

1. ### Region 区域 （22） 

   A region is considered a geographic location or an area on a map.

   区域间资源不会跨区域复制replicate

2. ### Availability Zone AZs 可用区

   An availability zone is an isolated location within a geographic region and is a physical data center within a specific region.一个可用区失败不会影响到另外一个可用区

3. ### Edge Location 本地区域

   An edge location is as a mini-data center used solely to cache large data files closer to a user's location. CDN

### Additional Information

- There are more Availability Zones (AZs) than there are Regions.
- There should be at least two AZs per Region.
- Each region is located in a separate geographic area.
- AZs are distinct locations that are engineered to be isolated from failures.

