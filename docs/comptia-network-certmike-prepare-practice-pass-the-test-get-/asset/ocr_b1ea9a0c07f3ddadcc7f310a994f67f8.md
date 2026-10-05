Troubleshooters can measure the RSSI at the client device location to quantify the signal loss in decibels (dB). Higher frequencies are subject to attenuation than lower ones, so a 5 GHz network is likely to attenuate more over the same distance than a 2.4 GHz network. To address an excess loss of signal due to attenuation, troubleshooters can do any of the following:

+   * Move the client device and the WAP closer.
* Add another WAP closer to the client.
* Replace the antenna on the access point with one more suitable to the environment.

# Wrong SSID

The service identifier (SSID) is the name by which a wireless network is identified by clients. When a wireless device starts, it searches the frequencies for nearby SSIDs and displays them as a list from which the user can choose. Selecting the wrong SSID from the list or typing an incorrect SSID will attempt to connect the device to a neighboring network.

In case of properly secured networks, the device will fail to authenticate to the wrong network and no connection will be established. In the case of unprotected networks, however, the device will connect to the wrong SSID, and it may take some time for the user to recognize that they are not connected to their usual network.

# Incorrect Passphrase

On a wireless network that uses a shared key for authentication, mistyping the key will cause the connection attempt to fail. Passphrases are case sensitive, and they are often masked in the interface, making it easy for users to mistype them without noticing.

As noted in Chapter 21, "Network Troubleshooting Methodology,"trouhooters should always question the obvious. When a user reports that they are unable to connect to the network, the troubleshooter should make sure they are typing the correct passphrase before exploring more complicated possibilities.

# Encryption Protocol Mismatch

Encryption issues are one of the most common problems faced by wireless troubleshooters. For a client device to connect to a WAP, both must be configured to use the same encryption protocol. With an incorrect passphrase, an encryption protocol mismatch will prevent the client from establishing a connection to the network. For example, a user might easily select the Wi-Fi Protected Access (WPA) security protocol instead of WPA2. Despite being different versions of the protocol, the two are not compatible, and the connection will fail.

For troubleshooters, the easiest way to determine whether a connection problem is due to a security issue is to temporarily configure the client device and the WAP with no