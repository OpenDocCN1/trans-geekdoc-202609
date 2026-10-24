CTS lines in the RS-232 interface. In software handshaking, the same lines that carry the data also carry handshaking codes. An example is the XON and XOFF codes transmitted on the data lines in RS-232 links.

USB uses software handshaking. A code indicates the success or failure of all transactions except in isochronous transfers. In addition, in control transfers, the Status stage enables a device to report the success or failure of an entire transfer.

Handshaking signals transmit in the handshake or data packet. The defined status codes are ACK, NAK, STALL, NYET, and ERR. The absence of an expected handshake code indicates a more serious error. In all cases, the expected receiver of the handshake uses the information to help decide what to do next. Table 2-4 shows the status indicators and where they transmit in each transaction type.

# ACK

ACK (acknowledge) indicates that a host or device has received data without error. Devices must return ACK in the handshake packets of Setup transactions when the token and data packets were received without error. Devices may also return ACK in the handshake packets of OUT transactions. The host returns ACK in the handshake packets of IN transactions.

# NAK

NAK (negative acknowledge) means the device is busy or has no data to return. If the host sends data at a time when the device is too busy to accept the data, the device returns a NAK in the handshake packet. If the host requests data from the device when the device has nothing to send, the device returns a NAK in the data packet. In either case, NAK indicates a temporary condition, and the host retries later.

Hosts never send NAK. Isochronous transactions don’t use NAK because they have no handshake packet for returning a NAK. If a device or the host doesn’t receive transmitted isochronous data, it’s gone.