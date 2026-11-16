You'll notice that only one of the systems shows headers, and out of those headers, there isn't a server type. The same server suggests that there is a redirect to a login page. Running the same scan with nmap returns server types. masscan doesn't have the same capabilities as nmap, including a lack of support for additional scan types, such as the unexpected TCP scans like XMAS, FIN, and ACK. It also doesn't support UDP scans. However, if you want all that functionality, you can use nmap. It's free and more than capable for those sorts of scans. What masscan gets you is the ability to indicate what rate you want to scan at and the ability to perform very fast scans.

# MegaPing

We've looked at MegaPing before for its capability to perform ping sweeps. As noted earlier, MegaPing has a number of capabilities, including the ability to run port scans. These are not just run-of-the-mill scans, however. You'll remember that nmap scans about 1,000 ports by default. These are commonly used ports. You can certainly select other ports if you want. One thing MegaPing provides us with that we don't get with nmap is some preselected port collections. You can see the drop-down in Figure 5.5 that provides you with different selections for ports. One of these is Hostile Ports, which are ports that are commonly misused as well as ports that may commonly be used by Trojan horse programs and other malicious software (malware). At the bottom, you will see the list of ports that are included in the scan type.

# FIGURE 5.5 MegaPing scan types

![](bbox=[0.19, 0.53, 0.82, 0.91])