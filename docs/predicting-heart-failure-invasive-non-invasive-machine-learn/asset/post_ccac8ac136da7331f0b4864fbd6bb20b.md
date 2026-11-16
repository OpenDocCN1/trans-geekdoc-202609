

![](img/721c7a2c71f4dc63a8585e2ef46838f7_161_0.png)

Figure 6.4 Comparing ML and deep learning.

By providing an ANN with a large training data set, these weights are fine-tuned, and the ANN is optimized to better establish the relationship between input and output [7]. ANNs typically consist of three layers – input, hidden, and output layer – and process inputs in a forward direction to solve problems related to tabular, image, or textual data [25]. ANNs can use many hidden layers to produce increasingly abstracted and non-linear representations of underlying data [1].

When a looping constraint is applied to a hidden layer of an ANN, it becomes an RNN [7]. RNNs are particularly well suited to processing sequential data, such as speech and language.

CNNs are fully connected neural networks that have learnable weights and biases. They employ kernels for automatic feature extraction which are a series of convolutional operations which progressively extract relevant features. CNNs are particularly useful in processing large and complex data sets such as imaging data [25]. Traditional ML algorithms struggle with imaging data as they are highly dimensional, and it is extremely difficult to assign individual weights for each feature.

For example, an image with a pixel size of 750 × 750 and three channels has nearly 2 million features (750 × 750 × 3). Additionally, a single-pixel does not carry enough useful information, but rather a patch of pixels will need to be analyzed [1]. Convolutional layers in a CNN attempt to overcome these difficulties. Each convolutional layer uses a set of filters that forms a small grid of weights and performs a weighted sum nonlinear transformation. The same filter is applied to all possible locations in the whole input. In this way, the number of weights to train is significantly reduced [7].

### 6.2.3.1 Examples of Deep Learning in Cardiology

Deep learning has been widely studied and applied to various aspects of cardiovascular medicine. One example is its application to ECGs. ECGs are routinely used in the evaluation of patients, and are relatively low-cost and widely available. Deep learning algorithms have been developed to detect structural heart disease, arrhythmias, phenotypic patterns and electrolyte disturbances [11, 29–34]. For example, CNN-derived ML algorithms applied to ECGs have been validated to detect LV systolic dysfunction [30, 34]. One study trained a CNN algorithm to detect LV dysfunction using paired 12-lead ECG and echocardiogram data from 44,959 patients [30]. The algorithm was then tested on an independent sample of 52,870 patients, and was found to have a sensitivity, specificity, and accuracy of 93%, 86.3%, and 85.7%, respectively [30]. Another example is a retrospective study which used a CNN algorithm to detect LV hypertrophy in 21,286 patients in two hospitals who underwent 12-lead ECG and echocardiography 4 weeks apart [35]. The AUCs of the AI ECG algorithm were 0.880 (95% CI: 0.877–0.883) and 0.868 (95% CI: 0.865–0.871) in the internal and external validation cohorts respectively, when compared with echocardiography [35]. Unsupervised learning CNN-based ML algorithms have been validated to detect and predict arrhythmias. A recent study developed a CNN-based ML algorithm from 180,922 patients to predict the probability of developing atrial fibrillation from normal sinus rhythm by studying temporal ECGs from these patients [31]. The study split the patients into a training data set (126,526 patients with 454,789 ECGs), internal validation data set (18,116 patients with 64,340 ECGs), and testing data set (36,280 patients with 130,802 ECGs). The algorithm had an AUC of 0.87 (95% CI: 0.86–0.88), a sensitivity of 79%, and a specificity of 79.5% [31, 36].

CNN has also been validated in detecting obstructive CAD from myocardial perfusion imaging (MPI), compared with total perfusion deficit (TPD). The study included 1638 patients undergoing stress 99mTc-sestamibi or tetrofosmin MPI in nine sites who also underwent invasive coronary angiogram within 6 months [37]. The CNN algorithm was trained using raw and quantified polar maps to evaluate and predict obstructive CAD using stratified 10-fold cross-validation [37]. The AUC for disease prediction by the CNN was higher than for TPD (per patient: 0.80 vs 0.78; per vessel: 0.76 vs 0.73; p < 0.01) [37]. Moreover, the time needed for the evaluation of a new patient with the pre-trained model was < 1 second, even without the dedicated graphics board used during the training of the system [37]

