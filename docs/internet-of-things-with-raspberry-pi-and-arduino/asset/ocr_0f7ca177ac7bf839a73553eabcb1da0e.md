# Basics of Raspberry Pi

![](bbox=[0.118, 0.093, 0.835, 0.463])

FIGURE 5.23
Circuit diagram of the Raspberry Pi interfacing with LED.

```
print("Two LED ON") # print string on terminal
wait.sleep(1)
RAJ.output(LED_PIN1, False) make pin 20 to LOW
RAJ.output(LED_PIN2, False) make pin 20 to LOW
print("Two LED OFF") # print string on terminal
wait.sleep(1)
exceptbyKeyboardInterrupt:
RAJ.cleanup()
```

# 5.14.1.1 Recipe for LED Blink Using GPIO Function

```
importRPI.GPIO as RAJ # RPI.GPIO can be referred as GPIO
import time as wait # import time library
ledPin1 = 21 # connect led1 on 21 pin
ledPin2 = 20 # connect led2 on 20 pin
def setup():
RAJ.setmode(RAJ.BOARD) # GPIO Numbering of Pins
RAJ.setup(ledPin1, RAJ.OUT) # Set ledPin1 as output
```