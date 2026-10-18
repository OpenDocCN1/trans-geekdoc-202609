
# Extractive Summarization

## Attention Mechanisms

○ Self-attention, used in models like BERT and transformer, assigns weights to each word in a sentence based on its importance. These weights can then be combined to score the overall sentence.

○ Hierarchical attention networks, on the other hand, apply attention at both the word and sentence levels to capture context and importance.

## Embeddings

• Embeddings: Following are some common types of embeddings used in NLP:

○ Word embeddings (for example, `word2vec`, `GloVe`): These convert individual words into dense vectors, which are numerical representations that capture the meaning of the word. Sentence embeddings can be formed by either averaging or concatenating word embeddings.

○ Sentence embeddings (for example, universal sentence encoder): Pre-trained models encode entire sentences into fixed-length vectors that capture the underlying semantics of the sentence.

## Supervised Learning

• Supervised learning: Supervised learning involves two main techniques for sentence classification:

○ One approach is to label sentences as important or non-important in a training dataset and then train a classifier (such as `SVM` or `logistic regression`) to predict sentence importance.

○ The second approach is to use deep learning models such as `CNN` or recurrent neural networks (`RNN`) that are trained using labeled data to score sentences.

## Content-based Features

• Content-based features: Certain content-based features need to be considered when it comes to extractive summarization:

○ Positional information: These include the positional information of sentences, where those at the beginning or end of a document may hold more importance.

○ Length of a sentence: The length of a sentence also plays a role, as longer sentences are likely to contain more information.

○ Named entities and keywords: Sentences that include named entities (such as names or locations) or relevant keywords are also important.

However, it is important to keep in mind that while extractive summarization aims to maintain the original text, it may still suffer from issues such as redundancy and a lack of coherence.

| Note: Extractive summarization aims to preserve the original wording but may suffer from redundancy and lack of coherence. |

| --- |

## Implementing Extractive Summarization using PyTorch

In this section, we will learn how to implement extractive summarization using PyTorch:

• Model architecture: The task at hand involves giving the model a pair of inputs, namely a sentence and a document. The model then predicts a relevance score, which is denoted as `y`. In order to process the textual input, we require suitable representations. To achieve this, one can choose any language model from the `transformers` library. In this particular scenario, we will be using `sentence-transformers`, which is essentially a BERT-based model that has been fine-tuned specifically for the purpose of extracting semantically meaningful sentence embeddings:

![](images/Figure_9.1.png)

```
from transformers import AutoTokenizer, AutoModel

sentence_model = "sentence-transformers/paraphrase-MiniLM-L3-v2"

tokenizer = AutoTokenizer.from_Pre-trained(sentence_model)

# Derive mean pooling for sentence model

def mean_pooling(model_input, attention_mask_input):

token_embeddings = model_input[0] #First element of model_input contains all token embeddings

input_mask_expanded = attention_mask_input.unsqueeze(-1).expand(token_embeddings.size()).float()

sum_embeddings = torch.sum(token_embeddings * input_mask_expanded, 1)

sum_mask = torch.clamp(input_mask_expanded.sum(1), min=1e-9)

return sum_embeddings / sum_mask

class SentenceBertModelClass(torch.nn.Module):

def __init__(self, model_name="sentence-transformers/paraphrase-MiniLM-L3-v2", in_features=384):

super(SentenceBertModelClass, self).__init__()

self.l1 = AutoModel.from_Pre-trained(model_name)

self.pre_classifier = torch.nn.Linear(in_features*3, 768)

self.dropout = torch.nn.Dropout(0.3)

self.classifier = torch.nn.Linear(768, 1)

self.classifierSigmoid = torch.nn.Sigmoid()

def forward(self, sent_ids_var, doc_ids_var, sent_mask_var, doc_mask):

sent_output = self.l1(input_ids=sent_ids_var, attention_mask_input=sent_mask_var)

sentence_embeddings_var = mean_pooling(sent_output, sent_mask_var)

doc_output = self.l1(input_ids=doc_ids_var, attention_mask_input=doc_mask)

doc_embeddings = mean_pooling(doc_output, doc_mask)

# elementwise product of sentence embs and doc embs

combined_features = sentence_embeddings_var * doc_embeddings

# Concatenate input features and their elementwise product

concat_features = torch.cat((sentence_embeddings_var, doc_embeddings, combined_features), dim=1)

pooler_var = self.pre_classifier(concat_features)

pooler_var = torch.nn.ReLU()(pooler_var)

pooler_var = self.dropout(pooler_var)

output_var = self.classifier(pooler_var)

output_var = self.classifierSigmoid(output_var)

return output_var
```

