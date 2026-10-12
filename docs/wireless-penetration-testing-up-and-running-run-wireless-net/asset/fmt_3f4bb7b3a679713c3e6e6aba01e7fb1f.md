
All five factors described in the previous paragraph can be obtained by an attacker smelling the air and listening to the entire conversation. The PSK is the only thing he lacks. So, how does a PSK get made? It is calculated by combining the WPA-PSK pass and the SSID provided by the user. The `Password-Based Key Derivation Function` (`PBKDF2`) is used to generate the 256-bit shared key from the combination of both.

The attacker would employ a big dictionary of possible passphrases with the attack tool in a standard WPA/WPA2 PSK dictionary assault. The tool would generate the PTK by extracting the 256-bit PSK from each of the passphrases and combining it with the other parameters specified earlier. One of the handshake packets' `Message Integrity Check` (`MIC`) will be verified using the PTK. If the pass from the dictionary matches, the guess was accurate; if not, it is incorrect.

If the authorized network passphrase is found in the dictionary, it will eventually be identified. This is how PSK is cracking for WPA/WPA2 works! The steps are illustrated in *[Figure 4.10](#c04.xhtml#fig4_10)*:

![](images/Figure-4.10.jpg)

**Figure 4.10:** WPA/WPA2 dictionary attack

# Cracking WPA-PSK and WPA2-PSK passphrase

To get started, simply follow the provided instructions.

1.  Let us first connect to our Wireless Lab access point and configure it to use WPA2-PSK [AES]. We will change the WPA2-PSK [AES] password to `abcdefgh` to make it vulnerable to dictionary attacks, as shown in *[Figure 4.11](#c04.xhtml#fig4_11)*:

    ![](images/Figure-4.11.jpg)

    **Figure 4.11:** Netgear router setting

2.  Type the following command into the Terminal:

    ```
    airmon-ng start wlan0
    ```

    The `wlan0` interface will be started in monitor mode with this command, as shown in *[Figure 4.12](#c04.xhtml#fig4_12)*:

    ![](images/Figure-4.12.jpg)

    **Figure 4.12:** airmon-ng command

3.  Press *Enter* after typing the following command:

    ```
    airodump-ng wlan0
    ```

    We will be able to inject packets into a wireless network because of this, as shown in *[Figure 4.13](#c04.xhtml#fig4_13)*:

    ![](images/Figure-4.13.jpg)

    **Figure 4.13:** airodump-ng command_1

4.  Press *Enter* after typing the following command, as shown in *[Figure 4.14](#c04.xhtml#fig4_14)*:

    ```
    airodump-ng -c 11 -w wpacracking --bssid DC:EF:09:59:B1:1F wlan0
    ```

    ![](images/Figure-4.14.jpg)

    **Figure 4.14:** airodump-ng command_2

5.  We can either wait for a fresh client to connect to the access point so that we can capture the four-way WPA2 handshake or we can force clients to re-join by sending a broadcast deauthentication packet. To make things go faster, we do the latter. With the unknown channel error, the same thing can happen. Use `--ignore-negative-one` once more. This may necessitate multiple attempts, as shown in *[Figure 4.15](#c04.xhtml#fig4_15)*:

    ```
    aireplay-ng --deauth 1 -a DC:EF:09:59:B1:1F wlan0 --ignore-negative-one
    ```

    ![](images/Figure-4.15.jpg)

    **Figure 4.15:** aireplay-ng command

6.  When we capture a WPA2 handshake, the airodump-ng program will display a WPA2 handshake followed by the access point's BSSID in the top-right corner of the screen. If you choose `– ignore-negative-one`, the tool may send a fixed channel message instead of the WPA2 handshake. Keep a lookout for a WPA2 handshake that flashes briefly.

7.  We can now terminate the airodump-ng utility. Let us look at the four-way handshake in Wireshark by opening the cap file. *[Figure 4.16](#c04.xhtml#fig4_16)* shows how your Wireshark terminal should look. In the snapshot, we have selected the first packet of the four-way handshake from the trace file. The EAPOL protocol is used in the handshake packets, as seen in *[Figure 4.16](#c04.xhtml#fig4_16)*, where the handshake does not contain data that helps recover the key but contains data that can be used to check if a key is valid or not.

    ![](images/Figure-4.16.jpg)

    **Figure 4.16:** Wireshark

8.  Now, we will start with the real key cracking! We will need a glossary of common words for this. Many dictionary files are included in Kali's `Metasploit` folder, as illustrated in *[Figure 4.17](#c04.xhtml#fig4_17)*. It is vital to remember that you are only as good as your dictionary when it comes to WPA2 cracking. Kali comes with a few dictionaries, but they may not be enough. People's passwords are influenced by a variety of factors. This contains information such as the users' home nation, prevalent names and phrases in that region, security knowledge, and a variety of other factors. When doing a penetration test, it is a good idea to combine country- and region-specific wordlists, as shown in *[Figure 4.17](#c04.xhtml#fig4_17)*:

    ![](images/Figure-4.17.jpg)

    **Figure 4.17:** Metasploit

9.  As demonstrated in *[Figure 4.18](#c04.xhtml#fig4_18)*, we will use the aircrack-ng software with the `pcap` file as the input and a link to the dictionary file as the output. As displayed in the terminal, I used `nmap.lst`:

    ```
    aircrack-ng wpacracking-05.cap -w /usr/share/wordlists/nmap.lst
    ```

    The dictionary file is used by aircrack-ng to test various combinations of passwords to crack the key. If the password is in the dictionary file, it will be cracked eventually, and your screen will look like the one in *[Figure 4.18](#c04.xhtml#fig4_18)*:

    ![](images/Figure-4.18.jpg)

    **Figure 4.18:** aircrack-ng command

10. Please keep in mind that because this is a dictionary attack, the password must be present in the dictionary file you submit to aircrack-ng. The attack will fail if the pass is not found in the dictionary!

We feed the capture file containing the WPA2 four-way handshake and a list of common passphrases (in the form of a wordlist) to Aircrack-ng because WPA2-PSK is vulnerable to a dictionary attack. Aircrack-ng can crack the WPA2-PSK shared pass because the pass `abcdefgh` is contained in the wordlist. It is worth repeating that you are only as good as the dictionary you have in WPA2 dictionary-based cracking. As a result, it is critical to start by compiling a vast and detailed lexicon. Even though Kali comes with its own vocabulary, it may be insufficient at times and require additional words.

# Speeding up WPA and WPA2 Cracking

As we saw in the last section, if we have the right password in our dictionary, breaking WPA2-Personal is a piece of cake. So, why do we not simply compile a massive dictionary of millions of commonly used passwords and phrases? This would be extremely beneficial to us, and we would almost always succeed in cracking the password. Everything sounds fantastic, but there is one thing missing: the time spent. The Pre-Shared key using the PSK pass and the SSID through the `PBKDF2` is one of the more CPU and time-consuming calculations. Before returning the 256-bit Pre-Shared key, this function hashes the combination of both over 4,096 times. The next stage in the cracking process is to use this key, along with parameters from the four-way handshake, to verify the handshake against the `MIC`. This is a low-cost computational phase. Furthermore, the characteristics of the handshake will vary from time to time; therefore, this phase cannot be pre-calculated. As a result, to speed up the cracking process, we must calculate the Pre-Shared key from the pass as quickly as feasible.

Pre-calculating the Pre-Shared Key, also known as the `Pairwise Master Key` (`PMK`) in 802.11 standard jargon, can help speed things up. It is worth noting that because the SSID is also used to calculate the `PMK`, we will get a different `PMK` if we use the same pass but a different SSID. As a result, the `PMK` is dependent on both the passcode and the SSID.

# Speeding up the cracking process
