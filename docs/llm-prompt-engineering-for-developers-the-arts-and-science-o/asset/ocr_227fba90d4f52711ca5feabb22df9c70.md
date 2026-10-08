In case the next word depends only on the previous word, the formula can be simplified to:

```
p(w1,w2,w3,...,wN) = p(w1) * p(w2|w1) * p(w3|w2) * ... * p(wN|wN-1)
```

To implement the above formula directly, you'd need the joint probability of the entire sequence. However, models typically provide probabilities (or log probabilities) for one word at a time. That's why we often work with modified formulas.

For a given word w with probability p(w), its log probability is log(p(w)). If we're looking at the likelihood of a sequence, instead of multiplying the probabilities, we add the log probabilities: log(p(w1,w2,w3,...,wN)) = log(p(w1)) + log(p(w2)) + ... + log(p(wN))

However, for log probabilities, a 'good' or 'likely' event has a high log probability (close to 0), whereas an 'unlikely' event has a very negative log probability. We sometimes talk about the "negative log likelihood" (NLL), which is just the negative of the log probability. A higher NLL indicates a less likely event.

Given that we have the NLL for each word in a sequence, the average NLL is: avg NLL= -log(p(w1)) - log(p(w2)) - ... - log(p(wN)) / N The perplexity is then: PP = exp(avg NLL).

A practical example using an OpenAI language model translated to Python would be:

```
import os
import openai
import math

# Set the model name.
model_name = "<MODEL_NAME>"

# Set the API key for OpenAI.
openai_api_key = os.environ["OPENAI_API_KEY"]
openai.api_key = openai_api_key
```