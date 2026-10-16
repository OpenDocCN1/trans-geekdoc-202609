
Given Windows’ ease of use, its enterprise Active Directory service, and the feature-rich .NET development platform, most organizations use the Microsoft platform for most of their networking and computing needs. Many businesses — especially small to medium-size ones — depend solely on the Windows OS for network use. Many large organizations run critical servers, such as web servers and database servers, on the Windows platform as well. If security vulnerabilities aren’t addressed and managed properly, they can bring a network or an entire organization (large or small) to its knees.

When Windows and other Microsoft software is attacked, especially by a widespread Internet-based worm or virus, hundreds of thousands of organizations and millions of computers are affected. Many well-known attacks against Windows can lead to the following problems:

*   Leaks of sensitive information, including files containing health-care information and credit-card numbers.

*   Passwords being cracked and used to carry out other attacks.

*   Systems taken down by denial of service (DoS) attacks.

*   Full remote control being obtained.

*   Entire databases being copied or deleted.

![remember](images/remember.png)When unsecured Windows-based systems are attacked, serious things can happen to a tremendous number of computers around the world.

## Choosing Tools

Hundreds of Windows hacking and testing tools are available. The key is finding a set of tools that can do what you need and that you’re comfortable using.

![technicalstuff](images/technicalstuff.png)Many security tools, including some of the tools described in this chapter, work only in certain versions of Windows. The most recent version of each tool in this chapter should be compatible with currently supported versions of Windows, but your mileage may vary.

![warning](images/warning.png)I’ve found that the more security tools and other power-user applications you install in Windows — especially programs that tie into the network drivers and TCP/IP stack — the more unstable Windows becomes. I’m talking about slow performance, general instability issues, and even the occasional Blue Screen of Death. Unfortunately, often the only fix is to reinstall Windows and all your applications. After years of rebuilding my testing systems every few months, I finally wised up and bought a copy of VMware Workstation and a dedicated computer that I can junk up with testing tools without worrying about all the software I install affecting my ability to get my other work done. (Ah, the memories of those DOS and Windows 3.*x* days, when things were so much simpler!)

### Free Microsoft tools

You can use the following free Microsoft tools to test your systems for various weaknesses:

*   **Built-in Windows programs** for NetBIOS and TCP/UDP service enumeration, such as these three: 

    *   `nbtstat` for gathering NetBIOS name-table information.

    *   `netstat` for displaying open ports on the local Windows system.

    *   `net` for running various network-based commands, including viewing shares on remote Windows systems and adding user accounts after you gain a remote command prompt via Metasploit.

*   **Microsoft Baseline Security Analyzer (MBSA)** ([`https://www.microsoft.com/en-us/download/details.aspx?id=7558`](https://www.microsoft.com/en-us/download/details.aspx?id=7558)) to test for missing patches and basic Windows security settings.

*   **Sysinternals** ([`https://docs.microsoft.com/en-us/sysinternals`](https://docs.microsoft.com/en-us/sysinternals)) to poke, prod, and monitor Windows services, processes, and resources both locally and over the network.

### All-in-one assessment tools

All-in-one tools perform a wide variety of security tests, including the following:

*   Port scanning.

*   OS fingerprinting.

*   Basic password cracking.

*   Detailed vulnerability mappings of the various security weaknesses that the tools find on your Windows systems.

I often use these tools in my work with very good results:

*   GFI LanGuard ([`https://www.gfi.com/products-and-solutions/network-security-solutions/gfi-languard3`](https://www.gfi.com/products-and-solutions/network-security-solutions/gfi-languard3))

*   Nexpose ([`https://www.rapid7.com/products/nexpose`](https://www.rapid7.com/products/nexpose))

### Task-specific tools

The following tools perform more specific tasks for uncovering Windows-related security flaws. These tools provide detailed insight into your Windows systems and provide information that you might not get from all-in-one assessment tools:

*   **Metasploit Framework and Metasploit Pro** ([`https://www.metasploit.com`](https://www.metasploit.com)) for exploiting vulnerabilities that such tools as Nessus and Nexpose discover to obtain remote command prompts, add users, set up remote backdoors, and do much more.

*   **NetScanTools Pro** ([`https://www.netscantools.com`](https://www.netscantools.com)) for port scanning, ping sweeping, and share enumeration.

*   **SoftPerfect Network Scanner** ([`https://www.softperfect.com/products/networkscanner`](https://www.softperfect.com/products/networkscanner)) for host discovery, port scanning, and share enumeration.

*   **TCPView** ([`https://docs.microsoft.com/en-us/sysinternals/downloads/tcpview`](https://docs.microsoft.com/en-us/sysinternals/downloads/tcpview)) to view TCP and UDP session information.

*   **Winfo** ([`www.ntsecurity.nu/toolbox/winfo`](http://www.ntsecurity.nu/toolbox/winfo)) for null-session enumeration to gather such configuration information as security policies, local user accounts, and shares.

Keep in mind that disabling the Windows Firewall (or other third-party firewall that’s running on your test system) can help speed your scans. The same is true for antivirus software — but be careful. If possible, run your security tests on a dedicated system or virtual machine, because doing so minimizes any effect your test results may have on the other work you do on your computer.

## Gathering Information About Your Windows Vulnerabilities

When you assess Windows vulnerabilities, start by scanning your computers to see what the bad guys can see.

![technicalstuff](images/technicalstuff.png)The exploits in this chapter were run against Windows systems from inside a firewall, on the internal network. Unless I point out otherwise, all the tests in this chapter can be run against all versions of the Windows OS. The attacks in this chapter are significant enough to warrant testing for, regardless of your current setup. Your results will vary from mine depending on the specific version of Windows, patch levels, and other system hardening you’ve done.

### System scanning

A few straightforward processes can identify weaknesses in Windows systems.

#### Testing

Start gathering information about your Windows systems by running an initial port scan, as follows:

1.  **Run basic scans to find which ports are open on each Windows system.**

    Scan for TCP ports with a port-scanning tool, such as NetScanTools Pro. The NetScanTools Pro results shown in [Figure 12-1](#c12.xhtml#c12-fig-0001) reveal several potentially vulnerable ports open on a Windows 10 system, including those for the ever-popular — and easily hacked — NetBIOS (TCP and UDP ports 139) and SQL Server Browser Service (UDP 1434).

2.  **Perform system enumeration (such as scanning for shares and versions of the Server Message Block, aka SMB, protocol) by using an all-in-one assessment tool (such as LanGuard) or a tool that does targeted work (such as NetScanTools SMB Scanner).**

    [Figure 12-2](#c12.xhtml#c12-fig-0002) shows a SMB Scanner scan that shows SMB version 1 running on a system, making it vulnerable to attacks such as those brought on by the WannaCry ransomware.
