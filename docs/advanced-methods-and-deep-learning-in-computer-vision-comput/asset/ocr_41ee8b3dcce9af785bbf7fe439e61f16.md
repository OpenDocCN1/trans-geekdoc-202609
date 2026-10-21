![](bbox=[0.12, 0.14, 0.88, 0.32])

FIGURE 7.5 The change in domain similarity when the supportive samples are added to the source domain. In our experiments, we only continue our adaptation as long as the similarity value goes up, which is represented by the solid lines before the slash symbols. A: Amazon, C: Caltech, W:Webcam, D: Dslr.

# Experiments.

We use Office+Caltech dataset containing images from four domains: Amazon (A), Webcam (W), DSLR (D), and Caltech (C). This leads to a total of 12 domain pairs for testing. 10 common classes are selected in all domains. For each class, A, C, D and W have about 100, 100, 15 and 30 images, respectively. We follow the protocol used in Gong et al. (2013) to generate the source and target domain data. DeCAF features (Donahue et al., 2014) are used in our experiment. We compare two nonadaptation (NA) methods, and five state-of-the-art unsupervised DA methods: SVM and Dictionary Learning Based Classification (DLC) are the two NA methods, Subspace Interpolation via Dictionary Learning (SIDL) (Ni et al., 2013), Geodesic Flow Kernel (GFK) (Gong et al., 2012), Transfer Joint Matching (TJM) (Long et al., 2014), Landmarks (Gong et al., 2012) and DA-NBNN (Tommasi and Caputo, 2013) are the unsupervised DA methods. DLC is implemented using the online dictionary learning method as Mairal et al. (2009) and is also used as the initial dictionary in the proposed approach.

We also compare in change of domain similarity in Fig. 7.5 with classification results in Table 7.3 and find that the accuracy likely increases when the domain similarity value continues to go up as more supportive samples are added to the source domain.

We showed that dictionary learning is an effective approach in addressing domain shifts under unsupervised setting. The general idea is to project data representations from multiple domains to the same latent space where their distributions are more similar. Instead of doing this transformation on one semantic level, we also showed the benefits of hierarchical dictionary learning for gradual adaptation on multiple semantic levels. Finally, we demonstrate the benefits of incrementally adding selective support samples to the source domain are guaranteed to increase the domain similarity, which generally leads to better classification performance.

Dictionary-based approaches appear to have fallen out of favor due to superior performance from methods based on Generative Adversarial Networks.

# 7.4 Unsupervised domain adaptation using deep networks

Deep neural networks are a powerful class of machine learning models for extracting meaningful representations from images. Despite their success in achieving state-of-the-art performance in several visual recognition tasks (Ren et al., 2015; He et al., 2016; 2017), neural networks suffer from domain shift i.e., the performance of neural networks drops signifi-