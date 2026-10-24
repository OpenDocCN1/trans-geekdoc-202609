
| Fair learning methods | Preprocessing | Optimization at training | Postprocessing |
|---|---|---|---|
| Key ideas | Learning feature representation to mitigate the impact of sensitive attributes | Using additional constraints in the objective of original mining tasks | Modifying thresholds of learned models in order to satisfy fairness constraints |
| Pros | (1) Can be used for any downstream task<br>(2) No need to modify classifier<br>(3) No need to access sensitive attributes at test time | (1) Relatively good performance<br>(2) Flexible on tradeoff between accuracy and fairness measures<br>(3) No need to access sensitive attributes at test time | (1) Can be applied after any classifiers<br>(2) Relatively good performance<br>(3) No need to modify classifier |
| Cons | (1) Only capable of optimizing statistical parity and individual fairness<br>(2) Relatively lower performance | (1) Task specific solver<br>(2) Need to modify classifier (may not be feasible) | (1) Need to access the sensitive attribute at test time<br>(2) No explicit accuracy and fairness tradeoff |

itself, both the theoretical and experimental tradeoff between utilities and individual or group fairness is worth further studying.

### Interpretability.

Most of the existing data mining and machine learning methods are “black boxes” and thus are hard for the end users (who are often not data mining experts) to understand the mining process or the results. The lack of interpretability and transparency in a data mining model and system will in turn cause trust, safety, and contestability issues.

### Example 12.9.

The AI-aided diagnosis of Alzheimer’s disease⁶ via patients’ word usage or brain MRI image has received extensive interest in data mining research. However, if the model can not provide human (doctor) interpretable predictions, the results will face trust and reliability issues. In another application, the lack of contestability has already led to significant criticism of proprietary recidivism predictors such as COMPAS, because it fails to let people appeal these decisions.⁷

In Chapter 7, we have learned some basic techniques to interpret classification. Beyond that, many interpretable data mining methods have been developed. To name a few, some works use summary statistics for each feature as interpretation; some methods visualize the feature summary statistics as intuitive interpretation; some methods aim to explore self-interpretable components of the models for interpretation, such as the weights in linear models or the learned tree structure of decision trees; and other methods focus on identifying key data points (both existing and newly created samples) to make a model interpretable.

### Robustness.

Another important aspect is the robustness of data mining models. Generally speaking, a robust data mining model should satisfy the condition that the test results are consistent with training results, or the test results stay stable with unintentionally inserted noises and intentional adversarial attacks.

![](img/90c930779c8f928df6ff4481fc59f9a3_681_0.png)

FIGURE 12.12
The taxonomy of adversarial attacks.

### Example 12.10.

One of the most well-known examples of robustness is the image classification by Convolutional Neural Networks (CNNs). Researchers have found that slight modifications that are imperceptible to the human eyes (e.g., a few additional darker pixels inserted in an image) may cause a CNN model to produce drastically different classification results.

The taxonomy of representative adversarial attacks is shown in Fig. 12.12, based on four criteria (i.e., adversarial falsification, adversary’s knowledge, adversarial specificity, and attack frequency). Common defend strategies can be divided as _reactive_ methods and _proactive_ methods. Reactive methods detect adversarial examples after data mining models have been built, whereas proactive methods try to make mining models more robust before attackers generate adversarial examples. Representative reactive approaches include adversarial detection, input reconstruction, and network verification; representative proactive approaches include network distillation, adversarial (re)training, and classifier robustifying. Besides adversarial attacks and defense, other robustness studies focus on the stability of the model performance. For example, an interesting method for studying the model robustness is through a game. Considering a classifier, the goal of designing a robust classifier through the game is to minimize the loss while choosing a distribution of test data to maximize the expected loss given the knowledge of this classifier.

## Bibliographic notes

Calmon et al. [CWV⁺17] develop a convex optimization method for learning a data transformation in order to mitigate discrimination, limit distortion in individual data samples, and preserve utility. Gordaliza et al. [GDBFL19] try to detect when a binary classification rule lacks fairness and to fight against the potential discrimination by two fairness definitions (i.e., disparate impact and balanced error rate). Zemel et al. [ZWS⁺13] develop an optimization method for maintaining group fairness and finding a good representation for obfuscating the data. Lum et al. build a statistical framework for removing the sensitive information in the features. Calders, Kamiran, and Pechenizkiy [CKP09] develop an accurate model for which the predictions are independent from a given binary (sensitive) attribute for ensuring individual fairness. Kang et al. [KHMT20] define individual fairness for graph mining and develop debiased approaches for tackling fairness problem on graph mining tasks.

Molnar comprehensively summarizes the fundamental interpretable machine learning approaches [Mol20]. Samek et al. [SWM17] propose two methods to explain predictions of deep learning models. One method computes the sensitivity of the prediction with respect to changes in the input, and the other decomposes the decision in terms of the input variables. Lundberg et al. [LNV+18] explore an explainable machine learning approach for the prevention of hypoxaemia during surgery, which draws extensive attention in both machine learning and bioinformatics domains. Holzinger [Hol18] comprehensively elaborates various explainable machine learning and points out several future directions.

Ren et al. [RZQL20] survey the recent advances in adversarial attacks and defense approaches comprehensively. Papernot et al. use network distillation to defend deep neural networks against adversarial examples [PMW+16]. Goodfellow et al. [GSS14] and Huang et al. [HXSS15] propose to include adversarial examples in the training stage and generate adversarial examples in every step of training to inject them into the training set. Zugner et al. [ZAG18] introduce the adversarial attack problem on graphs, which focuses on the training stage of Graph Convolutional Networks. Bagnell et al. develop a wrapper framework around a broad class of supervised learning algorithms to guarantee the robust behavior under changes in the input distribution [Bag05].

## 12.4.4 Data mining for social good

In recent years, data mining techniques have been applied to various settings with significant societal impacts, under an umbrella term “data mining for social good.” Let us look at an example of the lead water pipe detection project.

### Example 12.11.

Due to the corrosion of lead water pipes, Flint’s drinking water in Michigan was contaminated seriously, with significant consequences to public health. Since most of the records of water pipe services were incomplete or even lost, city officials were uncertain about the locations of lead water pipes. The ActiveRemediation project, led by a group of researchers at the University of Michigan, adopts various machine learning and data mining techniques to guide the pipe replacement procedure. For instance, it combines XGBoost (an ensemble technique introduced in Chapter 6) with a hierarchical Bayesian spatial model to estimate the probability that a pipe contains hazardous materials. Furthermore, active learning technique (introduced in Chapter 7) is used to identify homes for inspection and to guide the data collection process. Since its first deployment in 2016, the ActiveRemediation project has achieved an impressive accuracy of 70%, and it has successfully replaced 6228 pipes made of hazardous metals through 2017.

Numerous efforts have been made by leveraging data mining techniques to make positive societal impacts on a multitude of applications, ranging from education, public health, combating information manipulation, social care and urban planning, and public safety, to transportation (see Table 12.4 for a summary). For example, various data mining models (such as Random Forests and Adaboost) have been used to identify students who need intervention to graduate high school on time; a deep learning approach called EpiDeep has been developed to predict the future trend of the epidemic, with improved prediction accuracy and interpretability; the SVM classifier with RBF kernel function has been
