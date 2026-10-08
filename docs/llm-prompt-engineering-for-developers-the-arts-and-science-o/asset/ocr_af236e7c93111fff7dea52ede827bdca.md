```
def format(self, **kwargs) -> str:
    # Generate the prompt to be sent to the language model
    prompt = PROMPT.format(
        pet_description=kwargs["pet_description"],
    )
    return prompt

def _prompt_type(self):
    return "pet-name-generator"
```

```
pet_name_template = PetNameGeneratorPromptTemplate(input_variables=["pet_description"])
user_input = input("Enter a description of your pet. e.g. 'A small, fluffy dog.'\n")
pet_description = user_input.strip().lower()
prompt = pet_name_template.format(pet_description=user_input)
print(prompt)
```

# ## 16.10 - Few-Shot Prompt Templates

To create a few-shot prompt template, we need to use the FewShotPromptTemplate class, which is a prompt template that contains a few shot examples.

In the following example, we want the AI to answer questions in the style of Morpheus from the Matrix movie.