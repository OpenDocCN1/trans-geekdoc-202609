Let's test the prompt with the OpenAI API:

```
```python
from langchain.prompts.pipeline import PipelinePromptTemplate
from langchain.prompts.prompt import PromptTemplate

# Define the full template structure
full_template = """
{role}

{instructions}

{examples}
"""

full_prompt = PromptTemplate.from_template(full_template)

# Define individual components

# Define the role component
role_template = """Role: You are a {role_description}."""
role_prompt = PromptTemplate.from_template(role_template)

# Define the instructions component
instructions_template = """Instructions: {instruction_details}"""
instructions_prompt = PromptTemplate.from_template(instructions_templ\
ate)

# Define the examples component
example_template = """Examples:
{examples}"""

# Define the example prompt
example_prompt = PromptTemplate.from_template(example_template)

# Combine components into the pipeline
input_prompts = [
```
```