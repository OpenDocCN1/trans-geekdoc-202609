
Check for New Firmware button, we now see that there is a 1.12 version available to download.

![](img/5f597c6a70133069118d9e804ace3775_671_0.png)

Prior to clicking the Upgrade Firmware button, we need to set up our ping to monitor the device. When we click the Upgrade Firmware button, we should see the following download progress box:

![](img/5f597c6a70133069118d9e804ace3775_672_0.png)

```
root@kali:~/DAP-1320# ping 192.168.1.173
64 bytes from 192.168.1.173: icmp_seq=56 ttl=64 time=2.07 ms
64 bytes from 192.168.1.173: icmp_seq=57 ttl=64 time=2.20 ms
64 bytes from 192.168.0.63: icmp_seq=58 ttl=64 time=3.00 ms
①From 192.168.1.173 icmp_seq=110 Destination Host Unreachable
From 192.168.1.173 icmp_seq=111 Destination Host Unreachable
From 192.168.1.173 icmp_seq=112 Destination Host Unreachable
From 192.168.1.173 icmp_seq=113 Destination Host Unreachable
From 192.168.1.173 icmp_seq=114 Destination Host Unreachable
From 192.168.1.173 icmp_seq=115 Destination Host Unreachable
From 192.168.1.173 icmp_seq=116 Destination Host Unreachable
From 192.168.1.173 icmp_seq=117 Destination Host Unreachable
From 192.168.1.173 icmp_seq=118 Destination Host Unreachable
From 192.168.1.173 icmp_seq=119 Destination Host Unreachable
From 192.168.1.173 icmp_seq=120 Destination Host Unreachable
From 192.168.1.173 icmp_seq=121 Destination Host Unreachable
②64 bytes from 192.168.1.173: icmp_seq=122 ttl=64 time=1262 ms
64 bytes from 192.168.1.173: icmp_seq=123 ttl=64 time=239 ms
64 bytes from 192.168.1.173: icmp_seq=124 ttl=64 time=2.00 ms
```

You will notice that the host becomes nonresponsive ① and later comes back online ②. This indicates that the box was rebooted. At this point, we’ve proven that we can inject a command into the upgrade URL and the device will execute it. Without uploading an executable to the device, you are limited by what is on the device. For example, as previously explained, if telnetd is compiled into the Busybox (it is not on this system), you can just start it to access the shell without a password, as follows:

```
telnetd -l /bin/sh
```

This approach is demonstrated in the next section. If needed, you could cross-compile a binary such as netcat for this processor and then upload it via tftp or tfcp, as Craig Heffner has demonstrated, 2 or you could use another method.

## Dynamic Analysis with Emulation

It turns out, in some cases, not to be necessary to have hardware in hand to perform vulnerability analysis and exploit firmware.

### FIRMADYNE

The FIRMADYNE 3 tool allows for the emulation of firmware by using the QEMU hypervisor. The beauty of this approach is that you do not have to buy the hardware to test the firmware. This powerful approach allows for scaled testing in parallel. Dominic Chen downloaded and tested more than 23,000 specimens of firmware and was able to successfully run about 9,400 of them (approximately 40 percent), 4 which is not bad at all. In the following labs, we will set up and execute FIRMADYNE.

#### Lab 24-3: Setting Up FIRMADYNE

If you want to follow along in this lab, we will be using Ubuntu 16.04.3 server, running in VMware or VirtualBox, with NAT network settings, only OpenSSH installed, with a username of firmadyne. First, we need to set up the FIRMADYNE tool by using the instructions found on the FIRMADYNE GitHub (see the “For Further Reading” section at the end of this chapter):

```
firmadyne@ubuntu:~$ sudo apt-get update
<output skipped throughout this lab for brevity>
firmadyne@ubuntu:~$ sudo apt-get install busybox-static fakeroot git kpartx \
> netcat-openbsd nmap python-psycopg2 python3-psycopg2 snmp uml-utilities \
> util-linux vlan
firmadyne@ubuntu:~$ git clone --recursive \
> https://github.com/firmadyne/firmadyne.git
firmadyne@ubuntu:~$ git clone https://github.com/devttys0/binwalk.git
Cloning into 'binwalk'...
remote: Counting objects: 7413, done.
remote: Compressing objects: 100% (22/22), done.
remote: Total 7413 (delta 6), reused 15 (delta 3), pack-reused 7387
Receiving objects: 100% (7413/7413), 43.68 MiB | 3.62 MiB/s, done.
Resolving deltas: 100% (4265/4265), done.
Checking connectivity... done.
firmadyne@ubuntu:~$ cd binwalk/
firmadyne@ubuntu:~$ sudo ./deps.sh
<output skipped for brevity>
Continue [y/N]? y
<output skipped for brevity>
firmadyne@ubuntu:~/binwalk$ sudo python ./setup.py install
firmadyne@ubuntu:~/binwalk$ sudo apt-get install python-lzma
firmadyne@ubuntu:~/binwalk$ sudo -H pip install \
> git+https://github.com/ahupp/python-magic
firmadyne@ubuntu:~/binwalk$ sudo -H pip install \
> git+https://github.com/sviehb/jefferson .
firmadyne@ubuntu:~/firmadyne$ git clone https://github.com/firmadyne/sasquatch.git
firmadyne@ubuntu:~/firmadyne$ cd sasquatch/; make; sudo make install
```

Next, install the PostgreSQL database:

