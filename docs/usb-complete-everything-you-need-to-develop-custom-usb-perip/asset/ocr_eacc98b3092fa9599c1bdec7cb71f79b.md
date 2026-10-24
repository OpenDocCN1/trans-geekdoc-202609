bytes the host wants to transfer. For a device-to-host transfer, wLength is a maximum, and the device may return this number of bytes or fewer. If the wLength field is zero, there is no Data stage.

# Handshake Packet

Purpose: transmits the device’s acknowledgement.

Sent by: the device.

PID: ACK.

Additional Contents: none. The handshake packet consists of the PID alone.

Comments: If the device detects an error in the received Setup or Data packet, the device returns no handshake. The device’s hardware typically handles the error checking and sending of the ACK, with no programming required.

# Data Stage

When a control transfer contains a Data stage, the stage consists of one or more IN or OUT transactions. The device descriptor specifies the maximum number of data bytes in a transaction at Endpoint 0.

When the Data stage uses IN transactions, the device sends data to the host. An example is the Get_Descriptor request, where the device sends a requested descriptor to the host. When the Data stage uses OUT transactions, the host sends data to the device. An example is HID-class request Set_Report, where the host sends a report to a device. If the wLength field in the Setup transaction is zero, there is no Data stage. For example, in the Set_Configuration request, the host passes a configuration value to the peripheral in the wValue field of the Setup stage’s data packet, so there’s no need for a Data stage.

If all of the data can’t fit in one packet, the stage uses multiple transactions. The number of transactions required to send all of the data for a transfer equals the value in the Setup transaction’s wLength field divided by the wMaxPacketSize value in the endpoint’s descriptor, rounded up. For exam-