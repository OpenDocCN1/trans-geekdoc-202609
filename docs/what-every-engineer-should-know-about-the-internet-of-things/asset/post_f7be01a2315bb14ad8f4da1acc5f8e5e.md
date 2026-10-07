
# Networks of ‘Things'

Li, Q., Rus, D., “Global clock synchronization in sensor networks,” Twenty-Third Annual Conference of the IEEE Computer and Communications Societies (INFOCOM 2004), Hong Kong, March 7–11, 2004, pp. 564–574. doi:10.1109/INFCOM.2004.1354528.
NIST, Cyber-Physical Systems Public Working Group Workshop, [Web page], National Institute of Standards and Technology, August 11–12, 2014a. Accessed 13 July 2016. http://www.nist.gov/cps/cps-pwg-workshop.cfm.
NIST, The Smart Grid Interoperability Panel–Smart Grid Cybersecurity Committee, NIST Interagency Report (NISTIR) 7628 Revision 1. National Institute of Standards and Technology, Gaithersburg, MD, September 2014b, 668 pp. doi:10.6018/NIST.IR.7628r.
Voas, J. M., “Networks of ‘Things,’ NIST Special Publication 800–183, 2016. https://csrc.nist.gov/publications/detail/sp800-183/final.
Voas, J. M., Miller, K. W., “Semantic metrics for software testability,” Journal of Systems and Software, vol. 20, no. 3, March 1993, pp. 207–216. doi:10.1016/0164-1212(93)90064-5.
Voas, J. M., Miller, K. W., “Software testability: the new verification,” IEEE Software, vol. 12, no. 3, May 1995, doi:10.1109/52.382180.

![](img/41fdf2aa71adfa568d36836737f447e6_48_0.png)

# 3 Smart Cities¹

### 3.1 INTRODUCTION

The United Nations estimates that almost 70% of the world population will live in urban areas by 2050 (United Nations, 2018). Consequently, the urban environments, which are already crowded and chaotic, should be further improved and prepared to accommodate higher number of citizens sustainably and feasibly.

Cities will then be required to be smarter, i.e., to be transformed and connected via their physical, social, and business infrastructures using Information and Communication Technology (ICT) to leverage the collective services to the society (Harrison et al., 2010; Mohanty, Choppali & Kouianos, 2016). Smarter means that the services should ideally rely on technology infrastructure, particularly software. That infrastructure is composed of a diversity of individual systems and physical objects (e.g., sensors, actuators, and tags). For instance, in a smart traffic system, sensors can detect the presence of a person in a crossing. The traffic lights turn to red and the autonomous cars stop movement through brake systems (actuators). People cross the street interacting with tags to notify the traffic should still be interrupted. As no presence is detected, the traffic lights turn green and the car's actuators restart their movement. Those systems and objects interoperate to provide solutions for the population, as as

- i. offering transportation options that could be more economical or optimized about time and lower risks, as it has been implemented in Singapore (Asiat, 2020);
- ii. operating systems to provide a collective sense of safety, avoiding collisions between cars, between these and public buildings or between cars and pedestrians, as in the application proposed by Taylor, Siebold & Nowzari (2020);
- iii. exchanging and sharing data/information or energy to prevent electricity, water, or other natural resources, such as sensors measuring the energy wasting in a neighborhood and alerting users they should save power;
- iv. offering solutions for the population using artificial intelligence (AI) algorithms that could deliver more optimized results than using hoc strategies, such as smart solutions to find faster or more economical routes to achieve a destination.

Hence, turning smart cities into reality inherently leads to the intensive use of technology in all the public sectors.

> ¹ This chapter was contributed by Valdemar Vicente Graciano Neto and Renato F. Bulcão-Neto.

DOI: 10.1201/9781003027799-3

As a matter of consensus, the Internet of Things (IoT) is the technical backbone intended to underpin smart cities (Alampalli & Pardo, 2014). Under perspective, a smart city connects a network of interconnected physical objects so-called “things”, i.e., various physical components that embed some portion of the software, including electronics, sensors, actuators, microcontroller, or a microprocessor-based device, embedded computing, and Radio Frequency Identification (RFID)-based devices. Things can transmit and receive data over the smart city network infrastructure to collect information from the environment, control other devices, exchange and process data, or interact with a user.

Given that first glance, we can deepen the IoT theoretical basis that supports smart cities and explore the possible synergies that can emerge from combining these topics to establish the forthcoming vision of what we know as cities.

