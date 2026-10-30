
9. C. A vulnerability scanner is the only tool or method listed that will supply all three pieces of information. A port scanner could tell you whether or not port 80 is open, but would not test for share access or vulnerable versions of PHP. Most vulnerability scanners, such as Nessus, will perform basic TCP/IP port scanning as well as scanning for misconfigurations, insecure versions of software, and so on.

10. B. A list showing service “banners” such as “220 Microsoft FTP Service” is usually created by banner grabbing. There are a number of tools that specialize in banner grabbing, but you can accomplish the same thing by simply using a Telnet client to connect to a service. In most cases, the service will return a banner telling you various details about the service.

11. B. There must be a user error in testing. When any scanning tool reports a “finding” that isn’t really there and doesn’t really exist, this is known as a false positive.

12. B. Gray-box testing is a combination of white- and black-box testing. The tester has some knowledge of the system or application being examined, such as the data structures and algorithms, but doesn’t know everything about the application, as they would during white-box testing.

13. D. The attack surface of an application is really a description of all the different places where an attacker could penetrate or disrupt the application. This would include all data paths into and out of the application, all data used by the application, and the code that protects and processes the data and data paths.

14. B. If you want a tool that will look for vulnerabilities but won’t interfere with network traffic, your best compromise will be some type of passive network vulnerability scanner. A “passive” scanner waits for data to come to it—it doesn’t perform any scans or probes on its own and doesn’t interact with the traffic it observes.

15. D. Any time you find a vulnerability and then use tools or techniques that exercise that vulnerability to gain access or manipulate data, you have performed vulnerability exploitation. Identifying vulnerabilities stops short of doing something with the discovered vulnerabilities. Using a SQL injection attack to gain access to a system would definitely qualify as exploiting a vulnerability.

## PART IV
### Application, Data, and Host Security

- **Chapter 17** — Application Security Controls
- **Chapter 18** — Mobile Device Security
- **Chapter 19** — Host-based Security
- **Chapter 20** — Securing Alternative Environments

## Application Security Controls

In this chapter, you will

- Discover the importance of secure coding concepts
- Understand the importance of application security controls and techniques
- Discover the importance of input handling
- Learn about the tools and techniques used in secure coding
- Learn about application hardening techniques

Application security controls and techniques are important in ensuring that the applications deployed are as secure as possible. Beginning with secure coding techniques, and then providing defense in depth by adding security controls, the security of an application is established. Using application hardening techniques and proper configuration and change controls provides a process-driven method to ensure continued security per a defined risk profile.

### Secure Coding Concepts

Application security begins with code that is secure and free of vulnerabilities. Unfortunately, all code has weaknesses and vulnerabilities, so instantiating the code in a manner that has effective defenses preventing the exploitation of vulnerabilities can maintain a desired level of security. Proper handling of configurations, errors and exceptions, and inputs can assist in the creation of a secure application. Testing of the application throughout the system lifecycle can be used to determine the actual security risk profile of a system.

There are numerous individual elements in the Software Development Lifecycle (SDL) that can assist a team in developing secure code. Correct SDL processes, such as input validation, proper error and exception handling, and cross-site scripting and cross-site request forgery mitigations, can improve the security of code. Process elements such as security testing, fuzzing, and patch management also help to ensure applications meet a desired risk profile.

There are two main enumerations of common software errors: the Top 25 list maintained by MITRE, and the OWASP Top Ten list for web applications. Depending on the type of application being evaluated, these lists provide a solid starting point for security analysis of known error types. MITRE is the repository of the industry standard list for standard programs, and OWASP for web applications. Because the causes of common errors do not change quickly, these lists are not updated every year.

### Error and Exception Handling

Every application will encounter errors and exceptions, and these need to be handled in a secure manner. One attack methodology includes forcing errors to move an application from normal operation to exception handling. During an exception, it is common practice to record/report the condition, including supporting information such as the data that resulted in the error. This information can be invaluable in diagnosing the cause of the error condition. The challenge is in where this information is captured. The best method is to capture it in a log file, where it can be secured by an ACL. The worst case is when it is echoed to the user. Echoing error condition details to users can provide valuable information to attackers when they cause errors on purpose.

![](img/922567202a944c5e8d3ba0168d2ad3a5_361_0.png)

> **EXAM TIP** All errors/exceptions should be trapped and handled in the generating routine.

Improper exception handling can lead to a wide range of disclosures. Errors associated with SQL statements can disclose data structures and data elements. Remote procedure call (RPC) errors can give up sensitive information such as filenames, paths, and server names. Programmatic errors can give up line numbers that an exception occurred on, the method that was invoked, and information such as stack elements.

### Input Validation

With the move to web-based applications, the errors have shifted from buffer overflows to input-handling issues. Users have the ability to manipulate input, so it is up to the developer to handle the input appropriately to prevent malicious entries from having an effect. Buffer overflows could be considered a class of improper input, but newer attacks include canonicalization attacks and arithmetic attacks. Probably the most important defensive mechanism that can be employed is input validation. Considering all inputs to be hostile until properly validated can mitigate many attacks based on common vulnerabilities. This is a challenge, as the validation efforts need to occur after all parsers have completed manipulating input streams, a common function in web-based applications using Unicode and other international character sets.

Input validation is especially well suited for the following vulnerabilities: buffer overflow, reliance on untrusted inputs in a security decision, cross-site scripting (XSS), cross-site request forgery (XSRF), path traversal, and incorrect calculation of buffer size. Input validation may seem suitable for various injection attacks, but given the complexity of the input and the ramifications from legal but improper input streams, this method falls short for most injection attacks. What can work is a form of recognition and whitelisting approach, where the input is validated and then parsed into a standard structure that is then executed. This restricts the attack surface to not only legal inputs, but also expected inputs.

![](img/922567202a944c5e8d3ba0168d2ad3a5_362_0.png)

> **EXAM TIP** Consider all input to be hostile. Input validation is one of the most important secure coding techniques employed, mitigating a wide array of potential vulnerabilities.

Output validation is just as important in many cases as input validation. If querying a database for a username and password match, the expected forms of the output of the match function should be either one match or none. If using record count to indicate the level of match, which is a common practice, then a value other than 0 or 1 would be an error. Defensive coding using output validation would not act on values >1, as these are clearly an error and should be treated as a failure.

### Fuzzing

One of the most powerful tools that can be used in testing is fuzzing (aka fuzz testing), which is the systematic application of a series of malformed inputs to test how the program responds. Fuzzing has been used by hackers for years to find potentially exploitable buffer overflows, without any specific knowledge of the coding. Fuzz testing works perfectly fine regardless of the type of testing, white box or black box. Fuzzing serves as a best practice for finding unexpected input validation errors.

A tester can use a fuzzing framework to automate numerous input sequences. In examining whether a function can fall prey to a buffer overflow, a tester can run numerous inputs, testing lengths and ultimate payload-delivery options. If a particular input string results in a crash that can be exploited, the tester would then examine this input in detail. Fuzzing is still relatively new to the development scene, but is rapidly maturing and will soon be on nearly equal footing with other automated code-checking tools.

### Cross-site Scripting Prevention

Cross-site scripting (XSS) is one of the most common web attack methodologies. The cause of the vulnerability is weak user input validation. If input is not validated properly, an attacker can include a script in their input and have it rendered as part of the web process. There are several different types of XSS attacks, which are distinguished by the effect of the script:

- **Non-persistent XSS attack** The injected script is not persisted or stored, but rather is immediately executed and passed back via the web server.
- **Persistent XSS attack** The script is permanently stored on the web server or some back-end storage. This allows the script to be used against others who log in to the system.
- **DOM-based XSS attack** The script is executed in the browser via the Document Object Model (DOM) process as opposed to the web server.
