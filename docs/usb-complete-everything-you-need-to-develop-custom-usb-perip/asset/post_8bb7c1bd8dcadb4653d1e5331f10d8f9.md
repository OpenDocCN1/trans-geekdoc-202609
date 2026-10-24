
## Closing Communications

When finished communicating with a device, the application should call CloseHandle to close any handles opened by CreateFile, as described in Chapter 10. When finished using the PreparsedData buffer returned by HidD_GetPreparsedData, the application should call HidD_FreePreparsedData.

### Visual C++

This is the declaration for HidD_FreePreparsedData:

```
BOOLEAN
    HidD_FreePreparsedData(
        IN PHIDP_PREPARSED_DATA PreparsedData
    );
```

This is the code to call the function:

```
HidD_FreePreparsedData(PreparsedData);
```

### Visual Basic

This is the declaration for HidD_FreePreparsedData:

```
<DllImport("hid.dll")> _
Function HidD_FreePreparsedData _
    (ByRef PreparsedData As IntPtr) _
    As Boolean
End Function
```

This is the code to call the function:

```
HidD_FreePreparsedData(PreparsedData)
```

## 14 Bulk Transfers for Any CPU

Chapter 6 introduced FTDI Chip's FT245BM and FT232BM device controllers, which enable just about any CPU with a parallel or asynchronous serial interface to communicate with a USB host. The chips handle enumeration and other tasks with no USB-specific programming required. This chapter presents two example applications plus some tips on designing with these controllers.

### Two Projects

Both example applications interface to Microchip PICMicro 16F877 microcontrollers. The first example uses an FT232BM, which has an asynchronous serial interface. The second example uses an FT245BM, which has a parallel interface. The firmware is written for microEngineering Labs’ PicBasic Pro Basic compiler, but can be adapted to other languages.

As you’ll see, writing device firmware and host applications for these chips requires very little knowledge of USB. An understanding of USB can help you understand the devices’ abilities and limits, however.

### Asynchronous Serial Interface

The FT232BM has a USB port and an asynchronous serial interface that can connect to an external CPU.

### The Circuit

Figure 14-1 shows an example circuit. A DLP Design’s DLP-232M module contains the FT232BM chip, an EEPROM for storing configuration data, and a USB connector. I built the circuit using microEngineering Labs, Inc.’s LAB-X2 board, which has a 40-pin DIP socket for the PICMicro 16F877 microcontroller, a power-supply regulator, and a 40-pin header that provides access to the ’877’s port pins. You can use just about any FT232BM circuit based on FTDI Chip’s example schematic and any CPU with an asynchronous serial port. If you use the LAB-X2 board, remove the MAX232 chip from its socket (because the ’877’s serial-port pins connect to the ’232BM instead), and switches S1 and S2 on the board won’t be available if you use hardware handshaking.

To send data to the host computer, the ’877’s firmware writes serial data to its TX output, which connects to the DLP-232M’s RXD input. This pin in turn connects to RXD on the ’232BM. On receiving data at RXD, the ’232BM sends the data out its USB port to the host computer.

On receiving USB data from the host, the ’232BM writes the data to its TXD output, which connects to RX on the DLP-232M and to the RX input on the ’877. The microcontroller’s firmware reads the data received at RX.

The circuit has two optional LEDs that flash when the ’232BM is sending data to the PC or receiving data from the PC.

The example circuit includes connections for hardware handshaking. With the ’232BM and the ’877 configured to use hardware handshaking, the ’232BM transmits only when the ’877 has brought RTS# low, and the ’877 should transmit only when the ’232BM has brought CTS# low. If the corresponding handshaking signal is high, the sender should wait. Most microcontrollers (including the ’877) don't have dedicated pins for serial-port handshaking but can use any spare port pins monitored and controlled by firmware.

![](img/3955d77b6be34048e3bc722d0b15c2a9_429_0.png)

Figure 14-1: FTDI Chip’s FT232BM USB UART can interface to just about any CPU with an asynchronous serial port.

