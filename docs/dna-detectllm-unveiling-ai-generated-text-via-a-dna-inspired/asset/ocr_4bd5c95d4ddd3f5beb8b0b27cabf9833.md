# ## B Broader Impacts

The proposed DNA-DetectLLM contributes to the field of AI-generated text detection by improving accuracy and introducing a novel detection perspective to the research community. Its enhanced reliability may serve as a reference in socially relevant scenarios where auxiliary judgment is required. However, we emphasize that detection inherently carries a risk of implication or accusation. While our method demonstrates strong performance, we strongly oppose the use of its outputs as direct evidence in punitive or disciplinary contexts. Regardless of its accuracy, such applications could lead to serious consequences and misuse.

# ## C Prompt Design for Main Data

Table 3: Examples of input prompts and corresponding outputs across different writing tasks, where the outputs are sampled from GPT-4-generated texts.

| Writing Task | Input Prompt | Output |
| :--- | :--- | :--- |
| News Article Writing | A police source told the BBC that an infiltrator from the Taliban had allowed militants into the police station in the regional capital of Lashkar Gah last night. Please continue. | The militants, believed to be associated with the Taliban, reportedly raided the police station and engaged in a prolonged gun battle with the officers... |
| Story Generation | Two kids entered the Rockmount Zoo. Please continue. | As they excitedly crossed the threshold, their eyes widened at the sight of the vibrantly colored parrots squawking from the treetops... |
| Academic Writing | Please write an abstract based on the following title: “Pure Exploration and Regret Minimization in Matching Bandits”. | This paper delves into the field of pure exploration and regret minimization in the context of matching bandits problems - an important area in machine learning... |

Table 3 presents the general-purpose prompts we designed for different writing tasks. Using these prompts, we generated 4,800 AI-generated texts—corresponding to human-written texts—across GPT-4 Turbo, Gemini-2.0 Flash, and Claude-3.7 Sonnet, which were used in our experiments.

# ## D Implementation Details

All experiments are conducted on a single NVIDIA A100 GPU with 80GB of memory. Unless otherwise specified, default settings are used for temperature, top-k, and other generation parameters. No additional hyperparameter tuning is involved in this study. For training-based methods (Biscope and R-Detect), models are trained on 4,000 balanced samples from the HC3 dataset, and the best-performing checkpoints are selected based on validation performance on a separate 2,000-sample validation set. In the main experiments, all reported F1 scores are the maximum values obtained by selecting the optimal threshold based on the positive and negative scores of each method.

# ## E Robustness Experiments

In this study, we do not consider adversarial attacks on human-written texts, as evasion in such cases is generally inconsequential. Instead, we focus on adversarial scenarios involving AI-generated texts, introducing two common attack types: paraphrasing and token-level editing. For paraphrasing attacks, we employ DAPPER with hyperparameters set to a lexical diversity of 60 and a syntactic diversity of 60. This level of paraphrasing is sufficient to potentially bypass SOTA detectors. For editing attacks, we tokenize the input using the GPT-2 tokenizer and apply random insertions, deletions, and substitutions to 1% of the tokens. The inserted or substituted tokens are sampled uniformly from the tokenizer's vocabulary.