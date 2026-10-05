
# Introduction to Internet of Things

on the cloud. The system is suitable for a WSN-based solution with big data and computationally intensive requirement. An example is forest fire detection. The system is comprised of multiple nodes placed at different locations for monitoring temperature, humidity, and CO2 levels in the forest.

Level 6 IoT: A level 6 IoT is comprised of sensor nodes and actuator to perform sensing and controlling. It is a suitable cloud-based database designed for data analysis. The central controller knows the status of all end nodes and sends the control commands to the nodes. An example is a weather monitoring system. The system is comprised of multiple nodes that are placed at the different locations for monitoring temperature, humidity pressure, radiation, and wind speed. The sensor nodes are responsible for transmission of the data from end nodes to the destination via websocket. The data is stored on the cloud-based server. The data analysis is done on the cloud to make the prediction by aggregating the data.

# 1.6 IoT vs M2M

IoT can be defined as a system where multiple objects communicate with each other and share data through sensors and digital connectivity. Machine-to-machine (M2M) solutions are comprised of linear communication channels between the machines to make them work in a cycle. Here, the action of one machine triggers the activity of other.

# Differences between IoT and M2M

- A few experts define M2M as a subset of IoT, while others call the Internet of Things an evolved version of machine to machine. Either way, the conclusion is IoT is a broader area than M2M.

- Both the technologies work on the principle of connecting devices and make them to work together. While M2M relies on conventional connection tools like Wi-Fi, IoT has much flexibility and varied connectivity options.

- M2M solution has very limited scope and is confined to create a network of machines that work in synchronization. IoT creates 360° solutions for flexible responses and multi-level communication.

- The advantage of IoT over M2M is its ability to add interactivity amongst devices. Machine to operate by triggering responses based on an action. It is a one-way communication. IoT-based systems, communication flows to and fro freely.

![](img/526b5ff9486ff530988203e0cd92330a_30_0.png)

# 2
Sensors

## 2.1 Sensors Classification

Sensors are classified as follows:

- 1. Primary input quantity
- 2. Transduction principles
- 3. Technology and material
- 4. Property
- 5. Application

Classification of sensors can also be done on the basis of different areas:

- 1. Classification based on application: Sensors are chosen on the basis of application where they need to be implemented, such as industrial process control, measurement and automation, automobiles, consumer electronics, aircraft, and medical products. As with the change in application, the selection criteria changes, so the application needs to be considered.
- 2. Classification based on power or energy supply requirement
  Active sensor: Active sensors are those where a power supply is required to measure the physical quantity, e.g., temperature sensor, ultrasonic sensor, and light-dependent resistor (LDR).
  Passive sensor: Sensors that do not need a power supply are called passive sensors, and they measure the parameters, e.g., radiometers film photography.
- 3. Classification based on output of sensor
  Digital sensor: The output of sensor is in binary or digital form, which can be directly processed through a controller or processor.
  Analog sensors: The output of the sensor is in the form of a continuous signal. An analog-to-digital converter is required to read the sensor by microcontroller or processor.
- 4. Classification based on the type of sensor: There are several sensors available with different applications. Sensors can be categorized on the basis of types of sensors. A few types of sensors are discussed as follows:

  **Accelerometers:** Accelerometers are based on the technology named “microelectromechanical sensor.” They can be used in dynamic systems.

  **Biosensors:** Biosensors are based on the electrochemical technology. They can be used for medical care devices, water testing, food testing, etc.

  **Image sensors:** These are developed on the basics of the complete metal oxide semiconductor (CMOS) technique. These are widely used in video surveillance, biometrics, and traffic management.

  **Motion detectors:** Motion detectors are based on the infrared, ultrasonic, and microwave/radar technology. These are used in security purposes.

- 5. Classification based on property: The sensors are also classified on the basis of the property of the physical parameter. A few examples are as follows:

  **Temperature:** Thermocouples, thermistors, resistance temperature detectors (RTDs)
  **Flow:** Thermal mass, differential pressure, electromagnetic, positional displacement, etc.
  **Pressure:** Fiber optic, linear variable differential transformer (LVDT), elastic liquid-based manometers, vacuum, electronic
  **Level sensors:** Ultrasonic radio frequency, radar, thermal displacement, etc.
  **Proximity and displacement:** Capacitive, LVDT, magnetic, photoelectric, ultrasonic
  **Biosensors:** Electrochemical, resonant mirror, surface plasmon resonance
  **Image:** Charge-coupled devices, CMOS
  **Gas and chemical:** Semiconductor, conductance, infrared, electrochemical
  **Acceleration:** Accelerometers, gyroscopes

## 2.2 Working Principle of Sensors

The working principle of each sensor is different, as it is designed to measure a specific quantity. The principle of few basic sensors is as follows:

- Temperature sensor: The temperature sensor measures the environmental temperature and converts it to an electrical signal. The principle of the thermometer is expansion and contraction of mercury in glass. With an alteration in temperature, mercury expands and contracts proportionally.

- Contact sensor: The sensor that needs physical contact with the object, temperature of which is to sensed.

- Noncontact sensor: The sensor that needs't be in physical contact with the object, temperature of which is to sensed. This type uses sound waves to measure temperature.

- Thermocouple: Thermocouple is made of two wires, each junction formed by joining the ends.

- Resistance temperature detectors (RTDs): An RTD is type of thermal resistor that changes the electrical resistance.

- Thermistors: It is type of thermal resistor that changes its resistance.

- IR sensor: An IR sensor emits and detects infrared rays. It is easily available in the market, but it is sensitive towards environment noise and light.

Internet of Things with Raspberry Pi and Arduino

- 3. UV sensor: A UV sensor measures the intensity or the power of incident radiation. This electromagnetic radiation has longer wavelength than x-rays but smaller than visible radiation. A polycrystalline diamond material is used for ultraviolet sensing. It can transmit different types of energy but can accept only one type of signal. The electrical meter is used to read the output signals and processed to the computer through analog-to-digital converters. The UV sensor is used in UV water treatment, light sensors, UV spectrum detectors, etc.

- 4. Touch sensor: A touch sensor is variable resistor that changes its resistance as per the location where it gets touched. It is made of a conductive and partially conductive substance and insulated in a plastic cover. The flow of current is due to a conductive material that allows current partially. The touch sensor is a cost-effective solution for many applications, such as washing machines, fluid-level sensors, and dishwashers.

- 5. Proximity sensor: A proximity sensor can detect the presence of an object without any contact point. The working principle is electromagnetic waves that are emitted by the sensor and return when the object is in range of the waves. The presence of the object is detected with the change in field radiation. The proximity sensors working of different types, like inductive, capacitive, photoelectric sensor, ultrasonic, and Hall-effect.

  Inductive proximity sensor: This type of sensor has an oscillator as an input, which changes the loss resistance by the proximity of an electrically conductive medium. For metal detection, these types of sensors are used.

  Capacitive proximity sensor: This type of sensor converts capacitance by changing electrode displacement. It can be done by bringing the object within the variable frequencies. The object is detected with the help of the oscillating frequency, which is converted into a DC voltage. This current is compared with a fixed value to detect the object. For plastic targets, these types of sensors are used.

- 6. Ultrasonic sensor: An ultrasonic sensor is used to detect the distance of an object. The working principle is the time duration between the emission and receiving of the waves after reflecting from the object.
