
Cancer Patients by Artificial Neural Network Model.” Gastroenterology and Hepatology From Bed to Bench 11, no. 2 (2018): 110.

[10] Ferjani, Marouane. (2020). Disease prediction using machine learning. https://doi.org/10.13140/RG.2.2.18279.47521.

[11] Huang, Binglu, Shan Tian, Na Zhan, Jingjing Ma, Zhiwei Huang, Chukang Zhang, Hao Zhang, F. Ming, F. Liao, M. Ji, and J. Zhang. “Accurate Diagnosis and Prognosis Prediction of Gastric Cancer Using Deep Learning on Digital Pathological Images: A Retrospective Multicentre Study.” EBioMedicine 73 (2021).

[12] Gupta, Mayuri, and Ashish Mishra. “A Systematic Review of Deep Learning Based Image Segmentation to Detect Polyp.” Artificial Intelligence Review 57, no. 1 (2024): 7.

[13] Jha, Debesh, Sharib Ali, Nikhil Kumar Tomar, Håvard D. Johansen, Dag Johansen, Jens Rittscher, Michael A. Riegler, and Pål Halvorsen. “Real-Time Polyp Detection, Localization and Segmentation in Colonoscopy Using Deep Learning.” IEEE Access 9 (2021): 40496–510.

[14] Bernal, Jorge, Nima Tajkbaksh, Francisco Javier Sanchez, Bogdan J. Matuszewski, Hao Chen, Lequan Yu, Quentin Angermann, O. Romain, B. Rustad, I. Balasingham, and K. Pogorelov. “Comparative Validation of Polyp Detection Methods in Video Colonoscopy: Results From the MICCAI 2015 Endoscopic Vision Challenge.” IEEE Transactions on Medical Imaging 36, no. 6 (2017): 1231–49. https://doi.org/10.1109/TMI.2017.2664042.

[15] https://www.kaggle.com/datasets/plhalvorsen/kvasir-v2-a-gastrointestinal-tract-dataset. Accessed January 2024.

[16] https://github.com/Bhavanam-Gireesh-Reddy/Stomach-Disease-Prediction.

## 3 Data-Driven Techniques for Fault Diagnosis and Predictive Maintenance

Aparna Sinha and Debanjan Das

### 3.1 INTRODUCTION

In the new era of Industry 4.0, industries need to evolve and adapt to the use of new technologies to make them self-aware and self-sustainable. The maintenance and health diagnosis of industrial machines, equipment, and systems play a crucial role in ensuring safety, reliability, and production efficiency across several industries. A fault is an abnormal condition that may prevent the industrial equipment from performing its required function. This leads to non-permitted deviation of one or more characteristic properties of the system from their acceptable conditions [Gao et al., 2015]. The machine’s health may degrade due to prolonged usage, aging, harsh working conditions, etc., causing unscheduled downtime and accidents and impacting the yield and manufacturing cost of the industry [Webert et al., 2022]. It is to be noted that the maintenance cost accounts for nearly 15% to 60% of the manufacturing cost in the industry [Shukla et al., 2022]. Traditional health monitoring techniques involve manual inspection at scheduled intervals, which depends on the operator’s experience and is prone to human error. Another primitive strategy is corrective maintenance or ‘run-to-failure’ in which the maintenance is done after the failure occurs [Nunes et al., 2023], leading to unexpected production halt and decreasing the life expectancy of the equipment concerned. In order to mitigate the financial losses incurred due to unexpected production stops, a proactive approach known as predictive maintenance (PdM) has evolved, which predicts a failure before its occurrence. This results in less downtime in safety-critical operations, longer asset life, and improved yield and efficiency of the industry. This chapter aims to develop a fault diagnosis framework for the overall PdM of the industrial systems and the associated machines and equipment.

In general, the existing fault diagnosis techniques can be broadly classified as model-based and data-driven. The model-based methods involve complex mathematical modeling [Topan et al., 2016], but they require vast knowledge of the internal workings of the concerned machine and are difficult to implement for real-time applications. These challenges can be mitigated using data-driven artificial intelligence (AI) and machine learning (ML) methods in conjunction with the Internet of Things (IoT). The IoT plays a pivotal role in predictive maintenance by enabling real-time and remote monitoring, data collection, and analysis, which are critical for

