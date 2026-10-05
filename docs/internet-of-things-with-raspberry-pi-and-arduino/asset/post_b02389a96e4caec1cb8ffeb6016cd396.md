
# Basics of Raspberry Pi

```python
except KeyboardInterrupt:
    pass
finally:
    RAJ_lcd_display(0x01, RAJ_LCD_CMD)
    RAJ_cleanup() # clean all GPIOs
```

# 5.20 Interfacing LCD with Raspberry Pi in I2C Mode

The circuit is comprised of Raspberry Pi, LCD, and a power supply. An I2C driver is connected with LCD. Make the component connections as shown in Figure 5.29.

Step 1: Interface the LCD with Raspberry Pi

- Connect pin1 (Vss) and pin16 (LED-) of LCD and pin (GND) of the I2C driver to ground.
- Connect pin2 (Vcc) and pin15 (LED+) of LCD and pin (Vcc) of the I2C driver to +5 V DC.

![](img/526b5ff9486ff530988203e0cd92330a_97_0.png)

FIGURE 5.29
Circuit diagram for LCD interfacing in I2C mode.

# Internet of Things with Raspberry Pi and Arduino

- Connect pin3 (V_EE) of LCD to the output of a 10 K potentiometer and connect the other terminals of the potentiometer to +5 V DC and ground.
- Connect pin(SDA) of the I2C driver LCD to GPIO3 of Raspberry Pi.
- Connect pin(SCA) of the I2C driver LCD to GPIO5 of Raspberry Pi.

**Step 2:** Download the Python Script by using:
`wget https://github.com/MatthHawkinsUK/rpispy-misc/raw/master/python/lcd_i2c.py`

**Step 3:** Enable the I2C Interface on Raspberry Pi by following the path Menu>Preferences > Raspberry Pi Configuration (Figure 5.30). Then select the “Interfaces” and set I2C to “Enabled” (Figure 5.31).

Click the “OK” button. If prompted to reboot, select “Yes” so that the changes can be taken effectively (Figure 5.32). The Raspberry Pi will reboot, and the i2c interface is now enabled.

**Step 4:** Open the I2C Script with the command: `sudo nano lcd_i2c.py`

**Step 5:** Run the script with the command: `sudo python lcd_i2c.py`

![](img/526b5ff9486ff530988203e0cd92330a_98_0.png)

FIGURE 5.30
Setting on terminal.

# Basics of Raspberry Pi

![](img/526b5ff9486ff530988203e0cd92330a_99_0.png)

FIGURE 5.31
Enable I2C.

![](img/526b5ff9486ff530988203e0cd92330a_99_1.png)

FIGURE 5.32
Reboot.

# 5.20.1 Recipe to Interface LCD in I2C Mode

```python
import smbus
import time as wait
RAJ_I2C_ADDR = 0x24 # address of I2C device
RAJ_LCD_WIDTH = 16 # number of char per line
RAJ_LCD_CHR = 1 # Mode - Sending data
RAJ_LCD_CMD = 0 # Mode - Sending command
RAJ_LCD_LINE_1 = 0x80 # LCD RAM address for the 1st line
RAJ_LCD_LINE_2 = 0xC0 # LCD RAM address for the 2nd line
RAJ_LCD_LINE_3 = 0x94 # LCD RAM address for the 3rd line
RAJ_LCD_LINE_4 = 0xD4 # LCD RAM address for the 4th line
RAJ_LCD_BACKLIGHT = 0x08
RAJ_ENABLE = 0b00000010 # LCD enable(E) bit
RAJ_E_PULSE = 0.0005
RAJ_E_DELAY = 0.0005
```

# 82 Internet of Things with Raspberry Pi and Arduino

```python
bus = smbus_SMBus(1) # Rev 2 Pi uses 1
def RAJ_lcd_init():
    RAJ_lcd_byte(0x33, RAJ_LCD_CMD) # 110011 Initialise
    RAJ_lcd_byte(0x32, RAJ_LCD_CMD) # 110010 Initialise
    RAJ_lcd_byte(0x06, RAJ_LCD_CMD) # 000110 Cursor direction
    RAJ_lcd_byte(0x0C, RAJ_LCD_CMD) # 001100 Display On, Cursor, Off, Blink Off
    RAJ_lcd_byte(0x28, RAJ_LCD_CMD) # 101000 Data length, number of lines, font size
    RAJ_lcd_byte(0x01, RAJ_LCD_CMD) # 000001 Clear display
    wait.sleep(RAJ_E_DELAY)

def RAJ_lcd_byte(bits, mode):
    bits_high = (bits & 0xF0) | RAJ_LCD_BACKLIGHT
    bits_low = ((bits<<4) & 0xF0) | RAJ_LCD_BACKLIGHT
    RAJ_lcd_byte(0x33, RAJ_LCD_CMD) # 110011 Initialise
    RAJ_lcd_byte(0x32, RAJ_LCD_CMD) # 110010 Initialise
    RAJ_lcd_byte(0x06, RAJ_LCD_CMD) # 000110 Cursor direction
    RAJ_lcd_byte(0x0C, RAJ_LCD_CMD) # 001100 Display On, Cursor Off, Blink
    RAJ_lcd_byte(0x28, RAJ_LCD_CMD) # 101000 Data length, number of lines, font size
    RAJ_lcd_byte(0x01, RAJ_LCD_CMD) # 000001 Clear display
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

# 5.21 Interfacing of DHT11 Sensor with Raspberry Pi

The DHT11 sensor works with a one-wire system. The temperature and humidity values are measured by the sensor, and this data is communicated serially through the output pin. It is a four-pin device. A resistor of value 4-10 K needs to be placed between pin 1 (3.3V) and pin 2 (Data). The three-pin device has a built-in resistor (Figure 5.33).

The Adafruit DHT11 library can be used for DHT11, DHT22, or any other one-wire temperature sensor. The procedure to install the DHT11 library is similar to the steps followed for the LCD.

# Steps to interface DHT11

1. Update the package lists and install the Python libraries with the help of commands:
   `sudo apt-get update`
   `sudo apt-get install build-essential python-dev`

![](img/526b5ff9486ff530988203e0cd92330a_102_0.png)

FIGURE 5.33
View of DHT11 sensor.

2. Download the Adafruit library by using the command:
   `git clone https://github.com/adafruit/Adafruit_Python_DHT.git cd Adafruit_Python_DHT`

