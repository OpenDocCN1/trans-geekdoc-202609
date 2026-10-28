
For presentation and pedagogical purposes, we make some simplifications in this chapter. For this reason, the presented algorithm could be considered impractical. We revisit these simplifications in the following chapters.

In Chap. 5, we focus on minimizing the training error in the presence of adversarial machines. We first discuss the potential limitation of robustness due to *gradient dissimilarity*, an artifact of *heterogeneity* in data held by the nodes. We then show that many robust aggregation rules, though they can provide the optimal breakdown point, yield a suboptimal training error under gradient dissimilarity. We present the technique of *pre-aggregation* that circumvents this shortcoming and achieves optimality.

In Chap. 6, we focus on gradient complexity in robust machine learning. Although a composition of a robust aggregation rule with pre-aggregation yields order-optimal training errors, the resulting gradient complexity can be orders of magnitude higher than a traditional (non-robust) machine learning algorithm. This could greatly discourage the use of these robustness schemes. We highlight the important role of *gradient momentum at local level* in regulating the gradient complexity, thereby rendering robust machine learning more practical.

## 1.4 Chapter Notes

In this chapter, we have briefly recalled the evolution of machine learning: from the idea of artificial intelligence [16, 25, 26] to building machines that can play cognitive games [2, 9, 12, 24] to utilizing machines in healthcare [6, 10]. Modern machine learning systems, such as ChatGPT [3], derive their power from large-scale complex models that are trained over vast amounts of data. These automated systems are critically shaping the course of modern society, with applications ranging from healthcare to military [7, 11, 15, 18, 20, 22]. There is no denying that machine learning is rapidly transforming the realm of information technology, touching almost every aspect of our lives [14]. Although these changes could significantly improve the quality of life in general and might even help us find ways to fight against emerging global issues, such as climate change [21], they should be used with a great amount of caution.

We have highlighted that the classic machine learning algorithms, especially those proposed for developing large-scale models, are not robust to the challenges prevalent in real-world scenarios, specifically the element of *corruption*. It has been shown that the effectiveness of machine learning schemes can become highly compromised, when either the training data are adulterated or when some machines malfunction during the training procedure [1, 4, 5, 8, 13, 23, 27]. Using such *poorly trained* models in public-oriented applications could have severe consequences [17, 19]. Protecting machine learning systems against corrupted data and malfunctioning machines, thereby paving the path to *safe AI*, was our key motivation in developing the *robust machine learning* methods we present in this book.

## References