![](img/a454246e6e2ea26f4583534f7cbdd134_43_0.png)

anticipating equipment failures and optimizing maintenance schedules and costs. Additionally, IoT technology is highly scalable, making it suitable for monitoring thousands of assets across large industrial operations. The industrial IoT or IIoT [Yang et al., 2022] helps to improve the reliability, security, robustness, and timeliness of industrial systems. Figure 3.1 shows one such real-life industrial scenario where the IoT platform is utilized for efficient PdM.

### 3.2 DATA CATEGORIES FOR PREDICTIVE MAINTENANCE

In industry, predictive maintenance relies on two categories of data—process data and the associated machine health data, and each of them provides unique insights into the condition of the system or machine. As shown in Figure 3.1, both these data categories are acquired through the IoT platform. Now, let us first discuss these two data categories in detail.

#### 3.2.1 PROCESS DATA

Process data refers to information related to the real-time operation or functioning of a system. This includes various system process metrics, such as temperature, pressure, flow rates, speed, concentration, voltage, current, etc. These process data are often acquired via a distributed control system (DCS), such as a supervisory control and data acquisition (SCADA) system, or using the IoT platform. Process data helps monitor the system's performance during operation. By analyzing these metrics, industrial operators can detect abnormal behaviors or deviations from normal operating ranges, which may indicate potential issues before they escalate into failures.

#### 3.2.2 Machine Health Data

Health data provides information about the condition or integrity of the machine/equipment. It reflects the physical or structural health of the equipment. The health data are often collected through sensors and include metrics such as vibration, acoustic, ultrasound, etc. The equipment lifespan and rate of failure can be predicted by analyzing the health data.

### 3.3 Common Faults in Industries

In industries, faults can occur across a wide range of sectors, affecting systems, sub-systems, and machines due to prolonged usage, aging, overheating, leakage, unfavorable working environment, poor insulation, etc. These faults have an adverse effect on the operations and yield, cause safety issues, and result in significant downtime. Some common industrial faults are discussed in this section.

Large industrial systems generally suffer from various faulty phenomena that accumulate gradually over time and ultimately lead to catastrophic accidents, unexpected downtime, and significant loss of yield. One such critical industrial system is the boiler, which is widely used in various industries such as power plants and petrochemical, textile, building and construction, and paper and pulp industries, etc. These boilers often suffers from different faults like corrosion [Nugraha et al., 2023], slagging [Xu et al., 2021], fouling [Shohet et al., 2019], clinkering [Sinha et al., 2023b], etc. The early detection and prediction of such faults in the industrial system using the different process data is essential.

Apart from the major industrial systems, there are several associated machines and auxiliary equipment that help in controlling the various operations of these systems. These include pumps, motors, valves, fans, conveyor belts, etc., and various mechanical and electrical faults may arise in these machines. The pumps are prone to cavitation faults [Liu et al., 2023], seal damage and corrosion [Ahmad et al., 2020], which can be detected using health data such as vibration and acoustic emission signals. Another important industrial machine is the motor, and it suffers from different stator [Sinha and Das, 2023b], rotor [Xu et al., 2022], and bearing [Sinha et al., 2023a] faults. Valves play an important role in regulating, directing, or controlling the flow of fluids in industrial systems, and they suffer from failures such as leakage, clearance, cracks, and notches [Jafari et al., 2014]. The industrial fans and blowers undergo dust accumulation, blade damage, misalignment, etc. [Ciaburro et al., 2023; Dhamande et al., 2023], which may also be detected by intelligent analysis of health data such as vibration and acoustic.

The continuous health data acquisition for machine health diagnosis is carried out by mounting sensor nodes, which contain sensors, batteries, microcontroller, and trans-receiver. Among these components, the microcontroller and trans-receiver are less prone to faults compared to the sensors and batteries. For a sustainable solution, the node architecture must be capable of self-health monitoring of these electronic components. Rechargeable Li-ion batteries are commonly used due to their higher energy density, lower self-discharge, and prolonged lifetime compared to other battery types [Liu et al., 2022]. However, they also degrade over time with an increase in charge-discharge cycles. Since the battery provides power to the entire sensor node,
