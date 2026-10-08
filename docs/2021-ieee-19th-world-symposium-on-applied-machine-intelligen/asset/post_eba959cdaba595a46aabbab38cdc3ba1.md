
# Software Modernization Using Machine Learning Techniques

1st Norbert Somogyi
Department of Automation and Applied Informatics
Budapest University of Technology and Economics
Budapest, Hungary
somogyi@edu.bme.hu

2nd Gábor Kövesdán
Department of Automation and Applied Informatics
Budapest University of Technology and Economics
Budapest, Hungary
kovesdan@vik.bme.hu

**Abstract**—As software engineering techniques and practices continually evolve, programs created with an older technology stack are often referred to as legacy code. Naturally, the needs to make use of new and more effective technologies, making the legacy code easier to maintain and operate, become paramount. Many approaches have been proposed and proposed to reduce the cost of implementation by semi-automatically translating legacy systems into a more modern, architecture. However, the results of these efforts are often limited in scope and quality.

**Index Terms**—code modernization, analysis, machine learning

## I. INTRODUCTION

The maintenance of outdated software always requires great effort from developers. As software grows and time passes, it becomes harder and harder to maintain them. Over time, software engineering techniques constantly advance. New practices and paradigms may benefit to application development, which could be useful in legacy systems [1]. When one naturally needs to re-implement these systems using new tools, a more modern approach arises, but this is extremely difficult in practice. Firstly, the new implementation must be substantially equivalent to the former program.

Project no. FIEK_16-1-2016-0007 has been implemented with the support of the National Fund of Research, Development of Hungary, funded under the Center for Higher Education and Industrial Operation - Research infrastructure development (FIEK_16) funding scheme.

modern re-implementation is a time consuming and costly process in itself.

In order to make these difficulties more manageable, as assisted conversion of legacy code to a more advantageous environment is desirable. Depending on the specific software being translated, for example, many tools focus on architecture transformation, which is one of the most common and the necessary shift between the two languages. Transforming paradigms into object-oriented or functional paradigms is a common task. However, the linguistic differences between the source and target languages cause some structures of the legacy may not be supported in the target language. In some cases, elimination of such structures is required.

In this paper, we present the application of machine learning in software modernization. We present a study of a classification problem that arises during the transformation of legacy code. We aim to solve this problem using first static analysis. Finally, we compare the results to see how much machine learning can improve over classic static analysis. Our AI-based approach is fully automatic and highly precise, which, as we see, is a rare but desirable outcome.

The paper is structured as follows. Section 2 presents the difficulties of maintenance and analysis by problems and solutions proposed in relation. Section 3, we explore the methods of automation and precision. In Section 4, we present the case study of pointer conversion. In Section 5 we present the solution to the problem using machine learning analysis. Finally, Section 6 concludes the paper and highlights some must be in the target language. For example, C has no-pointer arithmetic that cannot be converted to Java, the latter does not have an equivalent convert.

The maintenance of legacy software has always been difficulty. Researchers have made an effort to determine the difficulties of maintaining software. Harrington and Walton [2] assert that the maintenance of legacy software is significant for many organizations. A three-year period of study found that in cases maintaining these systems accounted for the best of all costs. They also determined that the most complex systems are not the most costly, thus invalidating LOC (lines of code) as an indicator for maintenance.

In other cases, static code analysis does not prove to provide a reliable, fully automatic solution. In these scenarios, one has to a trade-off between attention and error-free generation. As mentioned before, this often manifests as a multiple-choice problem, where tone has to choose the correct approach to transforming source code. For example, the code developed by Systems [9] is fully automatic translation. However, in some cases, the generated code does not feel as natural as something a programmer might have created from scratch. For example, transforming to Java is a challenge when transforming C programs.

## II. RELATED WORK

Huijgens, Duversen and Van Jong [3] delve into the legacy software maintenance of various cases of studies. The authors give a description of a case in which an iterative, agile approach to a legacy system set stakeholders deemed the system being of questionable quality. They also identified 7 crucial factors that contribute to successful maintenance of legacy systems. The factors are listed in Table 1. Thus, we can say that agile methods in general may improve the successful management of these systems.

Sneed and Snowbo [5] analyze the complexity of object-oriented systems. They conclude that even such systems may be considered "at least formally, they are properly modeled and the system is supported by tools." The authors also claim that it may not be enough to actually reverse engineer systems, but enough to perform maintenance tasks. They claim that architectural comprehension would require the use of artificial intelligence.

They transform them by emulating pointer functions using generated source classes. However, fully automatic, this is the code maintaining primary-functionality and the code made so. On the other hand, one may come up with other ways of tackling that problem that yield more results. For example, using static code analysis, not is enable to estimate how a system is and convert it accordingly. It is clear that static analysis can lead the transformation.

There exist other approaches to help software version control systems contain useful information that can be used for software maintenance. They introduce it, which can be used, with developer activities. Visualizing information helps developers to learn understand the system and may improve maintainability and the reverse engineering process.

On the other hand, automatic transformation affects the goal of the transformation. For example, if the transformation is to create an object-orient design of source code, then it is only so much that can be recovered in a fully automatic way, the tools have enabled the transformation from PL/I code automatically. However, the resulting design has its flaws and does not feel like something a programmer would have wanted. Nevertheless, if one wants to keep the process fully-automatic, what is

Software maintenance and application of machine learning techniques in order to analyze the history of past maintenance of legacy systems. The authors conclude that by analyzing records of past maintenance one may use machine learning to predict if change in source file may contain change in another source. For example, it may be used to detect potential bugs and improve legacy software maintenance in general.

Recently, several successful works are in the automatic way. This may include user interaction, as offering the user to choose the code correctly or identify edit the generated code.

Reaching as high possible remains the goal of software modernization. There are certain limitations and researches suggest that complete automatic transformation cannot be fully achieved. We for and Verhof [88] have highlighted the difficulties of automated source code modernization that are beyond syntactic translation. As mentioned before, the target language may look like some source language's features

Another popular approach is required additional information-s code, or in the form of regular expressions and diagrams that describe the system in some point of view [11] [12].

In conclusion, maintaining legacy code is a complex and very part of software engineering. In order to reduce the risk, transforming legacy systems into another desirable solution. Solutions should strive to make these transformations as automatic as possible. However, fully automatic conversion has its limits and is often unreliable. One has then to make a trade-off better.
