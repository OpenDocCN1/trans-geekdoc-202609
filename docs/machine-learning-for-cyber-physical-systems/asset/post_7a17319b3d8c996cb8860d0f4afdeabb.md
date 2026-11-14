
**Open Access** This chapter is licensed under the terms of the Creative Commons Attribution 4.0 International License (http://creativecommons.org/licenses/by/4.0/), which permits use, sharing, adaptation, distribution and reproduction in any medium or format, as long as you give appropriate credit to the original author(s) and the source, provide a link to the Creative Commons licence and indicate if changes were made

The images or other third party material in this chapter are included in the chapter’s Creative Commons licence, unless indicated otherwise in a credit line to the material. If material is not included in the chapter’s Creative Commons licence and your intended use is not permitted by statutory regulation or exceeds the permitted use, you will need to obtain permission directly from the copyright holder.

![](img/a2f5eed6507498d886a06be86239344b_42_0.png)

## Web-based Machine Learning Platform for Condition-Monitoring

Thomas Bernard¹, Christian Kühnert¹, Enrique Campbell²

¹ Fraunhofer Institute for Optronics, System Technologies and Image Exploitation IOSB
Karlsruhe, Germany

² Berliner Wasserbetriebe, Neue Jüdenstraße 1, Berlin

* Corresponding author. Tel.: +49-721-6091-360
E-mail address: thomas.bernard@iosb.fraunhofer.de

**Abstract.** Modern water system infrastructures are equipped with a large amount of sensors. In recent years machine-learning (ML) algorithms became a promising option for data analysis. However, currently ML algorithms are not frequently used in real-world applications. One reason is the costly and time-consuming integration and maintenance of ML algorithms by data scientists. To overcome this challenge, this paper proposes a generic, adaptable platform for real-time data analysis in water distribution networks. The architecture of the platform allows to connect to different types of data sources, to process its measurements in real-time with and without ML algorithms and finally pushing the results to different sinks, like a database or a web-interface. This is achieved by a modular, plugin based software architecture of the platform. As a use-case, a data-driven anomaly detection algorithm is used to monitor the water quality of several water treatment plants of the city of Berlin.

**Keywords:** Machine-learning; water quality monitoring; anomaly detection; plugin architecture; data fusion.

### 1 Introduction

In recent years, a large number of new water quality and hydraulic sensors in water distribution networks and water treatment plants have been installed. Reasons for this trend are (1) a lot of new sensor companies and corresponding new sensors appeared on the market which means decreasing costs and increasing performance of the sensor units; (2) due to wireless communication technologies (e.g. GSM) the installation costs are drastically decreasing. Hence, there is a need for the development of integrated platforms for the storage, visualisation and enhanced data analysis of these data. The benefit of advanced data analysis in water infrastructures has been already investigated for different scenarios, e.g. monitoring of drinking water quality 4, forecasting of the water consumption 6 or the modelling of sediment transport 1. However, different data suppliers and old plants containing an outdated IT-infrastructure still complicate the integration of state-of-the-art data analysis algorithms. In spite of the fact that many IoT and data analysis platforms are available nowadays the effort for the integration of these platforms in the IT infrastructure of water utilities and the implementation of ML algorithms is still very high. To overcome some of these challenges, this paper presents a generic data fusion and analysis platform with the focus on condition monitoring of the WDN with machine learning algorithms. The platform follows a plug-in based architecture, which means that depending on the specific needs of the current use case (e.g. saving data in a database, performing anomaly detection) different software components can be installed. As a use case, the platform is used to perform the condition-monitoring of nine water quality measuring stations in parallel with a combination of Principal Component Analysis (PCA) 2 and Gaussian Mixture Models (GMMs) 9. The results of the machine learning algorithms, comprising the learned process map, the state trajectory and the anomaly index, are visualized for all stations in a web-interface.

### 2 Platform Architecture

The architecture of the proposed platform consists in three main parts shown in figure 1: (1) the platform core, (2) a plugin structure and (3) a web-interface. The platform core is responsible for the management of the different software modules and data handling and described in section 2.1; the plugins provide the required use case specific application functionality (e.g. analysis algorithms; connection to data source) and are described in section 2.2. Finally, the web-interface, used to give a feed-back to the user, is explained in section 2.3.

![](img/a2f5eed6507498d886a06be86239344b_44_0.png)

**Fig 1:** Plug-in architecture of the platform for real-time data analysis applications

### 2.1 Platform Core

The platform core’s purpose is to provide the stability to allow communication between all components - no matter their purpose, data rate or lifetime. Its main purpose is to act as information hub providing a standard interface for all plugins. Therefore, the platform core utilizes the mediator design pattern 3 to decouple all plugins from each other. The resulting communication topology of plugins and core is a star network with the core as central component, thus preventing any plugin to plugin communication. The core itself uses the Model-View-Controller (MVC) pattern 3.

The core manager is the controller of the platform. It is the owner of all plugins as well as the core cache and responsible for their creation and destruction. Since it is also the facade for the whole core, it is known by reference by all plugins, which need to request access for each core cache entry they want to access.

The core cache acts as model to separate the core’s data from its logic. In order to establish either a read only or read/write connection to the core cache, a plugin has to be granted permission by the core logic. Once a connection is established, the plugin receives a local copy of the requested core cache data which stays in sync with the cache via the observer pattern 3.

### 2.2 Plugins

To maintain the maximum amount of flexibility, the platform follows a plugin based architecture. This means that depending on the specific needs of the current use case different software components can be integrated into the platform. Basically, a plugin represents a software module fulfilling a specific task. Examples are the connection to the SCADA system of the water utility; the implementation of an event detection algorithm or the automated generation of a daily, weekly or monthly report. Plugins employ the factory pattern 3 to allow creating several instances which can be configured started and stopped individually.

### 2.3 Web interface

A web interface is provided to offer a cross device interface for different operating systems to access and interpret the data. Therefore, the main aim of the interface is to provide the users a quick overview of the results of the data analysis algorithms. Since it is implemented as a homepage, it can be accessed with any device with an internet connection from anywhere from multiple concurrent clients. Data is transferred to the web-client by using web sockets.

### 3 Data-driven Condition-Monitoring

In literature numerous approaches for data-driven condition-monitoring have been proposed. Among them, 10 or 11 provide good overviews of this topic. The method used in this paper for data-driven condition-monitoring of the measuring stations covers several steps and is sketched in Fig 2. Initially, a z-score normalization 2 of the measurements is performed. Next, the initial data is reduced down to two dimensions using principal component analysis (PCA) 8. Finally, using the first two principal components, a Gaussian Mixture model 9 is used for the detection of anomalies. All steps are described in the following sections
