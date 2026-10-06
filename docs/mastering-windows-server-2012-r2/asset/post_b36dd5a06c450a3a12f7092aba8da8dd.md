
# FIGURE 29.17
RD web access page for VDI

![](img/41a83208e6906a3732620203b836cea7_1506_0.png)

Figure 29.18 shows you the VMs related to the VDI deployment. Notice how one is in Saved state; this happens automatically, preserving resources on the box when they are not in use.

# Figure 29.18
VM view of a VDI deployment

![](img/41a83208e6906a3732620203b836cea7_1506_1.png)

Now it's a fully working VDI solution. We mentioned earlier that VDI has been optimized to work with storage Dedup in Windows Server 2012. To give you a quick idea, when we created our gold image we had 8 GB VHDX file. When we created the two pools, a copy of the gold image for each pool was created. This totals to 24 GB of storage just in VHD files, making it a prime candidate for storage Dedup. You save nearly 60 percent of the storage costs by enabling Dedup. Remember, though, not to place your VDI files on the root volume because you cannot enable Dedup on it. From step 25 onward, we showed how to configure the path to ensure it is not the root volume.

# Monitoring Remote Desktop Services

Once Remote Desktop Services is up and running, you'll need to monitor and manage it. In previous versions of Windows RDS tools were available:

- Remote Desktop Services Manager
- Remote Desktop Session Host Configuration
- RemoteApp Manager
- Remote Desktop Web Access Configuration
- Remote Desktop Licensing Manager
- Remote Desktop Connection Manager
- Remote Desktops

In Windows Server 2012 R2 all the administration tools except for two located directly within the Server Manager under Remote Desktop Services. The two that are still located under Start > Administrative Tools > Remote Desktop Services are as follows:

- Remote Desktop Licensing Manager
- RD Licensing Diagnoser (new)

The RD Licensing Diagnoser does exactly what it says: helps you figure out if you will have problems in your environment with licensing. In Figure 29.19 we show the output for an environment where we have not published licenses yet and are still within the grace period.

# FIGURE 29.19
RD Licensing Diagnoser

![](img/41a83208e6906a3732620203b836cea7_1507_0.png)

# MONITORING REMOTE DESKTOP SERVICES

The Remote Desktop Licensing Manager has not really changed and still performs the functions as before. The requirement to activate the licensing server or the Microsoft Clearinghouse is still in place, and you still need to install the appropriate CALs. A nice report feature for usage is now available, but that the feature is the same as in previous generations.

# Common Tasks and How to Do Them

As mentioned, all the legacy tools prior to Windows 2012 for monitoring and configuring Remote Desktop Services exist outside the UI (except PowerShell, obviously). During deployment of both Remote Desktop and VDI we provide screenshots of where you can access pieces of information you commonly need in a deployment. In the next couple of pages we will talk about some of the more commons required.

### Example 1: Configure licensing for RD Session Host or Virtualization Host

1. In Server Manager under Remote Desktop Services, click Overview.
2. Navigate to Deployment Overview, and choose Tasks > Edit Deployment Options.
3. Click the plus sign beside RD Licensing.

This lets you configure Per Device or Per User licensing for this host, as shown in Figure 29.20.

FIGURE 29.20
Configuring RD Licensing mode

![](img/41a83208e6906a3732620203b836cea7_1508_0.png)

# CHAPTER 29 INSTALLING, USING, AND ADMINISTERING REMOTE DESKTOP SERVICES

### Example 2: Modify the virtual desktop template export location

1. Review 29.20 and at the bottom of the left column you will see Export Location. This refers to the template location.
2. Open an elevated command prompt and type net share.
This will allow you to quickly map the share to the physical path.
3. Simply point it to another path that you have configured.

**Example 3: Change the RDS encryption level to FIPS Compliant**

1. Open Server Manager > Remote Desktop Services > Collection > "Name of your Collection."
2. Look at the properties window, and click Edit Properties.
3. Choose Security from the list, on the left, and under Encryption Level from the dropdown list, select FIPS Compliant; see Figure 29.21.

**FIGURE 29.21**
Changing the RDS encryption level

![](img/41a83208e6906a3732620203b836cea7_1509_0.png)

**Example 4: Change client settings for RD Session Host**

1. Choose Client Settings from the list shown on the left side of Figure 29.21.

Observe that now you can turn on and off different options to affect the client experience.
2. Map the share to the physical path.
3. Disable audio and video.

### Example 5: Find out who is logged on

1. Open Server Manager > Remote Desktop Services > Collection > "Name of your Collection."
2. Look at Figure 29.22.

FIGURE 29.22
Who is logged on

![](img/41a83208e6906a3732620203b836cea7_1510_0.png)

Observe that now you can turn on and off different options to affect the client experience.
2. Map the share to the physical path.
3. Disable audio and video.

# Remote Desktop Licensing Manager

The Remote Desktop Licensing Manager has not really changed and still performs the functions as before. The requirement to activate the licensing server or the Microsoft Clearinghouse is still in place, and you still need to install the appropriate CALs. A nice report feature for usage is now available, but that the feature is the same as in previous generations.
