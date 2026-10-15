We contrive the originality of the proposed framework with its ability to record and process the NCS signal with an affordable, reliable, and efficiently designed electronic platform incorporating a microcontroller-based decision-making module capable of providing a real-time decision on nerve diagnosis. While doing so, we have stressed more on the signal processing stage incorporating filters for proper acquisition of the nerve signals with minimal noise interference. To be precise, we measure the signal parameters from healthy subjects to validate the performance of the designed framework to prove its efficacy while using it in a real-time scenario. In particular, the proposed framework is capable of providing point-of-care diagnosis and can be used by any layman for self-assessment of the underlying median nerve.

# 15.2 FRAMEWORK

Figure 15.2 shows the framework of the proposed design setup, which comprises (a) a neurostimulator for nerve stimulation (Block A), (b) a signal conditioning circuit for signal amplification and processing (Block B), (c) an optimal neural network obtained from a pre-diagnosed dataset which is to be embedded in μC for instigating decision-making capability for disease diagnosis, and (d) a μC-based nerve parameter estimation and decision module. In the following sections, a detailed elaboration of each module of the proposed framework is provided.

# 15.2.1 Neurostimulator Module

Diagnosis of a nerve requires proper stimulation of the underlying nerve so that significant features can be extracted to ensure the nerves’ normal functioning. The voltage-controlled neurostimulator (VCN) acts as a stimulating platform for obtaining physiological nerve impulses from the diagnostic nerve site of the patients with the use of silver-silver chloride (Ag-AgCl) surface-disc electrodes. The VCN aims to

![](bbox=[0.1, 0.75, 0.9, 0.88])

FIGURE 15.2 Block diagram of the proposed design setup. Block A and Block B represent VCN and signal conditioning modules, respectively. The display panel indicates the estimated NCS parameters and the diagnosis decision for a particular subject examined. Here, (Nor) represents the normal nerve status under examination.