

> **TIP** Be inclusive of stakeholders from various departments to get a holistic view when drafting an ethics policy.

## HANDS-ON EXERCISE: SETTING UP A MODEL GOVERNANCE FRAMEWORK

**Goal:** Promote transparency, governance, compliance, quality, trust, and alignment with organizational objectives through a model governance framework.

| TASK | TASK DESCRIPTION | TASK OWNER | DELIVERABLES |
| :--- | :--- | :--- | :--- |
| Define ownership | Start by establishing the ownership of the model for various stages throughout its lifecycle. | Model governance team | Ownership documentation |
| Establish policies | Establish policies across the model lifecycle such as fairness, bias, interpretability, explainability, responsible AI, data privacy, security, etc., in line with industry regulations and company guidelines. | Compliance/regulatory team | Policy documentation |
| Establish review processes | Establish manual and automated review processes to ensure the model works without bias and with fairness. | Review team | Review process guidelines |
| Ensure traceability | Ensure traceability by tracking the model's activities across its lifecycle for troubleshooting, auditing, and regulatory compliance. | Audit & compliance team | Traceability report |
| Implement continuous monitoring | Implement continuous monitoring of the models using tools such as AWS SageMaker Model Monitor to ensure they work within prescribed ranges. | Monitoring & operations team | Continuous monitoring implementation and report |
| Conduct periodic audits of the governance framework | Ensure adherence to the governance framework through periodic audits. | Internal audit team | Audit reports |
| Impart training | Impart proper training and awareness about the governance framework and have clarity around everyone's roles and responsibilities. | Training and development team | Training materials and attendance records |
| Set up a feedback loop | Establish a feedback loop to ensure the governance framework is a living document that gets constantly updated and improved upon. | Feedback and improvement team | Feedback mechanism implementation and improvement plan |

## WORKBOOK TEMPLATE: MODEL GOVERNANCE FOR BIAS & ETHICS CHECKLIST

Download the “Model Governance for Bias & Ethics” template from the download section of the book (www.wiley.com/go/EnterpriseAIintheCloud). Use this template to ensure that the model is not biased and is ethical so that the results are not skewed or discriminatory in any way.

## SUMMARY

This chapter delved into the governance of models. Ethical considerations were emphasized, and you explored the topics of fairness, bias, explainability, and interpretability, as well as the implementation of augmented AI for human review. You learned about model tracking, from ownership to version control and lineage, and discussed managing model artifacts and controlling costs through tagging. The chapter concluded with practical steps to establish a robust model governance framework.

## REVIEW QUESTIONS

- 1. Which of the following services is useful for detecting threats like data leaks or unauthorized access?
  - A. Amazon S3
  - B. Amazon Macie
  - C. Amazon GuardDuty
  - D. AWS CodeCommit

- 2. What is the primary difference between model explainability and interpretability?
  - A. Explainability is about understanding the model's inner workings, while interpretability is about making sense of the model's outputs.
  - B. Explainability is about making sense of the model's outputs, while interpretability is about understanding the model's inner workings.
  - C. There is no difference; they mean the same thing.
  - D. Both concepts do not exist in model development.

- 3. Which of the following is NOT typically considered an artifact to be stored and managed in machine learning operations?
  - A. The preprocessed dataset used for training
  - B. Evaluation metrics to evaluate model performance
  - C. Temporary files generated during data cleaning
  - D. Model configuration, such as the hyperparameters

- 4. What is the first step in setting up a model governance framework?
  - A. Establish review processes
  - B. Implement continuous monitoring
  - C. Define ownership
  - D. Conduct periodic audits

## ANSWER KEY

- 1. C
- 2. B
- 3. C
- 4. C

# PART VIII

## Scaling and Transforming AI

You have built it, so now you can make it even bigger! In Part VIII, I present a roadmap to scale your AI transformation. I will discuss how to take your game to the next level by introducing the AI maturity framework and establishing an AI center of excellence (AI COE). I will also guide you through the process of building an AI operating model and transformation plan. This is where AI transitions from a project-level to an enterprise-level powerhouse.

## 21 Using the AI Maturity Framework to Transform Your Business

> The greatest danger in times of turbulence is not the turbulence—it is to act with yesterday's logic.
>
> —Peter Drucker

Having laid the foundation blocks for integrating AI into your business workflows, you will now venture into a pivotal phase: scaling and transforming your business through AI.

This chapter signifies a transformative shift from merely deploying AI systems to aspiring to become a genuinely AI-first company. But then, how do you know you are ready to make the transition? Enter the AI Maturity Framework (see Figure 21.1).

![](img/1490b3cf638678afadc8c48abc1698d5_571_0.png)

FIGURE 21.1: SCALE AND TRANSFORM: Use the AI Maturity Framework to transform your business

As you navigate this chapter, you will find the AI Maturity Framework to be an indispensable tool. This chapter walks you through the five stages of maturity, starting with the initial discovery, then pilot, operationalization, scaling, and culminating at the Transforming stage, where AI is not an addition but is core to your business strategy and operations.

**TIP** Understanding your company's vision and goals so you can conduct a maturity assessment helps identify gaps and enables you to create an AI transformation plan. This, in turn helps you move from pilot to production and makes AI a core part of your business strategy.

This chapter focuses on leveraging the AI Maturity Framework, a vital tool tailored to guide your business through the transformational journey of AI integration. By understanding where your organization stands in its AI maturity and recognizing the stages ahead, you can strategically plan, execute, and optimize your AI-driven solutions.

## SCALING AI TO BECOME AN AI-FIRST COMPANY

Now that you have deployed the pilot in production, it is time for the team to explore expanding AI adoption across the enterprise by identifying more use cases. You will soon realize that you can fully scale your AI efforts only if a few foundational elements are in place. To elevate your AI efforts to the next level, I recommend these three things:

- Setting up an AI center of excellence (AI COE)
- Developing the AI operating model
- Developing the AI transformation plan

These are interrelated, as you will learn after reading the rest of this chapter. The AI COE is responsible for building the AI operating model, a framework for adopting AI. The AI COE is also responsible for developing the AI transformation plan, which is used to implement the AI operating model. See Figure 21.2.

![](img/1490b3cf638678afadc8c48abc1698d5_573_0.png)

**FIGURE 21.2:** Strategic pillars for an AI-first strategy

This section explains how to set up an AI center of excellence to implement AI at the enterprise level. Typically, companies face many challenges during the first six months of setting up an AI COE, so following some of the best practices outlined in this section is wise.

> **NOTE** Setting up an AI COE is a strategic endeavor and needs careful thought and leadership support.

## Why Do You Need a Maturity Model Framework?

Companies such as Deloitte, Accenture, PwC, and Gartner have researched and concluded that only around 20 percent of companies have been able to go beyond the Envision or Launch phase. One of the reasons is that these companies have found it challenging to align the business, strategy, people, data, platform, governance, and operational capabilities to implement and realize the true business impact of AI. This maturity framework helps you measure where you are in the various stages of AI adoption across various dimensions,

