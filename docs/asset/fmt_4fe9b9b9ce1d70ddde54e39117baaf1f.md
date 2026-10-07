
```python
import Tkinter # 导入 Tkinter 库
import pyfirmata # 导入 pyfirmata
import time as wait # 导入 time 库
board = pyfirmata.Arduino('/dev/ttyUSB0')
wait.sleep(5) # 延迟 5 秒
PIR_pin = board.get_pin('d:8:0') # 连接 传感器到引脚 8
red_led_pin = board.get_pin('d:7:0') # 将 led 连接到引脚 7 并作为输出
green_led_pin = board.get_pin('d:6:0') # 将 led 连接到引脚 6 并作为输出
it = pyfirmata.util.Iterator(board)
it.start() # 迭代器
TOP = Tkinter.Tk()
TOP.title("PIR Sensor Test")
Motion_Label = Tkinter.Label(TOP, text="Waiting...")
Motion_Label.grid(column=1, row=1)
FLAG = Tkinter.BooleanVar(TOP)
FLAG.set(True)
def start_button_press():
    while True:
        if FLAG.get():
            if PIR_pin.read(is) is True:
                blink_LED(red_led_pin, "motion_status:Y")
                print 'Motion detected ' # 在终端打印
        else:
            blink_LED(green_led_pin, "motion_status:N")
            print 'No motion ' # 在终端打印
        else:
            break
    board.exit()
    TOP.destroy()
def stop_button_press():
    FLAG.set(False)

red_led_Var = Tkinter.IntVar()
red_CheckBox = Tkinter.Checkbox(TOP, text="Red_LED_status", variable=red_led_Var)
red_Checkbox.grid(column=1, row=2)
green_led_Var = Tkinter.IntVar()
green_Checkbox = Tkinter.Checkbox(TOP, text="Green_LED_status", variable=green_led_Var)
green_Checkbox.grid(column=2, row=2)
start_Button = Tkinter.Button(TOP, text="Start_button", command=start_button_press)
start_Button.grid(column=1, row=3)
stop_Button = Tkinter.Button(TOP, text="Stop_button", command=stop_button_press)
stop_Button.grid(column=2, row=3)
exit_Button = Tkinter.Button(TOP, text="Exit_button", command=quit)
exit_Button.grid(column=3, row=3)
TOP.mainloop()
```

# 使用 Tkinter 和 Arduino 的 Python GUI

## 8.6.2 Tkinter GUI

运行第 8.6.1 节中描述的程序，以创建一个用于读取电位器（POT）的 Tkinter GUI，并将出现一个窗口（图 8.16）。点击“Start_reading”按钮后，它将给出 POT 的读数（图 8.17）。

![](img/526b5ff9486ff530988203e0cd92330a_161_0.png)

图 8.16

读取电位器的 Tkinter GUI。

```
pi@raspberrypi:~ $ nano analog_in_tkinter.py
pi@raspberrypi:~ $ python analog_in_tkinter.py
analog values of pot
analog values of pot
analog values of pot
```

图 8.17

显示 POT 模拟值的窗口。

![](img/526b5ff9486ff530988203e0cd92330a_162_0.png)

# 9. 使用 Python 和 Tkinter 获取数据

## 9.1 基础

**`open()` 方法：** 该函数是 Python 中最常用的方法之一，用于操作文件。

打开文件的命令：

`>>> f = open('test.txt', 'w')`

此命令会在 Python 解释器所在的文件夹中，或者执行代码的路径中创建一个 `test.txt` 文件。

与 `open()` 函数配合使用的模式在表 9.1 中讨论。

**`write()` 方法：** 一旦以写入模式打开文件，即可使用 `write()` 方法开始向文件对象写入内容。`write()` 方法仅接受字符串格式的输入参数。

`>>> f.write('Hello World!\n')`

在这里 'Hello World' 是一个字符串，`\n` 意味着换行符。

要写入一系列字符串，则使用 `writelines()` 方法：

`>>> sq = ["Python programming for Arduino\n", "Bye\n"]`