This chapter involves offering a comprehensive background on smart cities besides how IoT is a critical topic in that domain. In the next section, we provide a motivational example that will guide our discussion for achieving that goal.

### 3.2 MOTIVATIONAL EXAMPLE

Our motivational example comprises a smart home. Smart homes (or smart houses) are important components of smart cities and materialize an ideal scenario to explain how IoT and smart systems, are tightly intertwined. In our example, the smart home is owned by an older adult, who demands a sort of specific services. That house consists of a domestic environment monitored by sensors to provide elderly people with fall detection and notification service. Falls are a fairly important topic, being one of the main reasons that leads to injuries and deaths of older adults (Burns, Stevens & Lee, 2016). As such, smart home environment has been equipped with IoT technologies to monitor and detect falls and notify smart emergency services accessible by citizens in a (Chaudhuri, Thompson & Demir, 2014; Gutierrez-Madñal et al., 2019).

In our scenario, an elderly person can be monitored by wearable and nonwearable devices. Device used in their everyday life, such as smartphones and smartwatches (Maudlin et al., 2018). Conversely, when the person is in the bathroom, nonwearable devices such as conversational agents, depth cameras (e.g., Kinect), and Doppler radar can monitor to instantaneously detect a fall (Anishchenko, Zhurav & Chizh, 2019). Although a small percentage of falls occurs in the bathroom, they are at least twice as likely to result in an injury as in other in-home places (Mulley, 2001; Stevens, Mahoney & Ehrenreich, 2014). Moreover, most of those falls are not detected, once people take off the wearable devices, for example.

Regardless of what happens, when a fall is detected, the smart home environment should notify emergency services that health professionals could assist the elderly, sending an ambulance and removing him/her as soon as possible. The smart home system then notifies an emergency service. The emergency service sends an ambulance that communicates with the smart traffic monitoring system to find the shortest and fastest path until the elderly’s route. Meanwhile, the traffic monitoring system monitors the ambulance’s route in response to likely traffic problems. The ambulance reaches the destination, the older adult is then removed.

# Smart Cities

The ambulance communicates with the most equipped hospital that could receive the elderly for emergency treatment and exams. The destination is a smart hospital that alerts the elderly emergency contacts as she/he is admitted. Meanwhile, a sensor network continuously monitors the patient's vital signs whenever her/his worsens.

Using this example, in the following sections, we will bring the theoretical and technological basis that converges IoT and smart cities, the anatomy of a smart city, and discuss the challenges that remain in the adoption of IoT.

### 3.3 BACKGROUND

A smart city is a complex network of several independent systems. Smart cities use ICTs, IoT, and other means to improve life quality and efficiency of urban operations while ensuring it meets the needs of present and future generations with respect to economic, social, and environmental (sustainability) aspects (ITU-T, 2014).

Standards for smart cities and their different components, including smart grids, the IoT, eHealth, and intelligent transportation systems (ITS), have been developed. A specific example of such a standard is ISO 37120 (ISO, 2014), which defines 100 city performance indicators, 64 core and 54 supporting, some of which include economy, education, energy, and environment. IoT can play an important role in smart cities by enabling the collection of some indicators. For instance, sensors collect environmental or energy data, such as humidity and air quality, or the energy expenditure in a neighborhood. Components of a smart city include smart infrastructure, smart buildings, smart transportation, smart energy, smart healthcare, smart technology, smart governance, smart education, and smart citizens (Mohanty, Choppali & Kougianos, 2016; Manzano, Graciano Neto & Nakagawa, 2020).

A smart city is actually formed by a high diversity of smart components and systems. Smart houses, smart traffic control systems, and autonomous cars are other examples of systems that are part of the smart cities. They are networked together and need to operate at a certain level to make the city work. By "certain level" we mean that not all the systems directly operate. For instance, smart buildings and smart traffic control systems do not have many reasons to operate, while, in parallel, a traffic control system and autonomous cars certainly should be able to convert.

As shown in Figure 3.1, a smart city is structured on many levels. In general, these levels are materialized by geographic coverage. At the bottom level, we have isolated systems. These systems are private properties, such as smart houses, smart buildings, autonomous cars, and smart hospitals. In the next level, we find the first level of interoperability that, in general, directly links the private systems to other external systems, such as the smart home from our motivational example that is linked to a public emergency service. Actually, multiple systems within a smart home environment can be linked to systems externally, as wearable devices linked to emergency services and electrical devices linked to
