# The Cognitive Engine: Artificial Intelligence for Wireless Communications

help the radio adjust its behavior, including radio propagation, interference models (temperature), position and location, time, and possible cues. The sensors collect the information by any means available or necessary: developed by a third party, prebuilt libraries, or specifically developed for use with the cognitive engine. whatever manner the data is collected, the important aspect of a sensor is having a standard approach to how data is transferred to the cognitive controller. The application programming interface (API) is described as a simple state machine with a few important states:

+   - Initialization;
- Waiting for data request from cognitive controller;
- Collecting data and building model;
- Transferring model to cognitive controller.

Initialization builds the proper interfacing to the cognitive controller. The sensor then enters a wait state to listen to its interface for a request for data from the cognitive controller. When the sensor receives a request, it performs its data collection process, by calling external libraries or applications, and packages the data into an XML format to describe the sensor data. The XML data is transmitted to the cognitive controller, and the state machine returns to its wait.

Another look at the structure of a sensor is seen in Figure 2.4. This figure shows that the cognitive engine sends information to the sensor through some generic interface. Sockets and Object Access Protocol (SOAP) are two simple ways to communicate information between software programs either colocated on the same hardware or distributed and connected through a network layer. These are only two possible methods for providing the communications between the sensor and the engine. Functions and processing algorithms are retrieved through an external application or library. The use of an external interface here also allows the sensor to access or differ functionality through simple and independent updates to a library or API.

Figure 2.5 lists the XML format for conveying information to the cognitive controller.

The first line defines this as an XML v1.0 file. The next line says that this is a model from a sensor. The particular model name is then the character data of the “model-name” tag. The remaining remains contain the model data. The important practice for proper representation of model data is shown in the fourth line where the data type, size, and unit are defined. The specification of the data type can be any used by a particular database or language specific to the processing of the data. For instance, data used with a MySQL database can have the type “int,”float,” or “char.” The size information indicates the number of items included in this data tag; basically,