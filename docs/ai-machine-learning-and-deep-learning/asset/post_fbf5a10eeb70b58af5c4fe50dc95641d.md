
Since the adversary in indirect collaborative learning can only manipulate its own local dataset and cannot observe other users’ data, the poisoned data only influences the global model indirectly. To understand the influences of indirect CDL, Shen et al. [10] ran the privacy-preserving deep learning (PPDL) system proposed by Shorkri et al. The users of this system compute DL parameters from local data and only upload the parameters as features to the server.

In this section, Shen et al. [10] assume that the number of attackers, denoted as f, is less than the number of users, . The adversary uses a targeted poisoning attack to target specific training outputs. Also, the attackers can collude to mislead the global model. The server is honest but curious. It honestly processes the uploaded data but is curious about user information and may infer user identification. But the learning model is privacy preserving: The server cannot learn user information from the uploaded data. And the attacks do not aim to break the privacy protection but only disturb the accuracy of the global model.

## Targeted Poisoning Attacks

Attackers can poison the training dataset before the training phase or during the training phase. Section 4.3 discusses the latter case. The poisoning attack has two types:
- (1) random attacks that reduce the model’s accuracy;
- (2) targeted attacks that are more objective.
The targeted attack’s goal is to misclassify a specific input (e.g., a spam email); the model classifies it as a target value (e.g., a benign email).

### 4.3.3 AUROR Defense

Shen et al. [10] proposed a defense scheme against a poisoning attack for indirect collaborative learning: AUROR. To identify the poisoned data, the server should distinguish malicious attackers from honest users and exclude the masked features submitted by attackers when training the global model. AUROR has a rule-of-thumb assumption to detect the adversary: The adversary is the minority. Suppose the distribution of original data is referred to as . The distribution of the masked feature should be close to within statistical error bounds. The poisoning attack can change the distribution of specific masked features, referred to as *indicative features*. Thus during the poisoning attack scenario, indicative features from honest users have distribution patterns that are distinct from malicious users. AUROR also assumes that the number of adversaries is inside the range , where is the lower bound on the number of adversaries that AUROR can detect. This parameter varies with the type of dataset, so that it should be determined for each dataset. After preprocessing masked features, AUROR finds the indicative features and classifies the input into two groups.

Figure 4.3 shows the detailed steps to distinguish attackers in AUROR. AUROR is applied to the training data before the global model’s testing phase. It takes the masked features as the input and analyzes the distribution of these features to identify the indicative features. The key challenge is to find the appropriate indicative feature that can distinguish malicious users from benign users. The indicative feature also varies based on the type of dataset. To decide whether a particular feature is indicative or not, AUROR groups the features into different clusters. If the distance between the centers of two clusters is larger than a predefined threshold , then AUROR assumes this feature is indicative. The value of is related to the original distribution of the training dataset.

![](img/efffc69cb8cda75bcf341884e3396898_129_0.png)

FIGURE 4.3 Workflow of AUROR.

Then AUROR detects suspicious users if their indicative feature’s distribution is different from that of the majority. The cluster with the majority of users is marked as honest, whereas the minority cluster is marked as suspicious (but without final confirmation). A suspicious user is finally marked as malicious if it appears in suspicious groups more than τ times. The parameter τ controls the honest users’ error rate tolerance. The indicative feature’s distribution is close to that of the malicious users due to statistical errors. AUROR determines the value of τ automatically based on the input. We should notice that the adversary appears in the suspicious groups multiple times. Thus the value of τ also depends on the number of indicative features.

Finally, AUROR trains the global model by excluding the features submitted by malicious users in order to produce . Therefore, AUROR automatically generates a final accurate global model when it is under a poisoning attack. Shen et al. [10] evaluated AUROR and demonstrated that the attack success rate and accuracy drop of were very small. Therefore, AUROR is a successful defense for indirect CDL.

### 4.3.4 Evaluation

Shen et al. [10] built an indirect CDL model and demonstrated how false training data affects the global model. They used two well-known datasets: MNIST (handwritten numbers) and GTSRB (German traffic images). Shen et al. set 30% of customers as malicious ones, and the accuracy of the global model dropped by 24% compared to the model trained by the benign dataset for MNIST. The GTSRB trained model accuracy dropped 9% when 30% of users are malicious. In a word, indirect CDL is susceptible to poisoning attacks.

After that, Shen et al. [10] added AUROR during indirect CDL. They observed that the attack success rate was reduced to below 5% when the malicious ratio was 10%, 20%, and 30% for MNIST simulations. The accuracy drop is 0%, 1%, and 3% when the malicious ratio is 10%, 20%, and 30%. This proved that AUROR could efficiently defend poisoning attacks and that the image recognition system retains similar accuracy even excluding the malicious features. In the GTSRB experiment, Shen et al. [10] observed that the attack success rate is below 5% for malicious ratios from 10% to 30% when AUROR is used to preprocess the input. And the accuracy drop remains negligible for malicious ratios from 10% to 30%.

## 4.4 A NEW CDL ATTACK: GAN ATTACK

Hitaj et al. [12] developed a new attack on an indirect CDL based on generative adversarial networks (GANs). He proved that the privacy-preserving feature of indirect CDL makes the model more susceptible than direct CDL. In Hitaj et al.’s model, the attacker runs a GAN and pretends to be a user; then he or she infers the privacy information from the victim’s device by downloading gradient vectors. The attacker can influence not only the local data but also the learning process of the global model and deceive the victim into releasing more personal information.

### 4.4.1 Generative Adversarial Network (GAN)

Unlike the normal deep learning model, the goal of GANs is to generate “new” images that have similar distributions as the target images. As shown in Figure 4.4, the generative network is first initialized with random noise. At each iteration, it is trained to minimize the distance between the generated images and training images, while the discriminator is trained to distinguish generated images from the original dataset. This iteration continues until the discriminator cannot identify the generated images. In other words, the generator is trying to fool the discriminator.

![](img/efffc69cb8cda75bcf341884e3396898_131_0.png)

FIGURE 4.4 Architecture of GAN.

### 4.4.2 GAN Attack

The GAN threat model may come from an active insider. The following assumptions are made:
- (1) the adversary works as an insider within the CDL protocol;
- (2) the object of the adversary is to steal personal information from victims, such as favorite places, movie ratings;
- (3) the adversary only attacks other users, not the central server; GAN attacks do not affect the global model;
- (4) the adversary already has knowledge of the global model, e.g., model structure, the label of the data;
- (5) a GAN attack is adaptive and works in real time.
The adversary actively downloads the parameters distributed by the server, runs GAN locally, slightly changes the uploaded parameters, and uploads the forged gradients.

### Main Protocol

Suppose the adversary A is an insider of a privacy-preserving CDL protocol. All users agree in advance on the learning object, which means that they agree on the neural network architecture.

For simplicity, we first consider only two players: the adversary A and the victim V. V declares labels [a, b], while A declares labels [b, c]. They first run CDL for several epochs until the accuracy of both the global model and the local model have reached a predetermined threshold.

Then V continuously trains its network: V downloads parameters from the central server and updates its local model, which corresponds to the label [a, b]. V uploads the parameters of its local model to the server after it trains the local model.

On the other side, A also downloads the parameters, updates its local network with labels [b, c]. Unlike V, A first trains its local generative adversarial network to mimic class [a]’s distribution. Then the faked class [a]’s samples are generated. Next, A labels class [a]’s samples as class [c]. After that, it trains its local model on [b, c] and uploads the parameters to the central server, as V does. This process iterates until V and A converge to the threshold.
