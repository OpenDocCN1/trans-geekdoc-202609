this case, WFS_CMD_PIN_GET_DATA, to read the information entered at the pinpad).

```
xor             ebx, ebx
push            408             ; WFS_CMD_PIN_GET_DATA
inc             ebx
push            ecx
mov             [ebp+var_1A], ebx
mov             [ebp+var_A], 0C000h
mov             [edx+83Ch], bl
call            ds:WFSAsyncExecute
```

Figure 20-5 Interacting with the pinpad

We have gone through all details an XFS-compliant ATM follows when dealing with daily operations, and we discussed the importance of the XFS manager in coordinating this effort. In the next section, we look at some techniques for analyzing ATM malware.

# ATM Malware Analysis

Now that you understand how the XFS-compliant ATM works from end to end, let’s look at some useful techniques for dissecting ATM malware based on real threats found in the wild.

We’ll take a quick overview of the main features of ATM malware so that you understand what types of threats are seen in the wild, how are they installed in the ATMs, how the malware interacts with the attackers, and how the malware steals information or money!

# Types of ATM Malware

There are two types of ATM malware: those affecting cardholders and those affecting banks.

# Malware Affecting Cardholders

This type of malware focuses on stealing information from the ATM such as the victims’ full names, debit card numbers, expiration dates, and encrypted PINs. All of this data is then sold on the black market, where cloned cards are created and unauthorized online payments are made. From a malware analysis perspective, these threats act like information stealers—no knowledge about ATMs is necessarily needed during the analysis. Examples of these kind of threats are PanDeBono and NeaBolsa, found in Latin America.⁴ These threats steal information via a USB device that’s inserted into the machine and is recognized and validated by the malware running inside.

Even though skimmer devices are related to physical attacks, and are therefore outside the scope of this chapter, it is worth mentioning them because they affect cardholders. These devices are physically attached to the ATM in a hidden way so that the victim cannot see them (see Figure 20-6). Those devices can come either with a camera or as a fake pinpad or