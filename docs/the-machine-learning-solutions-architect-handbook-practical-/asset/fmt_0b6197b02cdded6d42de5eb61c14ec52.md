
This approach capitalizes on the extensive knowledge gained during the initial pre-training of FMs and produces models that excel at target tasks beyond the general capabilities.

In the following sections, we will discuss instruction fine-tuning and parameter-efficient fine-tuning. Let’s get into it!

## Instruction fine-tuning

One technique to enhance an FM’s ability to perform new tasks or improve its ability to perform an existing task by teaching it to follow an instruction. This is where instruction fine-tuning comes in. Instruction fine-tuning teaches a pre-trained model to perform an existing task better or learn a new task such as summarization or reasoning. Compared to pre-training, instruction fine-tuning requires significantly less data.

Instruction fine-tuning is a supervised approach where you need to provide a labeled training dataset in the form of a prompt and the expected output from the prompt. The following is an example of instruction fine-tuning a dataset called `Dolly from Databricks`:

```
'instruction': 'Given this text give me short summary about Beavers',
'context': 'Beavers (genus Castor) are large, semiaquatic rodents of the Northern Hemisphere. There are two existing species: the North American beaver (Castor canadensis) and the Eurasian beaver (C. fiber). Beavers are the second-largest living rodents, after capybaras, weighing up to 30 kilograms (66 lb). Beavers have stout bodies with large heads, long chisel-like incisors, brown or gray fur, hand-like front feet, webbed back feet, and tails that are flat and scaly. The two species differ in skull and tail shape and fur color. Beavers can be found in a number of freshwater habitats, such as rivers, streams, lakes and ponds. They are herbivorous, consuming tree bark, aquatic plants, grasses and sedges.',
'response': 'Here is a short summary about Beavers:
There are two existing species - North American and Eurasian. They are the second-largest living rodents. Physically species of Beaver can vary in terms of fur colour but they all have webbed back feet, hand-like front feet and flat scaly tails. Long chisel-like incisors are a key feature. Beavers can be found in freshwater habits. aThey are herbivores.'
```

You can see the complete Dolly dataset at [https://huggingface.co/datasets/databricks/databricks-dolly-15k.](https://huggingface.co/datasets/databricks/databricks-dolly-15k)

After instruction fine-tuning with a labeled dataset such as Dolly-15K, the model should be able to generate responses with greater precision for the same question. For example, if we fine-tune the Llama 2 7B model with the Dolly-15k dataset, you will get the following output for the same text completion task from the previous section:

```
Input:
"The capital of France is"
Output:
Paris.
```

The process of instruction fine-tuning is very similar to any supervised ML, where you provide labeled training data, and the model learns to predict the output and minimize the loss between the predicted value and labels. You can also perform additional fine-tuning on models already fine-tuned to further improve their performance. The following diagram illustrates the flow of instruction fine-tuning:

![A diagram of a model Description automatically generated](OEBPS/Images/B20836_15_03.png)

Figure 15.3: Instruction fine-tuning of pre-trained LLM model

Several existing public datasets are available for instruction fine-tuning, such as Dolly and TriviaQA. However, when dealing with proprietary knowledge and specific capabilities, it becomes necessary to curate and prepare custom datasets for instruction fine-tuning. Depending on the domains and use cases, subject-matter experts may be required to assist in assembling these datasets, including crafting domain-specific prompts and defining desired answers. To ensure the high quality and standards of these datasets, a combination of human expert evaluation and automated scoring mechanisms should be employed. This approach ensures that the datasets meet rigorous criteria for accuracy and reliability.

In terms of automated scoring and evaluation of fine-tuned models, one can leverage powerful models like Claude from Anthropics or GPT-4. These models contribute to the robustness and precision of the evaluation process.

Fine-tuning an LLM is not without complexities. Challenges include issues such as overfitting, where the model excels on the training data but struggles to apply its knowledge to unfamiliar data, as well as the risk of catastrophic forgetting, which involves the model erasing its original pre-training knowledge. In order to tackle these obstacles, various strategies can be employed to alleviate the potential constraints associated with conventional fine-tuning for LLMs. These include implementing cautious regularization techniques such as dropout, L2 normalization, and early stopping to curb overfitting tendencies. The approach of gradual unfreezing can be adopted as well, involving a gradual release of lower layers over time to keep the model’s pre-existing knowledge. Engaging in multi-task training offers another avenue, where simultaneous fine-tuning is carried out across multiple datasets or objectives, fostering broader adaptability. Additionally, the method of continual pre-training can be integrated, supplementing fine-tuning batches with the initial pre-training objective to sustain foundational learning.

Fine-tuning can provide differentiating capabilities for organizations seeking a competitive edge with custom datasets and unique knowledge, without the heavy investment of training models from scratch.

## Parameter-efficient fine-tuning

Regular instruction fine-tuning requires the full pre-trained model to be fine-tuned and all its parameters need to be available for potential updates. This requires significant compute resources, especially when the models are large. To address this challenge, a new technique called `parameter-efficient fine-tuning` (`PEFT`) has been introduced. `PEFT` refers to techniques to adapt large pre-trained language models to downstream tasks by introducing a small new set of trainable parameters instead of updating the original parameters of the model.

This approach significantly reduces both computational requirements and storage demands. Additionally, `PEFT` mitigates the challenges posed by catastrophic forgetting—a phenomenon encountered during comprehensive LLM fine-tuning, whereby an LLM fails to perform tasks that it knew how to perform previously after fine-tuning.

There are several `PEFT` techniques available, including `Low-Rank Adaptation` (`LoRA`), prefix tuning, and prompt tuning. You can find out how these techniques work by visiting the related online resources directly. With these libraries, performing `PEFT` is a very straightforward process. For example, using `LoRA` for `PEFT` involves adding the following three main steps:

1. Import the necessary library packages:

```
from peft import get_peft_model, LoraConfig, TaskType
```

2. Create a configuration corresponding to the PEFT method:

```
peft_config = LoraConfig(
    task_type=TaskType.SEQ_2_SEQ_LM, inference_mode=False, r=8, lora_alpha=32, lora_dropout=0.1
)
```

3. Wrap the base model by calling `get_peft_model`:

```
model = get_peft_model(model, peft_config)
model.print_trainable_parameters()
```

The rest of the model training steps are the same as regular training. After the model is fine-tuned, you can save the model by calling the following command:

```
model.save_pretrained("output_dir")
```

This will only save the incremental PEFT weights that were trained. During inference time, you use the `PeftModel` package to load the base model and PEFT weights together as the combined model for serving. You can also merge the PEFT weights with the base model prior to deployment.

## Reinforcement learning from human feedback
