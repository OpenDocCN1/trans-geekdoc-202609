# Internet of Things with Raspberry Pi and Arduino

![](bbox=[0.143, 0.105, 0.856, 0.303])

FIGURE 7.5
Circuit diagram for potentiometer interfacing.

Read the analog pin, iteratorthread is used in the main loop.
This class is defined in the util module of the Pyfirmata package and is imported before getting it utilized in the code:

```
from pyfirmata import Arduino, util
# Setting up the Arduino board
port = 'COM3'
board = Arduino(port)
sleep(5)
it = util.Iterator(board) # Start Iterator to avoid serial overflow
it.start())
board.analog[3].enable_reporting()
```

# 7.6.1 Recipe

```
import pyfirmata # import library of pyfirmata
import time as we # import library of time
board = pyfirmata.Arduino('/dev/ttyUSB0') # define COM port of
Arduino
POT_pin = board.get_pin('a:0:i') # assign A0 pin as it
it = pyfirmata.util.Iterator(board) # use iterator
it.start() # start iterator
POT_pin.enable_reporting() # enable pin
while True: ## infinite loop
POT_reading = POT_pin.read() # read analog pin
```