```
RAJ.setup(ledPin2, RAJ.OUT) # Set ledPin2 as output
def loop():
    while True:
        print("BOTH LED on") # print string on terminal
        RAJ.output(ledPin1, RAJ.HIGH) # turn on LED1
        RAJ.output(ledPin2, RAJ.HIGH) # turn on LED2
        wait.sleep(1.0) # delay of 1 Sec
        print("BOTH LED off") # print string on terminal
        RAJ.output(ledPin1, RAJ.LOW) # turn off LED1
        RAJ.output(ledPin2, RAJ.LOW) # turn off LED2
        wait.sleep(1.0) # wait 1 sec
defendprogram():
    RAJ.output(ledPin1, RAJ.LOW) # turn off LED1
    RAJ.output(ledPin2, RAJ.LOW) #turn off LED2
    RAJ.cleanup() # clean GPIOs
if __name__ == '__main__': # Main program to call functions
    setup()
    try:
        loop()
    except KeyboardInterrupt: # keyboard interrupt to stop program
        endprogram()
```

#  5.15 Reading the Digital Input

The digital inputs at the Raspberry Pi can be read by two methods named as pull down and pull up, by setting the GPIO pins as active LOW or active HIGH output.

```
import RPi.GPIO as RAJ
RAJ.setup(23, RAJ.IN, pull_up_down=RAJ.PUD_DOWN)
RAJ.setup(24, RAJ.IN, pull_up_down=RAJ.PUD_UP)
```

These commands enable a pull-down resistor on pin 23 and a pull-up resistor on pin 24. The Pi is looking for a high voltage on pin 23 and a low voltage on pin 24. They are required to define in the loop, so that these can constantly check the pin voltage. To understand the concept, consider a small program for switch.