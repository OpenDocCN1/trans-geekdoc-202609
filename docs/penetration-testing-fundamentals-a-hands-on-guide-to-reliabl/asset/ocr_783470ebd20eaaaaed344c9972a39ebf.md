8. Which of the following commands would enumerate local network computers?

+   - A. **net share**
+   - B. **net enum**
+   - C. **net view**
+   - D. **net scan**

9. What is found in the Registry key HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\NetworkList\Profiles\?

+   - A. Wi-Fi SSID
+   - B. USB devices
+   - C. Internet Explorer passwords
+   - D. Uninstalled programs

# PROJECTS

# PROJECT 1

Download Cain and Abel and use it on your own machine or a lab machine to extract data. You can get the tool from http://www.oxid.it/cain.html.

# PROJECT 2

Try the various **net** commands, including **netshell**, on a lab computer. Make sure you are familiar with all of them.

Execute each of the following commands:

+   - **net users**
+   - **net view**
+   - **net session**
+   - **net session \\computername** (replace *computername* with your partner’s computer)
+   - **net share**

# netsh

Execute the following:

```
netsh firewall set portopening tcp 445 smb enable
```