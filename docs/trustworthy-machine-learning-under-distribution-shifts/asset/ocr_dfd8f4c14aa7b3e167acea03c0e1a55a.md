# Effect of Benign and Malign OOD Data

![](bbox=[0.221, 0.173, 0.778, 0.43])

Figure 2.5. Effect of adding benign and malign OOD data into training.

neither of the style and content features can be identified by the class predictor and domain predictor, respectively. Therefore, we can reasonably conclude that our disentanglement between content and style is effectively achieved.

**Effect of Adding Benign and Malign OOD Data into Training:** To give a illustrative comparison of adding benign OOD data and malign OOD data into training, we conduct experiments on the open-set SSL setting and separately augmenting OOD data and malign OOD data to compare their effects. Moreover, we conduct plain training as a baseline result which do not use either augmentations. The results are shown in Figure 2.5. We can see that after adding augmented data, the effect of malign OOD data causes performance degradation. On the contrary, benign OOD data can further improve the learning result compared to the plain training baseline. Which again shows that preserving content and augmenting style is beneficial, and eliminating content is harmful for generalization.

**Analysis of OOD Score** To show the effectiveness of identifying malign OOD data from benign OOD data, we test the performance of HOOD on three applications to observe the OOD scores of benign OOD data and malign OOD data and show the averaged OOD scores