# Asynchronous Data Link Protocols

Asynchronous protocols shown below are used to facilitate communications between two personal computers over the public switched network.

![](bbox=[0.193, 0.153, 0.819, 0.233])

**Figure 6**: Asynchronous protocols.

# XMODEM

The XMODEM protocol was created years ago as a simple means of having two computers talk to each other. With its half-duplex mode of operation, ACK/NAK responses and CRC data checking, the XMODEM protocol has found its way into many applications. XMODEM specifies a half-duplex stop-and-wait protocol using a data frame comprised of four fields. The frame format for XMOD contains four fields, as shown below.

![](bbox=[0.223, 0.467, 0.775, 0.626])

**Figure 7**: XMODEM representation.

# XMODEM Frame Format

The four fields for XMODEM are the SOH field, header field, data field, and error-detection field. The first field of an XMODEM frame is simply a one-byte start-of-heading (SOH) field. SOH is a data-link control character indicating the beginning of the header. The second field is a two-byte sequence that is the number of the current frame being transmitted. The first header byte is called the sequence number, as the second header byte is simply the 2-s complement of the first byte, which is used to verify the validity of the first header byte (this is sometimes called redundancy).

The next field is the information field, which contains the actual user data. The information field has a maximum capacity of 128 bytes (e.g., 128 ASCII characters).