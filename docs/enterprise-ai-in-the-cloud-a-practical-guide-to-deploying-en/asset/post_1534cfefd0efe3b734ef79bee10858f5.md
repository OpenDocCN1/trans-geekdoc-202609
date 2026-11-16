
![](img/1490b3cf638678afadc8c48abc1698d5_650_0.png)

**FIGURE 24.6:** Generative AI applications

## Transforming Customer Relationships Through Chatbots, Personalization

Generative AI has been instrumental in transforming customer relationships by analyzing customer behavior, preferences, and feedback to develop new product recommendations and responses and even create new products. This level of personalization can help engage with customers better and promote customer loyalty in the long term.

Another example is the application of generative AI to build a chatbot. Instead of having preprogrammed rules to answer the customer's question, you can have a generative AI chatbot similar to ChatGPT to answer a customer's questions in real time based on their style of language, preference, sentiment, and type of question.

## Breaking Language Barriers, Better Supplier Relationships, and Global Trade

In the case of supplier relationships, using the natural language translation capabilities of gen AI, you can communicate with suppliers across multiple geographies and countries. This ability helps you create better partner relationships and promotes global trade.

## Reimagining Workplace Efficiency with AI-Powered Assistants

Generative AI can also collaborate with internal employees to automate tasks and improve process efficiency and employee productivity. For example, GitHub's Copilot is an AI-powered assistant that can help developers to develop code faster. This opens up new opportunities because this concept of having a virtual assistant that can work with humans to improve employee productivity will be a game-changer when automating many of the business processes within the company.

## Long-Term Workforce Transformation with AI as a Partner

Figure 24.7 shows how AI can be a valuable partner that enables long-term transformation in the workforce. The ability of the employee to work with AI will not only enhance their productivity. It will also enhance the ability to come up with new ideas with the help of the AI assistant, which can act as a creative partner. It now becomes possible to develop groundbreaking ideas and efficient execution strategies.

## From Process Transformation to Life-Changing Applications

Generative AI has the potential to uncover hidden patterns and insights from large amounts of data that were not possible before because of the sheer size of the data. Armed with these new insights, gen AI can also propose changes to current workflows to eliminate process inefficiencies, remove bottlenecks, and automate tasks.

Enhanced productivity, idea generation, and performance

![](img/1490b3cf638678afadc8c48abc1698d5_651_0.png)

### Employee Transformation

- Automated task (coding, data analysis, document drafting, etc.)

![](img/1490b3cf638678afadc8c48abc1698d5_651_1.png)

### Task Automation

![](img/1490b3cf638678afadc8c48abc1698d5_651_2.png)

### New Opportunities

![](img/1490b3cf638678afadc8c48abc1698d5_651_3.png)

Generation of new ideas and process automation opportunities

### GitHub Copilot

![](img/1490b3cf638678afadc8c48abc1698d5_651_4.png)

Paired Programmer improved productivity

![](img/1490b3cf638678afadc8c48abc1698d5_651_5.png)

### Long-Term Workforce Transformation

**FIGURE 24.7:** Long-term workforce transformation with AI as a partner

Source: Blue Planet Studio/ Adobe Stock

The uses of generative AI are not restricted to businesses alone but can also impact our personal lives. Take, for example, the Stanford University research, where they converted human brain signals into written text.

> TIP Use generative AI not to replace creativity or other relationships but to augment your capabilities and open new possibilities to transform business and personal lives.

## The Fascinating World of Generative AI: From GANs to Diffusion Models

Now that you know what generative models do, you probably wonder how they work. Even though there are a number of generative models out there, three models stand out: generative adversarial networks (GANs), variational auto-encoders (VAEs), and transformer models. Despite their differences, they all follow the same principles: to learn the underlying patterns in the data and re-create data with similar data patterns.

## GANs: Interplay of Generator and Discriminator Networks

The GANs model was invented by Ian Goodfellow and his team in 2014. It is based on the beautiful concept of two neural networks working against each other. One is called the Generator, which creates realistic data, such as images, based on the data it was trained upon. The other is the Discriminator neural network, which tries to critique the new image and find the difference between the real image and the generated version. This constant tussle between the two networks results in an incredibly realistic image.

> TIP Use GANs to create realistic human faces and even photorealistic artwork out of sketches.

## VAEs: A Solution to GAN's Black-Box Problem

One of the drawbacks of GANs is that they operate like black boxes. We don't know how these models work. In such situations, VAEs can help because we can understand the hidden layers that drive the data. It is used in product recommendation engines and text generation use cases.

