
minimums). The easiest option to run the T-Pot honeypot is to download the ISO image or build your own and then mount it to a virtual CD in VMware or VirtualBox and launch the machine. The ISO is a 64-bit Ubuntu build, as shown next. Again, be sure to establish the minimum settings just given. For limited testing, you can get by with a smaller (5GB) hard drive.

![](img/5f597c6a70133069118d9e804ace3775_595_0.png)

Press ENTER to select the default installer (T-Pot 17.10). You will be prompted to select your language and keyboard. The installation will then begin and will take 20–30 minutes, depending on your system resources. Along the way, you will also be asked some configuration questions, such as type of honeypot (we selected Standard for this lab), password for the tsec user account, and a second username and password for the web interface (do not lose that). When finished, you will be prompted to log in. Use the tsec account and first password you supplied. On the login screen, you will see the IP of the honeypot and web URL, as shown next. Use the second user account you established and password for the web interface.

![](img/5f597c6a70133069118d9e804ace3775_595_1.png)

From another Linux or Mac system, scan the IP with Nmap. Next, open the web interface, using the preceding IP (https://IP:64297), and select the T-Pot dashboard. You will need to place your honeypot on a public Internet connection and/or scan it to see some activity in the dashboards. However, the following screenshot shows the potential of this tool.

![](img/5f597c6a70133069118d9e804ace3775_596_0.png)

NOTE The following two images were used with permission of the developer of the latest version of T-Pot and may have changed in format or functionality by the time of this book’s publication.

![](img/5f597c6a70133069118d9e804ace3775_596_1.png)

Scroll down to see further details.

![](img/5f597c6a70133069118d9e804ace3775_597_0.png)

The web interface has several tools, including an Elasticsearch head (starting point for searches), shown here.

![](img/5f597c6a70133069118d9e804ace3775_597_1.png)

Another tool is the SpiderFoot search page, which allows you to find out information about attackers.

## New Scan

| Scan Name | Google |
|---|---|
| Seed Target | google.com |
| By Use Case | All |
| By Required Data | All |
| By Module | All |
| Details | Get anything and everything about the target. All SpiderFoot modules will be enabled (slow) but every possible piece of information about the target will be obtained and analysed. |

Also, the web interface includes a Docker container UI, called Portainer, that allows you to control the Docker containers (for example, Dionaea, shown here).

![](img/5f597c6a70133069118d9e804ace3775_598_0.png)

You may also interact by shell with each container, as shown next.

![](img/5f597c6a70133069118d9e804ace3775_599_0.png)

Also, a Netdata page shows vital server information, which seemingly scrolls down endlessly.

![](img/5f597c6a70133069118d9e804ace3775_599_1.png)

Finally, if needed, you have full access to the web console via Wetty, shown next. For nonlocal access, you will need to upload your SSH keys.

```
Not Secure | https://192.168.0.139:64297/tpotweb.html
The authenticity of host '[127.0.0.1]:64295 ([127.0.0.1]:64295)' can't be established.
ECDSA key fingerprint is SHA256:uh6PSTMybP4F+uJishnmJgQfIX2Q6f3kRLy8Jjhn4Z0.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '[127.0.0.1]:64295' (ECDSA) to the list of known hosts.
tsec@127.0.0.1's password:
Welcome to Ubuntu 16.04.3 LTS (GNU/Linux 4.4.0-92-generic x86_64)

* Documentation:  https://help.ubuntu.com
* Management:     https://landscape.canonical.com
* Support:        https://ubuntu.com/advantage

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

[tsec@agreeablespray:~]$
```

All data is stored in the /data folder, which is accessible from the host.

```
Not Secure | https://192.168.0.139:64297/wetty/ssh/tsec
tsec@127.0.0.1's password:
Welcome to Ubuntu 16.04.3 LTS (GNU/Linux 4.4.0-92-generic x86_64)

* Documentation:  https://help.ubuntu.com
* Management:     https://landscape.canonical.com
* Support:        https://ubuntu.com/advantage
Last login: Sun Aug 20 19:28:37 2017 from 127.0.0.1
[tsec@agreeablespray:~]$ sudo bash
[sudo] password for tsec:
[root@agreeablespray:~]# ls /data/dionaea/bitstreams/2017-08-20/
ftpd-21-::ffff:192.168.0.117-XacM7c  mysqld-3306-::ffff:192.168.0.117-BE4jqi
[root@agreeablespray:~]#
```

![](img/5f597c6a70133069118d9e804ace3775_600_0.png)

NOTE To run this honeypot on a cloud-based Ubuntu 16.04 system, simply run the following commands. You will also need to open TCP ports 0–64000 to the public and 64001 and above to your IP (see the T-Pot website link at end of this chapter if you want to be more selective in what ports you expose).

```
git clone https://github.com/dtag-dev-sec/t-pot-autoinstall.git
cd t-pot-autoinstall/
sudo su
./install.sh
```

## Commercial Alternative: TrapX

When it comes to commercial solutions, you have several to choose from, including these:

- TrapX
- Attivo
- Illusive Networks
- Cymmetria

Each one has its merits and deserves a trial. However, in this chapter, we highlight only one: TrapX DeceptionGrid. TrapX was highlighted in the last edition of this book and was impressive then. Yet it has improved greatly since that time.

When logging into TrapX, you will be presented with a dashboard displaying various forms of data, including inbound and outbound threats, top-10 events, threat statistics, and the health status of workstation, server, and network decoy traps.

| Company | Risk Level | Type | # Of Events |
|---|---|---|---|
| ABC Motors | • | Outbound, Internal | 115 |
| Gotham Financial | • | Outbound, Internal | 109 |
| Wayne Enterprises | • | Outbound, Internal | 143 |
| Tyrell Corp | • | Outbound, Internal | 107 |

| Source IP | Attacks | Destination IP | Attacks |
|---|---|---|---|
| 10.0.0.155 | 112 | 10.0.0.17 | 96 |
| 10.0.0.223 | 32 | 66.228.39.114 | 92 |
| 10.0.0.247 | 29 | 10.0.0.18 | 64 |
| 10.0.0.241 | 26 | 10.0.0.15 | 62 |
| 10.0.0.7 | 25 | 10.0.0.16 | 47 |
| 10.0.0.249 | 24 | 45.63.6.180 | 20 |
| 10.0.0.18 | 23 | 8.8.8.8 | 16 |
| 10.0.0.17 | 19 | 10.20.30.101 | 12 |
| 10.0.0.16 | 18 | 10.20.30.100 | 11 |
| 10.0.0.15 | 17 | 10.20.30.106 | 9 |

- Workstation Traps
- Server Traps
- Networking Traps
- Industrial Traps
- Medical Devices Traps

| Statistic | Value |
|---|---|
| Trap events | 18 |
| Network Intelligence Events | 462 |
| Infection | 6 |
| Interaction | 2 |
| Reconnaissance | 2 |
| Connection | 8 |
| BotNet & CC | 36 |
| Malware & Trojan | 92 |
| Intelligence Gathering | 334 |

When displaying events using the Event Analysis screen, shown next, you may filter events (for example, you might filter on infections).

| ID | Svr | Type | Attacker hostname | Attacker IP | Trap name | Protocol | Port | Proxy | Start | Duration |
|---|---|---|---|---|---|---|---|---|---|---|
| 26218204 | ⏺ | Infection | 10.0.0.162 | 10.0.0.162 | GothamFinancial3_MT | SMB | 445 | | 29.06.2017 14:49:57 | 03:00 min |
| 26218190 | ⏺ | Infection | 10.0.0.162 | 10.0.0.162 | GothamFinancial3_MT | SMB | 445 | | 29.06.2017 09:59:49 | 02:59 min |
| 26218174 | ⏺ | Infection | 10.0.0.162 | 10.0.0.162 | GothamFinancial3_MT | SMB | 445 | | 28.06.2017 09:59:44 | 02:59 min |
| 26218163 | ⏺ | Infection | 10.0.0.162 | 10.0.0.162 | GothamFinancial3_MT | SMB | 445 | | 27.06.2017 09:59:40 | 03:00 min |
| 26218150 | ⏺ | Infection | 10.0.0.162 | 10.0.0.162 | GothamFinancial3_MT | SMB | 445 | | 26.06.2017 10:00:25 | 03:00 min |
| 26218135 | ⏺ | Infection | 10.0.0.162 | 10.0.0.162 | GothamFinancial3_MT | SMB | 445 | | 25.06.2017 09:59:43 | 03:00 min |
| 26218122 | ⏺ | Infection | 10.0.0.162 | 10.0.0.162 | GothamFinancial3_MT | SMB | 445 | | 24.06.2017 09:59:47 | 03:00 min |
| 26218110 | ⏺ | Infection | 10.0.0.162 | 10.0.0.162 | GothamFinancial3_MT | SMB | 445 | | 23.06.2017 09:59:41 | 03:00 min |
| 26218095 | ⏺ | Infection | 10.0.0.162 | 10.0.0.162 | GothamFinancial3_MT | SMB | 445 | | 22.06.2017 09:59:42 | 03:00 min |
| 26218083 | ⏺ | Infection | 10.0.0.162 | 10.0.0.162 | GothamFinancial3_MT | SMB | 445 | | 21.06.2017 09:59:41 | 02:59 min |
| 26218070 | ⏺ | Infection | 10.0.0.162 | 10.0.0.162 | GothamFinancial3_MT | SMB | 445 | | 20.06.2017 09:59:41 | 02:59 min |
| 26218059 | ⏺ | Infection | 10.0.0.162 | 10.0.0.162 | GothamFinancial3_MT | SMB | 445 | | 19.06.2017 09:59:40 | 03:00 min |
| 26218040 | ⏺ | Infection | 10.0.0.173 | 10.0.0.173 | GothamFinancial3_MT | SMB | 445 | | 17.05.2017 09:59:36 | 02:59 min |
| 26218036 | ⏺ | Infection | 10.0.0.166 | 10.0.0.166 | AbcMotors5_MT | SMB | 445 | | 17.05.2017 02:59:36 | 03:00 min |
| 26218025 | ⏺ | Infection | 10.0.0.173 | 10.0.0.173 | GothamFinancial3_MT | SMB | 445 | | 16.05.2017 09:59:36 | 03:00 min |
| 26218017 | ⏺ | Infection | 10.0.0.166 | 10.0.0.166 | AbcMotors5_MT | SMB | 445 | | 16.05.2017 02:59:39 | 03:00 min |
| 26218006 | ⏺ | Infection | 10.0.0.173 | 10.0.0.173 | GothamFinancial3_MT | SMB | 445 | | 15.05.2017 09:59:38 | 02:59 min |
| 26218001 | ⏺ | Infection | 10.0.0.166 | 10.0.0.166 | AbcMotors5_MT | SMB | 445 | | 15.05.2017 02:59:38 | 03:00 min |

In order to inspect an event, simply double-click it to see all recorded actions in a kill chain view, as shown here.
