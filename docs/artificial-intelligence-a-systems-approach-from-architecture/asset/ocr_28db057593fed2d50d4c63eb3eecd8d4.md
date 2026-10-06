# 11.1: Introduction to MLOps Fundamentals 365

evolve—as part of the CI/CD and monitoring cycles of the MLOps structure—into developments that are intended to transition into operations. The AI system architecture implementation framework shown in figure 10.3 enables the rigorous execution of the AISDM, while adhering to the SRL steps.

In this chapter, we start in section 11.1 with an introduction to the MLOps fundamentals. We then explore the MLOps flow in the instantiation of the AI system architecture implementation framework, discussed in section 11.2. Since an important objective, intrinsic to the MLOps flow, is to automate parts of the AI/ML development life cycle, we present representative MLOps enabling techniques and contemporary tools in 11.3.

We also discuss MLOps platforms, automated machine learning (AutoML), and low-code/no-code (LCNC) application development in section 11.4.

In section 11.5, we discuss a set of common pitfalls in AI development and deployment. We conclude the chapter with the main takeaways and exercises.

# 11.1 Introduction to MLOps Fundamentals

As we have described, within the MLOps definition, there are a set of fundamental elements that encompass the MLOps process. In this section, we introduce these key fundamentals, steps, and tasks that must be instantiated while following the MLOps process.

At a high level, and consistent with the cross-industry standard process for data mining (CRISP-DM) [8], the planning stage of an MLOps instantiation begins with a very good understanding of the business needs and stakeholder requirements of the organization, as discussed in chapter 3. Similarly, Baier et al. described the MLOps flow as follows: business understanding, data understanding, data preparation, model-ing, evaluation, and deployment [9]. These early stages of the MLOps process are key to the successful development and deployment of AI capabilities.

MLOps has evolved from well-understood fundamental steps—such as the DevOps methodology—adapted to the development and deployment of AI systems. We highlight the tasks found in the DevOps of software systems. The key steps are:

> DevOps: Plan by Code, Build, Test, Release, Deploy, Operate, and Monitor

Each of these steps or tasks must be implemented with security support, commonly referred to as “development, security, and operations (DevSecOps).”

For MLOps, we must modify these steps to include the full AI development and deployment life cycle: