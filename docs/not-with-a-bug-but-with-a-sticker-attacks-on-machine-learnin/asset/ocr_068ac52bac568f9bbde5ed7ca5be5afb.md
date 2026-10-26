want some of the more “vulnerable” data points to have additional layers of protection?

Insufficient technical solutions for explainability address one piece of our answer to the fourth question in our quest: why is it tricky to put these nudges in practice? The answer is that, there is no free lunch. There is mounting evidence showing that some of these properties conflict with each other. “Robust or Fair” is the title of one research paper detailing such a trade-off. You can have explainable AI systems or robust AI systems, but most likely, not both. You can have ML systems that are accurate at doing their tasks or robust to adversarial examples, but not necessarily both. So, you can have an AI system robust to stickers on the stop sign, but it might come at the cost of lowering the accuracy of identifying a pedestrian. If we rely only on AI systems, these are the trade-offs we might be forced to make.

But there are other reasons that the gap between standards and practice remains a chasm.

# Whatcha measure be whatcha get!

In our experience of applying the draft EU framework for AI systems as a tabletop exercise—the most mature requirement so far—we hit several roadblocks. One of the checklist items from the proposed EU framework included this question: “Did you assess potential forms of attacks to which the AI system could be vulnerable?”

This question seems straightforward enough to a policymaker, but to an ML engineer, it is too vague to be useful. It would be like asking a homeowner to “verify that your residence is burglar-proof.” Does a residence mean a townhome in Tennessee, a penthouse on Park Avenue, or a cabin in Colorado? Further, the guidance does not tell you *how* to burglar-proof the residence. Should one test the windows? Install cameras in the surroundings? Or install a moat with alligators? A world of choice leads to analysis paralysis.

In practice, no simple test applies to every AI system. Indeed, there is often not even a single ML model within an AI system! Instead, a network of interacting ML models works behind the