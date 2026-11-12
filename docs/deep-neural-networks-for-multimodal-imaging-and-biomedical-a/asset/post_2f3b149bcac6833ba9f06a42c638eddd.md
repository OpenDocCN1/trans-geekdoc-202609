
## INTRODUCTION

In India, marigold is one of the most commonly grown flowers and used extensively during religious and social functions in various forms. Based on the cultivation report (Sujitha & Shanmugasundaram, 2017), the southern state namely Tamil Nadu which ranks number one among the marigold production, that covers 6733 hectare with an estimated production range of ~100995 tonnes annually, and the productivity ranges around 15 tonnes/hectare. Most of the time, the marigold flowers are intentionally grown as decorative crops that could be marketed as loose flowers or ornamental garlands for specialty usage. It is also one of the prominent instinctive origins of xanthophylls as an artificial additive to brighten poultry skin and egg yolks (Sujitha & Shanmugasundaram, 2017). Apart from these usages, the most part of the flowers also being used efficaciously for commercial dyestuff fabrics (Sujitha & Shanmugasundaram, 2017). High necessities of marigold flower either as a extracted products or as cut flower is always peak in most of the developed and developing countries (Italy, Taiwan, South Korea, Japan, UK, Mexico, Spain, United States). Hence, exportation of marigold flower plays a crucial role in the uplift of farmer's economy. Although the entire cultivation of flower is systemically exercised in an open field environment, still the irrigation process lacks the regulated and efficient utilization of water which is the firm demand for the raise in yield.

Smart irrigation is rightfully became a crucial practice of modern days agriculture. For majority of the cropping strategies especially in arid and semiarid regions require an efficient and systematical irrigation system to yield the maximum production, and to elevate the socio-economic condition. Beside linear-movable irrigation systems, Self-propelled centre pivot systems are commonly applied to irrigate the agri-field quite systematically; however, crucial variances in soil properties and water availableness exist all over the fields (Crow & Wood 2003). Automated irrigation systems are efficient to irrigate plants to an appropriate level for a normal growth of plants. Conventional method results in the reduction of productivity and energy.

The modern techniques of Neuro-fuzzy have found application in almost all the fields. The “Neuro-Fuzzy” term entails a kind of system characterized for a similar structure of a fuzzy controller where the fuzzy sets and rules are adjusted using neural networks tuning techniques in an iterative way with input and output system data. The system includes two distinct way of behavior. In the first phase called learning phase, it behaves like neural network that learns its internal parameter. In the second phase called the execution phase, it behaves like a fuzzy logic system.

Neural-fuzzy networks are often referred as connectionist models that are trained as neural networks, but their system is structurized as a fuzzy rule interpreter to obtain an unambiguous, crisp resultant. A Neuro-fuzzy inference system comprises a set of linguistic rules and an inference operation that are substantiated or aggregated with a connectionist framework for better adaption.

The neuro-fuzzy controller which is developed can determine the quantity of water required by plants in well defined depth using sensor nodes such as soil moisture sensor, humidity sensor and temperature sensor. Automatic irrigation scheduling system can be used to supply the water automatically based on the measurements specified through sensors. Sensors fixed in the field are used to ensure the water level in the soil. A solution to the problem of excessive supply of water can prevent damage of crops.

The combined analysis of multi-images of the same specimen adopted in various imaging modalities is typically used to acquire more selective information about the flower growth progress than is potentially analyzed from just a single modality. Thus, after the successive execution of operational phase, to analyze the growth progress of marigold flower; Non-Subsampled Contourlet Transform (NSCT) is employed for fusing multi-modal images (L. da Cunha et al., 2006).

The proposed neuro-fuzzy based smart irrigation technique in precision agriculture of marigold cultivation is addressed in Section 2 of this chapter. The complete evaluation of smart irrigation system based upon the multimodal image analyzing is also discussed in Section 3. Justifiable and reasonable conclusion and the future research work of this proposed technique is discoursed in the Section 4 of this chapter.

## PROPOSED SMART IRRIGATION SYSTEM

To study the effect of smart irrigation system, the demonstration and research analysis was carried out in marigold crop field at Hosur region in Tamil Nadu state of India, which is located at the longitude of 77.8597148 and latitude of 12.7499988. The proposed smart irrigation system will collect temperature, soil moisture and humidity data from the marigold farming environment through deployed WSN in each hourly basis with respect to the current time stamp. Soil moisture evaporation rate depends on the above parameters. These parametric values are sensed by corresponding wireless sensors node and further the real-time data are processed through neuro-fuzzy system. Based on the final resultant of the process the irrigation procedures are carried out. The entire block diagram of the process is described in Section 3.1.

### Process Flow of the System

The process flow of the proposed system is depicted in the figure 1, apart from that the internal process of the neuro-fuzzy schema is shown in figure 2. Initially, all the sensed data from the layer 1(temperature value, current soil moisture value, and present humidity value) were collected and provided as input parametric value to the Layer 2 part of neuro-fuzzy system for Fuzzification process. Then several fuzzified values are treated with well framed rule-base in layer 3 which produces a specified output fuzzified values to each of the input fuzzified value set in layer 4. Finally, to obtain a crisp output; a defuzzification methodology is applied on those output values in layer 5.

### Clustering Phase

### System Model

The following parameters are considered in the demonstrative analysis. (1) Temperature sensor, humidity sensor, and soil moisture sensor are considered for monitoring and irrigation process. In this experimental demonstration one hectare of marigold crop field is chosen and nodes are dispersed randomly in a 100 × 100 square unit of that region following a uniform distribution. (2) Base station is fixed in the centre of the experimental field and all the nodes after their deployment send join messages to the base station containing their local information such as location coordinates, energy status, and neighboring node details. (4) The base station (BS) is a node with no energy constraint and enhanced computation capabilities.

### Figure 1. Block diagram of WSN based Smart Irrigation Schema

![](img/a636f78302652a9c2ec5900d81fba475_255_0.png)

### Figure 2. Block diagram of Neuro-fuzzy inference Module

![](img/a636f78302652a9c2ec5900d81fba475_255_1.png)

### Cluster Formation and Cluster-Head (CH) Selection Module

Without the involvement of separate algorithm for clustering, BS forms the static clusters based on the horizontal and vertical lines that are originated from fixed coordinates which is referred as Cluster Segregation Point (CSP). Thus, approximately four cluster zones namely UL, UR, LL, and LR zones are formed which is depicted in figure 3.

Since all the nodes in the network are of homogenous type, each and every parametric values and processing capabilities are also found to be same. Thus, initially, a randomized node which is very close to the CSP is chosen as Cluster Head (CH) in each zone. After this, all the Chosen CHs broadcast its selection information as an advertisement messages to all other non-CH nodes within their zonal range
