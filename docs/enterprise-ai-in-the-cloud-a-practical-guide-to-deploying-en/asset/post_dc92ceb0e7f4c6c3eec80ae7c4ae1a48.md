
![](img/1490b3cf638678afadc8c48abc1698d5_667_0.png)

FIGURE 24.19: Provisioning an OpenAI service in Azure

> **NOTE** At this point, the OpenAI Azure service is available with limited access to ensure its ethical use. Certain models are available in certain regions only.

## Effortless Gen AI Development Using Azure OpenAI Studio

Azure OpenAI Studio provides access to building, managing, and deploying models. It's a cloud-based service that makes building gen AI applications using OpenAI's APIs easy. It is a preconfigured environment that comes with a GPU-powered compute instance, a Jupyter notebook, a collection of pretrained models, and access to OpenAI's API documentation.

To access OpenAI Studio, you need to create an account, launch the Studio instance, and then start building by importing a pretrained model or by training your own model using the Jupyter Notebook. Once done, you can deploy your application to Azure Cloud using the OpenAI API.

> **NOTE** Azure OpenAI Studio is a great way to build your gen AI apps without worrying about the underlying infrastructure.

## Customizing Models in Azure OpenAI Service

When building apps with Azure OpenAI service, you need to choose a base model, and then you can customize it if required. These models are grouped by family and capability, as shown in Table 24.6.

## TABLE 24.6: Base Models Grouped by Family and Capability in Azure

| FAMILY | DESCRIPTION | BASE MODELS WITHIN THE FAMILY |
| :--- | :--- | :--- |
| GPT-4 | Models that generate natural language and code. These models are currently in preview. | gpt-4, gpt-4-32k |
| GPT-3 | Models that can understand and generate natural language. | text-davinci-003, text-curie-001, text-babbage-001, text-ada-001, gpt-3.5-turbo |
| Codex | Models that can understand and generate code, including translating natural language to code. | code-davinci-002, code-cushman-001 |

To make API calls to the model, you must deploy it. Note that you can deploy only one instance of the model. Once deployed, you can test it using the prompts. A prompt is the text input that is sent to the model's endpoint. Responses can come in the form of text, code, or other formats.

Prompts can be of various types, such as classifying content, generating new content, holding conversations, translating, summarizing content, picking up where you left off, and getting facts.

## Azure OpenAI Studio Playgrounds for Model Testing

Playgrounds are useful interfaces that you can use to test your deployed models without developing a client application. Azure offers multiple playgrounds with different parameter-tuning options.

![](img/1490b3cf638678afadc8c48abc1698d5_668_0.png)

## FIGURE 24.20: Azure OpenAI Studio playgrounds for model testing

## Optimizing Model Behavior Using Playground Parameters

These playground parameters are used to change the performance of the models. Consider this list:

- **Temperature:** A lower value provides more predictable answers, while a higher value will result in more creative answers.
- **Max length (tokens):** A token is equal to roughly four characters in the English language. This sets the maximum number of tokens per model response.
- Stop sequences: These instruct the model to stop the response at a desired point, such as the end of a sentence or list.

Other parameters include top probabilities (top P), frequency penalty, presence penalty, pre-response text, and post-response text.

## AI-Powered Code Assistance with GitHub Copilot

GitHub Copilot is like a pair programmer who can assist you in completing the code. It is trained based on an OpenAI Codex model and can provide coding suggestions and even write full functions. Using the tool can help improve the developer productivity by doing the following:

- Generating code for functions, classes, loops, and other programming tasks
- Filling in missing code
- Suggesting alternative code
- Translating code from one programming language to another

As shown in Figure 24.21, it can also troubleshoot bugs quickly by catching errors, enhance developer creativity by suggesting new ideas, reduce learning curves, and improve collaboration by increasing the readability and maintainability of the code.

![](img/1490b3cf638678afadc8c48abc1698d5_669_0.png)

FIGURE 24.21: GitHub Copilot's features and benefits

To use GitHub Copilot, you just need to install the extension in your IDE, such as Visual Studio, Neovim, and JetBrains. Currently, you need to have an active GitHub Copilot subscription to use Copilot. While GitHub Copilot may differ in the details from AWS CodeWhisperer, it's similar in terms of its goals to improve developer productivity.

