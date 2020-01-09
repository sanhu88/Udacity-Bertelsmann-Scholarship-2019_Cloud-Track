# infrastructure-as-code 

lesson 18 - 24

****

# lesson 18 AWS Management

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

