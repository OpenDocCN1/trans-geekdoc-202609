
For proper functioning, it is essential to deploy an efficient security system or proactive plan to mitigate DDOS attacks. Such kinds of security systems are capable of scanning suspicious activity or behavior and offer a greater serenity. For evaluation purpose \[[32](#ch05.xhtml#ref5_32)\], you must depend on your reference model that indicates the source stream, performance, time period, and other crucial aspects for the mitigation of attacks. Such types of solutions are associated with your stream of data. They send network traffic with centers of dedicated cleaning that filter the malicious traffic and allow only the authorized data to pass in real time. These kinds of systems must be a part of your overall plan of response to incidents so that the anomalies are quickly identified and resolved.

### [5.2.8 Reduce the Attack Surface](#ch05.xhtml#c_sec5_002_008)

We should reduce the attacked surface area to minimize DDOS attacks, which can limit the options for attackers and gain protection in one place.

Protocols or applications that are not expected to be used for communication should not be exposed. It will help to reduce the expected points of attacks \[[33](#ch05.xhtml#ref5_33)\].

### [5.2.9 Plan the Scaling](#ch05.xhtml#c_sec5_002_009)

There are two important things in reducing the large-scale volumetric DDOS attacks: the capability of servers and bandwidth (or transit) capacity to absorb and prevent attacks. In the case of a server's capacity, DDOS attacks can be volumetric attacks that exhaust the resources of victim server, i.e., RAM, disk, and increased CPU utilization, etc. It is important to reduce computing resources. To do this, it can generate greater computing resources or features, such as improved networks or broader network functions that support larger volumes. Moreover, the use of load balancers is also common to monitor or transfer loads from one resource to another resource to prevent overloading a resource \[[34](#ch05.xhtml#ref5_34)\].

When you develop your applications, ensure that your host providers give ample redundant internet connection in case of transit capacity.

It will help in managing large amounts of data or traffic. Since DDOS attacks stop the availability of continuous services or applications, it is necessary to put them close to large internet points of exchange.

It will help users to access the applications easily during high volume of internet traffic.

*Know What Normal and Abnormal Traffic Is*:

Whenever there is a high volume of internet traffic, the host will accept only the amount of data that it can easily manage without affecting the availability of services.

This is called the rate limit. Latest mitigation technique only accepts the authorized amount of data after analyzing the packets individually \[[35](#ch05.xhtml#ref5_35),[36](#ch05.xhtml#ref5_36)\]. So, you need to gain accurate information about the data traffic the receiver usually receives. Moreover, many other techniques are already experimented with in our previous work \[[37](#ch05.xhtml#ref5_37),[38](#ch05.xhtml#ref5_38),[39](#ch05.xhtml#ref5_39),[40](#ch05.xhtml#ref5_40),[41](#ch05.xhtml#ref5_41),[42](#ch05.xhtml#ref5_42)\].

### [5.2.10 Implement Firewalls for Sophisticated Application Attacks](#ch05.xhtml#c_sec5_002_010)

It is good to use a web application firewall (`WAF`) against attacks of the type injection of SQL code. Moreover, in case of attack, you must be able to produce customized measures against malicious applications or coming from unexpected sources or invalid IP addresses, etc. To prevent attacks at the moment they execute, it can sometimes be useful to take special support to analyze traffic patterns and produce the personalized protective measures. As users, we are required to review the configuration of our firewalls or routers to detect false IPs coming from expected attackers. Normally, our internet service provider (`ISP`) ensures that our router is up to date with this configuration. On the other hand, organizations that offer these services must save both their network and their whole infrastructure to mitigate such attacks from affecting the performance of their work and, consequently, to their clients \[[43](#ch05.xhtml#ref5_43)\]. If a company is affected by a denial-of-service (`DOS`) attack, it will lose the trust of its clients and lose customers for its services.

## [5.3 Methodology](#ch05.xhtml#c_sec5_3)

DDOS attacks cause the unavailability of services to the legitimate users. They start from overall analysis of the work. In DDOS attacks, intruders or attackers execute attacks from multiple locations rather than a single one. Some local systems re controlled by the attacker. The attacker initially compromises and gains control over these local systems. Such a compromised system is known as a master or handler. Masters are then used to gain control over further compromised systems that are closed to the victim server. These systems are called slaves or DDOS agents. They further launch multiple attacks on victim servers, as shown in [Figure 5.2](#ch05.xhtml#fig5_2).

![Figure 5.2 DDOS attacks execution.](Images/fig5_2.jpg)

[Figure 5.2 DDOS attacks execution](#ch05.xhtml#Ffig5_2).

### [5.3.1 Introduction to Expert Honey Mesh System](#ch05.xhtml#c_sec5_003_001)

Hackers are always in search of vulnerabilities within the systems for the execution of attacks. Systems that are not sufficiently protected can be easy targets for hackers. In computer terms, a honey pot is a security mechanism with which administrators trap the hackers and cyberattacks are executed in vain \[[10](#ch05.xhtml#ref5_10)\]. A honey pot offers network services or application programs that attract the hackers and save the production system against possible damage. In practice, users gather server-side or client-side technologies to create honey pots \[12\].

### [5.3.2 Creation of Honey Pots](#ch05.xhtml#c_sec5_003_002)

Honey pots can be created on both sides as given below:

1. Creation of honey pots on the server side

   The basic idea of a honey pot on the server side is to lure attackers to separate parts of a computer system and keep them away from production servers within the networks.

2. Creation of honey pots on the server side

   A honey pot on the client side imitates application software that makes use of services on the server.

### [5.3.3 Implementation of Honey Pot](#ch05.xhtml#c_sec5_003_003)

Honey pot can be implemented in three zones.

1. In Front of the Firewall

   By placing it in front of the firewall, it ensures that the security of our internal network is not compromised at any time as our firewall will prevent the attack from going to our internal network.

2. Behind the Firewall

   This option allows us to control internal and external attacks of any kind; the main problem that this method presents is that it requires a specific configuration to leave access to the `honey pot`, but not to our network, which causes possible security failures in the traffic filtration.

3. In a Demilitarized Zone

   By positioning it here, it is possible to separate the `honey pot` from the internal network and the union with the servers, and this possibility allows us to detect both internal and external attacks with a small modification of the Firewall.

## [5.4 Proposed System](#ch05.xhtml#c_sec5_4)