## Additional Tools and Platforms

With the advent of generative AI, several tools and platforms have also come up to benefit businesses and individuals. This section discusses the ones shown in Figure 24.22.

## OpenAI API Integrations

OpenAI has released many APIs for developers to access their models, such as GPT-3 and DALL-E. Take, for example, the Kuki.ai chatbot that leverages OpenAI APIs to provide an impressive conversational chatbot. Its ability to chat in almost 50 languages and handle so many conversational scenarios makes it a good candidate for customer service gaming, and so on.

## Transforming Conversations with GPT-3, GPT-4, and ChatGPT

GPT-3 and GPT-4 are large language models created by OpenAI, and ChatGPT is a chatbot built on those models. These LLMs can generate text, translate languages, answer questions, and respond to you in a personalized manner depending upon your prompts.

> NOTE The G in GPT stands for generative, P for pretrained, and T for transformer models.

![](img/1490b3cf638678afadc8c48abc1698d5_670_0.png)

FIGURE 24.22: Additional gen AI tools and platforms

## Text-to-Image Generation Using DALL-E 2

As discussed earlier, DALL-E 2 is a generative AI model that can create images from text. It can create hyper realistic images that can be used to create fictional characters or even new product designs.

## Unveiling Psychedelic Art with DeepDream

DeepDream is a generative AI tool created by Google that can create psychedelic images from ordinary images. It does this by learning the existing patterns in the image and creating strikingly new patterns and stunning images by adding variations.

## Creativity Through Image Style Transfer with DeepArt

DeepArt is a generative AI tool created by Google that combines one image's style with another's content to create entirely new art.

## Hyperrealistic Faces with NVIDIA StyleGAN

NVIDIA StyleGAN is a generative AI model that can create stunningly realistic faces that do not exist in the world.

## Unleash Creativity with Runway ML

Runway ML helps users to develop generative AI code without coding. Whether it is creating a new artwork or designing a new font, Runway ML can provide you with generative AI models to build upon.

## WORKBOOK TEMPLATE: GENERATIVE AI USE CASE PLANNER

Download the “Generative AI Use Case Planner” template from the download section of the book (www.wiley.com/go/EnterpriseAIintheCloud). Use this template to plan for Generative AI use cases and ensure you have factored in all aspects of planning for the generative AI use cases.

## SUMMARY

In this chapter, you journeyed into the complex world of generative AI. You learned about the critical components of deep learning, semi-supervised learning, generative versus discriminative models, diffusion models, foundation models, and large language and large image models.

Ultimately, generative AI opens a new chapter of innovation and potential. It can revolutionize and disrupt businesses, augment human potential, and provide a new perspective for solving business problems. However, it is not without risks, potential ethical concerns, and calls for an urgent need to protect data and user privacy and ensure fairness and transparency in decision-making.

It is undoubtedly a new era for businesses and personal lives, and I look forward to seeing how this technology evolves and transforms our lives.

## REVIEW QUESTIONS

These review questions are included at the end of each chapter to help you test your understanding of the information. You’ll find the answers in the following section.

- 1. What is the estimated economic benefit generated by generative AI use cases annually across industries according to McKinsey?
  - A. $1.5 to $2.3 trillion
  - B. $2.6 to $4.4 trillion
  - C. $5.5 to $7.2 trillion
  - D. $6.3 to $8.5 trillion

- 2. Discriminative models in machine learning are focused on
  - A. Predicting the label for new data points
  - B. Generating new data instances
  - C. Understanding the relationships between the features and the labels
  - D. Learning the probability distribution of the existing data

- 3. What is the main limitation of large language models (LLMs)?
  - A. They can only understand text.
  - B. They require a large amount of compute power.
  - C. They can only generate text.
  - D. They can work only with small amounts of data.

- 4. Variational autoencoders (VAEs) are beneficial because
  - A. They can understand the hidden layers that drive the data.
  - B. They are used in text generation use cases.
  - C. They can operate like black boxes.
  - D. Both A and B.

- 5. In terms of workforce transformation, AI can act as
  - A. A competitor
  - B. A partner
