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

## Infrastructure as Code

 allows you to describe and provision all the infrastructure resources in your cloud environment. You can stand up servers, databases, runtime parameters, resources, etc. based on scripts that you write. Infrastructure as Code is a time-saving feature because it allows you to provision (or stand up) resources in a reproducible way.

有点类似docker 的 yml部署

## Cloud Formation

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