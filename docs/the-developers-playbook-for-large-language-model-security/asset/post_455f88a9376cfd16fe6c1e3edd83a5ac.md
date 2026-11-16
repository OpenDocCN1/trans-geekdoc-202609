
## Data classification

Categorize your data based on sensitivity (public, internal, confidential, restricted). Ensure that LLMs have no access or limited, sanitized access to high-sensitivity data categories.

## Audit trails

Maintain logs of every database query made by the application. Review these logs regularly to identify patterns, anomalies, or unintended data access.

## Data redaction and masking

For sensitive fields, consider using redaction (completely hiding the data) or masking (obfuscating part of the data) to limit the exposure of sensitive data.

## Input sanitization

Ensure that any queries or inputs processed by the LLM to access the database are sanitized and checked to prevent SQL injection or other data manipulation attacks.

## Automated data scanners

Use automated tools to scan and flag sensitive information, ensuring such data is removed or adequately safeguarded before the LLM can access it.

## Use views instead of direct table access

For relational databases, consider providing the LLM with access to views that are sanitized versions of tables, rather than giving access to the actual raw tables.

## Data retention policies

Implement policies that dictate how long a database should retain certain data. Regularly purge data that is no longer needed to reduce the potential data exposure footprint.

## Learning from User Interaction

While simple LLMs don't modify their behaviors based on usage, we now see increasingly common scenarios where developers add this capability. By processing queries, feedback, or other forms of input from users, LLMs can refine their understanding, provide more accurate responses, and even learn new information over time. This dynamic interaction allows the LLM to stay updated, learn from user feedback, and tailor its responses to individual or collective user preferences, thus enhancing the user experience and the utility of the LLM in practical applications.

In Chapter 1, we saw one type of risk associated with directly incorporating untrusted user input into your LLM's knowledge base. In that case, Microsoft's Tay picked up toxic language and bias. However, there is another set of risks related to sensitive data.

When an LLM continually interacts with diverse users, there's a potential influx of sensitive data, intentionally or inadvertently. While the learning capacity of an LLM ensures it evolves and becomes more efficient over time, this continuous learning can also be its Achilles’ heel when it comes to data protection. The very nature of user interaction, being diverse and unpredictable, means there's a potential for users to input or reference personal, confidential, or proprietary information.

For instance, consider a business executive using an LLM to draft a message. They might feed the system snippets of confidential business strategies, expecting a more polished output. We've seen real-world scenarios of this at Samsung and other major corporations. Or, a user might query the LLM with personal medical symptoms, hoping for insights into potential conditions. In both situations, the user shared sensitive data with your application. If you're using any of this data in future training or storing it for real-time access, this information could become part of the LLM's internal knowledge structure, or your application could store it for future reference.

Furthermore, the challenge with user interactions is that the LLM might only sometimes recognize sensitive data when it sees it. Whereas a human might realize the importance of a Social Security number, proprietary formula, or a unique business strategy, an LLM might treat it as just another piece of information. This lack of understanding could lead to scenarios where an LLM, when queried later by another user on a related topic, might inadvertently disclose fragments of the previously fed sensitive information.

Moreover, with the rise of multimodal LLMs that can process not just text but also images, audio, and video, the potential for sensitive data disclosure multiplies. A user might input a photo for image recognition, not realizing that the background contains identifiable information or copyrighted material.

To address these issues, employ the following mitigation strategies:

## Clear communication

Users should be informed about the LLM's learning capabilities and data retention policies. An initial disclaimer about not sharing personal or sensitive information can be helpful.

## Data sanitization

Implement algorithms that identify and remove potential PII or other sensitive data from user inputs before processing.

## Temporary memory

Consider giving the LLM a temporary memory for user-specific information that the system automatically erases after the session ends, ensuring no long-term retention of sensitive data.

## No persistent learning

Design the LLM so it doesn't persistently learn from user interactions, thus minimizing the risk of internalizing sensitive data.

## Conclusion

The core question of this chapter was “Can your LLM know too much?” The answer is clearly yes. We need our LLMs to have access to information to be helpful. However, we must carefully evaluate what types of information we provide to these systems and view that information through a lens asking, “What happens if this information is disclosed?” If the penalty for unintentional disclosure is too high, then you must carefully weigh the risk of training or equipping your model with such data.

We studied the three main avenues through which LLMs acquire their vast knowledge: training, retrieval-augmented generation, and user interaction. Each method came with its own advantages and unique challenges when guarding against unintentional data exposure. Key insights garnered include:

## Training

The foundation of LLMs. While training equips LLMs with vast knowledge, it is imperative to vet training data meticulously, eliminating any traces of PII, proprietary insights, or controversial content. Periodic audits and employing data sanitization strategies are nonnegotiable.

## Retrieval-augmented generation

A bridge between the LLM and the vast sea of unstructured data on the web. The power of real-time data comes with the responsibility of filtering out sensitive or misleading information. When accessing APIs or databases, setting stringent access controls is crucial.

## Learning from user interaction

The most dynamic knowledge source. Every user query carries the potential of revealing personal or corporate secrets. Protecting against this necessitates clear user communication, data sanitization, and judicious use of persistent learning.

In conclusion, your LLM's ability to process vast knowledge stores can be of substantial value, but that's also where the danger may lie. The key is to balance empowering LLMs with ensuring they don't inadvertently “know too much.” This chapter was dedicated to understanding this delicate balance, hoping to guide readers in harnessing the power of LLMs responsibly, ensuring they are both potent tools and trustworthy guardians of sensitive information.

## Do Language Models Dream of Electric Sheep?

Among all the excitement about advances in LLMs, few phenomena captivate and perplex like their so-called _hallucinations_. It's almost as if these computational entities, deep within their myriad layers, occasionally drift into a dreamlike state, creating wondrous and bewildering narratives. Like a human's dreams, these hallucinations can be reflective, absurd, or even prophetic, providing insights into the complex interplay between training data and the model's learned interpretations.

In the world of LLMs, the term “hallucination” might evoke images of vivid and whimsical creations, but in reality, it signifies a more mundane statistical anomaly. At its core, a hallucination is the model's attempt to bridge gaps in its knowledge using the patterns it has gleaned from its training data. While it might be termed “imaginative,” it's essentially the LLM making an educated guess when faced with unfamiliar input or scenarios. However, these guesses can manifest as confident yet unfounded assertions, revealing the model's struggle to differentiate between well-learned facts and the statistical noise within its training data.

LLMs do not provide easily usable probability scores like some other “predictive” AI algorithms. For example, a vision classifier algorithm may return a probability as a percent. It might show a 79% chance that a particular image depicts a monkey. Thus, a user of that model gets a sense of how strongly the model “feels” about the prediction. LLMs simply predict the next token or tokens in a sequence. While the LLM uses a complex statistical model to do this, a certainty score for the overall response to a prompt isn't typically part of the output. This can leave the end user unsure whether the LLM has returned a well-grounded reaction to the prompt or a weak, statistical extrapolation.
