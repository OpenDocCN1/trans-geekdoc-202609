
Enter DevOps. DevOps grew out of the need to safely automate web-scale applications. When your application needs to scale to support millions of users, the only way to accomplish that is with automation. Human hands typing on keyboards are a nonstarter. In addition, when your application provides service to millions of people, the consequence of error starts to become astronomical. At the very least, a large-scale disruption could be measured in many millions of dollars and could well be an existential event for many businesses.

## What Is DevOps?

For our purposes, we define DevOps as a combination of culture, tools, and processes aimed at:

* Accelerating delivery of new services
* Improving the scale of services
* Improving the quality of services
* Lowering risk when doing all these things

## Automation

One of the underlying themes of DevOps is automation. Having humans in the loop can produce many undesirable outcomes, such as infrastructure that is slow to adapt and frequent disruption to the business. Today’s enterprise IT department often has well-defined instructions in place to lower the risk of disruption as changes are made to infrastructure. However, these processes are typically spelled out in a Word document, and humans are expected to accurately follow the steps. In a nutshell, DevOps seeks to automate this process at every stage from, for example, change request to functional test to security test to change approval and, finally, deployment to production.

## Infrastructure as Code

Another recurring theme of DevOps is the notion of representing your infrastructure as “code.” In practice, infrastructure as code means using tools like Ansible or Terraform to describe your infrastructure in human-readable text files, usually in a format such as HCL, JSON, or YAML, and then using those files to provision the compute, storage, networking, security, and so on required for a particular application. A few key advantages to this approach are as follows:

* Being able to represent infrastructure in text files means that you can leverage common version control tools, such as Git, to track changes, keep backups, and collaborate with others in a manageable way.
* Generally speaking, the formats used to describe infrastructure as code are designed to be human readable, allowing a human to quickly make changes to infrastructure by editing a file directly or programmatically.
* Describing infrastructure as code means that it is repeatable. Infrastructure can be provisioned once, twice, or a thousand times, and it will be deployed the same way each time.

## CI/CD

Continuous integration/continuous deployment (CI/CD) is a DevOps process that is central to achieving many of its goals, including accelerating delivery, improving quality, and lowering risk.

Continuous integration (CI) is the process of continually integrating changes made to applications, services, or infrastructure into a “main” or up-to-date branch. Building on the notion of infrastructure as code, automation is used to instantiate a copy of the application, service, or infrastructure in a test environment and run a series of unit or functional tests anytime a change is detected. If all tests pass, then the change is integrated into the current “main” branch; otherwise, it is rejected.

Continuous deployment (CD) takes the process one step further and, upon successful completion of all unit and functional tests, automatically deploys the change into production. For new applications or services, CI is usually enabled first, and then, after a certain level of comfort is reached that the process is functioning correctly and the tests are comprehensive enough, CD is enabled.

## Apps vs. Infrastructure

The argument is sometimes made that apps and infrastructure are so different that perhaps DevOps cannot be effectively applied to infrastructure. Infrastructure is indeed different. Network infrastructure, in particular, is often made up of physical hardware. Provisioning physical hardware is not as easy as, say, provisioning fully virtualized networking in AWS.

Taking CI/CD as an example, in the web application space, it is easy to instantiate an application for testing in a cloud environment using infrastructure as code. The tools and platforms support dynamic provisioning, or even dynamic reconfiguring of infrastructure on demand. Being able to dynamically reconfigure and recable physical network topologies is not feasible. This has traditionally been one of the main reasons that CI/CD has not been adopted for network infrastructure.

However, over the last several years, major improvements have been made in this area. Now we have platforms like Cisco Modeling Labs (CML) that allow us to dynamically provision arbitrary network topologies and reconfigure those topologies on the fly. In addition, we have access to an ever-increasing number of virtual network functions (VNFs) that enable us to simulate network topologies with greater fidelity. With these new capabilities, we can now simulate network topologies and start to consider real CI/CD applied to network infrastructure. If Bob had the ability to at least simulate the production network, it would have significantly reduced his risk of an outage during the maintenance window.

## Harnessing Automation-at-Scale

IT infrastructure teams have traditionally been skeptical of automation and for good reason. The speed and scale that are now achievable with automation have tremendous benefits and add real value to the business, but they also increase the consequence of error and, therefore, risk. Put another way, automation allows operators to crater IT infrastructure faster, and more completely, than they’ve ever cratered it before.

Remember that DevOps was created out of the need to harness automation at scale for this very reason. Web-scale applications need automation to achieve the agility and scale required, but they also have a need for stability, predictability, and low-risk injection of change into the environment. When we marry automation with infrastructure as code and wrap it in CI/CD processes, we can reconcile these two competing needs and start to deliver real value to the business.

## Why Are Enterprise IT Departments Not Adopting DevOps?

If the reasons to adopt DevOps are so compelling, then it should follow that IT departments everywhere would already be using it to better deliver apps, services, and infrastructure. The reality is many IT departments are starting to get their feet wet with DevOps applied to applications, but most IT services and infrastructure are still operated in the same way they have been for the last 30 years. The reasons for this fall into two categories: human factors and business factors. The sections that follow explore each of these factors in more detail.

## Human Factors

This section explores the human factors that can limit the adoption of DevOps in enterprise IT.

### Inertia

IT departments are risk averse. The reason is that they are tasked with keeping the business running, meeting compliance requirements, and securing the business, all while operating with a high consequence of error. Working under these conditions means they have a lot of inertia. Things are currently working as they are, and to change the operating model would mean injecting risk into the environment. If change is risky and risk is unacceptable, then the best course of action is to stick with the status quo.

DevOps is the key to enable speed, scale, and agility but also to do these things safely. As IT professionals become more aware of this fact, DevOps will be seen as a way to accelerate business while also lowering risk. However, even if this notion were universally understood and IT professionals wanted to implement DevOps today, they would still have another big problem, and that is the skills gap.

### The Skills Gap
