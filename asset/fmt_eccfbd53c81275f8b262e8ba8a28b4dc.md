
outputs: `TFBaseModelOutputWithPooling(last_hidden_state=<tf.Tensor: shape=(1, 8, 768), dtype=float32, numpy=array([[[ -0.00286604, 0.22725284, 0.0192489 , ..., -0.16997483, 0.22732456, 0.2084062 ], [ 0.37293857, 0.18514417, -0.1804212 , ..., -0.02841423, 0.92029154, 0.08076832], [ 1.0605763 , 0.68393016, 0.3488946 , ..., 0.23068337, 0.57474136, -0.2725499 ], ..., [ 0.36834046, 0.09277615, -0.49751407, ..., -0.21702018, -0.15317607, -0.17662546], [ 0.2218363 , -0.1452129 , -0.6224062 , ..., 0.19659105, 0.0055675 , 0.05520308], [ 0.38959947, 0.1536812 , -0.2523777 , ..., 0.3461408 , -0.5905776 , -0.2758692 ]]]), dtype=float32)>, pooler_output=<tf.Tensor: shape=(1, 768), dtype=float32, ... numpy=array([-8.23929489e-01, -2.69686729e-01, 2.79440969e-01, 5.52639008e-01, -5.11318594e-02, -8.98018852e-02, 7.92447925e-01, 1.49121523e-01, 4.11069989e-02, -9.99752760e-01, 2.84106694e-02, 4.69654143e-01, 9.74410057e-01, -2.57081628e-01, 9.02504683e-01, -4.83381122e-01, 3.19796950e-02, -5.14692605e-01, ... 3.13184172e-01, 3.45878363e-01, 7.98233569e-01, 4.64420468e-01, 6.13458335e-01, 4.65085119e-01, 2.03554392e-01, -5.93035281e-01, 8.85935843e-01]]), dtype=float32)>, hidden_states=None, attentions=None)`

Listing 11.14 显示了 `pytorch_gpt_next_word.py` 的内容，展示了如何在句子中预测下一个词。

***LISTING 11.14: `pytorch_gpt_next_word.py`***

```python
import torch

from pytorch_transformers import GPT2Tokenizer, GPT2LMHeadModel

# Load pre-trained GPT-2 tokenizer model:

tokenizer = GPT2Tokenizer.from_pretrained('gpt2')

# encode the words in a sentence:

text = "What is the fastest car in the"

indexed_tokens = tokenizer.encode(text)

# convert tokens to a PyTorch tensor:

tokens_tensor = torch.tensor([indexed_tokens])

# load pre-trained model (weights)

model = GPT2LMHeadModel.from_pretrained('gpt2')

# "eval" mode deactivates the DropOut modules:

model.eval()

# Predict each token:

with torch.no_grad():

    outputs = model(tokens_tensor)

    predictions = outputs[0]

print("=> list of predictions:")

print(predictions[0, -1, :])

print()

print("=> argmax of predictions:")

print(torch.argmax(predictions[0, -1, :]).item())

print()

# Get the predicted next sub-word

predicted_index = torch.argmax(predictions[0, -1, :]).item()

predicted_text = tokenizer.decode(indexed_tokens + [predicted_index])

# Print the predicted word

print("=> initial text:")

print(text)

print()

print("=> Predicted next word:")

print(predicted_text)
```
