
In this example, the DMZ is not positioned between the outer security level of the corporate network and the uncontrolled Internet. Instead, it is placed between the more secure OT network and the less trusted corporate IT network. Another DMZ should be created between the corporate network and the Internet.

### ICS Reference Architecture

After examining all the network models presented in this chapter for both IT and OT networks, you might still be wondering: How would you actually implement these concepts to create a secure IT/OT network environment?

In [Chapter 1](#c01.xhtml), "Industrial Control Systems," you were briefly introduced to the *Purdue ANSI/ISA 95 Reference Model Architecture*. It has become the international standard for interconnecting IT and OT networks.

Recall that this model defines the generic IT/OT network as five layers ranging from the Processes and Sensors/Actuators level up to the Business, Planning, and Logistics network level. In doing so, it also presents the types of equipment, network connectivity, and business operations occurring at each level.

The area of most interest for this security zoning conversation is the zone depicted between Level 4 and Level 3, as depicted in [Figure 3.20](#c03.xhtml#c03-fig-0020). This is where the DMZ is placed to separate the Business Planning and Logistics portion of the network from the Manufacturing Operations and Management portion. The DMZ places a firewall at each end of the zone programmed with different rule sets to provide the desired security functions for each interface.

![FIGURE 3.20 Where OT meets IT](images/c03f020.png)

**[FIGURE 3.20](#c03.xhtml#R_c03-fig-0020) Where OT meets IT**

This configuration also makes it more difficult for intruders to hack their way through both devices to reach the inside of the network. In some organizations, the two firewalls may be managed by two separate administrators: the IT network admin might be responsible for managing the enterprise firewall while the process control admin controls the ICS firewall.

#### Expanded ISA-95 Structures

The basic ISA-95 structure is often expanded to meet security demands presented by a specific organization's needs. For example, if the organization presents a robust Internet presence, such as a corporate website that provides B2C and/or B2B services, the network model should be extended to provide an additional enterprise DMZ to separate the organization's enterprise network from the Internet, as illustrated in [Figure 3.21](#c03.xhtml#c03-fig-0021).

![FIGURE 3.21 Securing the enterprise zone](images/c03f021.png)

**[FIGURE 3.21](#c03.xhtml#R_c03-fig-0021) Securing the enterprise zone**

It has also been expanded with additional zones to provide specific services, as depicted in [Figure 3.22](#c03.xhtml#c03-fig-0022):

*   **Database zones**: As described earlier, the enterprise network should be layered to provide defense-in-depth strategies such as segregating the databases that hold the most sensitive data into the innermost zone of the network.
*   **Monitoring zones**: These zones are created to monitor zones that process and store production information. In this case, a monitoring zone has been added at both level 3 and level 4. Both zones consist of a firewall and an intrusion detection system (IDS).
*   **Security zones**: As described in [Chapter 1](#c01.xhtml), production systems typically include a separate instrumentation and control system (SIS) dedicated specifically to the operational safety of the processes. When included in the ISA-95 architecture model, this system is shown as its own level, located at the bottom of the structure where the processes and OT sensors, actuators, and controllers reside. It is shown at this level because the SIS must be its own redundant system that is disconnected (air gapped) from the OT network.

![FIGURE 3.22 Additional ISA-95 zones](images/c03f022.png)

**[FIGURE 3.22](#c03.xhtml#R_c03-fig-0022) Additional ISA-95 zones**

#### Evolving Architecture Models

An industry movement referred to as *Industry 4.0* has pushed ICS environments to begin integrating newer technologies into their IT/OT network topologies. These technologies include cloud services, edge computing, and advanced 5G wireless networks along with other smart device technologies. This movement has produced many variations of the Standard Security Architecture, including a three-part *Industrial Internet of Things* (*IIoT*) reference architecture, depicted in [Figure 3.23](#c03.xhtml#c03-fig-0023).

![FIGURE 3.23 IIoT Purdue Architecture Model](images/c03f023.png)

**[FIGURE 3.23](#c03.xhtml#R_c03-fig-0023) IIoT Purdue Architecture Model**

This IIoT version of the model regroups the five levels of the hierarchical Purdue model into three distinct horizontal tiers:

*   **An edge tier**: This tier contains the level 0, 1, and 2 functions of the Purdue Model.
*   **A (cloud) platform tier**: This tier is typically a platform-as-a-service (PaaS) cloud that contains data storage, analytic systems, and network communications facilities. This tier replaces level 3.
*   **An enterprise tier**: This tier represents the organization's IT network, including its servers, user devices, and Internet connection(s). This tier corresponds to levels 4 and 5 of the Purdue Model.

In addition to the traditional sensors and actuators located in the edge tier, smart IIoT sensors and actuators can communicate with the platform tier directly or through an IIoT gateway. The enterprise tier, which may also be a cloud environment, communicates directly with the platform tier as well.

An IIoT/Purdue integration version proposed by the European Union Agency for Cybersecurity (ENISA) revises the hierarchical model to accommodate the operation of IIoT devices by combining an IIoT control platform with the traditional ISA-95 Level 3 functions. [Figure 3.24](#c03.xhtml#c03-fig-0024) depicts the ENISA model.

At this point, there is no widely accepted standard for ISA-95/IIoT integration. However, ICS standards organizations around the world are working on both wholesale replacements for the ISA-95 model and hybrid solutions that integrate IIoT technologies into the model and maintain segmentation and traditional IT/OT data movement control.

![FIGURE 3.24 IIoT Purdue Architecture Model](images/c03f024.png)

**[FIGURE 3.24](#c03.xhtml#R_c03-fig-0024) IIoT Purdue Architecture Model**

### The SANS ICS410 Reference Model

The SANS (SysAdmin, Audit, Network and Security) organization has created and released an expanded version of the Purdue model that they have titled the ICS410 Reference Model. This expanded reference architecture, depicted in [Figure 3-25a](#c03.xhtml#c03-fig-0524), makes provisions for the addition of Cloud Technologies and other technical advances to the OT environment, as well as the ever-increasing desire to push OT data up the organizational ladder through the IT networks.

Like the original ISA-95 Purdue model, the ICS410 model divides the IT/OT devices and networks into functional layers with appropriate cybersecurity devices and systems situated at the division points. However, it goes further than the Purdue model by dividing the Level-0 through Level-2 layers into distinct but separate silos (cells/lines/processes). The ICS410 also includes safety systems as part of the local Level 0-2 silos.
