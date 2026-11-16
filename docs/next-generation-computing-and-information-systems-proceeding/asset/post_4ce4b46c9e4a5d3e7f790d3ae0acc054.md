
### 3.6 Learning the parameters

Since the overall model is large and has many parameters, learning the parameters of the two encoding modules of text and pictures simultaneously may cause shocks in the training results. Then, during back propagation, only the parameters of the text encoding module and the joint representation learning module are updated until the accuracy converges on the validation set. In the second stage, the parameters of the text encoding module and the joint representation learning module are fixed.

## 4 DIFFERENT STAGES OF TRAINING

### 4.1 Domestic eating habits

Each recipe in the LCR dataset includes three parts: title, raw materials, and operation steps. According to statistics, the average title length of each recipe is 6.83 words, and each formula contains an average of 6.89 raw materials and 7.34 operating steps. At the same time, the method of (Saini et al. 2021) in this paper, through binary/triple matching.

### 4.2 Different model

#### 4.2.1 PyTorch framework

The code in this article is implemented using the PyTorch framework. The model was trained using the Adam optimizer with a learning rate of 10^{-4}, an interval α of 0.3, λ of 0.1, and a batch size of 50. The above hyper parameters are selected on the validation set. When computing the loss function, we select positive and negative examples for anchor samples in each batch.

#### 4.2.2 Median rank

In this experiment, two tasks of using images to retrieve recipes (im2recipe) and using recipes to retrieve images (recipe2im) were selected to measure the model's accuracy. In addition, they were tested on three alternative sets of 1 000/5 000/10 000 sizes.

### 4.3 Different algorithms

This paper selects three models proposed in recipe retrieval in recent years as the benchmark algorithm and compares the accuracy with the proposed algorithm. They are: (1) JNE joint neural embedding (Rida, Almaadeed and Almaadeed 2019); (2) ATTEN (Rida et al. 2016); (3) Adamine (Khan et al. 2020). The experimental results are shown in Figure 2. It can be seen from Table 1 that the accuracy of the model in this paper is significantly better than the three benchmark algorithms under different tasks and different candidate set sizes.

### Table 1. Comparison between two attention methods.

| Size | Method | MedR | R@1 | R@5 | R@10 | MedR | R@1 | R@5 | R@10 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1000 | Uc_glob | 2 | 0.4 | 0.733 | 0.833 | 2 | 0.41 | 0.734 | 0.836 |
| | Uc_title | 2 | 0.407 | 0.733 | 0.828 | 2 | 0.413 | 0.739 | 0.834 |
| 5000 | Uc_glob | 6.8 | 0.193 | 0.46 | 0.592 | 6.4 | 0.202 | 0.469 | 0.597 |
| | Uc_title | 6.5 | 0.194 | 0.462 | 0.598 | 6.1 | 0.203 | 0.475 | 0.606 |
| 10000 | Uc_glob | 12.2 | 0.132 | 0.345 | 0.468 | 12 | 0.138 | 0.354 | 0.476 |
| | Uc_title | 12 | 0.133 | 0.344 | 0.471 | 11.5 | 0.139 | 0.358 | 0.483 |

![](img/9eefc6d2972274efeb1680c6a31895e5_182_0.png)

Figure 2. Comparison between two attention methods.

### 4.4 Different mechanism in the model

While comparing the accuracy, this paper also conducts some control experiments to verify the effectiveness of each module in this model by changing or deleting some modules in the model and comparing the accuracy.

#### 4.4.1 Environment vector

This paper adopts a different mechanism from the (Khan et al. 2021; Kapoor et al. 2015; Soni and Jain, 2018) to select the environment vector in the attention mechanism (see Section 3.2.5 for details). This paper compares the two selection methods. Among them, Uc_glob is the selection method of the environment vector and Uc_title is the selection method in the model of this paper. (Bhatt and Sharma 2023) uses the same end-to-end learned parameter vectors as the environment vector for all recipes.

#### 4.4.2 Training model

Figure 3 with Table 2 shows the results of training the model on the data of each part of the recipe and its combination (reporting only the accuracy of the im2recipe task on the 10,000-sized candidate set), which can reflect the importance of each part in the recipe.

### Table 2. Experiments results of using different recipe parts and their combinations.

| Size | Method | R@1 | R@5 | R@10 |
|---|---|---|---|---|
| 1000 | JNE | 0.239 | 0.546 | 0.674 |
| 1000 | ATTEN | 0.253 | 0.555 | 0.69 |
| 1000 | Adamine | 0.352 | 0.672 | 0.771 |
| 1000 | Proposed | 0.407 | 0.733 | 0.828 |
| 5000 | JNE | 0.097 | 0.277 | 0.393 |
| 5000 | ATTEN | 0.105 | 0.3 | 0.408 |
| 5000 | Adamine | 0.162 | 0.405 | 0.534 |
| 5000 | Proposed | 0.194 | 0.462 | 0.598 |
| 10000 | JNE | 0.064 | 0.194 | 0.286 |
| 10000 | ATTEN | 0.068 | 0.202 | 0.304 |
| 10000 | Adamine | 0.109 | 0.295 | 0.412 |
| 10000 | Proposed | 0.133 | 0.344 | 0.471 |

![](img/9eefc6d2972274efeb1680c6a31895e5_183_0.png)

Figure 3. Experiments results of using different recipe parts and their combinations.

## 5 CONCLUSION

