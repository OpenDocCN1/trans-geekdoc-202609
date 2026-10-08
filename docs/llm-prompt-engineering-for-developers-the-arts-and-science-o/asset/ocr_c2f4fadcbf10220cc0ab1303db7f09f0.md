```
```python
from langchain.prompts.example_selector.base import BaseExampleSelector
from typing import Dict, List
import numpy as np

class CustomExampleSelector(BaseExampleSelector):

    def __init__(self, examples: List[Dict[str, str]]):
        self.examples = examples

    def add_example(self, example: Dict[str, str]) -> None:
        """Add an example to the list of examples."""
        self.examples.append(example)

    def select_examples(self, input_variables: Dict[str, str]) -> List[dict]:
        """Add your custom logic here."""
        return self.examples
```
```

Let's add logic to the selector that selects examples based on the sentiment of the user's input.

If the user's input is positive, the selector will select examples with positive sentiment. If the user's input is negative, the selector will try to give the user some encouragement and support by selecting examples with positive sentiment.

```
```python
from langchain.prompts.few_shot import FewShotPromptTemplate
from langchain.prompts.prompt import PromptTemplate
from langchain.prompts.example_selector.base import BaseExampleSelector
from typing import Dict, List
from textblob import TextBlob

examples = [
    {
        "question": "I just got promoted at work! Isn't that great?",
```