# Step 3:

+   Arduino:
+   * Connect 5V to the bottom positive (red) power rail on the breadboard.
+   * Connect GND to the bottom negative (black) ground rail on the breadboard.
+   * Connect the bottom negative (black) ground rail on the breadboard to the top negative (black) ground rail on the breadboard.

+   Potentiometer:
+   * Connect Terminal 1 to the ground (GND) on the Arduino.
+   * Connect Terminal 2 to the 5V on the Arduino.
+   * Connect Wiper to A0.

+   9V battery:
+   * Connect the positive terminal of the battery to the top positive (red) power rail on the breadboard.
+   * Connect the negative terminal of the battery to the top negative (black) ground rail on the breadboard.

+   H-Bridge motor driver (L293D):
+   * Place it, ensuring that it straddles the centre gap between the two sides of the breadboard.
+   * Connect "Enable 1 & 2" to the 5V on the Arduino.
+   * Connect Power 1 to the 9V on the battery.
+   * Connect all four ground pins to the GND.
+   * Connect Power 2 to the top positive (red) rail on the breadboard.
+   * Connect Input 1 to pin 5 on the Arduino.
+   * Connect Input 2 to pin 6 on the Arduino.

+   DC motor:
+   * Connect Terminal 1 to Output 2 on the L293D.
+   * Connect Terminal 2 to Output 1 on the L293D.

![](bbox=[0.095, 0.455, 0.905, 0.745])

```
C++
int potValue; // Variable to store the potentiometer input value
int maximumSpeed = 128; // Maximum motor speed (should not be exceeded)
int forwardPin = 5; // Pin connected to the forward control input on the
// motor driver
int reversePin = 6; // Pin connected to the reverse control input on the
// motor driver
```