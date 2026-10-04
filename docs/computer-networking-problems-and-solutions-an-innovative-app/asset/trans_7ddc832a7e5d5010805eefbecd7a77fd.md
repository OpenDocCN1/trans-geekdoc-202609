

## 2
虽然许多工程师认为通过路由验证计算出的路径会提高路径上流量的安全性，但这种方法似乎存在一些问题，其中一些问题在 `RFC5123` 中有所概述。解释你认为路由安全与网络中流量安全之间有什么关系。

## 3
文中将 `RADIUS` 称为 `AAA` 的一种形式；再找一种 `AAA` 的形式并简要描述它。

## 4
什么是入侵检测系统？描述它的作用。

## 5
什么是数据外泄检测系统？描述它的作用。

## 6
如果单播 `RPF` 在全球互联网中能有效阻止攻击，为什么如此少的提供转接连接的全球互联网提供商部署它？

### References
[1](#ch21.xhtml#ch21fn1). “EANS-Adhoc: FACC AG / UPDATE: FACC AG - Cyber-Fraud.”
[2](#ch21.xhtml#ch21fn2). Leary, “UCF Data Breach.”
[3](#ch21.xhtml#ch21fn3). CNN and Mallonee, “Hackers Publish 20,000 FBI Employees’ Contact Information.”
[4](#ch21.xhtml#ch21fn4). Leary, “IRS Data Breach Grows.”
[5](#ch21.xhtml#ch21fn5). “Data Breach Affects 80,000 UC Berkeley Faculty, Students and Alumni.”
[6](#ch21.xhtml#ch21fn6). “Premier Healthcare Faces Possible Data Breach That Could Affect 200,000 Patients.”
[7](#ch21.xhtml#ch21fn7). Leary, “Verizon Enterprise Data Breach.”
[8](#ch21.xhtml#ch21fn8). Gorrell, “Salt Lake County Data Breach Exposed Info of 14,200 People.”
[9](#ch21.xhtml#ch21fn9). McKinney, “Data Breach Exposes Information on More than 3,000 TCC Employees.”
[10](#ch21.xhtml#ch21fn10). Muncaster, “Every Voter in Philippines Exposed in Mega Hack.”
[11](#ch21.xhtml#ch21fn11). Siciliano, “Yahoo Data Breach: Almost 500 Million Affected”; “1 Billion Yahoo Accounts Compromised in Data Breach | IdentityForce.
[12](#ch21.xhtml#ch21fn12). Khandelwal, “World’s Largest 1 Tbps DDoS Attack Launched from 152,000 Hacked Smart Devices.”

# Chapter 22
## Network Design Patterns

### Learning Objectives

When you are finished reading this chapter, you should understand:

![Image](graphics/bull.jpg) The relationship between business problems and network design

![Image](graphics/bull.jpg) The different network ownership models

![Image](graphics/bull.jpg) How network investment cycles relate to waste

![Image](graphics/bull.jpg) What a choke point is and how it is used in network design

![Image](graphics/bull.jpg) How hierarchical design is used

![Image](graphics/bull.jpg) Common network topologies

![Image](graphics/bull.jpg) The concepts of planar, nonplanar, and regular topologies

After “yet another outage,” a large service provider called on its primary vendor with a demand: *send these 16 (specific, by name) people to our office for one week so they can redesign our network and prevent this kind of outage from ever happening again*. On hearing of the plan, one of the 16 engineers chosen for the “field trip” convinced the vendor’s management not to send such a large group of designers in to rebuild this network. The reason? *When you get 16 designers in a room, what you will have is 1 person drawing on the white board, and the other 15 erasing*.

This story encapsulates one of the primary truths about network design: there is no *one right way* to design a network. Of course, there are *better* designs and *worse designs*, but the protocols and systems that networks are built out of are designed to be very forgiving in the face of imperfect conditions. If they were not, networks would be very fragile, failing completely with the first network device or link failure. So, given you can pretty much “slap stuff together” and “make it work,” what makes a design better or worse? This chapter will focus on answering this question.

Getting to the answer, however, will require working through a range of ideas and concepts, beginning with the problem space itself.

### The Problem Space

What problem are designers trying to solve? While this might seem like an obvious question, it is far too often forgotten in the design process. What generally happens is this:

1. Engineers are given a set of objectives to fulfill.
2. A rough sketch is made of two or three possible solutions.
3. These two or three solutions are considered and compared at a technical level.
4. A solution is chosen, and the equipment and configurations are determined and deployed.

This is not a *bad* process, necessarily; rather, this process tends to take some points that should be considered in every step and push them into a “corner.” Once the first stage is passed, it is *never revisited*. Just like security is often left to the last, the larger questions of network design are often pushed to the first part of the process, and forgotten about when the real “geek-level stuff” of selecting equipment and building configurations arrives. It is better to use the basic problem set as a backdrop in *every* stage of the design.

#### Solving Business Problems

The network exists to solve business and real-world problems. When you are in the thick of choosing which forwarding engine is better, or which network software package has the greatest number of features, what is the fundamental question that network design needs to answer—the one that should be kept in mind at every stage of the design process?

`What is the least expensive and most flexible way to provide transport for the applications required to solve a real-world problem?`

This single question has many components, of course; it is worth looking at some of them in more detail.

What does the least expensive really mean? This is actually a difficult question with many different facets—and any answer given is probably the result of a good deal of crystal ball gazing and reliance on assumptions. Some expenses that engineers often remember to include are

• **Hardware:** The cost of the actual, physical devices, cabling, power, racks, and other gear required to physically build the network. This should include the cost of physical devices to connect the network through providers, for instance, spare equipment and tools.

• **Software:** The cost of licenses for the network operating system, routing stack, monitoring tools, and any ongoing maintenance costs.

• **Services:** The cost of having a technical assistance center to call, design services, offsite backup services, etc.

These kinds of costs, both in terms of capital expenses (`CAPEX`) and operational expenses (`OPEX`) are generally well understood, even if they are difficult to predict. A number of costs, however, are not generally included in any sort of planning, nor are they even well understood.

Many of these can be described as different forms of opportunity costs, and they often revolve around difficult operations and network modification driven by design complexity. Specifically, during the time it takes to bring the network up, modify the network, or troubleshoot and repair the network when there is a failure, the network is either not operational or is not fully supporting the business.

