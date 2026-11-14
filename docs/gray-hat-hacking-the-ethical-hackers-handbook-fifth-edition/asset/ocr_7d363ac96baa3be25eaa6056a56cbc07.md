# # Techniques for Dissecting the Malware

In this section, we talk about how to dissect ATM malware and extract the most important indicators of compromise (IOCs). The main goals during a malware investigation should be the following:

+   1. Confirm the sample is targeting ATMs.
+   2. Confirm the sample is malicious.
+   3. Identify how the malware was installed. Normally it is very difficult to know this, unless the customer affected provides that information.
+   4. Identify how the malware interacts with the attackers.
+   5. Identify the purpose of the malware: either targeting the cardholder or the cash inside the ATM.

All these steps are detailed in this section.

# ## Confirm the Sample Is Targeting ATMs

If your job requires you to perform analysis on ATM malware, the first thing you need to do is to confirm that the sample provided is actually targeting these machines. One way to validate this is to check whether the binary in question is importing MSXFS.dll, which is the DLL that implements the default XFS manager in the teller machine (all the WFS* and WFM* functions described earlier in the chapter). This is a strong indicator. Figure 20-7 shows the Import Table from Ripper ATM malware (after UPX has unpacked the malware), and you can see that MSXFS.dll has been imported. This is the case with other malware families as well, such as GreenDispenser, Alice, SUCEFUL, and Padpin.