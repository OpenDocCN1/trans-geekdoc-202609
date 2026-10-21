$Conf_i = \sum_{k=1}^{K} (W_k * p_{ik}) / \sum_{k=1}^{K} W_k$ (15.3)

A multi-stream discrete Hidden Markov Model (MSDHMM) included a stream-related weighting segment created to fuse the multiple modalities. The EHD and Gabor feature calculated a stream relevance weight using Baum Welch (BW) and minimum classification error (MCE). Distance-based MSDHMM structure (λ) referred to in Equation (15.4), where π, A, and B are state prior, transition and observation probabilities, and W-relevance weight, respectively. Probability-based MSDHMM b_ij was calculated using Equation (15.5), relevance weights w_ijk and partial stream probability b_ijk in each state i, symbol j, and stream k (Missaoui et al., 2011).

$\lambda = (\pi, A, B, W)$ (15.4)

$b_{ij} = \sum_{k=1}^{L} w_{ijk} b_{ijk}$ (15.5)

The multi-stream continuous Hidden Markov Model (MSCHMM) used a maximum likelihood estimation (MLE)-based BW algorithm and the MCE to identify the state and component level of stream relevance weights (Oualid Missaoui et al., 2013). Multiple Hidden Markov Model (HMM) was used to develop the ensemble Hidden Markov Model (eHMM). GPR images were analyzed using B-Scan signatures to extract EHD and Gabor features. HMM was used to identify the similarity between observed sequences in a cluster by log-likelihood-based similarity and path mismatch (Anis Hamdi, 2015).

Based on Multiple-instance HMM (MiHMM), they developed an HMM sequence from the alarm area. Discrete and HOG features were extracted from GPR data and tested on synthetic/landmine data sets (Manandhar et al., 2015). A forward-looking ground penetrating radar (FLGPR) uses stepped frequency for sensing and filtered back projection to create images of subsurface objects. A Machine Learning classification algorithm was trained with features around each selected location. With the help of Bag-of-Visual-Words (BOV) and Fisher Vector (FV) feature learning methods, k-means algorithms discriminate between landmines and non-mines in FLGPR data. (Camilo et al., 2016).

The context-based classification used various classifiers based on the measure of the context. It took a variable length of sequences using a mixer of experts (ME) and a mixture of the HMM Experts (MHM ME) model to decompose the data into several contexts (Yuksel and Gader, 2016). The data from the A-Scan images were normalized and classified using one-class support vector machines (OCSVMs), where the kernel Radial Basis Function (RBF) was measured using Equation (15.6) through x_i and x_j (Tbarki et al., 2017).

$K_{(RBF)} = e^{\left( -\frac{||x_i - x_j||^2}{2\sigma^2} \right)}$ (15.6)