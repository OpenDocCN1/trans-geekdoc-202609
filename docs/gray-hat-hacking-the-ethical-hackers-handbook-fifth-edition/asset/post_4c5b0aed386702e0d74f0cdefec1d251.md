
```bash
root@kali:~/DAP-1320# apt-get install git build-essential zlib1g-dev \
> liblzma-dev python-magic
<truncated for brevity>
After this operation, 111 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
<truncated for brevity>
root@kali:~/DAP-1320# git clone https://github.com/rampageX/firmware-mod-kit.git
<truncated for brevity>
root@kali:~/DAP-1320# export PATH=$PATH:/root/DAP-1320/firmware-mod-kit
root@kali:~/DAP-1320# extract-firmware.sh DAP1320_fw_1_11b10.bin
Firmware Mod Kit (extract) 0.99, (c)2011-2013 Craig Heffner, Jeremy Collake
Scanning firmware...
Scan Time: 2017-12-05 17:10:39
Target File: /root/DAP-1320/DAP1320_fw_1_11b10.bin
MD5 Checksum: 3d13558425d1147654e8801a99605ce6
Signatures: 344
DECIMAL HEXADECIMAL DESCRIPTION
--------------------------------------------------------------------------------
0 0x0 uImage header, header size: 64 bytes, header CRC: 0x71C7BA94, created: 2013-09-16 08:50:53, image size: 799894 bytes, Data Address: 0x80002000, Entry Point: 0x801AB9F0, data CRC: 0xA62B902, OS: Linux, CPU: MIPS,
image type: OS Kernel Image, compression type: lzma, image name: "Linux Kernel
Image"
64 0x40 LZMA compressed data, properties: 0x5D, dictionary
size: 8388608 bytes, uncompressed size: 2303956 bytes
851968 0xD0000 Squashfs filesystem, little endian, version 4.0,
compression:lzma, size: 2774325 bytes, 589 inodes, blocksize: 65536 bytes,
created: 2013-09-16 08:51:15
Extracting 851968 bytes of uimage header image at offset 0
Extracting squashfs file system at offset 851968
Extracting 544 byte footer from offset 5438942
Extracting squashfs files...
Firmware extraction successful!
Firmware parts can be found in '/root/DAP-1320/fmk/*'
root@kali:~/DAP-1320# ls fmk
image_parts logs rootfs
root@kali:~/DAP-1320# ls fmk/rootfs
bin dev etc lib linuxrc proc sbin share sys tmp usr var www
root@kali:~/DAP-1320# ls fmk/rootfs/bin
ash cli ethreg ln mount ps touch
busybox cp fgrep login mv rm udhcpc
busybox_161 date gpio_event ls netbios_checker sed umount
cat dd grep md nvram sh uname
cgi echo hostname mkdir ping sleep xmlwf
chmod egrep kill mm ping6 ssi
root@kali:~/DAP-1320# file fmk/rootfs/bin/busybox
busybox: ELF 32-bit MSB executable, MIPS, MIPS32 rel2 version 1 (SYSV),
dynamically linked, interpreter /lib/ld-uClibc.so.0, corrupted section header
size
```

Now that the update package has been extracted, it is time to browse the files, looking for features, configurations, or unknown applications. Table 24-1 defines some items to look for while browsing.

| Purpose | BASH Command Examples |
|---|---|
| Locate executable files (note: non-Busybox files). | `find . -type f -perm /u+x` |
| Determine the directory structure for future analysis. | `find . -type d` |
| Find web servers or associated technologies. | `find . -type f -perm /u+x -name "*httpd*" -o -name "*cgi*" -o -name "*nginx*"` |
| Find library versions. | `for i in \`find . -type d -name lib\`;do find $i -type f;done` |
| Find HTML, JavaScript, CGI, and config files. | `find . -name "*.htm*" -o -name "*.js" -o -name "*.cgi" -o -name "*.conf"` |
| Look for an executable version (for example, with lighttpd) | `strings sbin/lighttpd | grep lighttpd` |

Table 24-1 Examples of Interrogating the File System

![](img/5f597c6a70133069118d9e804ace3775_662_0.png)

**NOTE** Any executable or library found that has a version needs to be cross-checked against known vulnerabilities. For example, use a Google search of <name> <version number> vulnerability.

Once you've collected all this information, you will want to understand what is processing requests from the browser or any services running. Because I've already done all the preceding steps, I reduced the following example in order to make the analysis more condensed and straightforward. The web server was found to be lighttpd, which uses lighttpd*.conf and modules.conf for the configuration. Furthermore, it uses cgi.conf, which points almost all handling to /bin/ssi (a binary executable).

