
![warning](images/warning.png)A longer key length, such as 128 bits or 192 bits, doesn’t make WEP exponentially more difficult to crack because WEP’s static key scheduling algorithm requires that only about 20,000 or so additional packets be captured to crack a key for every extra bit in the key length.

The wireless industry came up with a solution to the WEP problem, called Wi-Fi Protected Access (WPA). WPA uses the Temporal Key Integrity Protocol (TKIP) encryption system, which fixes all the known WEP issues. WPA2, which quickly replaced the original WPA, uses an even stronger encryption method called Counter Mode Cipher Block Chaining Message Authentication Code Protocol (say that fast three times), or CCMP for short, based on the Advanced Encryption Standard (AES). WPA3, which addresses shortcomings in WPA2, is on its way in devices manufactured after the last quarter of 2018, so be on the lookout for it.

One other thing worth noting: WPA and WPA2 running in “enterprise mode” require an 802.1*x* authentication server, such as a RADIUS server, to manage user accounts for the network. Wireless networks running with this type of configuration are difficult to crack, so your testing efforts would be better served elsewhere on your network.

![remember](images/remember.png)For nonenterprise wireless APs (and that’s mostly what I see in business), there’s no good reason to *not* run WPA2 with preshared keys (PSKs).

You can also use aircrack to crack WPA and WPA2-PSK. To crack WPA-PSK encryption, you have to wait for a wireless client to authenticate with its access point. A quick-and-dirty way to force the reauthentication process is to send a deauthenticate packet to the broadcast address. Peter T. Davis and I cover this topic in detail in *Hacking Wireless Networks For Dummies* (John Wiley & Sons, Inc.).

You can use airodump to capture packets and then start aircrack (or run them simultaneously) to initiate cracking the PSK by using the following command-line options:

`#aircrack-ng -a2 -w path_to_wordlist &lt;capture file(s)>`

![warning](images/warning.png)WPA key recovery depends on a good dictionary. The dictionary files available at [`www.outpost9.com/files/WordLists.html`](http://www.outpost9.com/files/WordLists.html) are a good starting point. Even with a great dictionary chock-full of potential passwords, I’ve often found that dictionary attacks against WPA are futile. Know your limits so that you don’t waste too much time trying to crack WPA PSKs that aren’t crackable.

Another commercial alternative for cracking WPA and WPA2 keys is ElcomSoft Wireless Security Auditor (EWSA). To use EWSA, simply capture wireless packets in the tcpdump format (every WLAN analyzer supports this format) and load the capture file into the program; shortly thereafter, you have the PSK. EWSA is a little different because it can crack WPA and WPA2 PSKs in a fraction of the time it normally takes, but there’s a caveat: You must have a computer with a supported NVIDIA or AMD video card. Yep, EWSA doesn’t just use the processing power of your CPU; it also harnesses the power and mammoth acceleration capabilities of the video card’s graphics processing unit (GPU). Now, that’s innovation!

The main EWSA interface is shown in [Figure 10-7](#c10.xhtml#c10-fig-0007).

![ FIGURE 10-7:  Using ElcomSoft Wireless Security Auditor to crack WPA PSKs.](images/9781119485476-fg1007.png)

 [FIGURE 10-7:](#c10.xhtml#rc10-fig-0007)  Using ElcomSoft Wireless Security Auditor to crack WPA PSKs.

![tip](images/tip.png)Using EWSA, you can try to crack your WPA/WPA2 PSKs at a rate of up to 173,000 WPA/WPA2 PSKs per second. Compare that with the lowly few hundred keys per second using just the CPU, and you can see the value in a tool like this one. I always say you get what you pay for!

![remember](images/remember.png)If you need to use your network analyzer to view traffic as part of your security assessment, you won’t see any traffic if WEP or WPA/WPA2 is enabled unless you know the keys associated with each network. You can enter each key into your analyzer, but hackers can do the same thing if they’re able to crack your WEP or WPA PSKs by using one of the tools I mention earlier.

[Figure 10-8](#c10.xhtml#c10-fig-0008) shows how you can view protocols on your WLAN by entering the WPA key in Omnipeek via the Capture Options window before you start your packet capture.

![ FIGURE 10-8:  Using Omnipeek to view encrypted wireless traffic.](images/9781119485476-fg1008.png)

 [FIGURE 10-8:](#c10.xhtml#rc10-fig-0008)  Using Omnipeek to view encrypted wireless traffic.

### Countermeasures against encrypted traffic attacks

The simplest solution to the WEP problem is to migrate to WPA2 for all wireless communications. You can also use a virtual private network in a Windows environment — free — by enabling Point-to-Point Tunneling Protocol (PPTP) for client communications. Or you can use the IPSec support built into Windows, as well as Secure Shell (SSH), Secure Sockets Layer/Transport Layer Security (SSL/TLS), and other proprietary vendor solutions to keep your traffic secure. Just keep in mind that cracking programs are available for PPTP, IPSec, and other VPN protocols as well, but overall you’re pretty safe, especially compared with having no virtual private network at all.

Newer 802.11-based solutions exist as well. If you can configure your wireless hosts to regenerate a new key dynamically after a certain number of packets have been sent, the WEP vulnerability can’t be exploited. Many AP vendors have already implemented this fix as a separate configuration option, so check for the latest firmware with features to manage key rotation. The proprietary Cisco LEAP protocol, for example, uses per-user WEP keys that offer a layer of protection if you’re running Cisco hardware. Again, be careful, because cracking programs exist for LEAP, such as *asleap* ([`http://sourceforge.net/projects/asleap`](http://sourceforge.net/projects/asleap)). The best thing to do is just stay away from WEP.

The 802.11i standard from the Institute of Electrical and Electronics Engineers (IEEE) integrates the WPA fixes and more. This standard is an improvement on WPA but isn’t compatible with older 802.11b hardware because of its implementation of the Advanced Encryption Standard (AES) for encryption in WPA2.

If you’re using WPA2 with a PSK (which is more than enough for small Wi-Fi), ensure that the key contains at least 20 random characters so that it isn’t susceptible to the offline dictionary attacks available in such tools as Aircrack-ng and ElcomSoft Wireless Security Auditor. The attack settings for ElcomSoft Wireless Security Auditor are shown in [Figure 10-9](#c10.xhtml#c10-fig-0009).

![ FIGURE 10-9:  ElcomSoft Wireless Security Auditor’s numerous password cracking options.](images/9781119485476-fg1009.png)

 [FIGURE 10-9:](#c10.xhtml#rc10-fig-0009)  ElcomSoft Wireless Security Auditor’s numerous password cracking options.

As you can see, everything from plain dictionary attacks to combination attacks to hybrid attacks that use specific word rules are available. Use a long, random PSK so you don’t fall victim to someone with a lot of time on his hands!

Keep in mind that although WEP and weak WPA PSKs are crackable, they’re still much better than no encryption at all. Similar to the effect that home security system signs have on would-be home intruders, a wireless network running WEP or weak WPA PSKs isn’t nearly as attractive to a criminal hacker as one without it. Many intruders are likely to move on to easier targets unless they really want to get into yours.

### Wi-Fi Protected Setup
