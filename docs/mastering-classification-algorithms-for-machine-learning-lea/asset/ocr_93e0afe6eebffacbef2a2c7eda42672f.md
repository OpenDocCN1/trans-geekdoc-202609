# Function to remove Stop Words

```
def removeStopWords(text):
    # splitting strings into tokens (list of words)
    tokens = word_tokenize(text)
    tokens = [token.strip() for token in tokens]
    # filtering out the stop words
    filtered_tokens = [token for token in tokens if token not in stopWordList]
    filtered_text = ' '.join(filtered_tokens)

    return filtered_text
```

We can test the function removeStopWords().

removeStopWords("This is a test of Stop Word remover".lower())

‘test stop word remover’

# Removing special characters

In textual analysis, we are generally concerned about the text’s words. However, there can be exceptions based on the nature of the analysis. Special characters are often removed from the text so that only words remains. We must decide at what stage we eliminate the special characters. Special characters are parts of important text pieces, like those included in an email address, hashtags, URLs, references to persons, etc.

Removing special characters means that we need to retain only alphabets and numbers and remove all else. So, we can substitute anything which is not an alphabet or a number with an empty string. For substitution, we can use the **re** library available in Python.

```
import re

def removeSpecialCharacters(text):
```