and a Status stage. Each stage consists of one or more transactions that each contain a token phase, data phase, and handshake phase. Each phase transfers a token, data, or handshake packet.

As described in Chapter 2, low-speed transfers also use PRE packets, high-speed transfers use the PING protocol, and some low- and full-speed transfers use split transactions. Each packet also contains error-checking bits. Application programmers, device-driver writers, and firmware developers don’t have to worry about PREs, PINGs, error-checking, or split transactions because the host controller, hubs, and device hardware handle these protocols.

# Setup Stage

The Setup stage consists of a Setup transaction, which has two purposes: to identify the transfer as a control transfer and to transmit the request and other information that the device will need to complete the request.

Devices must accept and acknowledge every Setup transaction. A device that is in the middle of another control transfer must abandon that transfer and acknowledge the new Setup transaction. Here are more details about each of the packets in the Setup stage’s transaction:

# Token Packet

**Purpose:** identifies the receiver and identifies the transaction as a Setup transaction.

**Sent by:** the host.

**PID:** SETUP

**Additional Contents:** the device and endpoint addresses.

# Data Packet

**Purpose:** transmits the request and related information.

**Sent by:** the host.

**PID:** DATA0