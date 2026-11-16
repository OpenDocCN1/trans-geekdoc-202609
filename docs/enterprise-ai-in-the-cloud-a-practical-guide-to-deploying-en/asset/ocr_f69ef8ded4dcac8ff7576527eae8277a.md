# TABLE 24.6: Base Models Grouped by Family and Capability in Azure

| FAMILY | DESCRIPTION | BASE MODELS WITHIN THE FAMILY |
| :--- | :--- | :--- |
| GPT-4 | Models that generate natural language and code. These models are currently in preview. | gpt-4, gpt-4-32k |
| GPT-3 | Models that can understand and generate natural language. | text-davinci-003, text-curie-001, text-babbage-001, text-ada-001, gpt-35-turbo |
| Codex | Models that can understand and generate code, including translating natural language to code. | code-davinci-002, code-cushman-001 |

To make API calls to the model, you must deploy it. Note that you can deploy only one instance of the model. Once deployed, you can test it using the prompts. A prompt is the text input that is sent to the model's endpoint. Responses can come in the form of text, code, or other formats.

Prompts can be of various types, such as classifying content, generating new content, holding conversations, translating, summarizing content, picking up where you left off, and getting facts.

# Azure OpenAI Studio Playgrounds for Model Testing

Playgrounds are useful interfaces that you can use to test your deployed models without developing a client application. Azure offers multiple playgrounds with different parameter-tuning options.

![](bbox=[0.125, 0.39, 0.875, 0.73])

# FIGURE 24.20: Azure OpenAI Studio playgrounds for model testing

# Optimizing Model Behavior Using Playground Parameters

These playground parameters are used to change the performance of the models. Consider this list:

+   * **Temperature:** A lower value provides more predictable answers, while a higher value will result in more creative answers.
+   * **Max length (tokens):** A token is equal to roughly four characters in the English language. This sets the maximum number of tokens per model response.