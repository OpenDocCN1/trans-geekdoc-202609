

170 基于树莓派和 Arduino 的物联网

![](img/526b5ff9486ff530988203e0cd92330a_188_0.png)

图 10.14

(a) 湿度数据。(b) 温度数据。

![](img/526b5ff9486ff530988203e0cd92330a_188_1.png)

图 10.15

(a) 压力数据。(b) 海拔度数据。

![](img/526b5ff9486ff530988203e0cd92330a_188_2.png)

图 10.16

PIR 传感器数据。

# 智能物联网系统
171

![](img/526b5ff9486ff530988203e0cd92330a_189_0.png)

图 10.17 (a) 加速度计 x 轴数据。(b) y 轴数据。(c) z轴数据。

# 连接

- 将摄像头连接到树莓派的专用端口。
- 将 PIR 传感器、BMP180 传感器、加速度计、蜂鸣器和 DHT11 传感器的引脚（Vcc 和地）分别连接到 +5 VDC 和地。
- 将 DHT11 传感器的引脚(OUT) 连接到 Arduino Uno 的引脚(4)。
- 通过 USB 将 Arduino Uno 连接到树莓派。
- 将 PIR 传感器的引脚(OUT) 连接到 Arduino Uno 的引脚(2)。
- 将雨传感器引脚(OUT) 连接到 Arduino Uno 的引脚(A0)。
- 将蜂鸣器的引脚(OUT) 连接到 Arduino Uno 的引脚(5)。
- 将 BMP180 的引脚(SCL) 连接到 Arduino Uno 的引脚(A5)。
- 将 BMP180 的引脚(SDA) 连接到 Arduino Uno 的引脚(A4)。
- 将加速度计的“x 轴”连接到 Arduino Uno 的引脚 (A1)。
- 将加速度计的“y 轴”连接到 Arduino Uno 的引脚 (A2)。
- 将加速度计的“z 轴”连接到 Arduino Uno 的引脚 (A3)。

# 10.4.1 示例

```python
import sys # 导入库
import RPi.GPIO as GPIO
import time as wait # 导入时间库
import Adafruit_DHT as RAH
```

# 基于树莓派和 Arduino 的物联网

```python
import urllib2 # 添加 url 库
from adxl3345 import ADXL345
from picamera import PiCamera
from Adafruit_BMP085 import BMP085
mp_sensor = BMP085(0x77)
adxl345_sensor = ADXL345()
GPIO.setmode(GPIO.BCM) # 使用 BCM 下的树莓派引脚
GPIO.setup(16, GPIO.IN)
```

```python
def get_sensor_data():
    HUM, TEMP = RAH.read_retry(DHT.DHT11, 4)
    pir_sensor = GPIO.input(16) # 将 PIR 传感器连接到 GPIO 16
    mp_sensor = BMP085(0x77)
    pressure1 = bmp.readPressure() # 读取压力
    pressure_data = pressure1 / 100 # 缩放压力值
    altitude_data = bmp.readAltitude() # 读取高度
    axes = adxl345.getAxes(True)
    x1_data = axes['x']
    y1_data = axes['y']
    z1_data = axes['z']
    return (str(HUM), str(TEMP), str(pir_sensor), str(pressure_data),
            str(altitude_data), str(x1_data), str(y1_data), str(z1_data))
```

```python
def main_program():
    count = 0 # 初始化计数
    pir_data = GPIO.input(16) # 将 PIR 传感器连接到 GPIO16 作为输入
    if len(sys.argv) < 2:
        print('print data') # 在终端打印字符串
        exit(0)

    print 'process start...' # 在终端打印字符串
    base_URL = 'https://api.thingspeak.com/update?api_key=%s' % sys.argv[1]

    while True:
        try:
            HUM, TEMP, pir_sensor, pressure_data, altitude_data, x1_data, y1_data, z1_data = get_sensor_data()
            f = urllib2.urlencode(base_URL + "&field1=%s&field2=%s&field3=%s&field4=%s&field5=%s&field6=%s&field7=%s&field8=%s"
            % (HUM, TEMP, pir_sensor, pressure_data, altitude_data, x1_data, y1_data, z1_data))
            print(f.read()) # 读取函数

            if (pir_data == 1):
                print "hello" # 在终端打印字符串
                RAJ_camera = PiCamera()
                RAJ_camera.start_preview()
                wait.sleep(5) # 延迟 5 秒
                count = count + 1
                RAJ_camera.capture('img%s.jpg' % count) # 捕捉图像
                RAJ_camera.stop_preview() # 停止预览
                RAJ_camera.close() # 关闭摄像头
                f.close() # 关闭函数
                wait.sleep(15) # 等待 15 秒
        except:
            print 'exit from main program' # 在终端打印字符串
            break
if __name__ == '__main__':
    main_program()

# 10.5 智能运动检测器并上传图片

运动检测器是一个检测到运动时捕捉图片并发送到指定 Gmail 地址的系统。该系统由树莓派、摄像头、PIR 传感器、LED 指和电源组成。连接方式如图 10.18 所示。

- 将摄像头连接到树莓派的专用端口。
- 将 PIR 传感器的引脚（Vcc 和地）分别连接到 +5 VDC 和地。
- 将 PIR 传感器的引脚(OUT) 连接到树莓派的 GPIO21。
- 将 LED 的阴极连接到地，阳极通过电阻连接到 GPIO3。

174 基于树莓派和 Arduino 的物联网
![](img/526b5ff9486ff530988203e0cd92330a_192_0.png)
图 10.18 智能运动检测器电路图。

# 10.5.1 配置树莓派摄像头和 Gmail

步骤 1：使用以下命令更新并升级树莓派
```bash
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install python3
```

步骤 2：安装并配置 SMTP 服务
```bash
sudo apt-get install smtp
sudo nano /etc/smtp.conf
```

步骤 3：启用树莓派的 SSH 和摄像头权限。

步骤 4：按照以下步骤允许 Gmail SMTP 访问
1. 使用用户名和密码登录 Gmail 账号。
2. 进入右上角的“账号”(My Account)。
3. 选择“安全”(Security)部分。
4. 开启“允许不够安全的应用”(Allow less apps)。

# 10.5.2 示例

```python
import RPi.GPIO as GPIO # 导入 pi GPIO
import picamera as RAJ_camera # 导入摄像头
import time as wait # 导入时间库
import smtplib # 导入 smtplib
from email.mime.multipart import MIMEMipart # 导入库
from email.mime.text import MIMEText # 导入库
from email.mime.base import MIMEBase # 导入库
from email import encoders # 导入库
from email.mime.image import MIMEImage # 导入库

from_addr = "ssss@gmail.com" # 修改邮箱地址
to_addr = "rrrrrr@gmail.com"
mail_RAJ = MIMEMipart()
mail_RAJ['From'] = from_addr
mail_RAJ['To'] = to_addr
mail_RAJ['Subject'] = "Attachment"
body = "Please find the attachment"
led_pin = 3 # 连接树莓派的 GPIO 3
pir_pin = 21 # 连接传感器到树莓派的 GPIO21

HIGH = 1 # 赋值
LOW = 0 # 赋值
GPIO.setwarnings(False) # 移除警告
GPIO.setmode(GPIO.BCM) # 使用 BCM 模式
GPIO.setup(led_pin, GPIO.OUT) # 设置引脚为输出
GPIO.setup(pir_pin, GPIO.IN) # 设置引脚为输入
```

```python
def send_Mail(data):
    mail_RAJ.attach(MIMEText(body, 'plain'))
    print data # 在终端打印数据
    dat = "%s.jpg" % data
    print (data) # 在终端打印数据
    attachment_RAJ = open(dat, 'rb')
    image_RAJ = MIMEImage(attachment_RAJ.read())
    attachment_RAJ.close()

    mail_RAJ.attach(image_RAJ) # 附加图像
    server_RAJ = smtplib.SMTP('smtp.gmail.com', 587)
    server_RAJ.starttls()
    server_RAJ.login(from_addr, "ssss@gmail.com")
    text = mail_RAJ.as_string()
    server_RAJ.sendmail(from_addr, to_addr, text)
    server_RAJ.quit() # 退出服务器
```

```python
def RAJ_capture_image():
    data = wait.strftime('%d_%b_%Y|%H:%M:%S')
    RAJ_camera.start_preview() # 开启预览
    wait.sleep(5) # 等待 5 秒
    print data # 在终端打印数据
    RAJ_camera.capture('%s.jpg' % data)
    RAJ_camera.stop_preview() # 停止预览
    wait.sleep(1) # 等待 1 秒
    send_Mail(data) # 发送邮件
```

GPIO.output(led_pin, 0) # 将引脚置低
RAJ_camera = picamera.PiCamera()
RAJ_camera.rotation = 180 # 旋转摄像头
RAJ_camera.awb_mode='auto'
RAJ_camera.brightness = 55 # 选择亮度级别
while 1:
    if GPIO.input(pir) == 1: # 检查 PIR 状态
        GPIO.output(led_pin, HIGH) # 将引脚置高
        RAJ_capture_image() # 捕捉图像
    else:
        GPIO.output(led, LOW) # 将引脚置低
        wait.sleep(1) # 等待 1 秒
```
