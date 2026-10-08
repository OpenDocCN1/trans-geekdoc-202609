```
pip install Jinja2==3.1.2
```

Jinja is an extensible templating engine for the Python programming language. It is designed to be secure, fast, and easy to use. It is inspired by Django's templating system but extends it with an expressive language that gives template authors a more powerful set of tools.

Alternatively, you can use the **Python f-string**$^{62}$ template:

```
from langchain.prompts import PromptTemplate
fstring_template = "What is the difference between {object1} and {object2}?"
prompt = PromptTemplate.from_template(fstring_template)
prompt.format(object1="Asteroid", object2="Meteoroid")
```

F-strings provide a way to embed expressions inside string literals, using minimal syntax.

# ## 16.5 - Partial Prompting

In some cases, you may have a prompt template with one or more variables that you want to fill in later. For example, you may have a template that looks like this:

```
from langchain.prompts import PromptTemplate
prompt = PromptTemplate(template="{var_x}/{var_y}/{var_z}", input_variables=["var_x", "var_y", "var_z"])
partial_prompt = prompt.partial(var_x="a")
partial_prompt = partial_prompt.partial(var_y="b")
partial_prompt = partial_prompt.partial(var_z="c")
print(partial_prompt.format())
```

This could be useful in some scenarios when a variable is not ready yet. For example, you may want to fill in the variables with the results of a