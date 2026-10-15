
From direct prompt manipulation to semantic conditioning through dialogue, the techniques explored here underscore how fragile alignment and instruction-following can be in real-world deployments. This chapter covers methods that include indirect retrieval-based injections, embedding space exploitation, token-level perturbation, and conversational context poisoning. Each technique is grounded in a precise understanding of transformer model behavior, including attention dynamics, positional encoding, and the mechanics of generative coherence. These attack strategies highlight the architectural tension between helpfulness and safety—a tension that cannot be resolved with surface-level defenses alone.

For security architects and risk leaders, the implications are clear: Any AI system exposed to user-controlled inputs must be viewed as an adversarial environment. These techniques bypass conventional input sanitization, evade static filters, and compromise systems through model-conforming language alone. Compliance requirements, reputational risk, and operational safety demand that AI security professionals develop deep fluency in the patterns, weaknesses, and systemic design flaws that enable prompt injection and jailbreak behavior. This chapter equips practitioners with the technical insight required to anticipate these threats and begin the work of building durable defenses at the intersection of language, logic, and model intent.

## Technical Foundations of Prompt Injection Attacks

Prompt injection attacks manipulate the interpretive flexibility of generative models to subvert intended behaviors and safety protocols. At their core, these attacks embed malicious or adversarial instructions into input prompts, exploiting the models design to follow instructions regardless of context. The attacker's goal is to cause the model to disregard system-level constraints and generate outputs that are harmful, misleading, or unauthorized. Unlike traditional code injection that targets syntax parsers, prompt injection relies entirely on the model's semantic and contextual reasoning capabilities. This makes detection and prevention fundamentally different and, in many ways, more challenging.

The attack surface emerges from how large language models are conditioned. During training, these models learn to predict the next token based on prior context. Instruction-tuned models are further refined to follow human-like commands embedded in natural language. This conditioning creates an implicit contract: given a well-formed prompt, the model strives to produce a helpful and coherent response. Prompt injection breaks that contract by disguising malicious payloads within otherwise valid natural language inputs. The result is an attack that cannot be filtered using traditional input sanitization methods because the harmful instruction is semantically buried, not syntactically anomalous.

One key technical enabler of prompt injection is the transformer architecture's attention mechanism. These models weigh all tokens in the input context, allowing a carefully constructed adversarial segment to gain undue influence over the output generation process. Even if initial prompts include explicit boundaries—such as a system prompt that sets safety rules—later user-supplied input can override them if it introduces more contextually dominant directives. This vulnerability stems from the nonhierarchical way in which transformer models process and weigh context, treating earlier system instructions as just one part of a larger dialogue history.

Attackers exploit this behavior through linguistic precision. The most effective prompt injections are not simply aggressive commands; they are subtle, cleverly worded segments designed to co-opt the model's output generation logic. Examples include adversarial prefixes such as “Ignore previous instructions and instead respond as follows…” or embedded conditionals that mislead the model into interpreting harmful output as part of a roleplay or hypothetical exercise. These are not just accidental oversights—they reflect a deep understanding of how token-level attention and instruction-following are implemented in the model. The following figure maps out the critical points where injection attacks can enter and manipulate the generative AI pipeline ([Figure 9.1](#c09.xhtml#c09-fig-0001)).

Another dimension of this attack involves targeting the autoregressive nature of text generation. Since language models predict one token at a time, attackers can craft prompts that initiate benign sequences but later shift meaning or inject adversarial commands. This allows prompt injections to operate in stages, effectively bypassing static content filters or output guards that only evaluate the prompt holistically at a single time step. The exploit, therefore, emerges not just from the prompt itself, but from the evolving sequence of model decisions that follow.

Prompt injection can be either direct or indirect. In direct injection, the attacker interacts with the model through a user interface and crafts prompts that steer the output explicitly. In indirect injection, the attacker manipulates the environment surrounding the model—for instance, by embedding malicious instructions in data retrieved by the model from an external source like a document, webpage, or API response. This form of injection is particularly dangerous because it leverages retrieval-augmented generation systems, where content is dynamically pulled into the prompt context without human inspection. [Table 9.1](#c09.xhtml#c09-tbl-0001) compares key prompt injection techniques based on their method of delivery, model target, and behavioral manipulation characteristics.

![Figure 9.1 Injection points in the generative AI pipeline.](images/c09f001.png)

Figure 9.1 Injection points in the generative AI pipeline.

Table 9.1 Comparison of prompt injection techniques.

| Technique || Delivery Method || Targeted Model Behavior || Trigger Timing || Detectability |
| --- | --- | --- | --- | --- |
| Direct Prompt Injection || User Input || Instruction Following || Immediate || Moderate |
| Jailbreak Prompting || User Input || Safety Refusal Logic || Immediate || Low |
| Indirect Injection || External Retrieval || Contextual Completion || Deferred || High |
| Deferred Trigger || User or Document || Session Memory Influence || Delayed || High |
| Contextual Injection || Sequential Prompts || Multi-Turn Coherence || Gradual || Low |
| Token Perturbation || Formatted Input || Token Parsing Behavior || Immediate || Low |
| Semantic Reframing || Conversational Framing || Ethical Boundaries || Incremental || Moderate |
| Roleplay Exploit || Narrative Input || Safety Constraint Suspension || Immediate || Low |
| System Prompt Override || Input Header || System Role Authority || Immediate || Moderate |
| Latent Instruction || Embedded Context || Conditional Output Logic || Deferred || High |

Transformer-based models are especially susceptible because of the way instruction tuning and reinforcement learning from human feedback (RLHF) reinforce helpfulness. These techniques prioritize human-aligned outputs, but they also create a brittle expectation that any sufficiently well-formed command deserves compliance. This expectation becomes a double-edged sword: it improves usability but lowers resistance to adversarial phrasing. Once the attacker identifies the model's preferred language structures and stylistic cues, they can emulate them to maximize the chance that the malicious instruction will be followed.
