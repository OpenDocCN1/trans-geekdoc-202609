This dialog box is very important for three reasons:

+   - The Cost spinner box is used to help AD identify which link to use. AD will choose lower cost paths over higher-cost paths. It is set to a cost of 100 by default.

+   - The Replicate Every 17 Minutes spinner box is used to control how often AD tries to replicate over this link. It is set to 18 minutes by default.

+   - Last, the Change Schedule button allows you to modify when replication occurs based on a schedule.

Click the Change Schedule button, and you'll see a dialog box similar to Figure 22.18. The schedule for this site link has been changed to allow replication only during the nonpeak hours of midnight to 6 A.M.

# Figure 22.18
Setting the replication schedule

![](bbox=[0.415, 0.353, 0.835, 0.558])

It could be that the HQ-to-Crosstown link is heavily used during the daytime hours, and you want replication to occur only during nonbusiness hours. Setting the schedule tells AD not to bother to replicate before 6 P.M. daily.

# REPLICATE AT EVERY 180 DAYS

AD sites must replicate at least once 180 days or less. AD throws away objects that have been inactive for 180 days, if one site and another didn't talk for a few months, they'd start deleting from their copies of AD that they weren't using but other DCs in sites were still using. This is a problem if a DC goes down for a long period of time. Do not reconnect a DC to the network if it hasn't replicated to AD for more than 180 days.

This number was 60 days in previous operating system versions, based on the default tombstone lifetime. However, the tombstone lifetime was changed to 180 days in Server 2003 with SP1 and newer operating systems including Windows Server 2012 R2.