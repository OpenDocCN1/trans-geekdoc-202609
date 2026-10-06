
## PROPOSED METHODOLOGY

The primitive classes of activity are Sit, Stand, Walk, etc. In this chapter, an activity recognition framework, which enables active common activity recognition even when data is collected using one device kept at one position (say, shirt pocket) for training and activity is recognized for readings collected from a different device kept same or a different position (say, bag). The process utilizes only accelerometer sensor of smart phone which is available in almost all phones by any manufacturer making the framework ubiquitous. The proposed classification model can be employed on a wide range of human daily activity recognition problems. A two-phase activity recognition framework based on an ensemble of classifiers to identify static activities (Sit on chair, Stand) as well as dynamic activities (Walk, Climbing Stairs). The proposed technique work irrespective of device configuration and usage behavior.

This framework segregates static and dynamic physical human activities from smart phones raw accelerometer data and successfully classifies labels of several individual activities. Two static Sit and Stand, and two dynamic activities Walk and Climbing Stairs (CS) are considered in this work. The data are collected for these (Sit, Stand, Walk, CS) daily activities.

3. Raw accelerometer readings of different activities collected for 540s from a smart phone kept at right pant pocket

![](img/2d15ce7e8a63337e725a2581c64b1a6e_214_0.png)

Phase 1: Training device and position selection are crucial for activity recognition. Datasets from each training position are stored as train-test pairs, and classification accuracy is determined using different classifiers. The training dataset with maximum cross validation accuracy is used.

Phase 2: Identifying individual activities using a single base classifier is challenging, so ensemble methods are recommended. Ensemble methods combine hypotheses and use multiple base learners, resulting in a stronger generalization ability. Single base classifiers struggle to identify all activities with reasonable accuracy, so ensemble models are created based on their overall performance to identify multiple activities.

Figure 4. Block diagram of proposed two phase activity recognition framework

![](img/2d15ce7e8a63337e725a2581c64b1a6e_215_0.png)

This framework provides support to healthcare providers for assessing patients daily activity. It can help tracking activity of patients during post surgery period as they are not allowed to climb upwards or downwards. Activity recognition can also identify exact context of health monitoring.

## CONCLUSION

Human activity recognition and monitoring is an emerging field in pervasive computing. So, the aim of this chapter is recognizing daily actions with user setup. Smartphone hardware configuration, calibration, and usage behavior like the smart phone is kept for tests are important challenges that are addressed. Other challenges include uniform imprecise labeling of detailed activities. Machine learning techniques are applied to combine the data from different types of sensors. The machine learning models are developed to build classification model for HAR.

## REFERENCES

8. Billion Connected Things Will Be in Use 2017, Up 31. Available online: URL https://www.gartner.com/newsroom/id/3598 accessed on 19th September, 2020.

Babar, S. A., Arif, R., & Irfan, M. (2019). Internet of things-based smart city using big data analytics: a Survey. In Trends and Advances in IoT-enabled Networks (pp. 129–138). Springer. DOI: 10.1007/978-3-319-99660_12

Bouchabay, D., Nguyen, S. M., Lohr, C., LeDuc, B., & Kanellos, I. (2021). Using language model to bootstrap human activity recognition ambient sensors in smart homes. Electronics (Basel), 10(20), 2498. DOI: 10.3390/electronics10202498

Butt, S. A., Diaz-Martinez, J. L., Jamal, T., & Ali, E. Emir La-Hoz-Franco, and Muhammad Shoaib. IoT smart health therapies. In 2019 19th International Conference on Computational Science and Applications (ICCSA), IEEE, 2019.

Butt, S. A., Diaz-Martinez, J. L., Jamal, T., & Ali, E. Emir La-Hoz-Franco, and Muhammad Shoaib. IoT smart health therapies. In 2019 19th International Conference on Computational Science and Applications (ICCSA), pages 26–31. IEEE, 2019.

Chen, Shenfeng, Hongjing Fang, and Zhijian Liu. Human activity recognition based on extreme learning. Journal of Physics: Conference, Vol. 1437, No. 1. IOP Publishing, 2020.

