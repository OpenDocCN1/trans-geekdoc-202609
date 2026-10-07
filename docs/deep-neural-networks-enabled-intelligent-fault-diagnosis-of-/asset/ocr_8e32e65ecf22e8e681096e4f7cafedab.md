116 Deep Neural Networks-Enabled Intelligent Fault Diagnosis of Mechanical Systems

to the target network and other parameters were fine-tuned with a small amount of target data. Pre-trained deep neural networks on ImageNet were used in (Sharaf 2018) and were fine-tuned with limited target to adapt the domain of engineering applications. Ensemble techniques and multi-channel signals were used in (He et al. 2020) to initialize the target network which was fine-tuned by a few samples from the target domain. Two-dimensional images, such as gray images (Wang et al. 2021), time-frequency images (Wang et al. 2019), and thermal images (Shao et al. 2020), were used to pre-train the specific-designed networks, which were transferred to the tasks via fine-tuning.

Qureshi et al. (2017) pre-trained nine sparse autoencoders on one wind farm, and predictions on one wind farm were made by fine-tuning the pre-trained networks. (Zhong, Fu, and Lin 2019) trained a CNN on normal samples and then replaced Fc layers with support vector machine as the target model. (Han et al. 2019) discussed and compared three fine-tuning strategies: only fine-tuning the classifier, finetuning the feature descriptor, and fine-tuning both the feature descriptor and the classifier for diagnosing unseen machine conditions.

# Instanced-BUDTL for Intelligent Fault Diagnosis

# Basic Concepts

Instanced-UDLTL refers to reweight instances in the source domain to assist the classifier to predict labels or use statistics to help align the target domain, such as TrAdaBoost (Dai et al. 2007) and adaptive batch normalization (AdaBN) (Li et al. 2016). In this section, we use AdaBN to improve one of instanced-based BUDTL methods, which do not require labels from the target domain.

BN, can be used to avoid the issue of the internal covariate shifting, which is one of the most important techniques. BN can provide much faster training speed since it makes the input distribution more stable. It is worth mentioning that BN layers are only updated in the training procedure and the global statistics of training samples are used to normalize test samples during the test procedure.

AdaBN, which is a simple and parameter-free technique for the domain shift problem, was proposed in (Li et al. 2016) to enhance the generalization ability. The main idea of AdaBN is that the global statistics of each BN layer are replaced with statistics in the target domain during the test phase. In our AdaBN realization, we provide two updating strategies to fine-tune statistics of BN layers using target data, including updating each batch and the whole data. In this test, we update statistics of BN layers via batch consuming the memory limit.

# Applications to IFD

Xiao et al. (2019) used TrAdaBoost to enhance the diagnostic capability of the fault classifier by adjusting the weight factor of each training sample. Zhang et al. (2017b) used AdaBN to improve the domain adaptation ability of the model by ensuring that each layer receives data from a similar distribution.