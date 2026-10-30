![](bbox=[0.07, 0.115, 0.72, 0.325])

FIGURE 12-6 Wifi-Honey Help Command.

As you can see, you need to give your honey pot an SSID and a channel, and tell Wifi-Honey which interface to use. So, let’s do that. You can see this in Figure 12-7.

![](bbox=[0.07, 0.435, 0.73, 0.5])

FIGURE 12-7 Setting Up Wifi-Honey.

Now if you have any issues such as a conflict with another application, some file not found, Wifi-Honey will tell you that. Depending on your virtual machine (if you are using a VM), you might have issues with the wireless card. Many people find that the VMs work best with an external USB wireless card.

But if all goes well, you are now running a wireless access point from your Kali Linux machine. Just as you would with Windows, you now need to turn on some packet sniffer. Because tcpdump is included with Linux, that would be a good choice.

# Testing the WAP Administration

Aside from creating a WAP, you will want to check the existing wireless access points. In fact, this part is probably more important. The wireless access point is the most important part of the wireless network. It is important that you test its security. This is done by simply connecting to the Wi-Fi, then attempting to log in to its administrative screen. If the system has even the most basic security, you should not be successful. The steps are trivial:

+   - **STEP 1.** After connecting, run `ipconfig` (or `ifconfig` if using Linux) and get the gateway IP address.
+   - **STEP 2.** Open your browser and connect to the gateway router.
+   - **STEP 3.** Attempt to log in to the administrative screen with default passwords. You can get default WAP passwords by simply searching the Internet for “Default xxx wifi password” where xxx is replaced by Linksys, Belkin, Huawei, or whatever the brand of wireless access point you have.