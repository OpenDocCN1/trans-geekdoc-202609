
comparison, we also provide the results of both the training and testing using real data (row 1 of Table 7). The experimental results show that their accuracy differs by 1.3%.

From the above experiments, we can see that the results of the two cross-validation experiments have little difference in terms of accuracy, which indicates that GASN has good transfer ability.

The proposed GASN in this paper is capable of similarity learning. In other words, GASN is trained with a large number of training samples so that the network has the ability to measure the similarity of two input images (i.e., the template and the search image in the training data). The greater the similarity, the higher the output score of GASN. Therefore, once a template image of TOI is given, the information provided by the template (such as the location and shape) can be used to match the target in the next image based on the similarity measure capabilities of GASN. Then, the target with the highest similarity is determined as the tracking result in the next image. Therefore, GASN can track the TOI using the template information instead of the appearance features of the training data, so the proposed GASN is highly robust.

## 5.2. Ablation Experiment of GA-SubNet

We explored the effect of GA-SubNet on false alarms. Figure 26 shows the anchors on Siamese-RPN (Figure 26a) and GASN (Figure 26b). It can be seen that after adding GA-SubNet, the anchors are mainly concentrated around the TOI, and the number of anchors is also greatly reduced. Table 8 shows the comparison results of whether to add GA-SubNet or not. Because GA-SubNet discards the useless anchors in the background and improves the imbalance between positive and negative samples, the accuracy is improved by 4.52% after adding GA-SubNet. Therefore, GASN with GA-SubNet can better distinguish the TOI from the background.

![](img/828a5d28a36454f7b3332df93f35492f_138_0.png)

(a)

![](img/828a5d28a36454f7b3332df93f35492f_138_1.png)

(b)

Figure 26. Ablation experiment on GA-SubNet: (a) Siamese-RPN; (b) GASN.

Table 8. Ablation experiment of GA-SubNet.

| Method | GA-SubNet | Accuracy |
|---|---|---|
| Siamese-RPN | x | 55.57% |
| GASN (ours) | ✓ | 60.09% |

## 5.3. Research on Pre-Training

In the deep learning field, in recent years, a common practice is to pre-train a model on some large-scale training data [31–33]. As shown in Figure 6b, the one-channel SAR image needs to be copied three times to use the pre-training parameters of three-channel RGB optical images. This method of copying one-channel SAR images three times has been widely used in SAR image processing tasks [12,15]. For example, to be suitable for SAR tracking tasks, the pre-training parameters of the optical image are adjusted by the one-channel SAR data copied three times, and the tracking results are good.

To determine whether it is reasonable to apply a model trained on a three-channel RGB image to a one-channel radar image in a completely different domain or not, we arranged a group of experiments. The final tracking results for the simulated data are shown in Table 9. The second row of the results contains the tracking results after pre-training the model using optical images and then fine-tuning the training using SAR images replicated as three channels. The first row contains the tracking results after training using only replicated SAR images without pre-training with optical images. The tracking accuracy is significantly reduced by approximately 4% compared to the second row. This illustrates that it is feasible and reasonable to apply a model trained on three-channel RGB images to one-channel radar images. Therefore, it is wise to use fine-tuning in the absence of sufficient training data.

Table 9. Accuracy indexes of research on pre-training.

| Pre-Training | Accuracy |
|---|---|
| × | 56.73% |
| ✓ | 60.09% |

## 5.4. Research on the Statistical Analysis

Regarding the statistical analysis of small data, we added an experiment where we trained 10 times and calculated the statistical average (including the mean and variance of the accuracy and the central location error (CLE)). The results are shown in Table 10.

Table 10. The statistical analysis of the tracking result.

| Method | Accuracy % | CLE |
|---|---|---|
| Siamese-RPN | 56.37 ± 0.72 | 7.49 ± 0.98 |
| GASN (ours) | 58.79 ± 0.61 | 6.56 ± 0.89 |

From the table, we can see that our method outperforms Siamese-RPN in terms of accuracy (58.79 > 56.37) and the accuracy variance (0.61 < 0.72), which indicates that our method is accurate and that the accuracy is more stable.

Moreover, our method outperforms Siamese-RPN in terms of the central location error (CLE) (7.49 > 6.56) and the CLE variance (0.89 < 0.98), which indicates that the CLE of our method is smaller and that the CLE is more stable.

## 6. Conclusions

