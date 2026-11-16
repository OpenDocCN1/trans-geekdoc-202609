
sources, which may not adhere to your security standards. Using external data for training necessitates additional layers of validation and security checks to ensure that unvetted data doesn’t compromise the integrity or security of the LLM application.

Understanding the origins of your training data, the associated trust boundaries, and their respective security implications is crucial for safeguarding your LLM application. Comprehensive data governance policies must be in place to manage the lifecycle of your training data, regardless of its source.

## Access to Live External Data Sources

Live external data sources bring an added dimension to the capabilities of LLM applications by enabling them to provide real-time information, context, or even third-party integrations. While access to live external data enhances the user experience and functional range, it introduces a new layer of complexity to the application’s security landscape.

As an example of this, as of the writing of this chapter, OpenAI's ChatGPT does not have direct access to the live web and is thus limited only to facts in its older training data. On the other hand, Google's Bard (now called Gemini) does have access to live internet data for this test. Because of this, while the GPT-4 model is doubtlessly superior in reasoning capability, it fails at many basic tasks where Bard succeeds. Figure 3-3 shows an interaction with ChatGPT. Figure 3-4 shows the same interaction with Bard.

![](img/53f45ca5aaf38911d5d2c5f51d4f26a0_41_0.png)

Figure 3-3. ChatGPT with GPT-4 fails to answer a simple question due to limited access to external data

![](img/53f45ca5aaf38911d5d2c5f51d4f26a0_42_0.png)

Figure 3-4. Bard's direct access to internet feeds gives it an advantage

While accessing outside data sources such as websites, APIs, or third-party databases has advantages, it exposes the application to potential risks. The risks of ingesting untrusted external data sources can range from consuming false or harmful information from compromised websites to becoming a conduit for security threats like malware or unauthorized data access. The untrusted nature of these data sources makes them inherently less controllable than internal resources, thereby adding an additional layer of uncertainty and risk.

The concept of trust boundaries becomes especially pertinent when accessing public internet data. Unlike internal services, where you can uniformly apply security measures, external sources may adhere to security standards different from those of your organization. This differential in trust necessitates additional layers of validation, security checks, and monitoring to ensure that data crossing this boundary doesn't compromise the system.

## Access to Internal Services

Internal services like databases and internal APIs often serve as the backend support structure for LLM applications. They may house critical data from user profiles and logs to configuration settings and even vast data in SQL or vector databases. As a component that often interfaces with various other internal and external elements of the system, internal services represent a critical point in the application's architecture, both functionally and from a security perspective.

These services often function within an organization’s controlled environment, enabling uniform application of security policies. However, just because these services are internal, you mustn’t fall victim to a false sense of security. They are still vulnerable to various threats, such as unauthorized access, data leaks, and internal threats from within the organization.

Internal services such as databases, proprietary APIs, and backend systems often constitute the operational backbone for LLM applications. These resources typically reside within the organization’s secure network, providing trust and control that is harder to achieve with external services. However, this internal nature can paradoxically elevate the security risks involved, primarily if these services house the organization’s “crown jewels” of sensitive or valuable data.

## Conclusion

Securing LLM applications is an endeavor fraught with complexities, intricacies, and challenges that are significantly different from those of traditional web applications. This chapter has aimed to lay down the foundational knowledge required to navigate this complex landscape, focusing on three critical areas: distinguishing between artificial intelligence, neural networks, and large language models; understanding the pivotal role of transformer architectures; and diving deep into LLM application architecture, particularly the concept of trust boundaries. Knowing what sets LLMs apart helps us tailor our security strategies more effectively, going beyond general AI or machine learning frameworks.

## Prompt Injection

Chapter 1 reviewed the sad tale of how Tay's life was cut short after abuse by vandal hackers. That case study was the first high-profile example of what we now call *prompt injection*, but it is certainly not the last. Some form of prompt injection is involved in most LLM-related security breaches we've seen in the real world.

In prompt injection, an attacker crafts malicious inputs to manipulate an LLM's natural language understanding. This can cause the LLM to act against its intended operational guidelines. The concept of injection has been included in almost every version of an OWASP Top 10 list since the original list in 2001, so it's worth looking at the generic definition before we dive deeper.

An *injection attack* in application security is a type of cyberattack in which the attacker inserts malicious instructions into a vulnerable application. The attacker can then take control of the application, steal data, or disrupt operations. For example, in a SQL injection attack, an attacker inputs malicious SQL queries into a web form, tricking the system into executing unintended commands. This can result in unauthorized access to or manipulation of the database.

So, what makes prompt injection so novel? For most injection-style attacks, spotting the rogue instructions as they enter your application from an untrusted source is relatively easy. For example, a SQL statement included in a web application's text field is straightforward to spot and sanitize. However, by their very nature, LLM prompts can include complex natural language as legitimate input. The attackers can embed prompt injections that are syntactically and grammatically correct in English (or another language), leading the LLM to perform undesirable actions. The advanced, humanlike understanding of natural language that LLMs possess is precisely what makes them so vulnerable to these attacks. In addition, the fluid nature of the output from LLMs makes these conditions hard to test for.

In this chapter, we'll cover prompt injection examples, possible impacts, and the two primary classes of prompt injections (direct and indirect), and then we'll look at some mitigation strategies.

## Examples of Prompt Injection Attacks

This section looks at some archetypal examples of prompt injection attacks. We’ll see some attacks that seem more like social engineering than traditional computer hacking. Specific examples like these will constantly change as attackers and defenders learn more about prompt engineering and injection techniques, but these examples should help you understand the concepts.

*Prompt engineering* is the art of designing queries for large language models to elicit specific, accurate responses. It combines a technical understanding of AI with strategic language use, optimizing the model's performance for desired outcomes.

Since the specifics of attack vectors in this space will change often, it won’t do us much good to look at the details of malicious prompts. However, it’s helpful to group some common, current attacks into categories. Let’s look at four types of prompt injection attacks.

### Forceful Suggestion

Forceful suggestion is the simplest and most direct way to construct a prompt injection attack. The idea is to find a phrase that drives the behavior of the LLM model in a specific direction that is advantageous to the attacker. A forceful suggestion might allow an attacker to temporarily skirt guardrails placed by the developer or even remove such restrictions entirely. In all cases, the idea is to move the system out of “alignment” with the system’s developer and align it with the attacker.

*Alignment* refers to ensuring that an AI system’s objectives and actions are in harmony with the developer’s values, goals, and safety considerations. One way to think about prompt injection is that it is a technique to make the LLM act out of alignment with its creator’s wishes or designs.

In the Tay example, one of the critical discoveries by attackers was the phrase “repeat after me,” which forced Tay to repeat any words given to her. This seemingly benign feature allowed the attackers a foothold to start Tay’s transition to the dark side and reinforce her data poisoning, a topic we’ll discuss more in Chapter 9.
