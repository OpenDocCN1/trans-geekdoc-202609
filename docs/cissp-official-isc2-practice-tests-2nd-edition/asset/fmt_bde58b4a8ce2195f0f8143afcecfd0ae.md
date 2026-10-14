
# 练习题

## 26. Tracy is preparing to apply a patch to her organization’s enterprise resource planning system. She is concerned that the patch may introduce flaws that did not exist in prior versions, so she plans to conduct a test that will compare previous responses to input with those produced by the newly patched application. What type of testing is Tracy planning?

1.  Unit testing
2.  Acceptance testing
3.  **Regression testing**
4.  Vulnerability testing

## 27. What term is used to describe the level of confidence that software is free from vulnerabilities, either intentionally designed into the software or accidentally inserted at any time during its life cycle, and that the software functions in the intended manner?

1.  Validation
2.  Accreditation
3.  Confidence interval
4.  **Assurance**

## 28. Victor recently took a new position at an online dating website and is responsible for leading a team of developers. He realized quickly that the developers are having issues with production code because they are working on different projects that result in conflicting modifications to the production code. What process should Victor invest in improving?

1.  Request control
2.  Release control
3.  **Change control**
4.  Configuration control

## 29. What type of database security issue exists when a collection of facts has a higher classification than the classification of any of those facts standing alone?

1.  Inference
2.  SQL injection
3.  Multilevel security
4.  **Aggregation**

## 30. What are the two types of covert channels that are commonly exploited by attackers seeking to surreptitiously exfiltrate information?

1.  **Timing and storage**
2.  Timing and firewall
3.  Storage and memory
4.  Firewall and storage

## 31. Vivian would like to hire a software tester to come in and evaluate a new web application from a user’s perspective. Which of the following tests best simulates that perspective?

1.  **Black box**
2.  Gray box
3.  Blue box
4.  White box

## 32. Referring to the database transaction shown here, what would happen if no account exists in the Accounts table with account number 1001?

![](images/c08uf004.jpg)

1.  The database would create a new account with this account number and give it a $250 balance.
2.  The database would ignore that command and still reduce the balance of the second account by $250.
3.  **The database would roll back the transaction, ignoring the results of both commands.**
4.  The database would generate an error message.

## 33. What type of malware is characterized by spreading from system to system under its own power by exploiting vulnerabilities that do not require user intervention?

1.  Trojan horse
2.  Virus
3.  Logic bomb
4.  **Worm**

## 34. Kim is troubleshooting an application firewall that serves as a supplement to the organization’s network and host firewalls and intrusion prevention system, providing added protection against web-based attacks. The issue the organization is experiencing is that the firewall technology suffers somewhat frequent restarts that render it unavailable for 10 minutes at a time. What configuration might Kim consider to maintain availability during that period at the lowest cost to the company?

1.  High availability cluster
2.  Failover device
3.  **Fail open**
4.  Redundant disks

## 35. What type of security issue arises when an attacker can deduce a more sensitive piece of information by analyzing several pieces of information classified at a lower level?

1.  SQL injection
2.  Multilevel security
3.  Aggregation
4.  **Inference**

## 36. Greg is battling a malware outbreak in his organization. He used specialized malware analysis tools to capture samples of the malware from three different systems and noticed that the code is changing slightly from infection to infection. Greg believes that this is the reason that antivirus software is having a tough time defeating the outbreak. What type of malware should Greg suspect is responsible for this security incident?

1.  Stealth virus
2.  **Polymorphic virus**
3.  Multipartite virus
4.  Encrypted virus

---

### Questions 37–40

**Scenario:**

Linda is reviewing posts to a user forum on her company’s website and, when she browses a certain post, a message pops up in a dialog box on her screen reading “Alert.” She reviews the source code for the post and finds the following code snippet:

```
<script>alert(‘Alert’);</script>
```

## 37. What vulnerability definitely exists on Linda’s message board?

1.  **Cross-site scripting**
2.  Cross-site request forgery
3.  SQL injection
4.  Improper authentication

## 38. What was the likely motivation of the user who posted the message on the forum containing this code?

1.  **Reconnaissance**
2.  Theft of sensitive information
3.  Credential stealing
4.  Social engineering

## 39. Linda communicates with the vendor and determines that no patch is available to correct this vulnerability. Which one of the following devices would best help her defend the application against further attack?

1.  VPN
2.  **WAF**
3.  DLP
4.  IDS

## 40. In further discussions with the vendor, Linda finds that they are willing to correct the issue but do not know how to update their software. What technique would be most effective in mitigating the vulnerability of the application to this type of attack?

1.  Bounds checking
2.  Peer review
3.  **Input validation**
4.  OS patching

## 41. What property of relational databases ensures that once a database transaction is committed to the database, it is preserved?

1.  Atomicity
2.  Consistency
3.  **Durability**
4.  Isolation

## 42. Lauren wants to use software review process for the application she is working on. Which of the following processes would work best if she is a remote worker who works different hours from the rest of her team?

1.  **Pass around**
2.  Pair programming
3.  Team review
4.  Fagan inspection

## 43. Which one of the following is not a technique used by virus authors to hide the existence of their virus from antimalware software?

1.  Stealth
2.  **Multipartitism**
3.  Polymorphism
4.  Encryption

## 44. Which one of the following types of software testing usually occurs last and is executed against test scenarios?

1.  Unit testing
2.  Integration testing
3.  **User acceptance testing**
4.  System testing

## 45. What type of requirement specifies what software must do by describing the inputs, behavior, and outputs of software?

1.  Derived requirements
2.  Structural requirements
3.  Behavioral requirements
4.  **Functional requirements**

## 46. Which of the following organizations is widely considered as the definitive source for information on web-based attack vectors?

1.  (ISC)²
2.  ISACA
3.  **OWASP**
4.  Mozilla Foundation

## 47. If Chris is writing code for an application, what phase of the Agile process is he in?

1.  Planning
2.  Sprints
3.  Deployment
4.  **Development**

## 48. Lisa is attempting to prevent her network from being targeted by IP spoofing attacks as well as preventing her network from being the source of those attacks. Which one of the following rules is NOT a best practice that Lisa can configure at her network border?

1.  Block packets with internal source addresses from entering the network.
2.  Block packets with external source addresses from leaving the network.
3.  Block packets with private IP addresses from exiting the network.
4.  **Block packets with public IP addresses from entering the network.**
