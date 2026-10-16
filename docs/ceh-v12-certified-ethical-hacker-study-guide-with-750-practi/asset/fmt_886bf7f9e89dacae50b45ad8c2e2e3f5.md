
Unlike OpenVAS, Nessus doesn't give you a way to add notes to findings. One thing you do get, though, that you don't get in OpenVAS is an audit trail. You can search by plugin ID and by host and get additional details about the plugin that was run. As an example, searching for the plugin ID from the critical macOS out‑of‑date finding shows the IP addresses for hosts where Nessus couldn't identify the OS, hosts where Nessus did identify the OS but it wasn't macOS, and also IP addresses where the operating system was correct but the version number wasn't correct, meaning there was no finding resulting from the run of the plugin.

Like OpenVAS, Nessus uses Network Attack Scripting Language (NASL) scripts. They are stored with the rest of the Nessus installation. On Windows, the installation would be in the Program Files directory. On Linux, the files are stored in `/opt/nessus` with the plugins in `/opt/nessus/lib/plugins`. If you want to see exactly what a plugin does so you can verify the finding, you should check the script. You can use the plugin ID to identify the file that is run for that plugin. The scripts, once you get used to reading them, will provide you with the details on how to replicate the vulnerability test so you can verify. This verification is not only important to rule out false positives, but if it is actually a vulnerability, you will need to have documentation to present to the company or organization you are working with.

Vulnerability scanning is just a stage in the testing. It is not the end. Vulnerabilities should always be verified. Additionally, if you are expected to identify as many vulnerabilities as you can, you will need to move to exploiting these vulnerabilities in hopes of identifying more. While this may require the use of exploit tools like Metasploit or even tools that are custom‑developed, it could be that you need to create a packet that looks a particular way. No matter what the findings are, though, they need to be verified before being presented as findings.

### Looking for Vulnerabilities with Metasploit

Metasploit is a versatile tool. Certainly, you can use it for exploiting applications as well as the port scanning we did earlier. As it's a framework and there are a lot of modules, it shouldn't come as a big surprise that there are lots of vulnerability scanners. One example is a scanner module for the Eternal Blue vulnerability. This is a vulnerability in the implementation of the Server Message Block (SMB) protocol that was discovered by the National Security Agency (NSA), which developed an exploit for it, which was released without the NSA's approval by a group called the Shadow Brokers. The following is one of the vulnerability scanners that looks for systems vulnerable to the Eternal Blue exploit. While the fix for this vulnerability has been out for years at this point, there are still many systems in production that are vulnerable to it.

```
msf6 auxiliary(scanner/portscan/syn)> use auxiliary/scanner/smb/smb_ms17_010
msf6 auxiliary(scanner/smb/smb_ms17_010)> set RHOSTS 192.168.4.0/24
RHOSTS => 192.168.4.0/24
msf6 auxiliary(scanner/smb/smb_ms17_010)> run
 
[-] 192.168.4.10:445 - Host does NOT appear vulnerable.
[-] 192.168.4.15:445 - Host does NOT appear vulnerable.
[*] 192.168.4.0/24:445 - Scanned 26 of 256 hosts (10% complete)
```

There are a large number of scanners available in Metasploit. Not all the scanners are directly related to the vulnerabilities. Searching for the word *scanner* in Metasploit returned 619 results, with some of the output following. In just the output fragment here, you can see that some of them are related to known vulnerabilities while some are looking for instances of applications that may have a particular configuration issue.

```
   192  auxiliary/scanner/http/manageengine_deviceexpert_user_creds              2014-08-28       normal  No     ManageEngine DeviceExpert User Credentials
   193  auxiliary/scanner/http/manageengine_securitymanager_traversal            2012-10-19       normal  No     ManageEngine SecurityManager Plus 5.5 Directory Traversal
   194  auxiliary/scanner/http/mediawiki_svg_fileaccess                                           normal  No     MediaWiki SVG XML Entity Expansion Remote File Access
   195  auxiliary/scanner/http/meteocontrol_weblog_extractadmin                                   normal  No     Meteocontrol WEBlog Password Extractor
   196  auxiliary/scanner/http/mod_negotiation_brute                                              normal  No     Apache HTTPD mod_negotiation Filename Bruter
   197  auxiliary/scanner/http/mod_negotiation_scanner                                            normal  No     Apache HTTPD mod_negotiation Scanner
   198  auxiliary/scanner/http/ms09_020_webdav_unicode_bypass                                     normal  No     MS09-020 IIS6 WebDAV Unicode Authentication Bypass
   199  auxiliary/scanner/http/ms15_034_http_sys_memory_dump                                      normal  Yes    MS15-034 HTTP Protocol Stack Request Handling HTTP.SYS Memory Information Disclosure
```

It's not the most comprehensive vulnerability scanner, but if you are already in Metasploit for other purposes, you can make use of vulnerability scan modules to look in a targeted way for some vulnerabilities. If you have a good way to detect a vulnerability and feel like writing a little Ruby, you can write a module for Metasploit that can look for that vulnerability.

## Packet Crafting and Manipulation

When you are sending data out over the network, there is a clear path it follows before exiting the network interface on your system. We've gone over this, to a degree, by talking about the Open Systems Interconnection (OSI) model. Let's say that you are visiting a web page. You enter a URL into the address bar. Your browser takes the input and creates the HTTP request headers that are needed to send to the server. For simplicity, we'll skip the encryption pieces and just talk about how the complete packet is put together.

The application makes a request of the operating system to open a connection to the server. This triggers the operating system to build a packet using information provided by the application. This includes the hostname or IP address as well as the port number. Unless otherwise provided, the port number will default to either 80 or 443, depending on whether the communication is HTTPS or HTTP. This information will allow the operating system to create the necessary headers for both TCP and IP, layers 4 and 3.

All of this is to say that the application initiates requests based on interaction from the user. It follows a clear path, and the information placed into the necessary headers for each protocol is coherent and easily traced back to the original source of the information. Sometimes, though, you may need to send data that doesn't follow a coherent path. It could be that you need to manipulate headers with data that wouldn't normally be found in the header fields. Each header field is a known size and is binary, which means you aren't going to be sending a character instead of a number, for instance. Nothing in the network headers, looking at layers 4 and below, for sure, is data that would go through an ASCII decode to be converted to character data.