## Transformers: The Behind-the-Scenes Hero of GPT, BERT

Transformers are the model behind models such as GPT-3 and BERT, which revolutionized text generation, summarization, translation, and more. Transformers were introduced in 2017 and have revolutionized the world of natural language processing because they simultaneously consider all the words in a sentence when trying to make a prediction. We already know that ChatGPT has taken the world by storm, as more than 100 million people registered for the tool in just a couple of weeks. When using ChatGPT, it feels almost like talking to a human, which is impressive. Another example of using a transformer model is when people use Gmail, where the autocomplete feature is based on a Transformer model. As shown in Figure 24.8, a transformer model contains an encoder and decoder.

> NOTE Transformers have an encoder and a decoder, where the encoder encodes the input sequence and passes it to the decoder, which learns how to decode the representation for a relevant task.

![](img/1490b3cf638678afadc8c48abc1698d5_652_0.png)

**FIGURE 24.8:** Components of a transformer model

## Hallucinations: When Models Go Astray

Sometimes these models can generate outputs that are nonsensical or grammatically incorrect. This is known as hallucination and can happen when the model has not been trained adequately or on enough data or is trained on noisy data or has not been given enough context or constraints to work with.

## From Text-to-Image to Text-to-Task Using Diffusion Models

While GANs and VAEs have held the limelight for the most part, diffusion models have also been making waves recently. Diffusion models take a unique approach to creating new data. They take the original image (the picture of a cat) and add noise to it to distort it slightly. They continue this process until it becomes unrecognizable. Then, it tries to recover the image by removing the noise with each step. In this process, it ends up creating a range of new cat images depending on the noise with which it started the recovery process.

> NOTE Diffusion models can generate text-to-image, text-to-video, text-to-3D, and text-to-tasks.

Text-to-3D can be used in video games, and text-to-task models can be used to carry out tasks such as question and answer, performing a search, or taking some action such as navigating a UI or updating a document. Table 24.5 captures the differences between GANs, VAEs, and diffusion models.

## TABLE 24.5: Differences Between GANs, VAEs, and Diffusion Models

| | GANS MODEL | VAES | DIFFUSION MODELS |
|---|---|---|---|
| **Working Principle** | Two neural networks competing in a zero-sum game to generate new data that closely resembles the training dataset | A type of neural network that learns to encode and decode data by mapping it to a latent space | Adding noise to the original image and then removing the noise gradually to create a range of new images depending on the noise with which the recovery process started |
| **Applications** | • Image to image translation<br>• Scenes and people<br>• Realistic human faces<br>• Artwork<br>• Photorealistic photos of objects | • Image and video generation<br>• Data compression<br>• Anomaly detection | • Text-to-image<br>• Text-to-video<br>• Text-to-3D<br>• Text-to-tasks |
| **Examples** | • StyleGAN<br>• BigGAN | • Beta-VAE<br>• VQ-VAE | • DALL-E<br>• CLIP |

DALL-E and CLIP are two diffusion-type models from OpenAI. DALL-E can generate images from text descriptions, while CLIP can understand both text and images and can relate them to each other. For example, you can ask DALL-E to create an orange in the form of an apple, and DALL-E will precisely do that to create a novel image that was never seen before.

Diffusion models are not without their challenges because they can be very computationally intensive and slower than GANs. Despite their challenges, diffusion models are fascinating and extend the limits of virtual reality and what's possible with Gen AI.

## IMPLEMENTING GENERATIVE AI AND ChatGPT

Given its many risks, implementing generative AI and ChatGPT for your company is not a trivial task. Moreover, it is a constantly evolving space; you must keep close tabs on what's happening out there. Having said that, consider the different options you have when implementing generative AI or ChatGPT. Your options will span between buying off-the-shelf solutions and building them on your own. Figure 24.9 shows the different options laid out in front of you.

## From Packaged Software to Pretraining Models

Consider these build versus buy options that are available when implementing generative AI:

- **Out-of-the-box options:** You already use the out-of-the-box option when you use ChatGPT for various natural language processing tasks such as summarizing, answering questions, translation, and so on. The issue with that approach is that you need to figure out how your data is going to be leveraged by those companies.
- **Consuming APIs:** When you use APIs, cost is a critical factor because you are charged based on the tokens, you use both as a query to the API and the response you get back. It is therefore important to exercise controls over the amount of data input to the API as well as the amount of data generated from the API.
- **Prompt engineering:** The other option is prompt engineering, which has been gaining much attention lately. We are already seeing innovations in this space in the form of new models such as