Next, we instantiate the model, move it to a GPU that is available, and specify training parameters (learning rate, and binary cross entropy loss).

• Model training:

```
from torch import cuda

device = 'cuda' if cuda.is_available() else 'cpu'

model_var = SentenceBertModelClass(model_name=sentence_model)

model_var.to(device)

loss_function = torch.nn.BCELoss()

optimizer = torch.optim.Adam(params = model.parameters(), lr=LEARNING_RATE)
```

Next, we specify the model training loop. For each batch of data from our data loader, we first tokenize the input text, get predictions, compute gradients, and update model weights. We also keep a running sum of performance metrics per batch for subsequent visualization:

```
def train(epoch):

tr_loss = 0

n_correct = 0

nb_tr_steps = 0

nb_tr_examples = 0

model_var.train()

for _,data in tqdm(enumerate(training_loader, 0)):

sent_ids_var = data['sent_ids'].to(device, dtype = torch.long)

doc_ids_var = data['doc_ids'].to(device, dtype = torch.long)

sent_mask_var = data['sent_mask'].to(device, dtype = torch.long)

doc_mask_var = data['doc_mask'].to(device, dtype = torch.long)

targets = data['targets'].to(device, dtype = torch.float)

outputs_var = model_var(sent_ids_var, doc_ids_var, sent_mask_var,

doc_mask_var)

loss_var = loss_function(outputs_var, targets)

tr_loss += loss_var.item()

n_correct += torch.count_nonzero(targets == (outputs_var > 0.5)).item()

nb_tr_steps += 1

nb_tr_examples+=targets.size(0)

if _%print_n_steps==0:

 loss_step = tr_loss/nb_tr_steps

 accu_step = (n_correct*100)/nb_tr_examples

 print(str(_* train_params["batch_size"]) + "/" +

 str(len(train_df)) + " - Steps. Acc ->", accu_step, "Loss ->",

 loss_step)

 acc_step_holder.append(accu_step), loss_step_holder.append(loss_step)

optimizer.zero_grad()

loss_var.backward()

# # When using GPU

optimizer.step()

print(f'The Total Accuracy for Epoch {epoch}: {(n_correct*100)/nb_tr_examples}')

epoch_loss = tr_loss/nb_tr_steps

epoch_accu = (n_correct*100)/nb_tr_examples

print(f"Training Loss Epoch: {epoch_loss}")

print(f"Training Accuracy Epoch: {epoch_accu}")

return

for epoch in range(EPOCHS):

train(epoch)
```

• Model evaluation: To evaluate the model, we can write a loop similar to our training loop where we get predictions for data in each batch of our test set but do not update model weights:

```
def validate_model(model, testing_loader):

model.eval()

n_correct = 0; n_wrong = 0; total = 0; tr_loss = 0; nb_tr_steps = 0 ; nb_tr_examples = 0

with torch.no_grad():

for _, data in enumerate(testing_loader, 0):

 sent_ids_var = data['sent_ids'].to(device, dtype = torch.long)

 doc_ids_var = data['doc_ids'].to(device, dtype = torch.long)

 sent_mask_var = data['sent_mask'].to(device, dtype = torch.long)

 doc_mask_var = data['doc_mask'].to(device, dtype = torch.long)

 targets = data['targets'].to(device, dtype = torch.float)
```