### 6.2.4 Natural Language Processing

Most information in electronic health records is unstructured and in free text. Recent technological advances have allowed narrative text to be extracted using a technique called natural language processing (NLP), which converts unstructured text into a structured form [38]. NLP is a multistep process with the first and most important step being lexical analysis. There are various techniques which can be employed in lexical analysis, and these include part of speech (POS) tagging, hidden Markov model (HMM), named entity recognition (NER) and parsing or syntactic analysis (PSA) [38]. In POS tagging, each word is tagged to a corresponding category of words that share grammatical properties. HMM remembers the sequence of words in a sentence and tagged as nouns, verbs, and determiners. In NER, words are tagged by the type of entity the word represents. These entities can be persons, companies, times, or locations. PSA analyzes the grammar of the text and the way the words are arranged. It uses predefined grammatical rules to test whether a sentence string conforms to these set rules [38]. Examples of its current applications in cardiology include extracting information from clinical notes, radiology reports, and pathology reports.

## 6.3 Steps in Building an AI Algorithm

Building a clinically meaningful and effective ML algorithm is a multifaceted, complex process, and requires the input of a multidisciplinary team with diverse skills and talents. Most notably, clinicians are at the forefront of delivering healthcare and are most in tune with the problems arising in clinical care. However, clinicians often lack the technical capabilities to develop and test ML algorithms and thus require data scientists. The process can be broken down into six steps (Figure 6.6) [1]. The first is identifying the problem and often requires multidisciplinary input from clinicians, data scientists, data engineers, patients, and other stakeholders [2]. The second is collecting the appropriate data with features and labels of interest; this is often the most time-consuming and expensive aspect. The third is preparing the data through a combination of feature selection and feature engineering [4]. This step is closely linked with the next step, as the type of ML algorithms that can be used is often dictated by the type, quality, and preparation of the data. The fifth step involves developing and building the ML algorithm using a training data set. The final step is validating the ML algorithm through a process of internal and external validation using independent and separate data sets [7].

## 6.4 Limitations, Challenges, and Opportunities

It is important to appreciate the challenges associated with AI, and these can be broadly divided into limitations relating to existing research, limitations inherent with AI technology, and challenges in clinical translation.

### 6.4.1 Limitations of Existing Studies

Most studies thus far employ narrow AI and apply ML algorithms to predefined and preselected variables with parameter adjustments in testing cohorts to obtain a good

![](img/721c7a2c71f4dc63a8585e2ef46838f7_164_0.png)

**Figure 6.6** Steps in building AI algorithms in cardiology.

performance. Hence, the bulk of ML algorithms have been studied on retrospectively collected and curated data. The major limitation with this approach is the obvious risk of developing models that are overfitted to the target data that do not generalize well to previously unseen external data. There are also the inherent biases which are inadvertently introduced into algorithms that are built and validated solely on retrospective, single-center data. ML algorithms require large data sets, and therefore subtle biases are introduced, such as a lack of diversity leading to unintended downstream consequences of the algorithms being inherently skewed to identify the dominant types of patients contributing to the model development. Another related limitation is the lack of existing frameworks and guidelines in conducting AI research. This lack of data set, methodological, and reporting standardization leads to an inability to comprehensively evaluate for methodological bias in analyses, and often masks biases. Moreover, this makes institutional cross-collaboration more difficult.

The natural next step is to study these ML algorithms on external data sets, not involved in model development, in a multicenter prospective study design. These future prospective studies will need to evaluate patient outcomes and treatment pathways.

### 6.4.2 Pitfalls with the Technology

As with all technologies, AI remains susceptible to privacy, security, and data breach concerns. Patient data used for algorithm development need to remain de-identified and handled with care. Another unique limitation is the black-box phenomenon, which a lot of ML algorithms suffer from. This refers to the notion that certain ML

