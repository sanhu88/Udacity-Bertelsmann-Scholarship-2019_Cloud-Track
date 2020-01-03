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

## AWS Lambda

a chuck of code that run in the Cloud,Lambda is one serverless technology offered by AWS.

- Lambda is found under the Compute section on the AWS Management Console.
- Lambdas have a time limit of 15 minutes.
- The code you run on AWS Lambda is called a “Lambda function.”
- Lambda code can be triggered by other AWS services.
- AWS Lambda supports Java, Go, PowerShell, Node.js, C#/.NET, Python, and Ruby. There is a Runtime API that allows you to use other programming languages to author your functions.
- Lambda code can be authored via the console.

The Lambda console editor in the AWS Management Console is the easiest way.

Lambda is event-driven, so you can run your code based on certain events happening, like a file upload, or a record being inserted in a database, etc.

实习：

## Steps:

1. Create a Lambda Function

   - On the AWS Management Console page, type `lambda` in the `Find Services` box and then select `Lambda`.
   - Click the “Create function” button and select `Author from scratch`.(重头开始创造)
   - Enter a `Function name` and select `Node.js 8.10` as the runtime.
   - For `Permission`, click `Choose or create an execution role`, and select `Create a new role with basic Lambda permissions`.
   - Click `Create function`.

2. Modify a Lambda Function

   - Scroll down to the code for the Lambda function.

   - Replace the code on Line 5 with the statement below:

     ```
     body: JSON.stringify('Hello ' + event.key1 + ' from Lambda!'),
     ```

   - Click the `Save` button in the upper right-hand corner.

   - Scroll down to the

      

     ```
     Basic Settings
     ```

      

     section.

     - For the Description, enter `Udacity Function`.
     - Change the `Timeout` from 3 seconds to 10 minutes.
     - Click the `Save`button in the upper right-hand corner.

3. **Test a Lambda Function**

   - Click on the `Test` button in the upper right-hand corner.

   - Ensure the `Event template` is `Hello World`.

   - For the `Event name` enter `TestEvent` ***Important:\*** The name cannot contain spaces.

   - Update the JSON to the statement below, replacing the statement with your name.

     ```
     {
     "key1": "Place your name here"
     }
     ```

4. Click `Create`.

5. Click the `Test` button in the upper right-hand corner again.

6. Scroll up to see the output in the `Execution Results` pane.

7. Review your results in the window.

## Elastic Beanstalk（web 服务）

Elastic Beanstalks is an orchestration service(业务流程服务)

Elastic Beanstalk can spin up database instances for you, VPCs, security groups, EC2 instances, etc.

实习：

## Steps:

1. Access Elastic Beanstalk service from AWS Management Console
   - On the AWS Management Console page, type `elastic beanstalk` in the `Find Services` box and then select `Elastic Beanstalk`.
   - If this is your first time accessing Elastic Beanstalk, click the `Get started` button.
   - Enter an `Application name`.
   - Under `Platform`, click the dropdown for `Choose a platform`. Select `Tomcat`.
   - Under `Application code`, select `Upload your code`. Click the `Upload` button.
   - Under `Upload your code`, make sure `Local file` is selected for `Source code origin`.
   - Click `Choose File` and upload the downloaded WAR file (link above in pre-requisites), `udacity.war`.
   - Click the `Upload` button.
   - Click the `Create application` button. ***Important:\*** It will take about 10 minutes for your application to be created. There are several resources that need to be spun up to support your application. Your application is created once you see a green check mark and the `Health` of your application is `Ok`.
   - After the application is created, copy the application’s URL. ***Important:\*** The URL can be found on the top of the page, to the right of your application’s name.
2. Test the deployed web application in a browser
   - Navigate to a web browser like Chrome or Safari.
   - Paste the application URL and append `/message` on the end of the URL.
   - Upon successfully accessing that URL, you will see the text `Hello World` in your browser window.
