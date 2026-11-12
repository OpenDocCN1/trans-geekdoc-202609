# Table 2.4 Summary of lung segmentation models based on deep learning.

| Ref. | Modality | Model | Dataset | Performance |
| :--- | :--- | :--- | :--- | :--- |
| (Stirenko et al. 2018) | X-ray | CNN | SH | Acc – 70% |
| (Gaal et al. 2020) | X-ray | Attention U-Net | JSRT (Shiraishi et al. 2000) | DSC – 97.5% |
| (Hofmanninger et al. 2020) | CT | U-Net, ResU-net | LTRC (Goksel and Foncubierta-Rodriguez 2017), Anatomy3 (Yang et al. 2018b) | DSC – 94%, 92% |
| (Pawar and Talbar 2021) | CT | GAN | ILD (Depeursinge et al. 2012) | DSC – 96% |
| (Ait Skourt et al. 2018) | CT | U-Net | LIDC (Armato et al. 2011) | DSC – 95.02% |
| (Wu and Lin 2020) | CT | Dilated – FCN | LIDC/IDRI (Armato et al. 2011) | DSC – 97.02% |
| (Yahyatabar et al. 2020) | X-ray | Dense-Unet | JSRT (Shiraishi et al. 2000), Montgomery | DSC – 97.6%, 97.9% |
| (Liu et al. 2022) | X-ray | Improved UNet | JSRT (Shiraishi et al. 2000), Montgomery | DSC-97.9%, 97.7% |
| (Pal et al. 2022) | X-ray | Attention-UWNet | NIH Chest X-ray (Wang et al. 2017) | F1 – 83.8% |

comprising multiple fully connected convolutional layers. These layers establish connections with their corresponding up- and down-sampled blocks through skip connections. A down-sampling layer is employed to additionally link the intermediate layer to the decoder pipeline. UW-Net surpasses not only U-Net and its derivatives but also other traditional automatic and semiautomatic segmentation/annotation models developed in recent years. This model is optimal for the automatic annotation of organs due to the uniformity of the prediction accuracy of segmentation masks across all types (large, medium, and minor lesions). Table 2.4 summarizes various deep learning-based models for lung segmentation.

# 2.3.1.5 Kidney

Kidney segmentation is an essential step in analyzing images and the development of sophisticated procedures. For segmenting kidneys in CT scans,