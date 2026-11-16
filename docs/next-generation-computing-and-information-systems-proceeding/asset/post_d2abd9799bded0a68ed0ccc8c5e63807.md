
examination, and laboratory reports, and then gives the appropriate medicine for the disease according to the patient’s corresponding situational information.

## 3.2 Contextual information modeling methods

To solve the problem of the explosion of patient contextual information combination, it is necessary to try to reduce the dimensionality of the contextual information (Rida et al. 2018). Clustering is a standard method to solve such problems, which can be roughly divided into two types: hard clustering and soft clustering. Among them, the hard clustering classifies the data exactly. Finally, after several iterations converge, each document is assigned a fixed context topic, so the topic distribution of each context document can be calculated using Equation (1).

\[
Q(a|e) = \frac{n_{e,a} + \alpha}{\sum_{i=1}^k n_{e,a_i} + L\alpha} \quad (1)
\]

Where e and a represents the number of words in the context document d assigned to the topic a, α is the Dirichlet prior parameter, and L is the number of context topics.

## 3.3 Context-aware drug recommendation method

After the soft clustering of the context information is completed, the comprehensive modeling of all the data can be carried out. The modeling method proposed in this paper is based on two assumptions about the diagnosis and treatment process:

- 1) Context topics are soft clustering of context information, and each context topic may affect the suitable medicines and the prone diseases of patients.
- 2) The data of each patient corresponds to a latent variable, which represents the disease of the patient, called the disease theme.

Figure 1 shows the probability map representation of the model, and the symbol descriptions.

![](img/9eefc6d2972274efeb1680c6a31895e5_38_0.png)

Figure 1. Probability graph representation of the MLDA model.

## 3.4 Sampling and inference algorithms

MLDA needs to infer the hidden variables z, c, and y. However, since the exact inference algorithm is unsolvable, this paper uses the collapsed Gibbs sampling (CGS) to sample the hidden variables and obtains the parameters $\theta, \varphi, f$; then, the parameters obtained by training are used to recommend drugs to new patients.

First, random initialization is performed on all the data in the training set: for the nth data, the context topic latent variable $d_n$ and disease topic latent variable $a_n$ are randomly assigned, and for the mth disease document word in the nth data, the corresponding identifier is randomly assigned [15]. The conditional probability distribution of the latent variables z and c is

\[
q(a_n = l, d_n = g \mid \psi_n, v, e, a, z, \alpha, \beta, \eta) = \psi_n^f \times \frac{m_f^k + \alpha}{\sum_{j=1}^k (m_f^j + \alpha)} \times \prod_{m=1}^{M_{a,n,z_{n,m}=1}} \frac{w_k^{v_{n,m}} + \beta}{\sum_{v=1}^W (m_k^v + \beta)} \times \prod_{e=1}^{N_{n,d}} \frac{m_f^{c_{n,e}} + \eta}{\sum_{e=1}^E (m_f^{c_{n,e}} + \eta)} \quad (2)
\]

Among them, $\psi_n^f$ is the probability q (f|$\psi_n$) of sampling f from $\psi_n$, $m_f^k$ is the number of times that the word v is assigned to the topic k, both counts above exclude document n. For each word in the disease document, the conditional probability distribution of the corresponding identification variable y is

\[
q(z_{n,m} = 0 \mid v, e, a, z, \alpha, \beta, \eta) = \frac{m_{(n,m)}^{z=0} + \lambda}{\sum_{z=1}^1 (m_{n,m}^z + \lambda)} \times \frac{m_{z=0,(n,m)}^{x_{n,m}} + \beta}{\sum_{x=0}^Z (m_{x=0,n,m}^y + \beta)} \quad (3)
\]

Among them, $m_{n,m}^z$ is the number of words corresponding to the label y, $m_x^{z=0,(m,n)}$ is the number of occurrences of w in the word corresponding to the label 0, $m_{a,n,m,m}^x$ is the number of times the phrase v n,m is assigned the topic a n,m, and the above counts exclude the mth word in the nth document (Gupta and Awasthi 2010; Gupta et al. 2022; Khan et al. 2020).

\[
\theta_{f,k} = \frac{m_f^k + \alpha}{\sum_{j=1}^M (m_f^j + \alpha)} \quad (4)
\]

Among them, $m_f^l$ is the number of times the document with the situation topic f corresponding to the disease topic j.

$\varphi_{k,w}$ represents the probability that a certain disease topic generates a certain word:

\[
\Phi_{k,w} = \frac{m_f^k + \beta}{\sum_{j=1}^M (m_f^j + \beta)} \quad (5)
\]

Where $\varphi_{k,w}$ is the number of occurrences of word w in the document corresponding to disease topic k.

## 3.5 Drug recommendation

Suppose a set of test data sets are given, in which the corresponding drugs of patients are unknown. Then the conditional probability of the patient corresponding to any drug d can be obtained by formula (6).

\[
q(e|X, \psi) = \sum_{f=1}^F \sum_{l=1}^L \sigma_{f,l,e} \times \left( q_f \theta_{f,l} \prod_v (\pi_0 \theta_v^C + \pi_1 \varnothing_{l,e}) \right) \quad (6)
\]

## 4 EXPERIMENT AND RESULT ANALYSIS

This section describes in detail the datasets, metrics, benchmark methods, parameter settings and analysis of experimental results used in the experiments in this paper.

### 4.1 Experimental dataset

