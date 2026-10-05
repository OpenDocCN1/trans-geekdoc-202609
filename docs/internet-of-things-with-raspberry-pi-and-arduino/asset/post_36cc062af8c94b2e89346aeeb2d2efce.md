
# Raspberry Pi and Arduino

![](img/526b5ff9486ff530988203e0cd92330a_123_0.png)

Figure 6.5
Circuit diagram for LDR sensor interfacing with Arduino.

# LCD connection

- Connect Arduino digital pin 13 to RS pin(4) of LCD.
- Connect Arduino digital pin GND to RW pin(5) of LCD.
- Connect Arduino digital pin 12 to E pin(6) of LCD.
- Connect Arduino digital pin 11 to D4 pin(11) of LCD.
- Connect Arduino digital pin 10 to D5 pin(12) of LCD.
- Connect Arduino digital pin 9 to D6 pin(13) of LCD.
- Connect Arduino digital pin 8 to D7 pin(14) of LCD.

### 6.3.2 Sketch

```cpp
#include <LiquidCrystal.h> // include library of LCD
LiquidCrystal lcd(13, 12, 11, 10, 9, 8); // attach LCD pin RS,E,D4,D5,D6,D7
to the given pins
int LDR_sensor_Pin = A0; // select the input pin for the potentiometer
int LDR_sensor_ADC_Value = 0; // variable to store the value coming
from the sensor
int RED_LED=7; // assign pin 7 to RED_LED
```

# Internet of Things with Raspberry Pi and Arduino

```cpp
void setup()
{
    lcd.begin(20
```

# Raspberry Pi and Arduino

## 6.4 Play with Actuators

An actuator is a component of a machine that is used for moving and controlling a mechanism or system. A DC motor, stepper motor, and servo motor are commonly used actuators in the systems.

### 6.4.1 DC Motor

The DC-geared motors with 100 rpm 12 V are generally used for robotics applications. They are very easy to use. They have nuts and threads on the shafts to easily connect and internally threaded shafts for easy connection to the wheel. Figure 6.6 shows the block diagram to interface the DC motor with Arduino. It is comprised of an Arduino Uno, a power supply, liquid crystal display, a motor driver (L293D), and two DC motors.

### 6.4.1 Circuit Diagram

Connect the components as shown in Figure 6.7 to check the workings of a DC motor. Upload the program described in Section 6.4.1.2 and check the workings.

![](img/526b5ff9486ff530988203e0cd92330a_125_0.png)

FIGURE 6.6
Block diagram of DC motor interfacing with Arduino.

![](img/526b5ff9486ff530988203e0cd92330a_126_0.png)

FIGURE 6.7
Circuit diagram of DC motor interfacing with Arduino.

# L293D and DC motor connection

- Connect L293D pin 3 to +ve pin of DC motor1.
- Connect L293D pin 6 to -ve pin of DC motor1.
- Connect L293D pin 11 to +ve pin of DC motor2.
- Connect L293D pin 14 to +ve pin of DC motor2.

L293D connection

- Connect Arduino GND to pins 4, 5, 12, 13 of L293D.
- Connect Arduino +5 V to pins 1, 9, 16 of L293D.
- Connect Arduino pin 7 to pin 2 of L293D.
- Connect Arduino pin 6 to pin 7 of L293D.
- Connect Arduino pin 5 to pin 10 of L293D.
- Connect Arduino pin 4 to pin 15 of L293D.
- Connect L293D pin 8 to +ve of 12V battery

# LED connection

- Connect Arduino pin 7 to anode of LED1.
- Connect Arduino pin 6 to anode of LED2.
- Connect Arduino pin 5 to anode of LED3.
- Connect Arduino pin 4 to anode of LCD4.
- Connect cathode of all LEDs to ground.

# LCD connection

