# Attacking Windows Server 2008 R2

You may wonder, why do we address such an old server operating system? Particularly with servers, older operating systems are quite common.

This exploit is supposed to affect Windows Server 2008 R2, though I found it to have intermittent success. The exploit, illustrated in Figure 14-15, is **exploit/windows/local/ms14_058_track_popup_menu**.

![](bbox=[0.07, 0.26, 0.68, 0.5])

This exploit is based on a vulnerability in win32k.sys that involves NULL pointer dereferencing. It is used in the TrackPopupMenu API call, and under some circumstances can be used to execute code. The authors of this exploit claim it has been successfully executed on Windows Server 2003 SP2, Windows 2008 R2, as well as Windows 7. You can get more details on this attack at https://www.rapid7.com/db/modules/exploit/windows/local/ms14_058_track_popup_menu.

# Attacking Windows via Office

This particular exploit is claimed to work on Windows Vista, Windows 8, Server 2008, and Server 2012, if the Windows OS is running Office 2010 or 2013. The exploit, illustrated in Figure 14-16, is **exploit/windows/fileformat/ms14_060_sandworm**.

# Attacking Linux

Windows is not the only operating system you can attack with Metasploit. This exploit attacks Linux. It is based on a Linux kernel flaw. Use **exploit/linux/local/sock_sendpage** as demonstrated in Figure 14-17. For test purposes, Metasploit offers a Metasploitable Linux virtual machine you can download free of charge from https://information.rapid7.com/metasploitable-download.html.