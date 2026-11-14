# On switch S1

+   - Use the following options to configure the ssh connections:
+   - domain name: tri.local;
+   - the user name: sshadmin with the password: Ci$c0ssh;
+   - The RSA encryption key is 1024 bits;
+   - the SSH version used is version 2;
+   - the wait time is 90s;
+   - the number of login attempts is 3;
+   - allow the ssh and telnet sessions.

# Part C: simulating attacks on layer 2

Download and install the hyenae¹ tool.

# 1. Simulate a MAC address flooding attack.

# Objective

+   1.1. Send a ping between S1 and Host1.

```
S1#ping 172.16.0.2
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 172.16.0.2, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 8/20/36 ms
```

+   1.2. Display the S1 switch table.

```
S1#sh mac-address-table
Destination Address Address Type VLAN Destination Port
------------------------------------------------------
cc01.0d68.0000 Self 1 Vlan1
0200.4c4f.4f50 Dynamic 1 FastEthernet0/0
```

With cc01.0d68.0000 being the MAC address of VLAN1. This value is not necessarily the same when carrying out this exercise.

Write the address of your VLAN1: