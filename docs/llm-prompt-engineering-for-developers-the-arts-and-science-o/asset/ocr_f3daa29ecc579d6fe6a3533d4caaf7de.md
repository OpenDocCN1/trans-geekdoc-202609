uired assessments, you will receive a certificate of completion.\n"}
{ "prompt": "What should I do if I face technical issues->", "completion\n": " Please reach out to our support team via the 'Contact Us' page, an d they'll be happy to assist you.\n"}

Note that we removed the “?” from the prompts.

Next, install the OpenAI command-line interface (CLI):

```
```
pip install openai[data/lib]
```
```

Export your OpenAI API key:

```
```
export OPENAI_API_KEY=<your-api-key>
```
```

Save the JSONL file as data.jsonl and run the following command:

```
```
openai tools fine_tunes.prepare_data -f data.jsonl
```
```

You should see a similar output:

```
```
Analyzing...
- Your file contains 12 prompt-completion pairs. In general, we recommond having at least a few hundred examples. We've found that performance tends to linearly increase for every doubling of the number of examples
- All prompts end with suffix `->`
- All completions end with suffix `\n`

No remediations found.

You can use your file for fine-tuning:
> openai api fine_tunes.create -t "data.jsonl"
```
```