3. Inspect the EC2 instance created for you
   - Navigate to the EC2 console and inspect the instance that was created for you. The instance has the same name as your application. You can administer and manage this EC2 as if you created it yourself.
4. Cleanup and delete resources
   - To clean up the resources to avoid recurring charges, navigate back to the Elastic Beankstalk console.
   - Select your application.
   - Select the `Actions` button in the upper-right hand corner.
   - Select `Terminate environment`.
   - Enter the name of the environment to be deleted.
   - Click the `Terminate` button.
   - After the application is terminated, you will be brought to the main page for the application.
   - Click on the `Actions` button in the upper right-hand corner.
   - Select `Delete application`.
   - Enter the name of your application.
   - Click the `Delete` button.

## storage in the cloud

* Durability(耐久坚固) -guarantees that you will not lose the data that you upload to the cloud
* Availability - addresses how quickly you can access your data(解决访问数据的速度问题)
* Scalability - allows applications running in your environment to always meet demand seamlessly
  1. Vertical scaling -scaling up
  2. Horizontal scaling - scaling out  add or remove server to meet demands
  3. Diagonal scaling - combination horizontal and vertical;maximum flexibility

### Storage & Database Services

- Amazon Simple Storage Service (Amazon S3)
- Amazon Simple Storage Service (Amazon S3) Glacier
- DynamoDB
- Relational Database Service (RDS)
- Redshift
- ElastiCache
- Neptune
- Amazon DocumentDB

## 冰川网络S3 & S3 Glacier

Amazon Simple Storage Service (or S3) is an object storage system in the cloud，like file system in the cloud

文本，图片，html都可以

文件存储在bucket(存储桶)里，S3 的bucket在region里；必须全局唯一名字

使用案例：

* hosting static websites
* content delivery
* backup and recovery
* archiving and big data
* application data
* hybrid cloud storage

### Storage Classes 分类

- S3 Standard
- S3 Glacier(for data archiving purposes,比标准版便宜)
- S3 Glacier Deep Archive
- S3 Intelligent-Tiering
- S3 Standard Infrequent Access
- S3 One Zone-Infrequent Access

S3 Glacier 用于举例：

1. monthly log files
2. Audit(审计) purpose
3. preserve(保存) purpose
4. infrequently accessed(经常访问)

### Tips

- S3 is found under the Storage section on the AWS Management Console.
- A single object can be up to 5 terabytes in size.
- You can enable Multi-Factor Authentication (MFA) Delete on an S3 bucket to prevent accidental deletions.
- **S3 Acceleration** can be used to enable fast, easy, and secure transfers of files over long distances between your data source and your S3 bucket.

## DynamoDB 

DynamoDB is a NoSQL document database service that is fully managed. Unlike traditional databases, NoSQL databases, are schema-less. Schema-less simply means that the database doesn't contain a fixed (or rigid) data structure.

Data is stored in JSON or JSON like text,JSON is simple text representing data in key value pairs.



- DynamoDB is found under the Database section on the AWS Management Console.
- DynamoDB can handle more than 10 trillion requests per day.
- DynamoDB is serverless as there are no servers to provision, patch, or manage.
- DynamoDB supports key-value and document data models.
- DynamoDB synchronously replicates data across three AZs in an AWS Region.
- DynamoDB supports GET/PUT operations using a primary key.

实习DynamoDB:

### Topics Covered:

By the end of this lab, you will be able to:

- Create a table
- Add data to a table
- Query data in a table

### Steps:

1. Access the DynamoDB service from AWS Management Console
   - On the AWS Management Console page, type "dynamo" in the `Find Services` box and then select `DynamoDB`.
   - On the DynamoDB Console, click `Create table`.
   - Enter `Course` as the `Table name`.
   - Enter `Name` in for the `Partition key` and ensure `String` is selected. ***Note:\*** The partition key spreads data against partitions for scalability.
   - Keep the remainder of the defaults, and click the `Create` button.
