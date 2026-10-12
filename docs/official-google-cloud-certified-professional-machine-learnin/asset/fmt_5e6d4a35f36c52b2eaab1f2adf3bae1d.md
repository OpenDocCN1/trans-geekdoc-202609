
# Classification on image data || Custom‐trained TensorFlow models that use a TensorFlow prebuilt container to serve predictions

AutoML image models |

| XRAI (eXplanation with Ranked Area Integrals) || Image data || Models that accept image inputs. Recommended especially for natural images, which are any real‐world scenes that contain multiple objects. || Classification on image data || Custom‐trained TensorFlow models that use a TensorFlow pre‐built container to serve predictions

AutoML image models |

We mention differentiable models and nondifferentiable models in [Table 9.1](#c09.xhtml#c09-tbl-0001). Let's talk about the basic difference between them:

*   **Differentiable models:** You can calculate the derivative of all the operations in your TensorFlow graph. This property helps to make backpropagation possible in such models. For example, neural networks are differentiable. To get feature attributions for differentiable models, use the integrated gradients method.

*   **Nondifferentiable models:** These include nondifferentiable operations in the TensorFlow graph, such as operations that perform decoding and rounding tasks. For example, a model built as an ensemble of trees and neural networks is nondifferentiable. To get feature attributions for nondifferentiable models, use the sampled Shapley method.

For an in‐depth explanation, refer to the *AI Explanations Whitepaper* at `https://cloud.google.com/blog/products/ai-machine-learning/example-based-explanations-to-build-better-aiml-models`.

## Vertex AI Example–Based Explanations

Example‐based explanations are used for misclassification analysis and can enable active learning so that data can be selectively labeled. For instance, if out of 10 total explanations for an image, 5 are from class “bird” and five are from class “plane,” the image can be a candidate for human annotation, further enriching the data.

Example‐based explanations are not limited to images. They can generate embeddings for multiple types of data such as images, text, and table. Refer to this blog to learn more about this: `https://cloud.google.com/blog/products/ai-machine-learning/example-based-explanations-to-build-better-aiml-models`.

This feature is in public preview, and you might not get questions from this topic on the exam. However, it's a good topic to understand for the Explainable AI options provided by Google Cloud.

## Data Bias and Fairness

Data can be biased when certain parts of the data are not collected or are misrepresented. This might happen using data collected through surveys, data that is based on systemic or historical beliefs, or a data sample that is not random or is too small. Any of these can lead to skewed outcomes, as biased data does not accurately represent the machine learning model use case. It also presents another problem of system prejudice or fairness in the data.

ML fairness ensures that biases in the data and model inaccuracies do not lead to models that treat individuals unfavorably on the basis of characteristics such as race, gender, disabilities, or sexual or political orientation—for example, granting a credit card based on gender or denying an application based on race.

The following list includes some of the ways you can detect bias and fairness in data in Vertex AI:

*   The Explainable AI feature attributions technique, which is already present in AutoML tables, helps detect bias and fairness in the tabular or structured dataset.

*   Use Vertex AI to inspect models through an interactive dashboard with the integrated `What‐If Tool`. (We covered the What‐If Tool in [Chapter 8](#c08.xhtml), “Model Training and Hyperparameter Tuning.”) This tool can be used to detect bias in the dataset using the features overview functionality, which automatically detects bias from the data. You can refer to this link for more details: `https://pair-code.github.io/what-if-tool/learn/tutorials/features-overview-bias`.

*   Alternatively, for detecting bias and fairness in NLP (natural language processing) models, you can utilize the open source `Language Interpretability Tool`.

By using these tools and techniques, you can detect bias and fairness in your dataset before training models on them during the data exploration or data preprocessing phase, which we covered in [Chapter 2](#c02.xhtml), “Exploring Data and Building Data Pipelines,” and [Chapter 3](#c03.xhtml), “Feature Engineering.”

## ML Solution Readiness

We will talk about ML solution readiness in terms of these two concepts:

*   Responsible AI
*   Model governance

Google believes in Responsible AI principles, which we covered in [Chapter 1](#c01.xhtml), “Framing ML Problems.” Google shares best practices with customers through Google `Responsible AI practices`, `fairness best practices`, `technical references`, and `technical ethics` materials.

Responsible AI tools are an increasingly effective way to inspect and understand AI models. Some of the tools are listed here:

*   `Explainable AI`, which we covered earlier in this chapter—how you can have Explainable AI in your models using Vertex AI offerings.
*   `Model cards`, which explain what a model does, its intended audience, and who maintains it. A model card also provides insight into the construction of the model, including its architecture and the training data used. Refer to this link to learn more about model cards: `https://modelcards.withgoogle.com/about`.
*   `TensorFlow open source toolkit` to provide model transparency in a structured, accessible way.

Model governance is a core function in companies that provides guidelines and processes to help employees implement the company's AI principles. These principles can include avoiding models that create or enforce bias and being able to justify AI‐made decisions.

Some of the ways you can achieve model governance are as follows:

*   Make sure there is a human in the loop to review model output or prediction for sensitive and high‐impact workloads.
*   Have a `responsibility assignment matrix` for each model by task.
*   Maintain model cards to track model versioning and data lineage.
*   Evaluate the model on benchmark datasets that cover both standard cases and edge cases and validate the model against fairness indicators to help detect implicit bias.
*   Use `what‐if analysis tools` to understand the importance of different data features.
*   All the model readiness best practices from data cleaning, training, and tuning to deploying the model are mentioned in this Google Cloud documentation: `https://cloud.google.com/architecture/guidelines-for-developing-high-quality-ml-solutions`.

## How to Set Up Explanations in the Vertex AI

If you are using a custom‐trained model (TensorFlow, Scikit, or XGBoost), which we covered in [Chapter 8](#c08.xhtml), you need to configure explanations for custom‐trained models (`https://cloud.google.com/vertex-ai/docs/explainable-ai/configuring-explanations-feature-based`) to create a model that supports Vertex Explainable AI. For an AutoML tabular classification or regression, you do not need any specific configuration to use Vertex Explainable AI (`https://cloud.google.com/vertex-ai/docs/explainable-ai/getting-explanations`).

After having a model resource with Explainable AI created, you can perform the following explanations:

*   **Online explanations**: Synchronous requests to the Vertex AI API, similar to online predictions that return predictions with feature attributions. For online explanations, instead of sending a `projects.locations.endpoints.predict` request to the Vertex AI API, send a `projects.locations.endpoints.explain` request.

*   **Batch explanations:** Asynchronous requests to the Vertex AI API that return predictions with feature attributions. Batch explanations are an optional part of batch prediction requests. To get batch explanations, set the generateExplanation field to true when you create a batch prediction job.
