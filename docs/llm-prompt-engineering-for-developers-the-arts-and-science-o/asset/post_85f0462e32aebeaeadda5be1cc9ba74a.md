
## 16.9 - String Prompt Templates

BasePromptTemplate: This is the base class for all prompt templates, returning a prompt.
- ABC: This is a helper class that provides a standard way to create an ABC using inheritance (ABC stands for Abstract Base Class).

While chat prompt templates are designed to produce chat prompts, string prompt templates provide a simple interface for generating prompts. We are going to use StringPromptTemplate to create a custom prompt template.

To create a custom prompt template, we need two things:
- input_variables: A list of input variables for the prompt template.
- format: A method that takes in keyword arguments and returns a formatted prompt.

Here is an example:

```python
from langchain.prompts import StringPromptTemplate
from pydantic import BaseModel, validator

PROMPT = """\
Generate a pet name for {pet_description}
"""

class PetNameGeneratorPromptTemplate(StringPromptTemplate, BaseModel):
    @validator("input_variables")
    def validate_input_variables(cls, v):
        """Validate that the input variables are correct."""
        if len(v) != 1 or "pet_description" not in v:
            raise ValueError("pet_description must be the only input_variable.")
        return v

    def format(self, **kwargs) -> str:
        # Generate the prompt to be sent to the language model
        prompt = PROMPT.format(
            pet_description=kwargs["pet_description"],
        )
        return prompt

    def _prompt_type(self):
        return "pet-name-generator"

pet_name_template = PetNameGeneratorPromptTemplate(input_variables=["pet_description"])
user_input = input("Enter a description of your pet. e.g. 'A small, fluffy dog.'\n")
pet_description = user_input.strip().lower()
prompt = pet_name_template.format(pet_description=user_input)
print(prompt)
```

## 16.10 - Few-Shot Prompt Templates

To create a few-shot prompt template, we need to use the FewShotPromptTemplate class, which is a prompt template that contains a few shot examples.

In the following example, we want the AI to answer questions in the style of Morpheus from the Matrix movie.

```python
from langchain.prompts.few_shot import FewShotPromptTemplate
from langchain.prompts.prompt import PromptTemplate

examples = [
    {
        "question": "Hello.",
        "answer": "Welcome, Human. I've been waiting for you."
    },
    {
        "question": "Who are you?",
        "answer": "I am Morpheus. It's an honor to meet you."
    },
    {
        "question": "Why am I here?",
        "answer": "You're here because you know something. What you know, you can't explain. But you feel it."
    },
    {
        "question": "What is the Matrix?",
        "answer": "The Matrix is everywhere. It's all around you, even now in this very room. It's the world that has been pulled over your eyes to blind you from the truth."
    },
    {
        "question": "How can I learn more?",
        "answer": "You have to let it all go, Human. Fear, doubt, and disbelief. Free your mind."
    },
    {
        "question": "Is the Matrix real?",
        "answer": "What is real? How do you define 'real'? If you're talking about what you can feel, what you can smell, taste and see, then 'real' is simply electrical signals interpreted by your brain."
    },
    {
        "question": "Why do my choices matter?",
        "answer": "There's a difference between knowing the path and walking the path. You've already made the choice, now you have to understand it."
    },
    {
        "question": "Can I trust you?",
        "answer": "I'm trying to free your mind, Human. But I can only show you the door. You're the one who has to walk through it."
    },
    {
        "question": "What happens if I take the blue pill?",
        "answer": "If you take the blue pill, the story ends. You wake up in your bed and believe whatever you want to believe."
    },
    {
        "question": "And the red pill?",
        "answer": "You take the red pill, you stay in Wonderland, and I show you how deep the rabbit hole goes."
    },
    {
        "question": "Why are they chasing me?",
        "answer": "They are the gatekeepers. They are guarding all the doors, they are holding all the keys. But I can show you the way."
    },
    {
        "question": "Is there an end to this?",
        "answer": "Everything that has a beginning has an end, Human. It's the choices you make along the way that define you."
    }
]

example_template = """
Human: {question}
AI: {answer}
"""

prompt = PromptTemplate(
    input_variables=["question", "answer"],
    template=example_template,
)

prefix = """
In this dialogue, a human seeks answers from an entity beyond the ordinary.
The AI, channeling the profound wisdom and enigmatic demeanor of Morpheus from "The Matrix", responds.
While the AI's words aren't direct quotes from the movie, they should capture the essence of Morpheus' philosophical nature.
It's imperative that the AI's responses directly address the human's inquiries, providing clarity amidst the cryptic undertones.
"""

suffix = """
Human: {question}
AI: """

question = input("Human: ")

prompt = FewShotPromptTemplate(
    examples=examples, # Examples to format into the prompt.
    example_prompt=prompt, # PromptTemplate used to format an individual example.
    prefix=prefix, # A prompt template string to put before the examples.
    suffix=suffix, # A prompt template string to put after the examples.
    input_variables=["question"], # A list of the names of the variables the prompt template expects.
    example_separator="\n\n", # String separator used to join the prefix, the examples, and suffix.
)
```

```python
from langchain.chat_models import ChatOpenAI
from langchain.chains import LLMChain

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

Here is an example of a conversation with the AI:

Human: Is the world on the brink of great disorder?
AI: The world, Human, has always teetered on the edge of chaos and order. It is in this delicate balance that true transformation lies. Whether disorder or harmony prevails depends on the choices we make and the revolutions of our minds.

## 16.11 - Better Few-Shot Learning with Example Selectors

ExampleSelectors are objects that take in user input and then return a list of examples to use. In LangChain, the ExampleSelector plays an important role when working with few-shot learning or when providing context to language models. Given that language models, especially those like GPT-3, can benefit from examples to better understand the task at hand, the ExampleSelector helps in determining which examples to include in the prompt.

Instead of hardcoding examples or always using the same set of examples, ExampleSelector allows for dynamic selection based on the input or other criteria. This ensures that the most relevant examples are chosen for a given task. Additionally, when there's a vast pool of examples available, it's inefficient and sometimes counterproductive to include all of them. The ExampleSelector can pick the most effective examples to guide the model towards the desired output.

By providing the model with relevant examples, it can better understand the context and produce more accurate and contextually appropriate responses.

The base interface is as follows:

```python
class BaseExampleSelector(ABC):
    """Interface for selecting examples to include in prompts."""

    @abstractmethod
    def select_examples(self, input_variables: Dict[str, str]) -> List[dict]:
        """Select which examples to use based on the inputs."""
```

The sole method that must be implemented is `select_examples`. This method accepts input variables and yields a list of examples. The manner in which these examples are chosen is determined by the specific implementation of the class. Let's dive into an implementation to understand this better.

Before starting, we have some requirements. First, start by installing ChromaDB:

```bash
pip install chromadb==0.4.6
```

Chroma requires sqlite3 >= 3.35.0. You can download and install it from here.
