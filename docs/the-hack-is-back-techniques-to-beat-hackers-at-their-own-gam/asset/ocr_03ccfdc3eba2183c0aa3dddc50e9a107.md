You can also use John the Ripper to crack the password hash. John (the Ripper) has been around forever and you can crack many different types of password hashes with it using brute force or one of the many dictionary files available, like rockyou.txt. Another newer password-cracking tool is hashcat which is more optimized for using a Graphics Processor Unit (GPU) to aid in revealing the password hash.

![](bbox=[0.19, 0.19, 0.81, 0.319])

**FIGURE 1.22**  The password hash in cracked using John the Ripper.

Now I thought about this (and was teaching a lesson) and realized that some of you might not want to, or be in a position to disable AV on a host. There is another way to dump those hashes without using any malicious software. Instead, you can use a combination of two forensic tools to capture the system RAM and then you can dump the password hashes from image of memory. The easiest tool to dump RAM with is FTK Imager Lite, which does not even have to be installed on your system, thus even further minimizing any type of footprint.

![](bbox=[0.29, 0.492, 0.71, 0.801])

**FIGURE 1.23**  FTK Imager.

There are also command line tools, like dumpit (https://www.magnetforensics.com/resources/magnet-dumpit-for-windows/) which can be downloaded and added to a USB drive and then you can insert the USB drive into the system, invoke the Accessibility Options executable Utilman.exe (really cmd.exe) and switch to the drive letter of the USB drive, run dumpit, and capture the RAM to the external drive, use volatility to dump the password hash (hashdump plugin), and then run an