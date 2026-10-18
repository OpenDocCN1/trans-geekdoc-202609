
# 11.4 Circuit Diagram

## 11.4.1 Major Components Used

- `MICROCONTROLLER 8051`
- `IR TRANSCEIVER AND RECEIVER LED Setup`
- `WHITE LEDS`
- `PCB BOARD COMPONENTS`
- `MICROCONTROLLER`

The project uses `AT89S52` microcontroller to read in the inputs from series of `IR transmitter & receiver` signals.

- `IR SETUP:`

As you pass any object via the `IR setup`, each `IR setup` will sense the object/vehicle and send a signal to the microcontroller.

- `WHITE LED's:`

Based on vehicle presence, `8051` will turn on a set of white LEDs, which act like street lights.

- As the object passes by another `IR setup`, only a certain number of LEDs are turned on, keeping the energy consumption at minimum.

- Once the vehicle passes out of the last `IR setup`, all the LEDs turn OFF.

COMPONENTS SOLDERED IN PCB BOARD:

- `AT89S52-MICROCONTROLLER`
- `ON-OFF SWITCH WITH RED LED`
- `RESISTORS`
- `AC CABLE`
- `IR BLACK LEDs`
- `IR RECEIVER`
- `IR TRANSMITTER`
- `CAPACITOR.`
- `WHITE LED`
- `IR BLUE`

# 11.5 Architecture Diagram

The path is the important thing, which we will be focused on in this system. Because creating the path (a small gap) in the printed circuit board between `IR BLACK` & `BLUE` LEDs will be the object detection done by the system. The `WHITE LEDs` will be in series connected with the `IR transmitter` and `receiver`, which will detect the object when it passes through the path and displays the output through white LEDs. A flowchart of the discussed proposal is shown in [Figure 11.2](#ch11.xhtml#fig11_2).

![Figure 11.2 Flowchart.](Images/fig11_2.jpg)

[Figure 11.2 Flowchart.](#ch11.xhtml#fg11_2)

# 11.6 Proposed Work

In an automatic street light control system, the main components required to build the necessary circuit is Microcontroller `AT89S52`, `IR setup` for the white LEDs to glow brighter, dim or switched off. This system is completely focused on optimum utilization of street lamps with the main objective of saving energy. Because at night, most of the energy is wasted when there is no detection of pedestrians or automobiles, but the street lights still glow brighter. Keep this in mind as we build this system.

Building the circuit with necessary capacitors, resistors, power supply switch with red LED, `AC cable`, `IR setup` with `blue & black LEDs` that act as a path, white LEDs, and Microcontroller `AT89S52` being soldered in PCB. The `IR setup` transmits and receives signals from the path sending the information to the microcontroller. Based on the microcontroller instruction, the street lights perform modes of operation in projecting light in bright, dim, and dark. This is how our implemented system works by using `IR sensors` based on pedestrian or automobile detection on roads.

## 11.6.1 Instructions

- Connect the `AC cable` & turn the slide switch `ON` (the red LED should glow)

- Now pass your finger/any object through the passage between `IR blue` & `black LEDs`.

- As you keep passing your fingers, white LEDs will turn `ON`, illuminating the path ahead for you.

- Once you move out of the last `IR setup`, the top four white LEDs will be on for a few seconds and finally turn `OFF`.

# 11.7 Results and Discussion

The proposed system uses `AT89S52 Microcontroller` with `IR setup` based vehicle detection. The images of the implemented system's `IR setup` and two phases of operation results are shown.

The circuit board have been built and necessary components have been soldered, as shown in [Figure 11.3](#ch11.xhtml#fig11_3). After testing, we perform the operations in order to predict the output. In this system, it basically has two phases for street light system from dark mode to bright mode, as shown in [Figure 11.4,](#ch11.xhtml#fig11_4) as well as showing transition when the pedestrian moves, shown in [Figure 11.5](#ch11.xhtml#fig11_5).

![Figure 11.3 Automatic street light control system IR arrangement setup.](Images/fig11_3.jpg)

[Figure 11.3 Automatic street light control system IR arrangement setup.](#ch11.xhtml#fg11_3)

![Figure 11.4 Phase I.](Images/fig11_4.jpg)

[Figure 11.4 Phase I.](#ch11.xhtml#fg11_4)

![Figure 11.5 Phase II.](Images/fig11_5.jpg)

[Figure 11.5 Phase II.](#ch11.xhtml#fg11_5)

Street lights perform from dark mode to bright mode for fewer detection of pedestrian and automobile as shown in Figure 11.4. Street lights perform dull mode to bright mode for more detection of pedestrian and automobile in Figure 11.5. The automatic street light control system, when connected to the power supply, where `10 V DC` voltage is given to the circuit where input is `5 V` and the LEDs output is approximately `3 V`, which is verified in voltmeter in [Figure 11.6](#ch11.xhtml#fig11_6).

![Figure 11.6 Measurement using voltmeter.](Images/fig11_6.jpg)

[Figure 11.6 Measurement using voltmeter.](#ch11.xhtml#fg11_6)
