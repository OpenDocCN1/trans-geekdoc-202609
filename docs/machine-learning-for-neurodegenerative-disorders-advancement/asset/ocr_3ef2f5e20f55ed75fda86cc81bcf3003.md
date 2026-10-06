40

Machine Learning for Neurodegenerative Disorders

# 2.4.3.1 PCA and ICA

Principal component analysis and independent component analysis (ICA) are two prominent dimensionality reduction techniques widely applied in neuroimaging to extract meaningful information from complex datasets. PCA, introduced by [27] is a linear transformation method that identifies the principal components (PCs) capturing the maximum variance in the data. In neuroimaging, PCA has been used for tasks such as reducing the dimensionality of fMRI data, uncovering latent structures, and enhancing signal-to-noise ratios [24]. By transforming the original variables into orthogonal components, PCA aids in simplifying the representation of neuroimaging data while retaining critical information.

On the other hand, ICA, proposed by [28] is a more recent and advanced technique that seeks to decompose a multivariate signal into statistically independent components. ICA proven particularly valuable in uncovering spatial and temporally distinct sources of neural activity in MRI data [29]. ICA assumes that the observed signals are mixtures of independent sources, enabling the separation of brain networks with unique functional roles. In the realm of neuroimaging, ICA has been applied to uncover resting-state networks, providing insights into the intrinsic functional architecture of the brain

While PCA and ICA are powerful tools for dimensionality, they differ in their underlying assumptions and applications. PCA focuses on capturing variance, making well suited for denoising and feature extraction, while ICA emphasizes the stability of sources, enabling the identification of spatial and temporally distinct functional networks. The choice between PCA and ICA in neuroimaging studies depends on the specific goals and characteristics of the data [30].

# 2.4.3.2 Autoencoders

Autoencoders represent a powerful class of neural architectures widely employed in neuroimaging for unsupervised feature learning and dimensionality reduction. The fundamental idea behind autoencoders is to compress high-dimensional data into a lower-dimensional representation and then reconstruct the input from this compressed representation. This process enables the network to learn a compact and informative representation of the data. In the context of neuroimaging, autoencoders have been applied to various modalities, including MRI and fMRI.

The work of Hinton and Salakhutdin [31] introduced the concept of deep autoencoders, paving the way for the development of deep learning architectures. Deep autoencoders consist of multiple layers of encoding and decoding units, allowing the learning of hierarchical and abstract representations of complex neuroimaging data. Applications of deep autoencoders in neuroimaging include tasks such as denoising, feature extraction, and anomaly detection [32].

Furthermore, autoencoders have been integrated into generative models for the synthesis of realistic neuroimaging data. The variational autoencoder (VAE) combines autoencoders with probabilistic modeling, enabling the generation of diverse and realistic samples from the latent space. VAEs have been utilized in the generation of synthetic brain images, facilitating data augmentation and enhancing the training of latent models.

The versatility of autoencoders makes them valuable tools in neuroimaging research, providing a mean to learn representations of complex data in an unsupervised manner. As the field continues to advance, autoencoders are likely to play a pivotal role in tasks such as data classification, image reconstruction, and the generation of synthetic datasets [33].

# 2.5 DISEASE IDENTIFICATION AND CLASSIFICATION

# 2.5.1 SUPPORT VECTOR MACHINES

Disease identification and classification in neuroimaging has witnessed substantial advancements with the integration of ML techniques, particularly support vector machines. An SVM is a powerful supervised learning algorithm that excels in classifying data by finding an optimal hyperplane