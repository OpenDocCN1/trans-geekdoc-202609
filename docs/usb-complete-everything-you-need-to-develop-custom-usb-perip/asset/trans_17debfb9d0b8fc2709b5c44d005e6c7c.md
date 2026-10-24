

## 结束通信

当应用程序完成与设备的通信后，应调用 CloseHandle 关闭由 CreateFile 打开的所有句柄，如第10章所述。当使用完由 HidD_GetPreparsedData 返回的 PreparsedData 缓冲区后，应用程序应调用 HidD_FreePreparsedData。

### Visual C++

这是 HidD_FreePreparsedData 的声明：

```
BOOLEAN
    HidD_FreePreparsedData(
        IN PHIDP_PREPARSED_DATA PreparsedData
    );
```

这是调用该函数的代码：

```
HidD_FreePreparsedData(PreparsedData);
```

### Visual Basic

这是 HidD_FreePreparsedData 的声明：

```
<DllImport("hid.dll")> _
Function HidD_FreePreparsedData _
    (ByRef PreparsedData As IntPtr) _
    As Boolean
End Function
```

这是调用该函数的代码：

```
HidD_FreePreparsedData(PreparsedData)
```

## 14 适用于任意 CPU 的批量传输

第6章介绍了 FTDI 芯片公司的 FT245BM 和 FT232BM 设备控制器，它们使几乎任何带有并行或异步串行接口的 CPU 都能与 USB 主机通信。这些芯片处理枚举和其他任务，无需编写 USB 专用程序。本章介绍两个示例应用程序以及使用这些控制器进行设计的一些技巧。

### 两个项目

两个示例应用程序均与 Microchip PICMicro 16F877 微控制器接口。第一个示例使用具有异步串行接口的 FT232BM。第二个示例使用具有并行接口的 FT245BM。固件是为 microEngineering Labs 的 PicBasic Pro Basic 编译器编写的，但也可以改编为其他语言。

正如你将看到的，为这些芯片编写设备固件和主机应用程序几乎不需要 USB 知识。然而，了解 USB 可以帮助你理解这些设备的能力和限制。

### 异步串行接口

FT232BM 具有一个 USB 端口和一个可连接到外部 CPU 的异步串行接口。

### 电路

图14-1显示了一个示例电路。DLP Design 的 DLP-232M 模块包含 FT232BM 芯片、用于存储配置数据的 EEPROM 以及一个 USB 连接器。我使用 microEngineering Labs, Inc. 的 LAB-X2 板构建了该电路，该板具有用于 PICMicro 16F877 微控制器的 40 引脚 DIP 插座、一个电源稳压器和一个可访问 ’877 端口引脚的 40 引脚排针。你可以使用基于 FTDI Chip 示例原理图的几乎任何 FT232BM 电路，以及任何具有异步串行端口的 CPU。如果使用 LAB-X2 板，请从插座中取出 MAX232 芯片（因为 ’877 的串行端口引脚连接到 ’232BM 而不是它），并且如果使用硬件握手，板上的开关 S1 和 S2 将不可用。

为了向主机发送数据，’877 的固件将串行数据写入其 TX 输出，该输出连接到 DLP-232M 的 RXD 输入。该引脚又连接到 ’232BM 上的 RXD。在 RXD 接收到数据后，’232BM 将数据从其 USB 端口发送到主机。

在从主机接收到 USB 数据时，’232BM 将数据写入其 TXD 输出，该输出连接到 DLP-232M 上的 RX 以及 ’877 上的 RX 输入。微控制器的固件读取在 RX 接收到的数据。

该电路有两个可选的 LED，当 ’232BM 向 PC 发送数据或从 PC 接收数据时，它们会闪烁。

示例电路包含硬件握手的连接。当 ’232BM 和 ’877 配置为使用硬件握手时，’232BM 仅在 ’877 将 RTS# 拉低时发送数据，而 ’877 仅在 ’232BM 将 CTS# 拉低时才应发送数据。如果相应的握手信号为高电平，发送方应等待。大多数微控制器（包括 ’877）没有用于串行端口握手的专用引脚，但可以使用任何由固件监视和控制的备用端口引脚。

![](img/3955d77b6be34048e3bc722d0b15c2a9_429_0.png)

图14-1：FTDI Chip 的 FT232BM USB UART 可以与几乎任何具有异步串行端口的 CPU 接口。

如图所示，电路使用自己的 +5V 电源。要为 DLP-USB232M 使用总线电源，请将 VCC-IO、EXTVCC 和 RESET# 连接到 PORTVCC。使用总线电源的电路在主机配置 USB 设备之前，电流消耗不得超过 100 毫安，并且必须限制其在挂起状态下的电流，如第16章所述。FTDI Chip 提供了有关如何确保总线供电设备符合 USB 电源规范的信息。

### 程序代码

为与 ’232BM 进行异步串行通信而对 CPU 编程，不需要了解 USB 协议。’232BM 与设备 CPU 之间的连接是一条异步串行链路。设备 CPU 不需要知道 ’232BM 与 USB 主机之间的任何通信。程序代码将根据设备是否包含硬件 UART/USART 以及编程语言而有所不同。’877 有一个硬件 USART，在 TX 引脚上发送数据，在 RX 引脚上接收数据。当串行端口收到一个字节以及当一个字节已发送时，中断可以导致例程执行。

清单14-1演示了 PicBasic Pro 中 ’877 与 ’232BM 之间的通信。’877 读取从主机接收的一个字节，将该字节加一，然后将该字节发送回主机。对于握手，代码将一个端口位（PORTB.4）定义为 CTS 输出，将一个端口位（PORTB.5）定义为 RTS 输入。

程序将 CTS 拉低，以表示 ’877 准备好接收一个字节。CTS 连接到 ’232BM 的 RTS# 输入。在从 PC 接收到一个字节并确定 RTS# 为低电平后，’232BM 将该字节写入 ’877。

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

清单14-1：用于使 PICMicro 16F877 与 FTDI Chip FT232BM 通信的 PicBasic Pro 代码。

