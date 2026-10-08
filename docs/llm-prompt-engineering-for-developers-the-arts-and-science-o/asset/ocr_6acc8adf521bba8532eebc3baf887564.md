```
```python
    }
]

# Example selector that selects examples based on SemanticSimilarity
example_selector = SemanticSimilarityExampleSelector.from_examples(
    examples, # This is the list of examples available to select from. \n

    OpenAIEmbeddings(), # This is the embedding class used to produce e\nbeddings which are used to measure semantic similarity.
    Chroma, # This is the VectorStore class that is used to store the e\nbeddings and do a similarity search over.
    k=1 # This is the number of examples to produce.
)

# Let's create a list of questions to ask the example selector.
questions = [
    "What is real?",
    "How to know that I am not dreaming?",
    "Is there a way to know if I am in a simulation?",
    "What if I am a non-player character in a simulation?",
    "The world is a projection of the mind, can you prove me wrong?",
    "Quantum mechanics is the key to understanding the nature of realit\ny. Do you agree?",
    "Once upon a time, people believed that the Earth was flat. Now we \
know that it is round. What if we are wrong about everything else too?"
,
]

# Let's ask the example selector to select the most similar example to \
each question.
for question in questions:
    # Select the most symantically similar example.
    selected_examples = example_selector.select_examples({"question": q\
uestion})
    print(f"\n-> You asked: {question}\n")
```
```