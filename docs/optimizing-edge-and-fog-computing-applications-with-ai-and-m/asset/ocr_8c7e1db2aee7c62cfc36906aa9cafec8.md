![](bbox=[0.118, 0.105, 0.882, 0.375])

Figure 5.8 General traffic.

of "other" guarantees a more elaborate assessment of the system's performance in detecting and tracking events of any kind except malicious ones.

# 5.6.5 Discussion

The above findings are critical in understanding the valuable insights which the hybrid detection system has to offer with the integration of SIEM, IDS and ML models in identifying the DDoS attack. This discussion will critically evaluate these results, highlighting the system's strengths and weaknesses in comparison with existing research and providing suggestions for future growth.

The system's performance, which is measured through detection time analysis, has an average detection time of 0.514 ms and a maximum of 0.999 ms, indicating its suitability in real-world applications. This shows the efficiency of the system in handling and processing the events as swiftly as required in a dynamic environment. However, there are certain spikes in the detection time across some events, which possibly indicate occasional computational delays that might be due to resource contention or overheads in data preprocessing. For maintaining consistent real-time performance there is a space for further optimisation in terms of resource allocation and multi-threading capabilities. Both the classification reports for the ensemble learning models demonstrate high accuracy in terms of detection, with nearly perfect detection classification for the DDoS category. But it has been noticed that XGBoost slightly outperforms RF in terms of recall and precision as XGBoost is known to work well with imbalanced datasets. The support values in the classification report reveal the number of samples in each category– benign and attack– highlighting the effectiveness of the system during high traffic during DDoS simulations. Moreover,