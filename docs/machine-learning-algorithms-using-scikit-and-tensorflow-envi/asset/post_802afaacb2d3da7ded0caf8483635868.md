
## 3. PROPOSED METHOD

### 3.1 BERT Sentiment Analysis

BERT (Bidirectional Encoder Representations from Transformers). It is a Google-developed transformer-based machine learning approach for pre-training in natural language processing (NLP). When compared to frequently used heuristics, the design seeks to integrate numerous hidden layers of BERT in a way that enhances the accuracy of the Twitter sentiment analysis job. The average of the past four layers, which corresponds to a linear combination, is a common heuristic. Because tweets employ such a diverse range of languages, a fixed technique of layer combination, such as a linear combination, may not fully exploit BERT's capabilities. For instance, tweets including extraordinary words may help more from data which is available in the prior layers of BERT's character-based embeddings while more proper tweets may profit from the other layers. First chance to conquer this project is to consider the successive data stream between resulting layers through a repetitive unit. The gathering of various levels together could be helpful on the grounds that one bi-GRU's capacity might restrict its capacity to catch all of the data from the 12 layers. Thus, they isolated the work by utilizing various bi-GRUs and distributing gathered embeddings to them. To distinguish the best harmony between joining data across layers and the capacity of a solitary bi-GRU, the trial with various quantities of bi-GRUs. An illustration of the model engineering utilized. Figure 1 shows the flowchart of BERT Sentiment Analysis.

## 4. EXPERIMENTAL SETUP

First, we have downloaded the dataset IMDb dataset from Kaggle. Hugging Face's transformers library includes pre-trained BERT models and tokenizers. Glorot initialization is used to initialise dense layers, and a dropout rate of 0.5 is utilised. After every epoch, the Adam optimizer is multiplied by 0.9 with a starting learning rate of 1 to 5. Do fine-tuning on the whole BERT model in each iteration to balance the embeddings with the dataset. For all experiments, utilize a batch size of 64 and train for an aggregate of 15 epochs. A coarse grid search is used to choose the hyperparameters, although it is not comprehensive owing to computing resource constraints. The models are trained on a node with an NVIDIA GeForce GTX 1060 and an Intel Core i7 7th generation CPU using a single GPU. We have to follow the steps below:

- We have to import the downloaded dataset from my drive to Google Colab.
- Then tokenize the input into sub-tokens, then embed those sub-tokens
- After preprocessing the dataset have to split the dataset into training data (70%) and testing data (30%).
- BERT Sentiment Analysis is built to train and test the preprocessed dataset.
- We compared the output of our model by varying epoch values.
- Also, by altering the number of layers hidden we have compared the output of our model.
- For prediction and evaluating the model we compared the results of activation functions by varying layers and epochs.

## 5. RESULTS AND DISCUSSIONS

The IMDb reviews dataset was used in this thesis. There are a whole total of 50,000 reviews in all. The model's hyperparameters, such as batch size, were set at 128 with 5 epochs and a dropout of 0.25. Transformers picked ADAM as the optimizer for Bidirectional Encoder Representation. After multiple trials and comparisons of model accuracy, the hyperparameters were chosen. The model was also chosen after a series of experiments with diverse dropout rates. The accuracy of the model's predictions was used as a criterion to compare model performance. As the dataset grew larger, the models' accuracy improved. The training plot for training the model is shown below. The model's accuracy is 92.4 percent after this final training.

Figure 1. Flow chart of BERT sentiment analysis

![](img/20813928ec98c7f6fbdbab0d52bde2f1_289_0.png)

### 5.1 Prediction of Negative Sentiment

Figure 2 shows the prediction score of the negative sentence.

Figure 2. Prediction of negative sentiment

```
predict_sentiment(model, tokenizer, "This film is terrible")
0.007311545312404633
```

### 5.2 Prediction of Positive Sentiment

Figure 3 shows the prediction score of positive sentences.

Figure 3. Prediction of positive sentiment

```
predict_sentiment(model, tokenizer, "This film is great")
0.927232027053833
```

### 5.3 Prediction of Negative Sentiment in Sarcastic Comment

Figure 4 shows the Prediction of negative sentiment in sarcastic sentence.

Figure 4. Prediction of negative sentiment in sarcastic comment

```
predict_sentiment(model, tokenizer, "grr .. ready for school .. i hate uniforms ! ugh we need our real clothes !")
0.11376281827668217
```

### 5.4 Prediction of Positive Sentiment in Sarcastic Comment

Figure 5 shows the Prediction of positive sentiment in sarcastic comment.

Figure 5. Prediction of positive sentiment in sarcastic comment

```
predict_sentiment(model, tokenizer, "when people ask me stupid questions, it is my legal obligation to give a sarcastic remark.")
0.7934311032295227
```

Figure 6 shows the training accuracy and prediction accuracy in predicting the positive and negative sentences. The training result is given in Figure 7.

Figure 6. Training graph

![](img/20813928ec98c7f6fbdbab0d52bde2f1_291_0.png)

Table 1 provides the observation of the result obtained with the proposed model and Table 2 provides the comparison of the models with the other models.

Figure 7. Training result

