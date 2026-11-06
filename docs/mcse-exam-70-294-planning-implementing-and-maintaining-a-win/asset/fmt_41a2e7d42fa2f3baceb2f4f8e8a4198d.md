
☑ B, C, and E. Microsoft considers a password weak if it is all lowercase, contains any portion of the user’s account name (in this case, jronick), or contains a word found in the English dictionary (such as soprano or new); therefore, Answers B, C, and E are correct.
![wrong](images/wrong.png) Answers A and D are incorrect because both of these passwords meet the criteria for strong passwords. They are at least seven characters long and contain a mix of uppercase, lowercase, numeric, and non-alphanumeric characters.

### 4. You have implemented a password policy that requires your users to change their passwords every 30 days and retains their last three passwords in memory. While sitting in the lunch room, you hear someone advise his coworker that all she needs to do to get around that rule is to change her password four times so that she can go back to using the password that she is used to. What is the best way to modify your domain password policy to avoid this potential security liability?
A. Increase the maximum password age from 30 days to 60 days.
B. Enforce password complexity requirements for your domain users’ passwords.
C. Increase the minimum password age to seven days.
D. Increase the minimum password length of your users’ passwords.
☑ C. If your password policy retains three unique passwords in memory, this setting can help prevent your users from changing their passwords four times in rapid succession so that they can change them back to their initial passwords. A minimum password age of seven days will force users to wait at least seven days before they can change their passwords. Very few users will want to be forced to use a new password every week for three weeks, just to get back to their favorite.
![wrong](images/wrong.png) Answer A is incorrect. Increasing the maximum password age will not circumvent the security issue that is allowing users to change back to their favorite password. Answer B is also incorrect. Password complexity has nothing to do with how often a password can be changed. Answer D is incorrect because the minimum password length setting also has nothing to do with how often a password can be changed.

### 5. You are a new network administrator for a Windows Server 2003 domain. In making user support calls, you have noticed that many users are relying on simplistic passwords such as their children’s or pets’ names. Passwords on the network are set to never expire, so some users have been using these weak passwords for years. You change the default Group Policy to require strong passwords. Several weeks later, you notice that the network users are still able to log on using their weak passwords. What is the most likely reason why the weak passwords are still in effect?
A. You must force the users to change their passwords before the strong password settings will take effect.
B. The Group Policy settings have not replicated throughout the network yet.
C. Password policies need to be set at the organizational unit (OU) level, not the domain level.
D. The users reverted back to their passwords the next time they were prompted to change them.
☑ A. The password complexity policy only applies to new or changed passwords within the domain. It is not applied retroactively to existing passwords. If your users’ passwords are set to never expire, they will not be forced to change to strong passwords.
![wrong](images/wrong.png) Answer B is incorrect. Active Directory replication should not take several weeks to replicate, even on the largest networks. Answer C is also incorrect. Password policies can only be set at the domain level, not on individual OUs. Answer D is incorrect because Windows would reject passwords that did not meet the new complexity requirements.

## Creating User Authentication Strategies

### 6. You have created an e-commerce Web application that allows your customers to purchase your company’s products via the Internet. Management is concerned that customers will not feel comfortable providing their credit card information over the Internet. What is the most important step to secure this application so that your customers will feel confident that they are transmitting their information securely and to the correct Web site?
A. Use IP restrictions so that only your customers’ specific IP addresses can connect to the e-commerce application.
B. Issue each of your customers a smart card that they can use to authenticate to your e-commerce Web site.
C. Place your company’s Web server behind a firewall to prevent unauthorized access to customer information.
D. Install a Secure Sockets Layer (SSL) certificate on your Web server.
☑ D. Installing an SSL certificate provides mutual authentication so that your customers will know that they are communicating with the correct Web site and not being redirected to another site that’s being used to steal their information.
![wrong](images/wrong.png) Answer A is impractical because your customers (and their associated IP addresses) will change from day to day as you get new referrals. Answer B is also incorrect. The costs associated with supporting smart cards for your customers in this environment could be quite high, which makes Answer D more appropriate. Answer C, although a good security practice, is incorrect because it will not protect your customers’ data while it is being transmitted to and from your Web site. Protecting data during transit requires the kind of encryption offered by an SSL certificate.

### 7. Your network environment consists of Windows 2000 Professional, Windows XP Professional, and Windows NT 4.0 Workstation computers. You have just upgraded all domain controllers to Windows Server 2003. The domain and forest functional levels are both set to Windows Server 2003. The company does not use any Web applications or services. Which of the following authentication protocols will be used on the network? (Choose all that apply.)
A. Digest
B. NTLM
C. Kerberos
D. SSL
☑ B, C. Answer B is correct. NTLM will be used for authentication involving the pre-Windows 2000 computers in the domain. In the scenario, this means that the Windows NT 4.0 Workstation computers will use NTLM for authentication. Answer C is also correct. Kerberos is the default protocol for all Windows 2000 and later computers. Therefore, the network’s Windows 2000 Professional and Windows XP Professional clients will use Kerberos for authentication.
![wrong](images/wrong.png) Answers A and D are incorrect. Both Digest authentication and SSL are used in a Web services environment. The question states that there are no Web applications or services in use.

### 8. You’ve decided to implement Web-based authentication. You have a wide range of domains, domain controllers, and domain functional levels in your enterprise Windows Server 2003 forest. Because you are a homogenous Windows environment, you decide to implement digest authentication. Which of the following requirements must you keep in mind when planning to implement digest authentication? (Choose all that apply.)
A. Digest authentication requires IE 5 or later on the clients.
B. There must be at least one Windows Server 2003 DC in the IIS server’s domain.
C. User passwords must be stored with reverse encryption.
D. There must be at least one Windows 2000 or later DC in the IIS server’s domain.
☑ A, C, D. Answer A is correct. Clients must be using Internet Explorer 5 or later to use digest authentication. Answer C is also correct. Digest authentication requires user passwords to be stored with reversible (cleartext) encryption. Answer D is correct. Digest authentication requires at least one Windows 2000 or later domain controller in the domain that the IIS server is a member of.