To achieve the tracking of arbitrary TOIs in Video-SAR, this paper proposed a novel GASN. GASN is based on the idea of similarity learning, which uses the feature map of the template as the convolution kernel to slide windows on the feature map of the search image. Then, the output indicates the similarity of the two feature maps. Based on the maximum similarity, GASN can determine the tracking results in the search image. GASN tracks the TOI between the first frame and the next one instead of learning the appearance among all separate frames. Additionally, we established a GA-SubNet, which uses the location information of the template to obtain the location probability in the search image and selects the location with a probability greater than the threshold to exclude false alarms. To improve the tracking accuracy, the anchor that more closely matches the shape of the TOI is obtained by GA-SubNet through adaptive prediction processing. The experimental results showed that the tracking accuracy of the proposed method was 60.16% and 54.68% on the simulated and real Video-SAR data, respectively, which are higher than that of the two deep learning methods Siamese-RPN and Siamese-FC and the two traditional methods MOSSE and KCF.

In the future, we will try to apply scale invariant feature transform (SIFT) [34] and the Lee filter [35] to real Video-SAR for more accurate tracking results and research how to use the accurate tracking trajectory to refocus the moving target.

**Author Contributions:** Conceptualization, J.B. and X.Z.; methodology, J.B.; software, J.B.; validation, J.B., X.Z. and T.Z.; formal analysis, J.B.; investigation, J.B.; resources, J.S.; data curation, J.S.; writing—original draft preparation, J.B.; writing—review and editing, J.B.; visualization, X.Z.; supervision, T.Z.; project administration, X.Z.; funding acquisition, X.Z., J.S. and S.W. All authors have read and agreed to the published version of the manuscript.

**Funding:** This work was supported in part by the National Natural Science Foundation of China under grants 61571099, 61501098, and 61671113.

**Acknowledgments:** The authors thank all reviewers for their comments toward improving our manuscript, as well as the Sandia National Laboratory of the United States for providing SAR images. The authors would also like to thank Durga Kumar for his linguistic assistance during the preparation of this manuscript.

**Conflicts of Interest:** The authors declare no conflict of interest.

## Abbreviations

| Symbol | Definition |
|---|---|
| x | Search image |
| φ(x) | Detected feature map |
| g | Similarity learning function |
| F2 | New detected feature map for the best anchor shape |
| A^{reg}_{w×h×4k} | Similarity map regression |
| (w, h) | The weight and height of the shadow |
| loss_{loc} | Anchor location loss |
| loss_{cls} | Classification loss |
| p | The tracking result |
| (x_R, y_R) | The center coordinates of the tracking result |
| t | The total tracking time |
| z | Template image |
| φ(z) | Template feature map |
| F1 | Original detected feature map |
| k | The number of anchors |
| A^{cls}_{w×h×2k} | Similarity map for classification |
| (x, y) | The center point of the shadow in the previous image |
| loss_{shape} | Anchor shape loss |
| loss_{reg} | Regression loss |
| G | The shadow's ground truth |
| (x_G, y_G) | The center coordinates of the shadow's ground truth |
| N | The number of frames of the Video-SAR sequence |

## References

- 1. Damini, A.; Balaji, B.; Parry, C.; Mantle, V. A videoSAR mode for the X-band wideband experimental airborne radar. In Proceedings of the Algorithms for Synthetic Aperture Radar Imagery XVII, Orlando, FL, USA, 18 April 2010; p. 76990E.
- 2. Wells, L.; Sorensen, K.; Doerry, R.B. Developments in SAR and IFSAR systems and technologies at Sandia National Laboratories. In Proceedings of the 2003 IEEE Aerospace Conference Proceedings (Cat. No. 03TH8652.), Big Sky, MT, USA, 8–15 March 2003; pp. 21085–21095.
- 3. Hawley, R.W.; Garber, W.L. Aperture weighting technique for video synthetic aperture radar. In Proceedings of the Algorithms for Synthetic Aperture Radar Imagery XVIII, Orlando, FL, USA, 4 May 2011; p. 805107.
- 4. Linnehan, R.; Miller, J.; Bishop, E.; Horndt, V. An autofocus technique for video-SAR. In Proceedings of the Algorithms for Synthetic Aperture Radar Imagery XX, Baltimore, MD, USA, 23 May 2013; p. 874608.
- 5. Miller, J.; Bishop, E.; Doerry, A. An application of backprojection for Video-SAR image formation exploiting a subaperture circular shift register. In Proceedings of the Algorithms for Synthetic Aperture Radar Imagery XX, Baltimore, MD, USA, 23 May 2013; p. 874609.
