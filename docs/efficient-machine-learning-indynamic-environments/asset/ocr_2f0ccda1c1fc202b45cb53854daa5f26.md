| Category | Dataset | Tiers Used |
| :--- | :--- | :--- |
| Language Models | BERT [88]<br>RoBERTa [95]<br>XLNet [99]<br>ELECTRA [140] | BASE, LARGE |
| Image Models | ResNet [58]<br>ViT [104]<br>CLIP [103] | Selection based on FLOPs |
| Black-Box Models | LLaMA 3.1 [188]<br>Gemma 2 [199]<br>Qwen 2 [200] | See Table 3.1 |

Table B.2: Summary of models used for both benchmark and black-box API experiments, across image and language tasks.

self-verification 8 times at a high sampling temperature (temp = 1.0), using the same model that generates inference at the given cascade tier. Automix then averages the self-verification results and meta-verify it with the best parameters of the routing strategy to decide when to exit.

+   * **FrugalGPT**: Just like AutoMix, FrugalGPT needs to train $n - 1$ routers for $n$ cascade tiers, and each router needs to have a sense of the data distribution and the model's predictive power. $\ge 500$ training samples and inference generated on these samples by the tier's model are needed to train each tier/model's scorer, a DistilBERT [97].

+   * **MoT LLM Cascade**: Yue et al. [201] focuses on sampling and consistency checking as a means of cascade. To measure consistency, the weaker LLM generates multiple answers for a single question by varying the randomness in the LLM's responses—i.e., varying the temperature of the model—while using in-context demonstrations and reasoning techniques (e.g., Chain-of-Thought [162]) to influence how the model generates answers. The system compares the different sampled answers and picks the most consistent one. If the consistency score is high enough, the weaker model's answer is accepted. Otherwise, the question is passed to the next tier.

+   * **ABC**: We use the voting-based safe deferral rule, requiring no additional training or any complex routing strategies.