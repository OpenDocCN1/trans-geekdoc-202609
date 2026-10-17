
The setting is located at **HKLM\\SYSTEM\\CurrentControlSet\\Control\\Lsa\\Kerberos\\Parameters** and requires the **LogLevel** setting<sup>10</sup> of **0x1**. Once enabled, this shows the Kerberos activity logs and is clear when a large amount of attacks come through. However, Microsoft also states that this may create a performance degradation on the machine. Keep this in mind as we balance usability and security.

## Password Sprays

As discussed earlier, password sprays are attempting a small amount of specific and targeted passwords against many accounts on the system. The idea behind password sprays is that it is likely that a user on the network will use a predictable password. When paired with known passwords used in the environment, our chance of success increase dramatically.

After spending some time with intelligence gathering and reading information within the environment, it is very common to identify a "default" network password used by the organization. This can be something as simple as **Password123456** or could involve something such as the mascot or favorite local sports team. Generally, this information is shared via email or stored on file shares – once this password is uncovered we can attempt to spray it across many accounts to see how many are effective.

![](img/181571ad74cba0e6a2f38fcd2658651e_227_0.png)

**FIGURE 7.21** Diagram of a password spray attack, where a likely password is attempted against multiple accounts.

There are a handful of different protocols that are used to effectively attack a system with a password spray. LDAP, Kerberos, and NTLM are the three most commonly used protocols within an AD environment and can be used for various password spray attacks. There are several tools at our disposal to use here, however, there are many risks as well.

Spraying accounts with too many passwords can completely lock out individuals from their accounts. Depending on the configuration of the domain, the accounts could be locked out until they reach a specific time period or they are manually unlocked by an administrator. It is highly recommended that the password policy is identified and understood before beginning a password spray attack. Additionally, inform the point of contact of your intentions and ask if their actual password policy differs from the one identified.

Many spray tools are not lockout window and lockout attempt aware which leads to the risk of accounts being locked. This author has attempted several tools but was unable to find one that fits the bill for the specific spray attack with the confidence that it will operate as intended. To solve this problem, the program for pySpray was created. This is a python-based program that is lockout time and window aware. The pySpray program is available at [https://github.com/m4lwhere/pySpray](https://github.com/m4lwhere/pySpray) for download.

Running this program is simple, we must provide a list of usernames, passwords, the domain, the lockout number, and lockout window. This also informs the user how many total attacks will be attempted against the environment, notably the amount of passwords multiplied by the amount of users. This is done as an intended way to ensure the user understands the amount of authentication attempts across the domain. These should not be taken lightly, as locking out attacks causes a lack of availability. This can create an exceptionally impactful instance which can create a very unhappy paying customer!

![](img/181571ad74cba0e6a2f38fcd2658651e_228_0.png)

**FIGURE 7.22** Running the pySpray tool with LDAPspray to attempt a password spray against a list of users. This attack waits to send three authentication attempts every 11 minutes, as seen in the switches.

In the example of the screenshot above, we see that a user was identified with an easily guessed password. This was found after creating a list of likely passwords, identifying the domain's password policy, and then trimming down the potential passwords based on the information gathered. At this point, we can attempt to log into that user's account to identify if there's a way to pivot further within the environment.

## MULTICAST DNS POISONING

Windows machines have a few mechanisms to resolve hostnames with DNS, including fallback mechanisms to ask machines on the local network for help. What does this mean? If we can poison a request sent to the broadcast domain on our local subnet, we can convince a machine to connect to us. From there, we can capture password hashes for authentication, or even relay these connections to other machines (where we get access as the poisoned machine!).

### DNS Resolution Order

Windows DNS operates in a hierarchy, where the system needs to resolve a hostname to its applicable IP address to communicate to it on the Internet. Windows will operate<sup>11</sup> to resolve this address:

- 1. The client checks to see if the name is its own
- 2. HOSTS file (C:\Windows\System32\drivers\etc\hosts)
- 3. DNS Resolver Cache
- 4. Configured DNS
- 5. NetBIOS and Link Local Multicast Name Resolution (LLMNR)

### LLMNR

LLMNR is one of the primary focuses in multicast DNS poisoning, as Windows machines will request the broadcast address of the local subnet asking for help resolving a domain. Back in the day when this was established, internal networks were trusted to not have malicious actors. However, in today's world, internal networks can no longer be implicitly trusted and must always be considered as though an adversary may have access.

To exploit LLMNR, all we need to do is wait for an LLMNR request and then reply with the address of our system. Sounds easy enough right? But how do we actually achieve this?

### Responder

To exploit LLMNR on a local domain, the Responder tool can be leveraged to automatically identify and respond to LLMNR requests on the local subnet. These responses are sent with poisoned information in an attempt to convince the machine to connect to our machine. If properly poisoned, the victim will attempt to connect to our attack system and reveal credentials.

Poisoning LLMNR with responder is exceptionally effective in most networks, however, it is loud enough to cause alarms to be set off during detection. Each LLMNR, MDNS, and NBT-NS request that it sees will have a response sent which will be visible in the network traffic.

To run responder and reduce our chances of being detected, we can use the **-A** switch to analyze the traffic on the local subnet. When in Analyze mode, responder will not attempt to poison any requests and allows us to profile the network. It is highly recommended to run within analyze mode FIRST before running in active poisoning, as poisoning can reveal our location to others.

Beyond this, responder is also useful in catching or gathering credentials from systems based on various network services it impersonates. For example, we can run a fake LDAP server which can be used to catch credentials from a compromised printer. This is explored closely in [Chapter 2](#) about default credentials and can be applied in scenarios such as internal networks with responder.

### IPv6 MitM

While Responder is excellent at inviting NTLM connections from multicast DNS, we can leverage additional built-in and default preferences within Windows to attempt takeovers. One of these is the IPv6 preference that Windows has, where on a local network the IPv6 protocol will take precedence over IPv4. We can use this to our advantage by advertising malicious IPv6 information on the local subnet, convincing local machines to use our routes instead of the legitimate IPv4 ones. A tool to complete this action is **mitm6** from Dirk-jan Mollema, available at https://github.com/dirkjanm/mitm6.

This differs significantly from Responder, as Responder attempts to poison multicast DNS. With **mitm6**, we offer new DNS and route information to convince local hosts to use our host instead. This places us in the middle, which is why the tool is aptly called man-in-the-middle 6. We can run this tool by specifying the domains we want to respond to, narrowing them down to only specific internal domains. By selectively choosing domains, we can reduce the impact internally on the network if a user cannot reach certain resources.

To exploit this, we can use the commands below. This snippet is taken from the Game of Active Directory lab, (GOAD), which is a fully-fledged set of domains within a forest configured to be vulnerable. GOAD was created by Orange Cyberdefense and is available on GitHub at https://github.com/Orange-Cyberdefense/GOAD. The following mitm6 command attempts to takeover activity for the sevenkingdoms.local and essos.local domains:

```
mitm6 -i vboxnet0 -d sevenkingdoms.local -d essos.local
```

Remember, anytime we poison responses or attempt to perform man-in-the-middle techniques, there's always a risk that we can remove availability. To this end, mitm6 intelligently chooses to
