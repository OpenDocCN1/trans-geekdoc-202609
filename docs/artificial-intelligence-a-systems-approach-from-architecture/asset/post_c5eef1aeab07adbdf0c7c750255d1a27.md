
## Chapter 8: Responsible Artificial Intelligence

![](img/3a09e5358d763329b6e01a25dd2312d4_288_0.png)

Figure 8.2 AI development life cycle (simplified).

- End user and stakeholder analysis: Who are the end users and relevant stakeholders, and what is the context in which the system will be deployed?
- Sociotechnical implications and potential harms: What are the sociotechnical implications and likelihood and magnitude of harms of the proposed AI solution?
- System reliability and safety measures: How are we ensuring system reliability and safety, and what is the process for identifying and correcting system errors?

Data involves the collection, cleaning, and processing of data that will be used to enable the underlying technology. The quality of data is foundational to the overall success of an AI product or service. In this phase, important decisions must be made about how data is sampled and collected, how it is cleaned and processed, and how validation sets are created and developed to evaluate prospective real-world performance. Stakeholders responsible for the design and development of AI solutions should consider the following:

- Representativeness of the data set: How well does my data set reflect the target audience in the real world?
- Bias in data: Are there inherent biases in my data set because of historical or societal bias?
- Limitations of data: What are the limitations of my data, and how can that influence the model’s behavior?
- Mitigating biases: How do we handle sensitive features such as race, gender, and socioeconomic status? How do such features present themselves through other proxy features (e.g., socioeconomic status and ZIP code)?

## 8.5: RAI Considerations in the AI Development Life

- Regulatory considerations: Are we adhering to any regulations and laws that govern the use of data and ensuring compliance?

Development involves the iterative process of building out the planned AI system, featuring important decisions around model selection and training, but also the over-all user interface/user experience and engineering needed to package and deliver core AI technology as an end product. In the development phase, the following important considerations must be:

- Success metrics and trade-offs: How do we measure and monitor success, what trade-offs are we making among the various metrics (e.g., fairness and accuracy)?
- System reliability and safety: Is the system designed with the appropriate guard-rails and reliability to safely respond to edge cases and resist unintended attacks?
- Explainability and transparency: Is the AI system transparent, and are the decisions and recommendations being made explainable?
- Postdeployment performance monitoring and alerting: What is the process for monitoring postdeployment system performance, and who is accountable for implementing these processes?

Deployment refers to the process of making the developed AI system available to real-world users in a production environment. In this stage, continuous testing and evaluation efforts must be made to ensure the upkeep of the system’s performance and reliability. In chapter 10, we discuss in detail ten guidelines for the deployment of AI, as well as minimizing the likelihood and magnitude of harms, as well as the overall role of test harness (i.e., the test infrastructure to evaluate an AI system), benchmarks, and metrics in AI deployment. In this stage, a number of important considerations must be made, such as the following:

- Input validation and monitoring: How are data inputs being qualitatively and quantitatively audited to protect against manipulation and subsequent concept drift?
- Performance and functionality evaluation: Is the capability still meeting the desired functional goals, and is production use aligned with intended use?
- Postdeployment monitoring and incident management: How are postdeployment monitoring signals being used to identify and rectify potential harms or errors?

## 8.6 RAI Challenges

In the earlier sections, we addressed many of the challenges with RAI that require cooperative efforts from government, academia, and industry. In recent years, regulatory efforts, such as the establishment of the National Intelligence Initiative Office and the National AI Act of 2020 [55, 56], have been made, and more-focused bills are being introduced in the US Congress to call for federal AI regulation. The National Institute for Standards and Technology (NIST) has also released the AI Risk Management Framework [57], a guidance document for voluntary use by organizations designing, deploying, or using AI in order to help them "enhance AI trustworthiness while managing risks" [58].

Broderick et al. provide useful guidance using a taxonomy of probabilistic ML [59]. The authors addressed the full cycle, from real-world goals (desired at deployment) through algorithm implementation (i.e., development) and culminating with real-world output. As they emphasized, trust can break down at any of these stages, including training. They also provide methods for increasing trust at different stages within their taxonomy.

The rapid progress in the AI field, such as OpenAI's ChatGPT, has accelerated attention being paid to policy and regulation. A nonprofit organization called the Future of Life Institute recently issued "Pause Giant AI Experiments: An Open Letter," calling for a six-month moratorium on the training of AI systems that were any more powerful than the recently released GPT-4 in order to accelerate the "development of robust AI governance systems." [60]. The call has sparked debate and criticism within the AI community and with the public, some arguing that it could provide time for reflection, evaluation, and planning around the potential risks and benefits of advanced AI systems, while others claim that will stifle innovation, progress, and economic growth in the field.

As AI continues to advance rapidly, it is crucial that regulatory efforts keep pace with the technological progress to ensure safe and responsible development and deployment of AI systems, without stifling innovation. Further research is needed to provide technical approaches to help in the design and development of AI systems that use generative AI technologies, including the designs to avoid harm [61].

In table 8.1, we formulate a set of challenges as a function of the horizons described in chapter 1, but we propose this set as a function of near-term, mid-term, and far-term (i.e., horizons 1, 2, and 3) challenges and opportunities.

The challenges and opportunities discussed in this chapter are crucial for the successful deployment and adoption of RAI. While there is much to be done, we are seeing

### Table 8.1 RAI challenges and opportunities

| Horizon | Opportunities |
| :--- | :--- |
| Horizon 1 (1–2 years): Content-Based Insight | Apply AI to gain insight on the content of interest in disparate types of data.<br>- Design, develop, and deploy AI with attention to system testing-verification-validation, consistent with the FASTEPS principles.<br>- Address the three types of biases: preexisting, technical, and emergent.<br>- Formulate AI system capabilities with business value, but within the guardrails, in order to avoid individual harm, collective harm, and societal harm |
| Horizon 2 (3–4 years): Collaboration-Based Insight | Extend AI roles to include multiple human-machine teams (HMTs) working together.<br>- Develop AI capabilities while ascertaining ethics of data, ethics of algorithms, and ethics of practice and use met.<br>- Test-verify-validate output at the human-machine teaming (HMT) stage.<br>- Build a multicultural and multistakeholder ecosystem of trust. |
| Horizon 3 (5+ years): Context-Based Insight | Incorporate semantic context in the application of AI.<br>- Confidence in the machine versus consequence of actions should also incorporate FASTEPS principles.<br>- Employ counterfactuals to ascertain that the context is consistent with societal moral and core values.<br>- Avoid company embarrassments by employing an AI ecosystem to perform early prototyping to obtain user feedback (i.e., lessons learned in context) prior to full deployment (see chapter 10). |
