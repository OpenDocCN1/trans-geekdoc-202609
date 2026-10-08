```
# initialize the model
llm = ChatOpenAI(
    temperature=1.2,
)

# get the response
chain = LLMChain(
    llm=llm,
    prompt=prompt,
)

print("AI: " + chain.run(question))
```

In this example, we used the `SemanticSimilarityExampleSelector`. However, LangChain provides other example selectors. We are going to explore some of them.

# 16.11.1 - NGram Overlap Example Selector

`NGramOverlapExampleSelector` selects examples based on the number of overlapping n-grams between the input and the examples.

> The n-gram overlap score is a metric used to measure the similarity between two sequences of text by comparing the overlapping n-grams between them. An n-gram is a contiguous sequence of n items (e.g., words, characters) from a given text or speech. This metric is often used in tasks like text similarity, plagiarism detection, and machine translation evaluation.

For instance, consider the 2-grams (or bigrams) for the sentence “I love cats”:

+   - I love ice-cream

https://python.langchain.com/docs/modules/model_io/prompts/example_selectors/ngram_overlap
https://en.wikipedia.org/wiki/N-gram