2. Add Data to the Table
   - Once the table is created, click on the `Items` tab.
   - Click Create item
     - In the data entry window, type the following:
       - For name, enter, `Course 1` and click `Save`
       - Click the +i con to add additional fields:
         - Select `Insert`
         - Select `String`
         - For the field name, enter `Teacher`
         - For the value, enter `Kesha Williams`
         - Click `Save`
   - Follow the same process to add 5 more documents.
3. Query Data in a Table
   - In the dropdown that contains `Scan`, change it to `Query`.
   - Where it says `Enter value`, in the row next to the `name` Partition key, enter `Course 1` and click `Start Search`.
   - You should see your search results appear in the window.
4. Cleanup and delete resources
   - To clean up the resources to avoid recurring charges, ensure the table name is selected.
   - Click on the `Delete table` button.
   - Ensure `Delete all CloudWatch alarms for this table` is selected and click `Delete`.

## 关系型数据库RDS (or Relational Database Service)

RDS (or Relational Database Service) is a service that aids in the administration and management of databases. RDS assists with database administrative tasks that include upgrades, patching, installs, backups, monitoring, performance checks, security, etc.

- Oracle
- PostgreSQL
- MySQL
- MariaDB
- SQL Server

### Features

- failover
- backups
- restore
- encryption
- security
- monitoring
- data replication
- scalability

练习题：

To deliver a managed service experience, Amazon RDS doesn't provide shell access to DB instances.

## RedShift

Redshift is a cloud data warehousing service to help companies manage big data. Redshift allows you to run fast queries against your data using SQL(standard query language), ETL(extract transform load tolols), and BI (business intelligence )tools. Redshift stores data in a column format to aid in fast querying.

- Redshift can be found under the Database section on the AWS Management Console.
- Redshift delivers great performance by using machine learning.
- Redshift Spectrum is a feature that enables you to run queries against data in Amazon S3.
- Redshift encrypts and keeps your data secure in transit and at rest.
- Redshift clusters can be isolated using Amazon Virtual Private Cloud (VPC).

以在线商店为例，当年的订单数据应当存储在RDS关系型数据库中，以便每日使用。10年之前的数据可以archive到redshift中用来分析，有快速的查询和分析能力

实习：

## Steps:

1. **Launch MySQL Database**

   - On the AWS Management Console page, type `rds` in the `Find Services` box and then select `RDS`.

   - On the left-hand side, click `Databases`.

   - Click `Create database`.

   - Under engines option, select `MySQL` and click the `Next` button

   - Under `Instance specifications`, leave the defaults.

   - Under the `Settings` section:

     - Enter a name for the instance under `DB instance identifier`

     Note: This will not be the database name.

   - Enter a `Master username`

   - Enter a `Master password` and confirm the password.

   - Click `Next`

   - For `Virtual Private Cloud (VPC)`, select `Create new VPC`.

   - Ensure `Create new DB Subnet Group` is selected.

   - Leave the defaults for `Subnet group`, `Public accessibility`, `Availability zone`, and `VPC security groups`.

   - Under `Database options`, enter a `Database name` and leave the rest as defaults.

   - Under `Deletion protection`, uncheck `Enable deletion protection`. ***Important:\*** In a real production scenario, you would leave this option checked.

   - Click Create database`.

2. View Instance Details

   - Once your database is created, open it by clicking on `View DB Instance details`.
   - Make sure the `DB instance status` shows `available`.
   - Scroll through and observe how the instance is configured.

3. Delete Database Instance

    

   Clean up the resources to avoid recurring charges.

   - From the RDS Dashboard homepage, select `Databases` from the left-hand navigation pane.
   - Select your newly created database by clicking on the name radio button next to the name.
   - From the `Actions` menu, select `Delete`.
   - In the confirmation popup:
     - Uncheck `Create final snapshot`
     - Select `I acknowledge that upon instance deletion, automated backups, including system snapshots and point-in-time recovery, will no longer be available.`
     - Enter the requested confirmation for deletion.
     - Click the `Delete` button