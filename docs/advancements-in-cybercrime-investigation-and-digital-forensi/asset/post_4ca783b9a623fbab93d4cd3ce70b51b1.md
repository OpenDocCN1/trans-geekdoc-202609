
smartwatch to provide a user interface. The watch is essentially a wireless Bluetooth adaptor that allows the smartphone’s capabilities to be transferred to the smartwatch (Rowland, Goodman, Charlier, Light, & Lui, 2015). It facilitates the user in performing various daily tasks with ease and comfort such as managing calls, check, and dictate e-mail and text messages, get real-time weather and sports reports, listen to a song or speak to a digital assistant (Hayes, 2020; Tech Target Contributor, 2015) (Figure 4.1).

![](img/46a7ed74d391bf69db3c36e9484e1be4_98_0.png)

FIGURE 4.1 Some examples of wearable devices.

## 4.1.2 DESIGN PRINCIPLE OF WEARABLE DEVICES

The design of wearable devices is a complicated task. It is because of the various types of sensors working within an essentially interconnected system. Adebayo (2020) classified the sensors into three categories:

- 1. **Biosensors:** These comprise glucose, blood pressure, ECG, EMG, temperature, and brain wave sensors.
- 2. **Motion Sensors:** Examples include acceleration, gyroscope, geomagnetic, and atmospheric pressure sensors.
- 3. **Environmental Sensors:** For example, temperature and humidity, gas, pH, ultraviolet, ambient light, dust particles, and pressure sensors, as well as microphones (Adebayo, 2020).

The data to the CPU or display processor is sent by sensors. These sensors are coupled with a microcontroller, which is the most important component that facilitates the operation of the wearable technology. Microcontroller is a common component in small computers that enables the integration of the internet of things (IoT) with desired devices and applications. Most importantly, they help in performing different functions on a single component. Due to the ease in programming, low cost, small size, great connectivity with other sensors and the competency to handle complex functions, including graphic displays, microcontrollers are almost a must-use in wearable technology. A typical architecture of a device includes hardware to hold all the components, allied applications running in the users’ phone and a cloud server, apart from the wearable device itself (Aroganam, Manivannan, & Harrison, 2019).

Figure 4.2 depicts how fitness wearable technology could be used to track various lifestyle activities such as weight, calories burned, heart rate, GPS location, and so on (Chan et al., 2012). Sensors monitor the lifestyle activities of the users. The users input some of the data themselves, such as their food intake. These datasets are then conveyed to a smart phone and the cloud service. The data is then processed, making it suitable so that the user can understand it. Depending on the type of display, this processed data is then sent back to the paired smart mobile device or the wearable itself (Aroganam, Manivannan, & Harrison, 2019). Apart from the architectural design, the other design challenges that are important in the context of a wearable device are:

- 1. **Network Connectivity:** The architectural design of systems described above clearly shows that connectivity is the dominant feature in terms of connection of system elements with each other via different networks (Ngu et al., 2008; Stelvaga & Fortin, 2017).
- 2. **Limited Resources:** To make the device compact and to be carried it comfortably, several restrictions are obligatory such as, and a wearable device is created lightweight so as the user can easily use it. Secondly, the overall size is relatively small. The functions including computing capability, powering sensors and network connectivity suffer from the lack of energy resources and the design is highly constrained by this requirement (Nirjon, Gummeson, Gelb, & Kyu-Han, 2015; Stelvaga & Fortin, 2017).
- 3. **Asynchrony:** As stated by Rowland, for smartphones and desktops, it is attainable to handle network outages gracefully and assume that the flow of interactions will be moderately smooth. However, with wearables, the entire system becomes primarily asynchronous. A wearable device cannot maintain continuous connectivity due to the limited amount of power available. It can, however, only be used for intermittent connectivity. For example, the wearable device can be linked to a phone using a low-power protocol, such as Bluetooth low energy (Rowland, Goodman, Charlier, Light, & Lui, 2015; Stelvaga & Fortin, 2017).
- 4. **Sustainability:** According to Lee et al., the conception of wearable device is that an individual ought to carry it for extended periods of time. The device should even be resistant to the jolting, possible physical damage, and environmental changes. These factors, for example, have a significant impact on sensor readings, as do factors such as humidity, which can result in an increased skin conductivity signal on the output of a galvanic skin response sensor (Lee, Kim, Ryoo, & Shin, 2016; Stelvaga & Fortin, 2017).
- 5. **Convenience and Ergonomics:** As the wearable devices are worn directly onto the body of the user, it should be comfortable to the wearer. This requirement limits the types of materials, size, etc., that can be used in the product design (Ferraro, 2011).
- 6. **Service Focus:** According to Chan et al., users frequently tend to discern the wearable as a distinct object. However, the device behavior is often influenced by a software algorithm that is deployed somewhere elsewhere on the network. This implies that the service designed around the wearable is simply often more critical than the device itself in delivering the proper user experience (Chan et al., 2012; Stelvaga & Fortin, 2017).

![](img/46a7ed74d391bf69db3c36e9484e1be4_100_0.png)

FIGURE 4.2 Image depicts the utility and usability of wearable devices in day-to-day life.

## 4.1.3 WEARABLE DEVICES FORENSICS

Wearable device forensics focuses on the data recovery and its analysis from various types of wearable devices. The goal of the investigation process is to extract and analyze the data that is stored on a wearable device without altering/ modifying the data present on the device in a manner that is acceptable by the law (Loomis, 2019). Although the concept of wearable device forensics has been around for a while, but it is still in its infancy. Due to the wide variety of devices and their varying characteristics, forensic investigations are still challenging.

Potential information of evidentiary value that can be recovered from wearable devices include:

- Global positioning system (GPS);
- Heart rate;
- Biological data;
- Near field communication (NFC) devices;
- Bluetooth information;
- e-mail;
- CDR (call detail records);
- Messages;
- Application data, etc.

## 4.2 BACKGROUND AND RELATED WORK

Digital forensics is a branch of forensic science that deals with the type of investigation that is conducted when evidence of an event must be found. It can be performed in various ways, such as by analyzing a particular time of day or determining if a particular individual has committed a crime. Because of the importance of the investigation, digital forensics has grown into a thriving academic field. It entails gathering and analyzing digital evidence in order to answer questions about a case. In conventional digital forensics, data is acquired in the order of volatility, i.e., from the most volatile to the least volatile. Whereas data stored on the secondary storage devices have less possibilities to be corrupted or lost and may be acquired and recovered later. Digital forensics tools such as write blockers are used to prevent any alterations or modifications being made to the original evidence connected to the forensic workstation (Yoon & Karabiyik, 2020).

Digital forensics research also scrutinizes the development of new models and procedures for investigation, which raises new challenges and gaps in existing ones. Various studies in digital forensics have attempted to refine the way that forensic evidence is stored. Currently, most software platforms such as EnCase, Cellebrite UFED or AccessData’s FTK are able to store digital copies of devices in various formats. The way these formats are structured can affect the speed at which they are processed and the information they
