
are building a sentiment classifier or clustering documents.
Let us look at an example of image preprocessing:
Preprocessing typically involves resizing, normalizing, and converting images into tensors when working with image data, especially for classification or object detection tasks.
The following transformation pipeline prepares image data for deep learning models:

```
from torchvision import transforms
transform = transforms.Compose([
    transforms.Resize((128, 128)),
    transforms.ToTensor(),
    transforms.Normalize((0.5,), (0.5))
])
```

These preprocessing steps standardize image dimensions and pixel intensity values, ensuring that the data is suitable for feeding deep learning models.

# Role of AI tools

Tasks like text normalization, image resizing, or even spectrogram generation for audio data are often repeated across projects. AI-assisted programming tools like GitHub Copilot can accelerate these processes by auto-suggesting complete code blocks based on context. Meanwhile, ChatGPT helps developers understand why a particular method is used, offering alternative strategies and tailored recommendations for use cases.
By streamlining repetitive tasks and offering intelligent guidance, AI tools bridge the gap between structured and unstructured data processing, enabling developers to focus on building smarter, more adaptive ML systems.

# Automating feature extraction and selection

In machine learning, features are the foundation on which models are built. They represent the variables from which algorithms learn patterns, make predictions, and classify data. However, not all features contribute equally; some improve accuracy and offer valuable signals, while others introduce noise or, worse, encode hidden biases that can mislead the model.

That is where the twin processes of feature extraction and feature selection become essential. Feature extraction focuses on creating new, meaningful features from raw or unstructured data; for instance, generating numerical metrics from text or timestamps. On the other hand, feature selection involves filtering out irrelevant or redundant variables, ensuring the model trains only on what truly matters.

When done right, these steps can dramatically improve model performance, reduce overfitting, and speed up training, especially when dealing with high-dimensional datasets. However, manually engineering and selecting features can be time-consuming and error-prone, requiring domain expertise and technical precision.

Enter AI-assisted programming tools like GitHub Copilot and ChatGPT. These tools have transformed the feature engineering workflow. Copilot can anticipate transformation patterns and generate relevant code snippets on the fly, while ChatGPT provides contextual advice, helping you choose between techniques like polynomial expansion, encoding strategies, dimensionality reduction, or interaction terms based on your dataset and goal.

Whether you are building a regression model, a classifier, or exploring unsupervised learning, AI tools assist in automating the repetitive parts and elevating the quality and efficiency of your feature engineering process. By reducing manual overhead and supporting informed decision-making, these tools empower developers to craft better models faster and more reliably.

# Example dataset

Let us explore a simplified example based on an employee dataset to demonstrate how feature extraction and selection work in practice. This mock dataset contains basic employee attributes such as department, salary, experience, joining date, and even free-text comments. It provides a well-rounded foundation for experimenting with structured and unstructured feature engineering tasks.
Here is how the dataset is created:

```python
import pandas as pd
data = {
  'EmployeeID': [101, 102, 103, 104],
  'Department': ['Sales', 'HR', 'Engineering', 'HR'],
  'Salary': [58000, 62000, 72000, 60000],
  'Experience': [2, 4, 6],
  'JoinDate': ['2020-05-10', '2019-08-15', '2018-03-20', '2021-01-01'],
  'Comments': [
    'Hardworking and punctual',
    'Excellent team player',
    'Technically sound and innovative',
    'Quick learner'
  ]
}
df = pd.DataFrame(data)
```

This dataset allows us to showcase several types of feature engineering techniques:

- Feature extraction from text (**Comments**) and dates (**JoinDate**).
- Categorical encoding for **Department**.
- Numeric transformations or binning for **Experience** and **Salary**.
- Feature selection to identify which variables most influence downstream predictions.

In the following subsections, we will apply traditional and AI-assisted approaches to automate the feature engineering process on this dataset.

# Feature extraction from categorical and text data

Categorical and text features often hold rich, meaningful information, but must be transformed into numerical formats before machine learning models can use them effectively. This transformation is a core part of feature extraction, and the proper technique depends on the data's nature and the complexity of the model used.

# Traditional approach

One of the most common techniques for categorical variables like **Department** is one-hot encoding, which creates a separate binary column for each category.

The following line applies one-hot encoding to the **'Department'** column:

```python
# One-hot encoding for Department
df = pd.get_dummies(df, columns=['Department'], drop_first=True)
```

When working with free-text fields like **Comments, term frequency-inverse document frequency (TF-IDF)** is often used to extract key terms that can be fed into models.

The following code uses TF-IDF to extract key terms from the 'Comments' column:
```python
from sklearn.feature_extraction.text import TfidfVectorizer
vectorizer = TfidfVectorizer(stop_words='english', max_features=10)
X_text = vectorizer.fit_transform(df['Comments'])
```

TF-IDF helps quantify the importance of words in each comment while reducing the impact of commonly used words like and or or or the.

# AI assistance

AI-assisted tools significantly streamline and enrich this process:

- GitHub Copilot can automatically suggest code snippets for common transformations such as get_dummies() and TfidfVectorizer, including helpful parameters like stop_words='english' or max_features.
- ChatGPT provides intelligent recommendations tailored to your dataset and modeling needs. For example:
  - It might suggest label encoding for ordinal variables where the order of categories matters.
  - For categorical columns with many unique values (e.g., more than 100), frequency encoding or target encoding can be recommended to avoid creating an unwieldy number of new columns.
  - It helps you choose between TF-IDF and CountVectorizer, depending on the dataset size and whether you use linear or tree-based models.

Let us look at an example interaction:

# Prompt: How do I handle a categorical variable with 100+ unique values?

# ChatGPT insight: Use frequency or target encoding instead of one-hot encoding to avoid dimensionality issues and memory inefficiency.

By automating and guiding these choices, AI tools help developers efficiently extract meaningful features from categorical and data—without sacrificing performance or interpretability.

# Feature extraction from date and time

Date and time fields often contain valuable insights not immediately apparent in their raw form. By extracting meaningful components, such as the year, month, or day of the week, developers can uncover patterns related to seasonality, trends, and behavior over time. These extracted features can improve model performance, especially in time-sensitive applications like sales forecasting, employee attrition analysis, or web traffic prediction.

# Traditional approach

The most common way to derive new features from a date column is using Pandas’ datetime accessor.
Here is a simple example:

```python
df['JoinDate'] = pd.to_datetime(df['JoinDate'])
df['JoinYear'] = df['JoinDate'].dt.year
df['JoinMonth'] = df['JoinDate'].dt.month
df['JoinDayOfWeek'] = df['JoinDate'].dt.dayofweek
```

This snippet extracts the year, month, and day of the week from the JoinDate column. These new features can be used in downstream modeling tasks to understand seasonal trends, weekday-based behavior, and more.

# Cyclical encoding suggested by ChatGPT

While extracting numeric values from date fields is helpful,
