48 Chapter 2: Fundamentals of Systems Engineering

# 2.6 Systems Engineering Challenges

Systems engineering as a discipline, as discussed in this chapter, adheres to a set of fundamentals that have stood the test of time. But in addition, there are several important challenges that must be addressed as we apply systems engineering to AI. In this section, we present those challenges focused on the development and deployment of AI products and services.

Similar to earlier sections, we structure the challenges based on the triad of people-process-technology. This structure helps us delineate challenges over the full systems engineering spectrum—AI is not just about the best technology. We must give equal attention to processes and people, as delineated in table 2.1. We identify respective challenges under these three categories:

# Technology Challenges

+   1. Clearly articulating the stakeholder's requirements (both threshold and target requirements)
2. Functional architecture:
    * Design of a realistic architecture that can be implemented within the constraints of the available resources, schedule, and budget, while still meeting the stakeholder's requirements.
    * Availability of respective data (labeled "data" if using a supervised learning algorithm). Emphasis should be on good data (data that meet the performance desired of the ML algorithms) versus big data.
    * Rapid iteration of candidate ML algorithms, leveraging an agile development process, for example (more on this topic in chapter 10).
    * The determination of whether the computing should be performed at the enterprise level, at the edge, or a combination of both.
    * Identification of the right operating point between machines performing a task humans being complemented by the machine (i.e., the trade-off between confidence of the machine providing the desired insight relative to the consequence of actions).
    * Susceptibility to adversarial (intentional) attacks or unintentional use of AI systems.
    * Balancing all the issues addressed under the rubric of FASTEPS.