If you would want to keep track of what you eat and how much you consume, this research presents a cross-modal recipe retrieval model that uses a self-attention mechanism to automatically retrieve the recipes that are most relevant to the input food images. The model in this paper uses the Transformer model’s self-attention mechanism to capture better the long-distance dependencies appearing in recipes and improves the semantic understanding ability of the model. This research also improves the attention mechanism that is utilized in the classic recipe retrieval model, which better captures the uniqueness across various recipes and further boosts the model’s accuracy. Therefore, the current method only takes targeted consideration in the recipe text encoding module, while a more commonly used image processing model is used in the picture encoding module. In the future, the image encoding module will be adjusted and optimized for the recipe retrieval problem.

## REFERENCES

- Bhatt, M.W. and Sharma, S., 2023. An object recognition-based neuroscience engineering: A study for future implementations. *Electrica*, 23(2).
- Kapoor, L., Bawa, S. and Gupta, A., 2015. Peer clouds: a P2P-based resource discovery mechanism for the Intercloud. *International Journal of Next-Generation Computing*, 6(3): 153–164.
- Khan, F., Khan, A.W., Khan, S., Qasim, I. and Habib, A., 2020. A secure core-assisted multicast routing protocol in mobile ad-hoc network. *Journal of Internet Technology*, 21(2): 375–383.
- Khan, S.U., Khan, A.W., Khan, F., Khan, M.A. and Whangbo, T.K., 2021. Critical success factors of component-based software outsourcing development from vendors’ perspective: A systematic literature review. *IEEE Access*, 10: 1650–1658.
- Li, C., Niu, H., Shabaz, M. and Kajal, K., 2022. Design and implementation of intelligent monitoring system for platform security gate based on wireless communication technology using ML. *International Journal of System Assurance Engineering and Management*: 1–7.
- Li, T., Guo, Y. and Ju, A., 2019, December. A self-attention-based approach for named entity recognition in cybersecurity. In *2019 15th International Conference on Computational Intelligence and Security (CIS)* (pp. 147–150). IEEE.
- Lohani, T.K., Ayana, M.T., Mohammed, A.K., Shabaz, M., Dhiman, G. and Jagota, V., 2023. A comprehensive approach of hydrological issues related to ground water using GIS in the Hindu holy city of Gaya, India. *World Journal of Engineering*, 20(2): 283–288.
- Lohande, M.P., Patil, D.D., Patil, L.V. and Shabaz, M., 2021. Machine-to-machine communication for device identification and classification in secure telerobotics surgery. *Security and Communication Networks*, 2021: 1–16.
- Mehdobniya, A., Webber, J.L., Neware, R., Arslan, F., Pamba, R.V. and Shabaz, M., 2022. Modified Lamport Merkle Digital Signature blockchain framework for authentication of internet of things healthcare data. Expert Systems, 39(10): 12978.
- Phasinam, K., Kassanuk, T. and Shabaz, M., 2022. Applicability of internet of things in smart farming. Journal of Food Quality, 2022: 1-7.
- Rida, I., Almaadeed, N. and Almaadeed, S., 2019. Robust gait recognition: a comprehensive survey. IET Biometrics, 8(1): 14-28.
- Rida, I., Boubchir, L., Al-Maadeed, N., Al-Maadeed, S. and Bouridane, A., 2016, June. Robust model-free gait recognition by statistical dependency feature selection and global-locality preserving projections. In 2016 39th International Conference on Telecommunications and Signal Processing (TSP) (pp. 652-655). IEEE.
- Saini, G.K., Chouhan, H., Kori, S., Gupta, A., Shabaz, M., Jagota, V. and Singh, B.K., 2021. Recognition of human sentiment from image using machine learning. Annals of the Romanian Society for Cell Biology, pp.1802–1808.
- Salvador, A., Hynes, N., Aytar, Y., Marin, J., Ofli, F., Weber, I. and Torralba, A., 2017. Learning cross-modal embeddings for cooking recipes and food images. In Proceedings of the IEEE conference on computer vision and pattern recognition (pp. 3020–3028).
- Soni, M. and Jain, A., 2018, February. Secure communication and implementation technique for sybil attack in vehicular Ad-Hoc networks. In 2018 Second International Conference on Computing Methodologies and Communication (ICCMC) (pp. 539–543). IEEE.
- Tharewal, S., Ashfique, M.W., Banu, S.S., Uma, P., Hassen, S.M. and Shabaz, M., 2022. Intrusion detection system for industrial Internet of Things based on deep reinforcement learning. Wireless Communications and Mobile Computing, 2022: 1-8.
- Wawale, S.G., Shabaz, M., Mehdobniya, A., Soni, M., Deb, N., Elashiri, M.A. and Naved, M., 2022. Biomedical Waste Management Using IoT Tracked and Fuzzy Classified Integrated Technique. Human-centric Computing and Information Sciences, 12(32).
- Wu, C., Lu, P., Xu, F., Duan, J., Hua, X. and Shabaz, M., 2021. The prediction models of anaphylactic disease. Informatics in Medicine Unlocked, 24: 100535.
- Yang, J. and Yang, J., 2020, October. Aspect based sentiment analysis with self-attention and gated convolutional networks. In 2020 IEEE 11th International Conference on Software Engineering and Service Science (ICSESS) (pp. 146-149). IEEE.
- Yang, M., Kumar, P., Bhola, J. and Shabaz, M., 2021. Development of image recognition software based on artificial intelligence algorithm for the efficient sorting of apple fruit. International Journal of System Assurance Engineering and Management: 1–9.
- Ye, R., Wang, W., Ren, Y. and Zhang, K., 2020, October. Bearing fault detection based on convolutional self-attention mechanism. In 2020 IEEE 2nd International Conference on Civil Aviation Safety and Information Technology (ICCASIT (pp. 869–873). IEEE.
