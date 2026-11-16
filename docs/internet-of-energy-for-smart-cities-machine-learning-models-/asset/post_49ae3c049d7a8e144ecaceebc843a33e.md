
important role in PV system operation, availability of environmental data increases the options in combining different data sources in order to build and train better models. In [17] it is proposed a development system that aims at providing the functionality of integrating different information flows in order to be used for monitoring the PV system operation and early detection of changes in system integrity.

In this book chapter a review of the latest research done in the area of applying ML techniques for identification of possible degradation of photovoltaic panel operation will be presented at the beginning of the chapter. The main causes of panel operation degradation will be then presented and the problems that may appear when this situation occurs in a PV park. Next, a monitoring system architecture will be presented based on authors recent research that involve different sources of information. These include sensors which are part of PV panel system, sensors distributed in the PV park, meteorological stations in the proximity of the park, other sources of information available on the internet (weather channels, environment monitoring feeds as well as historical data). The results of applying different ML techniques will be presented and conclusions about the efficiency of applying these techniques in the frame of the future Internet of Energy will be drawn.

## 9.2 SOLAR PANEL MONITORING

Today PV parks are complex systems based on advanced technologies that support not only solar energy conversion, interaction with load, storage systems and network grid but also generation of useful information which is communicated via communication channels to be used for monitoring, sustain of their daily system operation and interaction with the working environment and human personnel.

As shown in Figure 9.1 the PV panel monitoring systems monitor the PV panels in their environment, perform continuous assessment of their physical and functional integrity (remote monitoring) and gather data from different sources in order to analyze system’s behavior and to improve operational performance.

The aim of PV monitoring system is to improve system operational conditions and functionality, as well as to ensure system safe and secure interaction with other systems. Besides, in the case of PV parks it is useful to continuously monitor the large number of PV panels as it constitutes a real support also for maintenance teams.

The devices that are generating data used for processing by the monitoring system can be part of the PV system or can be distributed in the local or enlarged environment (defining thus an intelligence at an environmental level). In this respect, a minimal list of characteristics that the monitoring system must implement includes compatibility with PV control systems, local and wide area connectivity, accuracy of collected data and security, all these in a frame of low power consumption.

The many possibilities of monitoring systems include:

- Normal operation recognition (availability of sun radiation, identifying the good tilting angle, possibility of either consuming or storing the generated energy).

![](img/617e854c2620a5a4bed0116cef33155a_253_0.png)

Figure 9.1 General view of PV panel monitoring

- PV panel localization and identification (this includes physical identification of one or many PV panels and also their identification in databases, all these based on different available information). The accuracy of localization depends on the monitoring system complexity and can include different technologies such as visual identification, video monitoring, signature identification, machine learning techniques.
- Event detection, recognition, classification and localization. Events can be of different nature (electrical, mechanical, and optical) therefore, the monitoring system should include a set of techniques associated to each class of events. This will provide information to build local or general situation awareness;
- Behavior analysis, will include detection and identification of behavioral patterns based on a statistical predictive algorithm using different activity models (sunny-cloudy, day-night, summer-winter, load-no load etc).
- Interaction with user and other systems (frequent use cases implying human-system or system-system interaction). Keeping these interaction at an appropriate level, allows the system to be aware of the local and overall context and have the capacity to make predictions regarding the situation evolution.

Besides their basic goal for increasing and monitoring the quality of system operation, the monitoring system may be useful also:

- to assess the general status of the PV system (long term or continuous status monitoring);
- to detect the emergency situations and subsequently elaborate appropriate suggestions for intervention (detection of damaged parts or entire subsystem, detection of hazards that can put the system or personnel in danger);
- to detect degrading status and/or its progression;
- to evaluate a maintenance intervention (result of repairs, substitutions, upgrades, improvements etc).

In Figure 9.2 is presented a general view of a PV panel monitoring environment identifying different aspects involved in the process, namely users, local and enlarged environments, technologies and devices that constitutes the ground basis for developing applications for implementation of monitoring solutions.

![](img/617e854c2620a5a4bed0116cef33155a_254_0.png)

Figure 9.2 Elements and applications involved in PV panel monitoring

## 9.3 PHOTOVOLTAIC OPERATION DEGRADATION

The ability of PV panels to provide same power levels over their lifetime is important because it directly influence the capacity to supply a certain power needed by the load and to ensure the return of investment. Numerous studies have been carried out identifying the degradation rates both by doing indoor testing labs or in the outdoor field [25].

The reduction in operation or efficiency of the solar panels due to covering the solar cells with different materials is determined by the shadowing effect [37]. Figure 9.3 presents the cases where solar cells of PV panels are covered to a certain degree with sand or mud, resulting in the modification of their generating current and further on of PV panel operation. Figure 9.3 shows that cells can be covered at different degrees thus, some of them can bias the bypass cell, resulting in a reduction in the generated power. Depending on the PV panel internal architecture, bypass diodes can be provided for every cell or for a group of cells. In the second case, the shadowing effect of a single cell has a greater impact on the overall PV panel operation (an entire group of cells are bypassed) than in the first case [38].

![](img/617e854c2620a5a4bed0116cef33155a_255_0.png)

Figure 9.3 PV cells covered at certain degrees level with sand (a) and mud (b)

This deposition can be temporary or can be of long term like the deposition of dust to the surface of PV cells [10, 13]. Several studies show the negative effect of dust deposition and that composition, and therefore color, can impact differently the PV cell degradation [26].

The reduction of PV panels' efficiency can be produced also by the effect of the air, water, salt or other impurities specific to regions located near the sea or oceans [40]. The main effects of this exposure is on the optical characteristics of solar panels because, the shielding glass can change color or even have its structure damaged after a certain period of time.

Some research has led to the development of additional devices that are attached to PV panels to remove impurities that can be deposited on the surface of the panels. These devices are based on various principles, the most common being those in which impurities are removed either with the help of air jets [41] or with the help of water jets. Other solutions consider the use of wiping or brushing systems, while another solution presented in [32] uses an electro dynamic screen. The cleaning systems can be individual, each panel having its own cleaning system or collective, in which case a single system is used, usually mobile, which performs the cleaning of several panels in a cleaning operation.

Another category of phenomena that can have medium to high impact on PV panel operation and also on their integrity are the meteorological phenomena. Among
