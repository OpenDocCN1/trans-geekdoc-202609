
![](img/617e854c2620a5a4bed0116cef33155a_106_0.png)

Figure 3.11 The AMI scheme

smart meters [34]. The IEDs are used to detect faults, protection relaying, event recording, measurement, control, and automation aims in power network [39, 40]. PMUs play an important role on Wide Area applications and can be a key technology to increase accuracy and obtain better response times in energy management systems (EMS). This technology has a data entry and acquisition interface and a microcontroller, and the global positioning system (GPS) receiver and internal phase-locked loop (PLL) ensure synchronization of the entire system with universal time-coordinated (UTC) timestamp [34].

The EMS are automation systems that collect energy measurement data from the field and making it available to users through graphics, online monitoring tools, and energy quality analyzers, thus enabling the management of energy resources [41]. This system uses SCADA application to perform data analysis and monitoring. Among the functions are topological analysis, load forecasting, power flow analysis, and state estimation. With the evolution and consolidation of SGs, SCADA will need to incorporate new smart metering elements, such as phasor measurement units (PMUs) and intelligent relays, and consider new renewable sources of power generation and energy storage in electric vehicles (EV) [42]. Figure 3.12 shows a typical SCADA architecture.

A wide area monitoring system (WAMS) represents an important and promising technological advance in monitoring and control of actual and future power transmission systems [40]. This system aims to complement the SCADA application in transmission networks. This system is based on PMUs, and is then also made up of phasor data concentrators (PDCs), a communication network, and a power system communication center. WAMS allows monitoring, state estimation, and analysis of power system events. Figure 3.13 shows the architecture of WAMS.

![](img/617e854c2620a5a4bed0116cef33155a_107_0.png)

Figure 3.12 Typical SCADA architecture based on [40]

## 3.3.3 MICROGRIDS AND KEY TECHNOLOGIES

The microgrids can be characterized as active local distribution systems, with elements of distributed generation such as solar, wind, microturbines, diesel generator, fuel cell, among other forms of generation and energy storage technologies. Those systems can operate connected to the main power grid or in island mode, disconnected from the utility grid. In the connected mode, microgrids provide better integration of renewable sources, in addition to promoting control and management strategies that improve energy quality and consumer spending. In times of interruption of supply by the concessionaire, for example, the micro-network can start the operation in island mode and isolate itself from the main network, becoming a network with reliability and resiliency. The isolated operation of the microgrid also seeks to serve remote locations, those that are unable to connect to a bulk electrical network. In the latter case, they require specific approaches to guarantee safe and quality operation, in addition to these networks being extremely important for remote communities.

Associated with renewable sources and smart microgrid technologies are the network’s electronic components, as power electronic converters that play a fundamental role in this context of distributed generation and for improvement of the power systems. Voltage Source Converters (VSC) and

![](img/617e854c2620a5a4bed0116cef33155a_108_0.png)

**Figure 3.13** WAMS architecture

Current Source Converters (CSC) are the main electronic interfaces for a renewable energy source, especially when we are talking about PV energy, it is also associated with the use of energy storage systems. Other components that play important roles are the Flexible AC Transmission Systems (FACTS), these are used to increase the power transfer capability of existing AC lines, to control steady-state and dynamic power flow through an AC circuit, to control reactive power and voltage and to enhance voltage and angle stability [43].

Microgrid architectures can be classified into three groups: AC microgrid, DC microgrid, hybrid AC/DC microgrid. The AC microgrid has a common AC bus which is generally connected to mixed loads (DC and AC loads), distributed generations, energy storage devices [44]. This has great compatibility with traditional AC networks, in addition to having greater reliability and capacity. On the other hand, when it comes to DC loads and sources, the integration is done by DC/AC inverters, which reduces efficiency [45, 46]. Figure 3.14 shows an example of AC architecture scheme.

In DC microgrid, common DC bus is used to connect to the grid through an AC/DC converter [44]. The DC microgrid has some advantages, one of which is to avoid losses due to energy conversion, it also has better integration with renewable energy sources. These also have greater stability. Finally, we have the hybrid AC/DC microgrid, which is the combination of the two architectures, presenting a sum of benefits and advantages in use. Figure 3.15 shows an example of DC architecture scheme.

Energy storage plays a key role in microgrids. This technology can be used in different ways, one of which is to use a large capacity to support the microgrid in reducing fluctuations and improve stability. Energy Storage also performs some energy management functions, such as load leveling, peak shaving, and RES energy shifting.

![](img/617e854c2620a5a4bed0116cef33155a_109_0.png)

Figure 3.14 Example of AC architecture scheme

It is possible to use energy storage also with the load or with the generation. Along with the load, it provides support when variations are obtained that require a quick response in which the generation follows the change in the load, thus avoiding sudden operations. Another way is to use storage with renewable generation to smooth the output of these intermittent sources. Below is a list of the main technologies in the sector. Figure 3.16 shows the applications and used technologies. The list below includes some of the most used technologies.

- 1. **Battery:** Battery is an electrochemical storage solution and the most applied in the market. Examples of types are the lithium-ion (Li-ion), lead-acid, nickel-cadmium (NiCad), sodium/sulfur (Na/S), vanadium-redox;
- 2. **Flywheels:** Mechanical devices that take advantage of rotational energy to provide instant electricity;
- 3. **Compressed air energy storage:** Using compressed air to create a reserve of potential energy;
- 4. **Thermal storage:** Capturing heat and cold to create energy on demand;
- 5. **Pumped hydro storage:** Big reservoirs of water to store energy;
- 6. **Superconducting magnetic energy storage (SMES):** In SMES, the energy is stored in the magnetic field of a superconducting coil formed by direct current flowing through the coil.

![](img/617e854c2620a5a4bed0116cef33155a_110_0.png)

Figure 3.15 Example of DC architecture scheme

## 3.4 INTEROPERABILITY AND SCALABILITY

### 3.4.1 MOVING FOR INTEROPERABILITY IN SMART GRIDS

The evolution of the energy sector has the main characteristic of being digital. Changes in the way of generating, distributing, and consuming energy go through a modernization process that is made possible by the wide use of ICTs, applications are no longer limited to electrical networks, they are now connected to the consumer and to new models of the grid.

A crucial point to make it increasingly possible to search for a digital electric sector is to move toward interoperability. It is the characteristic that allows two types of equipment or systems to operate together without any conflict of communication or compatibility. This is a very big challenge for power systems because each part of the energy supply chain has its standards, protocols, and culture to deal with its equipment operations. For this to occur, there must be a policy effort and convergence between institutional standards for the electricity sector.

The benefits related to interoperability vary among stakeholders of SG design, but everyone benefits from better clarity between operations, greater affordability, among other advantages. In this process, there are some difficulties to be overcome, following a list of key issues for this process [47].

- 1. The large number of stakeholders, different considerations, number and complexity of standards available (and missing) requires a more formal nationally driven governance structure;
- 2. Since SG efforts are underway, and in some cases complete, standards adoption must consider work already completed and underway;
- 3. Interoperability discussions and definitions should be expanded to focus on standards across systems (inter-system) rather than just within systems (intra-system);
