Interrupt transfers can use data toggles to ensure that all data is received without errors. A receiver that cares only about the most recent data can ignore the data toggle.

# Isochronous Transfers

Isochronous transfers are streaming, real-time transfers that are useful when data must arrive at a constant rate, or by a specific time, and where occasional errors can be tolerated. At full speed, isochronous transfers can transfer more data per frame than interrupt transfers, but there is no provision for retransmitting data received with errors.

Examples of uses for isochronous transfers include encoded voice and music to be played in real time. But data that will eventually be consumed at a constant rate doesn’t always require an isochronous transfer. For example, a host can use a bulk transfer to send a music file to a device. After receiving the file, the device can play the music at the appropriate rate.

Nor does the data in an isochronous transfer have to be consumed at a constant rate. An isochronous transfer is a way to ensure that a large block of data gets through quickly on a busy bus, even if the data doesn’t need to transfer in real time. Unlike with bulk transfers, once an isochronous transfer begins, the host guarantees that the time will be available to send the data at a constant rate, so the completion time is predictable.

# Availability

Only full- and high-speed devices can do isochronous transfers. Devices aren’t required to support isochronous transfers but a device class may require it. For example, many audio- and video-class devices use isochronous endpoints.

# Structure

Isochronous means that the data has a fixed transfer rate, with a defined number of bytes transferring in every frame or microframe. None of the other