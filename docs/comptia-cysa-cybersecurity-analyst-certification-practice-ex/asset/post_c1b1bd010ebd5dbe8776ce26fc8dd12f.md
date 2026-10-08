
6. To learn more about today's threats, a cybersecurity analyst could install a system that appears as a typical server but is available only as a lure for attackers. What is such a system called?

+   A. Jump server
+   B. Intrusion detection system
+   C. Honeypot
+   D. RBAC box
+   E. Micro-segmented server are

+   C is correct. The administrator wants a honeypot to lure in attackers to learn from their activities.

+   A, B, D, and E are incorrect. A is incorrect because a jump server is for administrators to remotely access to a protected network. B is incorrect because an IDS is for monitoring and alerting on malicious traffic. D and E are incorrect because both RBAC box and micro-segmented server are nonsensical terms.

7. Which of the following are direct impacts of employing ACLs? (Choose two).

+   A. Controlling access
+   B. Restricting malware from spreading
+   C. Filtering specific traffic
+   D. Enabling direct network routes

+   A and C are correct. A is correct because an access control list is primarily for controlling access. C is correct because using ACLs is a primary means of filtering traffic.

+   B and D are incorrect. B is incorrect because, although an ACL does facilitate filtering malware, it is a specific task for which ACL is just one option. The primary purposes of an ACL are to control access and filter traffic, generally by address, port, or protocol. D is incorrect because, although an ACL can enable a direct network route (via a “permit” ACL), that is not the sole or general purpose of an ACL.

8. The following text is an example of what?

```
deny icmp 172.16.0.0 0.15.255.255 192.168.50.0 0.0.0.255
```

+   A. Spam filter
+   B. Access control list
+   C. VPN tunnel setup
+   D. IGMP setup

+   B is correct. The string "deny icmp 192.168.50.0 0.0.0.255 172.16.0.0 15.255.255" is an access control list that denies ICMP traffic originating from the 192.168.50.0 subnet targetting any addresses between 172.16.0.0 and 172.31.255.255.

+   A, C, and D are incorrect. A is incorrect because ACL is not filtering spam but rather Internet Control Message Protocol (ICMP) traffic. C is incorrect because the ACL is not setting up a VPN. D is incorrect because the ACL is not configuring the Internet Group Management Protocol (IGMP).

+   9. In the following ACL, what does "10.235.235.235" represent?
permit tcp 10.15.0.0 0.255.255.255 10.235.235.235 0.255.255.255

+   A. Sub mask
+   B. Source address
+   C. Destination address
+   D. The filtered port

+   C is correct. The 10.235.235.235 in the ACL is the destination address.
A, B, and D are incorrect. A is incorrect because the subnet masks are 0.255.255.255. B is incorrect because the source address provided is 10.15.0.0 (a subnet). D is incorrect because no port is provided in the ACL.

+   10. When needing a new server, a company administrator starts installing a prebuilt server image. The image has most services running and applications already installed to make the task as easy as possible. As the cybersecurity analyst, what would be your best recommendation for the administrator?

+   A. Rebuild the server image with few services and applications as possible.
+   B. Rebuild the server image with all services and applications installed but not running.
+   C. Create several servers depending on the subnet.
+   D. Run a vulnerability scanner on the already-deployed servers.

+   A is correct. Certainly the best recommendation is to rebuild the image to have enabled the minimum number of services and applications running. The administrator would enable or install only what is needed for the particular target system.

+   B, C, and D are incorrect. B is incorrect because having all services and applications installed still provides several attack vectors compared to not installed, even if those are not running. C is incorrect because creating several images might be more work than it is worth. Having them specific to the subnet makes little practical sense. D is incorrect because a vulnerability scan is a good idea, but it does not address the ongoing practice of installing an image with several services running.

+   11. Which of the following are the method and purpose of a DNS sinkhole? (Choose two.)

+   A. Redirecting DNS queries away from a known-malicious server
+   B. Providing no DNS resolution responses
+   C. Logging DNS resolution requests to determine infected hosts
+   D. Logging DNS redirects to the infected domain

+   A and C are correct. The method of a DNS sinkhole is to redirect DNS queries by infected machines away from a known malware server. The purpose of a DNS sinkhole is to log DNS resolution requests to help identify what other machines are likely infected.

+   B and D are incorrect. B is incorrect because a DNS sinkhole provides responses. D is incorrect because the malicious domain is known.

+   12. A company has a significant investment in intrusion detection systems. What would be the best recommendation for security?

+   A. Upgrade the IDS.
+   B. Employ endpoint controls.
+   C. Prohibit all uses.
+   D. Replace employees.

+   B is correct. Endpoint controls are a necessary complement.

+   A, C, and D are incorrect. A is incorrect because the IDS is already monitoring traffic. C is incorrect because prohibiting all uses is not a feasible strategy. D is incorrect because replacing employees is not a solution for technical security gaps.

+   13. What type of access control is demonstrated in Figure 3-1?

+   A. Role-based
+   B.Rule-based
+   C. Time of day
+   D. Location

| Device Name | MAC Address | Allowed Days | Allowed Time |
| --- | --- | --- | --- |
| OfficePrinter | 98:e7:44:13:79:1 | MON,WED,THU,FRI | 9:00AM to 5:00PM |
| Bills-Phone | 40:33:10:79:18:2 | MON | 8:00AM to 8:15AM |
| Bills-iPad | 74:81:14:d0:27:19 | MON,WED,FRI | 8:00AM to 5:00PM |
| Beverly-iPhone | c0:1a:da:73:58:dc | MON,WED,THU,FRI | 9:00AM to 7PM |

+   C is correct. The device restrictions are based on days and times.

+   A, B, and D are incorrect. A is incorrect because there are no roles shown. B is incorrect because there is no access specific to a rule. D is incorrect because the location is unknown.

+   14. A cybersecurity analyst is tasked to enforce access control to files based on roles. Looking at the following two illustrations, select the appropriate answer when identifying an example of role-based access control.

### CySA+ Practice Exams Folder Permissions

| | Read | Write | Add | Delete |
| --- | --- | --- | --- | --- |
| Copy Editor | ✓ | ✓ | ✓ | |
| Author | ✓ | ✓ | ✓ | |
| Proj Mgr | ✓ | ✓ | ✓ | ✓ |
| Administrator | ✓ | ✓ | ✓ | ✓ |

### TPS Report Folder Permissions

| | Read | Write | Add | Delete |
| --- | --- | --- | --- | --- |
| P. Gibbons | ✓ | ✓ | | | |
| B. Lumbergh | ✓ | ✓ | | | |
| Bob 1 | ✓ | ✓ | ✓ | | |
| Bob 2 | | ✓ | ✓ | |
| M. Waddams | ✓ | | | ✓ |

+   A. Illustration A
+   B. Illustration B
+   C. Both illustrations
+   D. Neither illustration

+   A is correct. Illustration A shows roles such as author, editor, and manager.

+   B, C, and D are incorrect. B is incorrect because Illustration B shows names, not roles. C is incorrect because Illustration B is not correct. D is incorrect because Illustration A is correct.

+   15. Ensuring patches are properly tested and deployed can be a challenging but necessary task. Which of the following statements are true regarding patching? (Choose all that apply.)

+   A. Patch testing should be done very soon after version release.
+   B. Before patches are deployed, patches should be carefully tested, staged, and finally rolled out to production.
