# Structure

In this chapter, we will discuss the following topics:

+   - Count vectorizer
- TF-IDF vectorizer

# Count vectorizer

Count vectorizer, we count the number of times a word appears in a given text.

For example, suppose we have the text - “I went to the Ice Cream Parlor to have an Ice Cream...\ Suppose that this text was sent via SMS. This would be one SMS in our complete dataset of many SMS. We would call this data point a document of this full dataset. So, the dataset would contain many documents. The entire collection of documents is called the Corpus.

For a comprehensive discussion, let us consider that in the initial corpus, we have another document as “Great. Did you enjoy the Ice Cream?” . So, now our corpus has two documents, as shown in Table Annexure 6.1:

| Document ID | Document |
| 1 | I went to the Ice Cream Parlor to have an Ice Cream. |
| 2 | Great. Did you enjoy the Ice Cream? |

Table Annexure 6.1: Example Dataset

To create the count vectorizer for the data in Table Annexure 6.1, we need to identify all the unique words in the document and count how many times each word appears in each document, as shown in Table Annexure 6.2 (we will remove all the punctuation marks from the text before this exercise).

| Word | Document 1 | Document 2 |
| I | 1 | 0 |
| went | 1 | 0 |
| To | 1 | 0 |
| The | 1 | 1 |
| Ice | 2 | 1 |
| cream | 2 | 1 |
| parlor | 1 | 0 |
| To | 1 | 0 |