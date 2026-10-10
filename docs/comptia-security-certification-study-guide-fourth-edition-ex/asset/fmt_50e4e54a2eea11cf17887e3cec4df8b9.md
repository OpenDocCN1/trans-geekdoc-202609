
You can also implement account expiration with the account if the account is for a temporary employee. For example, an accounting firm may decide to hire a new temporary accountant for the tax season, but when tax season is over the employee is let go. When creating this account on your network, be sure to set the account expiration date (see [Figure 11-4](#ch11.xhtml#ch11fig4)) so that when the day of departure arrives, the account is no longer valid.

![Image](f0498-01.jpg)

**FIGURE 11-4**  
Setting the account expiration for a user account

### Time-of-Day Restrictions

Another example of a restriction that can be placed on a user account is a *time-of-day* restriction for account logons. Most environments allow you to specify as a property of the user account what hours the employee is allowed to be logged on to the system (see [Figure 11-5](#ch11.xhtml#ch11fig5)). The benefit of this is that you can ensure the employee is not accessing network resources after hours.

![Image](f0498-02.jpg)

**FIGURE 11-5**  
Setting the logon hours to control when the user can log on to the network

### Account Lockout

It is critical when implementing restrictions on your user accounts that you look at implementing an account lockout policy. An account lockout policy specifies that after a certain number of failed logon attempts, the account will be locked so it cannot be used. In the policy, you also specify how long the account is locked—you can set a time in minutes or specify to have the account locked until the administrator unlocks the account. [Figure 11-6](#ch11.xhtml#ch11fig6) displays the account lockout policy settings in Windows.

![Image](f0499-01.jpg)

**FIGURE 11-6**  
Account lockout will lock an account after a certain number of failed logons.

Three settings are used to configure the account lockout policy:

- **Account lockout threshold** Specifies how many failed logons can occur before the account is locked.
- **Account lockout duration** Specifies how long to lock the account. In Windows settings, a value of `0` configures the lockout until the administrator unlocks the account.
- **Reset account lockout counter after** After the user fails to log on, the counter is incremented by one until the account is locked or until the user successfully logs on. You can configure when the counter is reset to zero.

### Account Disablement

It is important as a security professional that you stress to the network administrators that unused accounts should be disabled so that they cannot be used. This will help protect the account from unauthorized use by employees or even hackers. Be sure to disable accounts when employees go on leave, are suspended from duty, or are terminated.

### View Account Details

One of the most useful commands I have come across when working with user accounts or troubleshooting user accounts is the `net user` command. When using the `net user` command, you can supply the name of a user account and then add the `/domain` switch so that the command will retrieve Active Directory account information such as the account name, account expiration time, password information, and workstation restrictions.

The following code listing displays the account details for the Tanya user account:

![Images](p0500-01.jpg)

![Image](exam.jpg)

**The Security+ exam expects you to know the different types of account policies listed next, especially geofencing, geotagging, and geolocation.**

## Account Policy Enforcement

You should be familiar with a number of concepts and best practices as they relate to access control. Some of these topics have been discussed in detail already in this chapter, but I wanted to create a summary of best practices for implementing account policies within the organization.

- **Shared accounts** It is critical that all users have their own account so that permissions can be uniquely applied and you can audit each individual's actions.
- **Credential management** Ensure that you have a central credential management tool and a policy surrounding how frequently users must change passwords.
- **Group policy** Group policies should be used to deploy security settings to all the servers and clients on the network.
- **Password complexity** Ensure you are using complex passwords for any accounts on systems and for network access. These passwords are harder to crack than noncomplex passwords.
- **Expiration** Ensure that passwords expire after a period of time and that users must set new passwords. Also, make sure you set the expiration date of any temporary user accounts created.
- **Recovery** Ensure you are able to recover any accounts that are deleted or can reset any passwords that are forgotten.
- **Disablement** Be sure to disable any unnecessary accounts and to disable accounts for employees going on leave.
- **Lockout** Configure an account lockout policy so that if the wrong password is typed after three tries, the account is locked (unusable) until the administrator unlocks it.
- **Password history** An important password setting to configure is the password history option—ensure that your systems are preventing users from using the same passwords by keeping previous passwords in a history.
- **Password reuse** Determine what your organization's policy is on reusing passwords and be sure to configure the password history to enforce that policy.
- **Password length** Most organizations require a minimum password length of eight characters.
- **Generic account prohibition** Similar to the shared account point made earlier, ensure that there are no generic accounts created for users or the system to share, as it makes it difficult to audit the actions.
- **Network location** Your company may want to implement access control policies that restrict access to specific resources from a specific network location. For example, in order to access a sensitive server, the user must be connected to the secure network. Another example we mentioned earlier is that in Azure you can block access based on the IP address coming from a specific country. Also, streaming services such as Netflix can block access to content based on the country you are in.
- **Geofencing** Geofencing is a feature that allows administrators of software to define GPS coordinates that create a boundary (or virtual fence). When a device running the software goes outside the boundaries, an alarm is triggered.
- **Geotagging** Geotagging is identifying your location with a posting in a social media app such as Facebook or Instagram. As a company policy, you may wish to restrict the use of geotagging and posting of company information on social media.
- **Geolocation** Geolocation is the term for identifying the geographic location of an item such as a mobile phone. For example, once the geolocation (GPS coordinates) of a mobile phone is determined, you can then associate that with a street address using mapping technologies.
- **Time-based logins** As mentioned earlier, you can limit what time of day a user may log in to the system. You may have policies in place that limit login hours for employees in different job roles.
- **Access policies** An access policy is a policy that defines the level of access that each user account gets to a system or information.
- **Account permissions** You should have policies in place that specify the different types of permissions accounts are to have to systems and data across the network.
- **Account audits** You should audit activity of your user accounts. This includes login activity, access to sensitive data, and any changes to the privileges of the user.
