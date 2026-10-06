# TABLE 2.3: The Configuration Passes

| PASS | DESCRIPTION |
|---|---|n| windowsPE | Boots up the Windows PE installation environment, configures the product key, and configures the installation disk. |
| offlineServicing | Applies updates to the Windows image, including packages, patches, and languages. |
|ialize | Configures settings that be unique to the system, such as network configuration, regional, and domain. |
| Generalize | Removes system-specific information. It is executed only when you run sysprep / |
| auditSystem | Processes unattended setup steps before a user logs on. This pass runs only if you boot into audit mode. |
| auditUser | Processes unattended setup steps after a user logs on. It runs only if you boot into audit mode. |

You will see some of these passes when you create your answer file in WISM. This will start to get a clearer outlook once you get into WISM.

For this section you will need your Windows Server 2012 R2 DVD. The \sources folder on your media will find a WIM file called .wim. This file contains everything needed to install the new operating systems. The clever thing is that WIM file contains everything required to install all editions of the operating system on the media. For example, Standard, Datacenter, Full Core, and Datacenter Core are all on the Windows Server 2012 R2 DVD. This WIM file uses single-instance storage; having of the identical file size six times, it stores once and contains a reference point for each of the subsets.

WISM is going to need a copy of that file on your administrative PC. WISM uses this image to know what tasks can be performed for the version and edition of Windows that you are working with. With vary depending on whether you are using Windows 8, Windows Server 2012 Standard, Windows Server 2012 R2 Datacenter, WISM needs to create a catalog of the contents of the image file, and its the folder containing the image as a working folder. You cannot write to read-only media such as a DVD.

For this example, you are working with the DVD for Windows Server 2012 R2. You have copied \sources\install.wim into C:\w2812\install.wim on your administrative PC.

Now launch WISM and get this process running by Selecting > Select Windows Images. Navigate to your install image (see Figure 2.67), which is C:\w2812\install.wim, and open it.

You can now see a little of the magic of the WIM file in action. The installation media has a number of different versions of Windows in it: Select the version of Windows that you want to install in an unattended fashion. We have selected the Standard edition of Windows Server 2012 R2 in Figure 2.68.