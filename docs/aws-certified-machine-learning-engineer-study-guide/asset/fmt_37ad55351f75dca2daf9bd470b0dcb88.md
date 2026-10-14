
## Featurize Datetime

It’s best practice to start the feature engineering process for time-series data by disambiguating date/time features. Date/time features are created from the `timestamp` column and provide an optimal way for ML engineers to start the feature engineering process. The *Featurize datetime* time-series transformation lets us break down a date/time feature by adding the `date_month`, `date_day`, `date_week_of_year`, `date_day_of_year`, and `date_quarter` new features to our dataset. Because we’re providing the date/time components as separate features, we enable ML algorithms to detect patterns for improving prediction accuracy.

## Encode Categorical

Date/time features aren’t limited to integer values. You may also choose to consider certain extracted date/time features as categorical variables and represent them as one-hot-encoded features, with each column containing binary values. To do so, leverage the *One-hot encode* transformation. The newly created `date_quarter` feature contains values from 0 to 3 and can be one-hot encoded using four binary columns, one column for each of the four quarters.

## Lag Feature

To increase model accuracy, it is best practice to create *lag features* for the target variable (or label). Lag features are values at prior timestamps that are helpful in predicting future values. They also help identify autocorrelation (also known as *serial correlation*) patterns in the residual series by quantifying the relationship of the observation with observations at previous time steps. Autocorrelation is similar to regular correlation but between the values in a series and its past values. Amazon SageMaker Data Wrangler provides the *Lag features* transformation, which helps create multiple lag features over a specified window size.

## Rolling Window Features

Amazon SageMaker Data Wrangler implements automatic time-series feature extraction capabilities using the open-source `tsfresh` package. With the time-series feature extraction transformation, you can automate the feature extraction process. This eliminates the time and effort otherwise spent manually implementing signal processing libraries. For the exam, you need to know that features can be extracted using the *Rolling window features* transformation, which computes statistical properties across a set of observations defined by the window size.

After feature engineering the time-series dataset, we are ready to use the transformed dataset as input for a forecasting ML algorithm.

# Techniques for Unstructured Data

Unstructured data, such as images, text, audio, and videos, doesn’t fit neatly into tables and often lacks a predefined format. AWS offers a comprehensive ecosystem of products and services that make feature engineering for unstructured data more manageable and efficient.

In the upcoming sections, we will cover the techniques you need to know for the exam that apply to image and textual data.

## Feature Engineering for Image Data

Just like structured data, feature engineering for image data is a critical step in developing effective ML models. This process involves extracting meaningful features from images, such as edges, textures, and colors, to improve the performance of image recognition and classification tasks by providing the model with more relevant information about the data.

For example, at the beginning of the chapter, we used an image of a car ([Figure 3.4](#c003.xhtml#c03-fig-4)) to show you what features could be extracted from this unstructured data.

To perform feature extraction on images, you primarily leverage pre-trained vision models within Amazon SageMaker JumpStart, often by processing them through a convolutional neural network (CNN) and retrieving the resulting feature vectors. These pre-trained vision models include models for object detection, image classification, and many others.

You can also use services like Amazon Rekognition for basic image analysis and feature extraction, depending on your use case. Amazon Rekognition can detect objects, scenes, text, and faces in images, providing high-level features without the need for extensive manual effort. For instance, Amazon Rekognition can identify and extract features such as labels and bounding boxes around objects, which are essential for tasks like object detection and image classification.

Once features are extracted, transforming them into a suitable format is essential. Amazon SageMaker Data Wrangler allows you to perform exploratory data analysis (EDA) and apply transformations like normalization and dimensionality reduction. This step ensures your features are optimized for model training. For example, you can normalize pixel values to a common scale or apply PCA to reduce the dimensionality of your feature set.

Efficiently storing and managing your engineered features is crucial for streamlined workflows. As you learned at the beginning of the chapter, Amazon SageMaker Feature Store provides a centralized repository for feature storage, making it easy to share and reuse features across different models and projects. This ensures consistency and saves time, as you don’t have to re-extract features for every new model.

## Feature Engineering for Textual Data

In today’s data-driven world, textual data is everywhere, from social media posts to customer reviews and beyond. Extracting meaningful insights from this unstructured data requires effective feature engineering. AWS provides a powerful ecosystem of products and services to streamline this process and turn raw text into valuable features for ML models.

Amazon Comprehend is a powerful tool for extracting high-level features from text. It can detect entities, key phrases, sentiment, and language, providing rich insights without extensive manual effort. Additionally, Amazon Textract can extract text from documents, turning unstructured data into structured information.

For more customized feature extraction, Amazon SageMaker offers built-in algorithms and frameworks. These algorithms can be used to train models and extract specific features like word embeddings (e.g., Word2Vec) or perform topic modeling (e.g., Latent Dirichlet Allocation). These algorithms will be discussed in detail in [Chapter 4](#c004.xhtml#c004).

The following are some essential techniques you need to know for the exam.

### Tokenization

Tokenization is the process of splitting text into smaller units, such as words or phrases, called *tokens*. This is the first step in preparing text data for modeling.

For example, the sentence `“Machine learning is fascinating”` is tokenized into `[“Machine”, “learning”, “is”, “fascinating”]`.

Tokenization is a key component used by Amazon Bedrock foundation models (FMs) to understand and process user prompts. By breaking down the input text into smaller tokens, these models can effectively interpret the meaning and context of the user’s request. For example, a prompt like `“Generate an image of a sunset”` would be divided into individual words and symbols, allowing the model to analyze each element and understand the overall directive. This token-based approach ensures that the model can handle complex and nuanced instructions with high accuracy and relevance.
