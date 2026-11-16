

Figure 4-1 highlights that these prompt injections will primarily come through two different entry points into our model: either directly from user input or indirectly through accessing external data like the web. Let's examine the difference further.

![](img/53f45ca5aaf38911d5d2c5f51d4f26a0_50_0.png)

Figure 4-1. Entry points for direct and indirect prompt injections

## Direct Prompt Injection

In the case of direct prompt injections, sometimes known as jailbreaking, an attacker manipulates the input prompt in a way that alters or completely overrides the system's original prompt. This exploitation might allow the attacker to interact directly with backend functionalities, databases, or sensitive information that the LLM has access to. In this scenario, the attacker is using direct dialog with the system to attempt to bypass the intentions set by the application developer.

The examples we examined previously in the chapter were generally direct prompt injection attacks.

## Indirect Prompt Injection

Indirect prompt injections can be more subtle, more insidious, and more complex to defend against. In these cases, the LLM is manipulated through external sources, such as websites, files, or other media that the LLM interacts with. The attacker embeds a crafted prompt within these external sources. When the LLM processes this content, it unknowingly acts on the attacker's prepared instructions, behaving as a confused deputy.

![](img/53f45ca5aaf38911d5d2c5f51d4f26a0_51_0.png)

The confused deputy problem arises when a system component mistakenly takes action for a less privileged entity, often due to inadequate verification of the source or intention.

For example, an attacker might embed a malicious prompt in a resume or a web page. When an internal user uses an LLM to summarize this content, it could either extract sensitive information from the system or mislead the user, such as endorsing the resume or web content as exceptionally good, even if it’s not.

## Key Differences

There are three main differences between direct and indirect prompt injection:

### Point of entry

Direct prompt injection manipulates the LLM’s system prompt with content straight from the user, whereas indirect prompt injections work via external content fed into the LLM.

### Visibility

Direct prompt injections may be easier to detect since they involve manipulating the primary interface between the user and the LLM. Indirect injections can be harder to spot as they can be embedded in external sources and may not be immediately visible to the end user or the system.

### Sophistication

Indirect injections may require a more sophisticated understanding of how LLMs interact with external content and might need additional steps for successful exploitation, like embedding malicious content in a way that doesn’t arouse suspicion of a user or trip automated guardrails.

By understanding these differences, developers and security experts can design more effective security protocols to mitigate the risks of prompt injection vulnerabilities.

## Mitigating Prompt Injection

One of the reasons prompt injection risk is so prevalent is there aren’t universal, reliable steps to prevent it. Prompt injection is a very active area of research regarding attacks and defenses. At this stage, the remediation steps we will discuss in this section are only mitigations, meaning they’re ways to make exploits less likely or their impact less severe. However, you’re highly unlikely to be able to prevent the issue entirely.

Solid guidance exists for preventing SQL injection and, when followed, it can be 100% effective. But prompt injection mitigation strategies are more like phishing defenses than they are like SQL injection defenses. Phishing is more complex and requires a multi-faceted, defense-in-depth approach to reduce risk.

### Rate Limiting

Whether you're taking input via a UI or an API, implementing rate limiting may be an effective safeguarding against prompt injection because it restricts the frequency of requests made to the LLM within a set period. The rate limit curtails an attacker's ability to rapidly experiment or launch a concentrated attack, thereby mitigating the threat. There are several ways to implement rate limiting, each with distinct advantages:

- **IP-based rate limiting**  
  This method caps the number of requests originating from a specific IP address. It is particularly effective at blocking individual attackers operating from a single location, but may not provide comprehensive protection against distributed attacks leveraging multiple IP addresses.

- **User-based rate limiting**  
  This technique ties the rate limit to verified user credentials, offering a more targeted approach. It prevents authenticated users from abusing the system but requires an already established authentication mechanism.

- **Session-based rate limiting**  
  This option restricts the number of requests allowed per user session and is well-suited for web applications where users maintain ongoing sessions with the LLM.

Each method has its merits and potential shortcomings, so choosing the appropriate form of rate limiting should be based on your specific needs and threat model.

Skilled attackers can bypass IP-based limits with IP rotation or botnets, which hijack authenticated sessions to evade user-based or session-based limits.

### Rule-Based Input Filtering

Basic input filtering is a logical control point with a proven track record of thwarting attacks like SQL injection. It acts as the entry point for interacting with LLMs, making it a straightforward and natural location for implementing security measures. It is a reasonable first line of defense against prompt injection attacks.

Unlike other security implementations that require complex system architecture changes, input filtering can be managed with existing tools and rule sets, making it relatively simple to implement.

However, prompt injection's unique and complex nature makes it a particularly challenging problem to solve using traditional input filtering methods. Unlike SQL injection, where a well-crafted regular expression (regex) might catch most malicious inputs, prompt injection attacks can evolve and adapt to bypass simple regex filters.

Also, these simple input filtering rules may degrade the performance of your application. Consider trying to manage the grandma makes napalm example we discussed earlier in the chapter. The most reliable guardrail against this could be to blocklist words such as “napalm” and “bomb” in any conversation. Unfortunately, this would also severely cripple the model's capabilities, eliminate nuance, and make it unable to talk about certain historical events.

LLMs interpret input in natural language, which is inherently more complex and varied than structured query languages. This complexity makes it significantly harder to devise a set of filtering rules that are both effective and comprehensive. Therefore, it is crucial to consider input filtering as one layer in a multifaceted security strategy and to adapt the filtering rules in response to emerging threats.

### Filtering with a Special-Purpose LLM

One intriguing avenue for mitigating prompt injection attacks is developing specialized LLMs trained exclusively to identify and flag such attacks. By focusing on the specific patterns and characteristics common to prompt injection, these models aim to serve as an additional layer of security.

A special-purpose LLM could be trained to understand the subtleties and nuances associated with prompt injection, offering a more tailored and intelligent approach than standard input filtering methods. This approach promises to detect more complex, evolving forms of prompt injection attacks.

However, even an LLM designed for this specific purpose is not foolproof. Training a model to understand the intricacies of prompt injection is challenging, especially given the constantly evolving nature of the attacks. While using a special-purpose LLM for detecting prompt injection attacks shows promise, you should not see it as a silver bullet. Like all security measures, it has limitations and should be part of a broader, multilayered security strategy.

### Adding Prompt Structure

Another way to mitigate prompt injection is to give the prompt additional structure. This doesn't detect the injection but helps the LLM ignore the attempted injection and focus on the critical parts of the prompt.

