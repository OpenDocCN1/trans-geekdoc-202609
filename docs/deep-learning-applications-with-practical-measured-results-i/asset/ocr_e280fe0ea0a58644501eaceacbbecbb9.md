While the model in [13] was trained to handle random holes and used the irregular mask dataset proposed by Liu [12], which can meet our experimental requirements. So we used the inpainting model proposed in [13] to prove the reliability of proposed mask dataset in removing redundant pedestrians in the image background.

We compared our mask dataset with the mask dataset proposed by Liu [12], the mixed mask dataset by training with the inpainting model [13]. Our mask dataset contains 23,500 masks for training and 11,480 masks for testing which are randomly generated from COCO dataset. The mask dataset proposed by Liu [12] contains 55,115 masks for training. The mixed mask dataset has a total of 78,615 masks (including 23,500 training masks that we randomly generated and 55,115 masks for training in Liu [12]).

Our comparison results are shown in the Table 2, from which we can see that we have improved the data in processing the image inpainting in a special application scene. We preserved the target character while filtering out redundant pedestrians by using our randomly generated masks. Although using our mask dataset and mixed mask dataset have similar results, it performs poorly without using our mask dataset. The comparison proves the reliability of our mask dataset in removing redundant pedestrians from image background.

# Table 2. The results of image inpainting using different mask datasets.

| COCO Dataset | PSNR | SSIM | L1 Loss (%) |
|---|---|---|---|
| Liu mask [12] | 26.59 | 0.9146 | 2.31 |
| Liu mask [12] + our mask | 27.55 | 0.9233 | 2.01 |
| our mask | 27.54 | 0.9230 | 2.02 |

Figure 6 shows the intermediate results of our test, from top to bottom, which are the original picture, the instance segmentation result about people, the result of removing redundant pedestrians, and the result of image inpainting. The visualization results show that our experiment can easily screen out one or more redundant pedestrians in background and remove them.

![](bbox=[0.2, 0.61, 0.82, 0.83])

# Figure 6. The result with our proposed mask dataset.

But our experiment still has some limitations. (1) When the target character is “glued” to the other characters, as shown in the left-most figure, it produces poor results even if the redundant pedestrians