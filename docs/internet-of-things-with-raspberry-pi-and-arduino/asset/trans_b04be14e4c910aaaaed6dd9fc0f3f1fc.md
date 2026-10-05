

![](img/526b5ff9486ff530988203e0cd92330a_146_0.png)

# 8 使用 Tkinter 和 Arduino 开发 Python GUI

## 8.1 用于 GUI 设计的 Tkinter

图形用户界面（GUI）库的基本特性包括易于安装和计算量最小。Tkinter 框架满足了这些基本需求。它也是 Python 安装自带的 GUI 库。Tkinter 接口是 Tk GUI 工具包的跨平台 Python 接口。Tkinter 在 Python 之上提供了一层，而 Tk 则提供了图形组件。Tkinter 是一个跨平台库，作为许多操作系统的 Python 安装包的一部分部署。

Tkinter 的设计初衷是为了用最少的编程工作创建图形应用程序。要测试 Tk 工具包的版本，请在 Python 提示符中使用以下命令：

```python
>>> import Tkinter
>>> Tkinter._test()
```

系统会弹出一个包含版本信息的窗口（图 8.1）。如果窗口（图 8.1）不可见，请重新安装 Python。

Tk 接口支持多种组件来开发 GUI。表 8.1 描述了部分组件。

## 8.2 LED 闪烁

为了理解 LED 与 Tkinter GUI 的工作原理，设计了一个简单的电路。该系统由一个树莓派、一个 Arduino、一个 LED 和一个电源组成。Arduino 通过 USB 接口连接到树莓派。LED 的阳极通过 10-K 电阻连接到 Arduino 的第 7 引脚，阴极连接到地。

图 8.2 显示了接口 LED 的电路图。

![](img/526b5ff9486ff530988203e0cd92330a_148_0.png)

图 8.1
Tk 版本。

# 表 8.1
用于开发 GUI 的 Tkinter 组件

| 组件 | 描述 |
| --- | --- |
| Tk() | 每个程序都需要的根组件 |
| Label() | 显示图像或文本 |
| Button() | 执行动作 |
| Entry() | 用于提供输入的文本框 |
| Scale() | 通过拖动滑块提供数值 |
| Checkbox() | 允许在两个值之间切换 |

![](img/526b5ff9486ff530988203e0cd92330a_148_1.png)

图 8.2
接口 LED 的电路图。

# 使用 Tkinter 和 Arduino 开发 Python GUI

### 8.2.1 固定时间延迟 LED 闪烁方案

```python
import Tkinter
import pyfirmata
import time as wait
# 使用 pyfirmata 端口和开发板
board = pyfirmata.Arduino('/dev/ttyUSB0')
wait.sleep(5) # 延迟 5 秒
led_Pin = board.get_pin('d:7') # 连接到第 7 引脚并作为输出
def call_LED_BLINK():
    button.config(state = Tkinter.DISABLED)
    led_Pin.write(1) # 将 led_Pin 置为高电平
    print('LED at pin7 is ON') # 在终端打印
    wait.sleep(5) # 延迟 5 秒
    print('LED at pin7 is OFF') # 在终端打印
    led_Pin.write(0) # 将 led_Pin 置为低电平
    button.config(state=Tkinter.ACTIVE)
# 初始化主窗口标题和大小
TOP = Tkinter.Tk()
TOP.title("Blink LED using button")
TOP.minsize(300,30)
# 在主窗口上创建一个按钮并与上述方法关联
button = Tkinter.Button(TOP, text="Press start to blink", command = call_LED_BLINK)
button.pack()
TOP.mainloop()
```

