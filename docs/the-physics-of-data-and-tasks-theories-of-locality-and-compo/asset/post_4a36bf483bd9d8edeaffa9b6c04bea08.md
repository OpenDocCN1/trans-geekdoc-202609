
# THE PHYSICS OF DATA AND TASKS: THEORIES OF LOCALITY AND COMPOSITIONALITY IN DEEP LEARNING

ALESSANDRO FAVERO

Presented on 26 September 2025 for the award of the degree in Physics at the École Polytechnique Fédérale de Lausanne (EPFL).

Accepted on the jury's recommendation:
- Prof. C. Theiler, jury president
- Prof. M. Wyart, thesis director
- Prof. P. Frossard, thesis director
- Prof. E. Vandenijnder, examiner
- Prof. S. Ganguli, examiner
- Prof. E. Abbe, examiner

Preprint. Official version at: epfl.ch

## ABSTRACT

Deep neural networks have achieved remarkable success, but our understanding of how they learn remains limited. These models can learn high-dimensional tasks, which is generally intractable due to the curse of dimensionality. This apparent paradox suggests that data must have an underlying structure. What is the nature of this structure? How do neural networks encode and exploit it, and how does it impact performance—for instance, how does generalization improve with the number of training examples? 

This thesis addresses these questions by studying the roles of locality and compositionality in data, and deep learning. We begin by analyzing convolutional networks in the limit of infinite width, where learning simplifies and becomes analytically tractable. Using tools from statistical physics and learning theory, we characterize their generalization abilities and show that they can overcome the curse of dimensionality if the target function is local.

We turn to more complex structures in which features are composed hierarchically, with elements at larger scales built from smaller scales. We model data using simple probabilistic models to describe such as images. Within this framework, we study how diffusion-based models compose new data by assembling features from examples. This theory predicts a phase transition in the generative process, which we confirm empirically in both image and language, providing support for the hypothesis of natural data. We further demonstrate that the sample complexity for learning these tasks grows polynomially with data, providing a mechanism by which models avoid the curse of dimensionality.

Finally, we shift our analysis from the structure of data in the input space to the structure in parameter space. Here, we investigate a novel form of compositionality where tasks can be composed. In particular, we empirically demonstrate that distinct directions in the weight space of large models are associated with task-specific areas in function space, and how this modular structure enables task editing at scale.

**KEYWORDS**: Deep learning, generalization, scaling laws, data structure, locality, compositionality, probabilistic graphical models, convolutional networks, diffusion models.

## RÉSUMÉ

Les réseaux de neurones ont connu un succès remarquable, mais notre compréhension de leur mode reste limitée. Ces modèles peuvent apprendre des tâches de haute dimension, ce qui est généralement insoluble en raison de la malédiction de la dimension. Ce paradoxe apparent suggère que les données peuvent posséder une structure sous-jacente. Quelle est la nature de cette structure ? Comment les réseaux de neurones l'encodent-ils et l'exploitent-ils, et quel est son impact aux performances—par exemple, la généralisation s'améliore-t-elle avec le nombre d'exemples ? Cette thèse aborde ces questions en étudiant les rôles de la localité et de la compositionnalité dans les données.

Nous commençons à analyser les réseaux de neurones convolutifs dans la limite d'infini. À l'aide d'outils de la physique statistique et de la théorie de l'apprentissage, nous caractérisons leurs capacités de généralisation et montrons qu'ils peuvent surmonter la malédiction de la dimension si la fonction est locale, en s'adaptant à une échelle spatiale.

Nous nous tournons vers des structures complexes auxquelles les caractéristiques sont composées hiérarchiquement, avec des éléments de grande échelle construits à partir de plus petites. Nous modélisons les données à l'aide de simples modèles probabilistes pour décrire tels que des images. Dans ce cadre, nous étudions comment les modèles génératifs par diffusion produisent de nouvelles données en assemblant des caractéristiques. Cette théorie prédit une transition de phase dans le processus génératif que nous confirmons empiriquement dans les modalités d'image et de langage, soutenant l'hypothèse d'une structure denelle naturelle. Nous démontrons que le nombre d'exemples nécessaires à l'apprentissage croît polynomialement avec la dimension des données, fournissant ainsi un mécanisme par lequel les modèles évitent la malédiction de la dimension de manière hiérarchique.

Enfin, nous explorons comment les tâches elles-mêmes peuvent être localisées et composées dans l'espace des poids du modèle. En particulier, nous montrons empiriquement que des directions distinctes dans l'espace des poids de grands entraînés sont associées à des zones sémantiques spécifiques et localisées dans l'espace des fonctions, et comment cette structure modulaire permet une arithmétique des tâches et l'édition de modèles à grande échelle.

**MOTS-CLÉS** : Apprentissage profond, généralisation, lois d'échelle, structure des données, localité, compositionnalité, modèles graphiques probabilistes, réseaux convolutifs, modèles de diffusion.

> The true sign of intelligence is not knowledge but imagination.
— Albert Einstein

## ACKNOWLEDGEMENTS

The years spent on this PhD have been a period of profound personal and academic transformation. I have had the privilege of meeting wonderful people, traveling the world, and growing in ways I had not anticipated. The achievements detailed in this thesis, and indeed any personal growth I have experienced, are by no means my merit alone. They are the result of a deeply collective endeavor, a reflection of the incredible people I have been surrounded by. This is, to me, the most beautiful way to do science.

My deepest gratitude goes first to my two PhD advisors, Prof. Mathieu Wyart and Prof. Pascal Frossard. To Mathieu, thank you for your unwavering belief in me from the very beginning. I am indebted to you for the countless hours of scientific discussion that fundamentally shaped how I think. You taught me the meaning of scientific rigor, clarity of thought, and importance of honest feedback. You showed me how to approach problems with precision without losing the underlying intuition, and you instilled in me a unique research taste for which I will always be grateful.

To Pascal, thank you for trusting me and for granting me immense freedom and independence to grow as a researcher and, later, as a mentor. Your constant support and patience, especially during my time away from UBS, were invaluable. I am grateful for your wisdom, your practical advice on navigating academia, and for always asking the right questions.

I was honored to have an exceptional committee. My sincere thanks to Prof. Surya Ganjali, Prof. Eric Vanden-Ijnder, Prof. Emmanuel Abbe, and the committee president, Prof. Christian Theiler. I could not have asked for a more distinguished and insightful group of experts in the field. It was a privilege to present my work to you, and I look forward to future scientific conversations.
