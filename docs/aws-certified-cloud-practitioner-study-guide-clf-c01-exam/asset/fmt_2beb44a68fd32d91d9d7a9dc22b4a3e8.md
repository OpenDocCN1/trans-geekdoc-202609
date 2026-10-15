
![FIGURE 1.2 The breakdown of responsibility across multiple infrastructure types ](images/c01f002.jpg)

[**FIGURE 1.2**](#c01.xhtml#figureanchor1-2) The breakdown of responsibility across multiple infrastructure types 

### Serverless Workloads

Besides doing an excellent job emulating traditional server behavior, cloud providers can also enable entirely new ways to administrate applications and data. Perhaps the most obvious example is serverless computing.

Now don’t be fooled by the name. You can’t run a compute function without a computer environment (a “server”) somewhere that’ll host it. What “serverless” does allow is for individual developers to run their code for seconds or minutes at a time on some else’s cloud servers.

The serverless model—as provided by services like AWS Lambda—makes it possible to design code that *reacts* to external events. When, for instance, a video file is uploaded to a repository (like an AWS S3 bucket or even an on-premises FTP site), it can trigger a Lambda function that will convert the file to a new video format. There’s no need to maintain and pay for an actual instance running 24/7, just for the moments your code is actually running. And there’s no administration overhead to worry about.

## Scalability and Elasticity

The world’s largest public cloud providers can accomplish a great deal through combining the wonders of server virtualization with the power that comes from owning vast data centers filled with racks upon racks of hardware resources. Elasticity and scalability are the two key principles through which a lot of this happens, and understanding exactly what they mean can help you optimize your design choices so you’ll get the most bang for your cloud buck.

Note that there really are no precise and authoritative definitions for scalability and elasticity in the context of cloud computing—and any definitions you do see are bound to involve at least some overlap. Nevertheless, building some kind of picture in your mind of how these two principles work can be valuable.

### Scalability

A scalable service will automatically grow in capacity to seamlessly meet any changes in demand. A well-designed cloud-based operation will constantly monitor the health of its application stack and respond whenever preset performance metrics might soon go unmet. The response might include automatically launching new server instances to add extra compute power to your existing cluster. But it will probably also involve prepopulating those instances with the application data and configuration settings they’ll need to actually serve your application to your clients.

A large cloud provider like AWS will, for all practical purposes, have endless available capacity so the only practical limit to the maximum size of your application is your organization’s budget (and default service limits imposed by AWS that you’ll learn about later in Chapter 2).

Just how big is AWS? Well, if it can handle the capacity stresses required to keep millions of Netflix customers happy—and if you’ve ever watched a movie on the AWS-hosted Netflix, then you know it can—then AWS will surely be able to keep up with whatever trouble your applications send its way.

### Elasticity

You can stretch an elastic band far beyond its resting state. But part of what makes it truly elastic is the fact that, when you let go of it, it immediately returns to its original size. The reason the word *elastic* is used in the names of so many AWS services (Elastic Compute Cloud, Elastic Load Balancing, Elastic Beanstalk, and so on) is because those services are built to be easily and automatically resized.

Generally, you set the maximum and minimum performance levels you want for your application, and the AWS service(s) you’re using will automatically add or remove resources to meet changing usage demands. By way of illustration, a scalable ecommerce website could be configured to function using just a single server during low-demand periods, but any number of additional servers could be automatically brought online as demand spikes. When demand drops back down, unused servers will be shut down automatically.

Assuming you don’t already have one, now is the time to create your own AWS account. Working through the rest of this book will be pretty much impossible without an active account. You will have to provide a credit card, but you won’t be charged anything unless you actually launch an actual resource. Work through Exercise 1.1 to make this happen.

Once you’re fully activated, you’ll receive another email, this one confirming that your account is ready for you.

## Summary

The size and quality of a major cloud provider like AWS means that its customers can often benefit from higher-quality security, availability, and reliability than they could provide locally.

While AWS customers are still responsible for the applications they run in the cloud, they don’t need to worry about the underlying physical infrastructure that’s managed by AWS.

Much of the attraction of cloud computing is the ability to pay for only the services you use, and only as you use them. This allows the provisioning of sophisticated applications with virtually no capital expenses (capex). You will, of course, need to assess and manage the operating expenses (opex).

Server virtualization makes it possible to more densely pack software operations on physical hardware, potentially driving down the costs and improving the time-to-deployment of compute workloads. An even more “virtualized” kind of virtualization is serverless computing, where customers are aware their code and the network events that trigger it.

Cloud-optimized workloads are designed to take advantage of the scalability and elasticity of cloud platforms.

## Exam Essentials

**Understand how a large and geographically dispersed infrastructure improves service quality.** The sheer scale and geographic redundancy of the physical compute and networking resources owned by AWS mean that the company is able to guarantee a level of reliability and availability that would be hard to reproduce in any other environment.

**Understand how metered, pay-per-use pricing makes for flexible compute options.** Access to cloud infrastructure—sometimes for pennies per hour—makes it possible to experiment, sandbox, and regularly reassess and update application stacks.

**Understand that cloud services come on a wide range of forms.** IaaS gives you near-full control over virtualized hardware resources, closely emulating the way you would administrate actual physical servers. PaaS products abstract the underlying infrastructure, providing a simplified interface for you to add your application code. SaaS products provide services over a public network directly to end users.

**Understand how serverless computing can be both cheap and efficient.** Serverless services like AWS Lambda allow you access to AWS compute power for up to 15 minutes for a single function. This lets you operate code in response to real-time event triggers.

**Understand how scalability allows applications to grow to meet need.** A cloud-optimized application allows for automated provisioning of server instances that are designed from scratch to perform a needed compute function within an appropriate network environment.

**Understand how elasticity matches compute power to both rising and falling demand.** The scaling services of a cloud provider—like AWS Auto Scaling—should be configured to force compliance with your budget and application needs. You set the upper and lower limits, and the scaler handles the startups and shutdowns to optimize operations in between those limits.

## Review Questions

1.  Which of the following does not contribute significantly to the operational value of a large cloud provider like AWS?

    1.  Multiregional presence

    2.  Highly experienced teams of security engineers

    3.  Deep experience in the retail sphere
