This key should be protected at a level comparable to the data stored on the drive. In other words, if you have secret proprietary data on the drive, protect the key like its secret proprietary data.

# Enabling BitLocker

BitLocker is not enabled by default. Before you can enable BitLocker, you must first add the BitLocker Drive Encryption feature. If you recall from adding roles exercise in the beginning of the chapter, we have already enabled the BitLocker role. Please refer to that if you need to refresh your knowledge on the process of adding the role to the server. The following steps assume that TPM 1 is not available on your system and the BitLocker role is already installed on the server.

+   1. Launch Control Panel, and click Security.

At this point, you will see the BitLocker Drive Encryption feature in the System and Security Center. If you looked here before adding the feature, it didn't appear.

# SEARCH CONTROL PANEL

Control Panel has a feature that is quite valuable but easily overlooked. In the upper-right corner is a search box. You can type in any search term (such as BitLocker or User), and it'll list only the relevant aspects. This is also available in Windows Vista, Windows 7, Windows 8, and Windows Server 2008. Now if you could make this feature available for Group Policy.

+   2. Click BitLocker Drive Encryption. You'll see a similar display to Figure 13-31.

FIGURE 13-31
Turning on BitLocker
Drive Encryption

![](bbox=[0.34, 0.573, 0.905, 0.915])