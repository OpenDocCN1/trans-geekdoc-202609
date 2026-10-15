
IT security is a constantly moving target. As difficult as it’s been to manage last year’s threats, you know there’s a whole new batch coming right behind them. As a business, you’re already responsible for protecting the workstations and networking hardware running in your office along with securing your organization’s data and code your developers put into your apps. The integrity of your underlying server infrastructure is just one more potential area of vulnerability for you to worry about.

No matter how good your IT security team is, they’re probably not better informed, equipped, and trained than their counterparts at a major cloud provider. Because AWS is so good at what it does—and because it takes responsibility for the security of its platform’s underlying networking and compute infrastructure—this is one area where outsourcing will usually make sense.

This won’t relieve you of all worries. As you’ll see in Chapter 4, “Understanding the AWS Environment,” the terms of the AWS Shared Responsibility Model mean that, in many cases, the security and integrity of the resources you run *on* the cloud are still your problem. But *the cloud itself* is managed by AWS.

### Metered Payment Model

One of the defining characteristics of any public cloud computing platform is the way it automatically allocates resources to meet client requests. Practically, this means that you can, for instance, log in to the AWS browser console, and define and launch a virtual server (called an *instance* in the AWS world), and moments later your new instance will be ready for you. There’s no need to wait for manual intervention by AWS employees.

The flexibility of the self-serve system permits usage patterns that would have been impossible using traditional compute paradigms. Let’s say you need to quickly test a possible application configuration you’re working on. In the old days, even if the test lasted only an hour, you would still need to find free capacity on a physical server in the server room. Once the test ended, you’d still be paying the maintenance and ownership costs of that server capacity even if it was idle.

In the cloud, by contrast, you fire up an instance, run it for the length of time your test requires, and then shut it down. You’ll be billed for only that testing time, which, in some cases, could cost you a fraction of a penny.

Since there’s no human processing involved in cloud compute billing, it’s as easy for a provider to charge a few pennies as it is thousands of dollars. This metered payment makes it possible to consider entirely new ways of testing and delivering your applications, and it often means your cost-cycle expenses will be considerably lower than they would if you were using physical servers running on-premises.

Comparing the costs of cloud deployments against on-premises deployments requires that you fully account for both capital expenses (*capex*) and operating expenses (*opex*). On-premises infrastructure tends to be very capex-heavy since you need to purchase loads of expensive hardware up front. Cloud operations, on the other hand, involve virtually no capex costs at all. Instead, your costs are ongoing, consisting mostly of per-hour resource “rental” fees.

You’ll learn more about AWS billing in Chapter 2, “Understanding Your AWS Account.”

## Server Virtualization: The Basics

The secret sauce that lets cloud providers give their customers on-demand compute resources in such a wide range of configurations is virtualization. When you request a *virtual machine* (VM) with a particular processor speed, memory capacity, and storage size, AWS doesn’t send some poor engineer running through the halls of its data center looking for an available machine with exactly that profile. Rather, as you can see illustrated in [Figure 1.1](#c01.xhtml#figure1-1), AWS carves the necessary resources from larger existing devices.

![FIGURE 1.1 VMs accessing storage and compute resources from their host server ](images/c01f001.jpg)

[**FIGURE 1.1**](#c01.xhtml#figureanchor1-1) VMs accessing storage and compute resources from their host server 

A 5 TB storage drive could, for instance, be divided into dozens of smaller virtual volumes, each associated with a different virtual server (or instance). And the resources of a single physical server could be invisibly shared between multiple instances. The operating systems installed on each of those instances could run, blissfully unaware that they’re actually only masters over a small subset of a much larger server environment.

The virtualization model offers two compelling benefits:

*   **Speed:** Defining, purchasing, provisioning, testing, and launching a new physical server can take months. Even a simple reboot can keep you waiting for a couple of minutes. The time lag between requesting a new cloud-based VM and logging in and getting to work can be seconds, but never more than a few minutes. Restarting a VM can sometimes happen faster than you can type your login details.

*   **Efficiency:** It’s rare to find a nonvirtualized physical server that utilizes anywhere near 100 percent of its capacity. More likely, either it’ll spend its time running mostly empty or it’ll be badly overused while you wait for more capacity to come online. Multiple virtual machines, on the other hand, can be tightly packed onto a physical server running a hypervisor (a common technology for hosting VMs). When space opens up on one server, you can quickly fill it with another virtual workload. When a server reaches capacity, overflow workloads can be moved to another machine. And the more workloads you’re managing, the more flexible everything gets.

Amazon’s formidable scale and logistical abilities mean that it’s often able to leverage the benefits of virtualization to provide both superior performance and pricing.

## Cloud Platform Models

Cloud services come in more than one flavor. Choosing the one that’s right for your project will depend on your specific needs and how much fine control you’ll need over the underlying gears and levers.

### Infrastructure as a Service

Infrastructure as a Service (IaaS) products generally simulate the look and feel you’d get from managing physical resources. IaaS products give you direct access to a provider’s compute, storage, and networking assets. Because it’s you that’s in there playing around at the hardware level, you—rather than the IaaS provider—are responsible for the consequences of any bad configurations. The trade-off is that you get to closely configure every layer of your operating stack.

You’ll learn much more about these examples later in the book, but AWS IaaS products include Elastic Cloud Compute (EC2) for virtual machine instances, Elastic Block Store (EBS) for storage volumes, and Elastic Load Balancing.

### Platform as a Service

Unlike IaaS, Platform as a Service (PaaS) products simplify the process of building an application by *hiding the complexity* of the infrastructure that runs it. You’re given an interface through which you define the behavior and environment you want for your application. This will often include the code that will run your application.

AWS PaaS products include Elastic Beanstalk and Elastic Container Service (ECS).

### Software as a Service

Software as a Service (SaaS) products offer services meant to be accessed by end users. An easily recognizable illustration is Google’s Gmail service, which allows users to manage their email by logging in to a browser interface or through an email client (like Microsoft Outlook) that’s running locally.

While some may disagree with the designation, AWS SaaS products arguably include Simple Email Service and Amazon WorkSpaces.

[Figure 1.2](#c01.xhtml#figure1-2) compares the scope of responsibility you have on IaaS, PaaS, and SaaS platforms with the way it works for on-premises deployments.
