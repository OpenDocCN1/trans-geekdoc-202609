
# Sandbox and Honeypot: Virtual Machines for Security

## Sandbox

A concept similar to virtualization is the notion of a sandbox. As its name implies, a **sandbox** is a protected environment in which a program can run and not endanger anything else on the system.

> **Sandbox: an environment from which a process can have only limited, controlled impact on outside resources**

The original design of the Java system was based on the sandbox concept, skillfully led by Li Gong [[GON97](#bib01.html#bib_234)]. The designers of Java intended the system to run code, called applets, downloaded from untrusted sources such as the Internet. Java trusts locally derived code with full access to sensitive system resources (such as files). It does not, however, trust downloaded remote code; for that code Java provides a sandbox, limited resources that cannot cause negative effects outside the sandbox. The idea behind this design was that web sites could have code execute remotely (on local machines) to display complex content on web browsers.

Java compilers and a tool called a bytecode verifier ensure that the system executes only well-formed Java commands. A class loader utility is part of the virtual machine monitor to constrain untrusted applets to the safe sandbox space. Finally, the Java Virtual Machine serves as a reference monitor to mediate all access requests. The Java runtime environment is a kind of virtual machine that presents untrusted applets with an unescapable bounded subset of system resources.

Unfortunately, the original Java design proved too restrictive [[GON09](#bib01.html#bib_233)]; people wanted applets to be able to access some resource outside the sandbox. Opening the sandbox became a weak spot, as you can well appreciate. A subsequent release of the Java system allowed signed applets to have access to most other system resources, which became a potential—and soon actual—security vulnerability. Still, the original concept showed the security strength of a sandbox as a virtual machine.

## Honeypot

A final example of a virtual machine for security is the honeypot. A **honeypot** is a faux environment intended to lure an attacker. Usually employed in a network, a honeypot shows a limited (safe) set of resources for the attacker; meanwhile, administrators monitor the attacker’s activities in real time to learn more about the attacker’s objectives, tools, techniques, and weaknesses, and then use this knowledge to defend systems effectively.

> **Honeypot: system to lure an attacker into an environment that can be both controlled and monitored**

Cliff Stoll [[STO88](#bib01.html#bib_594)] and Bill Cheswick [[CHE90](#bib01.html#bib_122)] both employed this form of honeypot to engage with their separate attackers. The attackers were interested in sensitive data, especially to identify vulnerabilities (presumably to exploit later). In these cases, the researchers engaged with the attacker, supplying real or false results in real time. Stoll, for example, decided to simulate the effect of a slow speed, unreliable connection. This gave Stoll the time to analyze the attacker’s commands and make certain files visible to the attacker; if the attacker performed an action that Stoll was not ready or did not want to simulate, Stoll simply broke off the communication, as if the unreliable line had failed yet again. Obviously, this kind of honeypot requires a great investment of the administrator’s time and mental energy.

Some security researchers operate honeypots as a way of seeing what the opposition is capable of doing. Virus detection companies put out attractive, poorly protected systems and then check how the systems have been infected: by what means, with what result. This research helps inform further product development.

In all these cases, a honeypot is an attractive target that turns out to be a virtual machine: What the attacker can see is a chosen, controlled view of the actual system.

These examples of types of virtual machines show how they can be used to implement a controlled security environment. Next we consider how an operating system can control sharing by separating classes of subjects and objects.

## Separation and Sharing

The basis of protection is separation: keeping one user’s objects separate from other users. John Rushby and Brian Randell [[RUS83](#bib01.html#bib_532)] note that separation in an operating system can occur in several ways:

*   **Physical separation**, by which different processes use different physical objects, such as separate printers for output requiring different levels of security
*   **Temporal separation**, by which processes having different security requirements are executed at different times
*   **Logical separation**, by which users operate under the illusion that no other processes exist, as when an operating system constrains a program’s accesses so that the program cannot access objects outside its permitted domain
*   **Cryptographic separation**, by which processes conceal their data and computations in such a way that they are unintelligible to outside processes

> **Separation occurs by space, time, access control, or cryptography.**

Of course, combinations of two or more of these forms of separation are also possible.

The categories of separation are listed roughly in increasing order of complexity to implement, and, for the first three, in decreasing order of the security provided. However, the first two approaches are very stringent and can lead to poor resource utilization. Therefore, we would like to shift the burden of protection to the operating system to allow concurrent execution of processes having different security needs.

But separation is only half the answer. We generally want to separate one user from another user’s objects, but we also want to be able to provide sharing for some of those objects. For example, two users with two bodies of sensitive data may want to invoke the same search algorithm or function call. We would like the users to be able to share the algorithms and functions without compromising their individual data. An operating system can support separation and sharing in several ways, offering protection at any of several levels.

*   **Do not protect**. Operating systems with no protection are appropriate when sensitive procedures are being run at separate times.
*   **Isolate**. When an operating system provides isolation, different processes running concurrently are unaware of the presence of each other. Each process has its own address space, files, and other objects. The operating system must confine each process somehow so that the objects of the other processes are completely concealed.
*   **Share all or share nothing**. With this form of protection, the owner of an object declares it to be public or private. A public object is available to all users, whereas a private object is available only to its owner.
*   **Share but limit access**. With protection by access limitation, the operating system checks the allowability of each user’s potential access to an object. That is, access control is implemented for a specific user and a specific object. Lists of acceptable actions guide the operating system in determining whether a particular user should have access to a particular object. In some sense, the operating system acts as a guard between users and objects, ensuring that only authorized accesses occur.
*   **Limit use of an object**. This form of protection limits not just the access to an object but the use made of that object after it has been accessed. For example, a user may be allowed to view a sensitive document but not to print a copy of it. More powerfully, a user may be allowed access to data in a database to derive statistical summaries (such as average salary at a particular grade level), but not to determine specific data values (salaries of individuals).
