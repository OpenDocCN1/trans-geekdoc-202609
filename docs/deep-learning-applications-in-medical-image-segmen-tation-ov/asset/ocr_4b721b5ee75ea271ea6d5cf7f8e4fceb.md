# Table 8.5 GAN-based segmentation method for breast.

| Reference | Modality | Method | Dataset | Performance (DSC) |
|---|---|---|---|---|
| Kamnitsas et al. (2017) | Mammography | FCN-CRF GAN | INBreast | 0.9097 |
| Kan et al. (2021) | X-ray | CGAN | INBreast | 0.8881 |
| Kazeminia et al. (2020) | Breast Ultrasound | BUS-GAN (Breast Ultrasound with GAN) | Private | 0.8712 |
| Kessler et al. (2020) | Breast Ultrasound | SPCGAN (semi-pixel-wise cycle GAN) | Private | 0.92 |
| Kim et al. (2017) | Mammography | CGAN | INBreast | 0.9154 |

address these challenges, several methods for bone segmentation and registration have been introduced.
Han et al. (2018) and Sekuboyina et al. (2018) employed GAN for spine segmentation. Han et al. focused on synchronously segmenting semantics of over 160 spinal structures, whereas Sekuboyina et al. concentrated on local spine segmentation. Meanwhile, Liu et al. integrated GAN with various neural networks for knee joint segmentation in MRI images across references (Liu 2019; Gaj et al. 2020; Kessler et al. 2020). Gong et al. (2021) utilized GAN for simultaneous segmentation and disease diagnosis of discs, neural foramens, thecal sacs, and posterior arches on axial MRI images (Table 8.6).

# Table 8.6 GAN-based segmentation method for spine.

| Reference | Modality | Model | Dataset | Performance (DSC) |
|---|---|---|---|---|
| Sekuboyina et al. (2018) | MRI | Spine-GAN (recurrent GAN) | Private | 0.87 |
| Shah (no date) | MRI | CycleGAN | T2PSE | Femur bone 0.97<br>Tibia bone 0.95<br>Femoral cartilage 0.66<br>Tibial cartilage 0.65 |
| Shen et al. (2019) | X-ray | DCGAN | Private | Femur 0.9762<br>Femoral head 0.9786 |
| Shi et al. (2020) | Ultrasound | CGAN | Private | 0.9603 |
| Shi et al. (2019) | MRI | GAN | Private | 0.949 |