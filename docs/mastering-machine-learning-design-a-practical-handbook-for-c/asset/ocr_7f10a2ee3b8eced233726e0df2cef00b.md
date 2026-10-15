```
```python
from nltk.stem import WordNetLemmatizer

stemmer = PorterStemmer()
lemmatizer = WordNetLemmatizer()

def normalize_text(text):
    # Choose stemming or lemmatization based on your needs
    # stemmed_text = stemmer.stem(text)
    lemmatized_text = lemmatizer.lemmatize(text)
    return lemmatized_text

normalized_data = data["text"].apply(normalize_text)

# or

normalized_text_data = normalize_text(text_data)
```
```

+   - **Stop word removal (Optional):** Remove common words that don't contribute much to the meaning:

```
```python
from nltk.corpus import stopwords

stop_words = stopwords.words("english")

def remove_stopwords(text):
    tokens = text.split()
    filtered_text = [word for word in tokens if word not in stop_words]
    return " ".join(filtered_text)

filtered_data = data["text"].apply(remove_stopwords)

# or

filtered_text_data = remove_stopwords(text_data)
```
```

# 3. Feature Engineering: