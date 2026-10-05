# Basics of Raspberry Pi

```
RAJ_lcd_byte(ord(message[ij]),RAJ_LCD_CHR
def main():
RAJ_lcd_init()
while True:
RAJ_lcd_string("I2C LCD<\
```

# 5.21 Interfacing of DHT11 Sensor with Raspberry Pi

The DHT11 sensor works with a one-wire system. The temperature and humidity values are measured by the sensor, and this data is communicated serially through the output pin. It is a four-pin device. A resistor of value 4.4-10 K needs to be placed between pin 1 (3.3 V) and pin 2 (Data). The three-pin device has a built-in resistor (Figure 5.33).

The Adafruit DHT11 library can be used for DHT11, DHT22, or any other one-wire temperature sensor. The procedure to install the DHT11 library is similar to the steps followed for installing the LCD library.

# Steps to interface DHT11

+   1. Update the package lists and install the Python libraries with the help of commands:
   sudo apt-get update
   sudo apt-get install build-essential python-dev