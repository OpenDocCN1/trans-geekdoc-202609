![](bbox=[0.13, 0.1, 0.86, 0.245])

Figure 6. Illustration of the PSNR, Runtime, and Params for dataset1.

![](bbox=[0.165, 0.3, 0.835, 0.5])

Figure 7. Visual comparison of the SOTA models.

Figure 5 presents a series of comparisons of our proposed model under noisy and low-contrast conditions. These examples highlight the model ability to mitigate noise and enhance subtle anatomical features, demonstrating its robustness and reliability for use in real-world clinical settings. The visual examples clearly show that our model effectively enhances image quality even in challenging situations, such as those with significant noise or low contrast, which are common in clinical practice. This further supports the suitability of our approach for medical applications where high fidelity is crucial.

# 4.5. Comparison of the Baseline Models

Table 2 offers a nuanced comparison of various super-resolution models, evaluating their performance across different scaling factors and showcasing their efficiency and effectiveness through parameters like runtime and the image quality metrics PSNR and SSIM. Dataset1 and Dataset2 refer to the Figshare and Kidney Stone datasets, respectively, which were used in our experiments. No additional datasets were introduced. We have explicitly stated this to ensure clarity and transparency in our manuscript. Furthermore, we performed several preprocessing modifications to the original datasets. These modifications included resizing the images to meet the input requirements of the proposed model, applying random augmentations such as rotations, flips, and brightness adjustments, and adding Gaussian noise to simulate realistic conditions. These preprocessing steps are detailed in the Data Preprocessing section to provide a comprehensive understanding of the dataset preparation.