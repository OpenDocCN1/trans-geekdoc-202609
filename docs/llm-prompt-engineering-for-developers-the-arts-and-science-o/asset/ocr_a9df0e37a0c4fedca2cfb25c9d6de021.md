In the LLM step, you need to select the LLM provider and the model. For example, if you created an OpenAI connection, you’ll see GPT-4, GPT-3.5, and the other models the API provides. You can also select the temperature, `max_tokens`, `top_p`, and other parameters.

In the prompt text, you can use a prompt like this:

```
```
system:
You are a nutrition specialist.
user:
{{question}}
```
```

Click on “Validate and parse input”. Then, in the “question” variable, select the output of the prompt step (e.g. `${Prompt_mxx8.output}`). This will connect the output of the prompt to the LLM step. Finally, execute to test. You should be able to see an output that is similar to the following:

```
```json
[
    {
        "system_metrics": {
            "completion_tokens": 61,
            "duration": 6.065642,
            "prompt_tokens": 30,
            "total_tokens": 91
        },
        "output": "In 100 grams of banana, you will find:\n- Carbohydrates: Approximately 23g\n- Protein: Approximately 1.1g\n- Fat: Approximately 0.3g\n\nPlease note, specific nutritional content might vary slightly based on the size and ripeness of the banana."
    }
]
```
```