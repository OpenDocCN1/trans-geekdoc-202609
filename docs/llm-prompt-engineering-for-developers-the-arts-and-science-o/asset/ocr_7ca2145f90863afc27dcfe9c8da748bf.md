![](bbox=[0.13, 0.11, 0.86, 0.17])

![](bbox=[0.13, 0.19, 0.86, 0.25])

**Prompt Flow inputs**

Next, add a Python code step. Use this code:

```
from promptflow import tool
@tool
def my_python_tool(input: str) -> str:
    return input
```

Click on “Validate and parse input” right below the code editor. This code is a simple Python function that takes a string as input and returns the same string as output. The input of the function should be named “input” and should have the following values:

${inputs.food}

This is a special syntax that allows the flow to connect the inputs and outputs of the flow. When configured this way, you will notice that a connection is created between the “inputs” and the Python code. Execute the code to validate the output. The output should be the same as the input: