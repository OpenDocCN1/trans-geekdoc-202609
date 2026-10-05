

# Arduino 基础

![](img/526b5ff9486ff530988203e0cd92330a_49_0.png)

图 4.2
Arduino Mega 板板。

# 表 4.2

| 引脚 | 描述 |
| --- | --- |
| Vin | 输入 Arduino 板的外部电压 |
| +5V | 输出调节的 5 V |
| 3.3 V | 板载 3.3 V 电源 |
| GND | 接地 |
| IOREF | 提供电压参考以选择合适的电源 |
| Serial0 | 可以通过 0(Rx) 和 1(Tx) 传输接收串口数据 |
| Serial1 | 可以通过 19(Rx) 和 18(Tx) 传输接收串口数据 |
| Serial2 | 可以通过 14(Rx) 和 16(Tx) 传输接收串口数据 |
| External Interrupts | 在低电值 2 (中断 0)、3 (中断 1)、18 (中断 5)、19 (中断 4) 和 20 (中断 2) 触发外部中断 |
| PWM | 8 位 PWM (引脚: 2-13 和 44-46) |
| SPI | 支持 SPI 通信 [10 (SS), 11 (MOSI), 13 (M)] |
| LED | 由引脚 13 驱动 |
| TWI | 支持 TWI 通信 [引脚: 20 (SDA), 21 (SCL)] |
| AREF | 模拟输入的参考电压 |
| Reset | 用于通过板重置微控制器 |

## 4.1.3 Arduino Nano

Arduino/Genu Nano 内了一个 ATmega328 微控制器。它有 8 个模拟输入、14 个数字 I/O 端口和 6 个 PWM。它具有 32 KB 闪存内存、1 KB EEPROM、2 KB SRAM，工作频率为 16 MHz。图 4.3 显示了 Arduino Nano（表 4.3 和表 4.4）。

| 引脚 | 描述 |
| --- | --- |
| Vin | 输入板的外部电压 |
| +5 V | 输出为 +5 V |
| 3.3 V | 板载 3.3 V 电源 |
| GND | 接地 |
| IORE | 提供电压参考帮助选择合适的电源 |
| Serial | 可以通过 0(Rx) 和 1(Tx) 传输接收串口数据 |
| External Interrupts | 在低值（引脚 2 和 3）触发中断 |
| PWM | 8 位 PWM (3, 5, 6, 9, 10, 11) |
| SPI | 支持与 10 (SS), 11 (MOSI), 12 (MISO) 和 13 (SCK) 的 SPI 通信 |
| LED | 引脚 13 双线接口驱动 LED |
| I2C | 支持双线接口 [A4 (SDA) 和 A5 (SCL)] |
| AREF | 模拟输入的参考电压 |
| Reset | 用于重置板载微控制器 |

# Arduino 基础

表 4.4
若干 Arduino 板板对比表

| 名称 | 处理器 | CPU 速度 | 工作输入电压 | 数字 IO/PWM | 模拟输入/输出 | UART | 闪存 [kB] |
| --- | --- | --- | --- | --- | --- | --- | --- |
| LilyPad | ATmega168V / ATmega328P | 8 MHz | 2.4-5.5 V / 2.4-5.5 V | 14/6 | 6/0 | — | 16 |
| Mega 2560 | ATmega2560 | 16 MHz | 5 V-12 V | 54/15 | 16/0 | — | 256 |
| Micro | ATmega324U | 16 MHz | 5 V-12 V | 20/4 | 12/0 | 1 | 32 |
| Uno | ATmega328P | 16 MHz | 5 V-12 V | 14/6 | 6/0 | 1 | 32 |
| Leonardo | ATmega324U | 16 MHz | 5 V-12 V | 20/4 | 12/0 | 1 | 32 |
| Yun | ATmega328P AR9331 Linux | 400 MHz | 5 V-12 V | 14/4 | 6/0 | — | 32 |
| Ethernet | | 16 MHz | | 3.3 V | 3/2 | 1/0 | — | 8 |
| Gamma | ATiny85 | 8 MHz | 4-16 V | | | — | 8 |
| MKRZero | SAMD21 Cortex-M0+ 32 位低功耗 ARM MCU | 48 MHz | 3.3 V | | 22/12 | 4 (ADC 8/10/12位)/ (DAC 10 位) | 1 | 256 |

## 4.2 Arduino IDE

Arduino 集成开发环境 (IDE) 是一款开源软件，它可以轻松编写代码并上传到板上。

### 4.2.1 安装 Arduino IDE 并打开窗口的步骤

**步骤 1：安装 Arduino IDE 并打开窗口**
开始之前，安装 Arduino IDE。图 4.4 显示 Arduino IDE 窗口。

**步骤 2：选择 Arduino 板**
Arduino 有许多版本，如 UNO、MEGA、NANO 等。在启动项目之前，根据要求找到合适的板。在 Arduino IDE 中，点击“Tool”（工具）然后选择“Board”。图 4.5 显示板的选择。

**步骤 3：编写并编译程序**
在 Arduino IDE 中编写程序。然后点击“编译”。图 4.6 显示编译程序的窗口。

```cpp
void setup() {
  // 在此处放置设置代码，运行一次
}

void loop() {
  // 在此处放置主代码，循环运行
}
```

**步骤 4：将 Arduino 连接到 PC**
使用 USB 线将 Arduino 连接到 PC 的 USB 口。每个 Arduino 板都有不同的串口（COM2, COM4 等），因此需要在 IDE 中重新配置端口。检查 Arduino 连接的端口，点击“Tool”然后选择“Manager”（管理器）；管理器窗口如图 4.7 所示。

**步骤 5：将程序上传到 Arduino 板**
将程序上传到 Arduino 板。图 4.9 显示如何上传程序。

# 设备管理器
![](img/526b5ff9486ff530988203e0cd92330a_54_0.png)

图 4.7
检查 Arduino 端口的窗口。

![](img/526b5ff9486ff530988203e0cd92330a_54_1.png)

图 4.8
板的串口。

```cpp
void setup() {
  // 在此处放置设置代码，运行一次
}

void loop() {
  // 在此处放置主代码，循环运行
}
```

![](img/526b5ff9486ff530988203e0cd92330a_55_0.png)

图 4.9
上传程序的窗口。

## 4.3 Arduino 基础命令

- pinMode(x, OUTPUT); 将引脚 x 设置为输出引脚，x 为数字引脚
- digitalWrite(x, HIGH); 将引脚 x 设置为高电平，x 为数字引脚
- pinMode(x, INPUT); 将引脚 x 设置为输入引脚，x 为数字引脚
- digitalRead(digital pin); 读取数字引脚，如 13 或 12 或 11 等
- analogRead(analog pin); 读取模拟引脚，如 A0 或 A1 或 A2 等

## 4.4 LCD 命令

- lcd.begin(1, 2); 初始化 16*2 或 20*4 LCD
- lcd.print("RAJESH"); 在 LCD 上打印字符串“RAJESH”
- lcd.setCursor(x, y); 在指定位置设置 LCD 光标，x 为列数，y 为行数
- lcd.print(LPU); 在 LCD 上打印整数 LPU
- lcd.Clear(); 清除 LCD 内容

## 4.5 串口通信命令

- Serial.begin(baud); 初始化串口通信，将波特率设置为 600/1200/2400/4800/9600
- Serial.print("RAJESH"); 在 Tx 线上按定义的波特率打印固定字符串
- Serial.println("RAJESH"); 在 Tx 线上按定义的波特率打印固定字符串
- Serial.print(LPU); 在 Tx 线上按定义的波特率打印整数字符串
- Serial.Write(BYTE); 在 Tx 线上传输一个字节
- Serial.read(); 从 Rx 线读取字节串口

## 4.6 玩 LED 和 Arduino

发光二极管（LED)是一种可以用作指示器的设备。LED 有两个端子：阳极和阴极。LED 有不同的颜色。图 4.10 显示了 LED。

![](img/526b5ff9486ff530988203e0cd92330a_56_0.png)

图 4.10
发光二极管。

不同的颜色代表不同的状态。LED 的颜色由于不同化合物在可见光谱特定区域发射光。

要理解 LED 的工作原理，将 LED 的阳极连接到 Arduino 的第 4 引脚，阴极连接到地。将 4.4.1 节描述的草图（sketch）上传到 Arduino 并观察 LED 的闪烁。

图 4.11 显示了 Arduino 与 LED 接口电路图。

![](img/526b5ff9486ff530988203e0cd92330a_57_0.png)

调节器 7812
Vcc=+5V

![](img/526b5ff9486ff530988203e0cd92330a_57_1.png)

图 4.11
Arduino 与 LED 接口电路图。

