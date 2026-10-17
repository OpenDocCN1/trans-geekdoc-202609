![](bbox=[0.107, 0.088, 0.894, 0.435])

**FIGURE 7.47** After adding the snap-in, we can right click in the middle window to click on New User.

Once the new user is created, we can add them to the Administrators group on the local machine, or the Domain Admins group in an AD environment. This action ensures that we will have an account active on the environment if the original account is removed or revoked.

To add a new account from the command line, we can use the `net` command. This tool will allow us to add a new account, and then add that account to other privileged groups, such as Administrators. The two following commands will complete these actions for us:

```
C:\Users\Administrator>net user newguy newpass /add
The command completed successfully.
```

```
C:\Users\Administrator>net localgroup administrators newguy /add
The command completed successfully.
```

```
C:\Users\Administrator>net localgroup administrators
Alias name    administrators
Comment       Administrators have complete and unrestricted access to
the computer/domain

Members
-------------------------------------------------------------------------------
Administrator
chris
newguy
The command completed successfully.
```