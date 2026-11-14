```
39345: May 22 13:56:35.811: %LINEPROTO-5-UPDOWN: Line protocol on Interface Serial0/0/1, changed state to down
```

+   - Seq num: 39345;
+   - Timestamp: May 22 13:56:35.811;
+   - FACILITY: LINEPROTO;
+   - SEVERITY level: 5 (notification);
+   - MNEMONIC: UPDOWN;
+   - message text: Line protocol on Interface Serial0/0/1, changed state to down.

# 3.3.3. Configuring a Syslog client

To configure a router as a Syslog client, proceed as follows:

| Command | Description |
|---|---|
| Router(config)# service timestamps log datetime msec | Activates the timestamps on the debug and log messages. |
| Router(config)# logging host [ ip-address | hostname ] | Identifies the address of the Syslog server or its host name. |
| Router(config)# logging trap level | Limits the messages sent to the Syslog function depending on the desired severity. The default value is 6 (0 to 6). |
| Router(config)# logging on | Activates the despatch of messages to be logged. The default value is “on”. |
| Router# show logging | Displays the logging status. |

# 3.4. Implementing the Simple Network Management Protocol (SNMP)

# 3.4.1. Introducing the SNMP

– The Simple Network Management Protocol (SNMP) allows you to monitor, diagnose, and manage network equipment remotely.

– SNMP’s objectives can be summarized as follows:

+   – monitoring the performance of the network and knowing the overall state of the devices (active, inactive, partially operational, operational, network gridlocked etc.);