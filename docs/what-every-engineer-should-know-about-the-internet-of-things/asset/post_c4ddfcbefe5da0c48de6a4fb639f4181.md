
IoT and Smart Energy

at consumption points that can indicate the real time demand. This has helped the island move from expensive and polluting fuel-based power generation to 100% clean renewable energy.

## 4.3.2 VIRTUAL POWERPLANT AND MICROGRID Aruba Caribbean Island

Virtual Powerplant advanced control system is used at Aruba island Endesa Gorona del Viento (https://www.endesa.com/en/projects/all-projects/energy-transition/renewable-energies/el-hierro-renewable-sustainability) as it does not have natural ways to store the energy as El Hierro island. Giving examples on islands as it is easier to visualize but this applies to all types of locations. With Smart Energy, power is carried across many interconnected islands “microgrids”. With advanced automation and control technologies the electricity generation system can function as a power plant integrating variable resources like wind and solar with weather forecasting and real time monitoring to meet the demand while keeping the grid stable and using less power generation from traditional fossil fuels. This predictive method of energy addition allows electric mobility to be accommodated and incentivize people to charge at home with lower electricity prices when there is abundance of renewable energy sources. This will lead to wider adoption of electric vehicles and further lower the pollution and fossil dependence.

## 4.4 CONCLUSION

As we have seen Smart Energy is essential and no longer optional for us to coexist and flourish with nature without consuming the planet. We need to produce and store energy in a sustainable and cost-effective way with digitalization to associate the bits with electrons in the decentralized system for decarbonization of the world to make zero-emissions a reality. Some aspects like storage, cybersecurity, and data need big attention in the development.

## FURHER READING

- Hansen, A., Staggs, J., Shenoi, S. “Security analysis of an advanced metering infrastructure,” Critical Infrastructure Protection, 2017. https://www.sciencedirect.com/science/article/abs/pii/S18745482173004957?via%3Dhub

- IEA on Energy Policy Opportunities for Electric Motor-Driven Systems. https://www.iea.org/reports/energy-efficiency-policy-opportunities-for-electric-motor-driven-systems, 2011.

- IEEE P2030.9. Guide for smart grid interoperability of energy technology and information technology operation with the electric power system (EPS), end-use applications, and loads. https://standards.ieee.org/project/2030.html, 2019.

![](img/41fdf2aa71adfa568d36836737f447e6_68_0.png)

## 5 Smart Cities – Security¹

## 5.1 INTRODUCTION

Smart cities use networked technology to gather data to optimize and manage city resources, businesses, and government entities. The optimization of a smart city comes from leveraging the data aggregated and analyzed that is collected from a city's assets. With the appropriate analysis of data collected from a city's assets, city components such as traffic patterns, energy distribution, and air quality can be improved more efficiently. These improved elements of a smart city can also increase the quality of life and convenience for its citizens, integrating IT technology into many aspects of a citizen's day-to-day tasks such as simplifying access to a city's services. According to the American Society of Mechanical Engineer (ASME), subjects such as mobility, healthcare, water, energy, engagement and community, economic development and housing, and security can all be integrated into the core of a smart city to create an infrastructure that makes a smart city (Kosowatz, 2020). The three US smart cities are New York, NY; Boston, MA; and San Francisco, CA (Datalux.com). Smart cities have also been deployed in many places such as Europe, Singapore, and South Korea.

Smart city implementations come with challenges such as insufficient funds, inconsistent connectivity, lack of experienced professionals, and security risks (Joshi, 2020). The focus of this chapter is on cybersecurity, and preparing countermeasures for the cyberattacks in a smart city can protect the lives of its citizens. Smart city security threats will be examined from a multilayer perspective, targeting representative elements that make up a smart city. This chapter will also describe attack scenarios and threat countermeasures. In addition, a discussion on educating the professionals needed to design and build smart cities will be provided.

## 5.2 SMART CITY ARCHITECTURE

One of the goals of a smart city is to improve the quality of life of people by building an IT infrastructure that improves the many pieces of everyday life. Figure 5.1 shows the multilayer architecture of a smart city. Figure 5.1 also shows the attack points of each layer. Security and privacy are essential in a smart city environment where many end-point devices are connected to the Internet, communicate with each other, and accumulate data store in a cloud. Cyberattacks on a smart city can debilit critical system such as water and electricity. In addition, these attacks can be very damaging on an individual level because smart cities are enabled by cyber-physical systems (CPSs), which involve connecting devices and systems as Internet of Things (IoT) (Aldairi & Tawalbeh, 2017). Emergency alert systems, street surveillance, and smart traffic lights are very vulnerable (Lawrence, 2021).

> ¹ Excerpts of this chapter are from Chung, Park and DeFranco (2021).

DOI: 10.1201/9781003027799-5

# What Every Engineer Should Know About IoT

# Cyber world

![](img/41fdf2aa71adfa568d36836737f447e6_70_0.png)

FIGURE 5.1 Smart city architecture.

To appreciate the severity, recall the 2018 situation in Hawaii where the emergency management agency mistakenly sent out this message,

> BALLISTIC MISSILE THREAT INBOUND TO HAWAII. SEEK IMMEDIATE SHELTER. THIS IS NOT A DRILL.

This false alarm was apparently not caused by hackers (according to the news), nonetheless critical phone systems had many attacks – where the attackers are looking for ransom payments in addition to determining where the weak points are in a critical network (Starks, 2018).

Researchers have faced security and privacy challenges for intelligent healthcare-transport, smart building and smart energy (Braun et al., 2018). However, there have been no studies on systematically addressing security level with a multilayer structure to include device/sensor level, network level, application level, and cloud level from viewpoint of security and privacy. In the remainder of this chapter, we will look at the attack points and countermeasures that exist on multiple layers of a smart city.

## 5.3 ATTACK POINT EXAMPLES IN A SMART CITY

In this section, we will discuss each of the attack point (i.e., device/sensor, application, network, cloud) with four smart city elements: smart transportation, smart healthcare, smart energy, and smart buildings.

## TABLE 5.1
The Device/Sensor Attack Points in Smart City

| Smart City Element | Device/Sensor Level |
| --- | --- |
| Smart transportation | smart car, street sign, smart traffic lights, streetlights, smart parking sensor |
| Smart healthcare | smart watch, fitness tracker, smart pacemaker, closed-loop insulin delivery (artificial pancreas) |
| Smart energy | air-conditioning, heating sensor, water leakage sensor, light sensor, temperature and humidity sensor |
| Smart building | smart thermostat, smart camera, smart speaker, smart door lock, smart baby monitor |

### 5.3.1 DEVICE/SENSOR LEVEL

Hardware chips of hub devices such as those that control digital devices or sensors (Table 5.1) can be exploited by physical attacks. Sensors used by smart cities are often built into traffic lights and streetlamps to manage parking and traffic congestion; however, wireless sensors are a vulnerability risk because they do not have built-in security. In addition, there are cases where the smart devices used in traffic lights, healthcare devices, energy sensors, and home environments are attacked at the hardware level (The 8 Most Common Types of Cyber Attacks Explained, 2019). For example, there were vulnerabilities discovered in Medtronic's infrastructure that enabled an attacker to control an implanted pacemaker remotely through compromised software updates (Newman, 2018).

### 5.3.2 APPLICATION LEVEL

As shown in Table 5.2, each element of smart cities use mobile or web applications to control the devices/sensors and to manage the data generated. Applications are a frequent target of cyberattacks via cross-site scripting (XSS) attacks (e.g., injecting malicious script into a client) or man-in-the-middle (MITM) attacks (e.g., data transfer eavesdropping). Smart cities are also a target of these type of attacks where transmitted data can be intercepted or altered.
