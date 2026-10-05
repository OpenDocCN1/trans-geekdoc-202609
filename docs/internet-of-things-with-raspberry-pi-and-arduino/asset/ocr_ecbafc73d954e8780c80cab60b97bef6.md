# Python GUI with Tkinter and Arduino

137

![](bbox=[0.218, 0.127, 0.781, 0.211])

FIGURE 8.10
Tkinter GUI for multiple LEDs.

```
@raspberrypi:~ $ name pyfirpy_two_led_tkinter_BOK.py
@raspberrypi:~ $ python pyfirpy_two_led_tkinter_BOK.py
start...
stop...
```

FIGURE 8.11
Screenshot for status window.

# 8.4.2 Tkinter GUI

To generate Tkinter GUI for multiple LEDs, run the program described in Section 8.4.1, and a window will appear (Figure 8.10). The GUI has two Checkbutton() widgets for each the red and green LED. The user can select the LEDs individually or together to make it start or stop (Figure 8.11).

# 8.5 Reading a PIR Sensor

A pyroelectric infrared (PIR) sensor is used to detect motion. A system is designed with a Raspberry Pi where two LEDs show the status of motion. If no motion is detected, the green LED will glow, and if motion is detected, an alert is generated with making the LED "ON." The system is made ON/OFF with Tkinter GUI. The status of sensors prints on the Python prompt. The system is comprised of a Raspberry Pi, an Arduino, two LEDs, a PIR sensor, and a power supply. Arduino is connected to Raspberry Pi through a USB. The anode terminal of LED1 and LED2 are connected to pin (7) and pin(6) of Arduino, respectively. the pin (OUT) of the PIR sensor is connected to pin (8) of Arduino, and pin (Vcc) and pin (GND) are connected to +5 V DC and ground, respectively (Figure 8.12).

# 8.5.1 Recipe to Read PIR Sensor

+   - Define custom function to perform Blink action
def blink_LED(pin, message):