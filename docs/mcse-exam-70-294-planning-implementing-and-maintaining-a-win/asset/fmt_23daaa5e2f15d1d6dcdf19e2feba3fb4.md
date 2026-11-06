
## Password Policy Configuration

### 3. Navigate to Password Policy

Navigate to `Computer Configuration | Windows Settings | Security Settings | Account Policies | Password Policy`. You’ll see the screen shown in [Figure 3.5](#B978193183694450009X.xhtml#f0030).

Using password policies, you can configure the following settings:

![Figure 3.5 Configuring Password Policy Settings](images/B978193183694450009X/f03-05-9781931836944.jpg)

Figure 3.5 Configuring Password Policy Settings

■ `Enforce password history` This option allows you to define the number of unique passwords that Windows will retain. This prevents users from using the same passwords again when their passwords expire. Setting this number to at least three prevents users from alternating between two passwords when they’re prompted to change their passwords.

■ `Maximum password age` This setting defines how frequently Windows will prompt your users to change their passwords.

■ `Minimum password age` This setting ensures that passwords cannot be changed until they are more than a certain number of days old. This works in conjunction with the first setting by preventing users from repeatedly changing their passwords in an effort to circumvent the “Enforce password history” policy. For example, if you specify that password history is enforced and set the number of remembered passwords at 5, a user can simply change his or her password six times in rapid succession and reuse a favorite password.

■ `Minimum password length` This option dictates the shortest allowable length that a user’s password can be. Remember that longer passwords are typically stronger than shorter ones. Enabling this setting also prevents users from setting a blank password.

■ `Password must meet complexity requirements` This policy setting, when activated, forces any new passwords created on your network to meet the following requirements: minimum of six characters in length, containing three of the following: uppercase letters, lowercase letters, numeric digits, and non-alphanumeric characters such as %, !, and \[.

■ `Store passwords using reversible encryption` This option stores a copy of the user’s password within the Active Directory database using reversible (cleartext) encryption. This is required for certain message digest functions and authentication protocols to work properly. This policy is disabled by default and should be enabled only if you are certain that your environment requires it.

### 4. Configure Policy Items

For each item that you want to configure, right-click the item and select `Properties`. In this case, we’re enforcing a password history of three passwords. In the screen shown in [Figure 3.6](#B978193183694450009X.xhtml#f0035), place a check mark next to `Define this policy setting`, and then enter the appropriate value.

![Figure 3.6 Defining the Password History Policy](images/B978193183694450009X/f03-06-9781931836944.jpg)

Figure 3.6 Defining the Password History Policy

### Modifying a Password Policy

You can modify an existing Windows Server 2003 password policy by navigating to the policy section listed in the previous exercise and making the changes. New and modified password policies are only enforced when passwords are changed. Therefore, altering password policy does not place an immediate burden on users. Typically, users won’t notice the policy change until their passwords expire and they are forced to set new ones. If you need to ensure that all passwords are forced to comply with the new policy, you can set the `User must change password at next logon` option in the properties of the user accounts you administer.

### Applying an Account Lockout Policy

In addition to setting password policies, you can configure your network so that user accounts will be locked out after a certain number of incorrect logon attempts. This can be a soft lockout, in which the account will be re-enabled after an administrator specified period of time. Alternatively, it can be a hard lockout in which user accounts can only be re-enabled by the manual intervention of an administrator. Before implementing an account lockout policy, you need to understand the potential implications for your network.

An account lockout policy will increase the likelihood of deterring a potential attack against your network, but you also run the risk of locking out authorized users. You need to set the lockout threshold high enough so that authorized users will not be locked out of their accounts due to simple human error, such as mistyping their passwords before they’ve had their morning coffee. Three to five is a common threshold. You should also remember that if a user changes his or her password on Computer A while already logged on to Computer B, the session on Computer B will continue to attempt to log on using the old (now incorrect) password. This will eventually lock out the user account and can be a common occurrence, especially in the case of service and administrative accounts. `Exercise 3.03` details the necessary steps in configuring account lockout policy settings for your domain.

### Exercise 3.03 Creating an Account Lockout Policy

1. From the Windows Server 2003 desktop, click `Start | Administrative Tools | Active Directory Users and Computers`.

2. Right-click the domain you want to administer, and then select `Properties`.

3. Select the `Default Domain Policy`, and dick the `Edit` button.

4. Navigate to the account lockout policy by clicking `Computer Configuration | Windows Settings | Security Settings | Account Policies | Account Lockout Policy`. You’ll see the screen shown in [Figure 3.7](#B978193183694450009X.xhtml#f0040).

Using `Account Lockout Policy`, you can configure the following settings:

![Figure 3.7 Account Lockout Policy Objects](images/B978193183694450009X/f03-07-9781931836944.jpg)

Figure 3.7 Account Lockout Policy Objects

■ `Account lockout duration` This option determines the amount of time that a locked-out account will remain inaccessible. Setting this option to 0 means that the account will remain locked out until an administrator manually unlocks it. Select a lockout duration that will deter intruders without crippling your authorized users; 30 to 60 minutes is sufficient for most environments.

■ `Account lockout threshold` This option determines the number of invalid logon attempts that can occur before an account will be locked out. Setting this option to 0 means that accounts on your network will never be locked out.

■ `Reset account lockout counter after` This option defines the amount of time in minutes after a bad logon attempt that the “counter” will reset. If this value is set to 45 minutes, and user `jsmith` types his password incorrectly two times before logging on successfully, his running tally of failed logon attempts will reset to 0 after 45 minutes have elapsed. Be careful not to set this option too high, or your users could lock themselves out through simple typographical errors.

5. For each item that you want to configure, right-click the item and select `Properties`. To illustrate, we create an `Account lockout threshold` of three invalid logon attempts. In the screen shown in [Figure 3.8](#B978193183694450009X.xhtml#f0045), place a check mark next to `Define this policy setting`, and then enter the appropriate value.

![Figure 3.8 Configuring the Account Lockout Threshold](images/B978193183694450009X/f03-08-9781931836944.jpg)

Figure 3.8 Configuring the Account Lockout Threshold

![b03-04-9781931836944](images/B978193183694450009X/b03-04-9781931836944.jpg) Exam Warning

The issue of password synchronization described in the previous paragraph is not an issue for organizations that are only running Windows Server 2003 operating systems.

## Creating User Authentication Strategies
