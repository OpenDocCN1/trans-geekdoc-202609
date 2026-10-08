# Amazon Comprehend

NLP has gained significant interest across different industries in solving a range of business problems, such as automatic document processing, text summarization, document understanding, and document management and retrieval. Amazon Comprehend** is an AI service that can perform NLP analysis on unstructured text documents. At its core, Amazon Comprehend provides the following main capabilities:

+   - **Entity recognition**: Entities are the who, what, where, and when of text analytics. Entities are the most important parts of a sentence as they identify the components in a sentence. Examples of entities are proper nouns such as a person, place, or product. Entities can be used to create document indexes and identify key information or relationships across documents.

Comprehend provides APIs (for example, `DetectEntities`) for detecting entities with its built-in recognition models. It can detect entities such as people, places, organizations, and dates from the input text.

You can also use Comprehend to train a custom entity recognizer for your custom entities if the built-in models do not meet your requirements. To train a custom entity recognizer, you can use the `CreateEntityRecognizer` API with your training data in the following formats:

+   - **Annotation**: You provide the locations of entities (beginning and end offsets of target characters) in a large number of documents, along with the entity type for each pair of offsets. This helps Comprehend train on both the entities and the context they are in.

+   - **Entity list**: You provide a list of entities and their entity types in plaintext and Comprehend will train to detect these specific entities.

You can evaluate the custom model using the metrics emitted by a Comprehend custom model training job. Example evaluation metrics include precision, recall, and F1 scores. Additional details on the evaluation metrics for Comprehend can be found at `https://docs.aws.amazon.com/comprehend/latest/dg/custom-metrics.html`.

Once the model has been trained, you have the option to deploy the model behind a private prediction endpoint to serve predictions.

+   - **Sentiment analysis**: Comprehend can detect sentiment in text with its `DetectSentiment` API. Sentiment analysis is widely used in many business use cases, such as analyzing customers' sentiment in customer support calls or understanding customers' perceptions toward products and services in reviews.