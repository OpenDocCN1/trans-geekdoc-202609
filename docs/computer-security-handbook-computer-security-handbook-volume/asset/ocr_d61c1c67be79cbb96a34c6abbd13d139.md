+   - **Access control list.** Allows only certain clients to gain physical access to the LAN, based on the MAC address; this adds complexity to client management.
+   - **Server-based authentication.** Flexible user authentication with RADIUS for an additional layer of protection from illicit connections.

For more information about security for wireless networks, see Chapter 33 in this Handbook.

# 25.5 NETWORK OPERATING SYSTEM ISSUES.

In the early 1990s, it was common to find desktop systems running the Windows operating system and the Novell NetWare network operating system (NOS). Desktop applications ran over Windows, and NetWare was used only to move files to and from the shared file space, or to print documents.

Today, the distinction among the desktop operating system, server operating system, and NOS has disappeared. Operating systems such as Linux, MacOS, UNIX, and Windows all provide desktop application suites with networking capabilities, including communications protocols such as TCP/IP. There are some general security considerations for all LANs regardless of the specific operating system:

+   - Use whatever capabilities are provided by the operating system to employ strong passwords.
+   - Create password policies that force strong passwords. Change passwords periodically and do not allow reuse. Periodically audit passwords using password-cracking tools such as L0phtCrack (Windows) or crack (UNIX). Ensure that the administrator and root accounts are given passwords that are not widely distributed or guessed.
+   - Disable (or uninstall) any services that are not being used.
+   - Keep the operating system and application software up to date, and with the latest security patches installed.
+   - Carefully manage access control lists for files and other system/network resources.
+   - Strictly define users, groups, and network/domain trusts.
+   - Tightly secure any running applications.
+   - Log on as administrator or root only when necessary; otherwise log on as a regular user.
+   - Allow operators and administrators to log on only locally at server systems.
+   - Limit use of guest, demo, or anonymous accounts.
+   - Where feasible, put boot and system files as well as application files and data on different partitions, hard drives, or input/output (I/O) controllers.
+   - Regularly audit server systems.
+   - Monitor log files.
+   - Remove floppy, CD, DVD, and thumb drives from servers after the system has a stable configuration.
+   - Implement best industry practices when securing the operating system.
+   - Use vulnerability assessment tools on a regular basis to scan servers.
+   - Use intrusion detection tools to monitor potential attacks on the LAN that are launched from the internal network.