# CHAPTER 2 INSTALLING AND UPGRADING WINDOWS SERVER 2002 R2

# FIGURE 2.59

ROLES AND FEATURES
All roles and Features: 15 total

Roles And Features
window

![](bbox=[0.337, 0.135, 0.853, 0.293])

| Server Name | Role | Path |
|---|---|---||
| TESTSERVER-1 | Web Server (IIS) | Role Service | Web Server (IIS) |
| TESTSERVER-1 | Management Tools | Role Service | Web Server (IIS)/Management Tools |
| TESTSERVER-1 | IIS Management Console | Role Service | Web Server (IIS)/Management Tools/IIS Management Console |
| TESTSERVER-1 | | Role Service | Web Server (IIS)/Web Server |
| TESTSERVER-1 | Performance | Role Service | Web Server (IIS)/Web Server/Performance |
| TESTSERVER-1 | Static Content Compression | Role Service | Web Server (IIS)/Performance/Static Content Cont |

# Wrapping Up Server Manager

You've learned that servermanagercmd is deprecated by Microsoft, and you've learned how to install and remove features using PowerShell and the Server Manager GUI. You have also seen how to use Server Manager to diagnose roles and features using the Best Practices Analyzer.

So it's time we mentioned domain controllers and Active Directory—cue the jaws-like dramatic music.

# Upgrading Active Directory

OK folks, some good news. We're not going to cover this subject in detail. That will be covered in Chapter 7, “Active Directory in Windows Server 2002 R2,” but we wanted to mention it here for the readers who have worked with Active Directory (AD) in the past. If you've never, don't worry about it—feel free to skip the next couple of pages, and you'll learn all about AD in Chapter 7.

# An Overview of Active Directory: New Functionality
in Windows Server 2002 R2

As usual, a new version of Server comes along, and you will get new functionality and design opportunities in Active Directory. A lot of this functionality will be pretty exciting because people expect it to be based on customer feedback. Some of these new options will definitely answer some of those questions we frequently see on Internet support forums.

# WHAT’S NEW IN ACTIVE DIRECTORY DOMAIN SERVICES

Active Directory Domain Services (AD DS) allows you to deploy domain controllers either locally or on your cloud. There are a host of administration tasks in deploying controllers that can be easily completed using AD DS. Let's discuss some of the new features you may find useful.

# Active Directory Recycle Bin

Do you hear that? That's the cheering of Active Directory administrators all around the world. Every administrator's worst nightmare is the deletion of objects. When Windows