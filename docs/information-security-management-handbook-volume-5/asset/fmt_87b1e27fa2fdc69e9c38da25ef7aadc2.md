
Few issues in the IT arena are regarded with more interest and zeal than virtualization. Virtualization refers to technologies that provide a layer of abstraction between computer hardware systems and the software that runs on them. By supplying a logical instead of a physical view of computing resources, virtualization solutions deliver several extremely useful functions. Most basically, they in effect make an operating system (`OS`) recognize a set of servers as a single pool of computing resources. They can also allow multiple operating systems (`OSs`) to run simultaneously on a single physical machine.

The beginnings of virtualization are in partitioning, which separates a single physical server into multiple logical servers. Once a physical server is divided, each logical server can run an OS and applications independently. In the 1990s, virtualization was used mainly to re-create end-user environments on a single piece of mainframe hardware. IT administrators who wanted to roll out new software, but first wanted see how it would work on a Windows NT or a Linux machine, used virtualized environments to create different test environments.

With the introduction of the x86 architecture and inexpensive PCs, virtualization lost much of its popularity and seemed to be little more than a passing fad of the mainframe era. The recent rebirth of virtualization on x86 platforms is more to the credit of the current market leader, VMware, than anything else. VMware developed the first hypervisor (a special type of virtual machine monitor) for the x86 architecture in the 1990s, serving as a strong impetus for the current virtualization boom.

# Types of Virtualization

There are four basic categories of virtualization: storage, network, application, and server virtualization, all of which are described in the following section.

## Storage Virtualization

Storage virtualization melds physical storage from multiple network storage devices so that they appear to be a single storage device. A good example of storage virtualization is Storage Area Networks (`SANs`), which typically use a large number of high-capacity storage devices to provide a large amount of virtualized storage space. They are a good example of storage virtualization.

## Network Virtualization

Network virtualization combines computing resources in a network by splitting the available bandwidth into independent channels that can be assigned to a particular server or device in real time.

## Application Virtualization

In application virtualization, an application is encapsulated and separated by the OS through a virtualization layer that intercepts the application’s file and other operations and redirects them to a virtual location.

## Server Virtualization

Server virtualization hides the physical nature of server resources, including the number and identity of individual servers, processors, and OSs, from the software running on them. This type of virtualization is by far the most common application of the technology today and is widely considered the primary driver of the market. When most individuals use the term “virtualization,” there is a good chance that they are referring to server virtualization.

# Benefits of Virtualization

The industry buzz around virtualization is just short of deafening. This “must-have” capability has fast become “gonna-get-it” technology, as new vendors enter the market and enterprise software providers weave it into the latest versions of their product lines. The reason is that the more virtualization is used, it continues to demonstrate additional tangible benefits, thereby augmenting its value.

## Server Consolidation

Server consolidation is the sweet spot in this market. Virtualization has become the cornerstone of just about every organization’s favorite money-saving initiative. Survey after survey show that between 60% and 80% of IT departments are pursuing server consolidation projects. The main reason is obvious—by reducing the numbers and types of servers that support their business applications, organizations are obtaining significant cost savings.

## Dynamic Load Balancing

Another major benefit of virtualization is dynamic load balancing capacity across multiple file systems and machines. Applications slow down or even come to a halt when processing bottlenecks occur on conventional machines. Dynamic load balancing helps ensure that such bottlenecks do not occur, thereby enabling applications to run continuously and without disruption. This is especially important for business-critical applications.

Still another benefit of virtualization is lowered power consumption, both from the servers themselves and the facilities’ cooling systems. Fuller use of existing, underutilized computing resources translates into a longer life for the data center and a fatter bottom line. Additionally, a smaller server footprint is simpler to manage.

# Information Security Benefits

Many potential benefits from an information security perspective also exist. These include the following:

## Process Isolation

Virtualization’s benefits go far beyond efficiency, functionality, and continuity in that virtualization offers much for information security. Virtual machines (`VMs`) can be used to isolate processes from attackers and malware, making systems and applications more difficult to successfully attack or infect. User access to applications can be tightly controlled in that virtualization allows special applications to be isolated from end-user applications, making unauthorized access to the former very difficult. Even if a system or application that runs in a virtualized environment is successfully attacked, any impact resulting from the attack is usually attenuated. The ability of attackers and malicious code to spread attacks (particularly malware-based attacks) is thereby reduced.

A good example of the usefulness of virtualization-supplied process isolation in information security is the way Java applets run in a “sandbox” environment in the Java VM. A sandbox is used when executable content has come from an external source that is not completely trusted. The sandbox restricts capabilities such as reading or writing to files on each local computer, starting or calling programs on each local computer, and obtaining network connectivity to the same computer from which applets have been loaded. Restrictions may include keeping a downloaded executable from being able to connect to the network from the machine to which it has been downloaded and from being able to reach the file system of the machine on which it runs. Most sandboxes place more restrictions on executables that have been remotely downloaded than those that have been locally downloaded.

## Use in Business Continuity and Disaster Recovery

Yet another benefit of virtualization is that it can greatly increase the efficiency and can greatly reduce the cost of business continuity and disaster recovery operations. Using virtualization in these arenas is still in its relative infancy. Still, virtualization can greatly reduce the cost of setting up and maintaining a duplicate data center in that fewer pieces of hardware need to be purchased. In addition, virtualization decreases procurement-related risks during outages and disasters. New VMs can be quickly created to support rapid recovery of business operations. Not to be overlooked also is that virtualization can greatly reduce electrical power demands when electricity is at a premium.

## Honeypot Support

Virtualization also supports honeypots: computers, services, or applications designed to serve as a decoy that attracts perpetrators. Not intended for legitimate users, honeypots appear to have something of value to attackers, behave as if vulnerable to a wide range of attacks, and appear to belong to a network, but are actually isolated. Almost every current honeypot tool is based on virtualization.
