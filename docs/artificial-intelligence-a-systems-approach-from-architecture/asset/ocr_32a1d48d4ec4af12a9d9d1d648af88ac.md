# Chapter 10: AI Deployment Guidelines

The AI ecosystem also serves as the foundational environment where an Agile process can be executed, while effectively and efficiently traversing all the elements of the AI system architecture framework shown in figure 10.3.

In the next section, we focus on the evaluation stage of the AI ecosystem. The gold standard, consisting of the test harness (i.e., the infrastructure necessary to perform the verification and validation tests), performance metrics, and benchmarks, constitutes critical parts of an overall AI infrastructure.

# 10.6 Gold Standard: Test Harness, Performance Metrics, and Benchmarks

The AI ecosystem not only serves as the foundational structure to successfully executing the strategy, but it also helps in transitioning from development to production. Many organizations fail in this transition because data science projects are decoupled from the business operations. Joshi et al. stressed the importance of coupling the end user through the development of data science projects [27]. The AI ecosystem facilitates this coupling.

However, the business goals and stakeholders’ requirements are the start of the AI development and deployment journey, as discussed in SRL 1. As shown in the AI ecosystem in figure 10.4, there is also a need to assess the prototype system against a gold standard. The gold standard is integral to successfully completing SRLs 5–9.

In this section, we address how to properly use a gold standard. Unfortunately, this topic is not very well ingrained among the AI community in the practice of developing and deploying AI products or services. The proper use of a gold standard is at the core of the systems engineering discipline emphasized throughout this book and illustrated in figure 10.1, as part of the system architecture building blocks, and the end-to-end AI capability.

One of the authors (D, Martinez) has decades of firsthand experience in the development and deployment of complex, real-time signal processors [28, 29]. In addition to following a systems engineering methodology during unit-level testing, subsystem integration, and single-thread integration, a key enabler successfully deploying a system was the V&V based on high-fidelity simulations used in modeling the user’s environment. In the implementation of these signal processors, the data simulations were done using fixed-point arithmetic and input into the real-time system during different stages of development. The results were then compared to a gold standard, simulated with full precision, to assess the accuracy and measure quantitative losses of the signal processing algorithms when operating in real time. These complex