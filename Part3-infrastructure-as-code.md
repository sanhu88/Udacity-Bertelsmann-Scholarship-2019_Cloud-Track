# infrastructure-as-code 

lesson 18 - 24

****

# lesson 18 - AWS Management

## logging and auditing in the cloud

假设网站的用户在输入信用卡的时候回显示错误。

Logging provides visibility into your cloud resources and applications. For applications that run in the cloud, you will need access to logging and auditing services to help you proactively（主动地） monitor your resources and applications.

Logging allows you to answer important questions like:

- How is this server performing?
- What is the current load on the server?
- What is the root cause of an application error that a user is seeing?
- What is the path that leads to this error?

## Cloud Trail 

跟踪用户活动和API使用率

allows you to audit (or review) everything that occurs in your AWS account. Cloud Trail does this by recording all the AWS API calls occurring in your account and delivering a log file to you.

CloudTrail provides event history of your AWS account activity, including:

- who has logged in
- services that were accessed
- actions performed
- parameters for the actions
- responses returned

This includes actions taken through the AWS Management Console, AWS SDKs, command line tools, and other AWS services.

贴士：

- Cloud Trail is found under the Management & Governance section on the AWS Management Console.
- CloudTrail shows results for the last 90 days.
- You can create up to five trails in an AWS region.

AWS默认开启CloudTrail 功能

多余一条之后要收费

## Cloud Watch

监控资源和应用程序

 is a service that monitors resources and applications that run on AWS by collecting data in the form of logs, metrics(度量；指标), and events.

There are several useful features:

- Collect and track metrics
- Collect and monitor log files
- Set alarms and create triggers to run your AWS resources
- React（做出反应） to changes in your AWS resources

贴士：

- CloudWatch is found under the Management & Governance section on the AWS Management Console.
- Metrics are provided automatically for a number of AWS products and services.

讲师演示CloudWatch 关于Lambda 的运行日志

## CloudWatch 实习

### Topics Covered:

By the end of this lab, you will be able to:

- Create Cloud Watch event to react to the creation of an Amazon EC2 instance
- Send SNS notification via Cloud Watch when an event occurs

### Steps:

1. Create CloudWatch Rule
   - On the AWS Management Console page, type `cloud watch` in the `Find Services` box and then select `CloudWatch`. The CloudWatch Dashboard appears.
   - On the left-hand menu, under `Events`, select `Rules`.
   - Click `Create rule`.
   - For `Service Name`, select `EC2`.
   - For the `Event Type`, select `EC2 Instance State-change Notification`.
   - Select the `Specific state(s)` radio button. Select `running` from the drop-down box. ***Note:\*** This configures the rule to trigger whenever an Amazon EC2 instance changes to the running state, which happens when an instance is launched or started.
   - On the right-hand side of the screen, in the `Target` section, add a target by clicking on `Add target`.
   - In the drop-down, change `Lambda function` to `SNS topic`.
   - For the `Topic`, select the topic you created in the SNS hands-on exercise. ***Important:\*** If the Topic doesn’t appear, the `Access policy – optional` section doesn’t have the correct permissions to allow other services to access the Topic.
   - Scroll down and click the `Configure details`.
   - Enter a name in the `Name` field. Ensure the state is `Enabled`. Click `Create rule`.
2. Test CloudWatch Rule
   - Navigate to the EC2 console page, by clicking on `Services` in the upper left-hand menu. Type `EC2` in the text box and click on `EC2` found in the search results.
   - On the EC2 Dashboard page, click on `Instances` in the left-hand navigation.
   - Click `Launch Instance`.
   - Select the `Amazon Linux 2 AMI (HVM), SSD Volume Type` Amazon Machine Image (AMI). ***Important:\*** You are free to choose a different AMI, but to avoid excessive charges, pick one that says, `Free Tier Eligible`.
   - For the `Instance Type`, select the free-tier instance type of `t2.micro`.
   - Click `Review and Launch`.
   - Click `Launch`.
   - Generate and download a new key pair and then launch the instance.
   - Click `Launch Instances`.
   - Click on `View Instances`.
   - Once the Instance state changes to `Running`, check your email client for an email alert from the SNS Topic.
