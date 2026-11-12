and Verguts model with elements that have direct physical connection and, therefore, more realistic interpretation.

In another experiment, Ruciński (2014) presented a new cognitive developmental robotics model to simulate aspects of the earlier work on gesture in counting by Alibali and DiRusso (1999), and indeed experimental results showed that pointing gestures significantly improved the counting accuracy of the humanoid robot iCub. The architecture was a recurrent neural network of the Elman type, with two input layers: one for the items to count—that is, a binary vector—and another for the proprioceptive information—that is, the arm and hand encoder values. The model was trained via backpropagation through time. Statistical analysis of the results showed adherence to the experimental data of Alibali and DiRusso.

Recently, Di Nuovo et al. conducted several experiments (De La Cruz et al. 2014; Di Nuovo, De La Cruz, and Cangelosi 2014; Di Nuovo et al. 2014) with the iCub humanoid robot to explore whether the association of finger counting with number words and/or visual digits could serve to bootstrap numerical cognition in a cognitive robot. The models (e.g., figure 22.2) were based on three RNNs of the Elman type, which were trained separately and then merged to learn the classification of the three inputs: finger counting (motor), digit recognition (visual), and number words (auditory)—that is, the triple-code

![](bbox=[0.13, 0.425, 0.85, 0.855])

Figure 22.2
A schematic representation of the deep architecture for number cognition showing an integration of the models
proposed by the several investigations of Di Nuovo et al. (2014).