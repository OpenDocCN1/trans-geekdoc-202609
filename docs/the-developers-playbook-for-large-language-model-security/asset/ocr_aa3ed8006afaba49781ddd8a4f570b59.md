and offers an integrated environment to assess, improve, and monitor models on various dimensions of responsible AI, including fairness, interpretability, and privacy.

# # Giskard LLM Scan

Giskard LLM Scan is an open source tool used to assess an LLM’s ethical considerations and safety. Available under the Apache 2.0 license, this component of the Giskard AI suite aims to identify biases, detect instances of toxic content, and promote the responsible deployment of LLMs. It employs a variety of metrics and tests designed to evaluate LLM behavior in terms of fairness, toxicity, and inclusiveness. Through its interface, Giskard LLM Scan offers detailed reports highlighting areas of concern, assisting developers and researchers in understanding and potentially mitigating ethical risks in their AI models.

# # Integrating security tools into DevOps

Integrating automated, LLM-specific security testing tools and traditional AST (application security testing) tools into LLMOps processes is not merely beneficial but imperative. Embedding these tools within CI/CD pipelines ensures that security is not an afterthought but a foundational aspect of application development. This approach enables automated, repeatable security checks performed with every build, significantly reducing the risk of vulnerabilities in production. Moreover, it fosters a culture of security mindfulness among development teams, ensuring that security considerations are paramount from the inception of a project through to its deployment.

# # Managing Your Supply Chain

As discussed in Chapter 9, the supply chain represents more than sourcing components and tools. It involves the meticulous generation, storage, and accessibility of development artifacts such as model cards and ML-BOMs.

Model cards are essential documentation for LLMs, providing an overview of a model’s purpose, performance, and potential biases. Similarly, ML-BOMs detail the components, datasets, and dependencies involved in developing an application using machine learning technologies like an LLM. Together, these artifacts form a cornerstone of transparency and accountability in LLM development.

To manage them effectively, developers must implement systems for generating, storing, and making these artifacts easily searchable. This facilitates regulatory compliance and enhances stakeholder collaboration and trust. By integrating these practices into a broader SBOM strategy, teams can ensure a holistic view of both AI and non-AI components of their applications, reinforcing the security and integrity of the supply chain.