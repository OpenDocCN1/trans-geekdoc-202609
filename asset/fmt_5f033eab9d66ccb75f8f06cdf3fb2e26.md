
# 简报记录内容

在简报中，您想了解哪些内容（您会记录什么）？通常您会依据通用检查清单进行记录。

# 1. 进入目录查找文件

进入`/path.to/xxx`目录，找到`xxx.json`。

在表达式`cvar = avar + bvar`中，加法运算符（`+`）将`avar`与`bvar`相加，得到它们的和`cvar`。

在`List.of(arg0, arg1, arg2)`中，`List`接口的工厂方法`of()`接受一系列的元素，返回包含它们的只读列表。

之后我们这样调用`cmd`命令：`cmd arg0 arg1 arg2`。

```
if (condVar > someVal) {console.log("xxx")}
```

# 2. 犯罪现场拍照步骤

If allowed, photograph the crime scene. This includes the area in general, computer monitors, electronic instrument information from devices that are lying around in the area (cell phones, pagers, etc.), and cabling connections (including under the floor if it is a raised floor). Make sketches as necessary. If there is an active modem connection (flashing lights indicating communication in progress), quickly unplug it and obtain internal modem information via an `rs-232` connection to your laptop. Look at raised ceilings. Is it normal for a modem to be here? If so, is it normal for it to be active at this time?

# 3. 确定远程登录与系统活动

You now want to find out whether anyone else is on Solaris 1 (remotely) and what has been going on with the system recently. What UNIX commands should you use?

* `script a:\\SaturnNightsSolarisEvidence1`: Opens a text file that will store everything you do on this system. Note that we are sending our data to a floppy drive, not to the hard drive of the Solaris system.
* `Date`: To have the date/time in this log.
* `Who`: To obtain a list of currently logged in users.

# 4. 判断 Leopold1 的来源含义

You notice someone on Solaris 1 named Leopold1 coming from `221-41-12.galaxy.com`. What does this indicate?

> Leopold1 is attached to Solaris 1 via an ISP named galaxy.com.

# 5. 显示所有 TCP/IP 连接

You now want to display a list of recent and current Transmission Control Protocol/Internet Protocol (TCP/IP) connections to the system.

```
netstat -a
```

When you performed the last command, you noticed a `.telnet` at the end of your system name. What does this indicate?

There is a telnet connection between Solaris 1 and Leopold1 (on `221-41-12.galaxy.com`).

# 6. 获取 Leopold1 的近期登录记录

You now want to obtain a list of recent logins pertaining to Leopold1.

```
last Leopold1
```

The results of your last command indicate that Leopold1 logged in earlier during the day and is currently logged into Solaris 1. You want to see all the processes running in memory that Leopold1 is running. What do you type?

```
ps -aux | grep Leopold1
```

The results of your last command indicate that the following processes are running that belong to Leopold1: `2365`, `2287`, `2087`, and `2001`. In these processes you see two that alarm you. One is “Sniffer” and the other is “256:47 rsh www.cirrus.com exec/tmp/.hidden/BeatYou.” This indicates the following:

* “Sniffer” indicates that Leopold1 has planted a device to monitor Solaris 1 for logins, user IDs, passwords, specific traffic.
* The other indicates that for 256 minutes and 47 seconds the program BeatYou has been running on a remote computer system named `www.cirrus.com` using the remote shell command `rsh`.

# 7. 通知 FBI 并进行取证

You notify the FBI agent working with you as to what you have found. He immediately utilizes bureau contacts and gets in touch with the ISP (Internet Service Provider) galaxy.com, then leaves for the ISP site. The ISP also does a traceback while the FBI agent is on site and determines exactly where Leopold1 is coming from. The ISP moves all logs pertaining to Leopold1 to a trusted system and backs them up to a DAT tape. An FBI agent picks up the tape and brings it to you at SaturnNights. You are now directed to remove Leopold1 from the system, collect RAM (Random Access Memory) evidence, and collect all evidence from the Solaris 1 hard drive. What steps do you follow to remove Leopold1 and collect RAM evidence?

To remove Leopold1 from the system, just remove all of his processes:

* `kill -9 2365`
* `kill -9 2287`
* `kill -9 2087`
* `kill -9 2001`

To collect RAM evidence:

```
ps -aux > a:\\Solaris1RAMproc
```

This shows you all processes running and collects this information to diskette.

You photograph the screen showing the information on the processes. The Solaris 1 expert tells you about each process that is running and tells you there is a battery backup on the box. He opens the box and disconnects it. You now pull the plug on the back of the box, which makes the box shut down ungracefully and causes a panic, and all RAM information is written to a core file.

Solaris 1 is now inactive. The evidence cannot leave the site. You have to do your analysis on site using the CF tools you brought with you. The FBI has supplied you with a “scrubbed” Intel-based PC (personal computer) running Windows XP. Also included are a diskette drive, a CD-ROM drive, and a new external 200-GB hard drive that you will use to hold the bitstream backup of the Solaris 1 system. In this case we will use SafeBack (from NTI [New Technologies, Inc.]) to obtain this bitstream backup (we covered its use in a prior chapter).

Now we can pick up where we left off earlier. `Lib27.s01` will represent the evidence we have collected from the Solaris 1 system. Figure 5.4 shows where we are.

![Figure 5.4 Evidence we have collected from the Solaris 1 system.](img/fig5.4.jpg)

*Figure 5.4* Evidence we have collected from the Solaris 1 system.

If I click the Total File Items button in the top left pane, I see the entry shown in Figure 5.5 in the bottom pane.

![Figure 5.5 Entry shown in the bottom pane.](img/fig5.5.jpg)
