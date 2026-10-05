# Message 4 Ticket Granting Service Reply (KRB_TGS_REP) from TGS to C, for conveying of Service Ticket, and a Session Key $K_{c,t}$ for communication between C and V.

$AS\to C: Realm_e || ID_e || Ticket_e || E_{K_{c,s}}[K_{c,t} || Times || Nounce_s || Realm_s || ID_s]$

$Ticket_e || E_{K_c}[Flags_e || Realm_e || ID_e || AD_e || Times]$

The Flag will contain the options available for the use of Ticket$_e$, for-forwardable, Proxy-able, and so on.

Times will indicate the validity period. Its start-time can be post-dated, and this fact can be indicated in the Flag

# Message 5 Service Request (KRB_AP REQ) from C to Application Server for obtaining service.

$AS\to C: Options || Ticket_e || Authenticator_{c,s}$

$Authenticator_{c,s} = E_{K_{c,s}}[ID_c || Realm_s || Sub-Key || Seq#s]$

# Message 6 Service Reply (KRB_AP REP) from Application Server to C, for mutual authentication.

$AS\to C: E_{K_{c,s}}[TS_s || Seq#s]$

# 9.5.3 Differences between Kerberos V4 and Kerberos V5

Kerberos V4 has the following environmental and technical limita-tions, which have been successfully overcome in Kerberos V5:

+   1. **Encryption Algorithm**: Kerberos V4 permits use of only DES for encryption. But, Kerberos V5 permits use of other encryption algo-rithms also; a tag attached to the cipher-text indicates the $ID$ of the algo-rithm used.

+   2. **Communication Protocol**: Kerberos V4 uses only IP addressing for communication; but Kerberos V5 permits use of other network addressing protocols also; a tag indicates the $ID$ of the network address-ing used.

+   3. **Protocol for Message Byte Ordering**: Kerberos V4 uses a little-endian or big-endian format for byte ordering, and the type of formatting used is tagged to the message; but in Kerberos V5, the message structures are defined using Abstract Syntax Notation (ASN .1) and Basic Encoding Rules (BER), which provide unambiguous byte ordering.