3. Cleanup & Disable EC2 Instance and Cloud Watch Rule
   - To avoid recurring charges for leaving an instance running, let’s disable the EC2 instance.
   - From the EC2 Dashboard, select the instance just created, click `Actions`, then `Instance State`, and then select `Terminate`.
   - To avoid recurring charges for leaving the Cloud Watch rule running, let’s disable it.
   - From the SNS Dashboard, select `Rules` from under the `Events` section.
   - Select the Rule you just created, by clicking the radio button next to the Rule.
   - Click on the `Actions` button, and select `Delete`.

![image-20200107215239335](Part3-infrastructure-as-code.assets/image-20200107215239335.png)

当指标数据达到您设定的水平时，您可以使用 CloudWatch 警报获取自动通知。

要编辑警报，首先请选择通知对象，然后设定何时发送通知。

![image-20200107215258673](Part3-infrastructure-as-code.assets/image-20200107215258673.png)

如果有多个SNS的主题，确保邮箱已经订阅这个主题。

> {"version":"0","id":"71a9f4e******77aaa2ec02d","detail-type":"EC2 Instance State-change Notification","source":"aws.ec2","account":"07295******16","time":"2020-01-07T14:01:36Z","region":"us-east-2","resources":["arn:aws:ec2:us-east-2:07295***16:instance/i-018b6*6c9f1"],"detail":{"instance-id":"i-018*9f1","state":"stopped"}}

Xshell连接AWS EC 

~~~
ssh -i /path/my-key-pair.pem ec2-user@ec2-198-51-100-1.compute-1.amazonaws.com
~~~

如果还提示，可以在本地先导入创建主机的私钥【**Amazon Linux 2 AMI (HVM), SSD Volume Type**】

EC2 开放端口是在网络安全--安全组--对应的组--入站

## Infrastructure as Code

 allows you to describe and provision all the infrastructure resources in your cloud environment. You can stand up servers, databases, runtime parameters, resources, etc. based on scripts that you write. Infrastructure as Code is a time-saving feature because it allows you to provision (or stand up) resources in a reproducible way.

有点类似docker 的 yml部署

## Cloud Formation（云模板）

使用模板创建额管理资源

AWS Cloud Formation allows you to model your entire infrastructure in a text file template allowing you to provision AWS resources based on the scripts you write.

- Cloud Formation is found under the Management & Governance section on the AWS Management Console.
- Cloud Formation templates are written using JSON or YAML.
- You can still individually manage AWS resources that are part of a Cloud Formation stack.

习题：

Since your infrastructure is now code, you can check your scripts into version control.

实习：

By the end of this lab, you will be able to:

- Create a CloudFormation stack using the CloudFormation Designer
- Launch S3 bucket using Infrastructure as Code
- Save and deploy a CloudFormation stack
- View resources created through CloudFormation

### Steps:

1. **Create CloudFormation Stack**
   - On the AWS Management Console page, type `cloud formation` in the `Find Services` box and then select `Cloud Formation`. ***Important:\*** The redesigned AWS CloudFormation console is available now. This tutorial covers the new designer. To access the new designer, click on the `Try it out now and provide us feedback.` message that displays in a message similar to what’s shown below.
   - On the AWS Management Console page, type `cloud formation` in the `Find Services` box and then select `Cloud Formation`.
   - If the left-hand menu options do not appear, expand the options by clicking on `` in the top left-hand corner.
   - Select `Designer` from the left-hand menu.
   - Locate `S3` in the `Resource Type` section and expand it.
   - Select Bucket and drag it to the designer window on the right-hand side.
   - Copy the JSON below and replace entirely the JSON found in the `Properties` (属性)tab.

~~~yaml
{
  "AWSTemplateFormatVersion": "2010-09-09",
  "Description": "Basic S3 Bucket CloudFormation template",
  "Resources": {
    "S3BucketCreatedByCloudFormation": {
      "Type": "AWS::S3::Bucket",
      "Properties": {
        "AccessControl": "PublicRead"
      }
    }
  },
  "Outputs": {
    "BucketName": {
      "Value": {
        "Ref": "S3BucketCreatedByCloudFormation"
      },
      "Description": "Name of the newly created Amazon S3 Bucket"
    }
  }
}
~~~

Hit the Refresh button in the upper right-hand corner so that the Designer is not out of date.

2. Save CloudFormation Stack

- In the CloudFormation Designer Toolbar, click the Document icon , and click Save.
- Click `Local File` and click `Save`. The JSON file will download.
- In the AWS CloudFormation Designer toolbar, click to validate your template（黑色对号）. You will see a message that states, `Template is valid`.

3. Deploy CloudFormation Stack