Cornelis, E., Vancheberg, N., & De Viendi, P. (2019). The relationship between basic, instrumental, and advanced activities of daily living and executive functioning in geriatric patients with neurocognitive disorders. International Journal of Geriatric Psychiatry, 34(6), 889–899. DOI: 10.1002/gpos.5087 PMID: 3076119

de Oliveira, S., Felipe, J. V., Plácido, J., & enough, A. C. (2020). Spatial navigation and dual-task performance in patients with Dementia mental personality present in instrumental activity of daily living. IBRO, 9, 52–57. DOI: 10.1016/jibro.2020.06.006 PMID: 3363104

Dhruv, A. J., Patel, R., & Noshi, N. (2021). The most advanced programming language for computer science applications. Proceedings of the international conference on cultural heritage, education, sustainable, and innovation technologies -CESIT 2020, 2021.

Fahad, L. G., & Tahir, S. F. (2020). Activity recognition in a smart home using local feature weighting and nearest-neighbors classifiers. Journal of Ambient Intelligence and Humanized Computing, 1–10. PMID: 328375

Färber, M., Svetashova, Y., & Harth, A. (2021). Theories of Meaning for the Internet of Things. Concepts in Action. Springer.

Fazilov, F. (2021). Anti-Corruption Review in global health. Ilkogret Online.

Franco, P., Martinez, J. M., Kim, Y.-C., & Ahmed, M. A. (2021). IoT based approach for monitoring and activity recognition in smart homes. IEEE Access: Practical Innovations, 9, 45325–45339. DOI: 10.1109/ACCESS.2021.3067029

Fu, Z., He, X., Wang, E., Huo, J., Huang, J., & Wu, D. (2021). Personalized human activity recognition based on integrated wearable sensor and transfer learning. Sensors (Basel), 21(3), 885. DOI: 10.3390/s21030885

Garcia, K., Rebelo, D., Pohl, C., Carvalho, M. (2021). On human activity recognition sensors to improve the performance of collaborative mobile manipulators: Review and outlook. Procedia CIRP, 97, 211–216. DOI: 10.1016/j.procir.2020.05.025

Gaur, D., & Dubey, S. Machine learning approaches. Proceedings of the International Conference on Paradigms of Communication, and Data Sciences. Springer, Singapore, 2022. DOI: 10.1007/978-9-030-16547-4

Kim, H., Choi, H., Kang, H., Yoon, S., & Hong, T. (2021). A systematic review of the smart energy system: From smart to sustainable. Renewable & Sustainable Energy Reviews, 140, 107155. DOI: 10.1016/j.rer.2021.107155

Li, Q., Ravina, R., Li, Y., Almasmi, S., Sun, F., & Fortune, G. (2020). Multi-user activity recognition: Challenges and opportunities. Information Fusion, 63, 121–135. DOI: 10.1016/j.infus.2020.06.004

Ma, Y., Arshad, S., Muniraju, S. (2021). Location and person-independent activity recognition with WiFi, deep networks, and reinforcement learning. ACM Transactions on Internet of Things. DOI: 10.1145/3424379

Manaf, A., & Singh, S. Computer Vision-based Survey on Human Activity Recognition System, Challenges and Opportunities. 2021 3rd International Conference on Signal Processing and Communication (ICSPC). IEEE, 2021.

Mohamed, N., Al-Jarood, J., & Jawhar, I. Towards-tolerant fog computing for IoT-based smart city applications. 2019 IEEE 9th Annual Conference and Communication Workshop and Conference (CCWC), pages 0752–0757. IEEE, 2019.

Quinting, J. F., &ing, C. M. (2021). Toward a systematic evaluation of warm conveyor belts in weather numerical prediction and climate models. Predictor selection and logistic regression model. Journal of Atmospheric Sciences, 78(5), 1465–1485. DOI: 10.1175/JAS-D-20-0139.1

Ramasubramanian, A. K., Aiman, S. M., & Papakostas, N. (2021). On human activity recognition sensors to improve the performance of collaborative mobile manipulators: Review and outlook. Procedia CIRP, 97, 211–216. DOI: 10.1016/j.procir.2020.05.025

Ritchie, Hannah, and Max Rose. Urbanization. Our world in data, 2018.
