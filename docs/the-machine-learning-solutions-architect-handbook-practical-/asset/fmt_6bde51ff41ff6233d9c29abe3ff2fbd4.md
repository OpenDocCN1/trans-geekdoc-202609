
Despite their impressive performance on standardized tests like BAR or SAT, LLMs have limitations in certain aspects of cognitive abilities. One notable limitation is their inability to engage in complex reasoning and long-range strategic planning. While they excel at processing and generating text based on patterns and existing knowledge, they struggle with tasks that require a deep understanding of context and the ability to make nuanced decisions. These models also lack the fundamental understanding of common-sense knowledge that humans take for granted. As a result, these models may perform well in structured assessments but fall short when faced with real-world scenarios that demand higher-orders and decisions. This limits what kind of use cases generative AI can be applied to.

Many of the limits and challenges are yet to have practical solutions. So, it is essential to assess and understand the risks before deploying generative AI solutions for the intended use cases. Consider mitigating measures, such as the human-in-the-loop method, for decision making and grounding of generative AI with curated data sources to reduce hallucination.

# Summary

In this chapter, we provided a comprehensive overview of the generative AI project lifecycle, from identifying business use cases to model deployment. We explored major generative technologies like FMs and key techniques for customization including domain adaptation, instruction tuning, reinforcement learning with human feedback, and prompt engineering.

The chapter also covered specialized engineering considerations around large model hosting and mitigating risks like factual inaccuracies. While limitations exist, responsible development and governance can allow enterprises across industries to harness generative AI’s immense potential for creating business value. With an understanding of the end-to-end lifecycle, practitioners can thoughtfully architect and deliver innovative yet practical generative AI solutions.

In the next chapter, we will talk about the key considerations for building a generative AI platform, `retrieval-augmented generation` (`RAG`) solutions, and practical generative AI applications.

# Join our community on Discord

Join our community’s Discord space for discussions with the author and other readers:

[https://packt.link/mlsah](https://packt.link/mlsah)

![](OEBPS/Images/QR_Code70205728346636561.png)

# 16

# Designing Generative AI Platforms and Solutions

Deploying generative AI at scale in an enterprise introduces new complexities around infrastructure, tooling, and operational processes required to harness its potential while managing risks. This chapter explores the essential components for building robust generative AI platforms and examines `Retrieval-Augmented Generation` (`RAG`), an effective architecture pattern for generative applications. Additionally, we highlight near-term generative AI solution opportunities ripe for business adoption across industries. With the right platform foundations and a pragmatic approach focused on delivering tangible value, enterprises can start realizing benefits from generative AI today while paving the way for increasing innovation as this technology matures. Readers will gain insight into the practical building blocks and strategies that accelerate generative AI adoption.

Specifically, this chapter is going to cover the following topics:

*   Operational considerations for generative AI platforms and solutions

*   The retrieval-augmented generation pattern

*   Choosing a `Large Language Model` (`LLM`) adaptation method

*   End-to-end generative AI platforms

*   Considerations for deploying generative AI applications in production

*   Practical generative AI business solutions

*   Are we close to artificial general intelligence?

# Operational considerations for generative AI platforms and solutions

In an enterprise, deploying generative AI solutions at scale requires robust infrastructure, tools, and operations. Organizations should contemplate establishing a dedicated generative AI platform to meet these evolving project demands.

Architecturally and operationally, a generative AI platform builds on top of an ML platform with additional new and enhanced technology infrastructure for large-scale model training, large model hosting, model evaluation, guardrails, and model monitoring. As such, the core operation and automation requirements for a generative AI platform are similar to those of a traditional MLOps practice. However, the unique aspects of generative AI projects such as model selection, model tuning, and integration with external data sources, require several new process workflows to be established, and as a result, new technology components need to be incorporated into the operation and automation of the AI/ML platform.

In this section, we will delve into several new business and operational workflows involved in building and running generative AI initiatives, and their implication in new technology requirements and new functional roles.

## New generative AI workflow and processes

One of the key steps in building generative AI solutions is to select the right foundation models for further evaluation and/or fine-tuning against the requirements. Before generative AI, data scientists were mainly concerned with selecting the right algorithms to train models from scratch. While there were techniques such as transfer learning available, the scope was small, and mainly limited to some computer vision tasks and tuning of language models such as BERT. With large foundation models, the process of model selection becomes a lot more involved, and the model-tuning process has evolved as well. While instruction fine-tuning remains similar to traditional supervised learning, `Reinforcement Learning Human Feedback` (`RLHF`) is a brand-new process to be considered.
