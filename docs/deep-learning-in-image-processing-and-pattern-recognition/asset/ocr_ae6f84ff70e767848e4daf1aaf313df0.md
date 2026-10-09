**Table 2. Mean TMQI scores of luminance-domain algorithm.**

| Preprocessing | Structure | Naturalness | Final |
| :--- | :--- | :--- | :--- |
| Gu's | 0.8273 | 0.4098 | 0.8562 |
| AdaLogT | 0.8305 | 0.6346 | 0.8983 |

# 5.2. Gradient-Domain Algorithm

The gradient-domain algorithm [16] based on the gradient-domain-aware AdaLogT method has achieved good results in quantitative evaluation and objective assessment.

Figure 10 shows the comparison of TM results for bright and dark scenes, where the first column is the HDR radiance map, the second column is the TM results under LogT, and the third column is the TM results using AdaLogT. When the input image is dark, the result under LogT is dim and the details are vague or even indistinguishable. Our method corrects image exposure and achieves a balance between detail preservation and image naturalness. The structure and local details of the image are better preserved in the result, and the visual effect is more consistent with the human eye's perception of the scene. In the quantitative user evaluation, the Fattal method and ours achieve scores of (6.73, 1.13) and (7.16,1.07), respectively.

![](bbox=[0.175, 0.405, 0.735, 0.774])

(a) (b) (c)

**Figure 10.** Comparison of the results of the gradient-domain TM algorithm in different preprocessing methods: (a) radiance map; (b) LogT; (c) AdaLogT.

Figure 11 is the scatter plot of the gradient-domain algorithm results under different preprocessing methods. Our algorithm achieves equal or better scores in the vast majority of images. Table 3 presents the mean TMQI scores under preprocessing methods LogT and AdaLogT. The gradient-domain objective function pays attention to image details and textures so that the TM results have better visual brightness and detail preservation. Therefore, compared with the result of LogT, the result of AdaLogT has a higher TMQI structure score, and has also achieved significant improvement in the naturalness index.