
Input
(input.channel)

(2+1)D Unit
[input.channel, output.channel]

1x3x3 conv, \(\alpha\),
stride 1, \(\gamma\), \(\gamma\)

batch normalization

ReLU

3x1x1 conv, \(\beta\),
stride \(\gamma\), 1, 1

Output
(output.channel)

\(\alpha = \frac{3^3 * input\_channel * output\_channel}{3^2 * input\_channel + 3 * output\_channel}\)

\(\beta = output\_channel\)

\(\gamma = \begin{cases} 1 & \text{if } input\_channel = output\_channel \\ 2 & \text{if } input\_channel \neq output\_channel \end{cases}\)

## Residual Module

Input
(input.channel)

R(2+1)D Block [input.channel, output.channel]

(2+1)D Unit [input.channel, output.channel]
batch normalization
ReLU
(2+1)D Unit [output.channel, output.channel]
batch normalization
+
ReLU

Output
(output.channel)

Branch:
input_channel = output.channel ?
yes -> direct add
no -> 1x1x1 conv, output.channel, stride 2, 2, 2 -> batch normalization -> add

Figure 4. Architecture of a (2 + 1)D residual module.

## Video frames
16 frames (224x224)

- 7x7x7 conv, 64, stride 2, 2, 2
- batch normalization
- ReLU
- 1x3x3 max-pool, stride 1, 2, 2
- 1x1x1 conv, 64, stride 1, 1, 1
- batch normalization
- ReLU
- 3x3x3 conv, 192, stride 1, 1, 1
- batch normalization
- ReLU
- 1x3x3 max-pool, stride 1, 2, 2
- inc. [64, 96, 128, 16, 32, 32]
- inc. [128, 128, 192, 32, 96, 64]
- 3x3x3 max-pool, stride 2, 2, 2
- inc. [192, 96, 208, 16, 48, 64]
- inc. [160, 112, 224, 24, 64, 64]
- inc. [128, 128, 256, 24, 64, 64]
- inc. [112, 144, 288, 32, 64, 64]
- inc. [256, 160, 320, 32, 128, 128]
- 2x2x2 max-pool, stride 2, 2, 2
- inc. [256, 160, 320, 32, 128, 128]

## Video frames
16 frames (112x112)

- 1x7x7 conv, 45, stride 1, 2, 2
- batch normalization
- ReLU
- 3x1x1 conv, 64, stride 1, 1, 1
- batch normalization
- ReLU
- R(2+1)D Block [64, 64]
- R(2+1)D Block [64, 64]
- R(2+1)D Block [64, 64]
- R(2+1)D Block [64, 128]
- R(2+1)D Block [128, 128]
- R(2+1)D Block [128, 128]
- R(2+1)D Block [128, 128]
- R(2+1)D Block [128, 128]
- R(2+1)D Block [128, 256]
- R(2+1)D Block [256, 256]
- R(2+1)D Block [256, 256]
- R(2+1)D Block [256, 256]
- R(2+1)D Block [256, 256]
- R(2+1)D Block [256, 256]

![](img/1752b062af2760b8561f6faaf183b3d0_205_0.png)

As discussed in the paper of Carreira, J. and Zisserman, A. [6], although I3D models can learn motion features from RGB input videos, using optical-flow as inputs can introduce some recurrent sense to the models and significantly improved the performances. In this research, we also use the same fusion method to combine output predictions of I3D models and R(2 + 1)D models. The two-stream fusion method is illustrated in Figure 6. To investigate the effects of different two-stream fusion ratios in prediction performances, we tested various fusion ratios of the two models by setting different values for rgb_weight and flow_weight in the Two-stream fusion module. For example, if only using 30% of RGB data fine-tuned model's output and 70% of optical-flow data fine-tuned model's output then rgb_weight is set to 0.3 and flow_weight is set to 0.7.

Because frames of the dataset come from 12 different videos, we used leave-one-videos-out cross-validation to properly evaluate the performance of the models. For each video, we used all the frames extracted from it as testing data and all the frames extracted from the other videos as training data. We used the training data to fine-tune the models and used the fine-tuned models to predict labels for testing data. Then we count the total number of correct and incorrect prediction and calculate the accuracy.

## Results

Figure 7 shows the results of using different fusion ratio of RGB and optical-flow data fine-tuned models on accuracies of prediction of each behavior. And Figure 8 and Figure 9 show confusion matrixes of correct and incorrect prediction ratio of behaviors in combinations of rgb_weight and flow_weight. In Figure 7, we can see that for “drink” behaviors, combinations with more portion of RGB fine-tuned models have better performance than combinations with more portion of optical-flow fine-tuned models for both I3D models and R(2 + 1)D models. And the performance of R(2 + 1)D models are better than the performance of the I3D models in this behaviors.

![](img/1752b062af2760b8561f6faaf183b3d0_206_0.png)

**Figure 6.** The two-stream fusion method.