- In the CloudFormation Designer Toolbar, click to deploy the stack. （云朵图标）The `Create stack` screen appears.
- Accept the defaults and click `Next`.
- Enter a `Stack name`. Leave `Parameters` empty. Click `Next`.
- Leave the defaults and click `Next`.
- Review the stack details and click `Create Stack`. The stack status will be `CREATE_IN_PROGRESS`. To the current status of the stack, select the Refresh button in the upper right-hand corner. Once the stack reaches the `CREATE_COMPLETE` status, the stack has been deployed.

4. View S3 Bucket created by CloudFormation Stack

- From the `Services` menu option at the top, type in `S3` and select `S3`.
- To quickly find the bucket created by the CloudFormation Stack, click on `Date Created` in the column heading to sort by the most recent buckets created.
- The newly created bucket appears at the top, `cfs3stack-s3bucketcreatedbycloudformation-1at0fv1v9ndc1`.

5. Delete CloudFormation Stack

- To avoid on-going charges, delete the stack by navigating to the stack, and clicking the `Delete` button in the upper right-hand corner. ***Note:\*** When the stack is deleted, all resources created by the stack template will be deleted also.

## The AWS CLI 

(or Command Line Interface) allows you to access and control services running in your AWS account from the command line. To use the CLI, simply download, install, and configure it.

安装 本地CLI上使用;

~~~bash
 aws ec2 describe-instance	#list all of the instance running in account
 
 aws sns publish --topic-arn arn:aws:sns:us-east-1:xxxxxxx:topicName --message "Publish via Command LIne"	#publish a message to an SNS topic ,will returns the message ID and Email will received
 
 aws sqs(severice name) send-message(action) --queue-ur https://sqs.us-east-q.amazonaws.com/xxxx/payment-request-q.fifo --message-body "Message fROM CLI" --message-group-if "3424235577" --message-deduplication-id "456456222445"#send message to sqs
 
 aws sqs receive-message --queue-url https://sqs.us-east-q.amazonaws.com/xxxx/payment-request-q.fifo#list th message in a queue
 
aws s3 ls s3://codevr(bucket name) #list the contents of an S3 bucket via the CLI
~~~

![image-20200110224403620](Part3-infrastructure-as-code.assets/image-20200110224403620.png)



![image-20200110224919911](Part3-infrastructure-as-code.assets/image-20200110224919911.png)



![image-20200110225134772](Part3-infrastructure-as-code.assets/image-20200110225134772.png)

