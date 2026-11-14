+   3. Set up specific hotkeys such as ALT-TAB to prevent the victim from switching to other windows.
+   4. Set the malicious window as the topmost so that any other window that might pop up will always be behind it.
+   5. Restrict the usage of the mouse to the area where the malicious window is located.

Although the consequence of having your Desktop locked by the malware is scary, most of the time this kind of malware comes as a stand-alone program that is executed from a specific location in your file system. Therefore, it is pretty easy to deactivate it: just boot the machine with a live CD, mount the Windows hard drive if you're using a Linux distro, and search for executables under the infected user's account. Here are the common paths you should check:

```
c:\Users\<user>\AppDatac
:\Users\<user>\Local Settings
c:\Users\<user>\Application Data
```

Alternatively, you can boot in Safe mode and go to the Run registry key, where you might find the executable name (although multiple places in the Registry are used to start the malware after reboot):

```
HKLM\Software\Microsoft\Windows\CurrentVersion\Run
```

# Wannacry

Wannacry is an infamous ransomware worm that appeared in May 2017 and quickly made headlines worldwide. It is labeled a worm because it used the CVE-2017-0144 vulnerability, named ETERNALBLUE, in the Server Message Block (SMB) protocol to infect vulnerable Windows hosts on the Internet. The ETERNALBLUE vulnerability was famous because it was disclosed as part of the information leak by the Shadow Brokers hacking group. The group released to the public several exploits that were developed and used by the NSA, one of which was ETERNALBLUE.

Wannacry is part of the crypter ransomware family because it encrypts the victim's data and holds it for ransom. In this section, we examine different approaches to analyzing Wannacry ransomware and try to answer following questions:

+   • How are the files encrypted and which cryptographic algorithms are used?
+   • Is it possible to decrypt the ransomed files?

# Example 19-3: Analyzing Wannacry Ransomware

Identifying and understanding the encryption scheme used by ransomware is one of the most important pieces of information for the affected victims. This information can help