

# 提取和转换文本特征

以下示例演示如何对 CSV 文件中的训练数据进行文本数据清洗和预处理。数据文件位于：`https://github.com/kittenpub/database-repository/blob/main/pandas_training_testdata.csv`

```python
import pandas as pd

# load the training data into a DataFrame
df = pd.read_csv('https://raw.githubusercontent.com/kittenpub/database-repository/main/pandas_training_testdata.csv')

# check the shape of the DataFrame
print("Shape of the DataFrame:", df.shape)

# check the first few rows of the DataFrame
print("First few rows of the DataFrame:")
print(df.head())

# check for missing values
print("Number of missing values in each column:")
print(df.isnull().sum())

# remove rows with missing values
df.dropna(inplace=True)

# convert text to lowercase
df['text'] = df['text'].str.lower()

# remove punctuation
import string
df['text'] = df['text'].apply(lambda x: x.translate(str.maketrans('', '', string.punctuation)))

# remove numbers
df['text'] = df['text'].str.replace('\d+', '')

# remove stopwords
import nltk
nltk.download('stopwords')
from nltk.corpus import stopwords
stop_words = stopwords.words('english')
df['text'] = df['text'].apply(lambda x: ' '.join([word for word in x.split() if word not in stop_words]))

# remove short words
df['text'] = df['text'].apply(lambda x: ' '.join([word for word in x.split() if len(word) > 3]))

# lemmatize the text
nltk.download('wordnet')
from nltk.stem import WordNetLemmatizer
lemmatizer = WordNetLemmatizer()
df['text'] = df['text'].apply(lambda x: ' '.join([lemmatizer.lemmatize(word) for word in x.split()]))

# check the first few rows of the cleaned DataFrame
print("First few rows of the cleaned DataFrame:")
print(df.head())

# save the cleaned DataFrame to a new CSV file
df.to_csv('cleaned_data.csv', index=False)
```

在本例中，我们首先使用 `read_csv()` 方法将训练数据加载到 `DataFrame` 中。随后检查 `DataFrame` 的形状 (`shape`) 以及前几行数据 (`head()`) 以了解数据概况。

接着，使用 `isnull()` 方法检查缺失值，并使用 `dropna()` 方法删除包含缺失值的行。

然后，我们对 `DataFrame` 的 `'text'` 列执行一系列文本清洗和预处理步骤：
- 使用 `lower()` 方法将文本转为小写。
- 使用 `translate()` 方法移除标点符号。
- 使用 `str.replace()` 方法移除数字。
- 使用 NLTK 库的 `stopwords` 语料库移除停用词。
- 使用 `lambda` 函数移除短词（长度 <= 3）。
- 使用 NLTK 库的 `WordNetLemmatizer` 进行词形还原。

最后，检查清洗后 `DataFrame` 的前几行，并使用 `to_csv()` 方法将结果保存到新的 CSV 文件中。

