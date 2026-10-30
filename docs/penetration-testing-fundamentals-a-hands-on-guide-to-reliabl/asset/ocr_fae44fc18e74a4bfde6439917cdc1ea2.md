It takes a bit of time to get comfortable with all of the command line flags; however, this is a very important tool and well worth the time spent. The reason why it is so important is that it is very popular with attackers. If you scan your wireless network with the same tool that attackers are likely to use, and you find problems and correct those, then your network is less vulnerable to wireless attacks.

When you download Aircrack you will notice a number of executables in the bin directory. There is airdecloak-ng.exe; airodump-ng.exe; aircrack-ng-avx2.exe; etc. Each of these has a different wireless function. Here are a few basic commands:

+   - **airodump-ng interface:** This will do packet capture for the interface designated.
+   - **airodump-ng -c 11 --bssid 00:01:02:03:04:05 -w dump interface:** The -c indicates the Wi-Fi channel, in this case 11. The -w indicates to dump to hard drive. The -bssid will define the bssid of the wireless you wish to capture. For older encryption, like WEP, you can capture around 50,000 packets and you should be able to crack it.
+   - **aircrack-ng -b 00:01:02:03:04:05 dump-01.cap:** This tells Aircrack to take the packet dump and try to crack it.

# General Scanners

There are several scanners that are general vulnerability scanners. These should be a part of your toolset for penetration testing. We will look at a few of the more common scanners in this section.

# MBSA

Microsoft Baseline Security Analyzer is not the most robust vulnerability scanner. However, it is a free download, and in addition to finding vulnerabilities, it is useful in finding configuration issues with Windows machines. You can download MBSA from:

https://www.microsoft.com/en-us/download/details.aspx?id=7558

In addition to being free, it is very easy to use. You can see the output from MBSA in Figure 8-10.

MBSA is a limited vulnerability scanner. It is primarily used just to find common, basic Microsoft issues; however, it is a free download and remarkably easy to use. For that reason, it should certainly at least be considered.