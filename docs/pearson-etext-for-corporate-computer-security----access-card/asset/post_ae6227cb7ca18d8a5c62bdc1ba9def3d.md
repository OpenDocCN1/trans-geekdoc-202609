
## Few Operating Systems, Many Applications

The mechanics of vulnerabilities, exploits, patches, and work-arounds are not fundamentally different for operating systems and applications. The main difference is the small number of operating systems that most firms support versus the large number of applications they typically use.

For operating systems, most firms have to deal with vulnerability reports, patches, and work-arounds only from a handful of vendors. However, firms might run application programs from dozens of application software vendors. In most firms, the lion’s share of all vulnerabilities and fixes relates to application programs.

Just finding information about vulnerabilities and fixes can be a maddening chore because each vendor releases information about its products’ vulnerabilities and fixes in its own way. Although various vulnerability tracking services help (especially BugTraq at SecurityFocus.com), server administrators have to visit their application vendors’ websites frequently.

After the firm finds patches, it must download and install the patches. Adding to the confusion, each vendor has different mechanisms for downloading and installing patches.

## Test Your Understanding

3. Why is patching applications more time-consuming than patching operating systems?

## Hardening Applications

How can companies harden applications so that they are difficult to attack? The answer is that firms must take several actions to protect their applications.

### UNDERSTAND THE SERVER’S ROLE AND THREAT ENVIRONMENT

The first task in security is to understand the environment to be protected. If a service such as e-mail runs on a single computer, for instance, then the systems administrator can rigorously cut out everything that does not deal directly with e-mail and perhaps with remote administration. However, if a server must support multiple applications, cutting out services will be a less viable option.

The threat environment is also important. If the threat environment is very dangerous, even remote administration might have to be cut off.

### THE BASICS

As discussed in Chapter 5, servers and clients must be protected with physical security. As we saw in Chapter 7, their operating systems need to be hardened with patches and high-security configuration settings.

### MINIMIZE APPLICATIONS

**Minimize Main Applications** As noted in Chapter 7, firms should minimize the applications a host runs. Fewer applications mean fewer opportunities to take over the computer. Many installed applications are configured to start every time the computer is started. These applications both consume system resources and are a potential point of attack.

Applications can be prevented from starting through Windows Services. *Services* is located in the Control Panel under System and Security → Administrative Tools. Figure 8-4 shows that Apache2.2 is set to automatically launch at startup.

## Understanding the Server’s Role and the Threat Environment

If it runs only one or a few services, easy to disallow irrelevant things

- **Basics**
  - Physical security
  - Backup
  - Harden the operating system
  - Etc.

- **Minimize Applications**
  - Main applications
  - Subsidiary applications
  - Be guided by security baselines

- **Create Secure Application Program Configurations**
  - Use baselines to go beyond default installation configurations for high-value targets
  - Avoid blank passwords or well-known default passwords
  - Etc.

## Install Patches for All Applications

## Minimize the Permissions of Applications

If an attack compromises an application with low permissions, will not own the computer

- **Add Application Layer Authentication, Authorizations, and Auditing**
  - More specific to the needs of the application than general operating system logins
  - Can lead to different permissions for different users

- **Implement Cryptographic Systems**
  - For communication with users

## Figure 8-3 Hardening Applications (Study Figure)

The *Action* menu allows access to the properties for each service. Figure 8-5 shows that the Startup type can be changed from Automatic to either Manual or Disabled. If the service is set to manual, it will only start if initiated by the user. The service can also be manually started or stopped. Disabling unnecessary services can free up system resources and protect the host from external attack. Disabling critical services without understanding their function can cause unintended systemic problems.

## Figure 8-4 Windows Services

![](img/073342643701cc54eb7875c41ab92ef2_399_0.png)

## Figure 8-5 Service Properties

![](img/073342643701cc54eb7875c41ab92ef2_400_0.png)

## Minimize Subsidiary Applications

Hackers often attack obscure programs that are started automatically when the operating system is installed with default settings or when a complex application depends on subsidiary applications, as all webserver programs do.