`>>> f.writelines(sq)`

**`close()` 方法：** `close()` 方法用于关闭文件，之后文件对象将无法再次使用。命令为：

`>>> f.close()`

**`read()` 方法：** `read()` 方法读取文件数据。该方法通过任何兼容读取的模式（如：w+, r, r+, 或 a+）打开文件：

`>>> D = open('test.txt', 'r')`

`>>> D.read()`

### 表 9.1

模式描述

| 模式 | 描述 |
| --- | --- |
| W | 此模式仅用于写入打开文件。它会覆盖现有文件。 |
| w+ | 此模式以读写双模式打开文件。它会覆盖现有文件。 |
| R | 此模式仅用于读取打开文件。 |
| r+ | 此模式以追加和读取模式打开文件。 |
| A | 此模式用于追加打开文件，从文档末尾开始。 |
| a+ | 此模式以追加和读取打开文件，从文档末尾开始。 |

```
'Hello World!\nPython programming for Arduino\nBye\n'
>>> D.close()
```

通过此方法，文件的整个内容被存储在内存中。若要行读取内容使用，请使用 `readlines()` 方法：

```
>>> D=open('test.txt', 'r')
>>> X =D.readlines()
>>> print X
['Hello World!\n', 'Python programming for Arduino\n', 'Bye\n']
>>> D.close()
```

## 9.2 CSV 文件

CSV 文件用于在 Python 中存储数据。使用 CSV 写入器向 CSV 文件写入数据，使用读取器通过简单命令读取：

### CSV 写入器

```python
import csv
data = [[1, 2, 3], ['a', 'b', 'c'], ['Python', 'Arduino', 'Programming']]
with open('example.csv', 'w') as f:
    w = csv.writer(f)
    for row in data:
        w.writerow(row)
```

### CSV 读取器

```python
import csv
with open('example.csv', 'r') as file:
    r = csv.reader(file)
    for row in r:
        print(row)
```

## 9.3 使用 CSV 文件存储 Arduino 数据

CSV 文件可存储来自 Arduino 的传感器数据。为了理解这一概念，我们讨论一个系统。该系统由树莓派、Arduino、热电红外（PIR）传感器（数字传感器）、电位器（POT，作为模拟传感器）和一个电源组成。目标是通过 CSV 文件存储传感器数据，并实现 Arduino 与 Python 的交互。图 9.1 显示了系统的电路图。

![](img/526b5ff9486ff530988203e0cd92330a_165_0.png)

#### 连接：

- PIR 传感器的输出连接到 Arduino 的数字 7 引脚。
- PIR 传感器的 VCC 和 GND 连接到 5V。
- 电位器的 VCC 连接到 5V。
- 电位器的地线连接到 GND。
- 电位器的滑变引脚连接到 Arduino 的 A0 引脚。

### 9.3.1 示例

```python
import csv
import pyfirmata
import time as wait

board = pyfirmata.Arduino('/dev/ttyUSB0')
it = pyfirmata.util.Iterator(board)
it.start()

with open('SensorData.csv', 'w') as f:
    w = csv.writer(f)
    w.writerow(["Number","Potentiometer", "Motion sensor"])
    ni = 0
    while True:
        pot_data = board['a0'][0]
        pir_data = board['d7'][0]
        if pot_data is not None:
            row = [ni, pot_data, pir_data]
            w.writerow(row)
            ni += 1
        wait.sleep(1)
```

## 9.4 绘制随机数

`set_xdata()` 和 `set_ydata()` 方法用于更新 x y 轴。

### 9.4.1 示例

```python
import matplotlib.pyplot as plt
import random
R = range(25)
S = [random.randint(0,100) for r in range(25)]
plt.figure()
plt.plot(R, S, '-')
plt.title('random numbers')
plt.xlabel('X Axis')
plt.ylabel('Y Axis')
plt.show()
```

## 9.5 绘制 Arduino 实时数据

