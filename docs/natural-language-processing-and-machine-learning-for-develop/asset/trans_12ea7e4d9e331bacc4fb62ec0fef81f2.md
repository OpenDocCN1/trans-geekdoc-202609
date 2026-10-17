
cleaned dataset: `['the sf weather is hot and the la weather is hotter']` word: `the` frequency: `2` word: `sf` frequency: `1` word: `weather` frequency: `2` word: `is` frequency: `2` word: `hot` frequency: `1` word: `and` frequency: `1` word: `la` frequency: `1` word: `hotter` frequency: `1` 

## NLTK and Stemmers

[Listing 6.2](#ch06.xhtml#list6.2) displays the contents of `stem_documents1.py` that illustrates how to perform stemming on a sentence with a `PorterStemmer`.

***LISTING 6.2: stem_documents1.py***

```python
import nltk
from nltk.stem import PorterStemmer
from nltk.tokenize import sent_tokenize, word_tokenize

# read file contents:
file = open("data-science-wiki.txt")
my_lines_list = file.readlines()

porter = PorterStemmer()

def stemSentence(sentence):
    token_words = word_tokenize(sentence)
    stem_sentence = []
    for word in token_words:
        stem_sentence.append(porter.stem(word))
        stem_sentence.append(" ")
    return "".join(stem_sentence)

def saveStemmedLines():
    stem_file = open("stem-data-science-wiki.txt", mode="a+", encoding="utf-8")
    for line in my_lines_list:
        stem_sentence = stemSentence(line)
        stem_file.write(stem_sentence)
    stem_file.close()

print(my_lines_list[0])
print("Stemmed sentence:")
x = stemSentence(my_lines_list[0])
print(x)
```

[Listing 6.2](#ch06.xhtml#list6.2) starts by reading the contents of a text file into the variable `my_lines_list`. Next, the variable `porter` is initialized as an instance of the `PorterStemmer` class that is available in NLTK. The next portion of [Listing 6.2](#ch06.xhtml#list6.2) is the definition of the Python function `stemSentence()` that determines the stem of each word in the sentence that is passed into the function.

The next block defines the Python function `saveStemmedLines()` that contains a for loop that iterates through the sentences that have been processed by the function `stemSentence()`. The last portion of [Listing 6.2](#ch06.xhtml#list6.2) invokes the Python function `stemSentence()` with the first sentence in `my_lines_list`, displays the output, and then saves the stemmed text. Launch the code in [Listing 6.2](#ch06.xhtml#list6.2) and you will see the following output:

`'data scienc is an interdisciplinari field that use scientif method , process , algorithm and system to extract knowledg and insight from data in variou form , both structur and unstructur , \[ 1 \] \[ 2 \] similar to data mine . \\n ' , 'data scienc is a '' concept to unifi statist , data analysi , machin learn and their relat method '' in order to '' understand and analyz actual phenomena '' with data . \[ 3 \] It employ techniqu and theori drawn from mani field within the context of mathemat , statist , inform scienc , and comput scienc . \\n '`

## NLTK and Lemmatization

[Listing 6.5](#ch06.xhtml#list6.5) displays the contents of `lemmatizer1.py` that illustrates how to perform lemmatization on a sentence.

***LISTING 6.5: lemmatizer1.py***

```python
import nltk
from nltk.stem import WordNetLemmatizer

wordnet_lemmatizer = WordNetLemmatizer()
sentence = "He eats Chicago deep dish pizzas, and lots of pizzas from Pizzeria Uno!"
punctuations = "?:!.,;"
sentence_words = nltk.word_tokenize(sentence)

for word in sentence_words:
    if word in punctuations:
        sentence_words.remove(word)

print("{0:20}{1:20}".format("Word", "Lemma"))
for word in sentence_words:
    print("{0:20}{1:20}".format(word, wordnet_lemmatizer.lemmatize(word)))
```

[Listing 6.5](#ch06.xhtml#list6.5) initializes the variable `wordnet_lemmatizer` as an instance of the `WordNetLemmatizer` class that is available in NLTK. The variables `sentence` and `punctuations` are initialized, as well as the variable `sentence_words` that consists of the tokens in the variable `sentence`. Next, a loop that removes any punctuation symbols from the variable `sentence_words`. The final code block contains a loop that displays each word in `sentence_words`, along with its lemmatized value. Launch the code in [Listing 6.5](#ch06.xhtml#list6.5) and you will see the following output:

`Word                Lemma He                  He                   eats                eats                 Chicago             Chicago             deep                deep                 dish                dish                 pizzas              pizza               and                 and                 lots                lot                 of                  of                   pizzas              pizza               from                from                 Pizzeria          Pizzeria          Uno              Uno              `

[Listing 6.6](#ch06.xhtml#list6.6) displays the contents of `lemmatizer2.py` that illustrates how to perform lemmatization on a sentence.

***LISTING 6.6: lemmatizer2.py***

```python
# (content omitted for brevity)
```

