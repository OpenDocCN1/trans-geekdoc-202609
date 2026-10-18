
In this section, we outline the adversarial attack types and introduce in detail the adversarial attack techniques in some classification methods. Three criteria are used to classify the attack methods: (1) Using the model access to classify different attacks refers to the knowledge of the attacked model at the time of executing the attack. (2) Using the target refers to the attacker’s goal, such as enforcing incorrect predictions or target specific outcomes. (3) Using the DL application domain refers to the different DL realistic applications in which the adversarial attack is applied. Figure 3.1 shows the different categories.

![](img/efffc69cb8cda75bcf341884e3396898_101_0.png)

FIGURE 3.1 Categories of adversarial attack methods.

A targeted attack means that the DL model may mistakenly classify the image being attacked as the adversary’s desired class (then we say that the attack is successful). In general, the target category in a targeted attack can be specified as the category with the lowest probability of classification by the defense model at the input of the original image. This is the most difficult case to defend against. The target category can also be specified as the category whose classification probability is second only to the probability of the correct category at the input of the original image to the defense model, which is the easiest case to defend. Finally, the target category can also be specified randomly, which is between the two previous.

The input image so that the loss value is greater than the value when the image before the modification passes through the classification network. Thus the probability that the model predicts the label correctly becomes smaller. On one hand, FGSM calculates the gradient based on the input image. On the other hand, when the model updates the input image, the gradient is added instead of subtracted. This is just the opposite of the common classification model for updating parameters. The FGSM algorithm is simple and effective, and it plays a major role in the field of image attacks. Many subsequent studies are based on this algorithm.

Moosavi-Dezfooli et al. [11] proposed the DeepFool concept to obtain superior results by calculating the minimum necessary perturbation and applying it to the method of adversarial sample construction, by using a method that limits the size of the perturbation to the L2 parametrization. Notably, this algorithm seeks the current point in the high-dimensional space that is closest to the decision boundary of all nonreal classes. And as a result, this class will be the postattack label.

L2 is one of the evaluation indices. The evaluation index of the current attack algorithm mainly uses the Lp distance (also generally called Lp parametric) with the following formula:

where vi denotes the pixel value modification magnitude of pixel point i, and n denotes the number of pixel points. v is generally obtained by comparing the image to the original image, and it denotes the difference between the two images (also called the perturbation).

The distance L0 is calculated as the number of different pixels between the attacked image and the original image, that is, the number of pixel points modified in the original image. The L0 parametric number itself also represents the number of nonzero elements, while for perturbation, a nonzero means that the pixel point is modified. It can be seen that this evaluation metric does not involve the magnitude of the perturbation, but rather it evaluates at the level of the number of perturbations.

The distance L2 is calculated as the Euclidean distance of the different pixel values between the attacked image and the original image.

The L∞ distance is calculated as the absolute value of the largest pixel value difference between the attacked image and the original image. This means that we only care about the value of the largest perturbation

magnitude and that, as long as the pixel value is modified within this limit, then it is valid.

### JSMA-based Method

The Jacobian saliency map (JSMA) is an attack sample generation method for acyclic feed-forward DNN networks. It limits the number of perturbed pixel points in the input image. While gradient-based and GAN-based adversarial attacks are based on global perturbations and generate adversarial samples that can be perceived by the human eye, JSMA generates adversarial samples based on point perturbations. Thus the resulting adversarial perturbations are relatively small. The adversarial saliency map (ASP) in [12] is based on the forward derivation of neural networks for targeted attacks under white boxes, and it indicates which input features in clean samples can be disturbed to achieve the attack effect.

One of the drawbacks of JSMA is that only targeted attacks can be performed, no untargeted attacks can be implemented, and the direction of the attack needs to be formulated (i.e., whether to increase or decrease pixels). In the MJSMA paper [13], the authors proposed two variants of JSMA: one without specifying a target class and the other without specifying the direction of the attack (i.e., increasing or decreasing pixels).

In [14], the authors proposed two improved versions of JSMA: the MJSMA means-weighted JSMA (WJSMA) and the Taylor JSMA (TJSMA). WJSMA is a simple weighting applied to the adversarial saliency map (ASP) by the output probability, and TJSMA also uses the ASP concept while additionally penalizing the input features. Both attacks are more effective than JSMA. The authors showed that TJSMA outperforms WJSMA in the case of targeted attacks and that WJSMA outperforms TJSMA in the case of untargeted attacks.

In addition to these two main methods of white-box attacks, there are other attack methods such as C&W-based, direction-based, and attention-based. The white-box attack is a common, basic adversarial attack technology, and we discuss it more later.

## 3.2.2 Black-box Attacks

In black-box adversarial attacks, the attacker does not have complete access to the policy network. The research just referenced classifies black-box attacks into two main groups: (1) The adversary has access to the training environment and has the knowledge of the training algorithm and hyperparameters. It knows the neural network architecture of the target policy network but not its random initialization. (2) For this case, the adversary has no knowledge of the training algorithm or hyperparameters. This type of attack often relies on heuristics to generate adversarial examples. In many real-world applications, the details of the DNN are a black box to the attacker.

### Mobility-based Approach

It is shown that the adversarial samples generated against the target model have transferability; i.e., the adversarial samples generated against the target model will likely be effective against other models with different structures. Therefore, in a black-box scenario, an attacker can train the model on the same dataset or the dataset with similar distribution as the attack target and thereby generates the adversarial samples against the trained model. Then it uses transferability to deceive the black-box target model. If the attacker does not have access to the training data, the attacker can use the target model to label the synthetic data based on the idea of model distillation and then use the synthesized data to train an alternative model to approximate the target black-box model. Eventually it can use the white-box attack method to generate adversarial samples against the alternative model and use the generated adversarial samples to perform a black-box migration attack on the target model [15]. However, while this approach has been shown to be applicable to datasets with low intraclass variability (e.g., MNIST), no study has yet demonstrated its extension to more complex datasets such as CIFAR or ImageNet. Subsequently, Papernot et al. [16] improved the training efficiency of alternative models by using reservoir sampling, which can further optimize the alternative model-based attack methods in terms of diversity, mobility, and noise size.

### Gradient Estimation-based Approach
