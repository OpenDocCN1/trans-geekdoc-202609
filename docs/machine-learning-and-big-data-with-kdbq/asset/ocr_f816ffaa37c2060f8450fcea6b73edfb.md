# 524

# MACHINE LEARNING

and explore the content (list of the output):

daVinci

> "There is no human experience that can be termed true science unless it can be mathematically demonstrated"; And if thou sayeth that the sciences which begin and end in the mind are true, this cannot be conceded, but must be denied for many reasons, and firstly because in such mental discourses experience is eliminated, and without experience there can be no certainty";

The sentences can contain symbols we do not understand. In addition, we convert everything lower case as the cases do not make a difference for us. We clean the text:

```
daVinci:lower(x where not in (""\";"\!\
```

Further, there are duplicate sentences within sentences; we remove them as:

We can explore the content of the corpus after we have performed the cleaning of the text:

daVinci

> "there is no human experience that can be termed true science unless it can be mathematically demonstrated";and if thou sayeth that the sciences which begin and end in the mind are true this cannot be conceded but must be denied for many reasons and firstly because in such mental discourses experience is eliminated and without experience there can be no certainty";

The sentences are now standardised and ready to be analysed in terms of word frequency.

Further, the notion of a document is played by a single sentence. The corpus is then the set of all sentences within the sample text specified above. This approach does not require dealing with excessively large data, which would not be suitable for the pedagogical purpose of the book (but reasonable in practical circumstances using q).

# 27.1.2 Frequency Counting

Our objective is to identify sentences – which play the role of documents – that carry the unique, informative content. Imagine we face a problem to choose a few sentences from the entire book (chapter in our case) which carry the most unique content. One possible way is to focus on sentences with different words. In addition, we extend the search question as follows. We are looking for a few sentences which contain a particular word or combination of words such that those sentences will tell us something unique