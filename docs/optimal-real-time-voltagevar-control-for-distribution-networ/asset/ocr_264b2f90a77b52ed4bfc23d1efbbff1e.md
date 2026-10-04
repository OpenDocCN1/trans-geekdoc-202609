# Distribution Network

![](bbox=[0.105, 0.091, 0.703, 0.175])

PV and Load historical data

State s,

![](bbox=[0.105, 0.135, 0.703, 0.175])

# Optimal Reactive Power $Q^*$

# Optimized Q-V Droop Control Parameters

![](bbox=[0.105, 0.241, 0.703, 0.355])

Input

![](bbox=[0.745, 0.241, 0.893, 0.355])

Output

Policy model /

Fig. 1. The distributed ORT-VVC scheme.

centralized and distributed control has the ability in global optimum searching, but they deny the real-time response speed according to the computation and communication buffers [16–18]. Model-based control methods often require precise and comprehensive distribution network parameters, which may be difficult to for low voltage distribution network [19,20].

is based on the dynamic characteristic of reactive power and node voltage. In other words, it follows the physical law of power system operation. As for the VVC of the distribution network, the model-based method can be realized with renewable VVC droop control.

The method proposed in this paper is different from the model-based method which has been used in VVC of distribution network and attracts lots of attention [27–21]. The reinforcement learning (DRL) is a data-driven method, that is based on the Markov Game. The DRL generator is realized through online training and combines with well-trained neural networks (DNNs). The decisions can be determined in milliseconds. In other words, the DRL can act in real-time with high optimum searching. Thus, the DRL method can optimize the operation of distribution network without variation. In fact, a multi-agent reinforcement learning (MADRL) method is proposed to optimize the static variance $Q$ reactive power for managing the bus loads, which can be decentralized and executed independently. Ref [24]

In this paper, the multi-agent reinforcement learning (MADRL) method is implemented as a model and control. The droop parameters are optimized by the MADRL, realizing the optimal real-time VVC (ORT-VVC) for distribution network. The main contributions are as follows:

+   - An ORT-VVC method is proposed to mitigate voltage fluctuation and reduce power losses. The ORT-VVC is implemented via a model and control. The PAC-DRL method is implemented together with the Q-V droop control, the relationship between voltage and reactive power with the optimum searching and online ability of MADRL for distribution network with high penetration of RES.
- A novelty penalty function is proposed to improve convergence rate during training. The particular define penalty function is replaced by a linear penalty function which equals 0 when the training time of one episode is finished. With this method, the episode occurs more frequently and the convergence rate will be reduced, to

the algorithm used for voltage control, which the control problem is formulated as a Markov game and the decentralized multi-agent gradient policy (MADPG) algorithm is employed. In Ref [25], a voltage reactive power control algorithm is proposed to control VVC, SVC and energy support system (ESS) coordination with decentralized execution framework. Ref [26] provides a data-driven multi-agent policy and the security-constrained optimal power flow model, in which the constrained DRL training is transformed into nonconstrained problem with a penalty function. In Ref [27], a data-driven reactive voltage control method is proposed with addressing the spatial and temporal characteristics of RES and loads, the data-VVC model is established as a partially observable Markov Game and solved with a modified MADPG algorithm. However, the DRL methods rely on data, and it may have the uncertain scenarios across distribution network operation. The Q-V droop control has high operation stability, which results from that

The reminder of the paper is organized as follows. Section 2 it the ORT-VVC scheme which is implemented in a distributed partition. In section 3, the Q-V droop model and the ORT-VVC model are described. In section 4, the ORT-VVC model is formulated to a DC-DRL problem based on a partially observable Markov process (POMG) and the solution process based on MADPG algorithm. Section 5 gives the case study drawn in section.