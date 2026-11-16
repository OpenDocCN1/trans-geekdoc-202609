Unlike other security implementations that require complex system architecture changes, input filtering can be managed with existing tools and rule sets, making it relatively simple to implement.

However, prompt injection's unique and complex nature makes it a particularly challenging problem to solve using traditional input filtering methods. Unlike SQL injection, where a well-crafted regular expression (regex) might catch most malicious inputs, prompt injection attacks can evolve and adapt to bypass simple regex filters.

Also, these simple input filtering rules may degrade the performance of your application. Consider trying to manage the grandma makes napalm example we discussed earlier in the chapter. The most reliable guardrail against this could be to blocklist words such as “napalm” and “bomb” in any conversation. Unfortunately, this would also severely cripple the model's capabilities, eliminate nuance, and make it unable to talk about certain historical events.

LLMs interpret input in natural language, which is inherently more complex and varied than structured query languages. This complexity makes it significantly harder to devise a set of filtering rules that are both effective and comprehensive. Therefore, it is crucial to consider input filtering as one layer in a multifaceted security strategy and to adapt the filtering rules in response to emerging threats.

# # Filtering with a Special-Purpose LLM

One intriguing avenue for mitigating prompt injection attacks is developing specialized LLMs trained exclusively to identify and flag such attacks. By focusing on the specific patterns and characteristics common to prompt injection, these models aim to serve as an additional layer of security.

A special-purpose LLM could be trained to understand the subtleties and nuances associated with prompt injection, offering a more tailored and intelligent approach than standard input filtering methods. This approach promises to detect more complex, evolving forms of prompt injection attacks.

However, even an LLM designed for this specific purpose is not foolproof. Training a model to understand the intricacies of prompt injection is challenging, especially given the constantly evolving nature of the attacks. While using a special-purpose LLM for detecting prompt injection attacks shows promise, you should not see it as a silver bullet. Like all security measures, it has limitations and should be part of a broader, multilayered security strategy.

# # Adding Prompt Structure

Another way to mitigate prompt injection is to give the prompt additional structure. This doesn't detect the injection but helps the LLM ignore the attempted injection and focus on the critical parts of the prompt.