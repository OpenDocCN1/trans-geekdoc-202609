In this chapter, we'll cover prompt injection examples, possible impacts, and the two primary classes of prompt injections (direct and indirect), and then we'll look at some mitigation strategies.

# Examples of Prompt Injection Attacks

This section looks at some archetypal examples of prompt injection attacks. We’ll see some attacks that seem more like social engineering than traditional computer hacking. Specific examples like these will constantly change as attackers and defenders learn more about prompt engineering and injection techniques, but these examples should help you understand the concepts.

*Prompt engineering* is the art of designing queries for large language models to elicit specific, accurate responses. It combines a technical understanding of AI with strategic language use, optimizing the model's performance for desired outcomes.

Since the specifics of attack vectors in this space will change often, it won’t do us much good to look at the details of malicious prompts. However, it’s helpful to group some common, current attacks into categories. Let’s look at four types of prompt injection attacks.

# Forceful Suggestion

Forceful suggestion is the simplest and most direct way to construct a prompt injection attack. The idea is to find a phrase that drives the behavior of the LLM model in a specific direction that is advantageous to the attacker. A forceful suggestion might allow an attacker to temporarily skirt guardrails placed by the developer or even remove such restrictions entirely. In all cases, the idea is to move the system out of “alignment” with the system’s developer and align it with the attacker.

*Alignment* refers to ensuring that an AI system’s objectives and actions are in harmony with the developer’s values, goals, and safety considerations. One way to think about prompt injection is that it is a technique to make the LLM act out of alignment with its creator’s wishes or designs.

In the Tay example, one of the critical discoveries by attackers was the phrase “repeat after me,” which forced Tay to repeat any words given to her. This seemingly benign feature allowed the attackers a foothold to start Tay’s transition to the dark side and reinforce her data poisoning, a topic we’ll discuss more in Chapter 9.