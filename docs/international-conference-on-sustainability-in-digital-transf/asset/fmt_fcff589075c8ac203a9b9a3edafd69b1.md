
# Occupancy Detection in Buildings

## PIR Sensors
The PIR sensor is probably the most widely used method of detection in buildings for occupant sensing, particularly for illumination control. Despite a substantial body of research on occupant sensing in building contexts over the past couple of years, technological limitations with PIR sensors continue to impede the exploration of novel occupancy sensing solutions \[[3](#ch55.xhtml#ref55_3)\]. The potential use of PIR sensing in buildings is well recognised to be limited due to numerous fundamental limitations. (a) PIR sensors are capable of delivering only rough binary data (occupied or unoccupied) (b) PIR sensors necessitate a straight line of vision from the location of the sensor and people in the vicinity of a place \[[4](#ch55.xhtml#ref55_4)\]; (c) PIR sensors demand continual movements to function properly (i.e., occupants must remain seated or the sensor’s view is obstructed by obstacles such as objects) (d) PIR sensors can be affected by different thermal currents such as heated coffee/tea, electrical gadgets, and heating & ventilating systems.

## Applications of Carbon-Dioxide Sensors
The amount of CO[2] in a space goes up directly when people are there. It has been shown that the CO[2] sensor is the best environmental sensor for figuring out how many people are in a room \[[2](#ch55.xhtml#ref55_2)\]. It can find things between 85% and 95% of the time. Statistical pattern matching was used by Szczurek et al. to come up with a simple way to estimate the number of occupants \[[5](#ch55.xhtml#ref55_5)\]. First, the researchers had been using a time sequence technique to measure and record the Concentration of carbon dioxide. Then, they used pattern matching to look at the relationship between the framework of the time series and the availability.

Dong \[[6](#ch55.xhtml#ref55_6)\] also used a mix of sensors (temperature, moisture, CO[2], and light) to find out if there were people in a room. He observed that the CO[2] sensor data had the most impact on the findings of the prediction. Above figure shows the two most common ways that sensors can be put together. The first one has a camera, a PIR sensor, and a CO[2] sensor. A CO[2] sensor is set up in the room to find out how many people are in there. On the seat of the occupant, a PIR sensor is set up to check if the person is there. The camera records how the person actually moves. [Figure 1](#ch55.xhtml#fig55_1) depicts applications of sensors in availability detection. This fusion is good for figuring out if there will be more than one person in an office building. Arora et al. showed a system for estimating occupancy by combining data from many sensors, such as temperature, humidity, CO[2], lighting, PIR, door state, and energy utilization \[[7](#ch55.xhtml#ref55_7)\].

![Figure 55.1 Occupancy detections using sensors](images/fig55_1_C.jpg)

[Figure 55.1 Occupancy detections using sensors](#ch55.xhtml#R_fig55_1)

Using environmental sensors to guess the number or variety of people in a room is more difficult. Since the raw sensory data is loud and not useful for estimating occupancy, study aimed to use a technique called “feature engineering,” which is often used for machine learning models \[[4](#ch55.xhtml#ref55_4)\]. The two parts of feature engineering are feature extraction and recovery of features. Using domain knowledge, feature extraction is the process of making some informative representations of the raw data. Feature selection is the process of choosing some features that are more insightful based on certain parameters. Zhang et al. used statistical modelling to combine CO[2] and power consumption data to estimate how many people were in a building \[[8](#ch55.xhtml#ref55_8)\]. First, they used a physical diffusion model to pull out some features from CO[2] . For occupancy prediction with restricted training data, statistical distribution was used with two models: maximum a posteriori probability (MAP) estimation of HMM and multiple-hypothesis sequential probability ratio test (MSPRT). First, they took the raw sensory data and pulled out some relevant properties. Then, information gain theory was used to choose which features to use. Using the chosen features and a DT algorithm, the number of occupants was finally found. In their other work, \[[9](#ch55.xhtml#ref55_9)\], they also added a microphone that can measure the room’s sound level. The same method for choosing features was used. The DT and RF learning algorithms were used to estimate how many people were in the room \[[10](#ch55.xhtml#ref55_10)\]. [Figure 2](#ch55.xhtml#fig55_2) shows how sensor-based occupancy detection works.

![Figure 55.2  Steps included in sensor-based occupancy detection](images/fig55_2_C.jpg)

[Figure 55.2  Steps included in sensor-based occupancy detection](#ch55.xhtml#R_fig55_2)

## Conclusion
Occupancy detection in buildings is beneficial in controlling things like illumination and ventilation, which saves energy and keeps the building comfortable. But because of their limitations, PIR and environmental sensors always make mistakes in detecting people and collecting data. By making occupancy predictions more accurate, the difference between what actually happened and what was predicted could be cut down by a lot. When CO[2] sensors and cameras are used to record data, the accuracy of the data is high. Light has a big effect on how well a camera can see, but a CO[2] sensor can compensate for this. The article discusses many methods of detecting occupancy, primarily using IR and CO[2] sensors.

## References
1.  [Wang, D., Federspiel, C. C., and Rubinstein, F.](#ch55.xhtml#R_ref55_1) (2005). Modeling occupancy in single person offices. Energy and Buildings, 37, 121–126.

2.  [Candanedo, L. M., Feldheim, V., and Deramaix, D.](#ch55.xhtml#R_ref55_2) (2017). A methodology based on hidden Markov models for occupancy detection and a case study in a low energy residential building. Energy and Buildings, 148, 327–341.

3.  [Sharma, A., Chaturvedi, R., Sharma, K., and Saraswat, M.](#ch55.xhtml#R_ref55_3) (2022). Force evaluation and machining parameter optimization in milling of aluminium burr composite based on response surface method. Advances in Materials and Processing Technologies, 8(4), 4073–4094.

4.  [Amayri, M., Arora, A., Ploix, S., Bandhyopadyay, S., Ngo, Q.-D., and Badarla, V. R.](#ch55.xhtml#R_ref55_4) (2016). Estimating occupancy in heterogeneous sensor environment. Energy and Buildings, 129, 46–58.

5.  [Chaturvedi, R., Sharma, A., Sharma, K., and Saraswat, M.](#ch55.xhtml#R_ref55_5) (2022). Tribological behaviour of multi-walled carbon nanotubes reinforced AA 7075 nano-composites. Advances in Materials and Processing Technologies, 8(4), 4743–4755.

6.  [Dong, B., Andrews, B., Lam, K. P., Höynck, M., Zhang, R., Chiou, Y. S., and Benitez, D.](#ch55.xhtml#R_ref55_6) (2010). An information technology enabled sustainability test-bed (ITEST) for occupancy detection through an environmental sensing network. Energy and Buildings, 42(7), 1038–1046.

7.  [Kumar, P., Singh, P. K., Nagar, S., Sharma, K., and Saraswat, M.](#ch55.xhtml#R_ref55_7) (2021). Effect of different concentration of functionalized graphene on charging time reduction in thermal energy storage system. Materials Today: Proceedings, 44, 146–152.

8.  [Liu, Z., Zhang, J., and Geng, L.](#ch55.xhtml#R_ref55_8) (2017). An intelligent building occupancy detection system based on sparse autoencoder. In IEEE Winter Applications of Computer Vision Workshops (WACVW), 2017, (pp. 17–22).

9.  [Chaturvedi, R., Islam, A., Singh, P. K., and Saraswat, M.](#ch55.xhtml#R_ref55_9) (202). Nanotechnology for advanced energy system: synthesis & performance characterization of nano-fuel. In AIP Conference Proceedings (Vol. 2721, No. 1). AIP Publishing.

10.  [Liu, H., and Motoda, H.](#ch55.xhtml#R_ref55_10) (199). Feature Extraction, Construction and Selection: A Data Mining Perspective, (Vol. 453), Springer Science & Business Media.
