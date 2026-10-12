
The use of federated learning involving multi-institution collaboration will surely have a good impact on precision medicine, which is an emerging area of research. Precision medicine is a form of medicine that uses knowledge about a person’s genes or proteins and his lifestyle to prevent, diagnose or treat disease. It will help doctors to use a person’s genetic information for giving personalized care. The impact of federated learning in precision medicine needs to be explored. Much research is also going on related to communication speed, convergence time of the model, working with non-IID data [[3](#ch10.xhtml#ref10_3)], different poisoning attacks on data and model, secure aggregation, secure sharing of data, selection of clients for participation, security, and privacy of data and so on. Some of the challenges that may come while implementing the FL approach are discussed here. The main challenge is the updating of weights. The central cloud server is responsible for the updating of weights when multiple hospitals collaborate and the weights that should be given for each hospital should not be the same as some hospitals will be superior to others [[5](#ch10.xhtml#ref10_5)]. Federated averaging is proposed by some researchers, but it is not a good solution. Another challenge is that when coming to the research funding for training and implementing a federated model, contributions by different hospitals will be different in the sense that some may be labelling and uploading large amounts of data sets, but the diversity of images will be less. So how to calculate the share for each hospital is still a challenge. Also, if the participating sites operate on diverse hardware and software, the process of optimization and debugging will be difficult. The fourth challenge lies in the protocol differences in image acquisition and labelling tools used by various participating hospitals.

The future of federated learning looks very promising, and it is expected to play an increasingly important role in the development of machine learning models, especially in fields such as healthcare, finance, and the Internet of Things (IoT). Here are some key trends that are likely to shape the future of federated learning:

1.  **Increased privacy protection**: Federated learning allows data to be kept on the device or server where it is generated, instead of being sent to a central location. This approach provides increased privacy protection, which is critical in industries such as healthcare and finance where data confidentiality is paramount.

2.  **Improved model accuracy**: Federated learning has the potential to improve model accuracy by allowing data from a wider range of sources to be incorporated into the training process. This can lead to more accurate predictions and better decision-making.

3.  **Greater scalability**: Federated learning can be scaled to accommodate many devices or servers, which makes it ideal for applications in the IoT space.

4.  **Continued research and development**: Federated learning is still a relatively new approach, and there is a lot of ongoing research and development happening in this area. As more researchers and developers work on federated learning, we can expect to see new and innovative applications of this technology.

One of the key advantages of federated learning is its ability to improve data privacy since data is kept on the device or server where it is generated, rather than being sent to a central location. Federated learning also has the potential to improve model accuracy by allowing a wider range of data sources to be used in the training process, and it can be scaled to accommodate many devices or servers. In the future, we can expect federated learning to become increasingly important in industries such as healthcare, finance, and the Internet of Things (IoT), and continued research and development in this area will likely result in new and innovative applications of the technology.

## 7. Conclusion

We have seen that for disease diagnosis or tumour detection, the creation of a model from the data generated from a single hospital will not be reliable. But with the use of federated learning, this problem is solved as data from various collaborating hospitals or imaging centres can be used for the generation of the model. Also, the fear of data breach is avoided as the data is not directly shared, instead a local model is created, and this model is shared with the global server which in turn creates a global model from the local models received. In that way, data privacy is also guaranteed. This chapter discussed the concept of federated learning, its benefits, types, and its various applications in the healthcare sector such as covid-19 diagnosis, tumour detection, and steganalysis. In the future, in many more areas, federated learning can be applied to generating accurate models while ensuring data privacy and security.

## References

1.  [McMahan, B., Moore, E., Ramage, D., Hampson, S. and y Arcas, B.A.](#ch10.xhtml#R_ref10_1) 2017, April. Communication-efficient learning of deep networks from decentralized data. In Artificial Intelligence and Statistics (pp. 1273–1282). PMLR.

2.  [Chowdhury, A., Kassem, H., Padoy, N., Umeton, R. and Karargyris, A.](#ch10.xhtml#R_ref10_2) 2022. A review of medical Federated Learning: Applications in oncology and cancer research. In International MICCAI Brainlesion Workshop (pp. 3–24). Springer, Cham.

3.  [Majeed, A., Zhang, X. and Hwang, S.O.](#ch10.xhtml#R_ref10_3) 2022. Applications and challenges of Federated Learning paradigm in the big data era with special emphasis on COVID-19. Big Data and Cognitive Computing, 6(4): 127.

4.  [Zhang, W., Zhou, T., Lu, Q., Wang, X., Zhu, C., Sun, H., Wang, Z., Lo, S.K. and Wang, F.Y.](#ch10.xhtml#R_ref10_4) 2021. Dynamic-fusion-based federated learning for COVID-19 detection. IEEE Internet of Things Journal, 8(21): 15884–15891.

5.  [Ng, D., Lan, X., Yao, M.M.S., Chan, W.P. and Feng, M.](#ch10.xhtml#R_ref10_5) 2021. Federated Learning: A collaborative effort to achieve better medical imaging models for individual sites that have small labelled datasets. Quant. Imaging Med. Surg., 11(2): 852857. doi: [10.21037/qims-20-595](http://dx.doi.org/10.21037/qims-20-595)

6.  [Rieke, N., Hancox, J, Li, W. et al.](#ch10.xhtml#R_ref10_6) 2020. The future of digital health with federated learning. npj Digit. Med., 3: 119. [https://doi.org/10.1038/s41746-020-00323-1](https://doi.org/10.1038/s41746-020-00323-1).

7.  [Yi, L., Zhang, J., Zhang, R., Shi, J., Wang, G. and Liu, X.](#ch10.xhtml#R_ref10_7) 2020, September. SU-Net: An efficient encoder-decoder model of federated learning for brain tumour segmentation. In International Conference on Artificial Neural Networks (pp. 761–773). Springer, Cham.

8.  [Sheller, M.J., Reina, G.A., Edwards, B., Martin, J. and Bakas, S.](#ch10.xhtml#R_ref10_8) 2019. Multi-institutional deep learning modelling without sharing patient data: A feasibility study on brain tumour segmentation. In International MICCAI Brainlesion Workshop (pp. 92–104). Springer, Cham.

9.  [Sheller, M., Edwards, B., Reina, G.A., Martin, J. and Bakas, S.](#ch10.xhtml#R_ref10_9) 2019. NIMG-68. Federated Learning in neuro-oncology for multi-institutional collaborations without sharing patient data. Neuro. Oncol., 21(Suppl 6): vi176–7. doi: [10.1093/neuonc/noz175.737](http://dx.doi.org/10.1093/neuonc/noz175.737). Epub 2019 Nov 11. PMCID: PMC6847543.

10.  [Roth, H.R. et al.](#ch10.xhtml#R_ref10_10) 2020. Federated Learning for breast density classification: A realworld implementation. In: et al. Domain Adaptation and Representation Transfer, and Distributed and Collaborative Learning. DART DCL 2020 2020. Lecture Notes in Computer Science, vol 12444. Springer, Cham. [https://doi.org/10.1007/978-3-03060548-3\_18](https://doi.org/10.1007/978-3-03060548-3_18).
