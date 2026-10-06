
# 214 Chapter 6: Human-Machine Teaming

final report, in the context of our discussion in this chapter, that there is no indication that technological advances will displace employment—instead, new work and jobs will be created. However, robotics and automation will play an increasing role in closing the gap between new jobs and the people available to fill those jobs. Another important finding of their study is that it takes a long time—measured in decades—between the birth of an invention and its commercial use. One of the important challenges will be how to prepare the workforce of the future for this inevitable transition of more and more operational roles being performed by intelligent machines.

## 6.7 Main Takeaways

It is indeed very exciting to witness and be part of the HMT evolution, as well as many applications where HMT is contributing to important business benefits and having societal impact. In this chapter, we have several examples used to ground this discussion. However, since HMT is a broad area, we also stated the working HMT definition we use in the book: HMT is the building block in the AI pipeline that transforms ML outputs (i.e., knowledge) into insights delivered to stakeholders (e.g., users, consumers, or customers).

HMT is a functional block in the simplified end-to-end architecture shown in figure 6.1. It spans a spectrum depending on the confidence that the human (as a joint role between a human and a machine) has in the machine making the decision versus the consequence of actions. Of course, the operating point in this spectrum is heavily dependent on the application domain. Several examples were illustrated to show how an AI practitioner would determine where to operate across this spectrum.

We discussed AI as a technology that augments human capabilities—meaning intelligent machines helping with the dull-dangerous roles, which allows humans to devote themselves to more cognitive functions. To reach this goal, we broke the discussion into three points:

- 1. AI as a search-and-discovery tool
- 2. AI as a teammate
- 3. Full autonomy

Today, it is not uncommon to hear the question, “When will intelligent machines achieve the same level of human intelligence?” There is a lot of debate within the AI community on the right answer. We believe that if the computation resources were there, it would be many years before intelligent machines can operate at the same levels of power efficiency as a human. Although there are many unprecedented remarkable advances to date, they require an immense amount of computation and electrical power, as discussed in chapter 5.

VPAs, because of the large advent of data, especially with the fast rate of increase in the proliferation of IoT devices, will continue to play an important role in our daily lives as AI search-and-discovery tools. Unfortunately, they remain mediocre, at, in answering more than just routine questions. Their limitations are in their ability to perform automatic speech recognition (e.g., users with strong accents), and the ability to achieve natural language understanding (e.g., in real-time applications).

Another role, occupying the middle of the HMT spectrum, is AI as a teammate. One example that we elaborated on was in the cybersecurity domain, where ML techniques were implemented as a recommender system. Again, to identify the HMT operating point, one must view this through the lenses of a trade-off between confidence level versus consequence of actions.

As we continue to advance AI systems to be able to make decisions autonomously, there is a need to ascertain whether these systems are operating under the rubric of RAI. There must be, at minimum, trust in the AI system. More generally, we emphasized the importance, regardless of where the HMT falls in the spectrum earlier, of complying with FASTSTEPS principles. That topic will be discussed further in chapter 8.

Full autonomy, particularly with autonomous vehicles, continues to be difficult to achieve because these systems are not yet able to operate in environments like city traffic, which are complex and require decision making while operating at high speed. Nevertheless, there have been impressive achievements with autonomous systems either in low-complexity scenarios (e.g., farming) or cases where the autonomous vehicles are limited by geofenced boundaries.

HMT is becoming the part of the AI pipeline where "rubber meets the road." We can have super data and well-performing ML algorithms, enhanced by modern computing, but unless the HMT step is able to create insights that provide value to the stakeholders, the AI system will fail to find acceptance in operations. Therefore, it is imperative that the AI community pays attention to qualitative and quantitative performance metrics, which will help practitioners determine if AI products or services are suitable for deployment. We formulated

- 1. Confidence
- 2. Consequence
- 3. Model representation
- 4. RAI

These performance metrics must be integrated into AI implementation and integration-verification-validation as part of the framework illustrated in figure 6.10. We will discuss in chapter 10 the process of assessing, in an iterative way, the overall AI system.

The AI research community is demonstrating very innovative architectures to have humans and machine work more effectively as teammates. These efforts emphasize the importance of building representative humans and machine models along realistic models.

We elaborated on a number of HMT challenges structured under the topology of micro-level and macro-level challenges. Admittedly, since HMT is a broad topic, we were only able to highlight a subset of HMT challenges in this chapter. The reader is encouraged to follow up with the extensive references provided in this chapter. One exciting area, but one that is also experiencing a number of research challenges, is the confluence of neural network and symbolic AI architectures. We also highlighted additional areas of research, such as multifaceted learning and self-supervised learning.

We concluded the chapter with a view of the future. All the indications are that intelligent machines will not displace the workforce. Instead, AI is likely to create new jobs, just as history has shown that general-purpose technologies contributed to new work.

## 6.8 Exercises

- 1. What is the working definition of HMT used in this chapter? Elaborate on the important concepts.
- 2. Explain the HMT spectrum and associated roles between human and machine.
- 3. Within HMT functions, decisions are best left to only the machine with confidence level is low.
  a. True
  b. False
- 4. A human, on average, uses about 100 watts, and 80 percent of that is consumed by the brain.
  a. True
  b. False
- 5. Provide real-world examples of VPAs used today as AI search-and-discovery tools and discuss their limitations.
- 6. One of the biggest challenges with robots today is their ability to perform tasks that humans commonly do with hands.
  a. True
  b. False
- 7. Explain why full autonomy is hard, and discuss with respect to complexity and speed.
- 8. Describe the four tiers of performance metrics and elaborate on their respective importance.
- 9. Provide examples of micro-level and macro-level challenges.
- 10. Explain what is meant by neurosymbolic AI.
- 11. What is the meaning of self-supervised learning? Why is it an important next step in AI?
- 12. It is expected that as autonomy and robotics advance, humans will be left without jobs.
  a. True
  b. False
- 13. How do you recommend that organizations prepare for a future where AI tools and techniques will do more of the routine tasks, permitting humans to undertake higher-level cognitive tasks?
- 14. With the advent of generative AI (e.g., GPT-4), what approaches do you recommend to verify the validity and veracity of the results?

## 6.9 References

- Asimov, I., *Reason. I. Robot.* 1941, 59–77.
- Asimov, I., Runaround. *Astounding Science Fiction, 1942*. 29(1): 94–103.
- Marcus, G. and E. Davis, *Rebooting AI: Building artificial intelligence we can trust*. 2019, Vintage.
- Martinez, D., N. Malsyka, and B. Sterling. *Artificial intelligence: Short history, present developments, and future outlook*. MIT Lincoln Laboratory, 2019. https://www.mit.edu/media/1186/
- Dubois, M. Halvey, and L. Azzopard, *A survey investigating usage of virtual personal assistants, 2018*. arXiv preprint arXiv:1807.04606.
- Martinez, D. Architecture for machine learning techniques to enable augmented cognition in the context of decision support systems, in *International Conference on Augmented Cognition*, Heraklon, Greece. 2014. Springer.
