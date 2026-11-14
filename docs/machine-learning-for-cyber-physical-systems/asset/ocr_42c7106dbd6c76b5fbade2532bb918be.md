# # Web-based Machine Learning Platform for Condition-Monitoring

Thomas Bernard¹, Christian Kühnert¹, Enrique Campbell²

¹ Fraunhofer Institute for Optronics, System Technologies and Image Exploitation IOSB
Karlsruhe, Germany

² Berliner Wasserbetriebe, Neue Jüdenstraße 1, Berlin

* Corresponding author. Tel.: +49-721-6091-360
E-mail address: thomas.bernard@iosb.fraunhofer.de

**Abstract.** Modern water system infrastructures are equipped with a large amount
of sensors. In recent years machine-learning (ML) algorithms became a promising
option for data analysis. However, currently ML algorithms are not frequently
used in real-world applications. One reason is the costly and time-consuming in-
tegration and maintenance of ML algorithms by data scientists. To overcome this
challenge, this paper proposes a generic, adaptable platform for real-time data
analysis in water distribution networks. The architecture of the platform allows
to connect to different types of data sources, to process its measurements in real-
time with and without ML algorithms and finally pushing the results to different
sinks, like a database or a web-interface. This is achieved by a modular, plugin
based software architecture of the platform. As a use-case, a data-driven anomaly
detection algorithm is used to monitor the water quality of several water treat-
ment plants of the city of Berlin.

**Keywords:**, Machine-learning; water quality monitoring; anomaly detection;
plugin architecture; data fusion.

# ## 1 Introduction

In recent years, a large number of new water quality and hydraulic sensors in water
distribution networks and water treatment plants have been installed. Reasons for this
trend are (1) a lot of new sensor companies and corresponding new sensors appeared
on the market which means decreasing costs and increasing performance of the sensor
units; (2) due to wireless communication technologies (e.g. GSM) the installation costs
are drastically decreasing. Hence, there is a need for the development of integrated
platforms for the storage, visualisation and enhanced data analysis of these data. The
benefit of advanced data analysis in water infrastructures has been already investigated
for different scenarios, e.g. monitoring of drinking water quality 4, forecasting of the
water consumption 6 or the modelling of sediment transport 1. However, different data
suppliers and old plants containing an outdated IT-infrastructure still complicate the
integration of state-of-the-art data analysis algorithms. In spite of the fact that many