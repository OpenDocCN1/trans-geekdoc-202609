
## Automatic doors

An automatic-door system uses a control system to manage the opening and closing of doors by processing input from sensors that detect the presence of people or objects near the entrance. These sensors, such as infrared motion detectors or pressure mats, send signals to the controller, which then decides when to open or close the doors.

The system operates using a closed-loop feedback mechanism. As soon as the sensors detect movement or pressure, they trigger the controller to open the doors. Once the person or object has passed through and the sensors no longer detect any presence, the controller signals the doors to close.

## REVIEW QUESTIONS

- 1 Describe how a control system operates in an autonomous vehicle. What components are involved, and how do they interact to ensure safe and efficient operation?
- 2 Compare the control system used in a home thermostat with that of an irrigation control system. What are the similarities and differences in how these systems maintain the desired environmental conditions?
- 3 Explain the importance of a closed-loop feedback mechanism in the operation of an automatic elevator control system. How does it ensure accurate and safe operation?
- 4 In the context of a traffic-signal control system, discuss how the control system adapts to changing traffic conditions. How does the use of sensors and feedback help in optimizing traffic flow?
- 5 Describe how a smart home-lighting system operates as a control system. Identify the key components, including the controller, sensors, actuators and feedback mechanism, and explain how they interact to automatically adjust the lighting in the home based on the time of day and occupancy.

## PROGRAMMING EXERCISES 1

- 1 Simulate a traffic-light control system. If you have access to an Arduino and the components, you can build this for real. Otherwise, you can use simulation software such as Tinkercad.

Tinkercad instructions:

- Step 1: Click on Circuits from the dashboard, and then click on Create new Circuit.
- Step 2: From the component library, search for and add the following components to your workspace:
  - [ ] One Arduino Uno R3 with breadboard
  - [ ] Three LEDs (Red, Yellow, Green) for one traffic light
  - [ ] Three resistors (220 ohms each)
  - [ ] Breadboard (optional, for better organization)
  - [ ] Pushbutton (optional, for triggering sensors)
- Step 3:
  - [ ] Red LED:
    - Connect the longer leg (anode – the bent leg) of the red LED to pin 13 on the Arduino.
    - Connect the other end of the resistor to the ground (GND) on the Arduino.
  - [ ] Yellow LED:
    - Connect the anode of the yellow LED to pin 12.
    - Connect the cathode to one end of a 220-ohm resistor.
    - Connect the other end of the resistor to GND.
  - [ ] Green LED:
    - Connect the anode of the green LED to pin 11.
    - Connect the cathode to one end of a 220-ohm resistor.
    - Connect the other end of the resistor to GND.
  - [ ] Step 4 (optional):
    - Place a pushbutton on the breadboard.
    - Connect one side of the pushbutton to 5V.
    - Connect the other side to a digital pin on the Arduino (e.g. pin 7).
    - Add a 10k-ohm resistor connecting the same side of the pushbutton to GND (which acts as a pull-down resistor).

## Set-up 1:

![](img/7f4ba44df9c5a19373dcc3ecd776c43a_107_0.png)

```cpp
// Pin assignments for LEDs
int redLED = 13;
int yellowLED = 12;
int greenLED = 11;
void setup() {
  // Set up the LED pins as outputs
  pinMode(redLED, OUTPUT);
  pinMode(yellowLED, OUTPUT);
  pinMode(greenLED, OUTPUT);
}
void loop() {
  // Turn on the green light for 5 seconds
  digitalWrite(greenLED, HIGH);
  delay(5000); // wait 5 seconds
  // Turn off green, turn on yellow for 2 seconds
  digitalWrite(greenLED, LOW);
  digitalWrite(yellowLED, HIGH);
  delay(2000); // wait 2 seconds
  // Turn off yellow, turn on red for 5 seconds
  digitalWrite(yellowLED, LOW);
  digitalWrite(redLED, HIGH);
  delay(5000); // wait 5 seconds
  // Turn off red, and repeat the cycle
  digitalWrite(redLED, LOW);
}
```

## Set-up 2 (with optional pushbutton):

![](img/7f4ba44df9c5a19373dcc3ecd776c43a_108_0.png)