Epoch: 01 | Epoch Time: 28m 44s Train Loss: 0.464 | Train Acc: 77.38% Val. Loss: 0.271 | Val. Acc: 88.47% Epoch: 02 | Epoch Time: 28m 36s Train Loss: 0.281 | Train Acc: 88.52% Val. Loss: 0.230 | Val. Acc: 90.57% Epoch: 03 | Epoch Time: 28m 32s Train Loss: 0.237 | Train Acc: 90.52% Val. Loss: 0.219 | Val. Acc: 91.41% Epoch: 04 | Epoch Time: 28m 35s Train Loss: 0.204 | Train Acc: 91.99% Val. Loss: 0.216 | Val. Acc: 91.80% Epoch: 05 | Epoch Time: 28m 34s Train Loss: 0.176 | Train Acc: 93.23% Val. Loss: 0.213 | Val. Acc: 91.66% Epoch: 06 | Epoch Time: 28m 34s Train Loss: 0.159 | Train Acc: 93.82% Val. Loss: 0.237 | Val. Acc: 91.64%

Table 1. Observation of the result

| Input | Predicted Range [0-1] | Inference |
|---|---|---|
| This film is terrible | 0.007 | NEGATIVE |
| This film is great | 0.9272 | POSITIVE |
| Get ready for school . . I hate uniform !! ugh we need our real clothes | 0.1137 | NEGATIVE |
| When people ask me stupid questions, it is my legal obligation to give a sarcastic remark | 0.7934 | POSITIVE |

Table 2. Comparison of results with other models

| | Method | Acc | Author |
|---|---|---|---|
| Cross-lingual | Ensemble | 81.00% | Wan,X |
| | Co-Train | 81.30% | Wan,X |
| | CLMM | 83.02% | Mengi |
| Lexical Based | Corpus | 74.00% | Turkey |
| Cross- Domain | Active Learning | 80.00%(avg) | Li, S |
| | Thesaurus | 80.00%(avg) | Bollegala |
| | SFA | 80.00%(avg) | Pan S J |
| Machine Learning | SVM | 86.40% | Pang,Lee |
| | Co-Training SVM | 82.52% | Liu |
| | Deep learning (LSTM) | 85.29% | Richard |
| | Proposed Architecture | 91.64% | |

## 6. CONCLUSION AND FUTURE SCOPE

A sentiment analysis by using Bidirectional Encoder Representation from Transformers is proposed. The proposed methodology is having very low computational time which makes it a lightweight algorithm. The proposed fine-tuning framework can be generalized to solve transfer learning problems. The achieved accuracy is 91.64% with a training set consisting of 50,000 reviews. From this, the positive or negative emotion of the person which has a directly proportional relationship with the mental stress of the person are identified. In the future, the twitter data collection tool can be used to extract the comments and conversations by a specific target to further the effectiveness and track a target person's mental state continuously for monitoring. This technology can also be used in other social media outlets for accurate tracking. This model also can be deployed in mobile using TensorFlow.js. The time taken for processing was suitable for real time processing.

## REFERENCES

Adnan, N. (2012). University students stress level and brainwave balancing index: Comparison between early and end of study semester. In Research and Development (SCOReD) 2012 IEEE Student Conference on. IEEE.

Akbik, A., Bergmann, T., Blythe, D., Rasul, K., Schweter, S., & Vollgraf, R. (2019). An easy-to-use framework for state-of-the-art NLP. Academic Press.

Ding, Y., Chen, X., Fu, Q., & Zhong, S. (2020). A Depression Recognition Method for College Students Using Deep Integrated Support Vector Algorithm. IEEE Access : Practical Innovations, Open Solutions, 8, 75616–75629. doi:10.1109/ACCESS.2020.2987523

Greco, A., Valenza, G., Lanata, A., Scilingo, E. P., & Citi, L. (2016). A Convex Optimization Approach to Electrodermal Activity Processing. IEEE Transactions on Biomedical Engineering, 63(4), 1. doi:10.1109/TBME.2015.2474131 PMID:26336110

Jawahar, G., Sagot, B., & Seddah, D. (2019). What does BERT learn about the structure of language. Proceedings of the 57th Annual Meeting of the Association for Computational Linguistics, 3651–3657. 10.18653/v1/P19-1356

Kharde, V., & Sonawane, S. (2016). Sentiment Analysis of Twitter Data: A Survey of Techniques. International Journal of Computer Applications, 139(11), 5–15. doi:10.5120/ijca2016908625

Meng, X. (2012). Cross-lingual mixture model for sentiment classification. Proceedings of the 50th Annual Meeting of the Association for Computational Linguistics: Long Papers-Volume 1.

Subhani, A. R., Mumtaz, W., Saad, M. N. B. M., Kamel, N., & Malik, A. S. (2017). Machine Learning Framework for the Detection of Mental Stress at Multiple Levels. IEEE Access : Practical Innovations, Open Solutions, 5, 13545–13556. doi:10.1109/ACCESS.2017.2723622

Talaat, A. S. (2023). Sentiment analysis classification system using hybrid BERT models. Journal of Big Data, 10(1), 110. doi:10.1186/s40537-023-00781-w

Wan, X. (2012). A Comparative Study of Cross-Lingual Sentiment Classification. In Proceedings of the IEEE/WIC/ACM International Joint Conferences on Web Intelligence and Intelligent Agent Technology-Volume 1 (pp. 24-31). 10.1109/WI-IAT.2012.54
