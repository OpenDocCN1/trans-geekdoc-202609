
# 知识点总结

**Know how security controls work and what they do.** Security controls use access rules to limit the access by a subject to an object.

**Be able to list the classes of TCSEC, ITSEC, and the Common Criteria.** The classes of TCSEC include verified protection, mandatory protection, discretionary protection, and minimal protection. [Table 8.4](#c08.xhtml#table8-4) covers and compares equivalent and applicable rankings for TCSEC, ITSEC, and the CC (remember that functionality ratings from F7 to F10 in ITSEC have no corresponding ratings in TCSEC).

**Define a trusted computing base (TCB).** A TCB is the combination of hardware, software, and controls that form a trusted base that enforces the security policy.

**Be able to explain what a security perimeter is.** A security perimeter is the imaginary boundary that separates the TCB from the rest of the system. TCB components communicate with non-TCB components using trusted paths.

**Know what the reference monitor and the security kernel are.** The reference monitor is the logical part of the TCB that confirms whether a subject has the right to use a resource prior to granting access. The security kernel is the collection of the TCB components that implement the functionality of the reference monitor.

**Understand the security capabilities of information systems.** Common security capabilities include memory protection, virtualization, and Trusted Platform Module (TPM).

## Written Lab

1.  Name at least seven security models.
2.  Describe the primary components of TCB.
3.  What are the two primary rules or principles of the Bell-LaPadula security model? Also, what are the two rules of Biba?
4.  What is the difference between open and closed systems and open and closed source?

## Review Questions

1.  What is system certification?
    1.  Formal acceptance of a stated system configuration
    2.  A technical evaluation of each part of a computer system to assess its compliance with security standards
    3.  A functional evaluation of the manufacturer’s goals for each hardware and software component to meet integration standards
    4.  A manufacturer’s certificate stating that all components were installed and configured correctly

2.  What is system accreditation?
    1.  Formal acceptance of a stated system configuration
    2.  A functional evaluation of the manufacturer’s goals for each hardware and software component to meet integration standards
    3.  Acceptance of test results that prove the computer system enforces the security policy
    4.  The process to specify secure communication between machines

3.  What is a closed system?
    1.  A system designed around final, or closed, standards
    2.  A system that includes industry standards
    3.  A proprietary system that uses unpublished protocols
    4.  Any machine that does not run Windows

4.  Which best describes a confined or constrained process?
    1.  A process that can run only for a limited time
    2.  A process that can run only during certain times of the day
    3.  A process that can access only certain memory locations
    4.  A process that controls access to an object

5.  What is an access object?
    1.  A resource a user or process wants to access
    2.  A user or process that wants to access a resource
    3.  A list of valid access rules
    4.  The sequence of valid access types

6.  What is a security control?
    1.  A security component that stores attributes that describe an object
    2.  A document that lists all data classification types
    3.  A list of valid access rules
    4.  A mechanism that limits access to an object

7.  For what type of information system security accreditation are the applications and systems at a specific, self-contained location evaluated?
    1.  System accreditation
    2.  Site accreditation
    3.  Application accreditation
    4.  Type accreditation

8.  How many major categories do the TCSEC criteria define?
    1.  Two
    2.  Three
    3.  Four
    4.  Five

9.  What is a trusted computing base (TCB)?
    1.  Hosts on your network that support secure transmissions
    2.  The operating system kernel and device drivers
    3.  The combination of hardware, software, and controls that work together to enforce a security policy
    4.  The software and controls that certify a security policy

10. What is a security perimeter? (Choose all that apply.)
    1.  The boundary of the physically secure area surrounding your system
    2.  The imaginary boundary that separates the TCB from the rest of the system
    3.  The network where your firewall resides
    4.  Any connections to your computer system

11. What part of the TCB concept validates access to every resource prior to granting the requested access?
    1.  TCB partition
    2.  Trusted library
    3.  Reference monitor
    4.  Security kernel

12. What is the best definition of a security model?
    1.  A security model states policies an organization must follow.
    2.  A security model provides a framework to implement a security policy.
    3.  A security model is a technical evaluation of each part of a computer system to assess its concordance with security standards.
    4.  A security model is the process of formal acceptance of a certified configuration.

13. Which security models are built on a state machine model?
    1.  Bell-LaPadula and Take-Grant
    2.  Biba and Clark-Wilson
    3.  Clark-Wilson and Bell-LaPadula
    4.  Bell-LaPadula and Biba

14. Which security model addresses data confidentiality?
    1.  Bell-LaPadula
    2.  Biba
    3.  Clark-Wilson
    4.  Brewer and Nash

15. Which Bell-LaPadula property keeps lower-level subjects from accessing objects with a higher security level?
    1.  (star) Security Property
    2.  No write up property
    3.  No read up property
    4.  No read down property

16. What is the implied meaning of the simple property of Biba?
    1.  Write down
    2.  Read up
    3.  No write up
    4.  No read down

17. When a trusted subject violates the star property of Bell-LaPadula in order to write an object into a lower level, what valid operation could be taking place?
    1.  Perturbation
    2.  Polyinstantiation
    3.  Aggregation
    4.  Declassification

18. What security method, mechanism, or model reveals a capabilities list of a subject across multiple objects?
    1.  Separation of duties
    2.  Access control matrix
    3.  Biba
    4.  Clark-Wilson

19. What security model has a feature that in theory has one name or label, but when implemented into a solution, takes on the name or label of the security kernel?
    1.  Graham-Denning model
    2.  Deployment modes
    3.  Trusted computing base
    4.  Chinese Wall

20. Which of the following is not part of the access control relationship of the Clark-Wilson model?
    1.  Object
    2.  Interface
    3.  Programming language
    4.  Subject

# Chapter 9: Security Vulnerabilities, Threats, and Countermeasures

**THE CISSP EXAM TOPICS COVERED IN THIS CHAPTER INCLUDE:**

*   **Domain 3: Security Architecture and Engineering**
    *   3.5 Assess and mitigate the vulnerabilities of security architectures, designs, and solution elements
        *   3.5.1 Client-based systems
        *   3.5.2 Server-based systems
        *   3.5.3 Database systems
        *   3.5.5 Industrial control systems (ICS)
        *   3.5.6 Cloud-based systems
        *   3.5.7 Distributed systems
        *   3.5.8 Internet of Things (IoT)
    *   3.6 Assess and mitigate vulnerabilities in web-based systems
    *   3.7 Assess and mitigate vulnerabilities in mobile systems
    *   3.8 Assess and mitigate vulnerabilities in embedded devices
