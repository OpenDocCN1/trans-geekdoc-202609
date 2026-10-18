all other images that do not contain numbers are adversarial samples that can lead to misclassification because the classifier of the target DL model has to classify that image. Input samples belonging to this class will be removed directly. (2) The adversarial sample is very close to the popular boundary for that task. If the generalization of that classification method is not good at that point, misclassification can also occur. Efforts are made to find a sample that is close to or just above the manifold for that task and then hand it over to the classifier. This is the second defense method conceived by the authors. [Figure 9.3](#figure-9-3) demonstrates the workflow of MagNet.

![](bbox=[0.117, 0.348, 0.826, 0.55])

**FIGURE 9.3** Workflow of MagNet.

Generally, the generation of functions to detect adversarial samples requires the knowledge of the specific adversarial sample generation process and therefore cannot generalize to other types of adversarial samples. Thus such a method can be easily bypassed by slightly modified attacks. In this paper, the authors proposed two new methods for detecting adversarial samples: reconstruction error-based detection and probabilistic divergence-based detection methods.

+   1. *Reconstruction error-based detection:* For the training set of all normal samples, the authors train an autoencoder such that the loss function of this training set is minimized, and its loss function is defined as
+   
+   where $X_{\mathrm{train}}$ is the normal samples in training set, and $E(x)$ is the reconstruction error. The authors argue that, if the sample to be tested