```
firmadyne@ubuntu:~$ sudo apt-get install postgresql
```

Then, set up user firmadyne with the password “firmadyne” (when prompted):

```
firmadyne@ubuntu:~$ sudo -u postgres createuser -P firmadyne
Enter password for new role:
Enter it again:
```

Now, create the database and initialize it. Notice firmware is appended to the end of the next command:

```
firmadyne@ubuntu:~$ sudo -u postgres createdb -O firmadyne firmware
firmadyne@ubuntu:~$ sudo -u postgres psql -d firmware < \
> ./firmadyne/database/schema
CREATE TABLE
ALTER TABLE
CREATE SEQUENCE
ALTER TABLE
<output skipped for brevity>
```

Download the pre-built binaries for FIRMADYNE (or build binaries using instructions on the FIRMADYNE GitHub):

```
firmadyne@ubuntu:~$ cd ~
firmadyne@ubuntu:~$ cd ./firmadyne; ./download.sh
Downloading binaries...
Downloading kernel 2.6.32 (MIPS)...
--2017-11-26 20:15:27--  https://github.com/firmadyne/kernel-
v2.6.32/releases/download/v1.0/vmlinux.mipsel
Resolving github.com (github.com)... 192.30.253.113, 192.30.253.112,
192.30.253.113
Connecting to github.com (github.com)|192.30.253.113|:443... connected.
<output skipped for brevity>
```

Now install QEMU:

```
firmadyne@ubuntu:~/firmadyne$ sudo apt-get install qemu-system-arm \
> qemu-system-mips qemu-system-x86 qemu-utils
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following additional packages will be installed:
<output skipped for brevity>
Do you want to continue? [Y/n] y
<output skipped for brevity>
```

Finally, set the FIRMWARE_DIR variable in the firmadyne.config file to the location of the firmadyne files:

```
firmadyne@ubuntu:~/firmadyne$ sed -i \
> 's#/vagrant/firmadyne#/firmadyne/firmadyne#' firmadyne.config
firmadyne@ubuntu:~/firmadyne$ sed -i 's/#FIRMWARE_DIR/FIRMWARE_DIR/' \
> firmadyne.config
firmadyne@ubuntu:~/firmadyne$ head firmadyne.config
#!/bin/sh

# uncomment and specify full path to FIRMADYNE repository
FIRMWARE_DIR=/home/firmadyne/firmadyne/

# specify full paths to other directories
BINARY_DIR=${FIRMWARE_DIR}/binaries/
TARBALL_DIR=${FIRMWARE_DIR}/images/
SCRATCH_DIR=${FIRMWARE_DIR}/scratch/
SCRIPT_DIR=${FIRMWARE_DIR}/scripts/
<truncated for brevity>
```

#### Lab 24-4: Emulating Firmware

Now that you have set up the environment, you may emulate a sample firmware (again, as described on the FIRMADYNE GitHub).

First, using the extractor script, extract the firmware:

```
firmadyne@ubuntu:~/firmadyne$ wget -r \
http://www.downloads.netgear.com/files/GDC/WNAP320/WNAP320%20Firmware%20Version%202.0.3.zip
firmadyne@ubuntu:~/firmadyne$ ./sources/extractor/extractor.py -b Netgear \
> -sql 127.0.0.1 -np -nk "WNAP320 Firmware Version 2.0.3.zip" images
>> Database Image ID: 1
```

```
/home/firmadyne/firmadyne/WNAP320 Firmware Version 2.0.3.zip
>> MD5: 51eddc7046d77a752ca4b39fbda50aff
>> Tag: 1
>> Temp: /tmp/tmpUVsRC8
<output skipped for brevity>
>> Skipping: completed!
>> Cleaning up /tmp/tmpUVsRC8...
```

Now, you may use the getArch script to get the architecture and store it in the database (enter the firmadyne DB password when prompted, which is “firmadyne”):

```
firmadyne@ubuntu:~/firmadyne$ ./scripts/getArch.sh ./images/1.tar.gz
./bin/busybox: mipseb
Password for user firmadyne:
```

Now, store the location of the extracted file system into the database:

```
firmadyne@ubuntu:~/firmadyne$ ./scripts/tar2db.py -i 1 -f ./images/1.tar.gz
```

Next, make a virtual image to launch with QEMU, using the makeImage script:

```
firmadyne@ubuntu:~/firmadyne$ sudo ./scripts/makeImage.sh 1
```

Then, infer the network (this command will run for up to 60 seconds, so be patient):

```
firmadyne@ubuntu:~/firmadyne$ ./scripts/inferNetwork.sh 1
Querying database for architecture... Password for user firmadyne:
mipseb
Running firmware 1: terminating after 60 secs...
main-loop: WARNING: I/O thread spun for 1000 iterations
qemu-system-mips: terminating on signal 2 from pid 23713
Inferring network...
Interfaces: [('brtrunk', '192.168.0.100')]
Done!
```

Now that you know what the IP is, run the emulator:

```
firmadyne@ubuntu:~/firmadyne$ ./scratch/1/run.sh
Creating TAP device tap1_0...
Set 'tap1_0' persistent and owned by uid 1000
Bringing up TAP device...
Adding route to 192.168.0.100...
Starting firmware emulation... use Ctrl-a + x to exit
<output skipped for brevity>
```

If at any time you mess up the preceding commands and want to reset the database and environment, simply run the following commands:
