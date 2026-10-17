
- 将 Arduino 数字引脚 `GND` 连接到 LCD 的 `RW` 引(5)。

- 将 Arduino 数字引脚 `12` 连接到 LCD 的 `E` 引(6)。

- 将 Arduino 数字引脚 `11` 连接到 LCD 的 `D4` 引(11)。

- 将 Arduino 数字引脚 `10` 连接到 LCD 的 `D5` 引(12)。

- 将 Arduino 数字引脚 `9` 连接到 LCD 的 `D6` 引(13)。

- 将 Arduino 数字引脚 `8` 连接到 LCD 的 `D7` 引(14)。

### 6.4.1.2 Sketch

```cpp
#include<LiquidCrystal.h> // 包含 LCD 库
LiquidCrystal lcd(13, 12, 11, 10, 8); // 将 LCD 引脚 RS, E, D4, D5, D6,
D7 连接到给定的引脚
int MPIN1=7; // 将引脚 7 分配为 MPIN1
int MPIN2=6; // 将引脚 6 分配为 MPIN2
int MPIN3=5; // 将引脚 5 分配为 MPIN3
int MPIN4=4; // 将引脚 4 分配为 MPIN4
```

```cpp
void setup()
{
    pinMode(MPIN1, OUTPUT); // 将 MPIN1 设置为输出
    pinMode(MPIN2, OUTPUT); // 将 MPIN2 设置为输出
    pinMode(MPIN3, OUTPUT); // 将 MPIN3 设置为输出
    pinMode(MPIN4, OUTPUT); // 将 MPIN4 设置为输出
    lcd.begin(20,4); // 初始化 LCD
    lcd.setCursor(0, 0); // 在 LCD 上设置光标
    lcd.print("DC Motor direction"); // 在 LCD 上打印字符串
    lcd.setCursor(0, 1); // 在 LCD 上设置光标
    lcd.print("control system..."); // 在 LCD 上打印字符串
    delay(1000); // 延迟 1000
    lcd.clear();
}

void loop()
{
    digitalWrite(MPIN1, HIGH);
    digitalWrite(MPIN2, LOW);
    digitalWrite(MPIN3, LOW);
    digitalWrite(MPIN4, LOW);
    lcd.setCursor(0, 0);
    lcd.print("CLOCKWISE");
    delay(2000);
    lcd.clear();

    digitalWrite(MPIN1, LOW);
    digitalWrite(MPIN2, HIGH);
    digitalWrite(MPIN3, LOW);
    digitalWrite(MPIN4, LOW);
    lcd.setCursor(0, 0);
    lcd.print("ANTI-CLOCKWISE");
    delay(2000);
    lcd.clear();

    digitalWrite(MPIN1, LOW);
    digitalWrite(MPIN2, LOW);
    digitalWrite(MPIN3, HIGH);
    digitalWrite(MPIN4, LOW);
    lcd.setCursor(0, 0);
    lcd.print("LEFT");
    delay(2000);
    lcd.clear();

    digitalWrite(MPIN1, LOW);
    digitalWrite(MPIN2, LOW);
    digitalWrite(MPIN3, LOW);
    digitalWrite(MPIN4, HIGH);
    lcd.setCursor(0, 0);
    lcd.print("RIGHT");
    delay(2000);
    lcd.clear();
}
```

## 6.4.2 伺服电机

伺服电机是一种用于精确位置控制的旋转执行器。这是一个闭环操作。带有金属齿轮的标准扭矩可以提供 360° 旋转。图 6.8 显示了伺服电机与 Arduino 接口的框图。它还需要一个反馈传感器。

![](img/526b5ff9486ff530988203e0cd92330a_129_0.png)

图 6.8

与 Arduino 接口的框图。

### 6.4.2.1 电路图

按照图 6.9 所示连接组件以检查伺服电机的工作情况。

#### 伺服连接

- 将 Arduino `GND` 连接到伺服的极。

- 将 Arduino `+5 V` 连接到伺服的正极。

- 将 Arduino 引脚(3) 连接到伺服的 `PWM` 引脚。

#### POT 连接

- 将 Arduino `GND` 连接到 `POT` 的地。

- 将 Arduino `+5 V` 连接到 `POT` 的正极。

- 将 Arduino `A0` 连接到 `POT` 的数据输出引脚。

![](img/526b5ff9486ff530988203e0cd92330a_130_0.png)

图 6.9

伺服电机与 Arduino 接口的电路图。

#### 树莓派与 Arduino

```
void setup()
{
  myservo.attach(3); // 将引脚9上的舵服器连接到舵器对象
lcd.begin(20
```

![](img/526b5ff9486ff530988203e0cd92330a_132_0.png)

## 7 使用 Pyfirmata 进行 Python 与 Arduino

