and increases the chances of finding the correct answer. This file named “`test_socratic.jsonl`”$^\text{41}$ on the OpenAI GitHub repository is a good example.

Let’s ask OpenAI text-davinci-002 the following question:

> If there are 3 cars in the parking lot and 2 more cars arrive, 1 car leaves, 15 cars arrive and 8 leave, how many cars are in the parking?

This is the Python code:

```
import openai
import os

openai.api_key = os.getenv("OPENAI_API_KEY")

prompt = """
Q: If there are 3 cars in the parking lot and 2 more cars arrive, 1 car\
leaves, 15 cars arrives and 8 leaves, how many cars are in the parking
?"
A:
"""
# the answer should be: 3 + 2 - 1 + 15 - 8 = 11

response = openai.Completion.create(
    engine="text-davinci-002",
    prompt=prompt,
    temperature=0.5,
    max_tokens=260
)
print(response.choices[0].text.strip())
```

The answer is incorrect as it returned:

$^\text{41}$https://github.com/openai/grade-school-math/blob/master/grade\_school\_math/data/test\_socratic.jsonl