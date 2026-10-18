
other resources you like to get started.

Make certain you consider not only shutting down access but also the possibility of proprietary research material existing on the faculty/staff member's workstation.

## Exercise 10.6: Student Lab Use Policy

Considering the material in this chapter, create a set of policies for acceptable use of computer lab computers.

Make sure to specify web use, email use, and any other acceptable uses.

Carefully spell out unacceptable usage. (For example, is game playing acceptable?)

## Projects

### Project 10.1: Examining Policies

- Examine the following web resources that discuss security policies:
  - EarthLink acceptable use policy: www.earthlink.net/about/policies/use/
  - SANS Institute policies: www.sans.org/resources/policies/
  - Key Elements of an Information Security Policy: Information Security Policy World
- Summarize the main theme of these policy recommendations. Pay particular attention to any area where these recommendations differ from or exceed the recommendations of this chapter.
- Choose which policy recommendation you believe is the most secure and state the reasons for your choice.

### Project 10.2: Real-World Security Policies

Ask a local business or your college to let you see its security policies. Study the policies carefully.

- Summarize the main theme of these policy recommendations. Pay particular attention to any area where these recommendations differ from or exceed the recommendations of this chapter.
- Choose which policy recommendation you believe is the most secure and state the reasons for your choice.

### Project 10.3: Creating Security Policies

Note: This project works well as a group project.

At this point in the book, you have studied security, including policies. In this chapter and the preceding exercises and projects, you have examined several policies from various web resources and the policies of some actual organizations.

Expand the brief policies you created for the exercises in this chapter to create an entire working security policy for your college. You will need to add administrative policies, development policies, and more.

Hector is a security administrator for a defense contractor. This business frequently works with highly sensitive classified material. Hector has developed a policy for departing employees. This policy handles everything mentioned in this chapter:

- All logon accounts to any server, VPN, network, or other resource are disabled.
- All keys to the facility are returned.
- All accounts for email, Internet access, wireless Internet, cell phones, and so on are shut off.
- Any accounts for mainframe resources are canceled.
- The employee's workstation hard drive is searched.

Given the highly sensitive nature of the work at this company, what other actions might you add to this policy?

## Chapter 11. Network Scanning and Vulnerability Scanning

After reading this chapter and completing the exercises, you will be able to do the following:

- Understand how to secure a system
- Probe a system for vulnerabilities
- Use vulnerability scanning tools
- Evaluate potential security consultants

At this point, it should be clear that it is necessary to periodically assess any system for vulnerabilities. The first part of this chapter discusses the essential steps that you should follow in assessing a system for vulnerabilities. The purpose of this chapter is to get someone who is new to computer security to begin thinking about these issues. This chapter is not meant to be a comprehensive treatment of the subject or a substitute for getting an expert consultant. In fact, most security topics, such as disaster recovery, cryptography, and policies, have had entire volumes written on them. This chapter should give you a basic blueprint you can follow. Specific details will depend on your particular environment, budget, skills, and security needs. The second part of this chapter discusses various tools you can use to scan your network for vulnerabilities.

In this book, you have thus far examined a number of threats to individual computers and networks. You have also learned about specific defenses against each of these dangers. However, you have not yet looked at a comprehensive approach to security. In the second part of this chapter, you will learn about many of the security procedures that can be implemented to provide an environment with more secure computing. Note that this chapter is about overall procedures that you need to perform in securing a system rather than specific step-by-step techniques.

### Basics of Assessing a System

Knowing where to begin with system security can be daunting for those new to security. To keep it simple and easy to remember, the stages of assessing a system’s security can be categorized into the six Ps:

- Patch
- Ports
- Protect
- Policies
- Probe
- Physical

The first rule of computer security is to check patches. This is true for networks, home computers, laptops, tablets, smart phones, ... literally any computer. The operating system, database management systems, development tools, Internet browsers, and so forth all need to be checked for patches. In a Microsoft environment, this should be easy, as the Microsoft website has a utility that will scan your system for any required patches to the browser, operating system, or Office products. It is a very basic tenet of security to ensure that all patches are up to date. This should be one of the first tasks when assessing a system.

It is also important to consider the types of patches. The most important patches are labeled important or critical. (Microsoft labels them critical, but other vendors may use another designation.) These patches must be applied; without them, your system simply is not secure. Recommended patches should be applied unless you have some compelling reason not to. Finally, optional patches usually enhance or correct some minor functionality in the system but are not necessary for security. Your system will not be vulnerable without these.

While home users might benefit from automatic patching, automatic patching is not appropriate for network administrators. It is always possible that a patch might interfere with some custom software or some system configuration. Therefore, patches need to be deployed first to a test system to ensure that they do not disrupt any other software or configurations. Once the testing is complete, you can push a patch out to the production network. Even then, patches should be rolled out in stages, in case something goes wrong. This does not mean that patches are not applied in a timely manner. If there is a critical patch, it must be tested promptly so that it can be rolled out to the production network.

### FYI: Patching and Applications

> Whenever there is a patch to an operating system or application, there is documentation (sometimes in a Read Me file, sometimes at the download site) that indicates what the patch is fixing and that lists any known adverse interactions with other applications. You should always read this documentation before installing a patch. In most cases, the problems are minimal and often involve obscure situations. But it is always good to ensure that a service or an application upon which you are dependent will not be adversely impacted.

### FYI: Ports on Routers

> One security flaw seen in many organizations that are otherwise security conscious is a failure to close ports on routers. This is particularly a problem for large organizations with wide area networks (WANs) spread over multiple locations. The routers between locations should be filtered but too often are not.

Once you have ensured that all patches are up to date, the next step is to set up a system to ensure that they are kept up to date. One simple method is to initiate a periodic patch review during which, at a scheduled time, all machines are checked for patches. There are also automated solutions that can patch all systems in an organization. It is imperative that all machines be patched, not just the servers.

An important issue is when to patch. For home users, it is usually recommended that automatic patching be turned on so that their systems get patched as soon as patches are available. However, this is not recommended for network administrators. It is entirely possible that a particular patch might not be compatible with some software on
