
Simpson, Thomas W., and Vincent C. Müller. 2016. “Just War and Robot Killings.” *Philosophical Quarterly* 66 (263): 302–322.

Smolan, Sandy. 2016. “The Human Face of Big Data.” PBS documentary. 56 mins.

Sparrow, Rob. 2007. “Killer Robots.” *Journal of Applied Philosophy* 24 (1): 62–77.

Sparrow, Rob. 2016. “Robots in Aged Care: A Dystopian Future.” *AI and Society* 31 (4): 1–10.

Stahl, Bernd Carsten, Job Timmermans, and Brent Daniel Mittelstadt. 2016. “The Ethics of Computing: A Survey of the Computing-Oriented Literature.” *ACM Computing Surveys* 48/4 (55): 1–38.

Stahl, Bernd Carsten, and David Wright. 2018. “Ethics and Privacy in AI and Big Data: Implementing Responsible Research and Innovation.” *IEEE Security and Privacy* 16 (3).

Stone, Christopher D. 1972. “Should Trees Have Standing—toward Legal Rights for Natural Objects.” *Southern California Law Review* 2:450–501.

Strawson, Galen. 2005. Free Will. London: Routledge. Last modified February 29, 2004. http://www.rep.routledge.com/article/v014.

Sullins, John P. 2012. “Robots, Love, and Sex: The Ethics of Building a Love Machine.” *IEEE Transactions on Affective Computing* 3 (4): 398–409.

Taddeo, Mariarosaria, and Luciano Floridi. 2018. “How AI Can Be a Force for Good.” *Science* 361 (6404): 751–752.

Thompson, Judith Jarvis. 1976. “Killing, Letting Die and the Trolley Problem.” *Monist* 59:204–217.

Torrance, Steve. 2011. “Machine Ethics and the Idea of a More-than-Human Moral World.” In *Machine Ethics*, edited by Michael Anderson and Susan Leigh Anderson, 115–137. Cambridge: Cambridge University Press.

Turner, Jacob. 2019. *Robot Rules: Regulating Artificial Intelligence*. Berlin: Springer.

Tzafestas, Spyros G. 2016. *Roboethics: A Navigating Overview*. Berlin: Springer.

Vanderelst, Dieter, and Alan Winfield. 2018. “The Dark Side of Ethical Robots.” In *AIES '18: Proceedings of the 2018 AAAI/ACM Conference on AI, Ethics, and Society*, 317–322. https://doi.org/10.1145/3278721.3278726.

van Wynsberghe, Aimee. 2016. *Healthcare Robots: Ethics, Design and Implementation*. London: Routledge.

van Wynsberghe, Aimee, and Scott Robbins. 2019. “Critiquing the Reasons for Making Artificial Moral Agents.” *Science and Engineering Ethics* 25 (3): 719–735.

Verbeek, Peter-Paul. 2011. *Moralizing Technology: Understanding and Designing the Morality of Things*. Chicago: University of Chicago Press.

Wallach, Wendell, and Peter M. Asaro, eds. 2017. *Machine Ethics and Robot Ethics*. London: Routledge.

Westlake, Stian, ed. 2014. *Our Work Here Is Done: Visions of a Robot Economy*. London: Nesta.

Whittaker, Meredith, Kate Crawford, Roel Dobbe, Genevieve Fried, Elizabeth Kaziunas, Varoon Mathur, Sarah Myers West, Rashida Richardson, and Jason Schultz. 2018. “AI Now Report 2018.” New York University. https://ainowinstitute.org/ai_now_2018_report.html.

Winfield, Alan F., Katina Michael, Jeremy Pitt, and Vanessa Evers. 2019. “Machine Ethics: The Design and Governance of Ethical AI and Autonomous Systems.” *Proceedings of the IEEE* 107 (3): 509–517.

Woollard, Fiona, and Frances Howard-Snyder. 2016. “Doing vs. Allowing Harm.” In *Stanford Encyclopedia of Philosophy* Fall 2021 edition, edited by Edward N. Zalta. Palo Alto: Stanford University. https://plato.stanford.edu/archives/fall2021/entries/doing-allowing/.

Zayed, Yago, and Philip Loft. 2019. “Agriculture: Historical Statistics.” *House of Commons Briefing Paper* 3339:1–19.

Zuboff, Shoshana. 2019. *The Age of Surveillance Capitalism: The Fight for a Human Future at the New Frontier of Power*. New York: Public Affairs.

## 13 Intrinsic Motivations for Open-Ended Learning

Gianluca Baldassarre

### 13.1 Introduction

