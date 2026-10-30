
- 13. Slava Kalyuga, Paul Chandler, Juhani Tuovinen, and John Sweller. When problem solving is superior to studying worked examples. Journal of Educational Psychology, 93(3):579–588, 2001.
- 14. Suna Kyun, Slava Kalyuga, and John Sweller. The effect of worked examples when learning to write essays in english literature. Journal of Experimental Education, 81(3):385–408, 7 2013.
- 15. Wayne Leahy and John Sweller. Cognitive load theory, modality of presentation and the transient information effect. Applied Cognitive Psychology, 25(6):943–951, 11 2011.
- 16. Nadine Marcus, Martin Cooper, and John Sweller. Understanding Instructions. Technical Report 1, 1996.
- 17. Roxana Moreno and Richard E. Mayer. Cognitive principles of multimedia learning: The role of modality and contiguity. Journal of Educational Psychology, 91(2):358–368, 6 1999.
- 18. Seyed Yaghoub Mousavi, Renae Low, and John Sweller. Reducing Cognitive Load by Mixing Auditory and Visual Presentation Modes. Journal of Educational Psychology, 87(2):319–334, 1995.
- 19. Jacob Nielsen. Heuristic evaluation. In Jacob Nielsen and R. L. Mack, editors, Usability Inspection Methods. John Wiley & Sons, New York, 1994.
- 20. Jacob Nielsen. 10 Usability Heuristics for User Interface Design, 1995.
- 21. Jacob Nielsen. How I Developed the 10 Usability Heuristics. Jakob Nielsen on UX., 2024.
- 22. Jakob Nielsen. Enhancing the explanatory power of usability heuristics. In Proceedings of the SIGCHI Conference on Human Factors in Computing Systems, pages 152–158, 1994.
- 23. F. D. Pociask and G. R. Morrison. Controlling split attention and redundancy in physical therapy instruction. Educational Technology Research and Development, 56:379–399, 2008.
- 24. J. Preece, Y. Rogers, and H. Sharp. Interaction Design: Beyond Human Computer Interaction. United Kingdom: John Wiley & Sons, 2002.
- 25. Costin Pribeanu. A Revised Set of Usability Heuristics for the Evaluation of Interactive Systems. Informatica Economica, 21(3/2017):31–38, 9 2017.
- 26. Alexander Renkl. Learning from worked-out examples: A study on individual differences. Cognitive Science, 21(1):1–29, 1997.
- 27. Arianne Rourke and John Sweller. The worked-example effect using ill-defined problems: Learning to recognise designers’ styles. Learning and Instruction, 19(2):185–199, 4 2009.
- 28. B. Shneiderman. Designing the user interface: Strategies for effective human-computer interaction. Boston: Addison-Wesley, Inc., 1987.
- 29. Anne Marie Singh, Nadine Marcus, and Paul Ayres. The transient information effect: Investigating the impact of segmentation on spoken and written text. Applied Cognitive Psychology, 26(6):848–853, 11 2012.
- 30. Robin Stark, Veronika Kopp, and Martin R. Fischer. Case-based learning with worked examples in complex domains: Two experimental studies in undergraduate medical education. Learning and Instruction, 21(1):22–33, 2 2011.
- 31. John Sweller. Cognitive Load Theory, volume 55. Elsevier Inc., 7 2011.
- 32. John Sweller. Cognitive Load Theory. In S. Tindall-Ford, S. Agostinho, and John Sweller, editors, Advances in Cognitive Load Theory: Rethinking Teaching. Routledge, 1st edition, 2019.
- 33. John Sweller. The Role of Evolutionary Psychology in Our Understanding of Human Cognition: Consequences for Cognitive Load Theory and Instructional Procedures. *Educational Psychology Review*, 34(4):2229–2241, 12 2022.
- 34. John Sweller. The Development of Cognitive Load Theory: Replication Crises and Incorporation of Other Theories Can Lead to Theory Expansion. *Educational Psychology Review*, 35(4), 12 2023.
- 35. John Sweller, Paul Ayres, and Slava Kalyuga. The Worked Example and Problem Completion Effects. In *Cognitive Load Theory. Explorations in the Learning Sciences, Instructional Systems and Performance Technologies*, volume 1. Springer, New York, 2011.
- 36. John Sweller and Graham A. Cooper. The Use of Worked Examples as a Substitute for Problem Solving in Learning Algebra. *Cognition and Instruction*, 2(1):59–89, 1985.
- 37. John Sweller and Susan Sweller. Natural information processing systems. *Evolutionary Psychology*, 4(1), 2006.
- 38. John Sweller, Jeroen J G Van Merrienboer, and Fred G W C Paas3. Cognitive Architecture and Instructional Design. *Educational Psychology Review*, 10(3):251–296, 1998.
- 39. John Sweller, Jeroen J.G. van Merriënboer, and Fred Paas. Cognitive Architecture and Instructional Design: 20 Years Later, 6 2019.
- 40. Huib K. Tabbers, Rob L. Martens, and Jeroen J.G. Van Merriënboer. Multimedia instructions and cognitive load theory: Effects of modality and cueing. *British Journal of Educational Psychology*, 74(1):71–81, 2004.
- 41. Rohani Ahmad Tarmizi and John Sweller. Guidance During Mathematical Problem Solving. *Journal of Educational Psychology*, 80(4):424–436, 1988.
- 42. Tamara van Gog, Fred Paas, Nadine Marcus, Paul Ayres, and John Sweller. The mirror neuron system and observational learning: implications for the effectiveness of dynamic visualizations. *Educational Psychology Review*, 21(1):21–30, 3 2009.
- 43. Mark Ward and John Sweller. Structuring Effective Worked Examples. *Cognition and Instruction*, 7(1):1–39, 1990.
- 44. Anna Wong, Wayne Leahy, Nadine Marcus, and John Sweller. Cognitive load theory, the transient information effect and e-learning. *Learning and Instruction*, 22(6):449–457, 12 2012.
- 45. Anna Wong, Nadine Marcus, Paul Ayres, Lee Smith, Graham A. Cooper, Fred Paas, and John Sweller. Instructional animations can be superior to statics when learning human motor skills. *Computers in Human Behavior*, 25(2):339–347, 3 2009.

## 7 Ripple Down Rules and Classification

Eric Martin
School of Computer Science and Engineering, UNSW Sydney
Kensington, Australia

### 7.1 RIPPLE DOWN RULES AND CLASSIFICATION

Fields and subfields often use variations on the same concepts and techniques, even if that is not always known to researchers working in their own domain of expertise. For instance, consider three subfields of Artificial intelligence: knowledge acquisition, knowledge representation, and . As particular techniques, they use Ripple Down Rules (RDR), belief revision based on preferential models, and learning in the limit with bounded mind changes, respectively. All three techniques are related to the topological concept known as the difference hierarchy. In this chapter, we show how developing a clear understanding of how RDR works, results in notions and questions on the basis of which such relationships naturally emerge.

### 7.2 PRACTICAL RIPPLE DOWN RULES

One aspect of knowledge acquisition is capturing human expertise. Recognising that it is an iterative process, that now and then requires revisions to what has been gathered so far, it is important to first design a framework that makes the exercise as easy and effective as possible. Ripple Down Rules (RDR) is such a framework, developed at the School of Computer Science and Engineering (CSE) at the University of New South Wales (UNSW) by a former Head of School, Paul Compton [1]. Adapted from [5], Figure 7.2 shows an example of an RDR tree, the key structure of the RDR framework, at a very early stage of knowledge acquisition from medical experts.

Each node of the tree comes with a set of conditions, meant to be evaluated as either true or false, and a conclusion—here, a reference to a particular diagnosis. That set is empty for the root of the tree, associated with a default conclusion. Each node has up to two children, connected to their parent either with an elif edge or with an unless edge; the latter kind of edge and only the latter leaves from the root. Decision trees only have implicit elif edges between siblings. This is illustrated in Figure 7.1 with respect to the toy example of deciding whether to play golf: if the outlook is sunny then consider the level of humidity, elif it is overcast then decide to play, elif it is rainy then consider the strength of the wind.
