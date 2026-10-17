Another major advantage of SOCKS proxies is that they can be used to pivot around inside of an internal environment. If a DMZ asset is compromised, the compromised server is likely able to communicate directly with other internal servers on the network. By establishing a SOCKS proxy on the DMZ host, an attacker can tunnel their requests from their machine directly to the internal network for additional reconnaissance.

![](bbox=[0.105, 0.194, 0.897, 0.414])

**FIGURE 4.19** Using a DMZ server as a SOCKS proxy to gain access to internal hosts on a secure network.

# ProxyChains

Some programs can natively support using SOCKS proxies to redirect their traffic, while others do not have that support built in. The tool **proxychains** can force non-proxy aware programs to utilize a specific proxy, or chain of proxies, to effectively hide their origination point.^3^

Keep in mind that while SOCKS proxies are an effective way to pivot and gain access to internal resources, they are not well suited for heavy scanning reconnaissance. Light scanning and web-recon (such as browsing for internal services with Burp) are an effective way to use this technology. For more in-depth and wide scans, either use Live-off-the-Land binaries on the existing host or route the traffic through the host using something similar to Metasploit’s Meterpreter route functionality^4^.

To use the proxychains tool, we must create a configuration file for the **proxychains** program to read. By default, the program searches for the configuration file named **proxychains.conf** in the following order:

```
file listed in environment variable PROXYCHAINS_CONF_FILE or provided as
a -f argument to proxychains script or binary.
./proxychains.conf
$(HOME)/.proxychains/proxychains.conf
/etc/proxychains.conf
/etc/proxychains4.conf
```

What this means is that the program will look for the **proxychains.conf** file and utilize the first configuration that it locates. A copy of a sample configuration file is located at **/etc/proxychains4.conf** and can be copied to one of the locations above, and then edited for our configuration purpose.

Proxychains supports many ways to utilize the proxies as well, where the proxies can be accessed through a chain one after another to further obfuscate where the activity originated from. Additionally, the proxies can be accessed in a randomized order with a type of configuration. **Dynamic chains** are used to access the proxies in the configuration file in the order they are listed, skipping any proxies that are listed as down or unreachable. **Strict chains** are connections