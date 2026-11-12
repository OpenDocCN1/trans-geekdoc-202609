# Table 2.2 Summary of brain segmentation models based on deep learning.

| Ref. | Modality | Model | Dataset | Performance |
| :--- | :--- | :--- | :--- | :--- |
| (Wachinger et al. 2018) | MR | CNN | MICCAI BRATS (Landman and Warfield 2019) | DSC – 91.0% |
| (Roy et al. 2019) | MR | FCN | MALC15 (Marcus et al. 2007), ADNI-29 (Jack et al. 2008) | Acc – 88%, 83% |
| (Coupé et al. 2020) | MR | CNN-ensemble | Private | DSC – 73.3% |
| (Chen et al. 2017a) | MR | ResNet | MRBrainS | DSC – 84.3% |
| (Wang et al. 2019c) | MR | CNN-3D | CANDI (Kennedy et al. 2012), IBSR-18 (Frazier et al. 1910) | DSC – 90.7%, 90.4% |
| (Sun et al. 2020) | MR | AG – UNet, AG – FCN | ADNI-29 (Jack et al. 2008), LONILPBA40 | DSC – 88.64%, 80.67% |
| (Xue et al. 2018) | MR | SegAN | MICCAI BRATS (Menze et al. 2015) | DSC – 85% |

deep supervision method for segmenting 3D images. For liver segmentation, the 3D deeply supervised network achieved higher performance. Tran et al. (2021) proposed an alternative network architecture called U^n–Net (n-fold U-Net). The U^n–Net model utilizes a skip connection based on the features extracted from the convolutional unit outputs. As a result, the U^n–Net network makes use of the convolution unit output features at the nodes. The authors tested a U^2–Net and a U^3–Net for segmentation of liver and liver tumor in this work. Moreover, the network nodes incorporated DC and a dense structure. The proposed networks outperformed existing networks in experiments. Wang et al. (2021) proposed SAR-U-Net architecture based on the traditional U-Net. The SE block within the U-Net encoder was initially introduced to dynamically extract image features following each convolution. It achieves this by concealing less relevant areas of the image while accentuating the portions essential to the current segmentation task. Second, the ASPP was employed to gather multi-scale image details through various receptive fields, replacing both the transition layer and the output layer. Third, the conventional convolution block was substituted with residual structures to address the gradient vanishing issue, consequently