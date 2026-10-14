
If you have taken the steps outlined earlier in this book (such as properly configuring your router and your firewall to reduce the impact of any attempted DoS), then you will already be alleviating some of the damage from DoS attacks. In addition, consider taking the following measures:

* Use your firewall logs or IDS to find out which IP address (or addresses) originated the attacks. Note the IP addresses and then (if your firewall supports this feature—and most do) deny that IP address access to your network.

* Use online resources (interNIC.net and so on) to find out who the address belongs to.

* Contact that organization and inform it of what is occurring.

* Log all of these activities and inform the appropriate organizational leaders.

* After you have dealt with the DoS attack and notified the appropriate people, have a meeting with appropriate IT staff to discuss what can be learned from this attack and how you might prevent it from occurring in the future.

#### Intrusion by a Hacker

What do you do if a malicious hacker has intruded into your network? In other words, what are the basics of incident response? Consider taking the following measures in the event of intrusion by a hacker:

* Immediately copy the logs of all affected systems (firewall, targeted servers, and so on) for use as evidence.

* Immediately scan all systems for Trojan horses, changes to firewall settings, changes to port filtering, new services running, and so on. In essence, you need to perform an emergency audit to see what damage has been done.

* Document everything. Of all of your documentation, this must be the most thorough. You must specify which IT personnel took what actions at what times. Some of this data may be part of later court proceedings, so absolute accuracy is necessary. It is probably a good idea to log all activities taken during this time and to have at least two people verify and sign the log.

* Change all affected passwords. Repair any damage done.

* Inform the appropriate business leaders of what has happened.

* After you have dealt with the breach and notified the appropriate people, you should have a meeting with appropriate IT staff to discuss what can be learned from this breach and how you might prevent another one from occurring in the future.

These are just general guidelines, and some organizations may want to take much more specific actions in the event of some security breach. You should also bear in mind that throughout this book when we have discussed various sorts of threats to network security, we have mentioned particular steps and policies that should be taken. The policies in this chapter are meant to be in addition to any already outlined in this book. It is an unfortunate fact that some organizations have no plan for what to do in case of an emergency. It is important that you do have at least some generalized procedures you can implement.

### Defining Access Control

An important area of security policies that usually generates some controversy in any organization is access control. There is always a conflict between users’ desire for unfettered access to any data or resources on the network and the security administrator’s desire to protect that data and resources. This means that extremes in policies are not practical. You cannot simply lock down every resource as completely as possible since doing so would impede users’ access to those resources. Conversely, you cannot simply allow anyone and everyone complete access to everything. The core of access control is the concept of least privileges, introduced in [Chapter 1](#ch01.xhtml#ch01), “[Introduction to Computer Security](#ch01.xhtml#ch01).” According to this concept, each person is given the minimum privileges necessary to do her job—no more and no less.

The idea of least privileges is simple: Each user, including IT personnel, gets the least access he can have and still effectively do his job. Rather than ask the question, “Why not give this person access to X?” you should ask, “Why give this person access to X?” And if you don’t have a very good reason, then don’t. This is one of the fundamentals of computer security. The more people who have access to any resource, the more likely some breach of security is to occur.

Along with, and related to, least privileges is the concept of implicit deny. Implicit deny means that all users are implicitly denied access to network resources until an administrator explicitly grants them.

Separation of duties, job rotation, and mandatory vacations are also important and related concepts. Separation of duties means that no one person can perform critical tasks; at least two individuals are needed. This prevents one person from accidently (or intentionally) causing some security breach via inappropriate use of critical functions. Both job rotation and mandatory vacations are used to make sure that, periodically, the person performing a given job changes. This makes it more difficult for one person to exploit her position to breach security.

Obviously, trade-offs must be made between access and security. Examples abound. One common example involves sales contact information. Clearly, a company’s marketing department needs access to this data. However, what happens if your competitors get all of your company’s contact information? That could allow them to begin targeting your current client list. This requires a trade-off between security and access. In this case, you would probably give salespeople access only to the contacts that are within their territory. No one other than the sales manager should have complete access to all the marketing data.

### Development Policies

Many IT departments include programmers and web developers. Unfortunately, many security policies do not address secure programming. No matter how good your firewalls, proxy server, virus scanning, and policies are, if your developers create code that is flawed, you will have security breaches. Clearly, the topic of secure programming could fill its own separate volume. Nonetheless, we can consider a brief checklist for defining secure development policies. If your company currently has no secure programming initiatives, using this checklist is certainly better than developing in a vacuum. It can also serve as a starting point to get you thinking and talking about secure programming:

* All code, especially code written by outside parties (contractors, consultants, and so on) must be checked for backdoors/Trojan horses.

* All buffers must have error handling that prevents buffer overruns.

* All communication (such as using TCP sockets to send messages) must adhere to your organization’s secure communications guidelines.

* Any code that opens any port or performs any sort of communication needs to be thoroughly documented, and the IT security unit must be apprised of the code, what it will do, and how it will be used.

* All input should be filtered for items that might facilitate an attack, such as an SQL injection attack.

* Every vendor should supply you with a signed document verifying that there are no security flaws in its code.

Following these guidelines will not guarantee that flawed code will not be introduced into your system, but it will certainly lower the odds significantly. And the unfortunate fact is that these simple steps alone are more than most organizations are taking. A very good place to look at security policies is the SANS Institute ([www.sans.org/security-resources/policies/](http://www.sans.org/security-resources/policies/)).

### Standards, Guidelines, and Procedures
