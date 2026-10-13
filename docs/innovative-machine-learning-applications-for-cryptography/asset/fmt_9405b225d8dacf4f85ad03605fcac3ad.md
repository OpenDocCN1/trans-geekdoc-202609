
## 3.1.1 Software Log Usage

The AI here uses software logs as a part of any in-app code maliciously runs any key logging or if an outsider/hacker tries Reverse-Brute forcing through some employee’s old password. Such cases are still prevailing as a go-to means of penetrating through the security of the company. The AI supposedly detects any form of malicious activity present within an application:

*   if any Brute forcing is occurring from within the application
*   if the application uses any malware code to steal user data
*   if the application has any unnecessary backdoors

Whenever there is a malicious code using an innocent part of any software as a host, it is bound to leave its traces within the software, and those traces will definitely be collected via the log. Some of the software code usage is cleared as it may be of over-usage of a singular function, ranging from small memory and ram usages to collectively using a large part of the software. Sometimes, the malicious code doesn’t keep track of how much ram it has consumed, while the AI scours through the software checking for valid signatures for the software and the software’s memory usage validity. The first defence is to note the usage down and report it to authorities whilst writing the ip of the memory usage. When specific threshold is reached and once the AI detects it, it causes its protocols to activate, decreases secure points and detects the malware to be sent to `IRS` (Intrusion Response System). Sample Software code log shown in Figure 1.

| Figure 1. Software code log |
| --- |
| ![Figure979-8-3693-1642-9.ch004.f01](i/ch004.f01.png) |

## 3.1.2 User Entry Log Usage

User Entry and Exit logs are stored as a part of code in the biometrics attendance section. The AI checks for stray IPs and checkout times to detect any strange activity of any of the IP Addresses within the network, proceeding to alert the Division responsible to handle, also triggering the lockdown protocol series-1 (refer lockdown protocols section) with the instance of the suspicious IP, thus protecting others from the network. If an Optimised Brute Force Algorithm user uses botnets or zombies to enter, a number of trials and entries can be detected and the lockdown protocol series-2 (refer lockdown protocols section) is triggered to protect the users. Other users are safe to work since their work is forcefully and temporarily moved to a virtual working environment until the attacker is contained or the botnets are removed by safety measures. User Sign in log shown in Figure 2.

> **NOTE:** Antibody AI here is not the entire IDPS and IRS package, it is just the cryptography securer and breach detector IDS, so depending on the IRS in the systems and the cyber division of respective company uses, the time of stay in virtual work environment for other users is depended.

| Figure 2. User sign-in log |
| --- |
| ![Figure979-8-3693-1642-9.ch004.f02](i/ch004.f02.png) |

## 3.1.3 Network Traffic Log Usage

Network Traffic Logs are monitored along with other inputs in any case there is a halt in any of the systems within the network. The halt in the network may denote an additional traffic that may be caused due to brute forcing algorithms using botnets or zombie PCs to enter the mainframe. If that is a halt due to any other hindrances, the reason is noted and sent to the Response mechanism as well as the network admin, cyber security admin present within the campus to alert them of any malicious activities. If the network's jam is nothing but a ping resends, or a slow network, the AI’s precision detects those and reports to corresponding staff members and measures are taken to prevent slow network traffic by any other means.

This Network log usage is directly translated into the base value of the “Secure points”, allowing the AI to detect breaches shown in Figure 3.

| Figure 3. Network traffic log |
| --- |
| ![Figure979-8-3693-1642-9.ch004.f03](i/ch004.f03.png) |

## 3.1.4 Database Log Usage

The AI uses the Logs and Errors from Database in any of the client computers to check if any botnet is trying to enter into the system using the SQL injection method, it checks for error logs occurred at a specific time to check if any zombies are trying to penetrate into the Database. To make the prevention easy and the zombies unharmed, the AI detects this as an “anomaly” tag, and returns to the Cyber Security division in the company and leaves the zombies trouble alone. The Database is also vulnerable to some script-kiddies using SQL Injection tags within the Text Fields, so the AI monitors the inputs from the Text Fields to checks for these vulnerable Tags, and if it is detected, it is forwarded to Cyber Division of the company; also the Security protocol for this specific problem is triggered. The Database logs are shown in Figure 4.

| Figure 4. Database log (SQL) |
| --- |
| ![Figure979-8-3693-1642-9.ch004.f04](i/ch004.f04.png) |

## 3.1.5 IRS Access

Like the previous note explains, This AI is not the Response System, but merely a detection and protection system. It needs access to the IRS system each network uses, in order to alert the systems as well as to Respond or counter-attack any threat which the systems withstand. In any case if there is a detection of intrusion, either by brute force, SQL injection, botnets or zombies, then the AI must activate the IRS situated within the company systems and alerts the other users that a situation is going on. The Final input that is required for this detection AI and key-changing AI is the access to the response system that can be used for the correct response to the intrusion.

## 3.2 Historical Breach Data Detection and Comparison of Current Breach With Previous Attempts

The Antibody AI uses the inputs given here not as separated as the raw numbers provided, but as a part of bigger inputs to detect what we call now as the “secure points” for a system at that specific time. The AI is fed these secure points through another AI we create called the “Lymph AI”. This Lymph AI is just a simple CNN based AI which collects the logs and its respective factors to create the “secure points” that we spoke of. The Lymph AI is trained with a dataset of Breaches which occurred in the past and their respective logs in the specific formula given in the table 1.2.

Table 2. Example dataset of previous breaches and output of lymph AI producing the secure points for the data received and calculating the breach percentage of the data

| Data No. | IP Address | Network Ping of the IP | Software Code Usage of the IP | Sql Injection Detection | Similar Tries of Other Users | Secure Points | Potential Breach Percentage |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | 192.168.0.71 | 345ms | 72% memory | False | 192.168.0.75 | 20 | 89% |
| 2 | 192.168.0.72 | 228ms | 68% memory | True | 192.168.0.76 | 10 | 92% |
| 3 | 192.168.0.73 | 315ms | 45% memory | False | NIL | 64 | 25% |
| 4 | 192.168.0.74 | 12ms | 30% memory | False | NIL | 85 | 8% |
| 5 | 192.168.0.75 | 562ms | 81% memory | False | 192.168.0.71 | 14 | 90% |
| 6 | 192.168.0.76 | 645ms | 84% memory | True | 192.168.0.72 | 8 | 96% |

This Historical data can be used to train the Lymph AI, and to collect the Data from Antibody AI and check for breaches. These occur in the intervals of 30 seconds for each system, and reports of this are submitted to respective divisions as a log file. These log files generated from the antibody AI can also be used to train the Lymph AI making the entire AI, self-learning automata. When the current data collected has a lower “Secure points”, the Antibody AI detects the Secure points and respective counter measures are taken regarding the breach.
