target word that a model uses while training the relationships within a word. For instance, if the context window size has been set at 2, and the target word is fox, and the context would comprise of quick, brown, jumps, and over. This size determines how much context from the local space the model takes for learning the semantic relations and, therefore, determines the fineness of the embeddings. The size of the window is larger, in case it captures a broader view of the context than that of the immediate neighbors of a pixel.

# Question 8: How do you handle OOV words when using pre-trained word embeddings?

Answer: Handling OOV words when using pre-trained word embeddings can be approached in the following ways:

+   - Use a special token: In the pipeline, OOV words are replaced by a unique symbol (for example, <UNK>), which it has an embedding all to itself.
+   - Sub word information: Make use of models, such as fastText, where it is possible to produce word embeddings, where OOV words are considered as a combination of sub words embeddings.
+   - Train embeddings on task-specific data: Simple ways to adapt the given embeddings to your own specific set of words from your own training set, including the OOV words.
+   - Character-level models: Optionally, character embeddings or other architectures that create word embeddings from character sequences, allowing dealing with OOV words.

It aids in ensuring that the OOV words are not so much off the embedded space, and this is facilitated by the following methods.