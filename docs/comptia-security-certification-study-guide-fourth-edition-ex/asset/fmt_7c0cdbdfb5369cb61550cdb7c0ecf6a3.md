
## 11. Select Installed Programs
Select **Installed Programs** to see a list of software installed on the system.

## 12. Select Operating System User Account
Select **Operating System User Account** to see a list of user accounts on the system.

## 13. View User Account Details
Choose one of the user accounts on the right to view more data about the account in the bottom-right pane.

## 14. Select Recent Documents
Select **Recent Documents** on the left to see a list of recently accessed files by the suspect. Note that you can select a file to display more information about the file.

![Image](f0846-01.jpg)

## 15. Select Web Account Type
Select **Web Account Type** to see a list of web sites the suspect has logged in to.

## 16. Select Web Downloads
Select **Web Downloads** to see a list of files downloaded by the suspect.

## 17. Select Web Search
Select **Web Search** to see a list of words the suspect has typed to search for content on the Internet.

## 18. Close Autopsy
Close **Autopsy**.

## EnCase Forensic and Forensic Toolkit
**Guidance Software** has created **EnCase Forensic**, which is a leader in the computer forensics analysis field. **EnCase Forensic** allows you to acquire the image of a suspect’s drive and to analyze the information.

**Forensic Toolkit (FTK)**, shown in [Figure 21-8](#ch21.xhtml#ch21fig8), is put out by **AccessData** and has some great features to help with the analysis of evidence on a suspect’s system. **FTK** has an acquisition tool known as **FTK Imager** to acquire an image of a suspect’s drive that can then be loaded into **FTK** for analysis. Like **Autopsy**, **FTK** has some great features for you to locate evidence in areas such as e-mail.

![Image](f0847-01.jpg)

**FIGURE 21-8**  
AccessData’s **FTK** is very popular forensics software.

I should note that it is important not to confuse **FTK** with **FTK Imager**. **FTK** is commercial forensics analysis software from **AccessData** that has a complete list of features, whereas **FTK Imager** is free software with limited capabilities.

### Live Analysis Tools
*Live analysis* is when an investigator decides to perform an investigation on a live system instead of capturing an image of the system. There are a few reasons to do this—one of which is that you may have a suspicion that the suspect is using drive encryption, and if you shut the system down, the drive will get encrypted. So, instead of shutting the system down, you perform a live analysis of the system. You may also perform a live analysis to review the contents of memory, as it may contain evidence as well.

Live analysis tools are great for responding to security incidents, such as a malware-infected system, as live analysis tools have many features to show the current state of the system. Live analysis tools can also be used to monitor running processes; locate all graphic files on the system; and view PST files, e-mail passwords, the registry, and Internet history, to name a few.

**CAINE** is an example of a live analysis tool that can be used for incident response and computer forensics.

### Hex Editors
Another important tool for a forensics investigator is a hex editor. A hex editor allows you to view the low-level content of a file or disk. With a hex editor, you can review file headers to identify the type of file you are dealing with, no matter what the file extension might be. **WinHex** is a common hex editor and one you should know for the Security+ exam. In [Figure 21-9](#ch21.xhtml#ch21fig9), you can see the first part of the file contents (the header) contains the value `FF D8`, which indicates that this is a JPG file, even though someone tried to hide the fact that it’s a JPG by renaming the file. The following is a list of starting header values for popular file types:

![Image](f0848-01.jpg)

**FIGURE 21-9**  
Looking at file headers with a hex editor

- **JPG files**: `FF D8 FF E0`
- **JPG files with Exif (exchangeable image file) metadata**: `FF D8 FF E1`
- **Bitmaps**: `42 4D`
- **TIFF (Tagged Image File Format) files**: `49 49 2A`
- **Office documents**: `00 CF 11 E0 A1 B1 1A E1`

## EXERCISE 21-5: Using FTK Imager to View File Headers

![Image](video.jpg)

In this exercise, you use **FTK Imager** to view the file header and identify the file as a JPG file.

1.  Launch **FTK Imager**.
2.  Click the **Add Evidence Item** button (the first button on the toolbar) to add an evidence item. This allows you to add a local hard drive, a partition, an image file, or the contents of a folder.
3.  Choose **Image File** and then choose **Next**.
4.  Choose to add the image called `Case20210602_FlashDrive.img` from this book’s labfiles folder and then choose **Finish**.
5.  Expand the contents of the image out on the left side in the **Evidence Tree**. Note that you can see a volume labeled `USB_DRIVE [FAT32]`.
6.  Expand out the `USB_DRIVE` node and then highlight the `[root]` node, which represents the root of the drive.
7.  Choose the **View Files in Hex Format** button on the right side of the toolbar.
8.  Select the file called `NewCompanyLocation.dat`. Notice that you can see the hex data for the file.
9.  Looking at the hex data for the file, notice that the file begins with `FF D8 FF E0`. This is the header used by a `.jpg` file. This means that `NewCompanyLocation.dat` is actually a JPG file.

![Image](f0850-01.jpg)

10. Close **FTK Imager**.

### Mobile Forensics
A growing area of computer forensics is mobile forensics—finding evidence on a mobile device such as a cell phone, tablet, or smart phone such as an Android or iPhone. Information stored on a mobile device is stored in different areas. The following summarizes popular areas where you can locate mobile device data:

- **ROM**: Read-only memory stores the operating system for the mobile device.
- **EEPROM**: Electrically Erasable Programmable Read-Only Memory contains system data for the mobile device. This data is stored in **EEPROM** so the service provider can update it as needed.
- **SIM card**: Located under the battery on the back of the cell phone, the Subscriber Identity Module (**SIM**) contains a microprocessor and **EEPROM** that is used to store routing information and authentication information for the mobile network. Older phones stored contacts and text messages on the **SIM** card by default, but newer phones have to be configured to do so.
- **Memory**: Depending on the mobile device, you may have additional memory or memory card slots to store other data such as pictures, videos, and data files.

Given the different types of mobile devices, how you perform the mobile forensics will depend on the device itself, but there are three key issues with mobile devices:

- **Maintaining power**: Since some of the data for the mobile device can be stored in memory that could be lost when the device loses power, ensure that you can maintain power to the device. This means that when you seize the mobile device, you should try to find the power adapter for the device.
- **Synchronization**: Prevent the mobile device from synchronizing with a computer because the synchronization may remove data from the device. If the mobile device is connected to a computer when you arrive at the scene, you should disconnect it to prevent synchronization.
- **Prevent remote wipe**: Be sure that you prevent the mobile device from receiving any signals, because a signal could be used to send a remote wipe command to the device. A **Faraday bag** can be used to shield the mobile device from communicating with any other components.

![Image](exam.jpg)

> **For the Security+ certification exam, know that you should store a mobile device collected as evidence in a Faraday bag to block any signal to the mobile device, which will prevent data from appearing or disappearing on the device after it has been seized. The Faraday bag also helps prevent the suspect from remotely wiping the device, because the remote wipe signal will be blocked.**

## EXERCISE 21-6: Performing Cell Phone Forensics

![Image](video.jpg)