For example, when users of many older versions of Windows 2000 started the IIS webserver, the operating system also started the Gopher service automatically under the default installation. Never heard of Gopher? Join the club. Gopher was a service that showed great promise for information retrieval just before the World Wide Web tidal wave hit. Today, nobody uses it. However, when attackers found a problem with the obscure Gopher program, they made almost every IIS implementation immediately vulnerable to attack until the company installed a patch.

## SECURITY BASELINES FOR APPLICATION MINIMIZATION

Again, the security baseline should guide us. The installer must know which optional helper programs to install for a given application and which are installed automatically that should be deleted after installation.

## CREATE A SECURE CONFIGURATION

Baselines will describe how to create a secure configuration in general. Most importantly, an application should never lack a password or have a well-known default password.

## INSTALL APPLICATION PATCHES AND UPDATES

Most importantly, the installer should be sure to install all application patches. As noted earlier, this usually involves tracking vulnerability and fix reports from many different application vendors.

In addition, the company should install a recent version of the software, updating the software if necessary. Newer versions of applications, once beyond the initial “teething period,” usually are much safer than older versions.

## MINIMIZE THE PERMISSIONS OF APPLICATIONS

As noted earlier, if attackers can take over an application, they can execute commands with the privileges of the program. Some programs must run with root privileges. However, many programs can run with lower levels of privileges and should be run with the minimum privileges possible for them to do their job.

## ADD APPLICATION-LEVEL AUTHENTICATION, AUTHORIZATIONS, AND AUDITING

One way to stymie attackers is to disregard input from anyone who has not been authenticated properly. To compromise a system, then, the attacker would have to have both an exploit and authenticated access to the system.

The operating system account password system provides some protection, but many applications also provide their own authentication. Instead of broad access to a computer, application authentication can be specific to the application program’s needs, for instance, only accepting people on an access control list and giving different people permissions that are relevant to the application.

The application program can require its own password—one with strong complexity. Or the application program might require a smart card or some other form of strong authentication such as public key authentication. Two-factor authentication is even better.

Although adding application-level authentication is difficult and sometimes impossible, firms should do it wherever possible. This is especially true for highly sensitive applications, such as human resource databases and customer information databases.

## IMPLEMENT CRYPTOGRAPHIC SYSTEMS

In Chapter 3, we saw the strong protections offered by cryptographic systems such as SSL/TLS and IPsec. Cryptographic system protections should always be used between the user and the application.

## Test Your Understanding

- 4.
  - a. Why must you know a server’s role to know how to protect it?
  - b. Why is it important to minimize both main applications and subsidiary applications?
  - c. Why are security baselines needed for installing applications?
  - d. Why is it important to minimize permissions for application programs?
- 5.
  - a. Why is application-level authentication superior to operating system authentication?
  - b. Why should cryptographic protections be used?

## Securing Custom Applications

Commercial off-the-shelf software is likely to have been written with some care, including checking for security vulnerabilities. However, custom applications built within a firm for its own use and the use of its customers are rarely constructed so carefully. The problem is that ordinary programmers are not likely to have been well trained in secure coding in general or in the good security practices necessary for given programming languages.

## NEVER TRUST USER INPUT

For all applications, a basic rule is “Never trust user input.” If a user is expected to enter text, check that the input really is text and ensure that it is not too long, does not contain an improper URL, does not contain a script, does not contain a Structured Query Language (SQL) statement or part of a SQL statement, and so forth. Later in this chapter, we will look at how attackers can use improper input to do damage or hack a computer.

> Never trust user input.

## BUFFER OVERFLOW ATTACKS

From the earlier discussion, one obvious concern with user input is buffer overflow attacks against the program. In some languages, such as C, one protection is only to use input functions that do length checking on the input.

## LOGIN SCREEN BYPASS ATTACKS

For website access programs, potential problems abound. For example, in login screen bypass, the attacker types a URL to a page beyond the login screen when the login screen appears. If the application is not programmed correctly, the bypass will work, giving an unauthenticated user access to information that should only be accessed by authenticated users.