The data used in this experiment comes from the electronic medical record database of the inpatient department of a large tertiary hospital from 2015 to 2018 and has been desensitized. The data set was cleaned and deduplicated, and 158,556 complete electronic medical records were obtained, each of which included patients' complete diagnosis and treatment process records from discharge to admission. Logarithmic form of drug frequency statistics is shown in Table 1.

Table 1. Logarithmic form of drug frequency statistics.

| Serial | Medicine ID |
|--------|-------------|
| 0 | 1400 |
| 200 | 1200 |
| 400 | 1000 |
| 600 | 800 |
| 800 | 600 |
| 1000 | 400 |
| 1200 | 200 |

### 4.2 Experimental results

Table 2 shows the performance of different methods on the dataset, and each experimental result is obtained by 5-fold cross-validation. The subject word prior in the LLDA model is set to 0.01; the number of topics in Tag-LDA is set to 50; the subject word prior is set to 0.01, the vector dimension in CF is set to 30, and the number of similar documents is set to 40.

Table 2. Performance comparison of different methods.

| Metric | Freq | LLDA | MLDT | MLP | NTM | MLDA | MLDA-pure | MLDA-z | MLDA-c |
|--------|------|------|------|-----|-----|------|-----------|--------|--------|
| NDCG@20 | 0.5116 | 0.3113 | 0.7206 | 0.7283 | 0.7333 | 0.707 | 0.7144 | 0.7155 | 0.8155 |
| NDCG@30 | 0.5492 | 0.3432 | 0.779 | 0.789 | 0.7961 | 0.7679 | 0.7757 | 0.7771 | 0.8771 |
| NDCG@40 | 0.5779 | 0.3631 | 0.8125 | 0.825 | 0.8334 | 0.8057 | 0.8135 | 0.8149 | 0.9149 |
| P@20 | 0.4137 | 0.2524 | 0.6084 | 0.611 | 0.6182 | 0.5925 | 0.6022 | 0.6103 | 0.7103 |
| P@30 | 0.3484 | 0.2252 | 0.5121 | 0.5147 | 0.5215 | 0.5006 | 0.5079 | 0.5156 | 0.6156 |
| P@40 | 0.3075 | 0.2032 | 0.4469 | 0.4481 | 0.4545 | 0.4369 | 0.4426 | 0.4486 | 0.5486 |
| R@20 | 0.4374 | 0.2661 | 0.667 | 0.6777 | 0.6829 | 0.6539 | 0.6616 | 0.6624 | 0.7624 |
| R@30 | 0.4962 | 0.3213 | 0.7635 | 0.7788 | 0.7878 | 0.756 | 0.7647 | 0.7654 | 0.8654 |
| R@40 | 0.5521 | 0.3587 | 0.8239 | 0.8444 | 0.8559 | 0.8259 | 0.8341 | 0.8354 | 0.9354 |
| F@20 | 0.3978 | 0.2432 | 0.5933 | 0.5982 | 0.605 | 0.5797 | 0.5893 | 0.591 | 0.691 |
| F@30 | 0.3837 | 0.2398 | 0.571 | 0.576 | 0.584 | 0.5595 | 0.568 | 0.5723 | 0.6723 |
| F@40 | 0.3663 | 0.2276 | 0.5374 | 0.5412 | 0.5494 | 0.5268 | 0.5341 | 0.539 | 0.639 |

In the following, the parameter sensitivity analysis of the proposed model is carried out. Figure 2 shows the effect of the number of contextual topics on the model effect, where K = 400, adjusting different F values (Limbasiya et al. 2018; Soni and Singh 2022). Figure 3 with Table 3 shows the impact of the number of disease subjects on the model performance where F = 10 and change different K values. When the parameters change within an extensive range, the model effect is only 0.01. It fluctuates in the field, which confirms the excellent performance of the proposed method (Bhatt and Sharma 2022; Liu et al. 2022).

![](img/9eefc6d2972274efeb1680c6a31895e5_41_0.png)

Figure 2. Influence of context topic number.

![](img/9eefc6d2972274efeb1680c6a31895e5_41_1.png)

Figure 3. Influence of the number of situational themes and disease themes on the model effect.

### Table 3. Influence of disease topic number.

| Serial | NDCG@40 | Recall@40 |
|--------|---------|-----------|
| 0 | 0.705 | 0.73 |
| 5 | 0.715 | 0.735 |
| 10 | 0.71 | 0.713 |
| 15 | 0.7 | 0.732 |
| 20 | 0.68 | 0.73 |

## 5 CONCLUSION

In this paper, a context-aware-based drug recommendation model, Medicine-LDA, is proposed that utilized a general probabilistic framework to describe the diagnosis and treatment process in real-life scenarios. The model inferred the possible diseases of patients based on patient documents composed of laboratory abnormalities and medical texts and proposed the use of disease topics to describe the probability of patients suffering from different diseases. Finally, through experiments on a data set from a large tertiary hospital, it is shown that the model proposed in this paper outperforms the commonly used traditional machine learning models, topic models and collaborative filtering models in accuracy. The analysis of the results can obtain a series of valuable information, which confirms the excellent performance of the model and its value in practical application.

## REFERENCES

- Ahmed, T.I., Bhola, J., Shabaz, M., Singla, J., Rakhra, M., More, S. and Samori, I.A., 2022. Fuzzy logic-based systems for the diagnosis of chronic kidney disease. BioMed Research International, 2022.
- Al-Saffar, M. and Baiee, W., 2022, March. Survey on implicit feedbacks extraction based on yelp dataset using collaborative filtering. In 2022 Muthanna International Conference on Engineering Science and Technology (MICEST) (pp. 125-130). IEEE.
