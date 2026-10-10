
# 账户类型

**For the exam, be sure to know these different types of accounts. Also remember that a shared account used by multiple employees makes it difficult to audit who performs the actions. From an auditing point of view, you want to ensure every employee has their own account.**

## 来宾账户

**Guest accounts** A guest account is one that can be used to access a system if a person does not have an account. This allows an individual to gain temporary access to a resource without requiring you to create an account for them. Most operating systems have a guest account, but it is disabled by default, which means if someone wants to access the system, they require that an account be created for them. It is a security best practice to keep the guest account disabled.

## 服务账户

**Service accounts** Secure operating systems such as Windows and Linux require that everything authenticates to the system, whether it is a user or a piece of software. When software runs on the system, it needs to run as a specific user so that the software can be assigned permissions. The user account you associate with a piece of software is known as a service account because it is a feature used by services running within the operating systems as well. When creating a service account (the user account the software application will be configured to use), you typically configure the service account with a strong password and specify that the password never expires.

![Images](job.jpg)

**Ensure that the service account does not have administrative capabilities, because otherwise, if the service were compromised by an attack such as a buffer overflow attack, the attacker would have the same credentials as the account associated with the service.**

## 特权账户

**Privileged accounts** A privileged account is an account that has extra permissions outside of what is assigned to a typical user. Privileged accounts typically are authorized to make configuration changes to a system or perform an action not normally performed by a regular employee.

# 使用安全组

The first method of implementing access control in most environments is by granting access to security groups. The correct method to grant access to resources is to place the user account into groups and then to assign the groups the permissions to the resource. This allows you to place new users in the group and not have to go back and modify the permissions.

## 练习 11-2

![Images](video.jpg)

### 配置安全组并分配权限

In this exercise, you will create a security group in Active Directory and then place a user account in that group. Once you have created the group, you will assign the group permissions to a folder.

1. On the ServerA VM, go to Server Manager and then choose **Tools** | **Active Directory Users and Computers**.
2. Create a new user called **Lab11UserA** by right-clicking the Users folder and choosing **New** | **User**.
3. Type a first name of **Lab11UserA**.
4. Type **Lab11UserA** in the **User Logon Name** field and then click **Next**.
5. Type **P@ssw0rd** in the **Password** field and **Confirm Password** field and then clear the check box that states you will need to change the password at next logon. Click **Next** and then **Finish**.
6. To create a security group, right-click the Users folder and choose **New** | **Group**.
7. Type **Authors** as the name of the group and then click **OK**.
8. To assign permissions to the group, go to File Explorer and navigate to drive **C:**. Right-click drive **C:**, choose **New** | **Folder**, and create a folder on drive **C:** called **Publications**.
9. To assign permissions to the Authors group, right-click the Publications folder and choose **Properties**. Click the **Security** tab.
10. To add the authors to the permission list, click **Edit** and then click **Add**.
11. Type **authors** in the **Select Users, Computers, or Groups** dialog box. Click **OK**.
12. Select **Authors** in the permission list and then assign the group the **Modify** permission.
13. Click **OK** twice.

![Image](exam.jpg)

**The Security+ exam expects you to understand proper usage of groups and permissions. Remember that the user is assigned to the group, and the group is assigned the permissions.**

# 权利与特权

A big part of the security of a system comes from the fact that only certain security principals (users or groups) can perform certain actions. For example, it would be a huge security concern if anyone could do a backup of any files on a system. In the Microsoft world, only a person with the “Back up files and directories” right can perform backups.

On a Windows system, you normally have to be logged in as the administrator to perform changes to a system, while in Linux, you typically need to be logged in as root to be able to make changes. It is possible to allow others to make changes to the system by granting them the correct rights or privileges.

Microsoft operating systems have a **User Rights Assignments** section of system policies where you can control who can perform common administrative tasks such as backing up files and directories or changing the system time. The following outlines some common rights in Windows:

## 常见 Windows 权利

- **Access this computer from the network** This right controls who is allowed to connect to the system from across the network.
- **Allow log on locally** This right controls who is allowed to sit at the computer and log on.
- **Back up files and directories** This right controls who can do backups on the system.
- **Change the system time** This right controls who is allowed to adjust the time on the computer.
- **Take ownership of files or other objects** This right controls who is allowed to take ownership of files, folders, or printers. The owner of a resource is allowed to change the permissions on the resource at any time.

## 练习 11-3

![Images](video.jpg)

### 在 Windows 系统上修改用户权利

In this exercise, you will learn how to modify the user rights on a Windows system.

1. Use either the Windows 10 VM or the ServerA VM.
2. Depending on whether you want to change the security of a single system or multiple systems, use the Start menu and type either **Local Security Policy** or **Group Policy** to launch the appropriate tool. If you are on a server, you can also use the **Tools** menu in Server Manager to launch the appropriate tool:
   - **Local Security Policy** Use Local Security Policy to administer security settings of a single Windows machine (either client or server).
   - **Group Policy Management Console** Use the Group Policy Management Console to administer policies on the network that apply to multiple systems.
3. In the Start menu, type **Local** and then launch the Local Security Policy.
4. Under **Security Settings** (on the left), expand **Local Policies** and then select **User Rights Assignment**.

![Image](f0487-01.jpg)

5. To allow the Authors group to back up files, double-click the “Back up files and directories” policy at right. List who currently has the right to do backups:

________________________________________________________________________________

________________________________________________________________________________

6. Click the **Add User or Group** button and add **Authors** to the list of those who can do backups.
7. Click **OK** and then close the Local Security Policy window.

When teaching in the classroom about security concepts, I often correct people on terminology—a *right* is someone’s privilege to perform a task, while a *permission* is someone’s level of access to a resource. For example, the Authors group was given the Modify *permission* to the Publications folder. The Authors group was not given the Modify *right.* The opposite is true as well—the Authors group was given the *right* to perform backups, not the *permission* to perform backups!

![Image](exam.jpg)
