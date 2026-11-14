```
XpL0iT:~$ lsusb
Bus 001 Device 004: ID 0403:6001 Future Technology Devices International, Ltd
FT232 USB-Serial (UART) IC
Bus 001 Device 002: ID 80ee:0021 VirtualBox USB Tablet
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Now that you know the USB device is connected to your Ubuntu box, there are many ways to interact with it, depending on the client you are using. Here are three ways to identify your USB:

```
@XpL0iT:~$ ls /dev/ttyUSB0
@XpL0iT:~$ ls /dev/serial/by-path/pci-0000\:00\:06.0-usb-0\:2\:1.0-port0
@XpL0iT:~$ ls /dev/serial/by-id/usb-FTDI_FT232R_USB_UART_A104WBLI-if00-port0
```

Looks like everything is set for your production test. However, you still do not know the serial communication configuration (in other words, the values of the baud rate as well as the parity and stop bits). There are three ways to approach this. The easiest method is to look for technical manuals about the device and try to find those parameters. The second option is to brute-force the values until you find the right ones. This should be fast because the available baud rates are around 5. The final option is to use a logic analyzer. You can think of this device as a sniffer for the serial port. It identifies pulses being sent and measures what is called the “frequency between those pulses,” which eventually can help you to identify the baud rate. It also helps to identify the serial port’s transmit and receive pins, like in this exercise. If you noticed, only two cables from the RJ-45 connector were used for this purpose. The Saleae logic analyzer is recommended for this task, although it is expensive. For this exercise, a logic analyzer was used to identify the parameters.

Let’s create a quick script to read from the serial port and see what you get. You can use Python’s “serial” module for this. Here is an example of a serial port reading. You can see that we are using the “/dev/ttyUSB0” device to interact with the port and are using a baud rate of 57600, which is taken from the logic analyzer: