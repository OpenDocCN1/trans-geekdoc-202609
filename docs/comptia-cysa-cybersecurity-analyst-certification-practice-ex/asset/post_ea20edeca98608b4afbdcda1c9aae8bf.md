
-   A. Redirecting DNS queries away from a known-malicious server
-   B. Providing no DNS resolution responses
-   C. Logging DNS resolution requests to determine infected hosts
-   D. Logging DNS redirects to determine the infected domain

12. A company has a significant investment in network intrusion detection systems, which are able to inspect traffic with significant speed and reasonable effectiveness. However, a recent incident reveals that employees could use point-to-point encryption to mask data exfiltration. What would be the best recommendation for the company?

-   A. Upgrade the IDS to an IPS.
-   B. Employ endpoint security controls.
-   C. Prohibit all uses of encryption.
-   D. Replace the suspected employees.

13. What type of network access control is being demonstrated in Figure 3-1?

-   A. Role-based
-   B. Rule-based
-   C. Time of day
-   D. Location

# Device Access Restriction List

| Device Name | MAC Address | Allowed Days | Allowed Time | Edit |
| --- | --- | --- | --- | --- |
| OfficePrinter | 98:e7:f4:48:13:79 | MON,TUE,WED,THU,FRI | 9:00AM to 7:00PM | Remove |
| Bills-iPhone | 40:33:1a:00:79:18 | MON,WED,FRI | 8:00AM to 5:00PM | Remove |
| Bills-iPad | 74:81:14:d0:27:19 | MON | 8:00AM to 8:15AM | Remove |
| Beverly-iPhone | d0:1a:da:73:58:d0 | MON,TUE,WED,THU,FRI | 8:00AM to 5:00PM | Remove |

**Figure 3-1** Device access restriction list

14. A cybersecurity analyst is told to enforce access access control to files based on roles. Looking at the following two illustrations, select the appropriate answer when identifying an example of role-based network access control.

| Copy Editor | Read | Write | Add | Delete |
| --- | --- | --- | --- | --- |
| Editor | ✓ | ✓ | ✓ | |
| Author | ✓ | ✓ | ✓ | |
| Proj Mgr | ✓ | ✓ | ✓ | ✓ |
| Administrator | ✓ | | ✓ | ✓ |

Illustration A

# TPS Report Folder Permissions

| | Read | Write | Add | Delete |
| --- | --- | --- | --- | --- |
| P. Gibbons | ✓ | ✓ | | | |
| B. Lumbergh | | ✓ | | | |
| Bob 1 | ✓ | ✓ | ✓ | | |
| Bob 2 | ✓ | ✓ | | | |
| M. Waddams | ✓ | | | ✓ | |

Illustration B

-   A. Illustration A
-   B. Illustration B
-   C. Both illustrations
-   D. Neither illustration

15. Ensuring patches are properly tested and deployed can be a challenging necessary task. Which of the following statements are true regarding patching? (Choose all that apply.)

-   A. Patch testing should be done very soon after vendor release.
-   B. Before patches are deployed, patches should be carefully tested, staged, and finally rolled out to production.
-   C. If done carefully, patches can be tested, staged, and sent to production at the same time.
-   D. If time is critical, patches can be tested and staged at the same time.

16. A cybersecurity analyst has identified a significant vulnerability to the company’s payroll server application. The analyst’s recommendation is to immediately patch the vulnerability. Unfortunately, because the application was developed internally and its developer has since left, the application cannot be patched. Without a patch, the analyst has to use other options to lessen the risk. Such options include using a host-based IDS on the application server and additional logging on upstream network devices. What is the term to describe the analyst’s options?

-   A. Network isolation
-   B. Location-based access control
-   C. Mandatory access control
-   D. Compensating controls

17. What hardening technique can be described as “minimizing the attack surface”?

-   A. Blocking unused ports and services
-   B. Endpoint security
-   C. Compensating controls
-   D. Role-based access control

18. What access control model involves granting explicit authorization for a given object, per a given user?

-   A. Group policies
-   B. RBAC
-   C. MAC
-   D. Role-based

19. What is a technique that allows system administrators to apply configuration changes to several systems at once?

-   A. NAC
-   B. GPO
-   C. ACL
-   D. IDS

20. A company would like for access only to be granted if the employee’s laptop meets a number of criteria. Specific conditions that each laptop must include only the approved version of Windows, mail application v2.5 or higher, browser v8.0, and database application v1.18. Also, each laptop must have no unauthorized storage attached. What access control model would you recommend the company use?

-   A. Location-based
-   B. Rule-based
-   C. Role-based
-   D. Mandatory access control

# QUICK ANSWER KEY

1. A
2. A, B, D
3. D
4. B
5. A, B, D, E, F
6. C
7. A, C
8. B
9. C
10. A
11. A, C
12. B
13. C
14. A
15. A, B, D
16. D
17. A
18. C
19. B
20. B

# IN-DEPTH ANSWERS

1. Currently a company web server is outside the company’s internal network. web server needs to be available for public access, but the external exposure poses a large, continuous risk. What is the most relevant recommendation for the company to mitigate risk to the web server?

-   A. Implement a triple-homed firewall.
-   B. Utilize IDS on the web server.
-   C. Segment the internal network.
-   D. Isolate the web server from the network.

A is correct. A triple-homed firewall is a firewall with three distinct networks attached—typically the external, the internal, and the DMZ.

2. Which of the following are benefits of segmentation? (Choose all that apply.)

-   A. Improving traffic
-   B. Mitigating risk
-   C. Simpler topology
-   D. Preventing spillover of sensitive data
-   E. Streamlining access
-   F. Reducing attacks

A, B, and D are correct. Segmentation benefits include improving traffic, mitigating risks, and preventing spillover of sensitive data. C and E are incorrect because segmentation does not simplify the network.

3. What would be your recommendation?

-   A. Implement a triple-homed firewall.
-   B. Allow administrators to bypass the firewall.
-   C. Configure the web server on the DMZ.
-   D. Install a stand-alone jump box just inside the firewall.

D is correct. A jump box should be stand-alone, with no unnecessary ports that an attacker could exploit.

4. A “captive portal” is an example of which of the following?

-   A. DAC
-   B. In-band NAC
-   C. Out-of-band NAC
-   D. Role-based NAC

B is correct. A captive portal is a form of in-band network access control.

5. NAC solutions grant access based on which of the following? (Choose all that apply.)

-   A. Roles
-   B. Rules
-   C. Rates
-   D. Location
-   E. System patch level
-   F. Time of day

A, B, D, E, and F are correct. Network access control types include rolebased, rule-based, location-based, the system’s health, and the time of day.

C is incorrect. “Rates” is not an option for setting ACLs.