- 1. Baruch M, Baruch G, Goldberg Y (2019) A little is enough: Circumventing defenses for distributed learning. In: Advances in Neural Information Processing Systems 32: Annual Conference on Neural Information Processing Systems 2019, 8–14 December 2019, Long Beach, CA, USA
- 2. Brown N, Sandholm T (2019) Superhuman AI for multiplayer poker. Science 365(6456):885–890
- 3. Brown T, Mann B, Ryder N, Subbiah M, Kaplan JD, Dhariwal P, Neelakantan A, Shyam P, Sastry G, Askell A et al (2020) Language models are few-shot learners. In: Advances in Neural Information Processing Systems, vol 33, pp 1877–1901
- 4. Cao X, Jia J, Zhang Z, Gong NZ (2022) FedRecover: recovering from poisoning attacks in federated learning using historical information. In: 2023 IEEE Symposium on Security and Privacy (SP). IEEE Computer Society, pp 326–343
- 5. Carlini N, Terzis A (2022) Poisoning and backdooring contrastive learning. In: International Conference on Learning Representations
- 6. Cuocolo R, Caruso M, Perillo T, Ugga L, Petretta M (2020) Machine learning in oncology: a clinical appraisal. Cancer Lett 481:55–62
- 7. Donepudi PK (2017) AI and machine learning in banking: a systematic literature review. Asian J Appl Sci Eng 6(3):157–162
- 8. Fang M, Cao X, Jia J, Gong N (2020) Local model poisoning attacks to Byzantine-Robust federated learning. In: 29th USENIX Security Symposium (USENIX Security 20), pp 1605–1622
- 9. Ferrucci D, Brown E, Chu-Carroll J, Fan J, Gondek D, Kalyanpur AA, Lally A, Murdock JW, Nyberg E, Prager J et al (2010) Building Watson: An overview of the DeepQA project. AI Mag 31(3):59–79
- 10. Ferrucci D, Levas A, Bagchi S, Gondek D, Mueller ET (2013) Watson: beyond jeopardy! Artif Intell 199:93–105
- 11. Hojtink M, Planqué-van Hardeveld A (2022) Machine learning and the platformization of the military: a study of Google’s machine learning platform TensorFlow. Int Polit Sociol 16(2):olab036
- 12. Hsu F.-H. (2002) Behind deep blue: building the computer that defeated the world chess champion. Princeton University Press, Princeton
- 13. Kairouz P, McMahan HB, Avent B, Bellet A, Bennis M, Bhagoji AN, Bonawitz K, Charles Z, Cormode G, Cummings R et al (2021) Advances and open problems in federated learning. Found Trends®Mach Learn 14(1–2):1–210
- 14. Kaplan A, Haenlein M (2019) Siri, Siri, in my hand: who’s the fairest in the land? On the interpretations, illustrations, and implications of artificial intelligence. Business Horizons 62(1):15–25
- 15. Leo M, Sharma S, Maddulety K (2019) Machine learning in banking risk management: a literature review. Risks 7(1):29
- 16. McCulloch WS, Pitts W (1943) A logical calculus of the ideas immanent in nervous activity. Bull Math Biophys 5(4):115–133
- 17. Nakagawa K, Moukheiber L, Celi L, Patel M, Mahmood F, Gondim D, Hogarth M, Levenson R (2023) AI in pathology: what could possibly go wrong? In: Seminars in diagnostic pathology. Elsevier, Amsterdam
- 18. Namiot D, Ilyushin E, Chizhov I (2021) Military applications of machine learning. Int J Open Inf Technol 10(1):69–76
- 19. Neri E, Coppola F, Miele V, Bibbolino C, Grassi R (2020) Artificial intelligence: who is responsible for the diagnosis? Radiol Med 125:517–521
- 20. Pati S, Baid U, Edwards B, Sheller M, Wang S.-H., Reina GA, Foley P, Gruzdev A, Karkada D, Davatzikos C et al (2022) Federated learning enables big data for rare cancer boundary detection. Nat Commun 13(1):7346
- 21. Rolnick D, Donti PL, Kaack LH, Kochanski K, Lacoste A, Sankaran K, Ross AS, Milojevic-Dupont N, Jaques N, Waldman-Brown A et al (2022) Tackling climate change with machine learning. ACM Comput Surv 55(2):1–96
- 22. Shailaja K, Seetharamulu B, Jabbar M (2018) Machine learning in healthcare: a review. In: 2018 Second International Conference on Electronics, Communication and Aerospace Technology (ICECA). IEEE, pp 910–914
- 23. Shejwalkar V, Houmansadr A (2021) Manipulating the Byzantine: optimizing model poisoning attacks and defenses for federated learning. In: NDSS
- 24. Silver D, Huang A, Maddison CJ, Guez A, Sifre L, Van Den Driessche G, Schrittwieser J, Antonoglou I, Panneershelvam V, Lanctot M et al (2016) Mastering the game of Go with deep neural networks and tree search. Nature 529(7587):484–489
- 25. Turing A (1950) Computing machinery and intelligence. Mind 59(236):433–460
- 26. Wiener N (1948) Cybernetics; or control and communication in the animal and the machine. Wiley, Hoboken
- 27. Xie C, Koyejo O, Gupta I (2019) Fall of empires: breaking byzantine-tolerant SGD by inner product manipulation. In: Proceedings of the Thirty-Fifth Conference on Uncertainty in Artificial Intelligence, UAI 2019, Tel Aviv, Israel, July 22–25, 2019, p 83

## Chapter 2
Basics of Machine Learning

Abstract Machine learning consists in designing algorithms that exploit data (sometimes called observations) in order to acquire domain knowledge and perform an automated decision-making task. Contrary to most conventional computing tasks, learning algorithms are data-dependent in the sense that they build task-specific models and improve upon them using the data fed to them. Machine learning algorithms are mainly classified into four classes: supervised learning, unsupervised learning, semi-supervised learning, and reinforcement learning. Each of these classes has its own interest and peculiarities. In this book, we focus on supervised classification to illustrate and to formalize the main concepts of robust machine learning. Most of the robustness techniques we discuss however in the book can also be applied to other machine learning classes. In this chapter, we present the fundamentals of supervised learning, through the specifics of the supervised classification task, and we review some of the standard optimization algorithms used for solving this task.

### 2.1 Supervised Classification

In supervised learning, the data (or observations) consist of input–output pairs, and the algorithm uses these pairs to build a function, a.k.a., a predictor, that maps an input to an output by identifying a pattern in the observations. This predictor can then be used to provide labels for unseen inputs. For example, as illustrated in Fig. 2.1, the predictor can take a picture as an input and tell us whether this image represents an elephant, a chicken, a mouse, or a snake.¹ When the outputs are categorical, the supervised-learning problem is also called supervised classification. We formalize this concept below and quickly go over the driving principles behind the selection of a good predictor.

¹ The animal icons we use in this figure are courtesy of the Freepick team. See the following links for the respective icons: Elephant, Chicken, Mouse and Snake.
