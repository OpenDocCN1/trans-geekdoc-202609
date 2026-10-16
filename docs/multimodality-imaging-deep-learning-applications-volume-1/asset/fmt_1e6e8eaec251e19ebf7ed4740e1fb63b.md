
A basic overview of machine learning techniques is provided in [appendix A](#Chapter_9.xhtml#Chapter_9.xhtml#ST234). Figure [9.3](#Chapter_9.xhtml#bk978-0-7503-2244-7ch9fig3) depicts the various AI approaches, with descriptions provided in table [9.2](#Chapter_9.xhtml#bk978-0-7503-2244-7ch9t2). This is divided into three categories: traditional, machine learning, and deep learning. In this section we will go through the various machine learning approaches used for cIMT/PA segmentation and measurements from CCA photos. As previously indicated, features must be retrieved before the ML model can be used. Some of the features are used to train the model, such as training data (*X*[*t**r*]), while the rest are used to test the model, such as test data(*X*[*t**s*]).

**Table 9.2.** Comparison between different cIMT regional segmentation methods for given attributes. (Reproduced with permission of Springer from \[[162](#Chapter_9.xhtml#bk978-0-7503-2244-7ch9bib162)\]. Copyright 2021 Society for Imaging Informatics in Medicine.)

| Attributes  || Conventional methods (1.1) || Machine learning (1.2.1) || Deep learning (1.2.2) |
| --- | --- | --- | --- |
| Types || Active contour, level sets, edge detection, dynamic programming (1.1.\*) || Supervised (1.2.1.1) || Geometric: ANN, SVM (1.2.1.1.1) || Supervised (1.2.2.1) || CNN, FCN (1.2.2.1.\*) |
| --- | --- | --- | --- | --- | --- |
| Logical: decision trees (1.2.1.1.2) |
| Probabilistic: Bayesian (1.2.1.1.3) || Unsupervised (1.2.1.2) || Autoencoders, deep belief networks (1.2.2.2.\*) |
| Unsupervised (1.2.1.2) || *K*\-means clustering (1.2.1.2.1) |
| Description || Techniques employing imaging features and processing for the cIMT regional segmentation. || The two-stage intelligence-based paradigm in which image features are extracted and then used by the ML model for training and testing for cIMT region identification. || Mimics the human visual cortex with numerous hierarchical networks of neurons extracting high-level features directly from images for recognition of the cIMT region. |
| Advantages || 
1. Fastest among all the methods for region estimation as no training and testing required.
2. Simple. 
1. Uses intelligence in the form of learning from experience/training and applies to unknown instances.
2. Somewhat generalized and can be applied to instances within a similar domain.
3. Faster than deep learning. 
1. Independent of feature extraction algorithms.
2. Can be scaled up to recognize/characterize millions of images.
3. Can be generalized and used in multiple domains. |
| Disadvantages || 
1. Task-specific and cannot be generalized.
2. Low accuracy. 
1. Dependent on the quality of features for better accuracy.
2. The accuracy curve diminishes when scaled up to a large number of instances. 
1. Costly in terms of computation time and memory.
2. Easily overfits and therefore requires different techniques for the prevention of overfitting. |
\* Other technologies.

The model parameters are adjusted based on the error during the training phase, which is based on the known and real outputs. This training procedure is repeated until the model parameters converge or do not change their values any longer, at which point training is considered complete. As a result, the model with learned parameters is put to the test with unknown outcomes. Once the model outputs are available, they are compared to actual outputs to determine the model’s performance. Arrhythmia \[[90](#Chapter_9.xhtml#bk978-0-7503-2244-7ch9bib90)\] and diabetes \[[91](#Chapter_9.xhtml#bk978-0-7503-2244-7ch9bib91)\] are two examples of ML applications that leverage the concept of an offline and online system. We call them supervised learning since they all use the ground truth during cross-validation, and it this used a lot in cIMT and PA computation from CCA images. Rosa *et al* \[[92](#Chapter_9.xhtml#bk978-0-7503-2244-7ch9bib92), [93](#Chapter_9.xhtml#bk978-0-7503-2244-7ch9bib93)\] and Molinari *et al* \[[23](#Chapter_9.xhtml#bk978-0-7503-2244-7ch9bib23)\] have two different schools of thought (SOTs) for segmenting the cIMT region from ultrasonography CCA images. Before applying the ML paradigm for cIMT segmentation, both SOTs extract the ROI. The following is a description of them.

#### 9.3.1 ANN model for cIMT region detection

Rosa *et al* \[[92](#Chapter_9.xhtml#bk978-0-7503-2244-7ch9bib92)\] obtained cIMT values from 60 B-mode ultrasonography CCA images in three steps. The CCA images were pre-processed to extract the ROI in stage 1, and stage 2 was the AI based classification step, which separated cIMT regional pixels from non-cIMT regional pixels, resulting in a binary picture. The determination of the LI and MA boundaries from the binary image was stage 3. The lower limit of the lumen was given as the posterior wall during the preprocessing stage, which involved using the CCA’s watershed transform \[[94](#Chapter_9.xhtml#bk978-0-7503-2244-7ch9bib94)–[96](#Chapter_9.xhtml#bk978-0-7503-2244-7ch9bib96)\] to detect the lumen. The final ROI in the region was where the far wall’s highest point was set to 0.6 mm above the binary lumen and the bottom boundary was set to 1.5 mm below the binary mask’s lowest point. As seen in figure [9.4](#Chapter_9.xhtml#bk978-0-7503-2244-7ch9fig4) (i), once the ROI has been recognized its dimensions are noted and retrieved from the original image. The retrieved ROIs are then used to demarcate the cIMT border in the next stage. The following stage uses an ensemble of four artificial neural networks (ANNs) \[[97](#Chapter_9.xhtml#bk978-0-7503-2244-7ch9bib97)\] to distinguish between pixels in the cIMT and non-cIMT regions. As illustrated in figure [9.4](#Chapter_9.xhtml#bk978-0-7503-2244-7ch9fig4)(ii), the ANN is in a form of multi-layer perceptron with three layers: input, hidden, and output. The computation is performed by the nodes in the ANN model, while the ‘learning experience’ is encoded in the weights between the hidden-input and hidden-output layers. These weights are typically randomly initialized and converge to a stable value as the learning advances, based on feedback on error propagation. In general, the algorithm is multiplying weights by the input values and then applying a sigmoid function $\\left( \\alpha = \\frac{1}{1 + e^{- x}} \\right)$,  

```
f̂(x) = α(β^j y + W^j y (α(β^i j + W^i j))),  
(9.1)
```

where *i* and *j* signify the weights between hidden-input and hidden-output layers, respectively. The weight values (*w*[*i* *j*] are optimized for each error propagation using the gradient $\\left( \\frac{\\mathrm{\\Delta}\\varepsilon}{\\mathrm{\\Delta}w} \\right)$,  

$$w_{\\mathit{ij}} = w_{\\mathit{ij}} - \\eta\\frac{\\mathrm{\\Delta}\\varepsilon}{\\mathrm{\\Delta}w},$$  

(9.2)
```
