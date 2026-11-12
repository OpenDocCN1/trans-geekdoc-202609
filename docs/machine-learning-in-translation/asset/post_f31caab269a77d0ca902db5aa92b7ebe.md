
estimation, and other natural language processing (NLP) tasks in translation. These tasks and tools are examined in a broad translation environment, including not only MT but also other elements of a conventional computer-assisted translation (CAT) environment, thus illustrating the expansion of language technology in the translation/localization workflow. Intentionality is highlighted as the factor that differentiates humans and machines.

Chapter 4 adopts a holistic approach to MT, illustrating the expansion of language technology in the translation/localization workflow. It discusses different paradigms of machine translation, from linguistic rules to statistical models, and the basic principles behind these paradigms. It also covers some major considerations in MT deployment. Finally, the chapter proposes a framework for workflows in which MT is part of translation in a broad sense.

Chapter 5 introduces machine translation quality assessment (TQA), quality estimation, and other methodologies to help us manage risk in a ML-driven translation environment. This chapter also covers machine translation post-editing (MTPE) and other human–machine interaction in a MT-driven localization process.

Chapter 6 introduces other natural language processing technologies relevant to a continuous translation process, which a translator, linguist, or domain expert is more likely to guide and support than a computer scientist. These NLP tasks are based on specific purposes in an ML–driven translation process. From a philosophical perspective, machines do not possess intentionality, which is solely in the minds of humans.

Part III turns to Data in human and machine learning. Chapters 7 through 9 focus on the role of data in both human learning and ML processes. It proposes that a translator's unique value lies in the capability to create, manage, and leverage language data in different ML tasks in the translation process, including data from parallel and monolingual corpora, terminology, and data in other formats such as component content management system (CCMS). It discusses data relevancy, data annotation, data quality, data fairness, and data security when leveraging ML tools in translation. Maximizing the value of language data and supporting both human learning and ML requires data sharing among humans and computer platforms up front. Finally, the integration of ML in translation research and practice implies that new knowledge and skills need to be incorporated into traditional translation education.

Chapter 7 proposes the concept of translation-driven language data, whose main characteristic is comparability. The chapter draws distinctions between data, corpus, and information as concepts and between two fundamental uses of language data: human analysis and learning vs. machine analytics and learning. The chapter discusses translator–computer interaction (TCI) through language data from three perspectives: (1) data design and acquisition, (2) data annotation, and (3) language data use.

Chapter 8 adopts a definition of learning as forming a mental model and adjusting the parameters of the model. A significant characteristic of both human and machine learning is the capability to generalize new conclusions based on available observations. This chapter discusses the collective capability of ML technologies to facilitate personalized human learning and the importance of converting generic ML models to personalized tools that help humans acquire these technologies and translation-related knowledge and expertise. Examples include illustrating how ML can facilitate human learning by using vector space to visualize terminological schematic context (TSC), compiling source text-oriented comparable corpora, and building intelligent tutors.

Chapter 9 discusses how machine learning adds a new dimension to translator education. It describes the impact of machine learning and summarizes translator competences in this new context. It describes the educator’s role in two approaches to structuring learning: bottom-up, learner-centered, and top-down, educator-guided environments. It discusses the value of educators when machine learning plays a significant role in translation and concludes with a discussion of new requirements for translation curriculum design in the ML era.

The book concludes with a discussion of Human-centered machine learning in translation, drawing attention to the need to empower translators with ML knowledge, through communication with ML users, developers, and programmers, and with opportunities for continuous learning.

## Note

- 1 A neural language model is a neural network that learns to predict the next word from prior words (Jurafsky & Martin, 2020, p. 113).

Taylor & Francis
Taylor & Francis Group
http://taylorandfrancis.com

Copyright © 2023, Taylor & Francis Group. All rights reserved.

Wang, P. & Sawyer, DB 2023, Machine Learning in Translation, Taylor & Francis Group, Milton. Available from: ProQuest Ebook Central. [6 June 2023].
Created from rmit on 2023-06-06 12:02:29.

## PART I

## Human and machine approaches to translation

Taylor & Francis
Taylor & Francis Group
http://taylorandfrancis.com

## CONVERGENCE OF TWO APPROACHES TO TRANSLATION

### KEY CONCEPTS

- The traditional human approach to translation is converging with machine learning from the linguistic, communicative, and mathematical perspectives.
- In machine learning and neural network language models, words are represented as real value vectors, which offer a new perspective on the nature of translation.
- Distributed representations in a neural network language model provide a feasible solution to describe sense-component relationships and can simulate the inner workings of meaning.

### 1.1 Introduction

Translation, first and foremost, is a human activity. It originates out of the necessity of communication. When examining the history of translation, three characteristics stand out. The first is that translation practice is the foundation of translation studies as a discipline, which has a very short but lively history (Gentzler, 2014, p. 14; Holmes, 1972/2004). Although philosophical writing about translation stretches back to antiquity, the focus tends to be on practice, with for example Horace and Cicero, and other poets and philosophers in the Western tradition, discussing aspects of word-for-word and sense-for-sense translation in the first century BC (Ghanooni, 2012, p. 77). The second is the interdisciplinary nature of translation studies, widely recognized and discussed in the field. The third is that there are technology tools and computer applications associated with computational linguistics, computer engineering, and software engineering, among other areas, that have contributed to the maturation of translation as a practice and an autonomous discipline (see Ożbot, 2015).

These characteristics lay out foundational considerations about the nature of translation:

- 1 At its core, translation is a human practice, with the facilitation of communication as its basic function.
- 2 Humans are creative when using language and translating, and although many disciplines can contribute to the study of translation, none can address exclusively and entirely the problem of translation, making them individually unsuitable to address translation practice as a whole.
- 3 The study of language and the study of translation are inextricably linked – many epistemological translation constructs originate from the study of language and application of linguistic constructs to translation.
- 4 While technology tools and computer applications provide a means to do translations, they also offer a new dimension when thinking about the nature of translation; they are thus both a methodology and a theoretical framework.

These considerations lead us to think of a well-known, over 2,500 year-old quotation attributed to Confucius: *There are three methods to gaining wisdom. The first is reflection, which is the highest. The second is imitation, which is the easiest. The third is experience, which is the bitterest.* To some degree, these three methods describe aspects of translation practice over the centuries, except that with the rise of computer science in modern times, translators are now able to reflect on translation practice and gain translation experience not only by using their own minds but also electronic resources. These developments have led to more diverse participants becoming involved in translation-related activities, including technology experts who focus on developing computer applications and now feature prominently. These applications attempt to simulate human processes by using machines to practice translation. They are augmenting, magnifying, and scaling up human knowledge and capability in this area. The rise of technological power in translation leads us to rethink the traditional roles of translators and linguists. In this new collaborative relationship between humans and machines, translators are also domain experts and pioneers in new ways of practicing translation. They support the development of computer applications produced by technical experts, while simultaneously being empowered by these applications and, quite importantly, finding new opportunities to reflect on their translation experience.

The rise of this technology dimension allows us to identify two fundamental approaches to translation. One is linguistic and represents humans’ intuitive and empirical reflection on translation practice from the interdisciplinary perspectives of translation studies. The other is mathematical and represents computer processing of linguistic information and translation data, which is fundamentally based on numbers, rather than texts. The focus of this book is on the relationship between machine learning and translation, which in theory and practice should not be
