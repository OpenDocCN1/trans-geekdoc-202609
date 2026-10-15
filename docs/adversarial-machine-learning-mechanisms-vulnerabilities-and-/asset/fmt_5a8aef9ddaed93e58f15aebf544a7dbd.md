
# 5  

Poisoning Attacks—Compromising AI Systems During Training  

Poisoning attacks represent one of the most insidious and technically sophisticated threats to artificial intelligence (AI) model integrity, particularly because they target the foundation of how models learn—during training. By introducing manipulated data, malicious updates, or corrupted experiences at strategic points in the training pipeline, adversaries can embed persistent and often invisible vulnerabilities into otherwise functional models. These attacks evade traditional validation techniques and can remain dormant until activated under specific conditions, making them exceptionally difficult to detect post-deployment. Understanding poisoning across supervised, federated, and reinforcement learning (RL) contexts is essential to building resilient AI systems capable of maintaining trust and reliability.

# Adversary Spotlight  

From an attacker's perspective, evasion is all about subtlety, timing, and model behavior. The attacker doesn't want to destroy a system—they want it to keep running, but under their control or with incorrect outputs. They see the model as a black box to probe or a white box to dissect, and they look for leverage points: decision boundaries, weak embeddings, or overconfident predictions. What catches their attention isn't just a model's predictions, but the internal mechanics—how it arrives at those predictions, and where that process can be nudged.

A particularly attractive target is any AI system with public-facing input, like image upload portals, language-based support bots, or real-time monitoring systems. If the attacker can find a way to alter inputs that get interpreted differently by the model than by a human, they gain an edge. For instance, feeding a manipulated traffic sign into an autonomous car's vision system isn't just about making the car misread it—it's about doing it in a way that's reproducible, subtle, and invisible to passengers or cameras.

Blind spots are especially common around preprocessing stages. If a model assumes input is clean, well formatted, or semantically uniform, attackers will deliberately violate those assumptions. A missing space, a shifted timestamp, or an unfamiliar character might be meaningless to a user—but it could derail the model's logic entirely. The adversary counts on defenders overlooking these “unimportant” parts of the input pipeline.

What gives attackers staying power is the model's overconfidence. When the system responds to a poisoned input with high certainty, that's not just a win—it's a shield. It makes it less likely that someone will question the output or look closer, especially if it passes surface-level audits. This is what makes inference-time evasion such a potent tool in the attacker's playbook.

# Common Misunderstandings  

* Evasion attacks don't require breaking into the model or accessing its code—many work entirely through input manipulation.

* Small changes to input data can have massive effects on output, even if humans can't see or hear the difference.

* Models that perform well in testing aren't necessarily robust—they may still be highly vulnerable to adversarial inputs.

* Defenses that rely on simple preprocessing, like noise filters or input normalization, often fail against well-crafted attacks.

* Transferability allows attackers to succeed even if they've never seen your exact model.

* Evasion isn't just about images—it affects text, audio, time-series, and any input type that AI models process.

* Real-world attacks don't have to be sophisticated to be effective—some use basic techniques like punctuation tricks or input reordering.

# Defense Framing  

Security professionals must shift from treating model inputs as static and benign to seeing them as potential adversarial surfaces. Just because input looks normal doesn't mean it's safe. The assumption that inference-time behavior is inherently trustworthy must be challenged. Models need to be evaluated not just on accuracy, but on robustness—how they behave under deliberate pressure.

Evasion defense begins with threat modeling. What kind of inputs does your system accept? Where do they come from? Can a user, customer, or external device influence them? Systems that ingest untrusted data streams should be architected with the expectation that inputs may be adversarial by default, not exception.

Mindset matters more than any one tool. It's not enough to rely on the same test set used in development. Adversarial testing, red teaming, and behavioral stress-testing must become part of the evaluation lifecycle. Think like an attacker: how would you confuse this system without making it look obviously wrong?

Finally, defenders must stop thinking about inputs in isolation. Context—whether visual, temporal, or linguistic—matters. Attackers exploit models' inability to reason across modalities or across time. Defenders should prioritize models and architectures that understand more than just the surface of the input, and that can flag unexpected, out-of-distribution, or low-confidence decisions for human review. Robustness is not just accuracy under pressure—it's resilience by design.
