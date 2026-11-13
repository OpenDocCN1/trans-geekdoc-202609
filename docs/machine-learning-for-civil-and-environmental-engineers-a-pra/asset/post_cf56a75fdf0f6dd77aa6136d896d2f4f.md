
33 Tapeh, A. and Naser, M.Z. (2022). Discovering graphical heuristics on fire-induced spalling of concrete through eXplainable artificial intelligence. *Fire Technol*. doi: 10.1007/s10694-022-01290-7.

34 Hastie, T.J. and Pregibon, D. (2017). Generalized linear models. In: *Statistical Models in S*. doi: 10.1201/9780203738535.

35 Chen, T. and Guestrin, C. (2016). XGBoost: a scalable tree boosting system. *KDD '16: Proceedings of the 22nd ACM SIGKDD International Conference on Knowledge Discovery and Data Mining*. doi: 10.1145/2939672.2939785.

36 Molnar, C. (2019). Interpretable machine learning. In: *A Guide for Making Black Box Models Explainable*. Book.

37 Naser, M.Z. (2020). Machine learning assessment of fiber-reinforced polymer-strengthened and reinforced concrete members. *ACI Struct. J*. doi: 10.14359/51728073.

38 Al-Tamimi, A.K., Hawileh, R., Abdalla, J., and Rasheed, H.A. (2011). Effects of ratio of CFRP plate length to shear span and end anchorage on flexural behavior of SCC RC beams. *J. Compos. Constr.* 15: 908–919. doi: 10.1061/(ASCE) CC.1943-5614.0000221.

39 De Lorenzis, L. and Teng, J.G. (2007). Near-surface mounted FRP reinforcement: an emerging technique for strengthening structures. *Compos. Part B Eng*. doi: 10.1016/j.compositesb.2006.08.003.

40 Hertz, K.D.D. (2003). Limits of spalling of fire-exposed concrete. *Fire Saf. J.* 38: 103–116. doi: 10.1016/S0379-7112(02)00051-6.

41 Kodur, V.K.R. and Phan, L. (2007). Critical factors governing the fire performance of high strength concrete systems. *Fire Saf. J.* 42: 482–488. doi: 10.1016/j.firesaf.2006.10.006.

## 8 Causal Discovery and Causal Inference

> There is no result in nature without a cause. Understand the cause, and you will have no need for experiments.
> Leonardo da Vinci

## Synopsis

The vast majority of this textbook is devoted to exploring, creating, applying, and assessing machine learning models. While this chapter continues this trend, yet unlike the rest, this chapter dives into the data in the hope of discovering the hidden mechanism(s) that generate the observations we are interested in.¹ My goal in this chapter is to divert your attention, for a bit, from the linear process of collecting data → run algorithms → arrive at a blackbox/whitebox ML model and toward collecting data → identify the data generating process² (DGP) → arrive at a causal ML → infer the effects of manipulation(s)/treatment(s). By now, you might be wondering. What is a DGP? What is a causal model? What are manipulations and treatments?

For this, allow me to first introduce some of the big ideas behind causality, its principles, and how we can integrate those into a ML paradigm.

### 8.1 Big Ideas Behind This Chapter

A fundamental pursuit for us is to understand how a phenomenon comes to be. As engineers, we design and conduct experiments to uncover cause(s) and effect(s)³ behind a phenomenon we happen to be interested in. Out of the system without having to resort to physical testing (or numerical simulation, etc.). Simply

- 1. Quick stories: Unlike the other chapters, I will be briefly going over two quick stories.
  - I have two nieces. They are four and three years old. Recently, they started to ask, why?, in response to many of our conversations, requests, and questions. We love their curiosity! As you know, the practice of questioning is very common to kids, and is, indeed, a process in which they learn! From this view, knowing the why is elementary! From this context, this chapter hopes to present a case for causality and causal ML.
  - In the previous chapter, I have italicized the data perspective in the last sentence of the first footnote. This chapter is about going beyond the data-driven nature of ML to identify causes and effects. I have debated the inclusion/de-inclusion this chapter from this textbook multiple times. Evidently, I feel that including this chapter would be more beneficial than excluding it.
- 2. The data generating process (DGP) can be simply defined as the process that generates the data. For example, loaded beams tend to deflect. A possible question targeting DGP would be, what causes a loaded beam to deflect? Thus, in a journey aimed at answering such a question, our goal is to identify or retrieve the underlying structure of DGP. Please refer to my review in [36] from which this chapter stems.
- 3. Say what causes a beam to fail in a certain way (i.e., flexure) as opposed to another (e.g., shear). Also, note that I am confining this discussion to physical testing. The same discussion could possibly be extended to FE simulations and analytical investigations.

put, manipulation causes the system to change. The effect of such change allows us to peek into a specific direction as to how the phenomenon occurs.

Causal knowledge depicts how a phenomenon, Y, comes to be by answering a specific set of questions such as, what causes Y? How, when, and why does Y occur? What would happen if we were to influence Y or one of its factors, etc.? [1]. Arriving at precious answers to such questions is an exciting and ambitious quest. All of which makes causal knowledge difficult to obtain [2].

Let us be optimistic for a minute and assume that we were able to arrive at the true DGP for testing beams under fire conditions – as in, we uncovered the DGP for how beams deflect when exposed to fire. With that in mind, it is then plausible that this knowledge will be tremendous since we will not need to rely heavily on expensive and complex fire tests. One might say, instead of testing, we could build FE models or a digital twin (DT) model – which happen to be more affordable than testing. This is a good suggestion! However, these models would still need to be validated, preferably per case basis, against a real fire test. To add a second shade of gray to the above, we continue to lack a standardized procedure to build and validate such models. In some instances, we cannot truly model some testing conditions. We are still constrained by the set of many assumptions and idealizations our models (numerical, analytical, physical, ML, etc.) have to obey. I, hence, believe that pursuing causal models is of high merit.

## 8.2 Re-visiting Experiments

As engineers, we devise an experiment (or a series of experiments) in hope of comprehending a phenomenon. In general, experiments are driven by a hypothesis. A hypothesis targets a specific direction to uncover the DGP (i.e., the cause(s) leading to the effect). We carry out our experiments and observe their outcome. Such outcome is then used to establish a set of theories. A theory postulates the workings of a DGP and gives us the recipe to predict the phenomenon with a level of certainty [3]. In other words, experiments draw a causal path (i.e., cause(s) → effect), for, without the cause(s), the phenomenon would not have been generated [4].

In the above procedure, we design controlled experiments. A benchmark specimen is kept as a reference line, which is also accompanied by a series of altered (manipulated) specimens. Each manipulated specimen is modified by changing a single parameter while holding all other parameters identical to the benchmark. Allowing only one parameter (say, X) to vary at a time gives us insights into how such parameter affects the observed response (e.g., the difference between the outcome of the altered specimen and that of the benchmark specimen is directly caused by the alteration of X) [4].

Let us think of the following simple example. Say we are trying to understand the concept of flexural capacity (bending) in simply supported steel beams. First, we will fabricate a Beam A with certain geometrical and material features. Then, we load this beam in a manner that enables us to capture its flexural response. We load the beam and report that this beam fails once the level of the applied moment reaches 361.6 kN.m.

In such an experiment, we associate the reported failure moment with the geometrical and material features as well as the loading configuration of Beam A. This link draws from the following observation: applying a bending moment of 361.6 kN.m to Beam A is followed by the failure of the beam. A series of questions may arise: what caused Beam A to fail? was failure triggered by the geometric configurations or material properties of Beam A? How do boundary and loading configurations affect such failure? These are causal questions.
