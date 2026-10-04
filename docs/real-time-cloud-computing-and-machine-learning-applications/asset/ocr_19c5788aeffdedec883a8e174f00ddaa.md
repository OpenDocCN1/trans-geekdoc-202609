# Server and Servlet Architectures for a Cloud-Based Real-Time . 463

# Table 5.13. Example of streaming data recorded for regression analytics

| Key | Download Speed | Upload Speed | Packets Received | Packets Sent |
| 1 | 1063 | 16 | 792 | 298 |
| 2 | 1595 | 25 | 1512 | 416 |
| 3 | 1471 | 22 | 1094 | 401 |
| 4 | 1691 | 29 | 1246 | 480 |
| 5 | 1618 | 27 | 1204 | 468 |
| 6 | 1660 | 26 | 1239 | 474 |

# 5.1.12.1. Using the Sliding Window Method

The regression algorithms in this chapter revolve around the use of the sliding window method, also known as the rolling window. It is efficient for short time series forecasting which is ideal in this case since the software takes as input particular prediction time value which is input by the user. Consider the following scenario, which consists of only "Packets Received" values taken from the "laptopcloudparameters" dataset with the following parameters:

+   * Window Size = 5
* Prediction Time = 2

The sliding windows are constructed per Figure 5.16.

| (Independent) | (Dependent) | (Independent) | Predicting the number of packets received (y) |
| Download Speed | Packets Received | Upload Speed | |
| n: 1 | x:1063.0 | y: 792.0 | z: 16.0 | Actual value for row 7 is: 1210.0 |
| n: 2 | x:1595.0 | y: 1512.0 | z: 25.0 | Predicted value for row 7 is: 1163.6 |
| n: 3 | x:1471.0 | y: 1216.0 | z: 22.0 | |
| n: 4 | x:1691.0 | y: 1216.0 | z: 29.0 | |
| n: 5 | x:1618.0 | y: 1204.0 | z: 27.0 | |
| n: 2 | x:1595.0 | y: 1512.0 | z: 25.0 | Actual value for row 8 is: 1179.0 |
| n: 3 | x:1471.0 | y: 1216.0 | z: 22.0 | Predicted value for row 8 is: 1253.0 |
| n: 4 | x:1691.0 | y: 1216.0 | z: 29.0 | |
| n: 5 | x:1618.0 | y: 1204.0 | z: 27.0 | |
| n: 6 | x:1660.0 | y: 1239.0 | z: 26.0 | |
| n: 3 | x:1471.0 | y: 1094.0 | z: 22.0 | Actual value for row 9 is: 1189.0 |
| n: 4 | x:1691.0 | y: 1216.0 | z: 29.0 | Predicted value for row 9 is: 1192.2 |
| n: 5 | x:1618.0 | y: 1204.0 | z: 27.0 | |
| n: 6 | x:1660.0 | y: 1239.0 | z: 26.0 | |
| n: 7 | x:1639.0 | y: 1210.0 | z: 30.0 | |

Figure 5.15. General concept is better explained through Figure 5.17 which shows that the first five independent variables from both the download speed and upload speed columns are input into the algorithm while setting the (window size + prediction time) value of the prediction as the variable. The sliding window is then