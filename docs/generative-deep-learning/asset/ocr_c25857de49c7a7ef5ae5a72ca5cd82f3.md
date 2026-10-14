```
sample_token, probs = self.sample_from(y[0][-1], temperature)
info.append({'prompt': start_prompt, 'word_probs': probs})
start_tokens.append(sample_token)
start_prompt = start_prompt + ' ' + self.index_to_word[sample_token]
print(f"\ngenerated text:\n{start_prompt}\n")
return info

def on_epoch_end(self, epoch, logs=None):
    self.generate("recipe for", max_tokens = 100, temperature = 1.0)
```

+   1. Create an inverse vocabulary mapping (from word to token).
+   2. This function updates the probabilities with a temperature scaling factor.
+   3. The start prompt is a string of words that you would like to give the model to start the generation process (for example, recipe for). The words are first converted to a list of tokens.
+   4. The sequence is generated until it is max_tokens long or a stop token (0) is produced.
+   5. The model outputs the probabilities of each word being next in the sequence.
+   6. The probabilities are passed through the sampler to output the next word, parameterized by temperature.
+   7. We append the new word to the prompt text, ready for the next iteration of the generative process.

Let's take a look at this in action, at two different temperature values (Figure 5-9).

```
temperature = 1.0
generated text:
recipe for sour japanese potatoes julienne | in a bowl stir together the yeast mixture with the milk and the peanut butter crumbs , the sour cream , and the butter mixture with a fork , gently fold in the prunes gently or until incorporated . lightly stir the oil and yeast until it just holds soft peaks , but not runny , on bottom of a 7 - sided sheet of aluminum foil , top it with a round , and a pinch of each brownies into a goblet , or with the baking dish . serve each with sorbet
```

```
temperature = 0.2
generated text:
recipe for grilled chicken with mustard - herb sauce | combine first 6 ingredients in medium bowl . add chicken to pot . add chicken and turn to coat . cover and refrigerate at least 1 hour and up to 1 day . preheat oven to 450°F . place turkey on rock in roasting pan . roast until thermometer inserted into thickest part of thigh registers 175°F , about 1 hour longer . transfer to rack in center of oven and preheat to 450°F . brush chicken with oil . sprinkle with salt and pepper . roast until thermometer inserted into
```

Figure 5-9. Generated outputs at temperature = 1.0 and temperature = 0.2