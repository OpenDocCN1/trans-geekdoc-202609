
# Packets matching the null route will be dropped

The null route creates a block-hole, which is a kernel routing table entry that leads to nowhere.

## Figure 6. LFA Model

![Figure978-1-6684-3448-2.ch003.f06](i/ch003.f06.png)

*(Rasool, R. U., et al. (2019))*

MLP is characterized by an input, an output, and one or more hidden layers that are interlinked with each other. On the contrary, there is no connection between the nodes in the same layer, and there are no bridging connections either.

### Output Layer

Output layer is the number of possible classes in the dataset that is desired to predict and is denoted by `y`. Here it is equal to two, Legitimate and Flooding.

### Hidden Layer

Hidden layers correspond to the number of intermediate connections that are used in the experiment, and by default, this number is selected as 1. The number of hidden layers depends on the mean value of the input and output layers. When data is linearly separable, the number of hidden layers to use is 0. These layers actually transform the single layer perception into multilayer, which is denoted by `h: (h1, h2, . . ., hn)`. Where hidden layer can comprise 1 to a maximum number of `n` layers.

### Backward Propagation

It is used to continuously update the weights of the layers so as to minimize the difference between the generated output and the expected output. Using this, the gradient descent can be calculated, which is further used to calculate the weights and to train the MLP model.

In Scaranti, G. F., Carvalho, L. F., Barbon, S., & Proenca, M.L. (2020), Artificial Immune System and Fuzzy Logic to Detect Flooding Attacks is proposed (Figure 7).

AIS-IDS is a biological inspired IDS. It uses fuzzy logic to automate the detection and mitigation of network anomalies. The proposal is placed on the control plane and has three modules with specific functions. The three modules are responsible for collecting flows, detection and mitigation.

Using the normal traffic behaviour, the anomaly traffic flow can be recognized. Fuzzy Interference System is used to solve the uncertainty in detecting the anomaly.

The mitigation module will recognize the suspicious IP addresses and ports to determine the mitigation strategies to mitigate/block the attack.

## Figure 7. AIS-DIS

![Figure978-1-6684-3448-2.ch003.f07](i/ch003.f07.png)

*(Scaranti, G. F., Carvalho, L. F., Barbon, S., & Proenca, M. L. (2020))*

For evaluating the efficiency of AIS-DIS, this model is compared with `KNN`, `LOF` (Local Outlier Factor) and `Naive Bayes` for the simulated DDoS.

AIS-DIS has three modules in the SDN controller: Flow Collector, AIS Detection and Mitigation. The first module periodically gets the IP flows from the data plane using the `OpenFlow (OF)` protocol. This data is further processed and sent to the subsequent module, i.e. AIS Detection. This module categorizes the network behaviour into normal or abnormal. If the behaviour is found to be abnormal, the Mitigation module blocks the traffic by creating forwarding rules.

## Figure 8. Flow collector module

![Figure978-1-6684-3448-2.ch003.f08](i/ch003.f08.png)

*(Scaranti, G. F., Carvalho, L. F., Barbon, S., & Proenca, M. L. (2020))*

The three modules are described below:

*   **A. Flow Collector Module (Figure 8)** collects the data which is needed by the AIS Detection module (Figure 9). `OpenFlow` protocol is used. Every instant, many flows are created and expired in SDN. If the collection of flows information is more frequent, anomaly detection becomes more accurate and makes it possible to take faster action to mitigate the attack. But there is a disadvantage in the periodic data collection, which is the volume of the flow which is being analyzed. Here creating an IDS that reacts accurately in real-time when detecting threats is a challenging issue.

*   **B. AIS** is inspired by biological immune systems. One of the best know algorithms for AIS is the Negative Selection Algorithm (`NSA`). It simulates the recognition of biological antibody to the job of self and non-self-classification. `NSA` is a computational model to generate immune detectors (Figure 10). This approach gives the advantage to detect threats without training the model with abnormal examples in the datasets. Each detector is complete only when its features have similarity values greater than the minimum similarity with the training dataset. This new detector is added to the detectors' collection, and the generation process terminates when this collection reaches `n` detectors. This is followed by classification.

*   **C. Mitigation Module (Figure 11)** gets all the flow of anomalous traffic which was routed by the AIS Detection module (Figure 9). Then the mitigation module applies packet dropping policies to mitigate the detected attack. Depending on the types of anomalies: DDoS or PortScan attack, there are two types of mitigation strategies.

## Figure 9. AIS detection module

![Figure978-1-6684-3448-2.ch003.f09](i/ch003.f09.png)

*(Scaranti, G. F., Carvalho, L. F., Barbon, S., & Proenca, M. L. (2020))*

## Figure 10. Pseudocode for detectors generation

![Figure978-1-6684-3448-2.ch003.f10](i/ch003.f10.png)

*(Scaranti, G. F., Carvalho, L. F., Barbon, S., & Proenca, M. L. (2020))*

The results of the experiments concluded AIS-IDS to have F-measure over 99.9%, showing that the IDS proposed by the authors is reliable for protecting networks. On testing with public dataset, f-measure was found to be over 92%. The mitigation module was also able to drop the anomalous packets and block the attacks. Hence AIS-IDS has proved to be effective for detecting and mitigating Flooding Attacks in SDN.

## Figure 11. Pseudocode for mitigation module

![Figure978-1-6684-3448-2.ch003.f11](i/ch003.f11.png)

*(Scaranti, G. F., Carvalho, L. F., Barbon, S., & Proenca, M. L. (2020))*

# DDoS Attack

DDoS attack involves a huge number of packets being sent to the target. If the attack is successful, the controller will be disconnected from the rest of the network. Separation of controller results in losing its centralized control. This single point of failure can be dealt with architecture proposed by Tan, L., et al. (2020).

The architecture proposed by Tan, L., et al. (2020) consists of detection and defence mechanism. It comprises four divisions: A) DDoS Detection Trigger Mechanism on Programmable Data Plane, B) Flow feature Extraction, C) DDoS Detection Algorithm, and D) DDoS Defence Mechanism. These four divisions are described below:

*   **A) DDoS Detection Trigger Mechanism on Programmable Plane:** The method used for DDoS attack detection uses fixed time intervals to detect network traffic. The efficiency of DDoS attack detection and performance of the controller is largely affected by the detection cycle periods. If the time interval is set to be too large, then the response time will be too high. This also increases the workload on the controller and the switches. And if the time interval is too small, then the attack detection will be started by the controller frequently, which increases the workload on the controller.

    The solution to the above problem of periodic triggering of DDoS attack detection in SDN environment is to introduce a detection trigger mechanism which determines the start time of the DDoS attack detection through the trigger mechanism. This method is successful in breaking the problem of regular trigger detection method.

    The detection trigger mechanism is deployed on the data plane and is implemented by counting `packet_in` messages on the switch. When the DDoS attack is initiated, there will be a huge spike in the number of `packet_in` messages, this abnormal increase in `packet_in` is used as a sign of a DDoS attack being initiated (Tan, L., et al. (2020)).
