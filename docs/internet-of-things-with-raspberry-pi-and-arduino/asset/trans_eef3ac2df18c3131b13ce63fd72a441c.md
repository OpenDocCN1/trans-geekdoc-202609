

## 8.4.1 实例代码 (Recipe)

```python
import Tkinter # 添加 Tkinter 库
import pyfirmata # 添加 pyfirmata 库
import time as wait # 添加 time 库
board = pyfirmata.Arduino('/dev/ttyUSB0')
wait.sleep(5) # 延迟 5 秒
red_led_pin = board.get_pin('d:7:0') # 将 led 连接到引脚 7 并作为输出
green_led_pin = board.get_pin('d:6:0') # 将 led 连接到引脚 6 并作为输出
def start_button_press():
    red_led_pin.write(red_led_Var.get())
    green_led_pin.write(green_led_Var.get())
    print('start...') # 在终端打印
def stop_button_press():
    red_led_pin.write(0) # 让引脚 7 置为高电
    green_led_pin.write(0) # 让引脚 6 置为高电
    print('stop...') # 在终端打印
TOP = Tkinter.Tk()
red_led_Var = Tkinter.IntVar()
red_CheckBox = Tkinter.Checkbox(TOP, text="Red_LED_status", variable=red_led_Var)
red_Checkbox.grid(column=1, row=1)
green_led_Var = Tkinter.IntVar()
green_Checkbox = Tkinter.Checkbox(TOP, text="Green_LED_status", variable=green_led_Var)
green_Checkbox.grid(column=2, row=1)
start_Button = Tkinter.Button(TOP, text="Start_button", command=start_button_press)
start_Button.grid(column=1, row=2)
stop_Button = Tkinter.Button(TOP, text="Stop_button", command=stop_button_press)
stop_Button.grid(column=2, row=2)
exit_Button = Tkinter.Button(TOP, text="Exit_button", command=quit)
exit_Button.grid(column=3, row=2)
TOP.mainloop()
```

# 使用 Tkinter 和 Arduino 的 Python GUI

![](img/526b5ff9486ff530988203e0cd92330a_155_0.png)

图 8.10
用于多个 LED 的 Tkinter GUI。

```
@raspberrypi:~ $ name pyfirpy_two_led_tkinter_BOK.py
@raspberrypi:~ $ python pyfirpy_two_led_tkinter_BOK.py
start...
stop...
```

图 8.11
状态窗口的截图。

## 8.4.2 Tkinter GUI

为了为多个 LED 生成 Tkinter GUI，请运行 8.4.1 节中描述的程序，将出现一个窗口（图 8.10）。该 GUI 为每个红色和绿色 LED 分配有一个 `Checkbutton()` 控件。用户可以单独或同时选择 LED 以使其启动或停止（图 8.11）。

## 8.5 读取 PIR 传感器

使用热电红外 (PIR) 传感器来检测运动。设计了一个基于树莓派的系统，用两个 LED 显示运动状态。如果没有检测到运动，绿色 LED 将发光；如果检测到运动，则会产生报警并让 LED “开启”。该系统通过 Tkinter GUI 进行开启/关闭。传感器的状态打印在 Python 提示符上。系统由树莓派、Arduino、两个 LED、一个 PIR 传感器和一个电源组成。Arduino 通过 USB 连接到树莓派。LED1 和 LED2 的阳极端分别连接到 Arduino 的引脚 (7) 和引脚 (6)。PIR 传感器的引脚 (OUT) 连接到 Arduino 的引脚 (8)，引脚 (Vcc) 和 (GND) 分别连接 +5 V DC 和地（图 8.12）。

## 8.5.1 读取 PIR 传感器的实例代码

- 定义自定义函数以执行闪烁动作

```python
def blink_LED(pin, message):
# 基于树莓派和 Arduino 的物联网
![](img/526b5ff9486ff530988203e0cd92330a_156_0.png)

图 8.12
PIR 传感器接口的电路图。

Motion_Label.config(text=message)
Motion_Label.update_idletasks())
TOP.update()
pin.write(1) # 让引脚置为高电
wait.sleep(1) # 延迟 1 秒
pin.write(0) # 让引脚置为高电
wait.sleep(1) # 延迟 1 秒
# 定义与启动按钮点击相关的动作
def process_start_button():
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
def press_exit_button():
    FLAG.set(False)

```

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

