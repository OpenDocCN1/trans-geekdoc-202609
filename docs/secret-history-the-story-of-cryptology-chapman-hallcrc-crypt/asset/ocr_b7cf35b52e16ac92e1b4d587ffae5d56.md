![](bbox=[0.22, 0.12, 0.75, 0.62])

# Figure 9.11 The entire encryption process.

warned that the device “should be operated at a maximum speed of 45 to 50 words per minute… if this speed is exceeded, characters may fail to print.”18

For many cipher machines of this era, the intended recipient would have to figure out where to insert word breaks to make the recovered message readable. In contrast to such machines, SIGABA was implemented in a way that conveyed the spacing along with the message. Because there are only 26 wires in each Cipher Rotor it might seem that this is impossible, but a 27th symbol really isn’t needed. The space-preserving method worked like so:

+   - Prior to enciphering, SIGABA converts every Z to an X. Real Xs are left unchanged. Basically, Zs and Xs are combined in a single character denoted by X.
+   - Spaces are converted to (the now available!) Zs.

18 Mucklow, Timothy J., SIGABA/ECM II: A Beautiful Idea, Center for Cryptologic History, National Security Agency, Fort George G. Meade, Maryland, 2015, p. 33.