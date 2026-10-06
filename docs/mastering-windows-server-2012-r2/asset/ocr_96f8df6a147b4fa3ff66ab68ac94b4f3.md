# USING MICROSOFT'S FREE MIGRATION TOOL: ADMT 35

The netdom.command comes installed with Windows Server 2012, but earlier versions had it available in the Support Tools. Microsoft released a later version of Support Tools after Windows Server 2003 Service Pack 2, so be sure to search its site for the latest version.

The following commands are run to deduce SID filtering. The /quarantine:no parameter does the trick. You should be able to deduce how SID filtering will be enabled:

```
Rem performed on dc01.bigfirm.com
netdom trust otherdomain/domain:bigfirm /quarantine:No
user:administrator /password:Pssword
```

```
Rem performed on DC2003.OtherDomain.local:
netdom trust bigfirm /domain:otherdomain /quarantine:No
user:administrator /password:Pssword
```

# Getting Both Sides ADMT-friendly

ADMT can be an absolutely frustrating nightmare of a program because of its needs. A program that takes information is fairly private and internal to a domain—user accounts and passwords—and reveals it to a completely different domain. Before ADMT can do that, you'll have to open a number of locked doors. The following is what you have to do.

# PUTTING A DOMAIN IN EACH OTHER'S ADMINISTRATORS GROUPS

The ADMT utility needs an account that is both a member of the Domain Admins group in the target domain, Bigfirm.com, and a member of local Administrator groups of servers and workstations in the source domain, OtherDomain.local. This will allow ADMT utility to perform changes to permissions, user rights, and other nifty stuff that powerful administrators have the privileges to do. In this example, we created an account with the imaginative name of ADMT in Bigfirm.com and assigned it to the Domain Admins group. Using the trust relation between the two domains, it was also assigned to the built-in Administrators group in OtherDomain.local and the local Administrators group on Win7-bigfirm.com.

On the source domain, OtherDomain.local, a similar requirement is needed for the Password Encryption Service (PES). This is an additional service that will read the password of migrating account, and store it with its properties. It needs to be a member of the Domain Admins group in the source domain, OtherDomain.local, and a member of the built-in Administrators group in the target domain, Bigfirm.com. Over at Bigfirm.com, we created an account with an equally imaginative name, PES, in OtherDomain.local. We opened Active Directory Users and Computers and drilled down to the Built-in folder to find the Administrators group. Then we made the PES account member of that.

# TURNING ON AUDITING

ADMT has some tricky auditing, preferably so that it can monitor how it's doing. The source domain—the one that are being copied from, OtherDomain.local—needs both success and failure audits for user and group management.

On the target and source machines (W2K8DC.Bigfirm.com and DC2003.OtherDomain.local), we enable auditing by modifying a group policy called Default Domain Controller Policies. In a