### 7.1 Python 与 Arduino

Arduino 是一个用于构建硬件和软件环境的开源平台。Arduino 为手工爱好者和电子爱好者提供了无限可能。

树莓派是一台功能完整的计算机，可以执行类似于台式电脑的任务。它为编写代码和设计电子电路提供了平台，从创建一个 Web 服务器到创建一个用于复古游戏的游戏机。

Arduino 不懂 Python，因此使用 Firmata 和 Pyfirmata 协议通过树莓派使用 Python 进行通信。Pyfirmata 是树莓派访问 Arduino 的协议。程序将在树莓派的接口上使用 Python 编写。Firmata 是一种 Arduino 通过 Python 与树莓派接口的协议，用于访问连接到 Arduino 的传感器。

要向 Arduino 安装 Firmata，请将其连接到树莓派的 USB 接口以通信并为 Arduino 电。接下来，在 Arduino 上安装 Firmata  sketch（程序），这需要打开 Arduino IDE。在 `File→Examples→Firmata→StandardFirmata` 中找到 Firmata sketch，并将其上传到 Arduino 板。一旦安装了 Firmata，Arduino 将等待来自树莓派的通信。

下一步是在树莓派上安装 Pyfirmata。为此，只需在树莓派上运行以下终端命令：

```bash
$ sudo apt-get install git
$ sudo git clone https://github.com/tino/pyfirmata.git
$ cd pyfirmata
$ sudo python setup.py install
```

### 7.2 使用 Python 控制 Arduino

使用“USB 标准 A 型”接口连接 Arduino 与树莓派。现在通过运行 `ls -l /dev/tty*` 来检查 Arduino 的 USB 地址。在我的树莓派上，它被列为 `/dev/ttyUSB0`（请记住这个值以备后用）。

从 Pyfirmata 模块导入 `Arduino` 和 `util` 类，以便在树莓派的 Python 脚本中控制 Arduino。完成后，借助 USB 地址创建上一步找到的对象。

```python
>>> import Arduino
>>> board = Arduino('/dev/ttyUSB0')
```

### 7.3 玩转 LED

项目的目标是通过树莓派使用 Python 控制 Arduino 的数字输出。要构建此项目，请将 LED 连接到 Arduino 的数字引脚，并编写一个短的 Python 程序使其闪烁。图 7.1 显示了 LED 接口的电路图。该系统由树莓派 3、一个 Arduino Uno、一个电源以及连接到 Arduino 引脚6 和引脚7 的两个 LED 组成。程序被编写为在延迟后让 LED 闪烁。

![](img/526b5ff9486ff530988203e0cd92330a_134_0.png)

图 7.1

LED 接口电路图。

### 7.3.1 代码示例

```python
import pyfirmata # 导入 pyfirmata 库
import time as wait # 导入 pyfirmata 库
board = pyfirmata.Arduino('/dev/ttyUSB0')# 定义 Arduino 的串口端口
red_pin = board.pin(d:7)# 指定数字引脚 7 为输出
green_pin = board.pin(d:6)# 指定数字引脚 6 为输出

while True:
    无限 循环
        red_pin.write(1)## 在引脚 7 上写入 '1'
        green_pin.write(1)## 在引脚 6 上写入 '1'
        wait.sleep(0.5)# 延迟 0.5 秒
        red_pin.write(0)## 在引脚 7 上写入 '0'
        green_pin.write(0)## 在引脚 6 上写入 '0'
        wait.sleep(0.5)# 延迟 0.5 秒
```

### 7.4 使用 Pyfirmata 读取 Arduino 数字输入

目标是通过 Python 在树莓派上读取 Arduino 的数字引脚。使用 Pyfirmata 读取 Arduino 上的数字输入。示例所需的组件是 Arduino Uno、1 kΩ 电阻和一个推动开关或按钮（作为传感器）。开关可以以两种方式连接：拉低和上拉。Arduino 数字引脚的输出通常为“LOW”（低电平），数字传感器有两种输出配置：低电平“LOW”和高电平“HIGH”。拉低配置用于数字引脚通常为“LOW”，在读取时变为“HIGH”的情况。这用于在事件发生时具有高电平“HIGH”的传感器；否则输出为“LOW”。上拉配置用于正常输出为“HIGH”、在事件发生时变为“LOW”的传感器。程序中需要将数字引脚激活为“HIGH”，以便读取传感器。图 7.2 显示了拉低电路图，图 7.3 显示了上拉电路图。

正如本文第二 节所讨论的那样，使用 Pyfirmata 协议通过树莓派读取 Arduino 的输入引脚。它使用迭代器（iterator）的概念来监控 Arduino 引脚。迭代器管理 Arduino 引脚的读取。

