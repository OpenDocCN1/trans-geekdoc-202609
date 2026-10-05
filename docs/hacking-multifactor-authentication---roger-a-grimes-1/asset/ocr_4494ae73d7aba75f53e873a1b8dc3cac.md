# Chapter 21 Test: Can You Stop the Vulnerabilities? 439

to be used for future authentication and, when successful, displays a four-digit alphanumeric code on the OLED screen that is input back into the Bloomberg Terminal software.

NOTE Other MFA solutions have used flashes of light. BRToken/Datablink (now owned by WatchGuard) has a similar flash communication technology back in 2008. It uses a bright light bit, for 1, no flash (i.e., dark) for 0, every 60 ms. You can watch (a Brazilian Portuguese-language) demonstration of this device here: https://www.youtube.com/watch?v=nFRSD_7XQOY.

Once the user registers and syncs the device, each time they want to log on to their Bloomberg Terminal software instance go the process just described, except their fingerprint will be used for authentication comparison instead of registration and they won't be prompted for eight-digit B-Unit serial number. You can read about the B-Unit 3 MFA device how to register and log on with it in more detail here: data.bloomberg.com/professional/sites/10/251766_BBGT_B-Unit_USRG_DIG_FINAL.pdf. Watch a video of the registration process here: bba.bloomberg.net/Video/BUnitTutorial.

The first time I saw the four Bloomberg B-Unit and its use, .i .blew. .me .away! I was a big fan. Let me summarize the pertinent MFA authentication:

+   1. User logs on to software using login name and password.
2. User holds MFA device up to screen so that software communicates optically to MFA device.
3. User swipes fingerprint to authenticate themselves to the MFA device.
4. MFA device displays a four-digit code, which user inputs into the software.

All of this must occur successfully, in order, for the user to be authenticated to the software. If any steps fail, the user will not be able to use the Bloomberg Terminal software. Users can have only one B-Unit at a time.

I'll end this by asking you to threat-model the Bloomberg MFA device. What potential vulnerabilities are even possible? Are there offsetting mitigations that can be deployed to minimize those vulnerabilities? Conduct a quick threat-modeling review, based on your limited knowledge of the Bloomberg MFA device, and then read further how to do it.

# Threat-Modeling the Bloomberg MFA Device

In this section I'm going to discuss some ways to possibly exploit users using Bloomberg Anywhere and relying on the Bloomberg B-Unit device. I'm not showing you this because I think the B-Unit device is weak or easily hackable. In fact, I think the exact opposite. I think the B-Unit is one of the best MFA devices and less hackable than most others that I've ever seen. The whole reason I'm using