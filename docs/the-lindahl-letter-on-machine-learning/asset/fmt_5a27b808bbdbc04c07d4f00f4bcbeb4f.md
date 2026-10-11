
# Operationalizing Machine Learning

Operationalizing your machine learning is going to involve either connecting an API to your workflow or having the pipelines necessary to interact with your deployed model at scale. A ton of different open-source MLOps tools do that, and I have shared my analysis on them publicly. Being able to actively use these types of tools at scale and in production is a skillset. It is a skillset that is markedly different from the model-creation and data-management skills mentioned above. Running and operationalizing machine learning at scale is about the day-to-day management of use case execution. Are the response times from the model slowing down production, and are the accuracy and delivery of the use case within acceptable tolerances, or does action need to be taken? Efficiency of even the best models can degrade over time in a drift against your ROI that has to be accounted for and managed. See Figure 3 again.

## Figure 3. MLOps: Scale versus maturity

![](media/file10.png)

## Footnotes

[1] https://scholar.google.com/scholar?hl=en&as_sdt=0%2C6&as_vis=1&q=machine+learning+practitioner&btnG=

[2] You could watch that video here: https://vimeo.com/577702076

[3] https://www.kdnuggets.com/2020/12/roadmaps-ai-developer-data-scientist-machine-learning-engineer.html

---

# Substack Week 41: Machine learning and the metaverse

**Published on November 5, 2021**

This is a great week to talk about machine learning and the metaverse. You can check back on Substack and see I set this topic Week 28. All that said, it was just in time for Mark Zuckerberg to change the name of Facebook to Meta this week [1]. One of the best 60 second takes on the name change came from Gary Vaynerchuk: "Facebook's biggest strength over the last two decades has always been going to where the attention is."

https://www.youtube.com/watch?v=qPkYzSLabLE

Before we get into the machine learning part of this Substack post, it is probably best to acknowledge that people generally agree that the term metaverse was coined by Neal Stephenson in the novel *Snow Crash* (1992) [2]. I'll admit that the ebook is on my phone right now, and I'm very slowly reading it. It is fair at this point to note I now recall why exactly I have never finished reading this book from start to finish.

A lot of my writing ends up being about the intersection of technology and modernity. Those of you who have been reading my work for years know that it comes from a combination of my interests in civil society and technology. That is sort of where the idea of a metaverse begins to come forward. I really enjoyed the book *Ready Player One* by Ernest Cline (2011) [3]. A central premise of the book is that people spend a lot of time in a virtual world that is essentially a metaverse called the Oasis. Why did we just run down the journey from 1992 and *Snow Crash* to *Ready Player One* in 2011 and Facebook trying to become Meta in 2021? Well, the answer is pretty straightforward and has to do with a land rush to build an online world in the form of a metaverse. The company who probably is the most invested in winning this land rush toward building an online virtual world is Facebook/Meta.

That effort toward world building is going to include a ton of machine learning. My journey into reading articles this week on Google Scholar that related to a search for "machine learning metaverse" ended up being a strange look at a mix of ethics-related concerns plus the word metaverse [4]. My guess on that one is that for years now (probably since 1992), authors have figured out that taking a subject they normally publish on and adding the word metaverse in the title of the article helped to get it published. This same phenomenon happened with the phrase machine learning as well. That means that looking for academic articles with both machine learning and metaverse was a strange journey.

One of the more amazing things in the machine learning space is the idea of translation and what it can do for live conversations. Check out *The AI Show* from October 22, 2021, Episode 36: "Translator Now Supports 100+ Languages and Dialects": https://www.youtube.com/watch?v=LdDK5SoUsHE

## Footnotes

[1] https://about.fb.com/news/2021/10/facebook-company-is-now-meta/

[2] https://www.penguinrandomhouse.com/books/172832/snow-crash-by-neal-stephenson/

[3] https://www.penguinrandomhouse.com/books/209887/ready-player-one-by-ernest-cline/

[4] https://scholar.google.com/scholar?hl=en&as_sdt=0%2C6&q=metaverse+machine+learning&btnG=

---

# Substack Week 42: Time crystals and machine learning

**Published on November 12, 2021**

Things have certainly gotten interesting. Between all of the talk just about everywhere about the metaverse and the Facebook/Meta name change, you have to mix in what happened with time crystals before that, and you have clear evidence that we live in interesting times. You might be wondering if these two topics are related. Why did I end up putting them as back-to-back topics? The answer to that question is simple. The topics were arranged by the order of inspiration. Back on July 28, 2021, researchers from Google, Stanford, and Princeton released a paper on arXiv called, "Observation of Time-Crystalline Eigenstate Order on a Quantum Processor" [1]. The paper is 16 pages and seems to conclude, "These results establish a scalable approach to study non-equilibrium phases of matter on current quantum processors." In terms of raw scientific achievement, this is a truly interesting paper. We normally think of the states of matter in terms of solid, liquid, gas, and plasma. The math explaining the time crystals within that paper was a little intense. They model and explain the idea of a time crystal where a regular and repeatable cycle is created without burning any energy [2]. This would appear to defy the second law of thermodynamics, making it a very interesting discovery.

What does all of this talk about time crystals have to do with machine learning, you might be asking? I tried to set the stage in that first paragraph that this discovery is really cool in terms of theoretical physics and science in general. When the phrase "time crystals" with quotations and machine learning are dropped into Google Scholar, a total of 240 papers show up [3]. Some of those papers are part of phenomenon of interdisciplinary crossing, where people who have a very clear academic focus elect to take a very popular term and work it into the title of their regular academic research trajectory. In this case, that is a very interesting thing to consider doing, given the complexity of the mathematics involved in trying to model a time crystal. I could not model one on my home computer or within any of my cloud instances. Nothing that I have available to me can model quantum computing. Note back to that paper title above and the last two words that denote that the research was done on a quantum processor. That directly limits the number of researchers that are going to be able to contribute to this space. Access to quantum computing is rarified air in terms of cost and equipment. You could maybe get access with something like `IBM Quantum`, where you can get access to quantum computing from the cloud [4]. I did spend some time looking at the programs and services that `IBM Quantum` has online [5]. It is sort of interesting to see which ones are online and how many Qubits they have at each location.

After thinking about the definition of time crystals and looking around to figure out how I could access quantum computing in the cloud, I ended up digging into a book from 2020, *Machine Learning Meets Quantum Physics* [6]. The book seems to really dig into things people are doing with machine learning within the context of quantum physics. That preview link lets you see roughly 61 pages of the book, including the introduction. They footnote in a very similar way to this weekly newsletter.

## Footnotes

[1] https://arxiv.org/abs/2107.13571
