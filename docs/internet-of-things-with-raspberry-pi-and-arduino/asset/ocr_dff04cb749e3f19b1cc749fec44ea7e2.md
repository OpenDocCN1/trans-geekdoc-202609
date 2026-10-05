# Internet of Things with Raspberry Pi and Arduino

![](bbox=[0.219, 0.131, 0.776, 0.417])

FIGURE 10.12
Air level data on ThingSpeak server.

+   - Connect pin(OUT) of MQ2 sensor to pin(A1) of Arduino Uno.
- Connect pin(OUT) of MQ3 sensor to pin(A3) of Arduino Uno.
- Connect pin(OUT) of MQ7 sensor to pin(A0) of Arduino Uno.
- Connect pin(OUT) of GP2Y1030 sensor to pin(A4) of Arduino Uno.

# 10.3.1 Recipe

```
import sys # import sys library
import urllib # add url library
import pyfirmata # add pyfirmata library
import Adafruit_DHT as RAJ_DHT
import time as wait # import time library
import RPi.GPIO as RAJ # import ri GPIO library
from picamera import PiCamera # import picamera library
nboard = pyfirmata.Arduino('/dev/ttyUSB0') # USB com number
led_Power = board.get_pin('d:12:o') # connect led_power pin to 12 pin
of Arduino as output
```