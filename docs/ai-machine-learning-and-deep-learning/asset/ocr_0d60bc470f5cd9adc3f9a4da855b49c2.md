Second, we simplify the dataset of network traffic for machine learning. Since the IoTSE has a static and particular task profile, the packet sending rate of all kinds of applications should be in a relatively stable range. Thus we can efficiently detect suspicious packets if the packet sending rate is out of the range in profile. We also reduce the size of dataset in order to reduce the cost of time and resources in training process.

# 16.7 FINAL REMARKS

This chapter has investigated three attacking scenes for interest flooding attacks (IFA) in NDN-based IoTSE. Using ns3 as the evaluation platform, we have designed two IFA scenarios with a nonexistent interest flooding attack strategy in small- and large-scale simulations, utilizing different link configurations. We first show the severity of the damage caused by IFA. Then, based on the collected dataset of the successful IFA, we process the dataset and reduce it into only the out-request and outer network interface in the PIT-related dataset. Finally, we have obtained a dataset with two features: packets and the label of attack. We compared the eight ML models to carry out attack detection and concluded that most ML models could effectively detect this kind of attack in a packet-rate-based dataset. However, we find that the linear-based ML model obtains worse detection accuracy when the dataset volume increases tremendously.

# ACKNOWLEDGMENT

This material is based upon work supported by the Air Force Office of Scientific Research under award number FA9550-20-1-0418. Any opinions, findings, and conclusions or recommendations expressed in this material are those of the author(s) and do not necessarily reflect the views of the United States Air Force.

# REFERENCES