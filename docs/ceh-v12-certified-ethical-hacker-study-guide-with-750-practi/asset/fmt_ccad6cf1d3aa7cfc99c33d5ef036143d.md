
# **************************** Evil Twin attacks menu
# ****************************
Interface `wlan0` selected. Mode: Managed. Supported bands: 2.4Ghz
Selected BSSID: None
Selected channel: None
Selected ESSID: None

Select an option from menu:
---------
0.  Return to main menu
1.  Select another network interface
2.  Put interface in monitor mode
3.  Put interface in managed mode
4.  Explore for targets (monitor mode needed)
--------------- (without sniffing, just AP) -----------------
5.  Evil Twin attack just AP
--------------------- (with sniffing) -----------------------
6.  Evil Twin AP attack with sniffing
7.  Evil Twin AP attack with sniffing and sslstrip
8.  Evil Twin AP attack with sniffing and bettercap-sslstrip2/BeEF
------------ (without sniffing, captive portal) -------------
9.  Evil Twin AP attack with captive portal (monitor mode needed)
---------

`airgeddon` requires two wireless interfaces to perform an evil twin attack. It needs this second interface for DoS pursuit mode, which prevents the frequency hopping that can be a protection against wireless attacks. The second interface is also used to perform a denial‑of‑service attack against the legitimate access point. This keeps it from responding to the station instead of the rogue access point.

While `airgeddon` is a useful tool, there is nothing it does that is unique. Under the hood, it is using a collection of tools that you need to already have in place, like `hostapd`, a DHCP server, DNSSpoof, and a lightweight HTTP server. The advantage to `airgeddon` is that it pulls all of those tools together. This makes complex, multitool attacks considerably easier. All you need to do is run `airgeddon` rather than having to set up several tools and get all the parameters right with them running in the correct order, as needed.

## Key Reinstallation

So far, you may have gotten the impression that wireless networks that are using WPA2 are invulnerable to attack, short of pretending to be the legitimate wireless network. When a station goes through a four‑way handshake, one of the outcomes is a session key that gets used for encryption and decryption. It's called a *session key* because it's used for the duration of the session while the station is connected to the access point. As these are potentially vulnerable over time, they are often replaced if the connection is maintained over a long period of time. This is not the only problem with session keys. Since session keys are derived rather than known ahead of time, if an attacker can force the use of a known value during key derivation, the key can be known.

The four‑way handshake is used to allow the station and the access point to derive a key based on a random value, or nonce, that is passed between the two ends. In the third message of the handshake, the client has what it needs to install the key used for the session. Since messages can get lost, especially as stations get farther from the access point, that third message can be retransmitted multiple times. We can take advantage of this in order to replay messages that have been captured previously. If the use of a known nonce could be forced, the encryption key would be known by the attacker. Since the key is known, messages can be decrypted or even injected into the communications channel.

If nonce value transmissions can be replayed, it means any key creation is vulnerable to attack. This not only means the session key between a station and an access point but also the group key. This exposes multicast and broadcast transmissions over a wireless network. Any modern wireless network, whether they are using WPA or WPA2, Enterprise or Personal, may be vulnerable to this sort of attack. As of this writing, there are not a lot of tools available to automate the exploitation of this Key Reinstallation Attack (KRACK). There are, however, some fixes available for network elements and this is likely to no longer be an issue.

## Using *mdk3/4*

Several tools exist for wireless attacks. One of these that can be used for multiple types of attacks is `mdk3`/`mdk4`. This is a tool that can be used to perform beacon flooding, authentication denial‑of‑service attacks, and deauthentication attacks, along with other tests. This is a tool that can be installed in Kali Linux and ParrotOS. Both versions are available in both operating systems. To get started, you need to enable monitor mode on the wireless interface. You can do this by using `airmon-ng` from the `Aircrack` toolkit. The following is the command used to turn on monitor mode on the interface `wlan0` on wireless channel 1:

```
kilroy@portnoy $ airmon-ng start wlan0 1
```

Once you have monitor mode enabled, you can start launching attacks. We can start an authentication attack on all available SSIDs on the channel you specified when you turned on monitor mode. The following is the command used to run the authentication attack using the interface `wlan0mon`:

```
kilroy@portnoy $ sudo mdk4 wlan0mon a
Waiting for targets…
Found new target AP 60:5F:8D:CD:77:A9
Found new target AP F8:BC:0E:05:BB:89
Found new target AP F8:BC:0E:05:D1:C9
Found new target AP 54:83:3A:AF:99:9D
Found new target AP 88:DA:1A:27:EB:C4
Found new target AP F8:BB:BF:7A:BF:03
Connecting Client F6:28:45:5A:18:AB to target AP 60:5F:8D:CD:77:A9 Status: No Response.
Packets sent:      1 - Speed:    1 packets/sec
```

This is a broad stroke attack, which isn't generally what you would be doing. Other attacks would be targeted at individual SSIDs. For these attacks, you'd need to provide some additional information. You could use a brute‑force attack to determine whether an SSID was cloaked. It will also look for whether an SSID is available within range. The following is one of these attacks against an SSID named WubbleWiFi:

```
kilroy@portnoy $ sudo mdk4 wlan0mon p -e WubbleWiFi
AP responded on 0 of 1 probes (0 percent)
Packets sent:      1 - Speed:    1 packets/sec
AP responded on 0 of 127 probes (0 percent)
Packets sent:    128 - Speed:  127 packets/sec
```

## Bluetooth

It's not only network transmission that has gone wireless. Peripherals have also gone wireless. More than that, any two devices that would commonly communicate over a wire may use a wireless protocol called Bluetooth. Bluetooth is a wireless protocol allowing for short‑range communication between one device and another. It operates in the set of frequencies referred to as the ISM band of 2.4 GHz. 802.11 uses a portion of the same frequency spectrum. While a Class A Bluetooth device has a range of about 100 meters due to a higher strength signal, most Bluetooth devices have a range of about 10 meters, requiring close proximity to interact with them.

Bluetooth offers a number of capabilities, described by profiles. Each Bluetooth device will implement a set of profiles, depending on the requirements for the device. For example, a Bluetooth headset would implement the Advanced Audio Distribution (A2DP) profile. This profile defines how multimedia audio may be streamed from one device to another. This is not the only profile a headset would implement, so each Bluetooth device may implement several profiles. When two devices are paired, they share their capabilities, meaning they tell each other what profiles they support.
