
# Naïve Bayes (NB) Algorithm

Naïve Bayes (NB) algorithm is a probabilistic classification algorithm based on Bayes’ theorem. The assumption of Naïve Bayes includes independence of features, where features do not interact with each other while predicting the classification results [[16](#ch17.xhtml#r183)]. The NB classifier is a supervised learning algorithm and can be efficiently trained using small amount of data. Since the variables or the features are assumed to be independent, thus only the calculation of the variances of each class variable is required instead of calculating the values of the entire covariance matrix. Naïve Bayes algorithm is remarkable in terms of performance because it can train on limited data as well [[17](#ch17.xhtml#r184)–[21](#ch17.xhtml#r188)]. Equation (7.1) describes the Bayes Rule below.

```
$P\left( {c_{i}~\text{|}~D} \right) = \frac{P\left( c_{i} \right)P\text{(}D~\text{|}~c_{i})}{P\left( D \right)}$ (7.1)
```

where $P\left( C_{i} \right) = P(C = c_{i}) = \frac{N_{i}}{N}$

where `P(C[i])` is the ratio of number of training samples of class `C[i]` in dataset (i.e. `N[i]`) over total number of samples in the dataset (i.e. `N`)

Although Naïve Bayes is based on the unrealistic assumption of independence between different features but still it delivers reasonable performance for many classification tasks. It is simple and elementary to implement. Therefore, it has been used by the researchers in different tasks [[22](#ch17.xhtml#r189), [23](#ch17.xhtml#r190)]. In [[24](#ch17.xhtml#r191)], the Naïve Bayes classifier performed exceptionally well where the probabilities computed by the model were not important. It is used for different classification applications like spam filtering [[25](#ch17.xhtml#r192)] in emails, spam categorization, and categorization of web content.

## 7.2.2 Long Short-Term Memory Model

Long short-term memory (LSTM) was proposed in [[26](#ch17.xhtml#r193)] which has proven to be extremely powerful in the past for learning sequences over standard recurrent neural networks (RNNs). RNNs are basically neural networks unfolded over multiple time steps and thus can process sequential data such as time series and sentences. With each time step having hidden state, processing inputs from the previous hidden state and current inputs. The disadvantages of RNNs are vanishing and exploding gradients. The transition functions of the LSTM [[26](#ch17.xhtml#r193)] are defined as per Equation (7.2)–(7.7):

```
i[t] = σ(W[i].[h[t−1],x[t]]+b[i]) (7.2)
f[t] = σ(W[f].[h[t−1],x[t]]+b[f]) (7.3)
o[t] = σ(W[o].[h[t−1],x[t]]+b[o]) (7.4)
c[t] = f[t]⊙ c[t−1] + i[t] ⊙ q[t] (7.5)
h[t] = o[t] ⊙ tanh(c[t]) (7.6)
```

In the above equations, ⊙ signifies the element wise multiplication operation. The notations are: current time step `x[t]`, old hidden state `h[t-1]`, the input gate `i[t]`, the forget gate `f[t]`, and the output gate `o[t]`. Weights are denoted by `W[o]`, `W[q]`, and `W[i]` which are trainable parameters with respect to different gates. Previous and current memory cell are denoted by `c[t-1]` and `c[t]`, respectively. The current hidden state `h[t]` is modified using `c[t]` and is collectively decided by these gates. [Figure 7.1](#ch17.xhtml#f40) depicts the LSTM cell diagram.

![Figure 7.1 Architecture of LSTM cell.](html/images/9781032942346_C007_001.jpg)

**Figure 7.1** Architecture of LSTM cell.

## 7.2.3 Bidirectional Long Short-Term Memory (Bi-LSTM) Model

Bidirectional LSTM (Bi-LSTM) models are helpful in extracting more contextual information [[27](#ch17.xhtml#r194)]. The data processing is performed in the backward and forward direction simultaneously [[28](#ch17.xhtml#r195)] and the LSTM outputs are merged using the sum statistic [[29](#ch17.xhtml#r196)].

Bi-LSTM models serve as state-of-the-art models for classifying the sequential data into multiple classes and have been used extensively for speech recognition [[30](#ch17.xhtml#r197), [31](#ch17.xhtml#r198), [32](#ch17.xhtml#r199), [33](#ch17.xhtml#r200), [34](#ch17.xhtml#r201)]. The text in the pages of the PDF documents is also a sequence of words and multiclass criteria also exist as the documents are to be classified into the respective language class. Therefore, Bi-LSTM model is applied for the classification task in this paper.

# 7.3 Methodology

## 7.3.1 Dataset Description

Dataset comprises pdf files from three languages, viz. English, Slovakian, and Czech language. Data cleaning and preprocessing is performed over the sentences. `Count Vectorizer` is used to encode set of sequences. Dataset is split as: 80% of data is used for training and remaining 20% is used in testing. Furthermore, cross validation is used to avoid the overfitting to a single sample set. Data are trained for 100 epochs which is selected by using grid search methodology. [Table 7.1](#ch17.xhtml#t9) shows the dataset details.

**Table 7.1** Dataset samples

| Class | Number of samples |
| --- | --- |
| English | 5000 |
| Slovakian | 5000 |
| Czech | 5000 |

## 7.3.2 Feature Extraction

Before starting with the analysis, firstly the extraction of the text from the PDF document file is performed. `Tesseract OCR` system is used to extract the content from a document page if the page is present in the form of a raster image [[15](#ch17.xhtml#r182)]. After extracting, the text passes through document classification engine, explained in detail in Section 7.3.3.

## 7.3.3 Document Classification Engine

The document classification engine can assist humans in the separation of documents of different languages into different folders. This prevents the documents from getting lost if they are not properly labeled and accelerates the process of usage of these documents for proper application. The proposed classification engine can also ingest and classify the PDF documents containing the data in the form of images. Document classification engine serves as a prerequisite to classify documents to leverage extraction of information from a variety of PDF documents.

[Figure 7.2](#ch17.xhtml#f41) depicts methodological steps for carrying out classification. Initially, preprocessing is done, which includes removal of stop words using `NLTK` library in Python. Further missing values, interpolation, and stemming are performed in the dataset. Later on feature selection is performed.

![Figure 7.2 Methodological steps.](html/images/9781032942346_C007_002.jpg)

**Figure 7.2** Methodological steps.

Since most of the text was obtained from the image format pages of the PDF by applying the OCR on the raster scanned documents with noise, many out-of-vocabulary words were found in the extracted data. Such problem can be resolved either by running a named entity recognition (NER) [[35](#ch17.xhtml#r202)] system or by the use of stemming and multiple regular expressions [[36](#ch17.xhtml#r203)]. In this work, we have used stemming as a preprocessing step.

# 7.4 Experiments and Results

## 7.4.1 Experimental Details

For carrying out experiments, we have utilized `Spyder 3.2.8` notebook with Python version 3.6.5. The experiments are executed on Windows 11, 64-bit OS system having 16GB RAM, with Intel(R) i5 CPU @ 2.40 GHz. Python `Tensorflow` and `Keras API` are used primarily to implement various algorithms in this work.

## 7.4.2 Baseline Models

### 7.4.2.1 DNN: Deep Neural Network

Architectural details of DNN are defined in [Figure 7.3](#ch17.xhtml#f42).

![Figure 7.3 DNN architecture.](html/images/9781032942346_C007_003.jpg)

**Figure 7.3** DNN architecture.

### 7.4.2.2 LSTM
