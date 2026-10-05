+   * LLC Class 3: Acknowledged-Connectionless (AC), this is a 'connectionless-acknowledged' implementation that is rarely used.

The structure of the LLC PDU shown in figure 12.

# LLC PDU

| Bits | 8 | 8 | 8 or 16 | |
|---|---|---|---||
| DSAP | SSAP | Control | Data |
| 7 | 1 | 7 | |
| Destination Address | I/G | Source Address of SAP | C/R |
| | | 0 - Individual 1 - Group | 0- Command 1- Response |

**Figure 12:** Structure of the LLC PDU.

**Table 1:** LLC command PDUs

| Operation | Command | Response | Format | Control Field Hex. Value |
|---|---|---|---|---||
| Type 1 (CL) | Unnumbered Information (UI) | | Unnumbered (U) | 03 |
| | Exchange Identification (XI) | Exchange Identification (XI) | Unnumbered (U) | AF, BF |
| | Test (TEST) | Test (TEST) | Unnumbered (U) | E, F3 |
| Type 2 (CO) | Information (I) | Information (I) | Information (I) | 00 00 to 00 FF |
| | Receiver Ready (RR) | Receiver Ready (RR) | Supervisory (S) | 01 00 to 01 FF |
| | Receiver Not Ready (RNR) | Receiver Not Ready (RNR) | Supervisory (S) | 05 00 to 05 FF |
| | Reject (REJ) | Reject (REJ) | Supervisory (S) | 09 00 to 09 FF |
| | Set Asynchronous Balance Mode Extended (SABME) | Unnumbered Acknowledgment (UA) | Unnumbered (U) | 6F, 7F (SABME) and 63, 73 (UA) |
| | Disconnect (DISC) | Disconnected Mode (DM) | Unnumbered (U) | 43, 53 (DISC) and 0F, 1F (DM) |
| | | Frame Reject (FRMR) | Unnumbered (U) | 87,97 |
| Type 3 (AC) | Ack Connectionless, seq 0 (AC0) | Ack Connectionless, seq 0 (AC0) | Unnumbered (U) | 67, F7 |
| | Ack Connectionless, seq 0 AC1 | Ack Connectionless, seq 0 (AC1) | Unnumbered (U) | E7, F7 |

The LLC SAP's job is to support the up and coming MAC frames and direct them to the appropriate application or upper layer protocol. NetBIOS uses the SAP address of F0, IP uses 06 while DLSw uses 04 and Network Management uses F4. The Null SAP, address 00 does not identify any SAP to any protocol.