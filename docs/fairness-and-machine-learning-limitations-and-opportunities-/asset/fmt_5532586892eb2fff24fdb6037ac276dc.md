
A few chapters, specifically chapter 3 on classification and chapter 5 on causality, require significant mathematical prerequisites, primarily in undergraduate probability and statistics. However, the other chapters we dedicate to much broader audiences. We hope that students in multiple fields will find this book helpful in preparing for research in related areas. The book does not fit neatly into the disciplinary boundaries of any single department. As a result it gives readers an opportunity to go beyond established curricula in their primary discipline.

Since we started publishing material from this book years ago, instructors have incorporated the material into a variety of courses, at both the undergraduate and the graduate level, in different departments. Hundreds of readers have sent us tremendously helpful feedback for which we are deeply grateful.

And to those lamenting our slow progress in writing this book, we respond empathetically: That’s fair.

## Online Materials

We have created a website to accompany this textbook: [https://fairmlbook.org/](https://fairmlbook.org/). The website includes a freely accessible online version of the textbook based on an earlier draft of the manuscript. It also includes a number of exercises. And it provides links to video recordings of a number of tutorials that we have given on these topics as well as the syllabi for our classes that served as the inspiration for the textbook.

# Acknowledgments

This book wouldn’t have been possible without the profound contributions of our collaborators and the community at large.

We are grateful to our students for their active participation in pilot courses at Berkeley, Cornell, and Princeton. Thanks in particular to `Brian McInnis` and `Claudia Roberts` for lecture notes of the Cornell and Princeton courses, respectively.

Special thanks to `Katherine Yen` for editorial and technical help with the book.

`Moritz Hardt` is indebted to `Cynthia Dwork` for introducing him to the topic of this book during a formative internship in 2010.

We benefited from substantial discussions, feedback, and comments from `Rediet Abebe`, `Andrew Brunskill`, `Aylin Caliskan`, `Alex Chouldechova`, `André Cruz`, `Frances Ding`, `Michaela Hardt`, `Jake Hofman`, `Lily Hu`, `Ben Hutchinson`, `Shan Jiang`, `Sayash Kapoor`, `Lauren Kaplan`, `Niki Kilbertus`, `Been Kim`, `Kathy Kleiman`, `Jon Kleinberg`, `Issa Kohler-Hausmann`, `Mihir Kshirsagar`, `Eric Lawrence`, `Karen Levy`, `Zachary Lipton`, `Lydia T. Liu`, `John Miller`, `Smitha Milli`, `Shira Mitchell`, `Jared Moore`, `Robert Netzorg`, `Helen Nissenbaum`, `David Parkes`, `Juan Carlos Perdomo`, `Eike Willi Petersen`, `Manish Raghavan`, `Daniele Regoli`, `Ofir Reich`, `Claudia Roberts`, `Olga Russakovsky`, `Matthew J. Salganik`, `Carsten Schwemmer`, `Ludwig Schmidt`, `Andrew Selbst`, `Matthew Sun`, `Hanna Wallach`, `Angelina Wang`, `Christo Wilson`, `Annette Zimmermann`, and `Tijana Zrnic`.

`Solon Barocas` is grateful for support from the `John D. and Catherine T. MacArthur Foundation` and `Cornell Center for Social Sciences`. `Arvind Narayanan` is grateful for support from the `National Science Foundation` under grants `IIS-1763642` and `CHS-1704444`.

# 1 Introduction

Our success, happiness, and well-being are never fully of our own making. Others’ decisions can profoundly affect the course of our lives: whether to admit us to a particular school, offer us a job, or grant us a mortgage. Arbitrary, inconsistent, or faulty decision making thus raises serious concerns because it risks limiting our ability to achieve the goals that we have set for ourselves and access the opportunities for which we are qualified.

So how do we ensure that these decisions are made the right way and for the right reasons? While there is much to value in fixed rules, applied consistently, *good* decisions take available evidence into account. We expect admissions, employment, and lending decisions to rest on factors that are relevant to the outcome of interest.

Identifying details that are relevant to a decision might happen informally and without much thought: employers might observe that people who study math seem to perform particularly well in the financial industry. But they could test these observations against historical evidence by examining the degree to which a person’s major correlates with success on the job. This is the traditional work of statistics—and it promises to provide a more reliable basis for decision making by quantifying how much weight to assign certain details in our determinations.

A body of research has compared the accuracy of statistical models to the judgments of humans, even experts with years of experience. In many head-to-head comparisons on fixed tasks, data-driven decisions are more accurate than those based on intuition or expertise. As one example, a 2002 study shows that automated underwriting of loans was both more accurate and less racially disparate \[[1](#references.xhtml#ref-1)\]. These results have been welcomed as a way to ensure that the high-stakes decisions that shape our life chances are both accurate and fair.

Machine learning promises to bring greater discipline to decision making because it offers to uncover factors relevant to decision making that humans might overlook, given the complexity or subtlety of the relationships in historical evidence. Rather than starting with some intuition about the relationship between certain factors and an outcome of interest, machine learning lets us defer the question of relevance to the data themselves: which factors—among all that we have observed—bear a statistical relationship to the outcome.

Uncovering patterns in historical evidence can be even more powerful than this might seem to suggest. Breakthroughs in computer vision—specifically object recognition—reveal just how much pattern discovery can achieve. In this domain, machine learning has helped to overcome a strange fact of human cognition: while we may be able to effortlessly identify objects in a scene, we are unable to specify the full set of rules that we rely on to make these determinations. We cannot hand-code a program that exhaustively enumerates all the relevant factors that allow us to recognize objects from every possible perspective or in all their potential visual configurations. Machine learning aims to solve this problem by abandoning the attempt to teach a computer through explicit instruction in favor of a process of learning by example. By exposing the computer to many examples of images containing preidentified objects, we hope the computer will learn the patterns that reliably distinguish different objects from one another and from the environments in which they appear.

This can feel like a remarkable achievement, not only because computers can now execute complex tasks but also because the rules for deciding what appears in an image seem to emerge from the data themselves.

But there are serious risks in learning from examples. Learning is not a process of simply committing examples to memory. Instead, it involves generalizing from examples: homing in on those details that are characteristic of, say, cats in general, not just the specific cats that happen to appear in the examples. This is the process of induction: drawing general rules from specific examples—rules that effectively account for past cases, but that also apply to future, as yet unseen cases. The hope is that we’ll figure out how future cases are likely to be similar to past cases, even if they are not exactly the same.
