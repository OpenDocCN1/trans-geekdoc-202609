Now, on the system where IDA Pro is installed, open exactly the same okiru-mips binary just executed and then go to Debugger | Select Debugger | Remote GDB Debugger.

Select the Debugger | Process Options and fill out the options, making sure you enter the path of the binary as it appears in the Ubuntu VM (Debuggee), as well as the IP address and port, and then click OK (see Figure 25-19).

![](bbox=[0.122, 0.203, 0.878, 0.519])

Figure 25-19 Debugger process options

Last but not least, set a breakpoint at the entry point of the program in IDA (by pressing F2 on the desired line) to make sure the malware execution stops at the beginning.

Although that is the expected behavior, sometimes it fails and executes all the way to the end. This is simply a sanity check. To run it, click Debugger | Start Process.

A warning will prompt to make sure you know what you are doing. Click the Yes button.

You should receive a message saying that there is a process already being debugged, which confirms we are heading in the right direction (see Figure 25-20).