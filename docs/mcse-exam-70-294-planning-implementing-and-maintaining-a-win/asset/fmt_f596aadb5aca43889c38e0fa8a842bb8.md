
15. You want to move a user account from an OU located in one domain, to an OU located in another domain. Which of the following tools will you use to perform this task?
A. Active Directory Users and Computers
B. Active Directory Domains and Trusts
C. `DSMOVE`
D. `MOVETREE`

## Self Test Quick Answer Key
For complete questions, answers, and explanations to the Self Test questions in this chapter as well as the other chapters in this book, see the Self Test Appendix.
1. C
2. A
3. D
4. A
5. C
6. C
7. C
8. A, D
9. A
10. D
11. B, C
12. B
13. B
14. D
15. D

# Chapter 3
## MCSE/MCSA 70–294: Creating User and Group Strategies
Exam Objectives in this Chapter:
3.1 Plan a security group strategy.
3.2 Plan a user authentication strategy.
3.2.1 Plan a smart card authentication strategy.
3.2.2 Create a password policy for domain users.
☑ [Summary of Exam Objectives](#B978193183694450009X.xhtml#s0315)
☑ [Exam Objectives Fast Track](#B978193183694450009X.xhtml#s0320)
☑ [Exam Objectives Frequently Asked Questions](#B978193183694450009X.xhtml#s0345)
☑ [Self Test](#B978193183694450009X.xhtml#s0350)
☑ [Self Test Quick Answer Key](#B978193183694450009X.xhtml#s0380)

## Introduction
Knowing how to create users and groups and the procedures for moving and managing them is only half the battle when it comes to effectively using these security objects on the network. The network administrator must also be able to develop strategies for authenticating the identity of anyone who uses network resources, and plan for how to use groups most effectively to provide the security and access needed.
In today’s connected world, proof of your identity is often required to ensure that someone else is not trying to use your identity. It used to be that a username and password were sufficient to authenticate someone to a network. However, password authentication is only the first step in true authentication of a user’s identity in today’s environment. You must have a well-defined password policy, which includes account lockout, password rotation, and other options to ensure limited access to your network. In this chapter, we develop a password policy for your Windows Server 2003 network. However, sometimes passwords and password policies are not enough, and we have to take authentication to the next plateau.
Tools such as biometric devices, token devices, voice identification, and smart cards are becoming much more mainstream for user authentication as the price continues to drop and acceptance continues to rise. If you have ever seen a large data center, you have probably seen biometric tools such as thumbprint or palm scanners at entryways. Other sites use smart card readers for access to public computer kiosks. For example, Sun Microsystems requires the use of smart cards for students to sign into class each day. Each student is assigned a smart card and a four-digit personal identification number (PIN) that they must use to sign in.
In Windows Server 2003 and Windows XP, Microsoft has implemented smart card technology into the operating system as well as Active Directory to provide you with enhanced authentication abilities, and add security to your network. As a Windows Server 2003 MCSE, you are required to understand how to implement smart card technologies and manage resources using smart cards.
An effective authentication strategy works hand in hand with a security group strategy. A well-designed group strategy will ensure that users receive only the appropriate level of access to resources on the network. It will also reduce the workload of the administrator and make it easier to manage large numbers of users. Microsoft has a number of fairly complicated models that you will be expected to follow when designing group strategy in an Active Directory environment.

## Creating a Password Policy for Domain Users
Since they are largely created and managed by end users, passwords have the potential to be the weakest link in any network security implementation. You can install all the high-powered firewall hardware and virtual private network (VPN) clients you like, but if your vice president of sales uses the name of her pet St. Bernard as her password for the customer database system, all your preventative measures might be rendered useless. Since passwords are the “keys to the kingdom” of any computer system, the database that Windows Server 2003 uses to store password information will be a common attack vector for anyone attempting to hack your network. Luckily, Windows Server 2003 offers several means to secure passwords on your network. A combination of technical measures, along with a healthy dose of user training and awareness, will go a long way toward protecting the security of your network systems.

### Creating an Extensive Defense Model
In modern computer security, a system administrator needs to create a security plan that uses many different mechanisms to protect a network from unauthorized access. Rather than relying solely on a hardware firewall and nothing else, defense in depth would also use strong passwords as well as other mechanisms on local client PCs, in the event that the firewall is compromised. The idea is to create a series of security mechanisms so that if one is circumvented, other systems and procedures are in place to help impede an attacker. Microsoft refers to this practice as an extensive defense model. The key points of this model are the following:
■ A viable security plan needs to begin and end with user awareness, since a technical mechanism is only as effective as the extent to which the users on your network adhere to it. As an administrator, you need to educate your users about how to best protect their accounts from unauthorized attacks. This can include advice about not sharing passwords, not writing passwords down or leaving them otherwise accessible, and making sure to lock a workstation if the user needs to leave it unattended for any length of time. You can spread security awareness information via e-mail, posters in employee break areas, printed memos, or any other medium that will get your users’ attention.
■ Use the system key utility (`syskey`) on all critical machines on your network. This utility, discussed later in this chapter, provides additional encryption for password information that is stored in the Security Accounts Manager (`SAM`) and Active Directory databases.
■ Educate your users about the potential hazards of selecting the Save My Password feature or any similar feature on mission-critical applications, such as remote access or VPN clients. Make sure that users understand that the convenience of saving passwords on a local workstation is far outweighed by the potential security risk if the workstation becomes compromised.
■ If you need to create one or more service accounts for applications to use, make sure that these accounts have different passwords. Otherwise, compromise of one account might leave multiple network applications open to attack.
■ If you suspect that a user account has been compromised, change the password immediately. If possible, consider renaming the account entirely, since it is now a known attack vector.
■ Create a password policy and/or account lockout policy that is appropriate to your organization’s needs. It’s important to strike a balance between security and usability in designing these types of account policies. For example, a 23-character minimum password length might seem like a good security measure on paper, but any security offered by such a decision will be rendered worthless when your users leave their impossible-to-remember 23-character passwords pasted to their monitors on sticky notes.

#### Strong Passwords
