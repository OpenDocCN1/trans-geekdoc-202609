
Required assessments, you will receive a certificate of completion."
}
{ "prompt": "What should I do if I face technical issues->", "completion
": " Please reach out to our support team via the 'Contact Us' page, and they'll be happy to assist you.\n"}

Note that we removed the “?” from the prompts.

Next, install the OpenAI command-line interface (CLI):

```
pip install openai[data/lib]
```

Export your OpenAI API key:

```
export OPENAI_API_KEY=<your-api-key>
```

Save the JSONL file as data.jsonl and run the following command:

```
openai tools fine_tunes.prepare_data -f data.jsonl
```

You should see a similar output:

```
Analyzing...
- Your file contains 12 prompt-completion pairs. In general, we recommend having at least a few hundred examples. We've found that performance tends to linearly increase for every doubling of the number of examples
- All prompts end with suffix `->`
- All completions end with suffix `\n`

No remediations found.

You can use your file for fine-tuning:
> openai api fine_tunes.create -t "data.jsonl"
```

After you've fine-tuned a model, remember that your prompt has to end with the indicator string `->` for the model to start generating completions, rather than continuing with the prompt. Make sure to include `stop=["\n"]` so that the generated texts ends at the expected place. Once your model starts training, it'll approximately take 2.61 minutes to train a `curie` model, and less for `ada` and `babbage`. Queue will approximately take half an hour per job ahead of you.

Now, we can fine-tune the model using the following command:

```
openai api fine_tunes.create -t "data.jsonl" -m curie --suffix "SkillUp\Academy"
```

You should see a similar output:

```
Upload progress: 100%|████████████████████████████████████████████████████████████████\████████████████████████████████████████████████████████████████████
██████████████████████████| 2.47k/2.47k [00:00<00:00, 8.63Mit/s]
Uploaded file from data.jsonl: file-RdACszHknkQC49hdZdGxpoEA
Created fine-tune: ft-WEYpsygNbeHy8YvxCaiyB4i
Streaming events until fine-tuning is complete...

(Ctrl-C will interrupt the stream, but not cancel the fine-tune)
[. .] Created fine-tune: ft-WEYpsygNbeHy8YvxCaiyB4i
[. .] Fine-tune costs $0.01
[. .] Fine-tune enqueued. Queue number: 0
```

...etc

As stated by the output, you can exit the stream by pressing Ctrl-C; this won't cancel the fine-tune job. You can also check the status of the fine-tune job by running the following command:

```
openai api fine_tunes.follow -i ft-WEYpsygNbeHy8YvxCaiyB4i
```

Where ft-WEYpsgNbeHy8YvxtCaiyB4i is the fine-tune ID.

When the fine-tune job is completed, you will see an output similar to this one:

```
[..] Created fine-tune: ft-WEYpsgNbeHy8YvxtCaiyB4i
[..] Fine-tune costs $0.01
[..] Fine-tune enqueued. Queue number: 0
[..] Fine-tune started
[..] Completed epoch 1/4
[..] Completed epoch 2/4
[..] Completed epoch 3/4
[..] Completed epoch 4/4
[..] Uploaded model: curie:ft-org:skillupacademy-2023-08-18-14-32-18
[..] Uploaded result file: file-3fxL6gfapDyHqG7cjXDzFFOf
[..] Fine-tune succeeded

Job complete! Status: succeeded

Try out your fine-tuned model:

openai api completions.create -m curie:ft-faun.skillupacademy-2023-08-18-14-32-18 -p <YOUR_PROMPT>
```

Let’s try it out:

```python
import openai
import os

openai.api_key = os.getenv("OPENAI_API_KEY")

model = "curie:ft-faun.skillupacademy-2023-08-18-14-32-18"
prompt = input("Ask a question: ")
instruction = f"""
You are a helpful and smart customer service representative for SkillUp
Academy.
Answer the following questions based on the training data provided.

If you don't know the answer, just say 'Sorry, I don't know the answer.'

AI: Hi there. I am Felix, the chatbot. How can I help you today?
User: {prompt}
"""

full_prompt = instruction + " " + prompt + "->"

response = openai.Completion.create(
    model=model,
    prompt=full_prompt,
    max_tokens=100, # adjust based on your need
    stop=["\n"],
    temperature=0 # strikes a balance between deterministic and random
)

print(response.choices[0].text.strip())
```

The training data is very limited, so the model will not be able to answer all the questions with 100% accuracy. However, it works well for a good number of questions.

The goal of this example is to show you how to fine-tune a model using a prompt dataset. In practice, you will need to use a larger dataset to get better results and use better, well-studied prompts.

## 11.7 - Why Is Prompt Engineering Vital for Transfer Learning and Fine-Tuning?

Transfer learning, particularly in the context of large language models like GPT, refers to the application of knowledge gained while solving one problem to solve a different, but related, problem. In the context of OpenAI’s GPT and fine-tuning, it essentially means taking the vast knowledge already encoded within the base GPT model and refining or redirecting it with a smaller, domain-specific dataset. This is what we see in the example above where GPT is fine-tuned with a specific dataset related to "SkillUp Academy."

However, merely possessing a fine-tuned model isn't the end of the story. The way we interface with that model—how we phrase our prompts—plays a crucial role in the kind of responses we receive. This is where the art and science of prompt engineering come into play.

Prompt engineering plays a central role in the success of fine-tuning for these five main reasons:

- 1 - Improving accuracy: Even with a perfectly fine-tuned model, imprecise or ambiguous prompts can lead to misleading or unhelpful answers. A well-engineered prompt helps guide the model towards the most relevant and accurate response.
- 2 - Exploiting model knowledge: Given the vast knowledge within GPT, a well-phrased prompt can extract nuanced information, even if the specific fine-tuning data did not cover it. It's like fine-tuning provides the specialization, while prompt engineering ensures we can still leverage the broader general knowledge of the base model.
- 3 - Guiding context: Especially in customer service or domain-specific applications, setting the right context is essential. For instance, in the given example, the instruction sets the model in a customer service role for SkillUp Academy. Without this context, the model might respond in a generic fashion, unaware of its specialized role.
- 4 - Handling Unknowns Gracefully: A good prompt can also instruct the model on how to handle questions it might not know, as seen with the "Sorry, I don't know the answer." instruction. This can be particularly useful in avoiding "hallucinations" or spurious answers.
- 5 - Maximizing Efficiency: In some cases, you might be limited by token counts or computational constraints. A concise and clear prompt ensures that the model's computational power is directed towards generating valuable output, rather than deciphering a vague question.

On the other hand, while prompt engineering has its advantages, it also comes with challenges:

- Iterative Process: Finding the perfect prompt often requires multiple iterations and testing.
- Overfitting: Over-optimizing a prompt for specific questions might lead to reduced performance on broader or slightly different questions.
- Training Data Limitations: No matter how expertly crafted the prompt, if the fine-tuning data is sparse or of low quality, the model's responses will be limited in accuracy and relevance.

In this fine-tuning example, GPT provides a powerful mechanism to specialize the model for a particular domain (client support). However, prompt engineering is the bridge between this specialized knowledge and the user's questions. Like any tool, the quality of the output depends not just on the tool's capability, but also on the expertise of the user.

As LLMs continue to grow and become more integrated into more industries and applications, prompt engineering will emerge as a key skill in fine-tuning and transfer learning.
