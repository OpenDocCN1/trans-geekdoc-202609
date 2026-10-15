
**WPA/WPA2** Unlike WEP cracking, WPA/WPA2 cracking can only be performed under certain conditions. One of these situations is WPA being configured in pre-shared key mode, which is using a shared password as opposed to certificates. You need to use a tool like airodump-ng to capture the WPA/WPA2 authentication handshake. This means waiting for a new client to connect or forcing an already connected client to disconnect and reconnect. Then finally, you’ll need to brute-force the handshake to reveal the pre-shared key. Level1 **1.** Start your injection-capable wireless adaptor in monitor mode: 

```
airmon-ng start <adaptor - for example: wifi0>
 <wireless channel - for example: 9>
```

This puts the passive interface into monitor mode. **2.** Start capturing WPA handshakes: 

```
airodump-ng -c <wireless channel - for example: 9>
 --bssid <MAC of target access point>
 -w psk <passive interface – for example: ath0>
```

**3.** You can now force a client into de-authenticating and hopefully re-authenticating: 

```
aireplay-ng -0 1 -a <MAC of target access point>
 -c <MAC of client you want to trick into de-authenticating>
 <passive interface - for example: ath0>
```

**4.** Once you’ve captured the handshake, you can try to crack it: 

```
aircrack-ng -w <password dictionary file>
 -b <MAC of target access point> psk*.cap
```

/Level1 

* * *

 end feature 

Although eavesdropping on networking traffic may be useful for you to gain access to sensitive material, it doesn’t always directly transfer into data tampering. For you to embed your initialization code into web traffic, you have to go beyond purely eavesdropping techniques.

Once you have gained access to a wireless network, you’re now able to perform other network attacks, such as ARP spoofing, to impersonate a web proxy or other gateway device. ARP spoofing techniques are discussed in the following sections.

Apart from trying to gain unauthorized access to wireless networks in order to perform MitM attacks, another common technique is to trick clients into back to Computer A’s MAC address with its own MAC address.

An example of an ARP request and response, as displayed in Wireshark, is shown in [Figure 2-5](#c02.html#figure2-5).

 start figure 

[**Figure 2-5:**](#c02.html#figureanchor2-5) ARP traffic in Wireshark

![c02f005.tif](image_fi/662090c02/c02f005.png)

 end figure 

ARP spoofing is possible because the ARP protocol does not have any method to validate the ARP traffic. What makes ARP spoofing particularly effective is that you don’t need to wait for a broadcast requesting a MAC address.

You can proactively tell your target machine what MAC address maps to what IP. It is conducted by sending a gratuitous ARP messages to your target system. This will update the target’s local ARP cache with your crafted entry and results in all subsequent IP traffic being sent to you instead of the victim machine.

Ettercap, developed by Alberto Ornaghi and Marco Valleri,27 is one of the more popular tools to perform this style of MitM attack on a local network. In addition to ARP poisoning attacks, the tool can also be used to perform DHCP spoofing, port stealing, packet filtering, and more. dsniff, a separate suite of tools developed by Dug Song,28 provides similar features to ettercap, including various filters for credential sniffing and other MitM attacks.

If the following ARP spoofing example is conducted on a network with peering technologies, it has the potential to take down systems. The following example (and all examples) should be used with caution. Now you have been warned, you can use ettercap by entering the following at the command line:

```
ettercap -T -Q -M arp:remote -i <network interface> /<target1>/ /<target2>/
```

The attributes will select the following options:

*   \-T—Runs in text mode.

*   \-Q—Runs in super quiet mode, which suppresses a lot of output.

*   \-M—Performs a MitM attack.

*   arp:remote—Specifies that the MitM attack will be an ARP poisoning attack. The remote option allows you to sniff remote IP traffic targeting a gateway.

*   \-i—Specifies the network interface, for example wlan0.

*   The two targets allow you to specify which sets of IP address you want to poison. This can include a range of IP addresses, or the entire subnet. For example to poison every host in the subnet in respect to traffic traversing the gateway, use /<gateway IP>/ //

The output from the preceding command will be similar to the following. It includes visually displaying the HTTP response from DropBox to a client on the local network:
