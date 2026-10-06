# CHAPTER 31 PATCH MANAGEMENT

**FIGURE 31.5**
Replica mode in a multiple branch-office scenario

![](bbox=[0.237, 0.116, 0.883, 0.473])

Replica mode, as shown in Figure 31.5, is a central administration design and allows an upstream server to share its updates, client groups, and other components with downstream servers. The replica servers are just downstream servers that are managed via the primary upstream server. This configuration is ideal when IT is managing updates in a multi-branch office scenario.

Branch offices are one of the newer scenarios first introduced in Windows Server 2008 R2. In this configuration you leverage Windows Server 2012 R2 BranchCache: http://tinyurl.com/c3lBranchCache: Using this and the Branch feature in Windows, you can help reduce WAN link utilization and improve responsiveness.

# Installation and Configuration of Patch Management

Installing updates on the computers of your organization's network is critical to protect the security of the network and to keep your client computers performing optimally. How updates are rolled out requires careful planning and testing to ensure a successful installation. Microsoft recommends a phased approach to patch management; each of the phases is discussed in detail on the Microsoft TechNet website at http://tinyurl.com/c3lupdateprocess.

# Installing the WSUS Role on Windows Server 2012 R2

One of the new features of Windows Server 2012 R2 is the ability to install a server role and it automatically adds all of the required components as part of the installation. In previous versions of Windows Server, you would have to configure many of the roles and features as separate tasks.