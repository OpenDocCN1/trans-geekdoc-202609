

More recently, in 2021, the `European Union` (`EU`) introduced the `EU AI Act` to promote the benefits of AI, while also ensuring the safe and responsible use of AI in the EU. The Act takes a risk-based approach to regulating AI, with different requirements based on the level of risks associated with AI systems. For example, AI systems supporting critical infrastructure would be rated with the highest risk designation and require the strictest oversight and regulations. The regulation also proposes provisions for AI transparency and accountability in the AI decision-making process, such as requirements for explainability and the ability to challenge the decisions made by AI systems. It also has new rules for AI use in biometric identification and surveillance.

# Understanding AI risk management

To address the various risks associated with AI and to comply with different compliance regulations, many organizations, especially in the regulated industry, have developed and implemented AI risk management programs. In short, AI risk management is the process of identifying, assessing, and mitigating the risk associated with the use of AI in automated decision-making. The ultimate goal of AI risk management is to establish trust in the `AI/ML` systems and ensure compliance with applicable rules and regulations.

Trusting an AI system requires rigorous assessment and consideration of the AI system across many different dimensions and criteria. Functionally, a trusted AI system needs to provide valid predictions/responses reliably for its intended use. This means that generated predictions/responses are consistently valid and can be trusted for reliable decision-making. Ethically, a trusted AI system needs to be safe to use, explainable, privacy-protected, and fair with bias properly managed and mitigated. From a cybersecurity perspective, a trusted AI system also needs to be secure and resilient against adversarial attacks. Lastly, a trustworthy AI system needs to provide transparency such as what and how data, algorithms, and models are used in the system. It is worth noting that it is often a balancing act and trade-off across these different dimensions when building and operating a trustworthy system, based on the needs and objectives of an organization. For example, to protect privacy, an organization might need to make sacrifices in model accuracy or prediction speed.

Now we understand what it takes to have trust in AI systems, let’s explore and dive deep into the AI risk management framework and its various components. The following figure illustrates the key components of AI risk management, which mainly consists of applying `MRM`, enterprise risk management, and third-party risk management across the AI lifecycle, governed by a set of AI risk governance principles. In this chapter, our exclusive focus will be on `MRM`. Enterprise risk and third-party risk management extend beyond the realm of AI and are universal considerations.

![](OEBPS/Images/B20836_12_01.png)

Figure 12.1: AI risk management components

Next, we will delve into the details of governance oversight principles and the AI risk framework. We will focus mainly on the understanding of AI risk governance and `MRM`, with the understanding that traditional enterprise security and third-party risk management are also part of the overall AI risk management considerations.

## Governance oversight principles

Implementing AI risk management starts with establishing key governance principles. The principles clarify the ultimate goals for what needs to be accomplished with risk management programs. Depending on the business and the regulatory environment an organization is in, an organization can make a decision on whether it should be included in its risk management framework. The following are some of the key areas for consideration:

*   `Transparency`: AI systems should be designed in a way that allows stakeholders to understand how decisions are made and why. This may include the ability to explain the ML model predictions, as well as transparency on what and how the data and algorithms are used and implemented.

*   `Accountability`: Organizations should be accountable for the decisions made by AI systems, including any negative consequences that may arise from their use. This accountability will ensure the owning organizations are incentivized to institute relevant policies and processes to govern the ML lifecycle.

*   `Data governance`: Organizations should ensure that the data used to train AI systems is accurate, representative, ethical, and unbiased. Without proper data governance, it would be highly challenging to trust AI systems that are built with ungoverned data.

*   `Human oversight`: While AI systems are meant to make decisions automatically in most cases without human intervention, organizations should have the ability to implement human oversight where required, meaning that humans should be involved in decision-making where it makes sense and should have the ability to override decisions when necessary.

*   `Privacy and security`: Appropriate policies and processes should be established to ensure AI systems are designed to protect the privacy and security of assets according to laws and regulations. Privacy and security breaches can have significant financial and non-financial implications for an organization.

*   `Fairness`: AI systems should not discriminate against certain individuals or groups based on attributes such as race and gender.

*   `Validity and reliability`: AI systems should be designed to produce reliable and valid results. Appropriate model validation and testing frameworks and processes need to be implemented to ensure highly reliable and predictable behaviors are displayed by AI systems in production. Mechanisms should be established to monitor system behaviors with processes for mitigation and rollback when abnormal behaviors are observed.

With governance oversight, organizations should also consider requirements for regulatory compliance, policies and guidelines around roles and responsibility, and standards and processes around AI systems and model inventory and risk classification, as well as how to deal with lifecycle and change management.

## AI risk management framework

With the AI governance oversight principles defined, organizations can move forward to establish a formalized AI risk management framework and detailed mechanisms for risk identification, risk assessment, and risk mitigation across the end-to-end ML lifecycle. One of the common frameworks adopted by many organizations is the Three Lines of Defense `MRM` model that is commonly used in the financial services industry. This framework focuses on establishing policies, roles, responsibilities, and processes designed to identify, assess, mitigate, and audit potential model risks associated with business problem identification, data management, and model development, deployment, and uses.

The first line of defense is owned by business operations. This line of defense focuses on the development and use of ML models. Business operations are responsible for creating and retaining all data and model assumptions, model behavior, and model performance metrics in structured documents, based on model classification and risk exposure. Models are tested and registered, the associated artifacts are persisted, and results can be reproduced. Once models are deployed, system issues, model outputs, model bias, and data and model drifts are monitored and addressed according to the established procedures and guidelines.

