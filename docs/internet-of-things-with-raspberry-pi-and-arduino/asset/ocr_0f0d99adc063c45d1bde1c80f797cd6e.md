# Smart IoT Systems

# 161

![](bbox=[0.188, 0.105, 0.863, 0.453])

Figure 10.6

Circuit diagram for interlacing ultrasonic sensor with Raspberry Pi.

ultrasonic sensor to +5 V and ground, Connect pin(TRIG) and pin(ECHO) of the ultrasonic sensor to GPIO20 and GPIO(21) of Raspberry Pi, respectively (Figure 10.6). Provide a “HIGH” signal to “TRIG” input, for at least 10-µS duration. This process will enable the module to transmit eight 40-KH ultrasonic waves. If any obstacle is in the way of the waves, these are reflected back to the “ECHO” pin. The time taken by pulse is accurately for to-and-fro travel of ultrasonic signals, is taken as Time/2. Distance = Speed * Time/2; here speed of sound at sea level = 343 m/s or 340 cm/s. Follow the steps described in Section 10.1.2 to create the Thing speaker, write the program described in Section 10.2.1, and check the results.

# 10.2.1 Recipe

```
import time as wait ### add time library
import RPi.GPIO as ANITA # add pi GPIO library
import sys # add sys library
import urllib2 # add urllib
my_API = 'F1MAEAF943TLMVTC!'
defget_sensor_data():
ANITA.setmode(ANITA.BOARD) # use pi in board mode
```