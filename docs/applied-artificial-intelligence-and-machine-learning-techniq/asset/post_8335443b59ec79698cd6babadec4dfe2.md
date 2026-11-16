
its timely health prediction is essential [Sinha et al., 2022]. Another vital component of the node, the sensors, suffers from various faults, such as drift, bias, complete failure, and precision degradation [Sinha and Das, 2023c]. The presence of these faults may mask or indicate faults in the associated machines; hence, automatic sensor fault detection becomes very important [Sinha and Das, 2023d]. In real-life industrial scenarios, faults may occur simultaneously in both the sensors and the associated machines. In such situations, sensor fault isolation and correction are required for successful health monitoring of the industrial machines [Sinha and Das, 2023a].

## 3.4 PREDICTIVE MAINTENANCE: THE GOOD AND THE BAD

Traditionally, the industry operators perform preventive maintenance (PM) on a scheduled basis, regardless of the machine’s condition and necessity for maintenance. This often leads to higher maintenance costs and inefficient use of resources. On the other hand, reactive maintenance (RM) is performed only after a failure occurs, causing unexpected downtime and higher repair costs. The challenges posed by these under-maintenance and over-maintenance methods can be overcome by predictive maintenance. It is a proactive maintenance strategy that uses data-driven methods to predict when industrial machines or systems may fail and allows early maintenance to be performed to prevent failures. The following subsections discuss the advantages and disadvantages of PdM.

### 3.4.1 ADVANTAGES OF PREDICTIVE MAINTENANCE

Some important advantages of PdM are listed as follows:

- **Reduced Downtime:** PdM reduces unexpected machine failures by identifying potential issues before complete breakdown. This ensures that maintenance is scheduled during planned downtime, thereby minimizing unplanned operational halts.
- **Cost Efficiency:** PdM averts major equipment failures and optimizes maintenance schedules, thereby minimizing costly emergency repairs and overtime labor.
- **Extended Equipment Lifespan:** Early detection of faults prevents excessive damage to machines, allowing them to operate more efficiently for a longer period.
- **Improved Safety:** Early identification of potential hazards and machine failures reduces the risk of accidents and injuries caused by malfunctioning machinery, ensuring a safer work environment.
- **Data-Driven Insights:** PdM analyses data collected via sensors and IoT to monitor equipment performance in real-time, providing valuable insights into machine health and efficiency and assisting in informed decision-making.
- **Asset Management:** PdM optimizes resource usage by conducting maintenance only when necessary, thus helping with efficient asset management.
- **Increased Reliability:** PdM strategy ensures well-maintained and monitored equipment, which improves reliability and reduces the frequency and severity of production interruptions, thereby increasing the yield.
- **Energy Efficiency:** PdM increases energy efficiency by keeping machines in optimal working condition, avoiding excess energy consumption by faulty machines.
- **Environmental Benefits:** PdM helps to maintain machines in optimal working conditions, prevents unexpected breakdowns, improves energy efficiency, and reduces waste, emissions, and adverse impact on the environment. Thus, the industries can meet sustainability goals with reduced energy consumption.

For a better understanding, the advantages of PdM over the traditional PM and RM strategies have been summarized in Table 3.1. Despite its many advantages, PdM comes with its own set of challenges, which are discussed in the next subsection.

### 3.4.2 Disadvantages of Predictive Maintenance

The key disadvantages of PdM are discussed as follows:

