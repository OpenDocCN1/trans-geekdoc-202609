Second, like firewalls, NIDSs cannot scan encrypted data. Although NIDSs can scan unencrypted parts of an encrypted packet (typically, an added IP header), this provides limited information. As encryption increases in popularity, the effectiveness of NIDSs will degrade proportionally.

# Test Your Understanding

+   18.  
+      a. At what information do NIDSs look?  
+      b. Distinguish between stand-alone NIDSs and switch-based or router-based NIDSs.  
+      c. What are the strengths of NIDSs?  
+      d. What are the two weaknesses of NIDSs?

# HOST IDSs

A firm has many host computers. The most critical hosts are the firm’s servers. Host IDSs (HIDSs) work on data collected on the host computer.

# ATTRACTION OF HIDSs

The main attraction of HIDSs is that they provide highly specific information about what happened on a particular host. This is important for problem diagnosis.

# WEAKNESSES OF HOST IDSs

**Limited Viewpoint**  Host IDSs have two major weaknesses. First, a host IDS has a limited view of what is happening on the network. The same myopic focus that allows them to be specific also means they cannot see the broader picture. Repeated login failures on one host are a cause for concern. Repeated login failures on multiple hosts within a short time period are a much greater cause for concern.

**Host IDSs Can Be Compromised**  In addition, host IDSs are subject to attack. As noted earlier, an attacker can delete or change log files, effectively making the attacker invisible to the HIDS.

# HOST IDSs: OPERATING SYSTEM MONITORS

Most host IDSs are operating system monitors, which focus on operating system events. Here are some data typically collected by operating system monitor IDSs.

+   - Multiple failed logins
+   - Creating new accounts
+   - Adding new executables (programs—may be attack programs)
+   - Modifying executables (installing Trojan horses does this)
+   - Adding registry keys (changes how system works)
+   - Changing or deleting system logs and audit files
+   - Changing system audit policies
+   - User accessing critical system files
+   - User accessing unusual files
+   - Changing the OS monitor itself

# Test Your Understanding

+   19.  
+      a. What is the major attraction of a HIDS?  
+      b. What are the two weaknesses of host IDSs?  
+      c. List some things at which host operating system monitors look.