```cpp
int buttonPin = 7; // Pin for the sensor (pushbutton)
int buttonState = 0;
int greenLED = 11; // Pin for green light
int yellowLED = 12; // Pin for yellow light
int redLED = 13; // Pin for red light
unsigned long previousMillis = 0; // Variable to store the last time the light
// changed
const long greenInterval = 5000; // Duration the green light stays on
// (in milliseconds)
const long yellowInterval = 2000; // Duration the yellow light stays on
// (in milliseconds)
const long redInterval = 5000; // Duration the red light stays on
// (in milliseconds)
// Define possible states for the traffic light
enum LightState { GREEN, YELLOW, RED};
LightState currentState = GREEN; // Start with the green light on
void setup() {
  pinMode(buttonPin, INPUT); // Set the pushbutton pin as an input
  pinMode(greenLED, OUTPUT); // Set the green LED pin as an output
  pinMode(yellowLED, OUTPUT); // Set the yellow LED pin as an output
  pinMode(redLED, OUTPUT); // Set the red LED pin as an output
  digitalWrite(greenLED, HIGH); // Initially turn on the green light
}
void loop() {
  unsigned long currentMillis = millis(); // Get the current time in milliseconds
  buttonState = digitalRead(buttonPin); // Read the state of the pushbutton
  switch(currentState) {
    case GREEN:
      // If the button is pressed or the green light has been on for the
      // full interval
      if (buttonState == HIGH || currentMillis - previousMillis >= greenInterval) {
        digitalWrite(greenLED, LOW); // Turn off the green light
        digitalWrite(yellowLED, HIGH); // Turn on the yellow light
        currentState = YELLOW; // Change the state to YELLOW
        previousMillis = currentMillis; // Reset the timer to the
        // current time
      }
      break;
    // The YELLOW and RED cases follow similar logic
    case YELLOW:
      if (currentMillis - previousMillis >= yellowInterval) {
        digitalWrite(yellowLED, LOW);
        digitalWrite(redLED, HIGH);
        currentState = RED;
        previousMillis = currentMillis; // Reset the timer to the
        // current time
      }
      break;
    case RED:
      if (currentMillis - previousMillis >= redInterval) {
        digitalWrite(redLED, LOW);
        digitalWrite(greenLED, HIGH);
        currentState = GREEN;
        previousMillis = currentMillis; // Reset the timer to the
        // current time
      }
      break;
  }
}
```

- 2 Observe how the control system manages the traffic-light sequence and adapts to changes (if a sensor is used).
- 3 Discuss how the components (LEDs, controller, optional sensor) work together as part of the control system.
- 4 Discuss the effectiveness of your traffic-light control system and how it could be improved or extended.

## PROGRAMMING EXERCISES 2

- 1 Simulate a motor control system where the speed of the motor is adjusted based on feedback from a sensor. It also has a maximum speed that is set in code and should not be exceeded by the motor. If you have access to an Arduino and the components, you can build this for real. Otherwise, you can use simulation software such as Tinkercad.

Tinkercad instructions:

- Step 1: Click on Circuits from the dashboard, and then click on Create new Circuit.
- Step 2: From the component library, search for and add the following components to your workspace:
  - One Arduino Uno R3 with breadboard
  - One potentiometer
  - H-Bridge motor driver (L293D)
  - One DC motor
  - One 9V battery

## Step 3:

- Arduino:
  - Connect 5V to the bottom positive (red) power rail on the breadboard.
  - Connect GND to the bottom negative (black) ground rail on the breadboard.
  - Connect the bottom negative (black) ground rail on the breadboard to the top negative (black) ground rail on the breadboard.

- Potentiometer:
  - Connect Terminal 1 to the ground (GND) on the Arduino.
  - Connect Terminal 2 to the 5V on the Arduino.
  - Connect Wiper to A0.

- 9V battery:
  - Connect the positive terminal of the battery to the top positive (red) power rail on the breadboard.
  - Connect the negative terminal of the battery to the top negative (black) ground rail on the breadboard.

- H-Bridge motor driver (L293D):
  - Place it, ensuring that it straddles the centre gap between the two sides of the breadboard.
  - Connect "Enable 1 & 2" to the 5V on the Arduino.
  - Connect Power 1 to the 9V on the battery.
  - Connect all four ground pins to the GND.
  - Connect Power 2 to the top positive (red) rail on the breadboard.
  - Connect Input 1 to pin 5 on the Arduino.
  - Connect Input 2 to pin 6 on the Arduino.

- DC motor:
  - Connect Terminal 1 to Output 2 on the L293D.
  - Connect Terminal 2 to Output 1 on the L293D.

![](img/7f4ba44df9c5a19373dcc3ecd776c43a_110_0.png)

```cpp
int potValue; // Variable to store the potentiometer input value
int maximumSpeed = 128; // Maximum motor speed (should not be exceeded)
int forwardPin = 5; // Pin connected to the forward control input on the motor driver
int reversePin = 6; // Pin connected to the reverse control input on the motor driver
```
