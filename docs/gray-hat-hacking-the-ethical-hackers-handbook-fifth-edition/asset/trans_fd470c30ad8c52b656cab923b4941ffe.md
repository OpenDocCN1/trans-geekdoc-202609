

检查新固件按钮，我们现在看到有 1.12 版本可供下载。

![](img/5f597c6a70133069118d9e804ace3775_671_0.png)

在点击升级固件按钮之前，我们需要设置 ping 来监控设备。当我们点击升级固件按钮时，应该会看到以下下载进度框：

![](img/5f597c6a70133069118d9e804ace3775_672_0.png)

```
root@kali:~/DAP-1320# ping 192.168.1.173
64 bytes from 192.168.1.173: icmp_seq=56 ttl=64 time=2.07 ms
64 bytes from 192.168.1.173: icmp_seq=57 ttl=64 time=2.20 ms
64 bytes from 192.168.1.173: icmp_seq=58 ttl=64 time=3.00 ms
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

您会注意到主机变得无响应 ①，随后重新上线 ②。这表明该设备已重启。此时，我们已经证明可以将命令注入升级 URL，设备会执行该命令。如果不向设备上传可执行文件，则受限于设备上现有的内容。例如，如前所述，如果 telnetd 编译进了 Busybox（本系统中不包含），您可以直接启动它以免密码访问 shell，如下所示：

```
telnetd -l /bin/sh
```

下一节将演示此方法。如果需要，您可以为该处理器交叉编译一个如 netcat 这样的二进制文件，然后通过 tftp 或 tfcp 上传，如 Craig Heffner 所演示，2，或者您可以使用另一种方法。

## 使用仿真的动态分析

事实证明，在某些情况下，无需手头有硬件即可执行漏洞分析和利用固件。

### FIRMADYNE

FIRMADYNE 3 工具允许使用 QEMU 虚拟机监控程序模拟固件。这种方法的好处是您无需购买硬件来测试固件。这种强大的方法允许并行进行规模化测试。Dominic Chen 下载并测试了超过 23,000 个固件样本，并成功运行了其中约 9,400 个（约 40%），4 这一点也不算差。在接下来的实验中，我们将设置并执行 FIRMADYNE。

#### 实验 24-3：设置 FIRMADYNE

如果您想跟进本实验，我们将使用 Ubuntu 16.04.3 服务器，运行在 VMware 或 VirtualBox 中，使用 NAT 网络设置，仅安装了 OpenSSH，用户名为 firmadyne。首先，我们需要使用 FIRMADYNE GitHub 上的说明来设置 FIRMADYNE 工具（参见本章末尾的“进一步阅读”部分）：

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

接下来，安装 PostgreSQL 数据库：

```
firmadyne@ubuntu:~$ sudo apt-get install postgresql
```

然后，设置用户 firmadyne，密码为“firmadyne”（出现提示时）：

```
firmadyne@ubuntu:~$ sudo -u postgres createuser -P firmadyne
Enter password for new role:
Enter it again:
```

现在，创建数据库并对其进行初始化。请注意，firmware 追加到下一条命令的末尾：

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

下载 FIRMADYNE 的预构建二进制文件（或使用 FIRMADYNE GitHub 上的说明构建二进制文件）：

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

现在安装 QEMU：

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

最后，将 firmadyne.config 文件中的 FIRMWARE_DIR 变量设置为 firmadyne 文件的位置：

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

#### 实验 24-4：模拟固件

既然您已经设置好了环境，可以模拟一个示例固件（同样，如 FIRMADYNE GitHub 上所述）。

首先，使用提取器脚本提取固件：

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

现在，您可以使用 getArch 脚本获取架构并将其存储到数据库中（出现提示时输入 firmadyne 数据库密码，即“firmadyne”）：

```
firmadyne@ubuntu:~/firmadyne$ ./scripts/getArch.sh ./images/1.tar.gz
./bin/busybox: mipseb
Password for user firmadyne:
```

现在，将提取的文件系统位置存储到数据库中：

```
firmadyne@ubuntu:~/firmadyne$ ./scripts/tar2db.py -i 1 -f ./images/1.tar.gz
```

接下来，使用 makeImage 脚本创建用于 QEMU 启动的虚拟镜像：

```
firmadyne@ubuntu:~/firmadyne$ sudo ./scripts/makeImage.sh 1
```

然后，推断网络（此命令将运行最多 60 秒，请耐心等待）：

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

既然您知道 IP 是什么，运行模拟器：

```
firmadyne@ubuntu:~/firmadyne$ ./scratch/1/run.sh
Creating TAP device tap1_0...
Set 'tap1_0' persistent and owned by uid 1000
Bringing up TAP device...
Adding route to 192.168.0.100...
Starting firmware emulation... use Ctrl-a + x to exit
<output skipped for brevity>
```

如果您随时搞砸了前面的命令并想要重置数据库和环境，只需运行以下命令：

