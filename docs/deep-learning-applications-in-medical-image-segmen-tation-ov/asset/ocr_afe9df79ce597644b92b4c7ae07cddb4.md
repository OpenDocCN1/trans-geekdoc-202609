# Table 2.3 Summary of liver segmentation models based on deep learning.

| Ref. | Modality | Model | Dataset | Performance |
| :--- | :--- | :--- | :--- | :--- |
| (Stollenga et al. 2015) | CT | FCN | 3DIRCAD (Soler et al. 2010) | DSC – 95.7% |
| (Christ et al. 2017) | CT, MR | Cascaded FCN | 3DIRCAD (Soler et al. 2010) | DSC – 94.3% |
| (Li et al. 2018b) | CT | H-Dense U-Net | LiTS (Bilic et al. 2023), 3DIRCAD (Soler et al. 2010) | DSC – 96.5%, 98.2% |
| (Seo et al. 2020) | CT | U-Net modified (mUNet) | LiTS (Bilic et al. 2023), 3DIRCAD (Soler et al. 2010) | DSC – 96.0%, 98.51% |
| (Liu et al. 2019) | CT | Cascaded UNet | LiTS (Bilic et al. 2023) | DSC – 97.16% |
| (Zhou et al. 2018) | CT | U-Net – Nested | LiTS (Bilic et al. 2023) | IoU – 82.9% |
| (Dou et al. 2017) | CT | CNN-3D | Sliver07 | VOE 5.4 |
| (Tran et al. 2021) | CT | U^n–Net | LiTS (Bilic et al. 2023), 3DIRCADb (Soler et al. 2010) | DSC – 96.38%, 96.45% |
| (Wang et al. 2021) | CT | SAR-UNet | LiTS (Bilic et al. 2023) | DSC – 95.71% |
| (Fan et al. 2021) | CT | MSN-Net | MICCAI2017 LiTS (Bilic et al. 2023) | DSC – 94.24%, IoU – 90.75% |

segmenting lungs in chest X-rays is that the automatic lung segmentation model may be incorrectly created due to the extreme lung shape shifts and fuzzy lung regions caused by severe lung diseases. Liu et al. (2022) using the pretraining efficientnet-b4 encoder, the residual block and the LeakyReLU activation in the decoder enhanced the U-Net network’s performance. By avoiding the gradient instability brought on by the multiplication effect in gradient back-propagation, the network was able to extract lung field features efficiently. Experiments comparing this method to others have shown that not only is it more accurate at segmenting the lung from CXR images, but it also has a lower standard deviation and is more robust. Pal et al. (2022) introduced Attention UW-Net, which links the encoder and decoder layers through a novel intermediate layer. The final encoder layer undergoes upsampling to generate the intermediate layer,