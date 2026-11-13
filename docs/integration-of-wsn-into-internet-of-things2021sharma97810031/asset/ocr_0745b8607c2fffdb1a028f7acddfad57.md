| Year | Data Analysis |
| :--- | :--- |
| 2001 | IoT implemented in 520 million farms |
| 2015 | 530 Million farms connected with smart IoT-based systems |
| 2020 | Forecast that 680 million farms would be converted into smart farms by implementing IoT-based smart technologies in the farming activities |
| 2050 | 2 Billion farms would be smart farms |

# 7.4 CASE STUDY—A SMART IRRIGATION SYSTEM

In the previous section, we have seen the emergence of smart agriculture. It is evident that IoT plays a key role in smart agriculture. Sensors are necessary to gather information about agricultural fields, climate parameters, and soil. Now, we present a case study—a smart irrigation system using automation. We developed a smart irrigation system at the laboratory using the WSN and sensors [31,32].

# 7.4.1 INTRODUCTION

The proposed system makes use of WSNs and collects data using multiple sensors installed at different nodes and sends the gathered data to the cloud via the wireless protocol. This smart agriculture system is developed using Arduino UNO, temperature sensor, moisture sensor, water level sensor, direct current (DC) motor, general packet radio service module, and Wi-Fi module. Irrigation system starts with checking the water level, humidity, and moisture level. It informs the farmers by generating an SMS alert on their phones regarding the levels and automatically starts the water pump. If the temperature goes above the threshold level, it automatically starts the fan. It constantly displays the status using LCD display. Constantly, the recordings are sent to cloud where it can be analyzed to find out the pattern and predictions can be made. The block diagram for the entire setup is shown in Figure 7.1. It shows the input (via sensors) and the output (via actuators or motors). The processor is Arduino UNO. The live data are stored to cloud.

The agenda is to assist the farmers by providing live environmental data like temperature and moisture for better environment and soil monitoring and enable the smart farming. It will increase the crop yield, and the quality of products will be enhanced. The live data feed is stored using cloud “ThingSpeak.com.” It is tested over diverse agricultural lands and shows a high accuracy of 98%.

# 7.4.2 WORKFLOW

The automated irrigation system works as depicted in Figure 7.2. All sensors read the parameters like climate temperature, humidity, and soil moisture. Then, the