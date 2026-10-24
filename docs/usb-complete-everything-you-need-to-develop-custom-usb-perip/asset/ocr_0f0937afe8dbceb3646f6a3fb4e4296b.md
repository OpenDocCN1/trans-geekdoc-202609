eventually gives up on receiving multiple NAKs. Bulk transfers use data toggles to ensure that no data is lost.

# Interrupt Transfers

Interrupt transfers are useful when data has to transfer within a specific amount of time. Typical applications include keyboards, pointing devices, game controllers, and hub status reports. Users don’t want a noticeable delay between pressing a key or moving a mouse and seeing the result on screen. A hub needs to report the attachment or removal of devices promptly. Low-speed devices, which support only control and interrupt transfers, are likely to use interrupt transfers for generic data.

At low and full speeds, the bandwidth available for an interrupt endpoint is limited, but high speed loosens the limits and enables an interrupt endpoint to transfer almost 400 times as much data as full speed per unit of time.

The name interrupt transfer suggests that a device might spontaneously send data that triggers a hardware interrupt on the host. But interrupt transfers, like all other USB transfers, occur only when the host polls a device. The transfers are interrupt-like, however, because they guarantee that the host requests or sends data with minimal delay.

# Availability

All three speeds allow interrupt transfers. Devices aren’t required to support interrupt transfers, but a device class may require it. For example, a HID-class device must support interrupt IN transfers for sending data to the host.

# Structure

An interrupt transfer consists of one or more IN transactions or one or more OUT transactions. On the bus, interrupt transactions are identical to bulk transactions (Figure 3-3). The only difference is the scheduling. An interrupt transfer is one-way; the transactions must be all IN transactions, or all