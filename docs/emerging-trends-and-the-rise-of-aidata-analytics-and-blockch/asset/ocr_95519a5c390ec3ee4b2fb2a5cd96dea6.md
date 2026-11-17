![](bbox=[0.1, 0.12, 0.9, 0.48])

were LSTM, GRU and CNN. Various variants of deep learning models were investigated in the study. For the LSTM model, there were four variants, including simple LSTM, LSTM with GloVe embeddings, Bi-directional LSTM and LSTM with an attention layer. Similarly, four variants of GRU were used in the study, including simple GRU, GRU with GloVe embeddings, Bi-directional GRU and GRU with an attention layer. For CNN, we have used simple CNN with random embeddings and CNN with GloVe embeddings. Bi-directional CNN and CNN with an attention layer is not possible. The results were evaluated using measures such as Precision, Recall, Specificity, F1-Score and AUC-ROC scores. The results obtained after text-based affective computing is then compared with the earlier proposed methods.

For image-based affective computing, the data was extracted from Instagram using API. The training data was generated using the hashtags given in Table 1. We have applied three deep learning models on the image data, including a custom CNN model, transfer learning model with pre-trained VGG-19 model and pre-trained ResNet-18 Model. The results in the image were also evaluated using metrics such as AUC-ROC score and confusion matrix. The results obtained are presented with a visualization tool called tensorboard embedding projector visualization tool. The tool provides various features such as PCA analysis and t-SNE (Bunte et al., 2012) visualization with a graphical interface.

# 4. Methodology and models

This section presents the methodology used in the study. The study presents the affective computing for both text and image data which are described in this section.

# 4.1 Affective computing for text data

The affective computing for text data was analyzed with three deep learning models, namely LSTM, GRU and CNN. We have also used various variants of three deep learning models. For