As shown, the circuits use their own +5V power supply. To use bus power for the DLP-USB232M, connect VCC-IO, EXTVCC, and RESET# to PORTVCC. Circuits that use bus power must draw no more than 100 milliamperes until the host configures the USB device and must limit their current in the Suspend state, as described in Chapter 16. FTDI Chip provides information on how to ensure that a bus-powered device meets USB's power specifications.

### Program Code

Programming a CPU for asynchronous serial communications with a '232BM requires no knowledge of USB protocols. The link between the '232BM and the device's CPU is an asynchronous serial link. The device's CPU doesn't have to know anything about the communications between the '232BM and the USB host. The program code will vary depending on whether the device contains a hardware UART/USART and on the programming language. The '877 has a hardware USART that transmits on the TX pin and receives on the RX pin. An interrupt can cause a routine to execute when a byte has arrived at the serial port and when a byte has transmitted.

Listing 14-1 demonstrates communications between an '877 and '232BM in PicBasic Pro. The '877 reads a byte received from the host, increments the byte, and sends the byte back to the host. For handshaking, the code defines one port bit (PORTB.4) as the CTS output and one port bit (PORTB.5) as the RTS input.

The program brings CTS low to indicate that the '877 is ready to receive a byte. CTS connects to the '232BM's RTS# input. On receiving a byte from the PC and determining that RTS# is low, the '232BM writes the byte to the '877.

```basic
' Registers that relate to serial communications:

' Automatically clear any receive overflow errors.
DEFINE HSER_CLRERR 1

' Set the baud rate.
DEFINE HSER_BAUD 2400

' Enable the serial receiver.
DEFINE HSER_RCSTA 90h

' Enable the serial transmitter.
DEFINE HSER_TXSTA 20h

' Handshaking bits. Use any spare port bits.
CTS                 VAR    PORTB.4
RTS                 VAR    PORTB.5

error               VAR    BYTE
byte_was_received   VAR    BIT
serial_in           VAR    BYTE
serial_out          VAR    BYTE

' The CTS output connects to the '232BM's RTS# input.
' The RTS input connects to the '232BM's CTS# output.
OUTPUT CTS
INPUT  RTS

' On detecting a hardware interrupt, jump to interrupt_service.
ON INTERRUPT GOTO interrupt_service

' Enable global and peripheral interrupts.
INTCON = %11000000

' Enable the serial receive peripheral interrupt.
PIE1 = %00100000

' Tell the '232BM it's OK to send a byte.
byte_was_received = 0
CTS = 0
```

```basic
' The main program loop.
loop:

    ' Find out if a serial byte was received.
    if byte_was_received = 1 then

        ' Find out if the '232BM is ready to receive a byte.
        if RTS = 0 then

            ' Increment the received byte.
            If (serial_in = 255) then
                serial_out = 0
            else
                serial_out = (serial_in + 1)
            endif

            ' Write the incremented byte to the serial port.
            HSEROUT [serial_out]

            ' Prepare to receive another byte.
            byte_was_received = 0
            CTS = 0
        endif
    endif

GOTO loop
```

```basic
' Disable interrupt processing in the interrupt-service routine.
DISABLE INTERRUPT
interrupt_service:

    ' This routine executes on detecting a hardware interrupt.

    ' Find out if a byte was received on the serial port.
    if ((PIR1 & %00100000) = %00100000) then

        ' Set CTS high to prevent receiving more serial data.
        CTS = 1

        ' Find out if there was a framing error.
        error = (RCSTA & %0000000100)

        ' Store the byte in serial_in.
        ' This also clears any framing-error flag.
        HSERIN [serial_in]

        ' If a byte was received without error,
        ' set byte_was_received = 1 to tell the main program loop
        ' that it should send a byte to the serial port.
        ' Otherwise, set CTS = 0 to enable receiving another byte.

        if error = 0 then
            byte_was_received = 1
        else
            CTS = 0
        endif
    endif

RESUME

' Re-enable interrupt processing.
ENABLE INTERRUPT
```

Listing 14-1: PicBasic Pro code to enable a PICMicro 16F877 to communicate with an FTDI Chip FT232BM.
