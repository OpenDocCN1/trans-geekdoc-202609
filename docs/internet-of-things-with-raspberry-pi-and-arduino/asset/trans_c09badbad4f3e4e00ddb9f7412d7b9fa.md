

# 树莓派基础

```python
except KeyboardInterrupt:
    pass
finally:
    RAJ_lcd_display(0x01, RAJ_LCD_CMD)
    RAJ_cleanup() # 清空所有 GPIO
```

# 5.20 在 I2C 模式下树莓派接接 LCD

该电路由树莓派、LCD 和电源组成。I2C 驱动器连接到 LCD。按照图 5.29 所示进行组件连接。

第 1 步：将 LCD 连接到树莓派

- 将 LCD 的引脚 1 (Vss)、引脚 16 (LED-) 以及 I2C 驱动器的引脚 (GND) 连接到地。
- 将 LCD 的引脚 2 (Vcc)、引脚 15 (LED+) 以及 I2C 驱动器的引脚 (Vcc) 连接到 +5V DC。

![](img/526b5ff9486ff530988203e0cd92330a_97_0.png)

图 5.29
I2C 模式下 LCD 连接的电路图。

# 树莓派与 Arduino 物联网

- 将 LCD 的引脚 3 (V_EE) 连接到 10K 电位器的输出端，并将电位器的其他端连接到 +5V DC 和地。
- 将 I2C 驱动器 LCD 的引脚 (SDA) 连接到树莓派的 GPIO3。
- 将 I2C 驱动器 LCD 的引脚 (SCA) 连接到树莓派的 GPIO5。

**第 2 步：**使用命令下载 Python 脚本：
`wget https://github.com/MatthHawkinsUK/rpispy-misc/raw/master/python/lcd_i2c.py`

**第 3 步：**按照路径 Menu>Preferences > Raspberry Pi Configuration（图 5.30）启用树莓派上的 I2C 接口。然后选择“Interfaces”并将 I2C 设置为“Enabled”（图 5.31）。

点击“OK”按钮。如果提示重启，选择“Yes”使更改生效（图 5.32）。树莓派将重启，i2c 接口现在已启用。

**第 4 步：**使用命令打开 I2C 脚本：`sudo nano lcd_i2c.py`

**第 5 步：**使用命令运行脚本：`sudo python lcd_i2c.py`

![](img/526b5ff9486ff530988203e0cd92330a_98_0.png)

图 5.30
终端上的设置。

# 树莓派基础

![](img/526b5ff9486ff530988203e0cd92330a_99_0.png)

图 5.31
启用 I2C。

![](img/526b5ff9486ff530988203e0cd92330a_99_1.png)

图 5.32
重启。

# 5.20.1 I2C 模式下接 LCD 的配方

```python
import smbus
import time as wait
RAJ_I2C_ADDR = 0x24 # I2C 设备地址
RAJ_LCD_WIDTH = 16 # 每行字符数
RAJ_LCD_CHR = 1 # 模式 - 发数据
RAJ_LCD_CMD = 0 # 模式 - 发命令
RAJ_LCD_LINE_1 = 0x80 # 第一行 LCD RAM 地址
RAJ_LCD_LINE_2 = 0xC0 # 第二行 LCD RAM 地址
RAJ_LCD_LINE_3 = 0x94 # 第三行 LCD RAM 地址
RAJ_LCD_LINE_4 = 0xD4 # 第四行 LCD RAM 地址
RAJ_LCD_BACKLIGHT = 0x08
RAJ_ENABLE = 0b00000010 # LCD 使能(E) 位
RAJ_E_PULSE = 0.0005
RAJ_E_DELAY = 0.0005
```

# 82 树莓派与 Arduino 物物

```python
bus = smbus_SMBus(1) # 第 2 版树莓派使用 1
def RAJ_lcd_init():
    RAJ_lcd_byte(0x33, RAJ_LCD_CMD) # 110011 初始化
    RAJ_lcd_byte(0x32, RAJ_LCD_CMD) # 110010 初始化
    RAJ_lcd_byte(0x06, RAJ_LCD_CMD) # 000110 光标方向
    RAJ_lcd_byte(0x0C, RAJ_LCD_CMD) # 001100 显示开启，光标关闭，闪烁关闭
    RAJ_lcd_byte(0x28, RAJ_LCD_CMD) # 101000 数据长度、行数、字体大小
    RAJ_lcd_byte(0x01, RAJ_LCD_CMD) # 000001 清除显示
    wait.sleep(RAJ_E_DELAY)

def RAJ_lcd_byte(bits, mode):
    bits_high = (bits & 0xF0) | RAJ_LCD_BACKLIGHT
    bits_low = ((bits<<4) & 0xF0) | RAJ_LCD_BACKLIGHT
    RAJ_lcd_byte(0x33, RAJ_LCD_CMD) # 110011 初始化
    RAJ_lcd_byte(0x32, RAJ_LCD_CMD) # 110010 初始化
    RAJ_lcd_byte(0x06, RAJ_LCD_CMD) # 000110 光标方向
    RAJ_lcd_byte(0x0C, RAJ_LCD_CMD) # 001100 显示开启，光标关闭，闪烁
    RAJ_lcd_byte(0x28, RAJ_LCD_CMD) # 101000 数据长度、行数、字体大小
    RAJ_lcd_byte(0x01, RAJ_LCD_CMD) # 000001 清除显示
    wait.sleep(RAJ_E_DELAY)
    bus.write_byte(RAJ_I2C_ADDR, bits_high)
    RAJ_lcd_toggle_enable(bits_high)
    bus.write_byte(RAJ_I2C_ADDR, bits_low)
    RAJ_lcd_toggle_enable(bits_low)

def RAJ_lcd_toggle_enable(bits):
    wait.sleep(RAJ_E_DELAY)
    bus.write_byte(RAJ_I2C_ADDR, bits | RAJ_ENABLE)
    wait.sleep(RAJ_E_PULSE)
    bus.write_byte(RAJ_I2C_ADDR, bits & ~RAJ_ENABLE)
    wait.sleep(RAJ_E_DELAY)

def lcd_string(message, line):
    message = message.ljust(RAJ_LCD_WIDTH, " ")
    RAJ_lcd_byte(line, RAJ_LCD_CMD)
    for i in range(RAJ_LCD_WIDTH):
        RAJ_lcd_byte(ord(message[i]), RAJ_LCD_CHR)

def main():
    RAJ_lcd_init()
    while True:
        lcd_string("I2C LCD", "")

# 5.21 树莓派接 DHT11 传感器

DHT11 传感器采用单总线系统。传感器测量温度和湿度，数据通过输出引脚串行传输。这是一个四脚设备。在引脚 1 (3.3V) 和引脚 2 (Data) 之间需要放置 4-10K 的电阻。三脚设备内置电阻（图 5.33）。

Adafruit DHT11 库用于 DHT11、DHT22 或任何单总线温度传感器。安装 DHT11 库的步骤与 LCD 类似。

# DHT11 的步骤

1. 使用命令更新软件包列表并安装 Python 库：
   `sudo apt-get update`
   `sudo apt-get install build-essential python-dev`

![](img/526b5ff9486ff530988203e0cd92330a_102_0.png)

图 5.33
DHT11 传感器视图。

2. 使用命令下载 Adafruit 库：
   `git clone https://github.com/adafruit/Adafruit_Python_DHT.git cd Adafruit_Python_DHT`

3. 使用命令为 Python 2 和 Python 3 安装库：
   `sudo python setup.py install`
   `sudo python3 setup.py install`

4. 如下连接组件：

连接方式：

- 将 LCD 的引脚 1 (Vss)、引脚 5 (RW) 和引脚 16 (LED-) 连接到地。
- 将 LCD 的引脚 2 (Vcc) 和引脚 15 (LED+) 连接到 +5V DC。
- 将 LCD 的引脚 3 (V_EE) 连接到 10K 电位器的输出端，并将电位器的另外端连接到 +5V DC 和地。
- 将 LCD 的引脚 4 (RS) 连接到树莓派的 GPIO26。
- 将 LCD 的引脚 6 (E) 连接到树莓派的 GPIO19。
- 将 LCD 的引脚 11 (D4) 连接到树莓派的 GPIO13。
- 将 LCD 的引脚 12 (D5) 连接到树莓派的 GPIO6。
- 将 LCD 的引脚 13 (D6) 连接到树莓派的 GPIO5。
- 将 LCD 的引脚 14 (D7) 连接到树莓派的 GPIO21。
- 将 DHT11 的引脚 (Vcc) 和引脚 (GND) 分别连接到 +5V 和地。
- 将 DHT11 的输出引脚连接到树莓派的 GPIO17。

![](img/526b5ff9486ff530988203e0cd92330a_103_0.png)

图 5.34
DHT11 连接的电路图。

图 5.34 显示了 LCD 和 DHT11 连接树莓派的电路图。

# 5.21.1 读取 DHT11 传感器的配方

```python
import Adafruit_DHT as RAJ_DHT
import time as wait
RAJ_sensor = RAJ_DHT.DHT11
RAJ_gpio = 17 # 赋值引脚 17
HUM, TEMP = RAJ_DHT.read(RAJ_sensor, RAJ_gpio)
if HUM is not None and TEMP is not None:
    print('TEMP={:.1f}C HUM={:.1f}%'.format(TEMP, HUM))
else:
    print('try again')
```

# 5.21.2 读取 DHT11 传感器显示在 LCD 上

```python
import time as wait
import Adafruit_Char as RAJ_LCD
import Adafruit_DHT as RAJ_DHT
```

RAJ_sensor_name = RAJ_DHT.DHT11 #我们在使用 DHT11 传感器
RAJ_sensor_pin = 17 # 赋值引脚 17
RAJ_lcd_rs = 26 # 连接到引脚 26 的 RS 引
RAJ_lcd_en = 19 # 连接到引脚 26 的 E 引
RAJ_lcd_d4 = 13 # 连接到引脚 26 的 D4 引
RAJ_lcd_d5 = 6 # 连接到引脚 26 的 D5 引
RAJ_lcd_d6 = 5 # 连接到引脚 26 的 D6 引
RAJ_lcd_d7 = 21 # 连接到引脚 26 的 D7 引
RAJ_lcd_backlight = 0
RAJ_lcd_columns = 20
RAJ_lcd_rows = 4
RAJ_lcd = RAJ_LCD.Char(RAJ_lcd_rs, RAJ_lcd_en, RAJ_lcd_d4, RAJ_lcd_d5, RAJ_lcd_d6, RAJ_lcd_d7, RAJ_lcd_columns, RAJ_lcd_rows, RAJ_lcd_backlight)
#为 LCD 库提供引脚详情
RAJ_lcd.message("VALUE FROM DHT11") # 在 LCD 上打印消息
wait.sleep(2) # 延迟 2 秒

def main():
    pass

whilewhile True:
    HUM, TEMP = RAJ_DHT.retry(RAJ_sensor_name, RAJ_sensor_pin)
    if HUM is not None and TEMP is not None:
        RAJ_lcd.clear(# 清空 LCD 内容
        RAJ_lcd.message("%.1f C %%") # 在 LCD 上打印温度值
        RAJ_lcd.message("\nHum=%.1f %%") # 在 LCD 上打印湿度值
    else:
        print('try again')

