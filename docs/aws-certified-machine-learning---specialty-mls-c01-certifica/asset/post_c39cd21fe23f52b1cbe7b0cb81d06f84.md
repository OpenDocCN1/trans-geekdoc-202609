
## Create function

Choose one of the following options to create your function.

- **Author from scratch**
  Start with a simple Hello World example.
- **Use a blueprint**
  Build a Lambda application from sample code and configuration presets for common use cases.
- **Container**
  Select a

## Basic information

Function name Enter a name that describes the purpose of your function. myFunctionName Use only letters, numbers, hyphens, or underscores with no spaces. Runtime Info Choose the language to use to write your function. Python 3.8 Permissions Info By default, Lambda will create an execution role with permissions to upload logs to Amazon CloudWatch Logs. You can customize this default role later when adding triggers.

## Change default execution role

- Execution role Choose a role that defines the permissions of your function. To create a custom role, go to the IAM console
- Create a new role with basic Lambda permissions
- Use an existing role
- Create a new role from AWS policy templates

Role creation might take a few minutes. Please do not delete the role or edit the trust or permissions policies in this role. Lambda will create an execution role named <myFunctionName>-role-vio40di, with permission to upload logs to Amazon CloudWatch Logs.

## Advanced settings

## Code signing

Code signing configuration - optional Info To enable code signing, choose a configuration that defines the signature validation policy and the signing profiles that are permitted to sign code. Choose a code signing configuration ARN

## Network

To provide network access for your Lambda function, specify a virtual private cloud (VPC), VPC subnets, and VPC security groups. VPC configuration is optional unless your user permissions require you to configure a VPC. VPC - optional Info Choose a VPC for your function to access. Choose a VPC

Figure 10.1 – Creating a new Lambda function from the AWS Lambda console

Here, you have a very important configuration that you should remember during your exam – the execution role. Your Lambda function might need permissions to access other AWS resources, such as S3, Redshift, and more. The execution role grants permissions to your Lambda function so that it can access resources as needed.

You have to remember that your VPC and security group configurations will also interfere with how your Lambda function runs. For example, if you want to create a function that needs internet access to download something, then you have to deploy this function in a VPC with internet access. The same logic applies to other resources, such as access to relational databases, Kinesis, and Redshift.

Furthermore, to properly configure a Lambda function, you have to, at least, write its code, set the execution role, and make sure the VPC and security group configurations match your needs. Next, you will take a look at other configurations.

## Completing your configurations and deploying a Lambda function

Once your Lambda is created in the AWS console, you can set additional configurations before deploying the function. One of these configurations is the event trigger. As mentioned earlier, your Lambda function can be triggered from a variety of services or even manually.

### IMPORTANT NOTE

> A very common example of a trigger is Amazon EventBridge. This is an AWS service where you can schedule the execution of your function.

Depending on the event trigger you choose, your function will have access to different event metadata. For example, if your function is triggered by a `PUT` event on S3 (for example, someone uploads a file to a particular S3 bucket), then your function will receive the metadata associated with this event – for example, the bucket name and object key. Other types of triggers will give you different types of event metadata!

You have access to that metadata through the event parameter that belongs to the signature of the entry point of your function. Not clear enough? You will now look at how your function code should be declared, as follows:

```
def lambda_handler(event, context) :
    TODO
```

Here, `lambda_handler` is the method that represents the entry point of your function. When it is triggered, this method will be called, and it will receive the event metadata associated with the event trigger (through the `event` parameter). That is how you have access to the information associated with the underlying event that has triggered your function! The `event` parameter is a JSON-like object.

If you want to test your function but do not want to trigger it directly from the underlying event, that is no problem; you can use **test events**. They simulate the underlying event by preparing a JSON object that will be passed to your function.

_Figure 10.2_ shows a very intuitive example. Suppose you have created a function that is triggered when a user uploads a file to S3, and now, you want to test your function. You can either upload a file to S3 (which forces the trigger) or create a test event.

By creating a test event, you can prepare a JSON object that simulates the S3-put event and then pass this object to your function:

![](img/87c29232224b00f5a8bba6a66a391700_283_0.png)

Figure 10.2 – Creating a test event from the Lambda console

Another type of configuration that you can set is an environment variable, which will be available on your function. Figure 10.3 shows how to add environment variables in a Lambda function:

## Edit environment variables

## Environment variables

You can define environment variables as key-value pairs that are accessible from your function code. These are useful to store configuration settings without the need to change function code. Learn more

| Key | Value |
|---|---|
| env | prod |

Add environment variable

Encryption configuration

Figure 10.3 – Adding environment variables to a Lambda function

You can always come back to these basic settings to make adjustments as necessary. Figure 10.4 shows what you will find in the basic settings section:

## Edit basic settings

## Basic settings Info

Description - optional

Memory (MB) Info
Your function is allocated CPU proportional to the memory configured.
128 MB
Set memory to between 128 MB and 10240 MB

Timeout
15 min 0 sec

Execution role
Choose a role that defines the permissions of your function. To create a custom role, go to the IAM console.
Use an existing role
Create a new role from AWS policy templates

Existing role
Choose an existing role that you’ve created to be used with this Lambda function. The role must have permission to upload logs to Amazon CloudWatch Logs.

Figure 10.4 – Changing the basic settings of a Lambda function

You can access log information by navigating through your Lambda function monitoring section and clicking on **View logs in CloudWatch**.

In CloudWatch, each Lambda function will have a log group and, inside that log group, many **log streams**. Log streams store the execution logs of the associated function. In other words, a log stream is a sequence of logs that share the same source, which, in this case, is your Lambda function. A log group is a group of log streams that share the same retention, monitoring, and access control settings.

You are now reaching the end of this section, but not the end of this topic on Lambda functions. As mentioned earlier, this AWS service has a lot of use cases and integrates with many other services. In the next section, you will look at another AWS service that will help orchestrate executions of Lambda functions. This is known as **AWS Step Functions**.

## Working with step functions

Step Functions is an AWS service that allows you to create workflows to orchestrate the execution of Lambda functions. This is so that you can connect them in a sort of event sequence, known as **steps**. These steps are grouped in a **state machine**.

Step Functions incorporates retry functionality so that you can configure your pipeline to proceed only after a particular step has succeeded. The way you set these retry configurations is by creating a **retry policy**.

### IMPORTANT NOTE

Just like the majority of AWS services, AWS Step Functions also integrates with other services, not only AWS Lambda.

Creating a state machine is relatively simple. All you have to do is navigate to the AWS Step Functions console and then create a new state machine. On the **Create state machine** page, you can specify whether you want to create your state machine from scratch or from a template, or whether you just want to run a sample project.

AWS will help you with this state machine creation, so even if you choose to create it from scratch, you will find code snippets for a various list of tasks, such as AWS Lambda invocation, SNS topic publication, and running Athena queries.

For the sake of demonstration, you will now create a very simple, but still helpful, example of how to use Step Functions to execute a Lambda function with the **retry** option activated:

```
{
"Comment": "A very handy example of how to call a lambda function with retry option",
"StartAt": "Invoke Lambda function",
"States": {
"Invoke Lambda function": {
"Type": "Task",
```
