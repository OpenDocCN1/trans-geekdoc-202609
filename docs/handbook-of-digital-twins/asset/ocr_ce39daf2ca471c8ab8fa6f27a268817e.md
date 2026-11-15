# ### 7.3.2.4 Conversion and Connection

At these levels, we will progressively refine the previously defined architecture by specifying the interconnections and communication protocols (software and hardware interfaces) and by favoring standard tools such as OLE for Process Control Unified Architecture(OPC-UA), Machine Tool Connectivity(MTConnect), Message Queuing Telemetry Transport(MQTT). These choices can then condition the selection of sensors and data collection methods according to the application environment. Indeed, many choices can be made according to the context of the application, because the already existing technologies in the company are often favored. The goal of these steps is to produce metrics that will allow the comparison of various technological choices in order to select the architecture that best meets the needs in terms of cost, performance, agility, security, etc.

# ## 7.4 Typology

In the sequel, we outline the 13 characteristics that make up our typology for the DT. These criteria aim at establishing a general architecture of the DT by defining the basic and fundamental requirements (user’s needs) to which the DT will have to provide an efficient DT response (and this still without making any technological choices on the DT components).

# ### 7.4.1 DT Entity

The ISO/DIS 23247 standard defines the entity as “thing (physical or non-physical) having a distinct existence” together with the OME as an item that as an observable physical presence or operation in manufacturing. OMEs include equipment, material, personnel, process, facility, environment, product, and supporting document. However, as our typology is not restricted to manufacturing applications, we choose to qualify this object as DT entity.

# ### 7.4.2 Type

According to Grieves’ classification of DT in Grieves and Vickers (2017), there are three distinct types: DT aggregate, DT prototype, and DT instance. The prototype is an item that is utilized mostly during the design process. The instance describes the specific piece of production-related equipment. The aggregate consists of all DT instances deployed in the exploitation or maintenance phases for the same entity.