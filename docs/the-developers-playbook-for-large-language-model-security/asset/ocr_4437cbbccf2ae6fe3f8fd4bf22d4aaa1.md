# Regular audits

Review and clean the training datasets to ensure no PII slips through.

# Data masking

Use techniques to hide original data with modified content structurally similar to the original data, such as transforming “John Doe” into “Xxxx Xxx.” The masked data is a sanitized version where you retain the essence but obscure the sensitive details.

# Use synthetic data

Generate data that is not based on actual user information but retains the same statistical properties as your original dataset.

# Limit data collection

Only collect the minimum data necessary for the task. If you don’t need certain pieces of information, don’t collect them in the first place.

# Automated scanning

Use tools that scan and flag potential PII in datasets.

# Differential privacy

Implement techniques that add noise to the data, ensuring that any single data point (or individual’s data) doesn’t significantly impact the overall dataset and that an attacker cannot reverse engineer the data.

# Tokenization

Replace sensitive data elements with nonsensitive equivalents with no exploitable meaning. These tokens act as placeholders for the original data, which is then securely stored in a separate location or data vault.

By adopting these strategies, organizations can significantly reduce the risk of incorporating PII into their training datasets, ensure regulatory compliance, and maintain trust with users and stakeholders.

# Retrieval-Augmented Generation

RAG is a transformative approach in LLM data acquisition and response generation. Instead of solely relying on a vast internal knowledge base acquired from training, as traditional LLMs do, RAG first retrieves relevant document snippets or passages from an external dataset. Then, the LLM utilizes these passages to inform its generated responses. This two-step approach—retrieving relevant information and then developing an answer based on that retrieval—allows the model to pull in real-time or more updated information that wasn’t part of its original training data.