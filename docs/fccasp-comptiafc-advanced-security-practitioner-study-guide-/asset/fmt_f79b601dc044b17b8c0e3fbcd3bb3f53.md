
Many database products such as Microsoft SQL Server, MySQL, and Oracle allow sophisticated access queries to be made. If the database and the underlying OS do not have the proper security controls in place, the attacker can create queries against the database that disclose unauthorized information. This type of attack is generally known as *SQL injection*. A SQL injection attack is carried out when the attacker uses a series of malicious SQL queries to directly manipulate the SQL database. SQL injection attacks can be launched from the address bar of a website, from within application fields, or through queries and searches. Once the SQL injection is launched, the malformed input may cause the database to become unstable or leak information. Attackers use logic such as a single quote (`'`) to test the database for vulnerabilities. Responses such as the one shown in the following code give the attacker the feedback needed to know that the database is vulnerable to attack:

```
Microsoft OLE DB Provider for ODBC Drivers error '80040e14'
[Microsoft][ODBC SQL Server Driver][SQL Server]Syntax error converting
the nvarchar value 'sa_login' to a column of data type int.
/index.asp, line 5
```

Preventing these types of input problems requires true defense in depth. This starts by filtering traffic before it ever enters the network. One approach is to use a web application firewall (WAF), the next advancement in firewall design. WAFs analyze web traffic and can be used to filter out SQL injection attacks, malware, XSS, and CSRF. WAFs require a high degree of application awareness as they have the ability to analyze web traffic and look for items such as malicious XML constructs and SQL injection commands.

Another item that can be used to help defend against SQL inject attacks is a database activity monitor (DAM). DAM systems have emerged because companies face many more threats such as SQL injection than in the past. There is also a much greater need for compliance so that companies can track what activity occurs within databases. Laws and regulations such as HIPAA and PCI-DSS have increased this demand. DAMs basically monitor the database and analyze the types of activity that is occurring. You can think of DAM as being similar to security information and event management (SIEM), except that SIEM systems like Spunk correlate and analyze events from multiple sources, whereas DAMs focus specifically on database access and activity.

## Application Sandboxing

*Application sandboxing* is the process of writing files to a sandbox or temporary storage area instead of their normal location. Sandboxing is used to limit the ability of code to execute malicious actions on a user's computer. If you launch an application in the sandbox, it won't be able to edit the registry or even make changes to other files on the user's hard disk.

One application area where sandboxing is used is with *mobile code*. Mobile code is software that will be downloaded from a remote system and run on the computer performing the download. The security issue with mobile code is that it is executed locally. Many times, the user might not even know that the code is executing. Java is mobile code, and it operates within a sandbox environment to provide additional security. Data can be processed as either client-side processing or server-side processing. Server-side processing is where the code is processed on the server, whereas with client-side processing the code will run on the client. PHP is an example of a server-side processing language where JavaScript is processed on the client side and can be executed by the browser.

## Application Security Frameworks

An application security framework is a framework for system development that can make the development process easier to manage for the security manager. It is designed to build in security controls as needed. There are many different models and approaches. Some have more steps than others, yet the overall goal is the same: to control the process and add security to build defense in depth. One industry-accepted approach is a standardized SDLC process. NIST defines SDLC in NIST SP 800-34 as “the scope of activities associated with a system, encompassing the system's initiation, development and acquisition, implementation, operation and maintenance, and ultimately its disposal that instigates another system initiation.” [Table 5.2](#c05.xhtml#c05-tbl-0002) provides a brief overview of a typical SDLC and the associated activity.

**TABLE 5.2** Typical systems development life cycle activities

| SDLC step | Description |
| --- | --- |
| Requirements | Define the purpose of the project and what customer needs have to be met. Distill the customer needs into a set of testable system requirements, including security controls. |
| Feasibility | Determine whether sufficient resources are available to develop software meeting the customer's requirements. |
| Design | Develop a design specification and verify that it addresses all requirements. |
| Development | Write code, verify that it conforms to the design specification, and test it to validate that it meets all system requirements. |
| Implementation | Installation by the customer, final user testing, and placing the software into operation. |
| Postimplementation | Formal review to evaluate the adequacy of the system. A cost–benefit analysis and review can be performed to determine the value of the project and to improve future projects. |
| Maintenance | Feature enhancements in response to user experience, and security patches in response to emerging threats, with full regression testing of all software changes before they are released. |

Standards and guidelines may be sourced from government or the open source community, including CMU Software Engineering Institute (SEI), NIST, and OWASP. The OWASP project provides resources and tools for web developers. OWASP (`www.owasp.org`) maintains a collection of tools and documents that are organized into the following categories:

1.  **Protect** Tools and documents that can be used to guard against security-related design and implementation flaws
2.  **Detect** Tools and documents that can be used to find security-related design and implementation flaws
3.  **Life Cycle** Tools and documents that can be used to add security-related activities into the SDLC

### Standard Libraries

A *standard library* for a programming language is the library that is made available in every implementation of that language. Depending on the constructs made available by the host language, a standard library may include items such as subroutines, macro definitions, global variables, and templates. The Standard C++ library can be divided into the following categories:

*   A standard template library
*   Inputs and outputs
*   Standard C headers

The problem is that some C standard library functions can be used inappropriately or in ways that may cause security problems when programmers don't follow industry-accepted approaches to developing robust, secure applications. Some C functions that can be exploited (because they do not check for proper buffer size) are `strcat()`, `strcpy()`, `sprintf()`, `vsprintf()`, `bcopy()`, `scanf()`, and `gets()`.

### Secure Coding Standards

*Secure coding* refers to the practice of building secure software with a high level of security and quality assurance. Building secure software requires that you do the following:

*   Understand common software weaknesses that lead to security vulnerabilities
*   Follow secure coding standards and practices.
*   Perform in-depth code reviews.
