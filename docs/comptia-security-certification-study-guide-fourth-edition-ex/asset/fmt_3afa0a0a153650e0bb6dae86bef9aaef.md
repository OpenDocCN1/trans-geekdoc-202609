
# EAP-TLS

EAP-TLS is the EAP protocol that uses TLS security for secure authentication on wireless networks. The EAP-TLS solution typically involves the use of client certificates to perform the authentication.

# EAP-TTLS

EAP-TTLS builds on EAP-TLS by having the capabilities to authenticate both the client and the server, although the client does not need to use certificates for authentication. The server can authenticate the client after a secure channel is set up using the server's certificate.

When configuring WPA on the wireless network, note that WPA operates in the following modes:

# WPA Personal

WPA Personal is also known as WPA-PSK, which means WPA preshared key. With WPA Personal, you configure the access point with a starting key value, known as the preshared key, which is then used to encrypt the traffic. This mode is used most by home users and small businesses.

# WPA Enterprise

WPA Enterprise, also known as WPA-802.1X, is a WPA implementation that uses a central authentication server such as a RADIUS server for authentication and auditing features. WPA Enterprise is used by larger organizations so that they can use their existing authentication server to control who has access to the wireless network and to log network access.

# Open

An open wireless network does not require any password to connect and does not use any form of encryption to keep the wireless data secret from prying eyes. Naturally, it is not recommend to leave your wireless network open (you should implement WPA2) or to connect your client system to an open network that you are not familiar with.

![Images](job.jpg)

**Although the Security+ certification exam will test your knowledge of WEP, WPA, WPA2, WPA3, and open networks, be sure to implement WPA2 or WPA3 in the real world because they are the more secure protocols.**

![Image](exam.jpg)

**For the exam, remember that WPA2 uses CCMP with AES as the symmetric encryption algorithm for data privacy, while WPA uses TKIP.**

## WPA2

WPA2 improves upon the security of WPA and should be used instead of WPA if you have the choice. WPA2 uses `Counter Mode with Cipher Block Chaining Message Authentication Code Protocol (CCMP or CCM Mode Protocol)` for data privacy, integrity, and authentication on a WPA2 wireless network. WPA2 uses CCMP with the `Advanced Encryption Standard (AES)` protocol for encryption of wireless traffic instead of TKIP and also supports additional features such as added protection for ad hoc networks and key caching.

Because WPA2 uses AES as its encryption protocol, it supports 128-bit, 192-bit, and 256-bit encryption.

![Image](video.jpg)

**To see how to configure WPA2, watch the video included in the online resources that accompany this book.**

## WPA3

In 2018, a new wireless security protocol was created known as WPA3, which improves on the security of WPA2. Like the previous WPA security protocols, WPA3 supports personal and enterprise mode. With personal mode it uses CCMP-128, which uses AES-128 (128-bit encryption with AES in CCM mode), but in enterprise mode it uses 192-bit encryption.

WPA3 has been improved by using a number of security features such `Simultaneous Authentication of Equals (SAE)`, which increases security by allowing the access point to authenticate the client as well as the client to authenticate the access point. This improvement to the authentication security helps prevent the cracking of handshake traffic that is common with WPA2.

Another major improvement is that WPA3 uses session keys in the encryption process, which helps prevent one user from decrypting another user's traffic even though the wireless password/key used by both users is the same.

## RADIUS Federation

Another common security technology for authentication with wireless networks is `RADIUS federation`. With RADIUS federation, two or more organizations who trust each other can configure their RADIUS servers for mutual authentication. For example, if an employee of CompanyX is visiting an office of CompanyY and attempts to log on, the servers at CompanyY forward the authentication request to CompanyX. After the RADIUS server at CompanyX authenticates the user and generates a token, that token can then be used to access resources on the network of CompanyY due to trust set up between CompanyX and CompanyY.

# CERTIFICATION OBJECTIVE 9.02

# Securing a Wireless Network

When I purchased my first wireless router several years ago, I knew nothing about wireless and was concerned that I would be unable to set up the wireless network. My concerns were quickly dismissed when I took the wireless router (access point) out of the box and gave it power. My laptop connected almost immediately! I was amazed at how easy it was to connect to the wireless network—there was `no` configuration required. Then it dawned on me—if my laptop connected with no configuration, what is stopping the rest of the world from connecting to my wireless network? The answer, of course, is that nothing is stopping someone from sitting outside my yard and connecting to my wireless network. I needed to figure out how to stop unauthorized access to my wireless access point.

You can use various techniques to prevent unauthorized persons from connecting to your wireless network. You may want to implement some or all of these features. To help secure your wireless infrastructure, consider changing settings on the router such as the admin password, the SSID, and MAC filtering, to name a few. The following are some basic best practices to secure your wireless router. You can see the steps to configure these features in the later section "Configuring a Wireless Network."

## Security Best Practices

Now that you have a basic understanding of wireless concepts and terminology, let's dive into some security best practices when configuring a wireless network. You should make a number of changes to the default configuration of a wireless access point in order to have a secure environment.

### Change the Admin Password

The first thing you should do after you take the wireless router out of the box and plug it in is change the admin password. The admin password is needed to connect to the web administration pages and change the settings of the router. All routers have a default admin password, so be sure to change the password from the default.

[Figure 9-3](#ch09.xhtml#ch9fig3) displays how to change the admin password on a D-Link router by going to the Tools link at the top and then choosing the Admin link on the left.

![Image](f0399-01.jpg)

FIGURE 9-3

Changing the admin password on a D-Link router

![Images](job.jpg)

**When performing any administration functions through web pages, it is critical that you use HTTPS instead of HTTP. In this example, you may need to configure the wireless router for HTTPS if it is not enabled by default.**

### Service Set Identifier

The Service Set Identifier (SSID) is a name you give the wireless network, and in order for someone to connect to your wireless network, that person needs to know the SSID. Any client who wishes to connect to your wireless network will need to specify the SSID name in their wireless network card settings. Therefore, it is important that you change the SSID from the default.

The problem is that wireless routers are configured to advertise this SSID automatically, so even if you change the SSID to something hard to guess, the router advertises the name. This means an individual can connect to your network by name without knowing in advance the name of the network because the router is advertising it. Proof of this is shown when you choose the option in Windows to connect to a network and a dialog box (shown in [Figure 9-4](#ch09.xhtml#ch9fig4)) displays all the wireless networks nearby.

![Image](f0400-01.jpg)

FIGURE 9-4

Displaying wireless networks close by
