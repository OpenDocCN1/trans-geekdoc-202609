# 3. PROPOSED METHOD

# 3.1 Bert Sentimental Analysis

BERT (Bidirectional Encoder Representations from Transformers). It is a Google-developed transformer-based machine learning approach for pre-training in natural language processing (NLP). When compared to frequently used heuristics, the design seeks to integrate numerous hidden layers of BERT in a way that enhances the accuracy of the Twitter sentiment analysis job. The average of the past four layers, which corresponds to a linear combination, is a common heuristic. Because tweets employ such a diverse range of languages, a fixed technique of layer combination, such as a linear combination, may not fully exploit BERT's capabilities. For instance, tweets including extraordinary words may help more from data which is available in the prior layers of BERT's character-based embeddings while more proper tweets may profit from the other layers. First chance to conquer this project is to consider the successive data stream between resulting layers through a repetitive unit. The gathering of various levels together could be helpful on the grounds that one biGRU's capacity might restrict its capacity to catch all of the data from the 12 layers. Thus, the isolated the work by utilizing various bi-GRUs and distributing gathered embeddings to them. To distinguish the best harmony between joining data across layers and the capacity of a solitary bi- GRU, the trial with various quantities of bi-GRUs. An illustration of the model engineering utilized. Figure 1 shows the flowchart of Bert Sentimental Analysis.

# 4. EXPERIMENTAL SETUP

First, we have downloaded the dataset IMDb dataset from Kaggle. Hugging Face's transformers library includes pre-trained BERT models and tokenizers. Glorot initialization is used to initialise dense layers, and a dropout rate of 0.5 is utilised. After every epoch, the Adam optimizer is multiplied by 0.9 with a starting learning rate of 1 to 5. Do fine-tuning on the whole BERT model in each iteration to balance the embeddings with the dataset. For all preliminaries, utilize a group size of 64 and train for an aggregate of 15 ages. A coarse grid search is used to choose the hyperparameters, although it is not comprehensive owing to computing resource constraints. The models are trained on a node with an NVIDIA GeForce GTX 1060 and an Intel Core i7 7th generation CPU using a single GPU. We have to follow the steps below:

+   - We have to import the downloaded dataset from my drive to google colab.
+   - Then tokenize the input into sub-tokens, then embed those sub-tokens
+   - After preprocessing the dataset have to split the dataset into training data (70%) and testing data (30%).
+   - BERT Sentimental Analysis is built to train and test the preprocessed dataset.
+   - We compared the output of our model by varying epoch values.
+   - Also, by altering the number of layers hidden we have compared the output of our model.
+   - For prediction and evaluating the model we compared the results of activation functions by varying layers and epochs.