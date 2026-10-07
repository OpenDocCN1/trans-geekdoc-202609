# What Every Engineer Should Know About IoT

number of dependencies on the part of the system responsible for integrating new hardware devices. There are three design concerns related to modifiability:

+   - Localize Changes: This relates to adding a new sensor/actuator device
- Prevention of Ripple Effects: This relates to minimizing the number of modules affected as a result of adding a new sensor/actuator device
- Defer Binding Time: This relates to the time when a new sensor/actuator device is deployed and the ability of nonprogrammers to manage such deployment

We address these concerns by creating IoT adaptors for sensor/actuator devices, “an anticipation of expected changes” tactic. We use two additional architectural tactics to minimize the propagation of change. First, we specify a standard interface to be exposed by all IoT adaptors to “maintain existing interfaces”. Second, we use the IoT adaptor as an “intermediary” responsible for the semantic translation into a standard format, of all the data received from sensor/actuator devices. As a side effect, this also addresses architectural driver #3.
The adaptors are assigned the following responsibilities:

+   - Send commands to sensor/actuator device
- Receive events from sensor/actuator device
- Perform semantic translation for sensor/actuator device

Instantiating and allocating responsibilities to the adaptors leads to a realization that the building automation server is sensitive to a change in the number of sensor/actuator devices it is connected to and must include logic to route commands and data, and from the correct adaptor. To address this concern, we use the “hiding information” tactic introducing an IoT adaptor manager to hide information about the number and type of sensor/actuator devices connected. The IoT adaptor manager together with the adaptors creates a virtual device, i.e., for all other components of the building automation system, there is one sensor/actuator device to interact with at all times.
Additionally, the IoT adaptor manager uses the following two architectural tactics to address the deferring binding time design concern:

-
- “Runtime registration”: This will support plug-and-play operation allowing nonprogrammers to deploy new sensor/actuator systems
- “Configuration files”: This tactic enables the setting of configuration parameters (such as initial property values) for the sensor/actuator systems at startup

The IoT adaptor manager is assigned the following responsibilities:

+   - Configure a sensor/actuator device
- Route data to a sensor/actuator device