
## PowerShell Portability

One of the nice aspects of PowerShell is that the modules are very portable and can be loaded in a variety of different ways. This gives us the ability to load both system install modules and modules in other locations. We also have the ability to load modules from Server Message Block (SMB) shares as well as the Web.

Why is being able to load from these remote locations so valuable? We want to leave as few traces as possible, and we want to have to duplicate as little work as possible. This means we can leave items we will use frequently on an SMB share, or even a website, and then reference them from there. Because a script is just text, we don't have to worry about blocks for binary or similar file types. We can also obfuscate the code and then decode it on the fly, which potentially makes bypassing antivirus (AV) easier.

Because a script is just text, we can include it almost anywhere. Frequently, code sites such as GitHub are handy for this type of activity, as such sites have many business-related purposes. We can include our scripts in a repository or as basic gist commands that we load from inside our PowerShell environment to bootstrap other activities. PowerShell can even use a user's proxy settings, so this is a great way to establish persistence in an environment.

## Loading PowerShell Scripts

Before we can do any exploitation with PowerShell, you need to know how to execute scripts. In most environments, unsigned PowerShell scripts aren't allowed by default. We're going to take a look at this behavior so you can identify it, and then we'll look at how to bypass it so you can bootstrap any code you want to run.

## Lab 15-1: The Failure Condition

Before we look at how to get around security, we should take a look at how the security works when in action. To do this, we're going to build a very simple script on our Windows 10 box that we set up in Chapter 10, and then we'll try to execute this script. For our script, we're just going to create a directory listing of the root of C:\. First, we need to open up a command prompt as Administrator and then run the following code:

```
c:\Users\User\Desktop>echo dir C:\ > test.ps1
c:\Users\User\Desktop>powershell .\test.ps1
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

You can see here that the execution of our test.ps1 script was blocked because running scripts on the system has been disabled. Let’s take a look at what the current execution policy is:

```
c:\Users\User\Desktop>powershell -command Get-ExecutionPolicy
Restricted
```

This shows that the current execution policy is “Restricted.” Table 15-1 provides a breakdown of what each of the possible execution policies does.

| Policy | Description |
|---|---|
| Restricted | Only system PowerShell commands can be run. The only way to run custom commands is via Interactive mode. |
| AllSigned | Any script can run if it is signed by a trusted publisher. This allows corporations and third parties to sign their scripts to enable them to run. |
| RemoteSigned | Scripts that have been downloaded can only be run if they are signed by a trusted publisher. |
| Unrestricted | Anything goes. Regardless of where or how the script has been obtained, it is allowed to run. |

Table 15-1 PowerShell Execution Policies

Let’s try changing the execution policy to Unrestricted and then run our test.ps1 script again:

```
c:\Users\User\Desktop>powershell -com Set-ExecutionPolicy Unrestricted
c:\Users\User\Desktop>powershell -command Get-ExecutionPolicy
Unrestricted
c:\Users\User\Desktop>powershell .\test.ps1
Directory: C:\
```

As you can see, once we change the policy to Unrestricted, our script runs just fine. Based on Table 15-1, it looks like RemoteSigned should also work. Let’s try it:

```
c:\Users\User\Desktop>powershell -com Set-ExecutionPolicy RemoteSigned
c:\Users\User\Desktop>powershell -command Get-ExecutionPolicy
RemoteSigned
c:\Users\User\Desktop>powershell .\test.ps1
Directory: C:\
```

The RemoteSigned policy works as well. In theory, we could just reset the execution policy to one of these two values. Unfortunately, in many environments, this value is enforced by Group Policies. In such a situation, it’s not that easy to change the policy. Therefore, let’s set the value back to Restricted, as shown here, and we’ll just proceed through the rest of the chapter with the strictest controls enabled:

```
c:\Users\User\Desktop>powershell -com Set-ExecutionPolicy Restricted
```

## Lab 15-2: Passing Commands on the Command Line

In Lab 15-1, we executed a number of PowerShell commands from the command line. In this lab, we’re going to look at how to execute more complex commands. In the previous examples, you saw that the -command option can be used to pass a command on the command line; however, many of the PowerShell options can be shortened. In this case, we can just use -com, as shown here, and save ourselves some typing:

```
c:\Users\User\Desktop>powershell -com Get-WmiObject win32_computersystem
```

| Domain | WORKGROUP |
|---|---|
| Manufacturer | VMware, Inc. |
| Model | VMware Virtual Platform |
| Name | DESKTOP-KRB3MSI |
| PrimaryOwnerName | Windows User |
| TotalPhysicalMemory | 8694255616 |

Here, we were able to issue a simple WMI query with PowerShell, and without any additional quotation marks around our query. For basic queries this will work fine; however, for more complex queries, we may run into a problem. Let’s see what happens when we try to get additional information about the user who owns the system:

```
c:\Users\User\Desktop>powershell -com Get-WmiObject win32_computersystem | select Username
'select' is not recognized as an internal or external command,
operable program or batch file.
```

You can see here that we couldn’t use the pipe character to pass data from one method to another because it is interpreted by the operating system. The easiest way to get around this is through the use of double quotes, like so:

```
c:\Users\User\Desktop>powershell -com "Get-WMIObject win32_computersystem | select Username"
```

```
Username
--------
DESKTOP-KRB3MSI\User
```

This time, the pipe character wasn’t interpreted by the operating system, so we could get just the username information from the output of the WMI query. For simple commands, this works well, and if we’re just doing a few of these commands, it’s easy enough to add them into a batch script and run them from there.

## Lab 15-3: Encoded Commands

When we have a more complex task, not having to worry about formatting is nice. PowerShell has a handy mode that allows us to pass in a Base64-encoded string as a script to run—as long as the script is not very long. The total length for a Windows command-line command is about 8,000 characters, so that’s your limit.

We have to make a few changes to create an encoded command. First of all, the encodedcommand option of PowerShell takes a Base64-encoded Unicode string, so we need to convert our text to Unicode first and then encode it as Base64. To do this, we need an easy way to convert to Base64 encoding. Although we could use the tools already on Kali to do this, we’re going to use one of my favorite toolkits, Ruby BlackBag by Eric Monti. This Ruby gem contains lots of encoding and decoding tools to help with both malware analysis and hacking. First, we need to install it before we can use it:

```
root@kali:~/Ch15# gem install rbkb
Fetching: rbkb-0.7.2.gem (100%)
Successfully installed rbkb-0.7.2
Parsing documentation for rbkb-0.7.2
Installing ri documentation for rbkb-0.7.2
Done installing documentation for rbkb after 1 seconds
1 gem installed
```

Once this toolkit is installed, it not only adds Ruby functionality but also creates some helper scripts—one of which is called b64, a Base64 conversion tool. Next, we’ll take the same command we used in the last lab and convert it to a PowerShell-compatible Base64 string:

```
root@kali:~/Ch15# echo -n "Get-WMIObject win32_computersystem | select Username"
| iconv -f ASCII -t UTF-16LE | b64
RwB1AHQALQBQAEUAbABrAHQAagB0AGUAbQBQAQAHwIA1BzAGUAbAB1AGMAZQ
BzAHk
AcwB0AGUAbQBQAgAHwIA1BzAGUAbAB1AGMAZQ=
```

Here, we are using echo with the -n option to print out our PowerShell command without incorporating a newline. Next, we pass that into iconv, a character set converter, which will convert our ASCII text into UTF-16LE, the Windows Unicode format. Finally, we pass all of that into b64, as shown next. The string that it outputs is the string we’re going to use with PowerShell.
