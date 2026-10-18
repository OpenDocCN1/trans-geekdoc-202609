**Figure 14.15** `netstat`.

# The Windows Registry

The Windows Registry is an incredible repository of potential valuable forensics information. It is the heart of the Windows machine. There are a number of interesting pieces of data you can find here. It is beyond the scope of this chapter to make you an expert in the Windows Registry, but it is hoped that you will continue on and learn more. Microsoft describes the Registry as follows:

A central hierarchical database used in the Microsoft Windows family of Operating Systems to store information necessary to configure the system for one or more users, applications and hardware devices.

The registry contains information that Windows continually references during operation, such as profiles for each user, the applications installed on the computer and the types of documents that each can create, property sheet settings for folders and application icons, what hardware exists on the system and the ports that are being used.

The Registry is organized into five sections referred to as *hives*. Each of these sections contains specific information that can be useful to you. The five hives are described here:

+   - **HKEY_CLASSES_ROOT (HKCR):** This hive stores information about drag and drop rules, program shortcuts, the user interface, and related items.
+   - **HKEY_CURRENT_USER (HKCU):** This hive is very important to any forensic investigation. It stores information about the currently logged-on user, including desktop settings and user folders.
+   - **HKEY_LOCAL_MACHINE (HKLM):** This hive can also be important to a forensic investigation. It contains those settings common to the entire machine, regardless of the individual user.
+   - **HKEY_USERS (HKU):** This hive is very critical to forensics investigations. It has profiles for all the users, including their settings.
+   - **HKEY_CURRENT_CONFIG (HCU):** This hive contains the current system configuration. This might also prove useful in your forensic examinations.

You can see the Registry and these five hives in Figure 14.16.

![](bbox=[0.143, 0.596, 0.335, 0.691])

**Figure 14.16** Windows Registry.

Most people use the `regedit` tool to interact with the Registry. In Windows 7 and Server 2008, you select Start, Run, and then type in `regedit`. In Windows 8 and 10, you have to go to the applications list, select All Apps, and then find Regedit or use the Windows+R key and type in `regedit`. Most forensics tools provide a means for examining the Registry as well.

Every Registry key contains a value associated with it called LastWriteTime. This value indicates when this Registry value was last changed. Rather than being a standard date/time, this value is stored as a FILETIME structure. A FILETIME structure represents the number of 100-nanosecond intervals since January 1, 1601. Clearly, this is important forensically.

It is also interesting to note that Microsoft rarely uses strong encryption to hide items in the Registry. If an item is encrypted, it is likely encrypted with some simple algorithm such as ROT 13.