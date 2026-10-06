# Blockchain-Based Parking System using IoT

# TABLE 6.3

# Testing for Hardware Requirements

| Test ID | Description | Status |
| --- | --- | --- |
| T1-1 | To check whether Arduino IDE is installed in the Arduino. | PASS |
| T1-2 | To check whether Arduino IDE opens properly. | PASS |
| T1-3 | To check whether it implemented the code for Arduino board. | PASS |
| T1-4 | To check whether the implemented Arduino board code is executed. | PASS |
| T1-5 | To check whether code is implemented on the web server. | PASS |
| T1-6 | To check whether the implemented web server integrates with the Arduino board. | PASS |
| T1-7 | To check whether the web server displays the slot status. | PASS |
| T1-8 | To check whether the server allows user to choose the location. | PASS |
| T1-9 | To check whether the server allows user to select a particular area. | PASS |
| T1-10 | To check whether the system updates every 3 minutes. | PASS |
| T1-11 | To check whether the Arduino board works properly. | PASS |
| T2-1 | To check whether the ESP8266 NodeMCU is working properly | PASS |
| T2-2 | To check whether the servomotor is working properly. | PASS |
| T2-3 | To check whether the infrared (IR) sensor works properly. | PASS |
| T2-4 | To check whether the LCD display is working properly | PASS |
| T2-5 | To check whether the servomotor opens and closes an exit gate. | PASS |
| T2-6 | To check whether IR sensors sense the object correctly. | PASS |
| T2-7 | To check whether LCD displays the slot status correctly. | PASS |
| T2-8 | To check whether ESP8266 NodeMCU integrates with the web server. | PASS |

# SOURCE CODE

# Arduino IMPLEMENTATION

```
#include <Servo.h> #include <LiquidCrystal.h>
LiquidCrystal lcd(12, 11, 5, 4, 3, 2); const int analogInPin = A0;
int sensorValue = 0; int servoPin = 10; int i = 90;
Servo servo;
const int analogIn1 = A1; int sensorValue1 = 0;
int servoPin1 = 9; int i = 90;
Servo servo;
const int analogIn2 = A2; int sensorValue2 = 0;
const int analogIn3 = A3; int sensorValue3 = 0;
const int analogIn4 = A4;
int sensorValue4 = 0;
const int analogIn5 = A5; int sensorValue5 = 0;
int LIGHT1 = 13; int LIGHT2 = 8; int LIGHT3 = 7; int LIGHT4 = 6;
```