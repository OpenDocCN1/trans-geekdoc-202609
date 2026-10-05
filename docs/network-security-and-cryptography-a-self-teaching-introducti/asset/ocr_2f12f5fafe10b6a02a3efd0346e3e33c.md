4. The local TGS issues Ticket and session key K_{cgs}. The ticket is encrypted using secret key K_{tgs} that the local TGS shares with the remote TGS so that the remote TGS can open the ticket. The session key K_{cgs} is used for communication between C and the remote TGS, that is, TGS_{rem}.

Figure 9.2 illustrates the Authentication Sequence (Kerberos Version 4). Messages (1) and (2) are exchanged once per session, while messages (3) and (4) are exchanged per "Type of Service," and messages (5) and (6) are exchanged per Service Session.

![](bbox=[0.216, 0.335, 0.836, 0.833])

FIGURE 9.2 A schematic diagram of the Authentication Sequence (Kerberos Version 4).