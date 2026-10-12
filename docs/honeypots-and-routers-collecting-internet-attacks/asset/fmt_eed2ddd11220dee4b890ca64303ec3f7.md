
*   [3.](#09_Chapter04.xhtml#rfn3) S.G. Cheetancheri, Collaborative Defense against Zero-Day and Polymorphic Worms: Detection, Response and an Evaluation Framework, PhD thesis, University of California, Davis, CA, 2007, [http://www.cs.ucdavis.edu/](http://www.cs.ucdavis.edu/) research/tech-reports/2007/CSE-2007-38.pdf.
*   [4.](#09_Chapter04.xhtml#rfn4) M.M.Z.E. Mohammed and A.-S. K. Pathan. Automatic Defense against Zero-day Polymorphic Worms in Communication Networks, ISBN 9781466557277, CRC Press, Taylor & Francis Group, Boca Raton, FL, 2013.

# 5 A Theoretical Guide to Honeypots

**MOHSEN MOHAMED**

## 5.1 Honeypot Concepts

### 5.1.1 Introduction to Honeypots

It would be best to first define honeypot, and then talk about its history, which we deem to be an appropriate sequence of reading and understanding relevant critical information.

There are many definitions of honeypot.

The formal definition of honeypot given by Lance Spitzner [1, p. 58] is: “A honeypot is a security resource whose value lies in being probed, attacked, or compromised.”

We will now ask a series of questions to give explanations about honeypot’s definition. First of all, why do we need to make a honeypot?

*   We need honeypot to collect information about who is trying to compromise our system. How? The honeypot has tools that can keep traces of the source and destinations.
*   Honeypot can provide us with the information about which tools and tactics have been used by the attacker to compromise our system. Such information can be found in the techniques that have been used inside a honeypot such as firewall logs, intrusion detection systems (IDSs), and system logs. By getting this information, we can avoid such attacks in the future. How? By improving our system against these known attacks. This point (i.e., collecting information about tools and tactics) is considered as the most important goal of a honeypot. Because, anyone likes to make his system as complex as possible, so that it becomes more difficult for the attackers to compromise the system.
*   By using honeypot, we can get zero-day attacks (unknown attacks). We should mention that most of the honeypot users are researchers, because honeypot provides them with extensive information about various attacks and their patterns. There are other people as well who make honeypots for other goals like finding solution for the attack in a company, or simply as a test, or for a demonstration of the concept, and so on.

An interesting fact about honeypot is that there is no value of a honeypot if it is not attacked by the attacker! This is because, to capture information about the attacker, the honeypot must be compromised. Otherwise, it has no utility as it cannot provide the required information. This point explains why we need a honeypot. Then we can ask another question that is, how can we apply a honeypot to get attacked.

1.  First, we should put a honeypot in our real network as real machines or as software in a device.
2.  We should separate honeypot from other machines in the network using firewalls, routers, or other defense mechanisms. Why should we make such separation between honeypot and other machines? To safeguard other machines from the attackers.
3.  If we need to improve our defense systems, then in the honeypot, we should use the same defense systems that we are using in the others protected machines. Using the same defense systems in honeypot helps us to know how the attackers can compromise these defense systems, so that we can improve them. For example, if we want to discover zero-day attacks, we should use an updated IDPS, antivirus, and add supporting defense mechanisms. Because, these defense systems can filter out the known attacks, and then just unknown attack(s) will compromise our honeypot (which is our expectation). Therefore, we can reduce the heavy loads for our honeypot.
4.  Based on need, we can use weak defense systems in the honeypot or may not use any defense system at all, if we would like to trace an attacker and get information about how it causes damage. For example, if a government wants to trace who will try to compromise their systems, then they can use a honeypot with weak defense systems or no defensive mechanism at all. Therefore, the attacker will be lured and can easily compromise the government systems. Then, the government can trace this attacker. We should note that in this case, the attacker can at least guess it as a honeypot, because if a device with weak defense systems is setup, especially in a government institution, it is highly likely that it is a honeypot. The attackers are not stupid. Hence, such trap may not always work to entice the attackers, when it comes to government institution’s machines/computers.
5.  We should inform all the people in an organization when we setup a honeypot, so that they do not try to access it. Therefore, anything going out or coming into the honeypot should be considered as attacks. After a considerable amount of time, we can go to the honeypot and check what it has captured. Also, in real time, we can see what exactly is happening in the honeypot.

As should be apparent from these descriptions, honeypots are different than most security tools. Most of the security technologies used today are designed to address specific problems. For example, firewall is a technology that protects your organization by controlling what traffic can flow where. They are used as an access control tool. Firewalls are most commonly deployed around an organization’s perimeter to block unauthorized activity. Network IDSs are designed to detect attacks by monitoring either system or network activity.

Honeypots are different because they are not limited to solving a single, specific problem. Instead, honeypots are a highly flexible tool that can be applied to a variety of different situations. This is why the definition of honeypot may at first seem vague, because they can be used to achieve so many different goals and can come in a variety of different forms. For example, honeypots can be used to deter attacks, a goal shared with firewalls. Honeypots also can be used to detect attacks, similar to the functionality of an IDS. Honeypots can be used to capture and analyze automated attacks, such as worms, or act as early indication and warning sensors. Honeypots also have the capability to analyze the activities of the blackhat community, capturing the keystrokes or conversations of attackers. How you use honeypots is up to you. It depends on what you are trying to achieve. In [Chapter 6](#11_Chapter06.xhtml), we will go into far greater details on the different goals you can accomplish with a honeypot. However, all possible manifestations share one common feature: their value lies in being probed, attacked, or compromised.

It is important to note that honeypots do not contain valuable data. Instead, they contain some kind of fake data. Therefore, honeypots are the security resources that have no production value; no person or resource should be communicating with them. As such, any activity sent their way is a `suspect` by nature. Any traffic sent to the honeypot is most likely a probe, scan, or attack. Any traffic initiated by the honeypot means the system has most likely been compromised and the attacker is making outbound connections.