- **High Initial Costs:** A significant initial investment is required in technology, including sensors, data acquisition tools, and predictive analytics software to set up a PdM system. Small and medium-sized businesses with limited budgets may struggle to manage the high initial costs.
- **Technical Expertise:** Another challenge in PdM implementation is the requirement of specialized knowledge in data analytics, machine learning, and condition-monitoring technologies. Industries will need to hire or train personnel with expertise in these areas, leading to additional expenses.
- **Compatibility Issues:** PdM is not suitable for all types of equipment (e.g., low-criticality or simple machines), making traditional maintenance strategies more justifiable for such assets. Another challenge may arise in integrating PdM systems with existing systems like enterprise resource planning (ERP), computerized maintenance management systems (CMMS), or supervisory control and data acquisition (SCADA), requiring significant customization.
- False Alarms: PdM systems can sometimes generate false positives (predicting a failure that does not happen) or false negatives (failing to predict an impending failure). Such prediction errors can lead to unnecessary or missed maintenance, respectively.
- Cybersecurity Risks: PdM systems using IoT devices and cloud-based platforms are often vulnerable to cyberattacks, causing data breaches, disruption of operations, and compromised asset security.
- Cultural Resistance: Shifting from traditional maintenance strategies to PdM requires a cultural change within the organization. Employees and management may resist adopting new technologies or processes, especially if they are comfortable with current practices.

For industries considering PdM implementation, it is important to weigh these disadvantages against the potential long-term benefits, taking into account factors like the type of equipment, available resources, and readiness for technological adoption.

## 3.5 THE PREDICTIVE MAINTENANCE BLUEPRINT

Predictive maintenance involves a systematic approach to condition monitoring, starting from real-time data acquisition to detection and prediction of machine failures. The key steps of predictive maintenance workflow in industries are shown in Figure 3.2. The detailed breakdown of the steps involved in PdM has been explained in the following subsections.

![](img/a454246e6e2ea26f4583534f7cbdd134_47_0.png)

FIGURE 3.2 Generalized workflow for implementing predictive maintenance in industries.

### 3.5.1 DATA ACQUISITION

Data acquisition forms the foundation of the PdM strategy, as it provides the raw information required for effective fault diagnosis and prediction. Some of the common sensors used for data collection for PdM are as follows:

- (i) Vibration Sensors: These sensors measure the vibrations in rotating machinery. Abnormality in vibrations may indicate wear, misalignment, or any other faults.
- (ii) Acoustic Sensors: These sensors help in detecting sound waves generated by machines. Abnormal acoustic data can indicate a wide variety of faults, such as leaks, cracks, etc.
- (iii) Temperature Sensors: These sensors are often employed to detect overheating, which is a sign of mechanical or electrical issues. They are also used to maintain an optimum environment in critical applications such as warehouse management.
- (iv) Ultrasound Sensors: The ultrasound sensors capture high-frequency sounds to detect leaks, electrical discharges, material fatigue in structures, or bearing lubrication issues.
- (v) Flow Sensors: These sensors measure the flow rate in fluid systems to detect the presence of any irregularities or blockages.
- (vi) Proximity Sensors: These sensors can identify alignment problems by measuring the distance or positioning of moving parts.
- (vii) Current/Voltage Sensors: These sensors monitor the health of electrical machines to detect faults such as spikes, short circuits, etc.

In certain industrial applications, data acquisition systems (DAQ) are utilized to collect sensor data and convert it into digital form for further analysis. They contain signal conditioners to prepare raw sensor signals for processing by filtering or amplification. DAQ systems also include analog-to-digital converters (ADC) to convert the analog sensor signals into digital data so that they can be analyzed by computers. The effectiveness of the different sensors heavily relies on how and where they are installed. Incorrect sensor mounting can lead to false readings, missed faults, and inaccurate diagnosis.

### 3.5.1.1 Sensor Mounting

To ensure that the collected data (e.g., vibration, temperature, sound, etc.) accurately reflects the true condition of the machines, proper sensor mounting is essential. Correct sensor positioning ensures consistent reading and helps minimize noise from external factors. This enables a reliable trend analysis and fault diagnosis scheme for critical industrial machines and systems. Some common sensor mounting techniques are discussed here.

- (i) Direct/Contact Mounting: The sensor is directly attached to the machine under testing, such that the sensor is in constant contact with the machinery and obtains real-time data. However, they are not securely fastened and
