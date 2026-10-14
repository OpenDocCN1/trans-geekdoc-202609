```
temperature = 1.0
Generated text:
wine review : us : washington : chenin blanc : a light , medium - bodied wine , this light - bodied expressi on is not a lot of enjoyment . it ' s simple with butter and vanilla flavors that frame mixed with expressiv e fruit . it ' s juicy and tangy with a lemon lingers on the finish .
```

```
temperature = 0.5
Generated text:
wine review : italy : piedmont : nebbiolo : : this opens with aromas of french oak , menthol and a whiff of to ast . the straightforward palate offers red cherry , black raspberry jam and a hint of star anise alongside firm but rather fleeting tannins , drink through 2016 .
```

Figure 9-10. Generated outputs at temperature = 1.0 and temperature = 0.5.

There are a few things to note about these two passages. First, both are stylistically similar to a wine review from the original training set. They both open with the region and type of wine, and the wine type stays consistent throughout the passage (for example, it doesn’t switch color halfway through). As we saw in Chapter 5, the generated text with temperature 1.0 is more adventurous and therefore less accurate than the example with temperature 0.5. Generating multiple samples with temperature 1.0 will therefore lead to more variety as the model is sampling from a probability distribution with greater variance.

# Viewing the attention scores

We can also ask the model to tell us how much attention is being placed on each word, when deciding on the next word in the sentence. The TransformerBlock outputs the attention weights for each head, which are a softmax distribution over the preceding words in the sentence.

To demonstrate this, Figure 9-11 shows the top five tokens with the highest probabilities for three different input prompts, as well as the average attention across both heads, against each preceding word. The preceding words are colored according to their attention score, averaged across the two attention heads. Darker blue indicates more attention is being placed on the word.