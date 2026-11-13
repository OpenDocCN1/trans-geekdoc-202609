Much closer already. Another common transformation is to convert special characters to a standard form, such as replacing “é” with “e,” “æ” with “ae,” and so on. Our token “méxico” would then become “mexico”.


Lastly, a much more advanced standardization pattern that is more rarely used in a machine learning context is _stemming_: converting variations of a term (such as different conjugated forms of a verb) into a single shared representation, like turning “caught” and “been catching” into “[catch]” or “cats” into “[cat]”. With stemming, “was staring” and “stared” would become something like “[stare]”, and our two similar sentences would finally end up with an identical encoding:


> “sunset came i [stare] at the mexico sky isnt nature splendid”
> 

With these standardization techniques, your model will require less training data and will generalize better—it won’t need abundant examples of both “Sunset” and “sunset” to learn that they mean the same thing, and it will be able to make sense of “México” even if it has only seen “mexico” in its training set. Of course, standardization may also erase some amount of information, so always keep the context in mind: for instance, if you’re writing a model that extracts questions from interview articles, it should definitely treat “?” as a separate token instead of dropping it, because it’s a useful signal for this specific task.


# ## 11.2.2 Text splitting (tokenization)


Once your text is standardized, you need to break it up into units to be vectorized (tokens), a step called _tokenization_. You could do this in three different ways:


+   - Word-level tokenization—Where tokens are space-separated (or punctuation-separated) substrings. A variant of this is to further split words into subwords when applicable—for instance, treating “staring” as “star+ing” or “called” as “call+ed.”
+   - _N_-gram tokenization—Where tokens are groups of _N_ consecutive words. For instance, “the cat” or “he was” would be 2-gram tokens (also called bigrams).
+   - Character-level tokenization—Where each character is its own token. In practice, this scheme is rarely used, and you only really see it in specialized contexts, like text generation or speech recognition.
+   

In general, you’ll always use either word-level or N-gram tokenization. There are two kinds of text-processing models: those that care about word order, called _sequence models_, and those that treat input words as a set, discarding their original order, called _bag-of-words models_. If you’re building a sequence model, you’ll use word-level tokenization, and if you’re building a bag-of-words model, you’ll use N-gram tokenization. N-grams are a way to artificially inject a small amount of local word order information into the model. Throughout this chapter, you’ll learn more about each type of model and when to use them.