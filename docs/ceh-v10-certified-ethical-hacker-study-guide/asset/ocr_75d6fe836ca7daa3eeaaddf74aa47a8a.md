One of these forks was the Open Vulnerability Assessment System (OpenVAS). Initially, about OpenVAS was the same as Nessus, as you’d expect. Over time, though, OpenVAS developed its own application architecture, using multiple tiers that Nessus hadn’t explicitly used. Nessus initially had a native application client to manage the scans, and OpenVAS continued to use the same native application. OpenVAS developed the Greenbone Security Assistant (GSA) as the user interface for OpenVAS. Today, GSA is accessed through a web interface. You can see the login screen from GSA in Figure 5.7.

# FIGURE 5.7 Greenbone Security Assistant

![](bbox=[0.191, 0.278, 0.815, 0.543])

OpenVAS allows you to have multiple users, each of which may have different permissions. Some users may be able to create scans, while others may only be able to look at the scan results. Other users would be able to create users and administer the OpenVAS installation. In addition to users, OpenVAS supports roles. Permissions within the roles can be altered and new roles can be created. When you install OpenVAS, the admin user is created as part of the setup process and a random password is generated.

# Setting Up Targets in OpenVAS

A scan in OpenVAS has many components. When you create a scan, you need a target or set of targets. Creating a target also requires some information. You need the set of IP addresses you want to run tests on. You can also exclude addresses from the set you are testing. You may do this in order to provide a network block in your target list, but you may also have fragile systems in that network block. Because of that, you may want to tell OpenVAS not to test that address. Figure 5.8 shows the dialog box in OpenVAS where you create a target. You’ll see the IP addresses as well as the exclusions.