```bash
root@kali:~/DAP-1320/fmk/rootfs# find . -type f -perm /u+x -name "*httpd*" -o
-name "*cgi*" -o -name "*nginx*"
<truncated for brevity>
./sbin/lighttpd
./sbin/lighttpd-angel
./etc/conf.d/cgi.conf
./bin/cgi
root@kali:~/DAP-1320/fmk/rootfs# find . -name *.conf
./etc/lighttpd.conf
./etc/conf.d/mime.conf
./etc/conf.d/cgi.conf
./etc/conf.d/auth_base.conf
./etc/conf.d/expire.conf
./etc/conf.d/auth.conf
./etc/conf.d/dirlisting.conf
./etc/conf.d/graph_auth.conf
./etc/conf.d/access_log.conf
./etc/modules.conf
./etc/host.conf
./etc/resolv.conf
./etc/lighttpd_base.conf
root@kali:~/DAP-1320/fmk/rootfs# cat etc/lighttpd_base.conf
###############################################################################
## /etc/lighttpd/lighttpd.conf
## check /etc/lighttpd/conf.d/*.conf for the configuration of modules.
```

```text
######################
<truncated>
# Load the modules.
include "modules.conf"
<truncated>
root@kali:~/DAP-1320/fmk/rootfs# cat etc/modules.conf
######################
```

```text
######################
# Modules to load
<truncated>
include "conf.d/cgi.conf"
root@kali:~/DAP-1320/fmk/rootfs# cat etc/conf.d/cgi.conf
######################
```

```text
######################
# CGI modules
#
# -------------------
#
# http://www.lighttpd.net/documentation/cgi.html
##
server.modules += ( "mod_cgi" )
```

```text
# Plain old CGI handling
# For PHP don't forget to set cgi.fix_pathinfo = 1 in the php.ini.
##
cgi.assign
= (
".htm" => "/bin/ssi",
".public.js" => "/bin/ssi",
".xml" => "/bin/ssi"
"save_configure.cgi" => "/bin/sh",
"hnap.cgi" => "/bin/sh",
"tr069.cgi" => "/bin/sh",
"widget.cgi" => "/bin/sh",
".cgi" => "/bin/ssi",
".html" => "/bin/ssi",
".txt" => "/bin/ssi"
)
```

At this point, we have an idea of how to proceed and will begin our vulnerability analysis.

## Lab 24-2: Performing Vulnerability Analysis

At this point, vulnerability analysis is not much different from what has been taught in previous chapters. Command-injection, format-string, buffer-overflow, use-after-free, misconfiguration, and many more vulnerabilities can be searched for. In this case, we will use a technique to find command-injection-type vulnerabilities in executables. Since /bin/ssi is a binary, we will look for format strings that use %s (for string) and then redirect the output to /dev/null (meaning we don’t care about the output). This pattern is interesting because it may indicate a sprintf function that’s creating a command, with a potentially user-controlled variable, to use with popen or system. For example, a command to see if another host is alive might be created as follows:

```text
sprintf(cmd, "ping -q -c 1 %s > /dev/null", variable)
```

If the variable is controlled by the attacker and not sanitized, and the cmd is used to execute in a shell, the attacker can inject their command into the intended command. In this case, we have two interesting strings that appear to download a file:

```bash
root@kali:~/DAP-1320/fmk/rootfs# strings bin/ssi | grep "%s" | grep "/dev/null"
wget -P /tmp/ %s > /dev/null
wget %s -O %s >/dev/null &
```

Armed with these two strings, we will begin to do some reversing of the binary to see if we have control over the variable, URL. IDA Pro will be our tool of choice for this exercise.

The main objective of the IDA Pro analysis is to determine whether the string is used in a way that the attacker has a chance to alter it. After opening the ssi binary in IDA Pro and ensuring that the processor is set to MIPS, we then take the following steps:

- 1. Search for the string of interest.
- 2. Determine how the string is used.
- 3. Determine where the URL comes from (if it is hardcoded, we are not interested in it).

Press ALT-T to bring up the text search screen and then select Find All Occurrences for the string, as shown next.

![](img/5f597c6a70133069118d9e804ace3775_665_0.png)

We find only two occurrences of the string; one is the static format string and the other is a reference to the static string, as shown next. (Note that you can ignore the function name; it was not there during the initial analysis but rather was added by the author.)

| Address | Function | Instruction |
|---|---|---|
| LOAD:00409010 | download_fw_and_lp | la $a1, aWgetPTmpSDevNu # "wget -P /tmp/ %s > /... |
| LOAD:00428458 | | aWgetPTmpSDevNu:.ascii "wget -P /tmp/ %s > /dev/null"<0> |

By double-clicking on the highlighted result, we are taken to that instruction in the
