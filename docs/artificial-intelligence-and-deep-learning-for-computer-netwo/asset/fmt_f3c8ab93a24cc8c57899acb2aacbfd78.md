
## 3.7.2 Evaluation Metric

## 3.7.3 Experimental Results

## 3.8 Conclusion and Future Work

## References

## 3.1 Introduction

In the last few years, SDN has defined an architectural paradigm that enables network-wide automation. The SDN market is developing quickly and, according to market reports \[[1](#ch03.xhtml#ref3_1)\], it is still believed to be in its early stages. The popularity of SDN stems from the fact that it allows automated provisioning, network virtualization, and efficient management by separating the forwarding and control planes. The network intelligence is centralized through programmable SDN controllers. Although the control plane is centralized, a single physical controller can lead to reliability, performance, and robustness issues.

The control plane in practice is logically centralized, which is achieved using multiple, physically distributed controllers. Each controller has a set of switches under its control, and it controls a specific portion of the network, called the SDN domain. The SDN domains periodically exchange messages to allow synchronization. However, these SDN domains cannot be static. Organizations need continuous network monitoring and performance optimization to support the highly dynamic network traffic. Consequently, there is a need for the network to evolve by continuously changing the boundaries of the SDN domains. A static SDN network can lead to controller load imbalance.

The research community has considered the application of artificial intelligence to optimize the network configuration automatically. The employment of machine learning (ML) techniques to operate the network has led to a new construct called the knowledge plane \[[2](#ch03.xhtml#ref3_2)\]. The logical centralization of the control plane facilitates ML techniques that were otherwise not possible on traditional networks that are inherently distributed. The knowledge plane captures the network traffic, uses analytics, and makes decisions on behalf of the network operator. The closed-loop feedback provided by the knowledge plane is fundamental to achieve the desired performance level.

In this chapter, we propose a reinforcement learning–based switch migration to handle the load imbalance among the controllers. The framework aims to discover which actions will lead to an optimal network configuration. The action is to move a switch from one controller to another. For each such act, a reward is associated. Ultimately, the algorithm will learn the set of switch migrations (action updates), leading to the target of a balanced network.

## 3.2 Literature Survey

The traffic on real networks varies spatially as well as temporally. The temporal variations occur due to traffic conditions depending upon the hour of the day. Spatial traffic variations happen because of the flows produced by applications associated with various switches. Due to these variations, the accumulated traffic at a controller may exceed its capacity. We may need to migrate switches from overloaded controllers to underloaded ones to deal with this load imbalance. However, unlike static controller to switch mapping, the migrations need to be on the fly. An additional issue that needs to be addressed is the disruption of ongoing flows.

Dixit et al. \[[3](#ch03.xhtml#ref3_3),[4](#ch03.xhtml#ref3_4)\] proposed to address the issue of load balancing by using the equal controller mode (specified in OpenFlow v1.2) while transitioning a controller from master to slave. In addition, they suggest resizing the controller pool depending on whether the controller load exceeds or falls below an upper or lower threshold.

Wang et al. \[[5](#ch03.xhtml#ref3_5)\] proposed a framework called switch migration-based decision-making (SMDM), where they compute load diversity, a ratio of controller loads. Switch migration takes place in case the load diversity between two controllers exceeds a certain threshold. The switches selected for migration are those with less load and higher efficiency.

Hu et al. \[[6](#ch03.xhtml#ref3_6)\] proposed efficiency-aware switch migration (EASM), where they measure the degree of load balancing using the normalized load variance of the controller load. If the load difference matrix exceeds a threshold, the controller load is presumed to be unbalanced. The threshold is a function of the difference between the maximum and minimum controller load.

Filali et al. \[[7](#ch03.xhtml#ref3_7)\] use the ARIMA time series model to predict a switch's load. The forecasting allows finding the time step at which a controller will become overloaded and accordingly schedule a switch migration in advance. The authors use a predetermined threshold to identify overloaded controllers.

The work by Zhou et al. \[[8](#ch03.xhtml#ref3_8)\] is among those few who consider the problem of load oscillation due to inappropriate switch migration. Load oscillation occurs when underloaded controllers, which are used to offload the traffic load of overloaded controllers, become rapidly overloaded themselves. As stated by the authors, the problem is due to the target switches not being selected based on the overall network status.

Ul Haque et al. \[[9](#ch03.xhtml#ref3_9)\] address the variance in the controller load by employing a controller module, which is a set of controllers. Their method estimates the number of flows that the switches will produce on a regular interval and accordingly activates the appropriate number of controllers.

Chen et al. \[[10](#ch03.xhtml#ref3_10)\] use a game-theoretic method to solve the problem of controller load balancing. The underloaded controllers are modelled as players who compete for switches from overloaded controllers. The payoffs are determined when an underloaded controller is selected as the master controller of a victim switch.

After this survey, we found that a system became unbalanced due to a change in the network traffic characteristics. If we learn the behavior of network traffic, then we can make the right decision. Several papers use a threshold to affect the switch migration, but they do not outline how the threshold can be determined. Our proposed work applies reinforcement learning to present a framework that learns the network traffic characteristics. It can take an optimal decision for choosing the underloaded controller that load balance the system.

## 3.3 Load Balancing in SDN

In a distributed SDN controller architecture, a forwarding device such as an SDN switch is associated with one of the controllers. The most common and crucial message exchange between a switch and a controller is a flow-request message and response. The communication between forwarding devices and a controller happen through the southbound API. OpenFlow is a well-known example of a southbound API. When a forwarding device receives a new flow, it sends a flow-request message to its mapped controller. On processing the request, the controller sends packet handling rules to the switches.

Therefore, the load on a controller is a function of the number of flow-request messages sent by the switches. The controller-switch association can be static or dynamic. In static association, switches direct flow requests to controllers based on pre-installed packet handling rules by the controllers. The main drawback of the static assignment strategy is that it cannot adapt to spatial and temporal variation in the network traffic.