In Figure 8 and Figure 9, from confusion matrixes of both I3D model and R(2 + 1)D model, we can see that almost false predicted samples of “drink” behaviors are misclassified as “eat” behaviors. We can explain that as the water-feed nipple and food-feed door are quite close to each other; Sometimes the two behaviors look very similar and the dataset is also imbalanced with the ratio of the number of “drink” frames to the number of “eat” frames is about 1:6.85. Therefore, the models tend to predict “drink” behaviors as “eat” behaviors in many cases. It also explains why models fine-tuned using RGB data are more precise in distinguishing the two behaviors than models fine-tuned using optical-flow data. RGB data fine-tuned models can utilize the information of the mouse’s mouth contact with water-feed nipple or food-feed door. However, this information is lost in optical-flow data because there is no motion of water-feed nipple or food-feed door in the scenes.

![](img/1752b062af2760b8561f6faaf183b3d0_207_0.png)

![](img/1752b062af2760b8561f6faaf183b3d0_207_1.png)

![](img/1752b062af2760b8561f6faaf183b3d0_207_2.png)

![](img/1752b062af2760b8561f6faaf183b3d0_207_3.png)

![](img/1752b062af2760b8561f6faaf183b3d0_207_4.png)

![](img/1752b062af2760b8561f6faaf183b3d0_207_5.png)

![](img/1752b062af2760b8561f6faaf183b3d0_207_6.png)

![](img/1752b062af2760b8561f6faaf183b3d0_207_7.png)

Figure 7. Accuracies of the prediction of each behavior with different two-stream fusion ratios.

![](img/1752b062af2760b8561f6faaf183b3d0_208_0.png)

Figure 8. Confusion matrices of predictions of I3D models with different two-stream fusion ratios.

![](img/1752b062af2760b8561f6faaf183b3d0_209_0.png)

**Figure 9.** Confusion matrices of predictions of R(2 + 1)D models with different two-stream fusion ratios.

For “eat”, “groom”, “micro-movement”, “rear”, and “walk” behaviors, we can see that using a right combination of RGB data fine-tuned models and optical-flow data fine-tuned models give a better performance than using these models only. The R(2 + 1)D model outperforms I3D model in classifying “micro-movement” and “rear” behaviors but the I3D model is better in classifying “walk” behaviors.

The two models work very well on classifying “hang” behaviors and their performances just slightly reduce when we use a high portion of optical-flow data fine-tuned models because of the lack of the mouse surrounding environment in the optical-flow data.

And for the “rest” behaviors, it is easy to understand why using a high portion of optical-flow data fine-tuned models give better performance as “rest” behaviors are different from other behaviors that they have no movement in the scenes.

Overall, the two deep learning models we investigated in this research outperform the previous research model in the Mouse behavior dataset as shown in Table 2. The accuracies of the two models with different fusion ratio are shown in Figure 10. Both models have best performances at fusion ratio of 40% RGB data fine-tuned models and 60% optical-flow data fine-tuned models. The I3D model achieves 96.9% of accuracy and the R(2 + 1)D achieves 96.3% of accuracy.

**Table 2. Comparison of performance of models**

| No | Model | Accuracy (%) |
| :--- | :--- | :--- |
| 1 | MF + SVMHMM [1] | 93.0 |
| 2 | FV + NN [4] | 95.9 |
| 3 | I3D | 96.9 |
| 4 | R(2 + 1)D | 96.3 |

![](img/1752b062af2760b8561f6faaf183b3d0_210_0.png)

**Figure 10.** Accuracies of I3D models and R(2 + 1)D models with different two-stream fusion ratios.

## CONCLUSIONS

We have investigated two current state-of-the-art deep learning models for human action recognition in a mouse behavior recognition task. Both models outperformed the models from previous researches. It proves that our approach of utilizing deep learning models that pre-trained on human action datasets and fine-tuning them for animal behavior recognition tasks is efficient despite the scarcity of training data. We also showed the effect of two-stream fusion ratios on the predictions. The fine-tuned models can precisely recognize most of behaviors they learned from the mouse behavior dataset. But there are some difficulties in classifying behaviors that are ambiguous or similar to other behaviors. Our proposal to solve the problem is to collect more data on difficult-to-classify behaviors. And we can redesign experimental environment such as changing the camera position or the cage configuration in order to minimize the ambiguity between behaviors. For further research, we will collect behavior data of other animals. Then we will use them to fine-tune the fine-tuned models we achieved from this research to experiment if we can really efficiently utilize deep learning models for animal behavior recognition tasks without any requirements of extensive data for training these models.

## ACKNOWLEDGEMENTS

In this research, the super-computing resource was provided by Human Genome Center, the Institute of Medical Science, The University of Tokyo. Additional computation time was provided by the super computer system in Research Organization of Information and Systems (ROIS), National Institute of Genetics (NIG). This work was supported by JSPS KAKENHI Grant Number JP18K11525.
