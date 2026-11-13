
## THE LAST RESORT

If all the repair and reinstallation options have failed, you may be able to reformat your hard drive and reinstall your OS from scratch. Reformatting will erase everything on your hard drive, which will mean you will have to reinstall not just the operating system, but also all your files, folders, programs and system drivers.

### Backing Up

Before you consider reformatting, you need to back up all your files. This means not just your documents, pictures and multimedia, but you also need to ensure you have copies of your system drivers (software that enables your hardware to run), programs and anything else you may lose when your hard drive is wiped.

### Windows Reformatting

On Windows machines, there are two choices when it comes to reformatting.

![](img/f1096bf6e51eba2af0c1cf60f883f3b6_233_0.png)

- Quick format: Does not check the drive for its condition. In addition, the data is not erased, but simply marked as being writable (new data can take its place).

- Full format: Will check the hard drive for any bad sectors; it then erases all data on the drive.

### Partitions

When a hard disk is formatted, it has to be assigned a drive letter, such as C:. This is done by means of a partition. Most computers have single partitions, so the letter C represents the entire hard disk, but you can have multiple partitions.

Above: You can run a format on a second hard drive in Windows by right clicking and selecting format.

### Reformatting a Windows PC

Once you have backed up your computer, you can reformat and reinstall your Windows operating system. To reformat a Windows hard drive, insert your Windows installation disk into the drive and reboot your computer.

- 1. At the **Welcome to Setup** page, press **Enter**, and then **F8** to accept the licensing agreement and press **Esc** to bypass Windows repair.

- 2. Use the arrow keys either to create a new partition or to use your current one. For a full format, it is best to create a new partition.

![](img/f1096bf6e51eba2af0c1cf60f883f3b6_234_0.png)

Above: Creating a partition before formatting.

- 3. Select the partition where you want to install Windows, then press **Enter**.

- 4. Select the format options (quick or full), then the file system option; for most recent versions of Windows, it is recommended to use a NTFS file system.

![](img/f1096bf6e51eba2af0c1cf60f883f3b6_234_1.png)

Above: Choosing partition options.

- 5. Press **Enter** to reformat the drive. Once complete, you will have to reinstall your operating system by rebooting and following the instruction on the installation disk.

### Reformatting a Mac

To reformat a hard drive on a Mac, you need to use Disk Utility (see pages 225–26).

![](img/f1096bf6e51eba2af0c1cf60f883f3b6_235_0.png)

Above: Entering name and size for partition.

![](img/f1096bf6e51eba2af0c1cf60f883f3b6_235_1.png)

- 1. Select your Mac's hard drive and select **Partition**.
- 2. In the Partition Information box, enter a name for your hard drive and the size of partition.
- 3. Click **Apply**, and then click **Partition**.
- 4. Go back to the **Disk Utility** main menu and select the partition you have just created.
- 5. Select **Erase** (ensure that the format is Mac OS Extended, which is set by default).
- 6. Select a security option. The securer the option, the more thorough it will be in erasing your data, but it will also be slower.
- 7. Once formatting is complete, reinstall your OS X operating system.

Above: Selecting erase.

![](img/f1096bf6e51eba2af0c1cf60f883f3b6_235_2.png)

## REMOVING STUBBORN THREATS

Some malware can be really stubborn when it comes to cleaning a computer. Either they act like normal programs so antivirus software does not spot them, or they infect areas that make them hard to remove. In these instances, you may have to take care of the threat manually.

### IDENTIFYING THREATS

If your antivirus scan comes up clean, you may still feel that your machine is infected with something because of the way it is acting: your PC may be running slowly, your Internet browser playing up, or some other symptom is indicating something is not quite right. If this is the case, you may have to do a bit of diagnosis to identify what the problem is.

### BROWSER THREATS

One of the most common threats missed by antivirus software is malware installed into browser extensions. Extensions, plug-ins, browser helper objects (BHOs) and add-ons are tools designed to expand the functionality of your web browser, but some malicious software developers use these to install adware and other malware.

![](img/f1096bf6e51eba2af0c1cf60f883f3b6_236_0.png)

Above: Extensions can be really useful, but they can also harbour malware.

### Browser Helper Objects

Browser helper objects (BHOs) are plug-ins for Internet Explorer designed to allow the browser to display file formats it could not otherwise interpret. However, they can also harbour malware, so if your browser seems to have a mind of its own, you may want to disable your BHOs to see if they are the cause.

![](img/f1096bf6e51eba2af0c1cf60f883f3b6_237_0.png)

Above: Disabling browser extensions.

- 1. Close Internet Explorer, click Start, Settings and Control Panel.
- 2. Select Internet Options and click the Advanced tab.
- 3. Under Browsing, clear the Enable third-party browser extensions check box.
- 4. Restart Internet Explorer.

### Removing BHOs

If Internet Explorer starts to function normally after disabling your browser extensions, you know a BHO is the cause of the problem. Therefore you may want to run a BHO removal tool to identify and remove the offending BHO. Many of these can be found on the Internet.

![](img/f1096bf6e51eba2af0c1cf60f883f3b6_237_1.png)

### Extensions and Plug-ins

Internet Explorer is not the only browser plagued by malware threats hidden in plug-ins. Most browsers rely on extensions to improve your web experience, and they can all too easily be hijacked by malicious malware. However, disabling and removing extensions and plug-ins can be pretty simple.

- 1. Go into your browser settings.

- 2. In Firefox click the Add-ons button, in Chrome, click the Extensions link on the left, in Opera select Extensions from the tools menu.

![](img/f1096bf6e51eba2af0c1cf60f883f3b6_238_0.png)

Above: Spy BHO Remover can remove malware posing as browser helper objects.

- 3. In Firefox, select Extensions or Appearance in the Add-ons Manager tab, and click the Disable button next to the extension you want to disable.

![](img/f1096bf6e51eba2af0c1cf60f883f3b6_238_1.png)

Above: You can enable and disable most extensions quite easily.

- 4. In Chrome, simply uncheck the Enable box to disable the extension.

- 5. In Opera, disable extensions in the Manage Extensions menu.

### Stubborn Extensions

Some extensions, such as Enterprise Policy extensions, which were created by Google to help developers, differ from normal extensions in that they cannot be removed or disabled in the normal way on Windows machines (OS X users can still delete them). This has made them a popular tool for malware producers, who can use them to install adware.

![](img/f1096bf6e51eba2af0c1cf60f883f3b6_239_0.png)

Above: Extensions with long random IDs that cannot be removed are usually malware.

![](img/f1096bf6e51eba2af0c1cf60f883f3b6_239_1.png)

Above: Searching for an extensions registry entry.

![](img/f1096bf6e51eba2af0c1cf60f883f3b6_239_2.png)

Above: Deleting an extension in registry.

### Removing Stubborn Browser Malware

If you have an extension that you cannot remove in the Extensions page, it is possible to get rid of them, although it is a fairly complicated procedure.

- 1. Go into the Control Panel and select the Install/Uninstall Programs.

- 2. Select anything that you do not remember installing and uninstall it. In particular, look for any programs with the words 'ad', 'blocker' or 'coupon' in the title.

- 3. Go into your extension manager in your browser, and make a note of the name of the extension that you want to remove.

- 4. Do a search (Start, Search) and type or paste in the name of the extension. Delete any folders or files that come up in the search.

- 5. Run the Registry Editor (regedit.exe), click Edit and select Find next.

- 6. Type or paste in the ID of the extension and press the Find next button.
