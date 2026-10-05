# 254 Transforming Healthcare

Here, P is the coefficient.

The webcam captures frames through image processing using OpenCV, detecting and analyzing the landmarks to determine the finger positions within a defined region of hand landmarks. The resulting finger states are converted into digital format and sent via serial communication to an Arduino board. The Arduino UNO controls the arm by sending command signals to the servo motor driver. The servo motor driver interprets these signals and deflects the fingers of the arm according to the specified motion. Springs facilitate the "back-and-forth motion, and an SMPS provides the main power supply to the motors. For sent PWM signals to 5 motors' servo PWM pins (digital pins marked with a tilde) in Arduino UNO are connected to the signal pins of the motor driver. The servo motors' pins are also connected to the motor driver regarding their power, signal, and ground pins. The prototype of the robotic hand is shown in Figure 12.4.

The whole circuit is powered by an SMPS, which supplies 12 V connected to the customized motor driver. The pins can be connected according to your choice, but they must all be PWM signals and the corresponding servo motor pins must be connected accordingly. The Python software tracks and detects landmarks in real time using Medapipe and OpenCV to process and record webcam video. This script shows how to use the OpenCV, Medapipe, and PySerial libraries to set up image processing and hardware connection applications. The definition of the function calculate_angle is to determine the angle between three locations.

To update the hand state array depending on the finger bending status, a function called update_hand_state is defined. When a serial port becomes available, set up serial communication and ask the user to choose one. Set up the Medapipe handles module so that hands may be tracked and detected. This activates the built-in camera to start recording video and draws

![](bbox=[0.148, 0.663, 0.849, 0.856])

Figure 12.4 Prototype of the robotic hand.