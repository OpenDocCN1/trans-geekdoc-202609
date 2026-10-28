
using word embeddings and assume their POS tags are closest to the neighbors in the embedding space.

- **Unsupervised learning**: If you know the context in which a word is likely to be used, then find words that are most similar to it and cluster them, then you assign the most likely POS tag to the unknown word by using either unsupervised or semi-supervised learning.
- **Hybrid approaches**: Integrate several techniques in order to mitigate the impact of unknown words at different levels, for instance, using the rule-based tagging in combination with the methods based on the contextual information or embeddings.

Therefore, the decision-making process for dealing with unknown words in POS tagging depends on both the linguistic approaches and the machine learning methods so that the POS taggers shall perform well in different situations.

## Question 11: How can deep learning techniques like NNs improve POS tagging accuracy?

**Answer**: Deep learning techniques, particularly NNs, can enhance POS tagging accuracy in several ways:

- **Representation learning**: NNs are capable, by design, of learning meaningful representations of words from the raw text, which is useful in capturing linguistic features that are important for accurate POS tagging.
- **Contextual information**: Some RNN types or transformers may be trained to make better use of context word vectors to address more extended dependencies for correct tagging.
- **Feature extraction**: An effective POS tagger uses NN to extract features from input data without human intervention: it reveals complex dependencies between words and POS tags.
- **End-to-end learning**: Sequence-to-sequence mapping in deep learning models eliminates the consecutive steps of preprocessing for tagging sequences to POS tags.
- **Transfer learning**: POS tagging tasks can be performed with pre-trained models, which are fine-tuned on specified problems; in such a way, knowledge from the language modeling is used, which can lead to better results when dealing with limited-labeled data.

In general, deep learning approaches provide efficient tools for POS tagging accuracy improvements due to automatic representations, contextual information, features extracting, end-to-end learning, and transfer learning from pre-trained models.

## Named entity recognition

NER is one of the significant NLP procedures that involves the identification of named entities in the text along with categorization into people, organizations, places, or dates. It has significance in several applications, such as information search, information extraction, and content analysis. Unlike other NLP sub-tasks, NER improves context handling for machine learning models, search relevance for search engines, and data categorization. With its broad outline of the topics and their significance, understanding NER is crucial to the emergence of smarter and more efficient identifying language text by using appropriate information or data from a larger entity of language text of considerably less importance.

### Question 1: What are some examples of named entities commonly identified by NER systems?

Answer: Examples of named entities commonly identified by NER systems:

- **Person**: *John Smith, Mary Johnson, Barack Obama*
- **Organization**: *Google, Microsoft, United Nations*
- **Location**: *New York City, London, Eiffel Tower*
- **Date**: January 1, 2023, 12th May, 2024
- **Time**: 3:00 PM, 10 minutes, 2 hours
- **Money**: $100, €50, £75
- **Percent**: 10%, 50%, 75.5%
- **Quantity**: 5 kilograms, 100 meters, 20 units
- **Product**: *iPhone, Coca-Cola, Toyota Prius*
- **Event**: World Cup, Olympics, Conference
- **Artifact**: Smartphone, Laptop, Telescope
- **Language**: English, Spanish, Mandarin

NER systems aim to identify and classify these named entities accurately in text data, facilitating various NLP tasks and applications.

### Question 2: What are the different types of named entities typically recognized by NER systems?

Answer: Most of the NER systems available can identify different forms of named entities in text data. Here are the different types commonly recognized:

- **Person**: Proper nouns referring to persons, actual or imaginary characters, and *Maryland* terms of honorable reference, such as Mr. or Dr.
- **Organization**: Firm and corporate names, as well as organizational and official designations, such as those of institutions, agencies, governments, ministries, and other similar organizations.
- **Location**: Geographical Names of places, like countries, cities, regions, address, landmarks, geographical features etc.
- **Date**: Expressions of dates, such as those that refer to day, month, year, and an interval of time between any two dates.
- **Time**: Any uses of the concept of time, such as particular time, length, or even period.
- **Money**: Measures of money and other indicators of monetary and financial values.
- **Percent**: Parts or fractions whereby the given assessment or evaluation is specified in text.
- **Quantity**: Semantic relations referring to measures, numerical counts, or amounts.
- **Product**: Some of the categories under this section include; product and service names, merchandise, and products, brands, and goods in the market.
- **Event**: To name some of them, the name of special circumstances, celebrations, seminars, gatherings, or other important situations.
- **Artifact**: Civilian names refer to tangible creations by humans or civilizations, such as inventions, technologies, tools, products, architectural designs, or structures.
- **Language**: All names of languages or dialects, as well as other linguistic terms used in the text.

These are some types of named entities that are commonly identified by the NER systems, though some other specific systems might identify other types in accordance with the domain of operation and the necessity.

### Question 3: Can you explain the difference between rule-based and machine learning-based approaches to NER?

**Answer:** Here is a brief explanation of the difference between rule-based and machine learning-based approaches to NER:

The rule-based approach works on the basis of certain language rules and/or pattern to recognize the named entities in the textual data. The following points discuss the pros and cons of the rule-based approach:

- **Advantages:**
  - **Transparency**: The rules are clear and explicit, and the system is understandable.
  - **Customizability**: It can also be easily configurable for different domains or languages using rules.
  - **Efficiency**: Most efficient when the patterns are pre-specified or easily identifiable in terms of computation.
- **Limitations:**
  - **Limited generalization**: Fails with patterns that are not necessarily clear or that cannot be captured by a rule.
  - **Maintenance overhead**: Must be updated and managed manually in order to assure that the rules are appropriate and up to date.
  - **Scalability**: These may not generalize well to other large datasets or other domains.

Machine learning-based approach analyzes the message content and applies pre-trained statistical models of the usually labeled data that enable the program to detect patterns that are characteristic of named entities. The following points discuss about the pros and cons of the ML-based approach:

- **Advantages:**
  - **Generalization**: This is gained from data and helps in enhancing the flexibility of recognizing many patterns.
  - **Performance**: There still can be higher accuracy by using these methods, especially when dealing with the complications of data.
  - **Scalability**: Can easily generalized for large data sizes and for different types of domains.
- **Limitations:**
  - **Black box nature**: Not as transparent, as this can be seen from rule-based systems.
  - **Data dependency**: Depends on categorized learning data.
  - **Computational complexity**: This can be computationally expensive, as with any computation involving deep learning models.

To sum up, the rule acquisition strategy provides interpretability and time efficiency but might provide low scalability. On the other hand, the approaches based on machine learning give far better scalability and performance at the price of interpretability and larger number of data and time for the calculations. This decision
