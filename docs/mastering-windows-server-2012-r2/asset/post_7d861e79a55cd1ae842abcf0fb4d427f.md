
Depending on which field you select, you'll have different conditions that can be selected (such as "is exactly" or "is not exactly") and you can enter a value (such as true or false). It is possible to configure multiple conditions for any single filter. If all conditions are met, the filter will detect the printer.

You also have the ability to configure notifications with your filter. You can create a filter to send an email or run a script. Figure 16.43 shows the notification page.

# FIGURE 16.43
Configuring the notifications

![](img/41a83208e6906a3732620203b836cea7_914_0.png)

You wouldn't do this for all your filters, or you'd get started swamped by your printer server. However, you could have a high-priority printer that needs to be fixed as soon as a problem is detected. You could create a filter with one condition to identify this printer and a second condition with a field of Queue Status, create a condition of "is exactly," and a value of Error. Now whenever this filter detects the printer in error, it will send a notification. Or, if the solution is to run a script, you could configure the filter to automatically run the script.

# Troubleshooting Printer Problems

Printing under Server 2012 R2 is usually pretty-free—in the software, at any rate—but once in a while you may run into problems. The remainder of this chapter describes some of the more common printer problems and tells you how to solve them.

# Basic Troubleshooting: Identifying the Situation

First, try to figure out where the problem lies. Is it the printer? The application? The network? If you can tell where the problem lies, you'll simplify the troubleshooting process.

# PAPER JAMS

The printing problem that frustrates us is paper jams. Getting that last shred of jammed paper out of the print device can drive you to madness. To minimize paper jams, store somewhere with low humidity (curled paper jams easily), don't overflow the tray, and keep paper near before it enters the tray. Furthermore, some paper is designed to be printed to a specific side; it is packaged with an arrow on the reel and should be loaded with the arrow pointing out.

There are also a lot of differences between paper types. As one of many examples, copy paper and printer paper have many different properties, and using paper designed for copying machines may impact the quality in addition to increasing the risks of paper jams.

Printing troubles can happen because of any combination of three different causes:

- Hardware errors
- Software errors
- User errors

# NO ONE CAN PRINT

If no one can print, check the print device and network connection. Check the easy stuff first. Is the printer on online? Does the cartridge have ink? Is the printer server up and running? Did the printer ever work, or is this maiden voyage? If it never worked, make sure you have the right driver installed, or try downloading a new one from the manufacturer's website.

From the console, check the port settings. Is the printer sending data to the port the print device is connected to? Make sure you set up the TCP/IP port for a network-connected printer properly.

Also, see whether you can print from the printer server's console. There could be a network problem preventing people from reaching the server.

Make sure there's enough space on the print server's hard disk to store spool files. If the print server can't create files, it can't print from a spool.

Make sure the printer is set up to the proper print processor.

If you're using Internet Printing, make sure that this service is enabled.

# SOME PEOPLE CAN'T PRINT

What do people have in common? Are they all in a single subset? In the same group? Using the same application? Printing to the same printer? Find the elements they have in common, and that's probably the element that's causing the printing problem. For example, if everyone's printing from one subset can print but users from another subset cannot print, the problem is with the network, not the printer.

# ONE PERSON CAN'T PRINT

If only one person can't print, try to narrow down the source of the problem. Can the person print from another application? Can the person print from another computer? If this person can't print at all, see whether someone else can print from their computer. If so, check the permissions attached to the person who can't print. They may be denied access to the printer altogether.

# REBOOTING SPOOLER SOLVES ILLS

If only one person is having printing problems, try rebooting the computer and retrying the print job. You can resolve many issues by rebooting the user's computer. You won't know what the exact problem was, but it'll be solved, and both you and the user will be off doing more important things.

# Restarting the Spooler Service

A common problem that occurs with print servers is that the print spool service occasionally hangs. When this occurs, print jobs don't print and cannot be canceled. The solution is to stop and restart the Spooler service.

You can restart the service in the Print Roles within Server Manager. Scroll down to find the Print Spool service, right-click it, and select Restart. Sometimes you'll need to select Stop and then, after it stops, select Start.

Of course, you can also do the same thing from the command line with the following commands:

```
Net stop spooler
Net start spooler
```

Finally, here is the PowerShell cmdlet to stop, start, or restart the Spooler service.

```
Stop-Service "Spooler" -force
Start-Service "Spooler"
Restart-Service "Spooler" -force
```

# Isolating Printer Drivers

A new feature available with Windows Server 2012 R2 is the ability to isolate printer drivers from the operating system. If you find that a printer driver is not playing well with others still allows users to print, you can isolate it. 16.44 shows a driver that has been configured in isolation mode.

# FIGURE 16.44
Setting driver isolation

![](img/41a83208e6906a3732620203b836cea7_916_0.png)

By isolating a printer driver, you can prevent a faulty driver from stopping all the operations on a server. These are the three available choices:

- None Drivers isolation is not attempted.
- Shared Drivers operate in a shared process.
- Isolated The driver is isolated. This does take additional resources so it should be used only when necessary, and it can be useful for testing new drivers.
- System Default (Shared) This is used by default for all new drivers added to the server.

# The Bottom Line

Add the Print and Document Services role. Windows Server 2012 R2 servers can be configured to perform as printers. One of the first steps you must take is to add the Print Document Services role. There are different steps needed if you're adding the role to a full installation of Windows 2012 R2 vs. Server Core.

**Master It** What would you use to add the Print and Document Services role on a full installation of Windows 2012 R2? What tool would you use to add the Print and Document Services role on a Server Core installation of Windows 2012 R2?