```python
import pyfmata # 导入 pyfirmata 库
import time as wait # 导入 pyfirmata 库
board = pyfmata.Arduino('/dev/ttyUSB0')# 定义 Arduino 的串口端口
red_pin = board.pin(d:7)# 指定数字引脚 7 为输出
green_pin = board.pin(d:6)# 指定数字引脚 6 为输出

while True:
    无限 循环
        red_pin.write(1)## 在引脚 7 上写入 '1'
        green_pin.write(1)## 在引脚 6 上写入 '1'
        wait.sleep(0.5)# 延迟 0.5 秒
        red_pin.write(0)## 在引脚 7 上写入 '0'
        green_pin.write(0)## 在引脚 6 上写入 '0'
        wait.sleep(0.5)# 延迟 0.5 秒
```

![](img/526b5ff9486ff530988203e0cd92330a_136_0.png)

图 7.2

拉低电路图。

![](img/526b5ff9486ff530988203e0cd92330a_137_0.png)

图 7.3

上拉电路图。

### 7.5.1 读取“低电”火焰传感器程序

```python
import pyfirmata # 导入 pyfirmata 库
import time as time # 导入 time 库
```

board = pyfirmata.Arduino('/dev/ttyUSB0') # 定义 Arduino 端口

flame_pin = board.get_pin('d:6') # 设置引脚 6 为输入

indicator_pin = board.get_pin('d:7') # 设置引脚 7 为输出

it = pyfirmata.util.Iterator(board) # 使用迭代器

it.start() # 迭代器

flame_pin.enable_reporting() # 输入

while True: # 无限循环

    flame_state = board.pin.read() # 读取数字输入

    if flame_state == False: # 检查状态

        print('无障碍') # 在终端上打印

        indicator_pin.write(1) # 向引脚 7 写入 1

        time.sleep(0.2) # 等待 0.2 秒

else:

        print('发现障碍') # 在终端上打印

        indicator_pin.write(0) # 向引脚 7 写入 0

        time.sleep(0.2) # 等待 0.2 秒

### 7.6 使用 Pyfirmata 读取模拟输入

电位器用于演示使用 Pyfirmata 读取模拟传感器。连接到 Arduino 的 `A0` 引脚（图 7.5）。当引脚配置为模拟输入时，程序开始向串口发送数据。如果数据没有被妥善管理，会导致溢出；这种情况可以通过 Pyfirmata 程序处理。

Pyfirmata 库具有报告和迭代器方法来解决这个问题。`enable_reporting()` 方法用于设置输入报告。在引脚上执行读取操作之前：

```python
board.analog[3].enable_reporting()
```

一旦读取完成，将引脚设置为禁用报告：

```python
from pyfirmata import Arduino, util
# 设置 Arduino
port = 'COM3'
board = Arduino(port)
time.sleep(5)
it = util.Iterator(board) # 迭代器以避免串口溢出
it.start()
board.analog[3].enable_reporting()
```

#### 7.6.1 示例

### 树莓派和 Arduino 的物联网

![](img/526b5ff9486ff530988203e0cd92330a_140.png)

图 7.5 电位器接线图

在主循环中使用迭代器读取模拟引脚。该类在 Pyfirmata 的 `util` 模块中定义：

```python
import pyfirmata # 导入 pyfirmata 库
import time as time # 导入 time 库
board = pyfirmata.Arduino('/dev/ttyUSB0') # 定义 Arduino 端口
POT_pin = board.get_pin('a:0:i') # 分配 A0 引脚为输入
it = pyfirmata.util.Iterator(board) # 使用迭代器
it.start()
while True: # 无限循环
    POT_reading = POT_pin.read() # 读取模拟引脚
    if POT_reading != None: # 检查条件
        POT_voltage = POT_reading * 5.0 # 将电平转换为电压
        print("POT_reading=%f POT_voltage=%fV" % (POT_reading, POT_voltage)) # 在 终端上打印值
        time.sleep(1) # 等待 1 秒
else:
    print("未获取读取") # 在终端上打印
    time.sleep(1) # 等待 1 秒
```

### 7.7 使用 Pyfirmata 读取温度传感器

LM35 系列传感器的输出电压与摄氏温度成正比。LM35 设备不需要任何校准或裁剪即可在室温提供 ±4°C 的精度，传感范围为 -55°C 到 150°C。LM35 从电源抽取 60µA 电流。LM35 系列提供密封 TO-92 封装，而 LM35C、LM3CA 和 LM35D 提供塑料 TO-92 封装。图 7.6 显示 LM35 的接线图。LM35 的输出连接到 Arduino 的 `A0` 引脚。

![](img/526b5ff9486ff530988203e0cd9233a_141.png)

图 7.6 LM35 接线图

#### 7.7.1 示例
