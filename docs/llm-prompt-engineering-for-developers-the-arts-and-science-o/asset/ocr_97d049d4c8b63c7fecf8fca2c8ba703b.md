The model is trained on a large dataset of text, such as books, articles, and websites. It learns the statistical relationships between words and the context in which they appear. Using its data, the model looks for patterns and tries to predict the most likely word to come next based on the input it has received.

To generate words, the model uses a technique called “probability sampling.” It assigns probabilities to different words based on their likelihood to appear in a given context. The model then selects the word with the highest probability or samples from a distribution of likely words based on parameters like temperature or top-p.

For example, if the prompt is “The weather is,” the model might assign high probabilities to words like “sunny,” “cloudy,” or “rainy” based on what it has learned from the training data and based on the global context of the conversation. It then generates the word that has the highest probability or samples a word from the distribution to complete the sentence.

This is a simplified explanation of how generative language models work. Other factors, such as how the model is trained to interact with the prompt and the context of the conversation, also play a role in the generation of text.

In reality, the model does not have real understanding or knowledge like a human does. It’s all about building statistical relationships between words and contexts.

# ## 4.9 - Understanding the API Parameters

Understanding API parameters can give you a better idea of how the model works behind the scenes, and how you can use it in conjunction with prompts to generate better results.

Web interfaces, like ChatGPT, are usually designed to be easy to use, and you don’t have the ability to directly modify the internal parameters of the model, such as temperature.

There are some workarounds to this limitation, such as describing the desired behavior in the prompt: