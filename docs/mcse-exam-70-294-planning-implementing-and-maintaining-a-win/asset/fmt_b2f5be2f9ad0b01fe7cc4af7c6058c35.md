
## Self Test Questions

B. You must delete the class that has the mistake and simply create the appropriate `Class` object.

C. You must wait 24 hours before you can delete any new classes in the schema. You can then delete the class and create the corrected `Class` object.

D. You can go in and fix the existing `Class` object without having to recreate the object.

13. You have an office with three locations separated by 56 K WAN links. You are experiencing slow queries when looking for objects in the Active Directory. You have one GC server at your main office. What can you do to improve the query performance?

A. Add GC servers to your other two locations.

B. Add DCs that are not GC servers to your other two locations.

C. Add a DNS server for faster resolution at your other two locations.

D. Add another OU to the directory to separate the locations by OU.

14. You have been experiencing a large amount of processor utilization on your GC server. Your network consists of one location with 2500 users. You currently have three DCs for fault tolerance and load balancing. What can you do to help with your GC server processor utilization?

A. Add a fourth DC to the network.

B. Add another GC server to the network to offload some of the traffic.

C. Remove one DC from the network.

D. Split your network into three OUs with less than 1000 users each.

15. You are working on updating the schema and cannot associate an attribute with a class. What can you do to resolve this?

A. Add yourself to the schema Admins group.

B. Makes sure the Schema Operations Master is online and reachable.

C. Reload the schema in the Schema admin tool.

D. Move the role of Schema Operations Master.

## Self Test Quick Answer Key

For complete questions, answers, and explanations to the Self Test questions in this chapter as well as the other chapters in this book, see the Self Test Appendix.

1. D

2. B, C

3. A

4. B, C

5. A

6. C.

7. B

8. D

9. A

10. A

11. C

12. A

13. A

14. B

15. C

# Chapter 9 MCSA/MCSE 70-294: Working with Group Policy in an Active Directory Environment

## Exam Objectives in this Chapter:

[4 Planning and Implementation Group Policy](#B9781931836944500155.xhtml#s0015)

[4.2.1 Distribute software by using Group, Policy.](#B9781931836944500155.xhtml#s0015)

[4.3.1 Distribute software by using Group Policy.](#B9781931836944500155.xhtml#s0015)

[4.1 Plan Group Policy strategy.](#B9781931836944500155.xhtml#s0090)

[4.2.2 Automatically enroll user certificates by using Group Policy.](#B9781931836944500155.xhtml#s0190)

[4.2.3 Redirect folders by using Group Policy.](#B9781931836944500155.xhtml#s0190)

[4.3.2 Automatically enroll computer certificates by using Group Policy.](#B9781931836944500155.xhtml#s0190)

[4.1.2 Plan a strategy for configuring the user environment by using Group Policy.](#B9781931836944500155.xhtml#s0205)

[4.1.3 Plan a strategy for configuring the computer environment by using Group Policy.](#B9781931836944500155.xhtml#s0205)

[4.2 Configure the user environment by using Group Policy.](#B9781931836944500155.xhtml#s0205)

[4.2.4 Configure computer security by using Group Policy.](#B9781931836944500155.xhtml#s0205)

[4.3 Deploy a computer environment by using Group Policy.](#B9781931836944500155.xhtml#s0205)

[4.3.3 Configure computer security setting by using Group Policy.](#B9781931836944500155.xhtml#s0205)

[5 Managing and Maintaining Group Policy](#B9781931836944500155.xhtml#s0265)

[5.1 Troubleshoot issues related to Group Policy application deployment. Tools might include `RSoP` and the `gpresult` command.](#B9781931836944500155.xhtml#s0270)

[5.3 Troubleshoot the application of Group Policy security settings. Tools might include `RSoP` and the `gpresult` command.](#B9781931836944500155.xhtml#s0270)

[4.1.1 Plan a Group Policy strategy by using Group Policy. using Resultant Set of Policy (`RSoP`) Planning mode.](#B9781931836944500155.xhtml#s0095)

## Introduction

Group Policy is used to manage and control various features and components of the Windows Server 2003 network. Group Policy settings can be used to define users’ desktop environments, to specify security settings, and to configure and control application behavior. Group Policy can be used to automatically deploy software to users and computers. You can also use group policies to assign scripts and redirect folders. Policies can be applied to a site, a domain, an organizational unit (OU) or a local computer.

Because Group Policy is used for so many important management functions, it is important for network administrators to be intimately familiar with how Group Policy works, and how they can use it for more flexibility and control of network components.

This chapter starts with the basics of Group Policy terminology and concepts, introducing you to user and computer policies and Group Policy Objects (`GPOs`). We discuss the scope and application order of policies, and you’ll learn about Group Policy integration in Active Directory. We show you how to plan a Group Policy strategy, and then walk you through the steps of implementing Group Policy. We show you how to perform common Group Policy tasks, and discuss Group Policy propagation and replication. You’ll also learn best practices for working with Group Policy, and we’ll show you how to troubleshoot problems with Group Policy.

## Understanding Group Policy

![u09-01-9781931836944](images/B9781931836944500155/u09-01-9781931836944.jpg)

Group Policy is derived from the System Policies of the Windows NT days, and has been significantly enhanced, first in Windows 2000 and now again in Windows Server 2003. Implementing Group Policy in the Active Directory allows system administrators to control aspects of the user or service environment within the network from a global perspective.

You can use Group Policy to accomplish the following tasks, among others:

■ Assign scripts You can specify scripts that will run at login, logoff, startup, shutdown, and other times.

■ Manage applications You can designate applications that will be installed on, updated on, or removed from computers.

■ Redirect folders You can specify alternate locations for system folders, such as My Documents, My Pictures, and others.

■ Change Registry settings You can designate a set of Registry settings that will be applied to the local computer when a user logs on.

Gaining a full understanding of how Group Policy can impact the network requires a full understanding of the terminology and concepts.

### Terminology and Concepts

You will encounter a number of terms, acronyms, and jargon when designing and implementing a group policy in your organization. Although some of the terms can be confusing at first, after you’ve had a chance to really work with policies, you will be able to navigate through even the most complex policy implementations.

Of course, when we refer to Group Policy, we are actually talking about the superset of all the individual components that make up the larger whole. You will find policy elements that affect only users or computers, policies that are set at the workstation level or applied to an OU in Active Directory, and ways to apply basic security to policies. Let’s start with the basic terms used as the foundation of building Group Policy.

#### Local and Non-Local Policies
