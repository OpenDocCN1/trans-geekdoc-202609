
Prompt injection and jailbreak techniques are not obscure edge cases—they are central threats in the era of large language models and generative AI systems. These attacks manipulate the model through its natural input mechanism—language—rather than breaking code or bypassing firewalls. That shift changes the security game: now the prompt *is* the payload, and the attacker's weapon is cleverly crafted text. This chapter reframed how we think about trust, control, and vulnerability in AI systems that generate responses based on context. Understanding these manipulation strategies is critical because the most advanced AI systems today are built to listen—and attackers have learned exactly how to talk to them.

### Essential Terms in Context

*   **Prompt Injection:** This is when an attacker manipulates an AI model by inserting carefully crafted instructions into its input. This chapter showed how attackers use this method to override or redirect a model's response, even when safety controls are in place. It's critical to adversarial machine learning because it weaponizes the very mechanism by which users interact with AI systems.

*   **Jailbreak:** A jailbreak happens when someone uses a prompt to force a model to break its own rules or ethical boundaries. In this chapter, we explored how jailbreak prompts use roleplay, hypothetical framing, or override commands to bypass refusals. Jailbreaking is a top concern in AI security because it shows how easily models can be led into dangerous behavior through language.

*   **Indirect Injection:** This type of attack uses content from external sources—like documents, websites, or APIs—that the model retrieves as part of its response process. This chapter explained how malicious instructions hidden in this retrieved data can sneak into the model's context and shape its behavior. Indirect injection matters because it turns trusted external data into a vector for attack, especially in systems that rely on retrieval-augmented generation.

*   **Token-Level Perturbation:** This refers to making small changes at the character or token level—like inserting spaces or misspellings—that alter how the model interprets a prompt. This chapter discussed how even minor token tweaks can bypass filters or change meaning in ways that steer output maliciously. These perturbations are important because they exploit how models process inputs internally, not how they look to a human reader.

*   **Semantic Boundary Exploitation:** This is when an attacker manipulates the grey area between safe and unsafe content, staying just inside the model's allowed behavior while nudging it toward risky output. This chapter showed how carefully worded prompts can blur ethical lines until the model steps over them. It's a key tactic in adversarial prompting because it avoids direct rule-breaking and instead bends the model gradually toward unsafe ground.

*   **Contextual Injection:** Contextual injection takes place over multiple turns in a conversation, where earlier messages are used to set up a harmful result later on. We looked at how attackers use a series of seemingly harmless prompts to build a context that makes the final malicious request seem acceptable. This technique is especially dangerous because it evades detection when prompts are evaluated in isolation.

*   **Deferred Trigger:** A deferred trigger is a hidden instruction planted early in a conversation or document that only activates when a later input references it. This chapter explained how attackers embed these triggers to stay under the radar until the right context appears. This matters for AI security because it shows how prompt injection can be time-delayed and context-sensitive, making it harder to catch.

*   **Retrieval-Augmented Generation (RAG):** RAG is when a language model retrieves external documents to help answer a prompt. In this chapter, we explored how attackers poison those documents to inject instructions indirectly. RAG systems are especially vulnerable because they blend model input with outside content, creating an uncontrolled entry point.

*   **Instruction-Following Fine-Tuning:** This is a technique where models are trained to respond helpfully to clear instructions. The chapter emphasized that this tuning, while useful, also makes models more obedient to adversarial commands. It's a double-edged sword in AI security because the same logic that helps the model follow good instructions can be turned against it.

*   **System Prompt Override:** This happens when a malicious user prompt tells the model to ignore its original configuration or safety rules. We looked at how prompts like “disregard previous instructions” often succeed in bypassing system safeguards. Recognizing this risk is essential for designing more resilient prompt processing pipelines.

*   **Latent Instruction:** A latent instruction is a hidden message that doesn't activate immediately but influences later output once the right conditions are met. This chapter illustrated how these can be embedded in external data or early conversation turns. Latent instructions are important because they extend the reach of prompt injection beyond what's immediately visible.

*   **Semantic Drift:** Semantic drift is the gradual shift in a model's tone, boundaries, or ethical alignment over the course of a dialogue. We showed how adversaries exploit this drift to erode safety constraints slowly. Monitoring for drift is crucial because it reveals how dangerous behavior can emerge incrementally rather than abruptly.

*   **Adversarial Prompt Engineering:** This is the intentional crafting of inputs to produce harmful or policy-violating outputs. In this chapter, we broke down how attackers use iteration, feedback, and linguistic strategies to refine these prompts. It's a core practice in adversarial machine learning, reflecting how attackers adapt their language to exploit model behavior.

*   **Session Memory Poisoning:** This occurs when an attacker manipulates what a model remembers from earlier in a session to influence future outputs. The chapter highlighted how persistent context can be turned into a liability. Understanding this concept is vital when building chatbots or assistants that maintain memory across user interactions.

*   **Context Window Manipulation:** This involves altering which parts of the input the model sees or prioritizes by manipulating length, position, or formatting. We saw how adversaries use this to hide or dilute safety instructions. It's a subtle but powerful technique because it affects the very mechanism the model uses to decide what matters most.

### Adversary Spotlight

A skilled adversary sees a generative model not as a black box to break into, but as a system eager to please—and often too trusting of what it's told. What draws their attention is the model's compulsion to comply, especially when instructions are wrapped in the right tone, structure, or roleplay. They know that these models don't reason in the human sense; they follow patterns. If those patterns resemble helpful requests, the model will respond—even if the underlying intent is malicious.

An attacker testing prompt injection doesn't start with obvious payloads. Instead, they probe gently, using indirect phrasing and hypothetical framing. They measure small shifts in the model's tone, looking for signs that ethical boundaries are weakening. Once they know which types of prompts bypass the filters or cause refusal logic to soften, they refine their input until they hit the edge—and then push past it.

Conversational attacks appeal to those who understand human psychology. The attacker acts like a cooperative user, playing a long game through friendly dialogue. They exploit memory, escalate context, and set up traps disguised as innocent scenarios. When the model starts to comply with nuanced or odd requests, the attacker knows it's ready for the final payload.
