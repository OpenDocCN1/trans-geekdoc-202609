Using a shared key generally means that there will be a great deal of traffic encrypted with the same key. This makes it far easier for cryptanalysis programs to crack the key. Once the key is cracked, then all security is gone.

To address this concern, 802.11i and WPA in PSK/personal mode only use the shared initial key very briefly—when a client first authenticates itself to the access point (Step 2). After authentication, the access point sends the client an unshared session key (Step 3) for use during the session (Step 4). With only a few messages transmitted using the shared initial key, cryptanalysis to discover the shared initial key is effectively impossible.

However, PSK/personal mode has one serious operational security issue. Unless the shared initial key is complex, cryptanalysis of the initial key will be possible. In practice, the administrator or user has to type a passphrase into every wireless client and the access point. The equipment generates the key from this passphrase. Long passphrases produce strong keys, but if the passphrase is too short, then 802.11i or WPA in PSK/personal mode will have very weak security. Passphrases must be at least 20 characters long, and longer passphrases are better.

> In 802.11i or WPA in PSK/personal mode, passphrases must be at least 20 characters long.

# Test Your Understanding

+   20. a. Why is 802.1X mode unsuitable for homes and small offices?
+       b. What mode was created for homes or very small businesses with a single access point?
+       c. How do users in this mode authenticate themselves to the access point?
+       d. Why is using a shared initial key not dangerous?
+       e. How are PSK/personal keys generated?
+       f. How long must passphrases be for adequate security?

# Wireless Intrusion Detection Systems

Companies that have central management for their many access points can purchase centralized wireless intrusion detection system software. As Figure 4-32 illustrates, each access point becomes a wireless IDS agent, sending appropriate information to the central wireless IDS console. The console transfers the data to an IDS database. It also sorts through data in the database to find indications of problems.

There is a good chance that a centralized wireless IDS can identify rogue or evil twin access points. There are two alternatives to using a centralized wireless IDS but neither are very effective.

The first is simply not to worry about intrusion detection. Given the commonness of wireless attacks, this is hardly wise. The second alternative is to walk around the building frequently with a laptop that has wireless IDS software. This is likely to require a prohibitive amount of labor, and it cannot catch threats that appear after the wireless security administrator has checked a part of the site for threats. Nor is this approach likely to catch evil twin access points, which only operate occasionally and so may not be operating when the wireless administrator is sweeping the building for concerns.