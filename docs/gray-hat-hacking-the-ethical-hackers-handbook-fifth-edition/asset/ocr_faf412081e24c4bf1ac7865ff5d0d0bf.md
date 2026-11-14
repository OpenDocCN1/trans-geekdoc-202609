# # Dissecting Ransomware

This chapter dissects a unique family of malware known as *ransomware*. This malware is able to take control of a system unless a ransom is paid to its creators.

In this chapter, we cover the following topics:

+   - History of ransomware
+   - Options for paying a ransom
+   - Dynamic and static analysis of Ransomlock
+   - Decoding in memory
+   - Anti-debugging checks
+   - Taking control of the Desktop
+   - Identifying and analyzing Wannacry encryption

# ## The Beginnings of Ransomware

Ransomware is a unique family of malware that is able to take full control of a machine until a ransom is paid by the victim. In order to increase the chances of getting money, the malicious program will pretend to look like it’s coming from a legitimate source, such as a law enforcement agency, stating that the end user has been caught visiting unauthorized websites and therefore needs to pay the violation fee. Other strategies to fool the end user include presenting a fake Windows Product Activation screen, asking the victim to pay to reactivate the system due to a specific fraud being detected. Normally, the crooks will set an expiration period in which to pay the ransom, forcing the victim to send the money right after being infected. An excellent video from Symantec explaining ransomware can be found in the “For Further Reading” section at the end of the chapter.

Ransomware can be classified in a few different ways, based on the way it manipulates the data:

+   - Crypters A type of ransomware that encrypts user data, effectively holding it for ransom until the victim decides to exchange money for the decryption key.
+   - Lockers A type of ransomware that utilizes various techniques to prevent users from interacting with their operating system. In this case, the operating system is held for ransom; the user’s data on disk is not modified by the malware.
+   - Leakware (doxware) Unlike the previous two classes, where the attacker doesn’t have access to the data, leakware typically employs a remote administration tool to exfiltrate the victim’s data. The attacker then threatens to publish the data unless a ransom is paid.

This kind of malware is not new. The first ransomware utilizing encryption, called the