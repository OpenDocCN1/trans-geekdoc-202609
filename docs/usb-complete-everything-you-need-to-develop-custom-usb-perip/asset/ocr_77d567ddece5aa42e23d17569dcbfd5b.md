only thing a hub does to manage multiple speeds. High speed is 40 times faster than full speed and 320 times faster than low speed. It doesn’t make sense for the entire bus to wait while a hub exchanges low- or full-speed data with a device.

The solution is split transactions. A 2.0 host uses split transactions when communicating with a low- or full-speed device on a high-speed bus. What would be a single transaction at low or full speed usually requires two types of split transactions: one or more start-split transactions to send information to the device and one or more complete-split transactions to receive information from the device. The exception is isochronous OUT transactions, which don’t use complete-split transactions because the device has nothing to send.

Even though they require more transactions, split transactions make better use of bus time because they minimize the amount of time spent waiting for a low- or full-speed device to transfer data. The USB 2.0 host controller and the closest 2.0 hub upstream from the low- or full-speed device are entirely responsible for performing split transactions. The device and its firmware don’t have to know or care whether the host is using split transactions. The transactions at the device are identical whether the host is using split transactions or not. At the host, device drivers and application software don’t have to know or care whether the host is using split transactions because the protocol is handled at a lower level. Chapter 15 has more about how split transactions work.

# Ensuring that Transfers Are Successful

USB transfers use handshaking and error-checking to help ensure that data gets to its destination as quickly as possible and without errors.

# Handshaking

Like other interfaces, USB uses status and control, or handshaking, information to help to manage the flow of data. In hardware handshaking, dedicated lines carry the handshaking information. An example is the RTS and