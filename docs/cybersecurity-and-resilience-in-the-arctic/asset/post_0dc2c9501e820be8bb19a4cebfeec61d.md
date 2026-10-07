
# I. Skarga-Bandurova and I. Kotsiuba / Cyber Security and Resilience of Smart Grid Infrastructure 259

Wide area measurement and control

- Data processing and storage;
- Secure data collection and storage;
- GPS spoofing attacks.

Disaster forensics

- Data collection during severe disasters
- Smart grid control under communication system failure or damage
- Event logging hardware for highly critical assets (similar to flight recorders)
- Audio/video authentication by ENF (Electrical Network Frequency)
- Obtaining pattern database for old recordings

## 6. Perspectives of leveraging Decentralized Smart Energy Transaction Platform

## 6.1. Basic components

The proposed solution (see Fig. 2) is a decentralized transaction platform containing all the latest technology as advanced metering infrastructure, distributed generation, demand-side management, etc. Besides financial transactions in the energy market, it covers other uses beyond just crypto-payments and can be extended to perform any number of smart grid forensic tasks mentioned in Table 3.

The operation of the platform is governed by computational nodes. Practically, each node is a computer server running under Windows Server 2016 OS or Red Hat Linux OS where "Energy Core" is deployed. The network is divided into subnets or networks.

The system consists of several types of nodes:

- Full nodes
Full nodes (ECore) are deployed on the core objects of energy infrastructure, such as power plants; it is worth pointing out that we need a big data warehouses to store all energy data. Remaining facilities are placed on the light nodes.

- Energy Core
Energy core is a set of software for controlling transactions and storing information. It performs the functions of receiving and validating transactions and then forms an encrypted block by a private key, which is sent to all the nodes for confirmation and storage in their data warehouse. It also detects and connects to similar network nodes, forming a decentralized information energy platform, which is a decentralized virtual machine, which allows for the management of network nodes based on smart contracts, and in turn, creates an environment for distributed hardware and applications. At the moment, there is a big challenge for cyber forensics in cases when it is necessary to obtain data from the operating equipment, as the equipment's disconnection from the network affects power and safety, rendering further investigation impossible. The blockchain provides real-time management and resilience capabilities that will up the speed of investigating cyber crimes and failures during natural disasters, acts of cyber-terrorism, and computer fraud.

![](img/fe2b494937620764cde04f8bcd27e5e0_271_0.png)

Figure 2. A Decentralized Energy Transaction Platform on Blockchain (Kotsuba et al., 2018)

Each element of this infrastructure, from blockchain nodes to Smart Grid components, is a potential source of information. Below are some examples of items mentioned in the general scheme (see Figure 1) and their possible use for cyber- or disaster forecasts.

- Intelligent Electronic Devices (IED)
IEDs are microprocessor-based tools used for protection, automation, control, and monitoring of power system hardware. They sense voltage, current, or frequency anomalies, and raise or lower voltage levels in order to maintain the desired level.

- Charging stations
Information from charging stations provides the duration of the charge (the time stays at a point), the connected car, and payment. It also keeps logging, possibly including notifications about hazard, abnormal activity of the charging station, etc.

- Smart counters
Smart meters and IEDs provide granular energy/demand data. This information allows utilities to interpret behaviors, work schedules, occupancy rate (how many people live in a home), types of equipment in a home, heating/cooling systems. Investigation of incidents with theft of electricity, as mentioned in El-Rokantanci, and Mouftah (2013), may indicate the cultivation of marijuana.

- Phasor Measurement Unit (PMU)
A PMU is able to measure the phase, amplitude, frequency, and Rate of Change of voltage and current waveforms. Beside utilization of PMUs in power systems for protection purposes, they are also used for several tasks related to the investigation of photovoltaic power in the grid (Vergara and Carpentieri, 2018)

- Phasor Data Concentrator (PDC)
PDCs receive and synchronize phase data from multiple PMUs to produce real-time data streams. A PDC can exchange phasor data with PDCs at all locations. Both PDC and PMU data be used by forensic specialists for Electric Network Frequency analysis. They compare frequency changes in background mains when using long-term high-precision historical data. PDCs can identify when the record was created, and help detect any edits in the recording.

## 6.2. System deployment

In parallel with the SCADA system, the light node (network node) is installed at the object, and the local data store is deployed. Physically, the light node is a separate computing device.

Devices on a network site transmit information (a transaction) to the SCADA system; in turn, SCADA stores the data in its local store. The node, working in parallel with the SCADA system, is already working directly with the warehouse to ensure the security of the system. To ensure authenticity (the device is valid / data is not substituted) of transactions, they are produced according to the ZKP (zero-knowledge protocol). Transactions are recorded in a block and sent to the General Blockchain.

To register new devices on the network, one shared Sidechain is required (if it is a)

## 2.1. I. Skarga-Bandurova and I. Kotsuba / Cyber Security and Resilience of Smart Grid Infrastructure

Authentication of new devices on the network can occur using a Bloom filter (probabilistic data structure that provides time and space efficient) (Guan et al., 2018).

Registration of operator also has. The blocks are included in the General Blockchain. The more nodes, the higher decentralization, the greater reliability. The blocks can be created not only by network but also by operators. The blocks can also store, for example, information from smart meters, charging stations of electric cars, and weather information from the regions. Requests for information may carry in the investigation of cyber incidents, the trace of criminals, or investigation of system failures during disasters. To perform a more forensic investigation, more decentralized and possibly fully distributed Smart grids are required. In this case, the blockchain ensures the security and validity of the data (Trump et al., 2018).

## 7. Summary

This chapter has presented an overview of electricity production and implementation of Smart Grids in the Arctic region, performed analysis of Smart grid security requirements and perspectives on integrating forensic techniques with the blockchain to ensure the cybersecurity and resilience. The use of the blockchain enables to create a single information space for investigating incidents in the Smart Grid. Necessary conditions for this are: all device must be authenticated (this device will generate this data); all attacks must be very expensive for an attacker; the information environment should be transparent as possible.

This technology is still in its early stages and faces immaturity, with problems of scalability, and transaction processing delays, as trust issues. However, because blockchain has some proven applications in the financial industry, there are some grounds to believe that it has a high potential to be widely adopted in Smart Grids.

## 8. Acknowledgments

The authors are grateful to colleagues and colleagues who participated in the NATO ARW on Governance for Security and Resilience in the Arctic, held in Rovaniemi, Finland on 27-30 January, 2019. The views expressed in this document are solely those of authors, and do not represent the views of their affiliated organizations.

# References

Aitzhan N. J. and Zvetovic D., 2016, "Security and Privacy in Decentralized Exchange Trading through Multisig,Blockchain and Anonymous Messaging, IEEE Transactions on Database and Secure Computing, 2016, vol. 29, pp. 1–11."

Beres A., Benge B., Lisa K., 2015, "A survey on smart grid data analysis in the cloud," Proceedings IEEE, 2015, vol. 4, pp. 56-59.

Berggreen, Jesper, 2018, "44% Wind Denmark – Set New Wind Energy Record In 2017," Clean Teica. January 6, 2018. https://cleantechmedia.com/2018/01/06/44-wind-denmark-smashed-huge-wind-energy-report/
