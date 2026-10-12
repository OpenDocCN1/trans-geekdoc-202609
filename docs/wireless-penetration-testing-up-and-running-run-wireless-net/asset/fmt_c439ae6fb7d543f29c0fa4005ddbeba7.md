
We can go ahead and do the following:

1.  Using the `genpmk` tool, we can compute the PMK for a given SSID and wordlist ahead of time:

    ```
    genpmk -f <chosen wordlist> -d PMK-Wireless-Lab -s “Wireless Lab”
    ```

    This generates the `PMK-Wireless-Lab` file, which contains the PMK, as can be seen in *[Figure 4.19](#c04.xhtml#fig4_19)*:

    ![](images/Figure-4.19.jpg)

    **Figure 4.19:** genpmk command

2.  We will now build a WPA-PSK network with the passphrase `abcdefgh` (found in the dictionary) and capture a WPA handshake for it. As illustrated in the accompanying *[Figure 4.20](#c04.xhtml#fig4_20)*, we now use `Cowpatty` to crack the WPA passphrase:

    ```
    cowpatty -d PMK-Wireless-Lab -s “Wireless Lab” -r wpacracking-05.cap
    ```

    ![](images/Figure-4.20.jpg)

    **Figure 4.20:** Cowpatty command

    `Cowpatty` uses the pre-calculated PMKs to crack the key in approximately 6 seconds.

3.  With the same dictionary file, we now run `aircrack-ng`, and the cracking operation takes almost 22 minutes. This demonstrates how much we gain because of the pre-calculation.

4.  We will need to use a tool named `airolib-ng` to use these PMKs with `aircrack-ng`, as follows:

    ```
    airolib-ng PMK-Aircrack --import cowpatty PMK-Wireless-Lab
    ```

    Where `PMK-Aircrack` is the `aircrack-ng` compatible database to be built, and `PMK-Wireless-Lab` is the previously created `genpmk`-compliant PMK database. Refer to *[Figure 4.21](#c04.xhtml#fig4_21)*:

    ![](images/Figure-4.21.jpg)

    **Figure 4.21:** airolib-ng command

5.  We now feed this database to `aircrack-ng`, which significantly speeds up the cracking process. The following command is used, as shown in *[Figure 4.22](#c04.xhtml#fig4_22)*:

    ```
    aircrack-ng -r PMK-Aircrack wpacracking-05.cap
    ```

    ![](images/Figure-4.22.jpg)

    **Figure 4.22:** aircrack-ng command

6.  Additional Kali tools, like `Pyrit`, can make use of multi-processor platforms to speed up cracking. Intel® CoreTM i7 CPUs, for example, can do faster cracking operations. The `-r` option specifies the `pcap` filename, whereas I specify the `genpmk`-compliant PMK file. `Pyrit` takes roughly 3 seconds to break the key on the same system as the preceding tools, using the same PMK file prepared using `genpmk`.

**In addition to the aforementioned factors, the length of the WPA/WPA2 PSK plays a major role in the cracking process. The cracking of longer passes takes longer.**

# [Spoofing your mac address](#toc.xhtml#s82a)

You might be aware that MAC address filtering is not entirely secure. It is much less effective than WEP encryption, in my opinion, because it is trivial to forge. This is not to say that MAC address filtering is not useful. It does filter out many attackers who are only interested in the weakest link networks. Whatever you do, do not rely just on MAC filtering! WEP encryption is preferable to no encryption. Refer to *[Figure 4.23](#c04.xhtml#fig4_23)* for an illustration of MAC Spoofing:

![](images/Figure-4.23.jpg)

**Figure 4.23:** MAC spoofing

This does not necessitate a high level of competence. All you must do is listen in on wireless network traffic and change your MAC address to someone who is already connected. Changing your MAC address is as simple as 1, 2, and 3 with automation scripts or applications. Then, using an application called `macchanger`, let us see how we can spoof our MAC address.

1.  Open the Terminal.

2.  Press *Enter* after typing the following command:

    ```
    ifconfig wlan0 down
    ```

    This command disables or turns off the wireless interface, as shown in *[Figure 4.24](#c04.xhtml#fig4_24)*:

    ![](images/Figure-4.24.jpg)

    **Figure 4.24:** ifconfig wlan0 down command

3.  To reactivate `wlan0`, use the following command and press *Enter*, as shown in *[Figure 4.25](#c04.xhtml#fig4_25)*:

    ```
    ifconfig wlan0 up
    ```

    ![](images/Figure-4.25.jpg)

    **Figure 4.25:** ifconfig wlan0 up command

4.  Press *Enter* after typing the following command:

    ```
    macchanger --random wlan0
    ```

    This command generates a fake MAC address for the wireless interface at random, as shown in *[Figure 4.26](#c04.xhtml#fig4_26)*:

    ![](images/Figure-4.26.jpg)

    **Figure 4.26:** macchanger command_1

5.  Press Enter after typing the following command:

    ```
    macchanger --mac=00:11:22:33:44:55 wlan0
    ```

    As displayed, this command allows you to fake a MAC address on the wireless interface, as shown in *[Figure 4.27](#c04.xhtml#fig4_27)*:

    ![](images/Figure-4.27.jpg)

    **Figure 4.27:** macchanger command_2

It is as simple as that! Is it not simple? Knowing this can help you avoid paid hotspot networks where you must pay money for a long period of time. These networks will be available in coffee shops, restaurants, airports, and hotels. When a user pays, their MAC address is added to the list of permitted MAC addresses for internet access.

# [Protect yourself from wireless attacks](#toc.xhtml#s83a)

We must always be aware of how to defend ourselves against such dangers and attacks.

Following that, we will go over ways to defend yourself against these attacks:

*   Encryption that is more robust reduces the likelihood of an attack.
*   MAC filtering can also help to lessen the chances of an attack.
*   If your devices are not compatible with WPA/WPA2, you can use WEP instead; however, it is not suggested because it is insecure.
*   To restrict access to a business network, create a distinct VLAN.
*   WPS settings should be disabled or turned off.
*   Make a strong, complicated passphrase.
*   Passwords should be changed every three to four months.
*   Use the manufacturer’s default passwords only as a last resort.
*   Instead of PSK, use EAP.
*   Change the SSID name that comes up by default.

# [Conclusion](#toc.xhtml#s84a)

We put prepared an offensive plan in this chapter. Following that, we outlined many attack methods. Then we went through the details of WEP, WPA, and WPA2 encryption. Finally, we outlined a few strategies for reducing the likelihood of a wireless attack.

In the upcoming chapter, we will look at how to identify hosts on a wireless network, figure out how big it is, and spot susceptible devices and systems on it. Let us start!

# [Questions](#toc.xhtml#s85a)

1.  Explain the WEP encryption?
2.  How do you crack the WEP encryption?
3.  Explain the WPA/WPA2 encryption?
4.  How crack the WPA/WPA2 encryption?
5.  How do you protect yourself from wireless attacks?

# [CHAPTER 5](#toc.xhtml#c05)

# [Gain Access to Wireless Network](#toc.xhtml#c05)

# [Introduction](#toc.xhtml#s86a)

We have arrived at the fifth chapter! In this chapter, we will cover a variety of topics related to having network access as a wireless penetration tester. We will conduct network evaluations to identify hosts, calculate network size, and identify vulnerable hosts. When doing a penetration test, it is a good idea to know how many hosts are on the network because you do not want to leave anything out. Let us start by talking about why this is so crucial.

# [Structure](#toc.xhtml#s87a)

In this chapter, we will discuss the following topics:

*   Identifying hosts
*   Determining network size
*   Detecting vulnerable hosts
*   Preventing against threats

# [Objectives](#toc.xhtml#s88a)

In this chapter, you will understand why it is important to find the number of live hosts when conducting a penetration test on a network. Next, you will be identifying hosts on the network with Kali Linux. Then, you will determine network size and explain why it is important to understand as a penetration tester. In the end, you will be able to detect vulnerabilities in Windows 7 using the `Nessus` vulnerability scanner, and you will able also to use several preventions that could help reduce risk.
