# A Transfer Type for Every Purpose

some high-speed transfers and for low- and full-speed transfers with 2.0 hubs on high-speed buses.

In the Setup stage, the host begins a Setup transaction by sending information about the request. The token packet contains a PID that identifies the transfer as a control transfer. The data packet contains information about the request, including the request number, whether or not the transfer has a Data stage, and if so, in which direction the data will travel.

The USB 2.0 specification defines 11 standard requests. Successful enumeration requires specific responses to some requests, such as the request that sets a device’s address. For other requests, a device can return a code that indicates that the request isn’t supported. A specific class may require a device to support class-specific requests, and any device may support vendor-specific requests defined by a vendor-specific driver.

When present, the Data stage consists of one or more Data transactions, which may be IN or OUT transactions. Depending on the request, the host or peripheral may be the source of these transactions, but all data packets in this stage are in the same direction.

As described in Chapter 2, if a high-speed control Write transfer has more than one data packet in the Data stage, and if the device returns NYET after receiving a data packet, the host may use the PING protocol before sending the next data packet.

The Status stage consists of one IN or OUT transaction, also called the status transaction. In the Status stage, the device reports the success or failure of the previous stages. The source of the Status stage’s data packet is the receiver of the data in the Data stage. When there is no Data stage, the device sends the Status stage’s data packet. The data or handshake packet sent by the device in the Status stage contains a code that indicates the success or failure of the request.

If a host is performing a control transfer with a low- or full-speed device on a high-speed bus, the host uses the split transactions introduced in Chapter 2 for all of the transfer’s transactions. To the device, the transaction is no different than a transaction with a 1.x host. The device’s hub carries out the transaction with the device and reports back to the host when requested.