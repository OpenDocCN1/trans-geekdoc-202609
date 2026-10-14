
The sequence diagram demonstrates a sequence of actions; however, these models were meant to diagram intended activities, not attacks. To modify the sequence diagram involves adding/modifying some symbolism. For the SecML, the notation shown in [Figure 15.13](#ch15.xhtml#ch15fig13) is added to the security sequence diagram.

![Figure 15.13 Cybersecurity addition to sequence diagrams.](Images/15fig13.jpg)

**Figure 15.13** Cybersecurity addition to sequence diagrams.

Traditional sequence diagrams do not differentiate between authorized and unauthorized actions. In fact, nothing in SysML even contemplates unauthorized activities. However, in cybersecurity, unauthorized actions are of critical importance. [Figure 15.14](#ch15.xhtml#ch15fig14) shows an exemplary modified sequence diagram.

![Figure 15.14 Modified sequence diagram. ¶  ¶ A figure shows a modified sequence diagram. The diagram illustrates how an object interacts over time and the actions that are related between objects. The diagram shows a computer and a server. An e-mail to be checked is sent to the computer. The computer now sends the unsent e-mail to the server, where there is no response from the server. An unauthorized spoof e-mail is sent to the server from the computer after there is no response to the unsent e-mail. So the computer again sends a new mail to the server and the response is received from the server. The computer now sends a request to the server to download the new e-mail and delete the old e-mail. ¶ ](Images/15fig14.jpg)

**Figure 15.14** Modified sequence diagram. ¶ 

As in a traditional SysML sequence diagram, the messages are still written with the message name above and the directionality of the message. However, the modification for SecML allows one to differentiate between normal operations and unauthorized actions. Seeing unauthorized and authorized actions as they actually occur in a system, provides a very effective understanding of system operations.

The modified sequence diagram provides an overview of the sequence of events in any cyber attack. This allows the cybersecurity engineer to model various attacks. Coupling the security sequence diagram with a misuse-case diagram provides an effective overview of the attack vector in question.

#### Data Interface Diagram

This diagram type is created specifically for SecML. The data interface diagram (DID) is used to provide the cybersecurity engineer an understanding of data flow in the system of interest. It models the flow of data into and out of any system. The concept is to look at any system or subsystem and diagram all interfaces for data to flow into and out of the system of interest. Any place that data can flow is an area for security concerns. Data flowing outward can lead to data exfiltration. Data flowing inward can lead to malware being introduced to the system. This is shown in [Figure 15.15](#ch15.xhtml#ch15fig15).

![Figure 15.15 Data interface diagram.](Images/15fig15.jpg)

**Figure 15.15** Data interface diagram.

[Figure 15.16](#ch15.xhtml#ch15fig16) shows the specific elements of the data interface diagram.

![Figure 15.16 Data interface diagram elements. ¶  ¶ A table lists the diagrams of various data interface elements. The first element is a left arrow and it represents the direction of communication flow. The second element is a rectangular box and it represents a specific interface to a system or subsystem. The third element is a box with a left arrow attached to it. It is an interface with only outbound communication. The third element is a box with left and right arrows attached to it and its an interface with both inbound and outbound communication. The fourth element is a box with left and right arrows attached to it and an X inside it. It is an interface that has some countermeasures implemented for attacks. The fifth element is a box with left and right arrows attached to it and an X inside along with a numeral written above it. It is an interface with a countermeasure and the number indicates that there are multiple countermeasures. ¶ ](Images/15fig16.jpg)

**Figure 15.16** Data interface diagram elements. ¶ 

This diagram is intentionally simple. The goal is to make the process one that cybersecurity engineers can efficiently use with minimal training required. The concept it to ensure that all data flow points have been identified, and that mitigation measures have been identified. This diagram is used to examine the system of interest and to determine what, if any mitigation strategies have been put into place for each data interface. This is essentially a limited interface diagram.

#### Security Block Diagram

Unified Modeling Language (UML), which was the basis for SysML, has a component diagram. In UML, component diagrams are used to identify components in software and to model how they connect. For example, UML contains assembly connectors that model a connection when one component requires another component. The delegation connector links an external component.

This section described the foundations of SecML, which is based on the preexisting SysML. It may be that further research leads to enhancements to these models, and the addition of new models to SecML. As with all modeling language, it is expected that SecML will be revised and expanded.

### Summary

In this chapter, you have seen the application of systems engineering to cybersecurity. The goal is that you would begin to apply a methodical, systematic approach to cybersecurity. Penetration testing, as one example, should not be just a set of random hacking attempts. Rather, it should be a carefully engineered process that is mapped to specific testing requirements. It is also beneficial to model cybersecurity scenarios in order to better understand system security requirements. The SecML modeling language that was briefly introduced in this chapter provides such a methodology.

### Test Your Skills

#### Multiple Choice Questions

**[1](#app02.xhtml#ch15ans1).** What type of diagram is used to show how any entity might interact with a system?

**A.** Use-case diagram

**B.** Sequence diagram

**C.** Data interface diagram

**D.** Requirements diagram

**[2](#app02.xhtml#ch15ans2).** What is the most appropriate tool for capturing the requirements of any security process or system?

**A.** Use-case diagram

**B.** Sequence diagram

**C.** SysML

**D.** Traceability matrix

**[3](#app02.xhtml#ch15ans3).** Which of the following cybersecurity activities would be most accurately described as engineering?

**A.** Implementing complex IPS rules

**B.** Implementing asymmetric cryptography

**C.** Creating a requirements traceability matrix

**D.** Conducting a forensic investigation

**[4](#app02.xhtml#ch15ans4).** Which modeling language is used by systems engineers?

**A.** SecML

**B.** SysML

**C.** UML

**D.** DML

**[5](#app02.xhtml#ch15ans5).** What does this symbol represent in SecML?

![](Images/15fig17.jpg)

**A.** A forbidden action

**B.** A blocked system

**C.** A countermeasure

**D.** An attack

**[6](#app02.xhtml#ch15ans6).** What does this symbol represent in SecML?

![](Images/15fig18.jpg)

**A.** Attack victim

**B.** System abuser

**C.** System user

**D.** Isolated user

**[7](#app02.xhtml#ch15ans7).** What does this system represent in SecML?

![](Images/15fig19.jpg)

**A.** Blocked activity

**B.** External attack

**C.** Unauthorized activity

**D.** Internal attack

#### Exercises

**Exercise 15.1:** Misuse-Case Diagram

Create a misuse-case diagram for a specific type of attack. You can choose any attack described in this book.

**Exercise 15.2:** Requirements Gathering

Consider the cybersecurity requirements of a college campus. Create a requirements traceability matrix for penetration testing a campus computer network.

### Glossary
