
![](img/526b5ff9486ff530988203e0cd92330a_146_0.png)

# 8 Python GUI with Tkinter and Arduino

## 8.1 Tkinter for GUI Design

The basic features for graphical user interface (GUI) libraries include the easy to install and minimal computations. Tkinter framework satisfies the basic requirements. It is also the default GUI library with the Python installations. Tkinter interface is a cross-platform Python interface for the Tk GUI toolkit. Tkinter provides a layer on Python while Tk provides the graphical widgets. Tkinter is a cross-platform library that gets deployed as a part of the Python installation packages for many operating systems.

Tkinter is designed with minimal programming efforts for creating graphical applications. To test the version of the Tk toolkit, use the following commands on the Python prompt:

```python
>>> import Tkinter
>>> Tkinter._test()
```

An image with the version information will be prompted (Figure 8.1). If the window (Figure 8.1) is not visible, then reinstall Python.

The Tk interface supports various widgets to develop GUI. Table 8.1 describes the few widgets.

## 8.2 LED Blink

To understand the working of LED with Tkinter GUI, a simple circuit is designed. The system is comprised of a Raspberry Pi, an Arduino, an LED, and a power supply. An Arduino is connected to Raspberry Pi through a USB connector. The anode terminal of LED is connected to pin(7) of Arduino through a 10-K resistor, and the cathode terminal is connected to the ground.

Figure 8.2 shows the circuit diagram to interface LED.

![](img/526b5ff9486ff530988203e0cd92330a_148_0.png)

FIGURE 8.1
Tk version.

# TABLE 8.1
The Tkinter Widgets to Develop GUI

| Widget | Description |
| --- | --- |
| Tk() | Root widget need in every program |
| Label() | It shows an image or a text |
| Button() | Execute actions |
| Entry() | Text field to provide inputs |
| Scale() | It provides a numeric value by dragging the slider |
| Checkbox() | It enables toggling between two values |

![](img/526b5ff9486ff530988203e0cd92330a_148_1.png)

FIGURE 8.2
Circuit diagram to interface LED.

# Python GUI with Tkinter and Arduino

### 8.2.1 Recipe for LED Blinking with Fixed Time Delay

```python
import Tkinter
import pyfirmata
import time as wait
# Associate port and board with pyfirmata
board = pyfirmata.Arduino('/dev/ttyUSB0')
wait.sleep(5) # delay of 5Sec
led_Pin = board.get_pin('d:7') # connect to pin 7 and use as output
def call_LED_BLINK():
    button.config(state = Tkinter.DISABLED)
    led_Pin.write(1) # make led_Pin to HIGH
    print('LED at pin7 is ON') # print on terminal
    wait.sleep(5) # delay of 5 sec
    print('LED at pin7 is OFF') # print on terminal
    led_Pin.write(0) # make led_Pin to LOW
    button.config(state=Tkinter.ACTIVE)
# Initialize main window with title and size
TOP = Tkinter.Tk()
TOP.title("Blink LED using button")
TOP.minsize(300,30)
# Create a button on main window and associate it with above method
button = Tkinter.Button(TOP, text="Press start to blink", command = call_LED_BLINK)
button.pack()
TOP.mainloop()
```

### 8.2.1 Tkinter GUI for LED Blinking with Fixed Delay

Run the program described in Section 8.2.1, and a GUI will appear (Figure 8.3).

After pressing the "Press start to blink" button on GUI, it will print "LED at pin7 is ON" for 5 sec and print "LED at pin7 is OFF" (Figure 8.4).

### 8.2.2 Recipe for LED Blinking with Variable Delay

```python
import Tkinter
import pyfirmata
```

![](img/526b5ff9486ff530988203e0cd92330a_150_0.png)

FIGURE 8.3
Tkinter GUI to control LED with fixed delay.

```bash
pi@raspberrypi:~ nano pyfir_led_tkinter_BOOK.py
pi@raspberrypi:~ $ python pyfir_led_tkinter_BOOK.py
LED at pin7 is ON
LED at pin 7 is OFF
```

FIGURE 8.4
LED ON/OFF.

```python
import time as wait
board = pyfirmata.Arduino('/dev/ttyUSB0')
wait.sleep(5) # delay of 5 sec
led_Pin = board.get_pin('d:7') # connect led to pin 7 and used as output
def led_blink_variable_delay():
    # ... logic ...
    pass
```

(Note: The remaining text in the OCR contained redundant fragments and artifacts which have been cleaned up based on the logical flow provided above.)
