# STEP 3. Bring your network card back up:

```
ifconfig eth0 up
```

If you get errors, the most common issue is not having root-level privileges.

![](bbox=[0.07, 0.21, 0.73, 0.54])

FIGURE 11-15 macchanger.

# Note

While ifconfig is commonly used, it does have known bugs, some of which are listed in the man page. There is an alternative, the package iproute2, with the tool ip. Here are the equivalent ip commands for bringing up/down an interface and changing its MAC address:

+   - ip link set eth0 down
+   - ip link set address a1:b2:c3:11:22:33 eth0
+   - ip link set eth0 up

# Ghost Phisher

Ghost Phisher is a very versatile tool with several interesting functions. Figure 11-16 shows the main screen.