3. Install the library for Python 2 and Python 3 using the command:
   `sudo python setup.py install`
   `sudo python3 setup.py install`

4. Connect the components as follows:

Connections:

- Connect pin1 (Vss), pin5 (RW) and pin16 (LED-) of LCD to ground.
- Connect pin2 (Vcc), and pin15 (LED+) of LCD to +5 V DC.
- Connect pin3 (V_EE) of LCD to output of 10 K potentiometer and connect other two terminals of potentiometer to +5 V DC and ground.
- Connect pin4 (RS) of LCD to GPIO26 of Raspberry Pi.
- Connect pin6 (E) of LCD to GPIO19 of Raspberry Pi.
- Connect pin11 (D4) of LCD to GPIO13 of Raspberry Pi.
- Connect pin12 (D5) of LCD to GPIO6 of Raspberry Pi.
- Connect pin13 (D6) of LCD to GPIO5 of Raspberry Pi.
- Connect pin14 (D7) of LCD to GPIO21 of Raspberry Pi.
- Connect pin (Vcc) and pin (GND) of DHT11 to +5 V and ground, respectively.
- Connect output pin of DHT11 to GPIO17 of Raspberry Pi.

![](img/526b5ff9486ff530988203e0cd92330a_103_0.png)

FIGURE 5.34
Circuit diagram for the interfacing of DHT11.

Figure 5.34 shows the circuit diagram for the interfacing of LCD and DHT11 with Raspberry Pi.

# 5.21.1 Recipe to Read DHT11 Sensor

```python
import Adafruit_DHT as RAJ_DHT
import time as wait
RAJ_sensor = RAJ_DHT.DHT11
RAJ_gpio = 17 # assignment variable to pin 17
HUM, TEMP = RAJ_DHT.read(RAJ_sensor, RAJ_gpio)
if HUM is not None and TEMP is not None:
    print('TEMP={:.1f}C HUM={:.1f}%'.format(TEMP, HUM))
else:
    print('try again for reading')
```

# 5.21.2 Recipe to Read DHT11 Sensor and Display on LCD

```python
import time as wait
import Adafruit_Char as RAJ_LCD
import Adafruit_DHT as RAJ_DHT
```

RAJ_sensor_name = RAJ_DHT.DHT11 #we are using the DHT11 sensor
RAJ_sensor_pin = 17 # assign variable to pin 17
RAJ_lcd_rs = 26 # assign name to pin 26 where RS pin is connected
RAJ_lcd_en = 19#assign name to pin 26 where E pin is connected
RAJ_lcd_d4 = 13 #assign name to pin 26 where D4 pin is connected
RAJ_lcd_d5 = 6 #assign name to pin 26 where D5 pin is connected
RAJ_lcd_d6 = 5 #assign name to pin 26 where D6 pin is connected
RAJ_lcd_d7 = 21 #assign name to pin 26 where D7 pin is connected
RAJ_lcd_backlight = 0
RAJ_lcd_columns = 20
RAJ_lcd_rows = 4
RAJ_lcd = RAJ_LCD.Char(RAJ_lcd_rs, RAJ_lcd_en, RAJ_lcd_d4, RAJ_lcd_d5, RAJ_lcd_d6, RAJ_lcd_d7, RAJ_lcd_columns, RAJ_lcd_rows, RAJ_lcd_backlight)
#provide pin details to LCD library
RAJ_lcd.message("VALUE FROM DHT11") #print message on LCD
wait.sleep(2) # delay of 2 sec

def main():
    pass

whilewhile True:
    HUM, TEMP = RAJ_DHT.retry(RAJ_sensor_name, RAJ_sensor_pin)
    if HUM is not None and TEMP is not None:
        RAJ_lcd.clear(#clear the contents of LCD
        RAJ_lcd.message("%.1f C %% TEMP") #print temp value on LCD
        RAJ_lcd.message("\nHum=%.1f %% HUM") #print hum value on LCD
    else:
        print('try again for reading')
    wait.sleep(2)
