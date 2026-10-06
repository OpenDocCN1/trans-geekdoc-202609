# CHAPTER 8 CREATING AND MANAGING USER ACCOUNTS

Managing domain-based user account objects is pretty when using Active Directory Users and Computers. You'll now take a look at how to do it when the command prompt is your only option.

# MANAGING DOMAIN-BASED USER PROPERTIES AT THE COMMAND LINE

Let's look at how you can do the same using the command prompt. You'll be using a command called dsmod with the user option. You can view the help for this by running the following:

```
dsmod user /?
```

Notice that you have to use the DN of the user that you want to modify. Check out the previous tip to get the DistinguishedName of the user object on the Attribute Editor tab ("Obtaining the Easy Way" sidebar). That's all well and good if you have a GUI available to you. What happens if you don't? If you know the UPN of the user, then you can run dsquery to get the DN:

```
dsquery user -upn bigfirm.com
"CN=Steve Red,OU=Users,OU=Bigfirm,DC=bigfirm,DC=com"
```

Alternatively, you can run the dsquery using the SAM account name, which is the friendly name that you know as SRed:

```
C:\Administrator\dsquery user -samid SRed
"CN=Steve Red,OU=Users,OU=Bigfirm,DC=bigfirm,DC=com"
```

dsquery is a fairly powerful command, it's well worth getting to know it with /?
Now you can proceed with dsmod. Let's see how you can configure a home drive and a drive to map it for: Steve Red:

```
dsmod user "CN=Steve Red,OU=Users,OU=Bigfirm,DC=bigfirm,DC=com" -hmir \DC01\nhome$\SRed -hendrv P
```

This will configure a home drive (a network-based shared folder specific to this user) with the drive letter whenever Steve Red logs in.

You now want to configure the manager for Steve Red. You've just learned that Marcel Zehner has been promoted to the department head. You can do this by running the following:

```
dsmod user "CN=Steve Red,OU=Users,OU=Bigfirm,DC=bigfirm,DC=com" -mgr "CN=Marcel Zehner,OU=Users,OU=Bigfirm,DC=bigfirm,DC=com"
```

Notice that you didn't enter something like bigfirm or mezhner as the manager. You actually used the DN for the account that is the manager.

At first, dsmod looks like a difficult command to Play with it for a few minutes, and you'll see that it's not actually that bad.