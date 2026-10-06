# 356 Chapter 10: AI Deployment Guidelines

+   - The AI system architecture implementation illustrated in figure 10.3, while following the SRLs described in table 10.3

The rapid evolution of AI and the need for rapid and iterative demonstrations have led to adopting an Agile software methodology, which evolved as an alternative to the classical waterfall software development methodology. Complex hardware and software are best developed in incremental versions (i.e., shorter cycles) to get customer feedback and to improve the ultimate value to the customer instead of a long period of development before you see the system instantiated (as occurs with the classical waterfall methodology). The Agile process methodology had its origin in a “Manifesto for Agile Software Development” [20, 21], supported by twelve principles as outlined in table 10.5.

As shown in the AI system in figure 10.4, there is also a need to assess the prototype system a gold standard. The gold standard is an integral part to success-fully completing SRLs 5–9.

Unfortunately, this topic is not well inrained in the AI community when it comes to the practice of developing and deploying AI products or services. The proper use of a gold standard is at the core of the systems engineering discipline established throughout this book and illustrated in figure 10.1 as part of the subsystem integration, verification, and validation of each of the AI system architecture blocks, as well as the end-to-end AI capability.

Unfortunately, there is an emerging concept referred to as “digital twins”, which can now be used in the development and deployment of complex AI systems. A digital twin infrastructure can facilitate a test harness for implementing performance metrics and benchmarks—in some instances, that infrastructure might have those tools already available.

Digital twins are used for much more than performing AI system assessments. An AI platform, with a digital twin, can look at how an AI capability will function using a virtual environment with simulated sensors, physical sensors, or a hybrid of the two across the full AI pipeline.

There are also many specific tools and benchmarks used to assess data quality, ML algorithms, and computing technologies, as discussed in this chapter and in earlier chapters of this book. However, as a community, we still lack rigorous end-to-end system benchmarks and standards.

We concluded this chapter with a discussion of the desired characteristics and the accrued benefits in the selection of an AI platform. An AI platform is necessary because of the likelihood of incurring “hidden technical debt,” as described by researchers at Google [43]. The ML code is a very small component of what is needed to successfully