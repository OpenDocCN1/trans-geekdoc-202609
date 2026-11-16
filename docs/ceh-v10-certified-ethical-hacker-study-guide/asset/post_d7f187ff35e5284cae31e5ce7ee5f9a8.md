
You can take advantage of this by using a command delimiter. This means knowing the operating system that underpins the web application. This is because the command delimiter on Linux is different from that on Windows. On Linux, which is the operating system under the web page in Figure 12.3, the string entered was 127.0.0.1; cat /etc/passwd. The semicolon (;) was used to terminate the command ping 127.0.0.1 before running the second command, cat /etc/passwd. On a Windows system, the semicolon is used to separate parameters. Instead, you would use the ampersand (&) between commands through the Windows command processor.

With both Windows and Linux, you can use Boolean operators between commands. This conditions the execution of the second command on the success of the first. As an example, ping -c 5 127.0.0.1 && cat /etc/passwd would mean the cat command would only run if the ping command succeeded. If you wanted to condition the command in the other direction, meaning only run the second command if the first one failed, you could use something like dir \Windows | echo wubble. If the dir command fails, for some reason, the echo command is run.

As with the other web application attacks, there are a couple of ways of remediating. As always, input validation is the right answer. Know what the input should look like. If anything doesn't look like you expect it to look, fail the input and demand something cleaner from the user. In the case in Figure 12.3, an IP address has a clearly defined structure. You could check input against that structure. If the input doesn't look like an IP address, you don't accept any of the input. You could also structure the application such that no input from the user is ever directly passed to the system, even if it's part of a command.

## Denial of Service Attacks

Remember the triad of confidentiality, integrity, and availability. So far, we've been talking about integrity when it comes to the web application attacks. The attacks impact the integrity of the overall application. If the attacker manages to gain access to the system through one of the attacks, we start talking about confidentiality. In the following sections, we're going to talk about availability. The purpose of a denial of service is to take an application out of service so legitimate users can't use it. As users often interact with businesses through web applications, they are often the target of denial of service attacks. This is also because attackers are often outside the enterprise and web servers are generally exposed to the Internet.

## Bandwidth Attacks

A bandwidth attack is used to generate a lot of traffic that overwhelms the network connection a service is using. A problem with bandwidth attacks, especially today, is that your target will likely have a lot more bandwidth capacity than you do. This means alone you can't possibly generate enough traffic to take a site offline. You can take a couple of approaches to this. The first is to just gang up on your target. This may mean you get all of your friends together and send as much data to your target as you absolutely can. If you have enough friends, you may be able to generate enough traffic to take a service offline.

Another approach that's similar to this but more practical, especially if you don't have a lot of friends, is to use a large number of compromised systems. This could be done using a botnet that has the capability of issuing requests to a target. The larger the botnet, the more traffic you can generate. This does assume you either have access to a botnet or know where you can rent one. Not everyone spends time acquiring botnet clients, however. This means you need to take another approach.

Fortunately, there is another approach you can take to get a lot back for putting very little in. Amplification attacks have long been a possibility. One of the first protocols used for amplification attacks was ICMP. A Smurf attack used an ICMP echo request to a broadcast address. If you selected a large enough network and made your requests large enough, you could get a large number of large responses. Since the request would have a spoofed source address, the responses would all go to your target. At its peak in the late 1990s and early 2000s, pinging a broadcast address could get tens of thousands of responses, called duplicates because after the first response to a request, every successive response is considered a duplicate. This sort of attack doesn't have nearly the same impact today as it used to. Figure 12.4 shows the largest Smurf amplifiers that still existed in 2017 before the Smurf amplifier registry stopped checking.

### FIGURE 12.4 Smurf amplifier registry

Smurf Amplifier Registry (SAR)
http://www.powertech.no/smurf/

**Current top ten smurf amplifiers (updated every 5 minutes)**
*(last update: 2017-03-01 12:06:01 CET)*

| Network | #Dups | #Incidents | Registered at | Home AS |
|---|---|---|---|---|
| 212.11.130.0/24 | 38 | 0 | 1999-02-20 09:41 | AS9105 |
| 204.158.83.0/24 | 27 | 0 | 1999-02-20 10:09 | AS3354 |
| 209.241.156.0/24 | 27 | 0 | 1999-02-20 08:51 | AS701 |
| 193.109.122.0/24 | 20 | 0 | 1999-02-20 11:52 | AS3304 |
| 194.220.118.0/24 | 19 | 0 | 1999-02-20 09:38 | AS685 |
| 204.193.121.0/24 | 19 | 0 | 1999-02-20 08:54 | AS701 |
| 198.253.187.0/24 | 16 | 0 | 1999-02-20 09:34 | AS22 |
| 140.226.141.0/24 | 14 | 0 | 1999-11-20 11:30 | AS546 |
| 194.17.163.0/24 | 13 | 0 | 2000-11-29 19:05 | not-analyzed |
| 199.08.24.0/24 | 13 | 0 | 1999-02-18 11:09 | AS6199 |

2458442 networks have been probed with the SAR
56 of them are currently broken.
193885 have been fixed after being listed here

Fortunately, we don't have to rely on Smurf attacks any longer for amplification attacks. Another protocol that can be used is DNS. These attacks have gained some notoriety in recent years. One attack that was very well known was the attack on Brian Krebs's website Krebs on Security, which provides information security stories written by Krebs, an investigative journalist. The volume of traffic reached 620 gigabits per second at its peak.

A DNS request uses UDP as the transport protocol, and just as in ICMP, there is no verification of the source address performed, which makes spoofing the source address trivial. The attack works because a DNS request is small, whereas the right DNS response can be considerably larger. A common DNS amplification attack has a ratio of 70:1, meaning for every byte sent in the request, the response has 70 bytes. The attack does require a reflector, meaning a DNS server that would perform recursive queries (a resolver rather than an authoritative server) that is open to the Internet. Ideally, you would use multiple resolvers and multiple requesters to get the most volume.

There are a number of tools that can be used to run these denial of service attacks, of course. One of them is the Low Orbit Ion Cannon (LOIC). This is a .NET program that can run on Windows systems as well as Linux systems that have the Mono package installed. You can see the interface for LOIC in Figure 12.5. This program can be used to blast requests to both URLs and IP addresses. You could use LOIC to send TCP, UDP, or HTTP requests to the target.

### FIGURE 12.5 Low Orbit Ion Cannon

![](img/421171b17a0c0dfae0aacde15d9831c1_462_0.png)

A common term for these sorts of attacks is distributed denial of service, because there are usually multiple systems involved in the attack and they are often scattered all over the Internet. It's the scattered nature that makes it distributed. As noted earlier, as businesses get more bandwidth, it makes it considerably harder for a single system or site to be able to generate enough traffic to take down sites. Effectively, every modern denial of service attack that is bandwidth oriented is a distributed denial of service attack. This is not to say that all denial of service attacks are distributed or even bandwidth oriented.

When it comes to remediation against this sort of attack, there aren't a lot of options. If you are hosting your own services on your own network and you are the target of a denial of service attack, the best you can do once you're under attack is contact your Internet service provider (ISP) and hope they will do something to divert the attack before it gets to you. By the time it gets to your network connection, it's too late. Your connection to your ISP is flooded, which is the source of the denial of service. There's nothing at all your firewall or other device on your premises can do.
