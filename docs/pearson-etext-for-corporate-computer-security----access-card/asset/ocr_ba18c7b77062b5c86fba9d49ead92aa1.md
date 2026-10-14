![](bbox=[0.3, 0.067, 0.89, 0.232])

**Figure 10-12** Intrusion Detection Systems (IDSs) (Study Figure)

![](bbox=[0.301, 0.28, 0.89, 0.448])

**Figure 10-13** Functions of a Simple IDS

**AUTOMATED ANALYSIS BY THE IDS** IDSs do a good deal of automated analysis throughout the day. Administrators tend to be unaware of this analysis unless the IDS issues a warning based on what it finds during automated analysis.

Attack Signatures  Several general methods are available for the IDS to find patterns in the large amount of data in its log files. The simplest IDS analysis is the use of attack signatures. These identify known attack patterns. This works much of the time but fails to detect attacks that do not have signatures in the signature database.

Anomaly Detection  The most sophisticated techniques involve anomaly detection, in which the IDS looks for deviations from historical traffic patterns. Anomaly detection can detect new threats that do not yet have attack signatures, but it is less precise than attack signatures.

**ACTIONS** Finally, there are the actions taken by the IDS and by the people using it.

Alarms  Merely collecting and analyzing data accomplishes nothing. IDSs must use results from analysis to interact with humans. Most obviously, they generate **alarms** if analysis indicates a dangerous condition.

The IDS should only generate alarms for high-threat conditions. If an IDS were to send alarms for all threats, security administrators would be flooded with alerts. (Think of hair-trigger car alarms.) Some firms find that even high-threat alarms are too numerous (and too frequently incorrect) and throw away their IDSs.

Alarms should not be generalized indicators that something appears to be wrong.

+   - Alarms should be as *specific* as possible, giving the user a description of what the problem is.
+   - There should be a way to *test* the alarm for accuracy, and
+   - The alarm should give *advice* about what the security administrator should do.