- Connect Arduino digital pin 13 to RS pin(4) of LCD.
- Connect Arduino digital pin GND to RW pin(5) of LCD.
- Connect Arduino digital pin 12 to E pin(6) of LCD.
- Connect Arduino digital pin 11 to D4 pin(11) of LCD.
- Connect Arduino digital pin 10 to D5 pin(12) of LCD.
- Connect Arduino digital pin 9 to D6 pin(13) of LCD.
- Connect Arduino digital pin 8 to D7 pin(14) of LCD.

### 6.4.1.2 Sketch

```cpp
#include<LiquidCrystal.h> // include library of LCD
LiquidCrystal lcd(13, 12, 11, 10, 8); // attach LCD pin to RS, E, D4, D5, D6,
D7 to the given pins
int MPIN1=7; // assign pin 7 as MPIN1
int MPIN2=6; // assign pin 6 as MPIN2
int MPIN3=5; // assign pin 5 as MPIN3
int MPIN4=4; // assign pin 4 as MPIN4
```

```cpp
void setup()
{
    pinMode(MPIN1, OUTPUT); // make MPIN1 as an output
    pinMode(MPIN2, OUTPUT); // make MPIN2 as an output
    pinMode(MPIN3, OUTPUT); // make MPIN3 as an output
    pinMode(MPIN4, OUTPUT); // make MPIN4 as an output
    lcd.begin(20,4); // initialise LCD
    lcd.setCursor(0, 0); // set cursor on LCD
    lcd.print("DC Motor direction"); // print string on LCD
    lcd.setCursor(0, 1); // set cursor on LCD
    lcd.print("control system..."); // print string on LCD
    delay(1000); // delay of 1000
    lcd.clear();
}

void loop()
{
    digitalWrite(MPIN1, HIGH);
    digitalWrite(MPIN2, LOW);
    digitalWrite(MPIN3, LOW);
    digitalWrite(MPIN4, LOW);
    lcd.setCursor(0, 0);
    lcd.print("CLOCKWISE");
    delay(2000);
    lcd.clear();

    digitalWrite(MPIN1, LOW);
    digitalWrite(MPIN2, HIGH);
    digitalWrite(MPIN3, LOW);
    digitalWrite(MPIN4, LOW);
    lcd.setCursor(0, 0);
    lcd.print("ANTI-CLOCKWISE");
    delay(2000);
    lcd.clear();

    digitalWrite(MPIN1, LOW);
    digitalWrite(MPIN2, LOW);
    digitalWrite(MPIN3, HIGH);
    digitalWrite(MPIN4, LOW);
    lcd.setCursor(0, 0);
    lcd.print("LEFT");
    delay(2000);
    lcd.clear();

    digitalWrite(MPIN1, LOW);
    digitalWrite(MPIN2, LOW);
    digitalWrite(MPIN3, LOW);
    digitalWrite(MPIN4, HIGH);
    lcd.setCursor(0, 0);
    lcd.print("RIGHT");
    delay(2000);
    lcd.clear();
}
```

## 6.4.2 Servo Motor

Servo motor is a rotary actuator used for precise position control. This is a closed-loop operation. The torque standard with metal gears can provide 360° rotation. Figure 6.8 shows the block diagram to interface the servo with Arduino. It also requires a feedback sensor.

![](img/526b5ff9486ff530988203e0cd92330a_129_0.png)

FIGURE 6.8
Block diagram to interface with Arduino.

### 6.4.2.1 Circuit Diagram

Connect the components as shown in Figure 6.9 to check the workings of a servo motor.

# Servo connection

- Connect Arduino GND to GND of servo.
- Connect Arduino +5 V to “+\” terminal of servo.
- Connect Arduino pin(3) to PWM pin of servo.

# POT connection

- Connect Arduino GND to GND of POT.
- Connect Arduino +5 V to “+\” terminal of POT.
- Connect Arduino A0 to data out pin of POT.

![](img/526b5ff9486ff530988203e0cd92330a_130_0.png)

FIGURE 6.9
Circuit diagram to interface servo motor with Arduino.
