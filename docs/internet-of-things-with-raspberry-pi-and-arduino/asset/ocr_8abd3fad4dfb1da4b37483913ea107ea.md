# Python and Arduino with Pyfmata

# 7.3.1 Recipe

import pyfmata # import lib of pyfmata
import time as wait # import lib of pyfmata
board = pyfmata.Arduino('/dev/ttyUSB0')# define COM port of Arduino
red_pin = board.pin(d:7)# assign digital pin 7 as an output
green_pin = board.pin(d:6o)# assign digital pin 6 as an output

```
while True:
    infinite loop
        red_pin.write(1)## write 'I' on pin 7
        green_pin.write(1)## write 'I' on pin 6
        wait.sleep(0.5)# delay of 0.5 Sec
        red_pin.write(0)## write 'O' on pin 7
        green_pin.write(0)## write 'O' on pin 6
        wait.sleep(0.5)# delay of 0.5 Sec
```

# 7.4 Reading an Arduino Digital Input with Pyfmata

The objective is to read the digital pins of Arduino on a Raspberry Pi by Python. Pyfmata is used to read a digital input on Arduino. The components required for the recipe are Arduino Uno, 1 kΩ resistor, and a push switch or button (as sensor). Switch can be connected in two arrangements: pull down and pull up. The output of a digital pin of Arduino is normally “LOW,” and digital sensors are available in two configurations for output: active “LOW” and active “HIGH.” The pull-down arrangement is used where digital pin normally “LOW,” and on reading it gets “HIGH.” This is used for the sensor that has the active “HIGH” on occurrence of an event; otherwise, the output is “LOW.” The pull-up arrangement is for the sensor that has a normal output as “HIGH,” and on occurrence of an event gets “LOW.” The digital pin needs to be activated as “HIGH” in the program so that it can read the sensor. Figure 7.2 shows circuit diagram for pull down, and Figure 7.3 shows circuit diagram for pull up.

As discussed in Section II of this, the Pyfmata protocol is used to read the input pin of Arduino by Raspberry Pi. It uses the concept of an iterator to monitor the Arduino pin. The iterator manages the reading of the switch using the following commands:

```
it = pyfmata.util. Iterator(board)
it.start()
```