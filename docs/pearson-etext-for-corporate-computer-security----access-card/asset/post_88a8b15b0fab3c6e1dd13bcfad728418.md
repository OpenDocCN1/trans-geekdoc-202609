
## MANAGEMENT IS THE HARD PART

One reason why people tend to focus on technology is that it is easier to think about technology than about management. Technology is visible, and there are many things that we can say about security technologies. Most of these technology concepts, furthermore, are well defined and are therefore easy to discuss.

Management, by contrast, is abstract. You cannot show pictures of devices or talk in terms of detailed diagrams or software algorithms. There are fewer general principles to discuss, and most of these principles cannot be put into practice without well-defined and complex processes.

Security management, however, is far more important than security technology. One official from the U.S. federal General Services Administration talked about helping a series of federal agencies reorganize their security technologies. In every case, the agencies enjoyed good security immediately. However, their security decayed rapidly. These agencies had the technology, but they lacked the management ability to make security work for the long term.

## COMPREHENSIVE SECURITY

It is not surprising that these agencies failed. For one thing, attackers only need to find a single way to get into the corporation. By contrast, Figure 2-3 shows that organizations need comprehensive security—closing all routes of attack to their systems to attackers. Comprehensive security does not come by accident.

Figure 2-3 The Need for Comprehensive Security (Study Figure)

![](img/073342643701cc54eb7875c41ab92ef2_69_0.png)

## WEAKEST-LINKS FAILURES

Another reason why security management is difficult is that some protections have many components that must all work in tandem for the countermeasure to succeed. Figure 2-4 gives an example. Here, the firewall administrator draws up filtering rules. The firewall then examines all packets passing through it. It drops provable attack packets and stores information about dropped packets in a log file. The firewall administrator should check the log file daily.

If there is any failure in this process, the firewall becomes useless. If an important filtering rule is omitted, provable attack packets will get through. Or, if the administrator fails to read log files daily, a problem may go undetected for weeks or months.

In chains of activities within a single countermeasure, everything must be done well. If even one step is not implemented well, security may seem good, but there will be no real protection. If the failure of a single element of a system will ruin security, this is called a weakest-link failure. In many cases, human actions are the weakest links in security protections.

Figure 2-4 Weakest-Link Failure (Study Figure)

![](img/073342643701cc54eb7875c41ab92ef2_70_0.png)

> If the failure of a single element of a system will ruin security, this is a weakest-link failure.

### THE NEED TO PROTECT MANY RESOURCES

A third reason why security management is difficult is that companies need to protect a large number of resources. Some of these are relatively well-defined assets such as databases and servers. Others are broad organizational processes, such as financial reporting and new product development. All are changing rapidly. As discussed later in this chapter, companies need to identify all of their resources and develop a security program for each one. This is a Herculean effort.

### Test Your Understanding

- 2.
  - a. For what reasons is security management hard?
  - b. What is comprehensive security, and why is it needed?
  - c. What are weakest-link failures?

### The Need for a Disciplined Security Management Process

Schneier’s use of the term *process* in the quotation at the beginning of this chapter is particularly important. Security is too complicated to be managed informally. Companies must develop and follow formal **processes** (planned series of actions) in security management. Some of these processes might include a process for annual security planning, processes for planning and developing individual countermeasures, and a process for handling incidents.

> Processes are planned series of actions.

Business strategists have long said that quality improvement is a never-ending process, not a one-time effort. One football coach noted that recruiting is like shaving; you miss one day, and you look like a bum. Security management is also a never-ending process.

One external factor that is motivating firms to formalize their security processes is a growing number of compliance laws and regulations. Many compliance regimes require firms to adopt specific formal governance frameworks to drive security planning and operational management. We will look at several of these governance frameworks later in this chapter.

- **Complex**
  - Cannot be managed informally
- **Need Formal Processes**
  - Planned series of actions in security management
  - Annual planning
  - Processes for planning and developing individual countermeasures
- **A Continuous Process**
  - Fail if let up
- **Compliance Regulations**
  - Add to the need to adopt disciplined security management processes

Figure 2-5 Security Management Is a Disciplined Process (Study Figure)

### Test Your Understanding

- 3.
  - a. Why are processes necessary in security management?
  - b. What is driving firms to use formal governance frameworks to guide their security processes?

### The Plan–Protect–Respond Cycle

If security processes must be managed comprehensively, we need a formal top-level security management process. Most firms today protect against threats by using a highest-level security management process called the plan–protect–respond cycle, shown in Figure 2-6.

**PLANNING** The cycle begins with planning. Without an excellent plan, you will never have comprehensive security. Of course, once plans are implemented, the results will feed back into planning. New threats and business conditions will also force companies to return to planning. Although the figure seems to indicate a neat and sequential process among the stages, all three activities take place simultaneously and constantly feed into one another. This chapter discusses planning in detail. We will also return to planning frequently throughout the book.

**PROTECTION** Protection is the plan-based creation and operation of countermeasures. Most of the security professional’s day will be spent in the protection phase, so it is no surprise that nearly all of this book is devoted to the creation and operation of controls.

- *Chapter 3* deals with cryptographic protections, which are used alone or as components of many other countermeasures. Given their use in other controls, we will look at them first. Before covering these chapters, many teachers will cover Module A, which reviews networking concepts.
- *Chapter 4* deals with protecting both wired and wireless networks.
- *Chapter 5* deals with access control and site security. Attackers who cannot reach your resources cannot harm them.
- *Chapter 6* deals with a particular family of access controls—firewalls. Although firewalls are not magic bullets for protection, they are enormously important (and somewhat complicated). It is important for IT security people to understand firewalls thoroughly.
- *Chapter 7* deals with host hardening. This will look at securing the host operating system.
- *Chapter 8* looks at application security. Most hackers today succeed by compromising application programs. If the attacker compromises an application, the attacker inherits the permissions of the application program. In many cases, these permissions give the attacker complete control of the computer.
- *Chapter 9* looks at how to protect data on hosts and servers. Data must be cleaned, protected, validated, and backed up frequently. Data is the lifeblood of the firm and must be protected.

For each type of protection, we need to manage the systems development life cycle (SDLC), which runs from initial planning through implementation. Information systems professionals often focus on the SDLC (see Figure 2-7). However, most of a countermeasure’s life consists of the operational stage after development. To teach security students to focus on the SDLC would be like training doctors in prenatal care and teaching them nothing about health care after birth. This book focuses on the management of controls through the entire **systems life cycle**, and this means focusing heavily on ongoing management after creation.

**RESPONSE** Even with great planning and meticulous protection, some attacks will succeed. Chapter 10 deals with incident response. Response is complex

Figure 2-6 The Plan–Protect–Respond Cycle for Security Management

![](img/073342643701cc54eb7875c41ab92ef2_72_0.png)
