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
3. Sever-less 无主机 cloud运营商提供管理主机服务（cloud provider manages servers for you）；分工

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

## 共同责任模式 Shared Responsibility Model

当我们开发程序并提供服务给用户和客户时，我们与AWS共同承担责任

### AWS is responsible for:

- Securing edge locations
- Monitoring physical device security
- Providing physical access control to hardware/software
- Database patching
- Discarding physical storage devices
- Providing generators and un-interruptible power supply (UPS) systems

### You are responsible for:

* Managing AWS Identity and Access Management (IAM)
* Encrypting data
* Preventing or detecting when an AWS account has been compromised
* Restricting access to AWS services to only those users who need it
* Applying security patches to EC2 
* Configuring a firewall

## 开设试用账户 Setup free-tier account

## Prerequisites:

- Credit card
- Valid email address
- Phone number (used during sign up for validation)
- Virtual Multi-Factor Authentication (MFA) application, such as, Google Authenticator, Authy 2-Factor Authentication, or Authenticator installed on your mobile phone

# Travel blog website

## 为何需要云服务器

1. Scale capacity up and down based on demands.
2. Storage, more memory, and computing power can be added as needed.
3. Obtain servers in minutes.
4. No need for onsite hardware or capital expenses.

## EC2 - Elastic Cloud Compute 弹性云计算

EC2 instance 

EC2 is found under the Compute section of the AWS Management Console.是AWS 最小的基础单位

价格选项：

1. On Demand - Pay as you go, no contract.
2. Dedicated Hosts - You have your own dedicated hardware and don't share it with others.
3. Spot(点) - You place a bid on an instance price. If there is extra capacity that falls below your bid, an EC2 instance is provisioned. If the price goes above your bid while the instance is running, the instance is terminated.
4. Reserved Instances - You earn huge discounts if you pay up front and sign a 1-year or 3-year contract.

## EBS -elastic block store 弹性块存储

a storage solution for EC2 instances and is a physical hard drive that is attached to the EC2 instance to increase storage.

好处 benefit ：

1. able to persist(存留) data after EC2 is terminated
2. automatically  replicated in its AZ(availability zone)

## security in the cloud

- Configure your virtual network with public or private facing subnets-使用面向公共或私有子网配置虚拟网络
- Launch your servers in the selected network to secure access-启动所选网络中的服务器以确保访问安全

## Virtual Private Cloud (VPC)-隔离云资源

Virtual Private Cloud or VPC allows you to create your own private network in the cloud. You can launch services, like EC2, inside of that private network. A VPC spans all the Availability Zones in the region.

VPC 可以控制：

- IP address ranges
- subnets
- route tables
- network gateways

EC2 Instances can be launched in a VPC, and you can store data in Amazon S3 and restrict access so that it’s only accessible from instances in your VPC.

## AWS实战项目

Topics Covered:

By the end of this lab, you will be able to:

- Launch a secure EC2 (Elastic Cloud Compute) instance within a VPC (Virtual Private Cloud)
- Manage an EBS volume



### **Access VPC service from AWS Management Console**

- On the AWS Management Console page, type `vpc` in the `Find Services` box and then select `VPC`.
- Click the `Launch VPC Wizard` button and select `VPC with a Single Public Subnet`. ***Important:\*** In the `VPC Name` text box, enter a name for the VPC, and then select the first AZ from the `Availability Zone` dropdown. Leave everything else as the defaults.
- Select `Create VPC` button.
- You should see the `VPC Successfully Created` page, click the OK button in the far right. ***Important:\*** You should see a table that lists all of the VPCs, make a note of the one just created.

### **Launch an EC2 instance**

- Navigate to the EC2 console page, by clicking on `Services` in the upper left-hand menu. Type `EC2` in the text box and click on `EC2` found in the search results.
- On the EC2 Dashboard page, click on `Instances` in the left-hand navigation.
- Click `Launch Instance`.
- Select the `Amazon Linux 2 AMI (HVM), SSD Volume Type` Amazon Machine Image (AMI). ***Important:\*** You are free to choose a different AMI, but to avoid excessive charges, pick one that says, `Free Tier Eligible`.
- For the `Instance Type`, select the free-tier instance type of `t2.micro`.
- Click on `Next: Configure Instance Details`.
- Enter the 1 for the `Number of Instances`.
- For Purchasing option, leave unchecked.
- For Network, select the VPC that was created in the previous step, and then select the subnet in to which to launch the instance.
- Keep the other default settings on this page as is.

![image-20200103113451529](cloud-fundamental.assets/image-20200103113451529.png)

### **Attach an EBS volume**

- Click on `Next: Add Storage` to attach an EBS volume. ***Important:\*** Here we already see there is a root volume (or device) attached to your instance, this is an EBS volume. We are going to add additional storage.
- To attach additional storage, click on `Add New Volume`.
- Select `Delete on Termination` and keep the other default settings.
- Click `Review and Launch`.
- Click `Launch`
- Generate and download a new key pair and then click `Launch Instances`. ***Important:\*** This will allow you to SSH into your instance from your local machine. This is a one-time process, so generate and download the new key pair now.
- The launch will take a couple of minutes, select `View Instances` during the wait.
- Check the instance state, it should say running.

![image-20200103113741855](cloud-fundamental.assets/image-20200103113741855.png)

### **Cleanup & Disable EC2 Instance** 

To avoid recurring charges for leaving an instance running, let’s disable the EC2 instance and terminate the VPC

- From the EC2 Dashboard, select the instance just created, click `Actions`, then `Instance State`, and then select `Terminate`.
- From the VPC Dashboard, select the VPC just created, click `Actions`, then `Delete VPC`.

![image-20200103114320880](cloud-fundamental.assets/image-20200103114320880.png)

需要先删除实例，再删除VPC

![image-20200103114427987](cloud-fundamental.assets/image-20200103114427987.png)

![image-20200103114600819](cloud-fundamental.assets/image-20200103114600819.png)

## Why do we need compute power in the cloud

Compute power 特点：

1. run code in the cloud
2. no provisioning or managing servers 不需要预先提供或者管理服务器
3. automatically scales 自动弹性伸缩
4. hight availability
5. fault tolerance 容错容差
6. focus on writing code

Compute power in the cloud is a faster way to build applications, providing:

- no servers to manage (i.e. serverless)
- ability to continuously scale
- ability to run code on demand in response to events
- pay only when your code runs