Figure 3-2 adds the trust boundaries to our architecture diagram.

![](bbox=[0.14, 0.11, 0.86, 0.39])

# Figure 3-2. LLM application architecture with trust boundaries

These boundaries, as depicted in the diagram, serve as gateways through which the LLM interfaces with diverse components—public data from the web, structured databases, spontaneous user interactions, or internally sourced training sets. Each delineated boundary highlights considerations we must make when considering data that flows into and out of the LLM. Here’s a quick summary; we’ll dive more deeply in the next section:

# User interactions

You’ll need to consider safeguarding the model from potential adversarial or misleading inputs that users or systems might introduce. You’ll also need to worry about toxic, inaccurate, or sensitive data being output from the model and passed back to the user.

# In-the-wild training data

LLMs are often trained on massive amounts of internet data. You need to consider this data untrusted and watch out for potential toxicity, bias, and adversarial data poisoning, which we’ll cover in Chapter 7.

# Internal test and training data

You may use internally curated data to fine-tune your model, which can significantly increase accuracy. But you must be wary of ingesting and exposing sensitive, confidential, or personally identifiable information. We’ll discuss this more in Chapter 5.