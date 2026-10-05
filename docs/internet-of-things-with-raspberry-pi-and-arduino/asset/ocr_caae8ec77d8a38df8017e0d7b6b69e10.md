# Basics of Raspberry Pi

![](bbox=[0.218, 0.093, 0.782, 0.452])

FIGURE 5.34
Circuit diagram for the interfacing of DHT11S.

Figure 5.34 shows the circuit diagram for the interfacing of LCD and DHT11 with Raspberry Pi.

# 5.21.1 Recipe to Read DHT11 Sensor

```
import Adafruit_DHT as RAJ_DHT
import time as wait
RAJ_sensor = RAJ_DHT.DHT11
RAJ_gpio = 17 # assignment variable to pin 17
HUM, TEMP = RAJ_DHT.read_retry(RAJ_sensor, RAJ_gpio)
if humidity is not None and temperature is not None:
    print('TEMP={0.1f}C HUM={0.1f}%'.format(TEMP, HUM))
    wait.sleep(0.2)
else:
    print('try again for reading from DHT11')
    wait.sleep(0.2)
```

# 5.21.2 Recipe to Read DHT11 Sensor and Display Data on LCD

```
import time as wait time library
import Adafruit_CharLCD as RAJ_LCD #Import the LCD library
import Adafruit_DHTas RAJ_DHT #Import DHT library
```