links [[AWS Command Line Interface](https://aws.amazon.com/cli/)](https://amazonaws-china.com/cn/cli/)

英文版 [https://amazonaws-china.com/cli/?nc1=h_ls](https://amazonaws-china.com/cli/?nc1=h_ls)

***

# lesson 19 - Cloud Formation

## Course Overview

**Lesson 1:** Introduction to Cloud Formation
**Lesson 2:** Understanding Diagrams of Cloud Architecture
**Lesson 3:** Infrastructure as Code (convert diagrams into code)
**Lesson 4:** Deploying Services
**Lesson 5:** Additional services that you’ll use in the project

## DevOps 

development operations

#### Issues that DevOps tries to solve:

- Unpredictable deployments
- Mismatched environments (development doesn’t match production) 不同的系统
- Configuration Drift-配置漂移，比如线上因为某次维护使得线上和本地开发不一致

#### DevOps gives best practices and tools for solving these problems:

- DevOps Tools: DevOps tools deploy and manage configuration changes to servers.
  - [Stackexchange](https://softwareengineering.stackexchange.com/questions/130850/difference-between-devops-and-software-configuration-management) has a discussion post detailing the difference between DevOps tools vs. Software Configuration Tools
- Allows for predictable deployments, because it’s an automated script.
- Enables **Continuous Integration Continuous Deployment (CI/CD)** so that new features are automatically deployed with all the required dependencies.

## CloudFormation

### AWS region used for this course

Choose AWS region US-west-2 (Oregon) for our course. This will guarantee the options are the same for all students.

### Glossary

**CloudFormation:** CloudFormation is a tool in AWS for managing, configuring and deploying infrastructure (push code along with the necessary server configurations).

习题：

You'll need these three tools to get started in CloudFormation：

* Version Control 
* Code Editor for YAML and JSON
* Amazon Web Services account

## Deciding Access Privileges within AWS

#### Programmatic Access

In the AWS console, choose "**programmatic access**." This allows us to use code to interact with AWS, instead of relying on mouse clicking in the console web pages.

#### Administrator Access

For IAM access, choose “**administrator access**.” This is just for initial setup of your account. Afterwards, you’ll want to limit access to only what you need.

#### Dev and Prod user accounts

In practice, Dev and DevOps members may have separate user accounts for the dev environment as opposed to the production environment. This makes it easier for developers by giving them wider privileges in the dev environment that would normally only be reserved for DevOps members in the production environment.

#### Access Key ID and Secret Access Keys

Remember not to save these in your code or to check into any repositories. Keep these private to you.

保证秘钥的安全性

![image-20200116191142180](Part3-infrastructure-as-code.assets/image-20200116191142180.png)



![image-20200116191207228](Part3-infrastructure-as-code.assets/image-20200116191207228.png)

![image-20200116191228295](Part3-infrastructure-as-code.assets/image-20200116191228295.png)

![image-20200116191404417](Part3-infrastructure-as-code.assets/image-20200116191404417.png)

练习：

When creating a new API Access user, you will：

* Specify the region - in our case, us-west-2
* Create a programmatic access IAM User
* Configure the AWS CLI Tool with the newly created keys for our user
* Assign an appropriate IAM Policy to the user, depending on the required access

Specifying a region is a nice-to-have and not mandatory, but it does make your life easier when using region-specific services.

## Configuring AWS CLI

https://aws.amazon.com/cli/ to download software

习题：

Regarding your access keys it's always best to：

* Rotate them (change them ) frequently，It's great practice to change them every 90 days or sooner and 

* Make them inactive if they won't be used for a while，also to just delete them or mark them inactive when not in use.
* Please do NOT store your access key in a code repository; this is very insecure.
* We strongly recommend you don't put them in shared storage inside a text file either.

### Configuring the AWS Command Line Interface (CLI)

- Download and install the [AWS CLI tool.](https://aws.amazon.com/cli/)
- In the terminal, type `aws --version`: this verifies that you have the AWS CLI tool.

~~~
$ aws --version
aws-cli/1.17.3 Python/2.7.16 Windows/10 botocore/1.14.3

~~~



- To set up your AWS CLI, type `aws configure` in the terminal. Next when prompted for the AWS Access Key ID, paste in your `Secret access key`.
- Region: Please use `us-west-2`, even if you’re living closer to another available region.

![image-20200116194738699](Part3-infrastructure-as-code.assets/image-20200116194738699.png)

### Verifying your Setup

- One way to check if your AWS CLI is set up properly is to try a command. You can try listing your S3 buckets:`aws s3 ls` . **This will be blank if you have no S3 buckets**. However, if you have no error message, then you’ve verified that your user has API access to communicate with AWS.

~~~
aws s3 ls
2020-01-16 19:17:45 elasticbeanstalk-us-east-2-0729
~~~



- Note that each user can have up to 2 access keys at the same time.

more detail on 

1. [https://github.com/aws/aws-cli](https://github.com/aws/aws-cli)
2. [http://docs.aws.amazon.com/cli/latest/reference/](http://docs.aws.amazon.com/cli/latest/reference/)

## Additional Access Keys

Note that each user can have up to 2 access keys at the same time.

### Why Making Keys Inactive is a Better Choice

You may make your access key temporarily inactive rather than destroying it and creating a new one. This may be helpful if you want to stop an automated process that uses that key (for example, a CI/CD process).

## CloudFormation

- CloudFormation is a declarative language(声明性语言), not an imperative language（命令性语言）.
- CloudFormation handles resource dependencies, so that you don’t have to specify which resource to start up before another. There are cases where you can specify that a resource depends on another resource, but ideally, you’ll let CloudFormation take care of dependencies.
- VPC is the smallest unit of resource.

### Glossary

**Declarative languages**: These languages specify what you want, without requiring you to specify how to get it. An example of a popular declarative language is SQL.
**Imperative languages**: These languages use statements to change the state of the program.
*Additional resources:*

- Here is the [Wikipedia page](https://en.wikipedia.org/wiki/Imperative_programming) describing the differences between the two.
- Here is a [Stack Overflow](https://stackoverflow.com/questions/17826380/what-is-difference-between-functional-and-imperative-programming-languages) thread describing imperative languages.

## CloudFormation Script

#### YAML and JSON

- YAML and JSON file formats are both supported in CloudFormation, but YAML is the industry preferred version that’s used for AWS and other cloud providers (Azure, Google Cloud Platform).
- An important note about YAML files: the whitespace indentation matters! We recommend that you use **four white spaces for each indentation**.（四个空格作为一个缩进）

#### Glossary in CloudFormation scripts

**Name**: A name you want to give to the resource (does this have to be unique across all resource types?)
**Type**: Specifies the actual hardware resource that you’re deploying.
**Properties**: Specifies configuration options for your resource. Think of these as all the drop down menus and checkbox options that you would see in the AWS console if you were to request the resource manually.
**Stack**: A stack is a group of resources. These are the resources that you want to deploy, and that are specified in the YAML file.

#### Best practices

**Coding best practice:** Create separate files to organize your code. You can either create separate files for similar resources, or create files for each developer who uses those resources.

#### Documentation for CloudFormation syntax

You don't need to memorize the code that you need for each resource. You can find sample code in the [documentation for CloudFormation](https://docs.aws.amazon.com/index.html) for examples of how to write your CloudFormation scripts.

习题：

If you have a team of database, operations and networking experts, you would split your CloudFormation script into several files based on:

Type of resource

You'd have a file for network resources, another for database resources, and so on. This allows each expert to work on, and become familiar with, their resources and leverage their already-existing knowledge.

## run CloudFormation

- For this example, we’ll assume your CloudFormation file name is called `testcfn.yml`, and you’re giving your stack the name `myfirsttest`.
- In the terminal, to use your yml code to request the resources, type the following in the same directory as your yml file:

~~~yaml
aws cloudformation create-stack 
--stack-name myfirsttest 
--region us-west-2 
--template-body testcfn.yml
~~~

* You may also want to use `update-stack` when you want to update an existing stack instead of destroying your stack and creating a new one.

习题：

If you have a team of database, operations and networking experts, you would split your CloudFormation script into several files based on: Yes

CloudFormation uses a lot of logic behind the scenes to make sure everything works as expected, even when you don't specify resources in a specific order.

## Creating a VPC: Manually vs Automated

1. select our VPC from our region and I'll click the Create VPC button in the AWS console
2. use YAML file create at AWS CLI

## Automating with CloudFormation

duplicate with before we learn about create a user in IAM.

习题：

Can you verify the status of your CloudFormation stack from the command line?

Certainly! This is actually very useful if you are creating a program or script that verifies your stacks for you. However, if you are troubleshooting your stack, is probably best to do so from the AWS Console.



## Verifying in console

like in run CloudFormation ,use user use AWS cloud formation create-stack to create a stack in CLI

习题：

You are likely to need AWS Credentials (API Keys) in order to write code using the AWS SDK and to use the AWS Command Line Interface (CLI). Where do you suggest we store those credentials

On my work computer

Surprisingly, this is the best choice here! The problem with S3 and EC2 is that in order to access those, you'll need credentials in the first place.

## Conclusion

### Manually deploy an EC2 Instance for use with the CLI Tool.

We have installed and configured the AWS CLI to do our work for this course. However, there’s an alternative.

Go ahead and create an EC2 Instance that you can SSH into (or Remote Desktop, if you prefer Windows). Do this manually, in the console. Be sure to limit access to your IP address only, using Security Groups.

Once the instance is running, create an IAM Role with Admin access to your account, associate the role to your EC2 and install the AWS CLI on it.

The CLI tool, in this case, will pick up the credentials from the role and won’t need hard-coded credentials

# lesson 20 Infrastructure Diagrams 、基础设施图表

## Introduction

in the cloud,don't have physical access to that data center，need diagrams and then turn those diagrams into actual infrastructure called scripts

## Generalizing(归纳) to other cloud providers

similar names when it comes to other Cloud providers

In Google Cloud and AWS, they call it BPC

Generalizable to AWS, Google Cloud Platform, Microsoft Azure

The diagrams and resources covered in this lesson are generalizable to other cloud providers (such as Azure and Google Cloud Platform).

## Setting up Lucidcharts

练习：

Cloud Architecture diagrams are...

a great discussion tool to communicate to others what you intend to create

#### Lucidchart

We’ll use [Lucidchart](https://lucidchart.com/) to create cloud diagrams. Other applications that generate diagrams include Visio or Cloudcraft.

**Note to students**: You won’t need to know how to create diagrams for the project. The goal of this lesson is to get you familiar with cloud diagrams so that you can write cloud formation code based on interpreting the diagrams.