来自 Arduino 的实时数据是一项任务。`ion()` 方法用于初始化交互模式。通过调用 `ion()` 设置交互模式。这有助于动态更改 x y 值。

```python
plt.ion()
```

一旦设置了交互模式，可以通过调用 `draw()` 方法绘制图形。现在，用一组空白数据（在本例中为0）初始化图形：

```python
pData = [0] * 25
```

在该 y 值数组 `pData` 中，在循环循环中追加传感器值以将最新值追加到此数据数组，并使用这些更新的数组重新绘制图形。

### 9.5.1 示例

```python
# ... (之前的设置代码)
while True:
    val = float(a0.read())
    if val is not None:
        pData.append(val)
        pData.pop(0)
        plt.draw()
    wait.sleep(1)
```

# 基于树莓派和 Arduino 的物联网

```python
pyplot.ion()
pData = [0.0] * 25
fig = pyplot.figure()
pyplot.title('Real time data plot from POT')
ax1 = plt.axes()
l1, = plt.plot(pData)
plt.ylim([0, 1])
```

```python
while True:
    try:
        wait.sleep(1)
        pData.append(float(POT_pin.read()))
        plt.ylim([0, 1])
        del pData[0]
        l1.set_xdata(i for i in xrange(25))
        l1.set_ydata(pData) # update the data
        pyplot.draw() # update the plot
    except KeyboardInterrupt:
        board.exit()
break
```

## 9.6 将图表集成到 Tkinter 窗口

第 9.5 节描述了如何为 Arduino 的连续传感器数据绘制图表。Python 与 matplotlib 库和 Tkinter 图形界面具有强大的集成能力。本文将针对图 9.3 所示电路讨论这种集成。该程序使用了 Tkinter 与 matplotlib 的接口。

### 9.6.1 配方

```python
import sys # import sys library
from matplotlib import pyplot # import library
import pyfirmata # import library
import time as wait # import time library
import Tkinter # import library
```

# 使用 Python 和 Tkinter 进行数据采集

```python
def start_button_press():
    while True:
        if FLAG.get():
            sleep(1) # wait for 1 Sec
            pData.append(float(POT_pin.read()))
            pyplot.ylim([0, 1])
            del pData[0]
            Il.set_xdata([li for i in xrange(25)])
            Il.set_ydata(pData) # update the data
            pyplot.draw() # update the plot
            TOP.update()
        else:
            FLAG.set(True)
            break
```

```python
def pause_button_press():
    FLAG.set(False)
```

```python
def exit_button_press():
    print("out from data recording....")
    pause_button_press()
    board.exit()
    pyplot.close(fig)
    TOP.quit()
    TOP.destroy()
    print("completed...")
    sys.exit()
```

```python
board = pyfirmata.Arduino('/dev/ttyUSB0')
# 使用迭代器线程避免缓冲区溢出
it = pyfirmata.util.Iterator(board)
it.start() # start iterator
# 给模拟引脚 0 分配角色和变量
POT_pin = board.get_pin('a:0:i') # read read POT
# Tkinter 画布
TOP = Tkinter.Tk()
TOP.title("Tkinter + matplotlib")
# 创建标志以配合无限循环
FLAG = Tkinter.IntVar(TOP)
```

```python
FLAG.set(True)
pyplot.ion()
pData = [0.0] * 25
figure = pyplot.figure()
plt.title('Potentiometer')
ax1 = pyplot.axes()
l1, = plt.plot(pData)
plt.ylim(0, 1)
```

# 创建启动按钮并关联启动按钮按下方法

start_Button = Tkinter.Button(TOP, text="Start", command=start_press)

start_Button.grid(column=1, row=2)

# 创建退出按钮以退出窗口

exit_Button=Tkinter.Button(TOP,text="Exit",command=exit_button_press)

exit_Button.grid(column=3, row=2)

TOP.mainloop()

执行程序，屏幕上将出现一个窗口（图 9.4）。

可以使用“Start”（启动）、“Pause”（暂停）和“Exit”（退出）按钮控制图表。
