
That material can contain features quite apart from the content and meaning.

It may seem strange to use meaningless features as evidence. However, Richard Forsyth reported on studies and experiments that found that short substrings of letter sequences can be effective in identifying authors. Even a relative count of the use of single letters can be characteristic of authors.

Certain message formats may provide additional information. A number of Microsoft email systems include a data block with every message that is sent. To most readers, this block contains meaningless garbage. However, it may include a variety of information, such as part of the structure of the file system on the sender’s machine, the sender’s registered identity, programs in use, and so forth.

Other programs may add information that can be used. Microsoft’s word processing program, Word, for example, is frequently used to create documents sent by email. Word documents include information about file system structure, the author’s name (and possibly company), and a global user ID. This ID was analyzed as evidence in the case of the Melissa virus. MS Word can provide even more data. Comments and "deleted" sections of text may be retained in Word files and simply marked as hidden to prevent them from being displayed. Simple utility tools can recover this information from the file itself.

## Mobile Code Controls

The concept of attaching programs to webpages has very real security implications. However, through the use of appropriate technical controls, the user does not have to consider the security consequences of viewing the page. Rather, the controls determine if the user can view the page. Secured systems should limit mobile code (applets) access to system resources such as the file system, the CPU, the network, the graphics display, and the browser’s internal state. Additionally, the system should garbage-collect memory to prevent both malicious and accidental memory leakage. The system must manage system calls and other methods that allow applets to affect each other as well as the environment beyond the browser.

Fundamentally, the issue of safe execution of code comes down to a concern with access to system resources. Any running program has to access system resources to perform its task. Traditionally, that access has been given to all normal user resources. Mobile code must have restricted access to resources for safety. However, it must be allowed some access to perform its required functions.

It is important to identify the resources the program needs and then provide a certain security sandbox that allows only a set of safe operations. Privileged applets can run outside the security sandbox and have extensive capabilities to access the client.

Applets that are not signed are restricted to the security sandbox, and they run only if the user accepts the applet. Applets that are signed by a certificate from a recognized certificate authority can either run only in the sandbox, or they can request permission to run outside the sandbox. In either case, the user must accept the applet’s security certificate; otherwise the applet is blocked from running.

Sandbox applets are restricted to the security sandbox and can perform the following operations:

- They can make network connections to the host they came from.
- They can easily display HTML documents using the showDocument method of the java.applet.AppletContext class.
- They can invoke public methods of other applets on the same page.
- Applets that are loaded from the local file system (from a directory in the user’s CLASSPATH) have none of the restrictions that applets loaded over the network do.
- They can read secure system properties.
- When launched by using the Java Network Launch Protocol (JNLP), sandbox applets can also perform the following operations:
  - They can open, read, and save files on the client.
  - They can access the shared system-wide clipboard.
  - They can access printing functions.
  - They can store data on the client, decide how applets should be downloaded and cached, and much more.

Sandbox applets cannot perform the following operations:

- They cannot access client resources such as the local filesystem, executable files, system clipboard, and printers.
- They cannot connect to or retrieve resources from any third-party server (any server other than the server it originated from).
- They cannot load native libraries.
- They cannot change the SecurityManager.
- They cannot create a ClassLoader.
- They cannot read certain system properties.

The plan could change the configuration of the entire system and could essentially void any certification that it is a secure, trusted system. In a project, configuration management often refers to the controlling of changes to the scope or requirements of the project. Scope creep caused by a lack of configuration management can lead to a project never being completed or structured because its requirements are continuously changing.

At its heart, CM is intended to eliminate the confusion and error brought about by the existence of different versions of artifacts. An artifact may be a piece of hardware or software or documentation. Changes are made to correct errors, provide enhancements, or simply reflect the evolutionary refinement of product definition. Without a well-enforced CM process, different team members can use different versions of artifacts unintentionally; individuals can create versions without the proper authority; and the wrong version of an artifact can be used inadvertently. Successful CM requires a well-defined and institutionalized set of policies and standards that clearly define:

- The set of artifacts (configuration items) under the jurisdiction of CM
- How artifacts are named
- How artifacts enter and leave the controlled set
- How an artifact under CM is allowed to change
- How different versions of an artifact under CM are made available and under what conditions each one can be used
- How CM tools are used to enable and enforce CM

These policies and standards are documented in a CM plan that informs everyone in the organization just how CM is carried out.

## Information Protection Management

If software is shared, it should be protected from unauthorized modification by ensuring that policies, developmental controls, and lifecycle controls are in place. In addition, users should be trained in security policies and procedures. Software controls and policies should require procedures for changing, accepting, and testing software prior to implementation. These controls and policies require management approval for any software changes and compliance with change control procedures.

## Security of Code Repositories

The security professional needs to be concerned with how to ensure the safety of code while it is being developed, as well as during usage and while at rest in the enterprise.

The security of code repositories can pose a challenge for the security professional for several reasons. With the move to offshoring application development, the code being developed may not be available to the enterprise directly, and the development environment may likewise be unavailable for management and inspection. The following is a summary of the security measures that GitHub has put in place to safeguard code hosted through it:

### Physical Security

Data center access limited to data center technicians and approved GitHub staff. Biometric scanning for controlled data center access. Security camera monitoring at all data center locations. 24/7 onsite staff that provides additional protection against unauthorized entry. Unmarked facilities to help maintain low profile. Physical security audited by an independent firm.

### System Security

System installation using hardened, patched OS. Dedicated firewall and VPN services to help block unauthorized system access. Dedicated intrusion detection devices to provide an additional layer of protection against unauthorized system access. Distributed Denial of Service (DDoS) mitigation services powered by industry-leading solutions.

### Operational Security

Our primary data center operations are regularly audited by independent firms against an ISAE 3000/AT 101 Type 2 Examination standard. Systems access logged and tracked for auditing purposes. Secure document-destruction policies for all sensitive information. Fully documented change-management procedures.

### Software Security

We employ a team of 24/7/365 server specialists at GitHub to keep our software and its dependencies up-to-date, eliminating potential security vulnerabilities. We employ a wide range of monitoring solutions for preventing and eliminating attacks to the site.

### Communications

All private data exchanged with GitHub is always transmitted over SSL (which is why your dashboard is served over HTTPS, for instance). All pushing and pulling of private data is done over SSH authenticated with keys, or over HTTPS using your GitHub username and password.

The SSH login credentials used to push and pull cannot be used to access a shell or
