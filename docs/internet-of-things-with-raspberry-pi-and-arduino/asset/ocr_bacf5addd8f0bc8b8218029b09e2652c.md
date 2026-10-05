# Internet of Things with Raspberry Pi and Arduino

![](bbox=[0.143, 0.115, 0.875, 0.442])

**Figure 6.3**nCircuit diagram for PIR interfacing with Arduino.

+   - Connect Arduino digital pin (9) to D6 pin(13) of LCD.
- Connect Arduino digital pin (8) to D7 pin(14) of LCD.

LED connection

+   - Connect Arduino digital pin 7 to anode of RED-LED through 330-ohm resistor.
- Connect Arduino digital pin 6 to anode BLUE-LED through 330-ohm resistor.
- Connect cathode of all LEDs to Ground.

# 6.2.3 Sketch

```
#include <LiquidCrystal.h> // include library of LCD
LiquidCrystallcd(3, 12, 11, 10, 9, 8); // attach LCD pin RS,E4,D5,D6,D7
to the given pins
int PIR_SENSOR_LOW=5; // assign pin 5 as PIR_SENSOR_LOW
int RED_LED=7; // assign pin 7 as RED_LED
int BLUE_LED=6; // assign pin 6 as BLUE_LED
void setup()
[
```