Cognitive robotics and machine learning are producing a growing amount of works on intrinsic motivations (IMs) and open-ended learning. IMs, often contrasted to extrinsic motivations (EMs) that in animals are directed to satisfy biological needs such as hunger and thirst, refer to processes such as curiosity, surprise, novelty, and success at accomplishing one’s own goals (Barto et al. 2004; Oudeyer et al. 2007; Baldassarre 2011; Baldassarre and Mirolli 2013). Open-ended learning refers to robots and agents that, similarly to the early development of humans (Weng et al. 2001; Lungarella et al. 2003), undergo prolonged periods of learning wherein they autonomously acquire knowledge and skills that might be useful to later solve tasks given by the user (Seepanomwan et al. 2017; Doncieux et al. 2018).

IMs are very important for robotics and machine learning because they can drive the autonomous open-ended learning of robots and machines by requiring little or no human intervention to furnish guidance in terms of data sets, behaviors to imitate, tasks, reward functions, and goals. Moreover, they allow the construction of robots and machines able to robustly operate in cluttered and unstructured environments posing challenges that cannot be anticipated at design time and preventing the possibility of programming behaviors in advance. Consider, for example, service robots that have to operate in warehouses, offices, houses, and health-care environments and in the fields of construction, agri-food, and space. Despite this importance, IMs are a subtle concept, as they come in different types, involve both functions (“what they are for”) and mechanisms (“how do they work”), and can be mixed in various ways in the components of cognitive systems and robot controllers. This tends to generate quite a lot of confusion and to make it difficult to choose between the different available solutions when implementing robots and machines. This chapter addresses this problem in two ways. First (section 13.2), it provides computationally driven conceptual grids to define IMs by contrasting them with EMs and then to classify different types of IMs based on their possible functions and mechanisms, in particular by referring to three main classes of IMs here referred to as epistemic intrinsic motivations (eIMs). Second (section 13.3), it presents a selection of example models from cognitive robotics and machine learning to show how different IMs can be used to face different computational problems. The work concludes (section 13.4) by presenting some of the open challenges of the research on IMs.

### 13.2 Conceptual Grids: Mechanisms and Functions of Extrinsic and Intrinsic Motivations and Classes of (Epistemic) Intrinsic Motivations

The concept of IM has been proposed and developed within the psychological literature to overcome the difficulties of the behaviorist theory on learning and drives (e.g., Skinner 1938; Hull 1943), in particular to explain why animals spontaneously engage in puzzles (Harlow 1950) or can be instrumentally conditioned to produce particular responses on the basis of apparently neutral stimuli (e.g., a sudden light onset; Kish 1955), as happens with “standard” primary rewards (e.g., food). Subsequent proposals highlighted how the properties of certain stimuli can trigger animals’ exploration and guide their learning processes—for example, when the stimuli are complex, unexpected, or in general surprising (Berlyne 1966). Another important thread of psychological research highlighted the importance that action plays in IMs—for example, in relation to the motivation coming from the fact that an agent manages to affect the environment with its behavior (effectance; White 1959) or can autonomously set its own goals and master their achievement (Ryan and Deci 2000). IMs involving actions are also related to sensorimotor contingencies studied by psychology and involving the mechanisms underlying the keen interest of animals and humans for the effects of their own actions (Polizzi di Sorrentino et al. 2014; Taffoni et al. 2014; Jacquey et al. 2019).

Within the computational sciences, Schmidhuber (1991a, 1991b) was the first to present a computational operationalization of some IM mechanisms (in particular *prediction-based IMs*; see below), and Barto et al. (2004) settled the fundamental link between IMs (in particular *competence-based IMs*; see below) and reinforcement-learning (RL) methods (Sutton and Barto 2018). These initial ideas were first developed within the developmental robotics scientific community (with works in the *IEEE Transactions on Autonomous Mental Development* journal, the International Conference on Development and Learning, and the Epigenetic Robotics Conference; Zlatev and Balkenius 2001; Lungarella et al. 2003; Oudeyer et al. 2007; Schembri et al. 2007; Doya and Taniguchi 2019), and more recently have been developed within the autonomous/cognitive robotics and machine-learning community (e.g., Bellemare 2016; Nair et al. 2018), in particular driven by the success of deep neural networks and RL (Goodfellow et al. 2017; Sutton and Barto 2018).

We now focus on understanding and defining these concepts more in detail and furnish conceptual grids on them. These grids are grounded in two perspectives from which one can look at cognitive processes (Tinbergen 1963; Marr and Poggio 1976): 1) the *computational functions* they serve—that is, the problems they solve: these indicate the possible “uses” for which they might be employed within an overall cognitive/robotic system; 2) the *mechanisms*, or algorithms: these refer to the information operations used to accomplish the functions. Some specifications are due on how the terms “functions” and “mechanisms” are used here. First, for animals “function” refers to *adaptive function*—that is, the utility of certain elements of intelligence, such as an IM, for the animal’s biological fitness. For robots, “function” refers to the utility of a certain element of the robot’s intelligence for the robot’s *user*. Second, as with the functions in a computer program, “functions” can
