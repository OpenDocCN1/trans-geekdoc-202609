# # PowerShell Exploitation

The majority of corporate systems are still Windows based, so it’s important that we have a good grasp of the available tools in Windows systems. One of the most powerful of these tools is PowerShell. In this chapter, you learn about what makes PowerShell such a powerful tool, and we look at some ways to use it as part of our exploitation toolkit.

In this chapter, we cover the following topics:

+   - Why PowerShell
+   - Loading PowerShell scripts
+   - Creating shells with PowerShell
+   - PowerShell post exploitation

# ## Why PowerShell

Although the PowerShell language has been a blessing for Windows systems automation, it also gives hackers leverage. PowerShell gives us access to almost all of the Windows features in a programmatic way, and it’s extendable and can be used to administrate Active Directory, e-mail systems, SharePoint, workstations, and more. PowerShell also gives us access to .NET libraries from a scripting standpoint, making it one of the most flexible tools you can use in a Windows environment.

# ## Living Off the Land

When we talk about “living off the land,” we mean using the tools already present on systems to further our exploitation. This is valuable because whenever we add things to a system, we increase the possibility of detection. Not only that, when we leave tools behind, it helps disclose our tactics, techniques, and procedures (TTPs) so that it is easier to find our activity across other systems. When we live off the land, we can leave fewer artifacts behind and limit the tooling we have to move from system to system.

PowerShell is useful as an already existing tool on a system because it gives us the ability to easily script and also includes .NET integration, so almost anything we can write in .NET we can write in PowerShell. This means we can go beyond basic scripting and actually interact with kernel functions and more, which gives us additional flexibility that would normally require the use of separate programs.

One of the main benefits of PowerShell is that it can use the Internet Explorer options, so things like proxy support are built into PowerShell. As a result, we can use the built-in web libraries to load code remotely, meaning we don’t have to download any code to the target system. Therefore, when someone looks at the file-system timeline, these pulls from websites won’t show up, which allows us to be even stealthier.