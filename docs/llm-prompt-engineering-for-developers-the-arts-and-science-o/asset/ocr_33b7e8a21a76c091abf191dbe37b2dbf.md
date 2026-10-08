# 16.2 - Installation

LangChain supports several LLM providers, like Hugging Face and OpenAI. We are going to use OpenAI for this project.

To install LangChain, run the following command:

```
pip install langchain==0.0.270
```

Alternatively, if you want to use Hugging Face, install this additional dependency, then create an account on Hugging Face^{60} and get your API keys.

```
pip install huggingface_hub
```

Since we are using OpenAI, we need to have openai installed and configured. This was already done in one of the previous chapters, but if you haven't done it yet, run the following command:

```
pip install openai
```

You will also need to set the OPENAI_API_KEY environment variable. You can do this by running the following command:

```
export OPENAI_API_KEY=<your-api-key>
```

# 16.3 - Getting Started

To get started, let's create an app that predicts the next word in a sentence using two types of outputs: LLM and ChatModel.