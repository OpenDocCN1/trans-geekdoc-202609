![](bbox=[0.1, 0.1, 0.85, 0.6])

FIGURE 9.2 Sample MRI scans depicting various stages of AD. The MD and MOD images are visible in the first and second columns, respectively. A few ND and VMD images are represented in the third and fourth columns, respectively.

# 9.3.2 PROPOSED FRAMEWORK

The typical workflow of the suggested approach is illustrated in Figure 9.3. It has three primary modules: preprocessing, feature extraction and classification, and ensemble learning. The oversampling data-level technique and image resizing are carried out during preprocessing. The feature extraction and classification module extracts the pertinent attributes and classifies them using customized EfficientNet-B0 and customized ViT models. The best configurations from CNN and ViT are picked for further processing. To enhance the overall performance, ensemble learning is adopted in the final stage. This stage involves ensemble selection, probability averaging, and classification.

**Preprocessing:** Generally, deep CNN yield better outcomes with huge data. The data distribution confirms the presence of a class imbalance problem. To address this, an oversampling data-level technique is utilized. The training set images are