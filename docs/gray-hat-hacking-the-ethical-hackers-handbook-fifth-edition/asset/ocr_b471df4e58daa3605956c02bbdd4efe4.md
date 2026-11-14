# PowerShell Portability

One of the nice aspects of PowerShell is that the modules are very portable and can be loaded in a variety of different ways. This give us the ability to load both system install modules and modules in other locations. We also have the ability to load modules from Server Message Block (SMB) shares as well as the Web.

Why is being able to load from these remote locations so valuable? We want to leave as few traces as possible, and we want to have to duplicate as little work as possible. This means we can leave items we will use frequently on an SMB share, or even a website, and then reference them from there. Because a script is just text, we don't have to worry about blocks for binary or similar file types. We can also obfuscate the code and then decode it on the fly, which potentially makes bypassing antivirus (AV) easier.

Because a script is just text, we can include it almost anywhere. Frequently, code sites such as GitHub are handy for this type of activity, as such sites have many business-related purposes. We can include our scripts in a repository or as basic gist commands that we load from inside our PowerShell environment to bootstrap other activities. PowerShell can even use a user's proxy settings, so this is a great way to establish persistence in an environment.

# Loading PowerShell Scripts

Before we can do any exploitation with PowerShell, you need to know how to execute scripts. In most environments, unsigned PowerShell scripts aren't allowed by default. We're going to take a look at this behavior so you can identify it, and then we'll look at how to bypass it you so can bootstrap any code you want to run.

# Lab 15-1: The Failure Condition

Before we look at how to get around security, we should take a look at how the security works when in action. To do this, we're going to build a very simple script on our Windows 10 box that we set up in Chapter 10, and then we'll try to execute this script. For our script, we're just going to create a directory listing of the root of C:\. First, we need to open up a command prompt as Administrator and then run the following the code:

```
c:\Users\User\Desktop>echo dir C:\ > test.ps1
c:\Users\User\Desktop>powershell .\test.ps1
powershell .\test.ps1
.\test.ps1 : File C:\Users\User\Desktop\test.ps1 cannot be loaded because
running scripts is disabled on this system.
For more information, see about_Execution_Policies at
http://go.microsoft.com/fwlink/?LinkID=135170.
At line:1 char:1
+ .\test.ps1
+ ~~~~~~~~~~
+ CategoryInfo          : SecurityError: (:) [], PSSecurityException
+ FullyQualifiedErrorId : UnauthorizedAccess
```