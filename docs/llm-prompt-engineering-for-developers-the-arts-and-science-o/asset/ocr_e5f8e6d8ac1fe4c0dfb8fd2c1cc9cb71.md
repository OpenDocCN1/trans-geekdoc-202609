After you've fine-tuned a model, remember that your prompt has to end with the indicator string `~>~` for the model to start generating completions, rather than continuing with the prompt. Make sure to include `stop=["\n"]` so that the generated texts ends at the expected place. Once your model starts training, it'll approximately take 2.61 minutes to train a `curie` model, and less for `ada` and `babbage`. Queue will approximately take half an hour per job ahead of you.

Now, we can fine-tune the model using the following command:

```
```
openai api fine_tunes.create -t "data.jsonl" -m curie --suffix "SkillUp\Academy"
```
```

You should see a similar output:

```
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
```

...etc

As stated by the output, you can exit the stream by pressing Ctrl-C; this won't cancel the fine-tune job. You can also check the status of the fine-tune job by running the following command:

```
```
openai api fine_tunes.follow -i ft-WEYpsygNbeHy8YvxCaiyB4i
```
```