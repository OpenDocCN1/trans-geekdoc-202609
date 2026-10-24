# Control Transfers: Structured Requests for Critical Data

**Sent by:** the host.

**PID:** the opposite of the direction of the previous transaction’s data packet. If the Data stage’s PID was OUT or if there was no Data stage, the Status stage’s PID is IN. If the Data stage’s PID was IN, the Status stage’s PID is OUT.

**Additional Contents:** the device and endpoint addresses.

# Data Packet

**Purpose:** enables the receiver of the Data stage’s data to indicate the status of the transfer.

**Sent by:** if the Status stage’s token packet’s PID is IN, the device sends the data packet; if the Status stage’s token packet’s PID is OUT, the host sends the data packet.

**PID type:** DATA1

**Additional Contents:** The host sends a zero-length data packet. A device may send a zero-length data packet (success), NAK (busy), or STALL (endpoint halted).

**Comments:** For most requests, a zero-length data packet sent by the device indicates that the requested action (if any) has been taken. An exception is Set_Address, which the device implements after the Status stage has completed.

# Handshake Packet

**Purpose:** the sender of the Data stage’s data indicates the status of the transfer.

**Sent by:** the receiver of the Status stage’s data packet. If the Status stage’s token packet’s PID is IN, the host sends the handshake packet; if the token packet’s PID is OUT, the device sends the data packet.

**PID type:** the device’s response may be ACK (success), NAK (busy), or STALL (the request isn’t supported or the endpoint is halted). The host’s response to a data packet received without error must be ACK.