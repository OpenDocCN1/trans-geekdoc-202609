```
- The Rottweiler is a breed of domestic dog, regarded as medium-to-large\ ne or large. The dogs were known in German as Rottweiler Metzgerhund, meaning Rottweil butchers' dogs, because their main use was to herd livestock and pull carts laden with butchered meat to market. Read more here: https://dogbreeds.wiki/rottweiler
"""
```

```
print(pipeline_prompt.format(
role_description=role_description,
instruction_details=instruction_details,
examples=examples
))
```

This is how the final code looks like:

```
from langchain.prompts.pipeline import PipelinePromptTemplate
from langchain.prompts.prompt import PromptTemplate
```

```
# Define the full template structure
full_template = """
{role}

{instructions}

{examples}
"""
```

```
full_prompt = PromptTemplate.from_template(full_template)
```

```
# Define individual components
```

```
# Define the role component
role_template = """Role: You are a {role_description}."""
role_prompt = PromptTemplate.from_template(role_template)
```

```
# Define the instructions component
```