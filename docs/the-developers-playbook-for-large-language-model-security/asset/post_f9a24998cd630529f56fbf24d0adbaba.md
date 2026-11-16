

You'll need to focus on three pillars to ensure your artifacts are properly tracked, thus helping to ensure you're in control of your supply chain:

### Automated generation

Implement tools and workflows that automatically generate model cards and ML-BOMs at key development milestones.

### Secure storage

Store these artifacts in secure, version-controlled repositories to ensure they are tamper-proof and retrievable.

### Accessibility

Make these artifacts accessible to relevant stakeholders, incorporating search functionalities to facilitate quick retrieval and review.

The supply chain in LLM application development is a complex ecosystem that requires diligent management to ensure the security and integrity of both development artifacts and the development pipeline. By prioritizing the generation and storage of key artifacts like model cards and ML-BOMs and by securing the development pipeline, organizations can safeguard against supply chain vulnerabilities, fostering trust and reliability in their LLM applications.

## Protect Your App with Guardrails

Tools such as web application firewalls (WAFs) and runtime application self-protection (RASP) have become fundamental in defending web applications against attacks during runtime. Unlike AST tools that analyze code for vulnerabilities at build and test time, WAFs and RASP provide continuous protection while an application operates in production. They act as vigilant guardians, identifying and mitigating threats in real time, thus adding a critical layer of security.

In the context of LLMs, a parallel can be drawn with the concept of guardrails. Guardrails help ensure that LLMs operate within defined ethical, legal, and safety parameters, preventing misuse and guiding the models toward generating appropriate and safe outputs. Initially, guardrail implementations were relatively simplistic, often built in house and tailored to specific use cases. In Chapter 7, we walked through the construction of some simple guardrails to help screen output from the LLM for toxicity and PII. This exercise was a great way to understand the basics of how some guardrails work.

However, the demand for more sophisticated security and safety frameworks has increased as LLM-based applications have grown more complex. Today, there is a burgeoning ecosystem of tools, both open source and commercial, offering more comprehensive guardrail frameworks for LLMs. These tools serve as runtime security measures, continuously monitoring and guiding the behavior of LLMs to prevent the generation of harmful, biased, or otherwise undesirable content. They are akin to WAFs and RASP in the web application space, providing a dynamic shield that adapts to emerging threats and challenges.

## The Role of Guardrails in an LLM Security Strategy

Incorporating advanced guardrail solutions into LLM deployments is not just a recommendation; it’s becoming a necessity. As these models become more deeply integrated into critical and consumer-facing applications, the potential impact of their misuse or malfunction grows exponentially. Guardrails offer a way to mitigate these risks. Guardrails frameworks offer a range of functionality, but here are some typical functions you’ll want to look for as you evaluate your options.

### Input validation

There are several benefits of implementing guardrails that scan the input into your LLM:

### Prompt injection prevention

Monitor for signs of prompt injection, such as unusual phrases, hidden characters, and odd encodings, to prevent malicious manipulation of the LLM.

### Domain limitation

Keep the LLM focused on relevant topics by restricting or ignoring irrelevant prompts. This enhances security by reducing the risk of generating inappropriate or irrelevant content and diminishing the likelihood of hallucinations.

### Anonymization and secret detection

While interacting with the LLM, users may input confidential data, like email addresses, telephone numbers, or API keys. This poses a problem if the data is logged, stored, or transferred to a third-party LLM provider or if the data could potentially be used for training purposes. It’s crucial to anonymize PII and redact sensitive data before the LLM processes it.

### Output validation

Screening all output from your LLM is a critical part of your zero trust strategy. Here are some of the benefits:

### Ethical screening

Filter outputs for content that could be considered toxic, inappropriate, or hateful to ensure the LLM’s interactions align with ethical guidelines. This could have saved poor Tay from Chapter 1 and countless other projects from falling victim to vulnerabilities such as unchecked toxicity.

### Sensitive information protection

Implement measures to prevent the disclosure of PII or other sensitive data through the LLM's outputs.

### Code output

Look for unintended code generation that could lead to downstream attacks such as SQL injection, server-side request forgery (SSRF), and XSS.

### Compliance assurance

In sectors with strict regulatory standards, like health care or legal, tailor outputs to meet specific compliance requirements and keep the LLM's responses within the scope of its intended use.

### Fact-checking and hallucination detection

Verify the accuracy of LLM outputs against trusted sources to ensure the information provided is factual and reliable. Identify and mitigate instances where the LLM generates fictitious or irrelevant content to ensure outputs remain relevant and grounded in reality.

## Open Source Versus Commercial Guardrail Solutions

The choice between open source and commercial guardrail solutions depends on several factors, including the organization's specific needs, the level of customization required, and budget considerations.

Open source tools offer the benefits of flexibility and community support, allowing organizations to tailor solutions to their unique requirements. However, they may require significant internal expertise and resources to deploy and maintain effectively. Some examples of open source guardrails tools you may wish to evaluate include NVIDIA NeMo-Guardrails, Meta Llama Guard, Guardrails AI, and Protect AI.

On the other hand, commercial solutions may provide more out-of-the-box functionality with the added benefits of professional support, regular updates, and advanced features. Some examples of commercial guardrail options include Prompt Security, Lakera Guard, WhyLabs LangKit, Lasso Security, PromptArmor, and Cloudflare Firewall for AI.

## Mixing Custom and Packaged Guardrails

In Chapter 7, we implemented some basic guardrails by hand. While the emergence of prebuilt guardrail frameworks can offer a significant boost in security, these handcrafted guardrails still have a role. Supplementing a guardrail framework with your own custom, domain-, or application-specific guardrails can make a lot of sense. These types of defense-in-depth strategies are often the most successful in cybersecurity.

## Monitoring Your App

In the lifecycle of LLM applications, effective monitoring encompasses not only the conventional components—such as web servers, middleware, application code, and databases—but also the unique elements intrinsic to LLMs, including the model itself and associated vector databases used for RAG. This comprehensive approach is pivotal for maintaining operational integrity and security throughout the application's lifecycle.

### Logging Every Prompt and Response

One of the foundational practices in monitoring LLM applications is to log every prompt and response. This detailed logging serves multiple purposes: it provides insights into how users interact with the application, enables the identification of potential misuse or problematic outputs, and forms a baseline for understanding the model's performance over time. Such granular data collection is critical for diagnosing issues, optimizing model behavior, and ensuring compliance with data governance standards.

### Centralized Log and Event Management

Aggregating logs and application events into a _security information and event management_ (SIEM) system is essential. A SIEM system enables data consolidation across the entire application stack, offering a unified view of all activities. This allows your organization to easily store a historical record of how your application has responded to every user input. These centralized logs can then be stored for compliance purposes. Also, SIEM systems offer advanced search tools that enable your team to quickly search for patterns across a huge range of prompts and responses. This can enable your security operations team to hunt for threats while your application is in production.

### User and Entity Behavior Analytics

To enhance monitoring capabilities further, incorporating _user and entity behavior analytics_ (UEBA) technology can be layered on top of SIEM. UEBA extends traditional monitoring by leveraging machine learning and analytics to understand how users and entities typically interact with the application, thereby enabling the detection of activities that deviate from the norm. For LLM applications, extending UEBA frameworks to encompass model-specific behaviors—such as unusual prompt-response patterns or atypical access to the vector database—can provide early warning signs of security breaches, data leaks, or the need for model retraining. In addition, dramatic changes in usage patterns could help you identify denial-of-service, denial-of-wallet, and model cloning attacks, as discussed in Chapter 8.

