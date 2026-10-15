
The system that we consider in our experiments is composed of a DVS camera for capturing the scenes of the environment as event sequences and a given SNN deployed on the neuromorphic device. As shown in `Figure 7.28`, the adversarial attacks and noise filters are located at the input of the SNN and can modify the sequences of events. We perform several experiments with different combinations of attacks and defenses. The noise filters described in `Section 7.5.3` have been employed as a defense mechanisms. For the combinations where both attacks and defenses are applied to the system, the perturbations injected by the attack are applied before the filtering operation. In this way, it can filter out any events generated or modified by the attack, thus aiming at making a strong defense in practical systems. The detailed discussion of the adversarial attack methodologies is conducted in the following `Section 7.5.5`.

![Figure 7.28: Threat model considered in this work, where different types of adversarial attacks are deployed, and different types of DVS noise filters are applied as a defense.](images/fig7_28.jpg)

`[Figure 7.28:](#chapter7.xhtml#b7fig7_28)` Threat model considered in this work, where different types of adversarial attacks are deployed, and different types of DVS noise filters are applied as a defense.

### 7.5.5.1 Sparse Attack

The proposed `Sparse Attack` is an iterative algorithm that progressively updates the perturbation values according to the loss function (lines 2–7 of `Algorithm 31`) for every frame series of the dataset `D`. Its mask `M` determines in which subset of the event frames the perturbation should be added (line 3). Then, the output probability and its loss, obtained in the presence of the perturbation, are computed in lines 5 and 6, respectively. Finally, the perturbation values are updated according to the gradients of the inputs with respect to the loss (line 7).

![](images/comp07_9.jpg)

### 7.5.5.2 Frame Attack

The `Frame Attack` is a simple yet effective attack methodology that consists of adding a noise frame around the sample (see lines 4–5 of `Algorithm 32`). It does not require expensive calculations since the same perturbation (that forms the frame) is added to all the samples. Such a frame is not easy to spot in a dataset made of large images, like the DvsGesture (128 × 128), while its perturbations are more evident in the NMNIST dataset (34 × 34). One drawback is the overhead in terms of events added to the samples. In fact, the number of events dramatically increases for every frame since the attack targets each pixel of the boundary. Therefore, the sample size and the inference latency for processing the events with SNNs and filters increase as well.

![](images/comp07_10.jpg)

### 7.5.5.3 Corner Attack

As the name suggests, the `Corner Attack` targets the corner of the images. It starts by targeting only two pixels on the top-left corner (lines 8–9 of `Algorithm 33`). Then, if the attack is not successfully fooling the SNN (line 11), the algorithm moves to the other corners. If some samples are still correctly classified after hitting all four corners, the perturbation size increases and the algorithm resumes back from the first corner. Before the updating phase, when the perturbation switches between corners or increases its size, the attack is applied to each sample in the dataset that was not corrupted yet. The number of samples reduces as the algorithm proceeds, and the process speeds up. The main characteristic of this attack is that the samples are affected by a different amount of perturbation. For example, while the SNN misinterprets the majority of the samples after a few iterations, other samples are perturbed for a longer time, thus making the attack easier to spot.

![](images/comp07_11.jpg)

### 7.5.5.4 Dash Attack

The `Dash Attack` methodology is designed taking inspiration from the `Corner Attack`. Indeed, the two algorithms are pretty similar. The main difference is that in the `Dash Attack`, only two pixels are targeted at a time. The main structure of the algorithm is similar to the `Corner Attack`, as the `Dash Attack` starts targeting the top-left corner and modifying the first two pixels. Moreover, the `x`, `y` coordinates are updated to hit only two consecutive pixels within the same timestamp (see lines 14–22 of `Algorithm 34`). Hence, this attack is tough to spot, and the introduced perturbations do not cause a significant overhead of events on the samples. Moreover, all the samples under the `Dash Attack` are subjected to the same amount of perturbations.

![](images/comp07_12.jpg)

### 7.5.5.5 MF-Aware Dash Attack

A critical issue of the above-discussed attacks, as will be discussed in `Section 7.5.6`, is their intrinsic weakness against the `MF`. They targeted both ‘on’ and ‘off’ channels of the same pixels for the whole sample duration. Hence, the distinction between the pixels modified by the attack and those not affected is evident since the number of events generated in the targeted pixel coordinates is significantly higher than those associated with the other coordinates that were not hit during the attack. In addition, we have to consider that the proposed attacks primarily focus on the boundaries of the images. Therefore, they do not typically overlap with useful information since, in the datasets that we used, the subject is centered. Therefore, by hitting the perimeter or the corners, there is a low risk of superimposing adversarial noise on the main subject. These considerations explain why the `MF` is successful in restoring the original SNN accuracy. The targeted pixel coordinates are easily identifiable given their large number of events, and the filter does not interfere with the useful information because modifications are mainly made at the edge of the image.

Based on these observations, we have designed an attack that aims to nullify the defense provided by the `MF`, which we call the `MF-Aware Dash Attack`. It receives as input the parameter `th`, which is related to the `T` parameter of the `MF` (recall from `Algorithm 30`), and limits the number of frames that can be modified for each pixel (line 11 of `Algorithm 35`). Therefore, the algorithm perturbs only a couple of pixels, as in the case of the `Dash Attack`. However, after perturbing `th` frames, it proceeds to the following frames (lines 13–14). The `MF-Aware Dash Attack` generates the visual effect of a dash advancing along a line. The larger the parameter `th` is, the slower the dash will seem to move along the image.

![](images/comp07_13.jpg)

### 7.5.6 Evaluation of the DVS-Attacks

#### 7.5.6.1 Experimental Setup
