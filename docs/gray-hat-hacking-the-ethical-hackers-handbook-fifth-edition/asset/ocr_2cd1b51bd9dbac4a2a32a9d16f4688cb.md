section at the end of this chapter.

Back in its heyday, RS-232 was the standard communication port in personal computers; however, due to its low transmission speed (among other factors), it was eventually replaced by USB technology. However, in the IoT world, it is still a very common communication protocol used mainly to provide console access to medical, networking, entertainment, and industrial devices.

RS-232 can transmit or receive data synchronously and asynchronously, and it can operate in full duplex mode, exchanging data in both directions concurrenctly. The data is transmitted via voltage levels where a logical 1 (mark) is between –15 and –3 VDC and a logic 0 (space) is between +3 and +15 VDC. Figure 25-1 presents a typical example of an RS-232 waveform; the transmission begins with a “start” bit (logic 0), followed by the data bits enclosed between the least significant bit (LSB) and the most significant bit (MSB), and finishes with a “stop” bit (logic 1) to signal the end of the data. Although it’s not reflected in the figure, a parity bit can also be used or discarded in order to validate data integrity. Last but not least is the baud rate, which measures the number of bits transferred per second (bps). The most common values are standardized at 9600, 38400, 19200, 57600, and 115200 bps.

![](bbox=[0.12, 0.44, 0.88, 0.535])

Figure 25-1 RS-232 waveform example

# RS-232 Pinout

The most common RS-232 connectors are the DB-9 and DB-25. In this chapter, we focus on the DB-9 because it is the most common connector on IoT devices. Before the pinout details are listed, it is important for you to understand how these devices are classified, because a pinout is defined based on the device classification. There are two types of RS-232 devices: data terminal equipment (DTE) and data circuit-terminating equipment (DCE). Commonly, a DTE is tied to a computer and a DCE to a modem. However, modems are not so common anymore. So, the best way to identify whether you are dealing with a DCE or DTE is by measuring the voltage in the transmit pin, which in a DB-9 can be either pin 3 or pin 2. If you get a voltage between –15 and –3 VDC in pin 3, the device is a DTE. If you get that voltage on pin 2, you are dealing with a DCE device.

Why is it important to identify whether a device is a DCE or DTE? Because the pinout is different, as shown in Figure 25-2. Pay attention to the differences between pins 2 and 3, because a wrong connection will cause null communication with the serial port.