
[Figure 7.1:](#chapter7.xhtml#b7fig7_1) Overview of the flow for generating attacks and designing defensive countermeasures discussed in this chapter.

**Major Contributions of the Chapter:**

*   **`Robustness analysis of SNNs`**: An in-depth methodology is designed to evaluate the robustness of SNNs and compare it to non-spiking DNNs. It investigates their robustness against random noises added to the inputs and against crafted adversarial examples.

*   **`NeuroAttack` methodology design**: It injects bit-flips in specific weight memory locations to fool SNNs and DNNs. The attack is triggered when a crafted adversarial pattern is provided in the input image.

*   **`Robust SNN designs by tuning their structural parameters`**: A systematic methodology is designed for investigating the SNN robustness. It explores the impact of SNNs’ structural parameters for designing robust SNNs.

*   **`R-SNN` methodology design**: It is an adversarial defense technique that employs noise filters for DVS to increase the SNNs’ robustness.

*   **`DVS-Attacks` design**: It is a set of adversarial attack methodologies that perturb DVS signals. It also contains specifically crafted attacks that fool SNNs in the presence of DVS noise filters.

## 7.1 Security Evaluation of Snns Vs. Dnns

SNNs present many advantages in terms of energy efficiency and biological plausibility compared to standard non-spiking DNNs. Prior works have demonstrated that DNNs are susceptible to adversarial attacks, i.e., minimal perturbations added to the input can lead to targeted or random misclassifications. In this section, we aim to investigate the security of SNNs. Toward this, we comparatively study the security vulnerabilities in DNNs and SNNs with respect to the adversarial noise. Afterward, we propose a novel black-box attack methodology. Without knowing the internal structure of the SNN, it employs a greedy heuristic to generate imperceptible and robust adversarial examples for the given SNN. To obtain a fair comparison, we conduct an in-depth evaluation of our methodology for a Spiking Deep Belief Network (SDBN) and a DNN with the same number of layers and neurons, for understanding the differences between SNNs and DNNs when subjected to adversarial examples. Our work opens new avenues of research toward the SNNs’ robustness, considering their similarities to the human brain's functionality.

### 7.1.1 System Overview

In this section, we aim to generate imperceptible and robust adversarial examples for SNNs under black-box settings. Prior works \[[10](#refbib.xhtml#refbib10)\] studied the vulnerabilities of SNNs under white-box settings, while we consider a black-box assumption, which makes the attacker stronger in a wide range of real-world environments. For a fair comparison during the evaluation, we apply these attacks to an SDBN and a DNN with the same number of layers and neurons. First, we analyze the vulnerability of SDBNs to random and adversarial noise, for identifying the similarities/differences w.r.t. DNNs. Our experiments demonstrate that when a random noise is applied to a given SDBN, its classification accuracy decreases for higher noise magnitude. Moreover, when our attack is applied to SDBNs, we notice that the output probabilities exhibit a different behavior than for the case of DNNs. While the adversarial example remains imperceptible, misclassification is not always achieved in the SDBNs.

In short, we make the following *novel contributions*:

*   We analyze the variation in the accuracy of an SDBN when random noise is added to the inputs.

*   We evaluate the improved generalization capability of the SDBN when adding random noise to the training images.

*   We develop an automated methodology to create imperceptible adversarial examples for DNNs and SNNs.

*   We apply our methodology for generating adversarial examples to an SDBN *(the first attack of this kind applied to SDBNs)* and a DNN and evaluate their imperceptibility and robustness.

### 7.1.2 Analysis: Applying Random Noise to SDBNs

#### 7.1.2.1 Spiking Deep Belief Networks

Deep Belief Networks (DBNs) \[[15](#refbib.xhtml#refbib15)\] are widely used multi-layer networks for classification tasks and have been implemented in many domains such as audio processing, visual processing, images and text recognition \[[15](#refbib.xhtml#refbib15)\]. DBNs are constructed by stacking pre-trained Restricted Boltzmann Machines (RBMs), which are energy-based models consisting of two layers of FC neurons. RBMs are typically trained with unsupervised learning algorithms to extract the information stored in the hidden neurons, and then a supervised approach is conducted to train an ML classifier based on these features \[[85](#refbib.xhtml#refbib85)\].

*Spiking DBNs (SDBNs) improve the energy efficiency and computation speed compared to DBNs*. Such behavior has already been observed in the work of \[[192](#refbib.xhtml#refbib192)\], which proposed a DBN model composed of 4 RBMs of 784 − 500 − 500 − 10 neurons, respectively. After its offline training, it is transformed into the event-based domain to increase the processing efficiency and computational power. The RBMs are trained with Persistent Contrastive Divergence (CD), an unsupervised learning rule that employs Gibbs sampling, a Markov-Chain Monte-Carlo algorithm that optimizes for fast parameter convergence, selectivity, and sparsity \[[229](#refbib.xhtml#refbib229)\]. Once every RBM is trained, their feature information is saved in the hidden neurons to use as input for the following layer. Afterward, a supervised learning algorithm \[[87](#refbib.xhtml#refbib87)\], based on the features coming from the unsupervised training, is implemented. The RBMs of this model use the *Siegert* function \[[250](#refbib.xhtml#refbib250)\] in their neurons. It allows having a good approximation of the firing rate of LIF neurons used for CD training. Hence, the neurons of an SDBN generate Poisson spike trains, according to the *Siegert* formula.

This represents a significant advantage in terms of speed and power consumption compared to the classical DBNs based on a discrete-time model \[[192](#refbib.xhtml#refbib192)\]. *Since there has been no prior work on studying the security vulnerabilities of such SDBNs, we aim at investigating these aspects in a black-box setting, which is important for their real-world applications in safety-critical systems*.

#### 7.1.2.2 Experimental Setup

As a case study, we consider an SDBN \[[192](#refbib.xhtml#refbib192)\] composed of 4 FC layers of 784 − 500 − 500 − 10 neurons, respectively. We implement this SDBN in Matlab for analyzing the MNIST database. Each pixel intensity is encoded as a value in the range between 0 and 255. The input data are scaled to the range \[0,0.2\] to directly convert intensities into spikes. In our experiments, the pixel intensities are represented as the probability that a spike occurs.

#### 7.1.2.3 Understanding the Impact of Input Random Noise on the Accuracy of an SDBN

We evaluate the accuracy of the SDBN for different noise magnitudes applied to three different sets of images:

*   to all the training images.

*   to all the test images.

*   to both the training and test images.

To test the SDBN's vulnerability, we apply two different types of noises: *normally distributed* and *uniformly-distributed* random noise.
