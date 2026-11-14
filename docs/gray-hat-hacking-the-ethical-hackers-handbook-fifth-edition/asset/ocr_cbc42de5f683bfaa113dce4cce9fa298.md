# ATM Malware

The automated teller machine, or ATM, is a major target for criminals, and the reason is simple: it’s loaded with cash! Twenty years ago, the challenge for criminals was to break into a secure ATM vault where the money was kept, but in recent years attackers find a potentially easier path to money by infecting ATMs with malware. In this chapter, we take a look at some of the most dangerous ATM malware in recent years and, more important, techniques that aid in dissecting and identifying indicators of compromise. In addition, we look at ways to mitigate the risks presented by ATM malware.

In this chapter, we discuss the following topics:

+   - Automated teller machines (ATMs)
+   - Extensions for Financial Services (XFS)
+   - XFS architecture
+   - XFS manager
+   - ATM malware
+   - ATM malware countermeasures

# ATM Overview

Automated teller machines have existed for more than 50 years now, and their main purpose is to dispense cash. However, nowadays these machines can also be used to pay utility bills, add credit to phones, or even deposit checks. In this chapter, we are going to be working with a real NCR Personas 5877 ATM (P77), which is a Windows PC–based self-service ATM. Figure 20-1 shows the external components of the machine. Some of these components are self-explanatory, but the following deserve more explanation: