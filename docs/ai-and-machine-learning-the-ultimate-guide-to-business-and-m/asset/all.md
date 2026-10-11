 

 

 

JAMIE DAVISON

 

 

 

# AI AND MACHINE LEARNING: THE ULTIMATE GUIDE TO BUSINESS AND MARKETING

 

 

Knowledge Representation + Solution Search Methods 

 

 

 

 

 

 

 

 

 

Contents

[AI AND MACHINE LEARNING: THE ULTIMATE GUIDE TO BUSINESS AND MARKETING](#part0000.xhtml#_Toc106280996)

[INTRODUCTION](#part0002.xhtml#_Toc106280997)

[CHAPTER 1.](#part0003.xhtml#_Toc106280998)

[APPLIED ARTIFICIAL INTELLIGENCE SYSTEMS](#part0003.xhtml#_Toc106280999)

[1.1. AI APPS AT A GLANCE](#part0003.xhtml#_Toc106281000)

[1.2. PLACE OF REPRESENTATION OF KNOWLEDGE IN ARTIFICIAL INTELLIGENCE](#part0003.xhtml#_Toc106281001)

[1.3. HISTORY OF ARTIFICIAL INTELLIGENCE](#part0003.xhtml#_Toc106281002)

[1.4. CLASSIFICATIONS OF APPLIED ARTIFICIAL INTELLIGENCE SYSTEMS](#part0003.xhtml#_Toc106281003)

[(3) sort { x i }   i , j ( i < j  x i < xj\_ \_ )](#part0003.xhtml#_Toc106281004)

[CONCLUSIONS ON CHAPTER 1](#part0003.xhtml#_Toc106281005)

[CHAPTER 2. KNOWLEDGE REPRESENTATION THROUGH PRODUCT SYSTEMS](#part0004.xhtml#_Toc106281006)

[2.1. PRODUCT SYSTEMS](#part0004.xhtml#_Toc106281007)

[2.2. MANAGEMENT STRATEGIES](#part0004.xhtml#_Toc106281008)

[2.3. SPECIAL PRODUCT SYSTEMS](#part0004.xhtml#_Toc106281009)

[2.3.1 Reverse Production Systems](#part0004.xhtml#_Toc106281010)

[CONCLUSIONS ON CHAPTER 2](#part0004.xhtml#_Toc106281011)

[CHAPTER 3.](#part0005.xhtml#_Toc106281012)

[SOLUTION ALGORITHMS](#part0005.xhtml#_Toc106281013)

[3.1. HEURISTIC SEARCH](#part0005.xhtml#_Toc106281014)

[3.2. PROPERTIES OF ALGORITHM A\*](#part0005.xhtml#_Toc106281015)

[3.3. SEARCH IN GRAPHICS AND/OR](#part0005.xhtml#_Toc106281016)

[3.4. SEARCH ON PLAY TREES](#part0005.xhtml#_Toc106281017)

[CONCLUSIONS ON CHAPTER 3](#part0005.xhtml#_Toc106281018)

[CHAPTER 4](#part0005.xhtml#_Toc106281019)

[4.1. METHOD OF DECISIONS](#part0005.xhtml#_Toc106281020)

[4.2. Strategies for seeking refutation through the method of resolutions](#part0005.xhtml#_Toc106281021)

[4.3. GET RESULT](#part0005.xhtml#_Toc106281022)

[4.4. RULES-BASED DEDUCTION SYSTEMS](#part0005.xhtml#_Toc106281023)

[CONCLUSIONS ON CHAPTER 4](#part0005.xhtml#_Toc106281024)

[CONCLUSION](#part0005.xhtml#_Toc106281025)

## INTRODUCTION

You could call this book "Artificial Intelligence = Knowledge Representation + Solution Search Methods". The allusion to Niklaus Wirth's book Algorithms + Data Structures = Programs \[1\] is intentional. Because of our upbringing, accumulated experience, and innate preferences, we sincerely adhere to the ideology of pioneers and founders like Wirth and others, we often quote them and retell them a lot.

The choice of material for the handbook is quite traditional, one might say classic, but the manner of presentation is entirely that of the author. First of all, we put applied aspects first, i.e. solving meaningful problems on the computer using methods of artificial intelligence, and as an answer to the question "can a machine think?". dismiss with a laugh. Theory without practice strikes us as boring scholasticism, and we avoid it. Second, we believe that studying the ways of representing "human" knowledge in a computer is currently much more relevant than improving "machine" algorithms for finding solutions, which have been prioritized for the past half-century. That is why we pay the greatest attention to the representation of knowledge. Third, we prefer explanations through examples and short programs to the all-too-dominant scientific imagery in this area. We believe that presenting the text of a program that solves a problem is often more convincing than introducing numbered definitions and proving "mathematical" theorems.

The material of the book focuses on the answer to the question: how to express a person's knowledge and skills in the form of a program for a computer. Before answering this technical question, it is appropriate to answer the ideological question: Why? Why represent knowledge in a computer? Our answer is simple: recently it has become inexpensive. Also, it's quite difficult, so it's just extremely interesting.

Current trends in the use of computers are characterized by the increasing importance of artificial intelligence (AI) methods in software. You could say it's a continuous process.

"Intellectualization of Computers" [\[1\]](#part0005.xhtml#_ftn1). We have in mind the following undoubted trend: computers were "big calculating machines" at the beginning of their development, and now the root calculator in the word computer is already an anachronism. A modern computer is an information machine that processes knowledge presented in the form of data. This trend is represented by the histogram for Error! Source not found. , in which we showed the relationship between the computational resources used for technical computation and for knowledge processing today and half a century ago. Engineering computing is a collective term for applications such as rocket flight calculations, payroll, etc., and knowledge processing is Internet information retrieval, telecommunications, etc. [\[2\]](#part0005.xhtml#_ftn2)Note that the numeric values of the percentages and the scale in this figure are rather arbitrary. In fact, the computing power available to mankind has increased more than 10 10 times in half a century, rather than four times as in Number. The growth rate of computing resources is beyond our imagination; mankind has never experienced anything like this before. An ever-increasing portion of this rapidly growing power is being expended on knowledge processing!

![](Images/image00324.jpeg)

 

Rice. 0.1 Reallocation of computing resources over time

From the very beginning, the direction of artificial intelligence in computer science has aroused great, even unhealthy interest. Unscrupulous journalists, greedy for sensations, exaggerated the timid offspring of new ideas and raised unreasonably high public expectations, and when the first theoretical results did not justify inflated expectations, the same journalists took part in booing the ideas of artificial intelligence. But in the 21st century the situation has changed. Recently, the results obtained in this direction have outgrown the framework of academic experimental developments and have begun to be applied in practical applications. Artificial intelligence systems have meaningful uses in real life, from medical diagnostics to spacecraft control; this can be treated however you like, but it is impossible to deny. For this reason, the courses "Methods of Knowledge Processing", "Applied Artificial Intelligence" etc. have become practically obligatory in the curricula for the training of computer scientists.

Applied mathematics engineers and computer scientists working in science-intensive application areas must master the basic, well-established methods for solving enumeration problems developed in artificial intelligence research.

It should be emphasized that the essential formalisms of these methods for knowledge transfer in computers play a decisive role for the practical applicability of methods for solving enumeration problems. Methods of knowledge representation are therefore the core of the direction of artificial intelligence. This core, indispensable for both novice and experienced engineers, is the subject of the book.

We expect students taking this course to achieve the following outcomes.

1.               Knowledge of the most important methods for solving algorithmically complex problems; knowledge of the comparative advantages and disadvantages of these methods; Knowledge of the basic principles of the most well-known methods of knowledge representation: production rules, predicate calculus formulas, semantic networks.

2.               The ability to choose the appropriate way of representing knowledge for a given task in simple cases; the ability to assess the appropriateness of applying one or another method of finding a solution to a particular problem.

3.               Mastery of basic concepts from the field of artificial intelligence and knowledge representation; the ability to study other methods of artificial intelligence in the literature; the ability to evaluate and use a specific applied artificial intelligence system.

Artificial intelligence methods are developing and changing very quickly today, and it is impossible to give ready-made recipes for all cases of AI application. Instead, the book gives a general overview of the basic principles of artificial intelligence, identifying the most common ways of representing knowledge in a computer.

# CHAPTER 1.

#  APPLIED ARTIFICIAL INTELLIGENCE SYSTEMS

Researchers have long been concerned with the problem of human intelligence, although attempts to structure this phenomenon of the psyche, or at least to approximate more or less rigorous definitions of phenomena and processes that implement human intelligence, are not always productive. The authors are not experts in brain physiology or psychology, nor will they "play" in the field of classical philosophy. Nevertheless (or rather "to support the position") we allow ourselves a few digressions and quotations that illustrate the situation in the areas mentioned.

Today it is generally recognized in psychology that there is a certain general intelligence as a universal mental cognitive ability that can be based on a genetically determined property of the nervous system to process information with a certain pragmatism, speed and accuracy. It is believed that many types of human mental activities such as programming, mathematics, lecturing or reading such books require intelligence.

Unfortunately, the understanding of what each of us carries on our skulls, by and large, can hardly be considered complete enough. If we talk about the structure of the brain as a carrier of intelligence, then it is known that the forming elements are cells of a special type - neurons. It has been proven that at least one of the forms of neuron interaction is realized electrochemically, but the question of whether this form is the only one remains open. The current situation is reminiscent of a hypothetical Cro-Magnon attempt to understand how a personal computer works and what it can do. But what can one say about the brain if we can't yet fully understand the mechanics of walking on two limbs.

We see that the term "intelligence" for a person is defined indirectly, through the specialty, according to some outcomes of the activity, and does not directly indicate what this aspect of the psyche is and how it is implemented. Existing definitions found in encyclopedic publications usually give an interpretation using synonymy and recursion. For example, the encyclopedic dictionary gives the following brief definition.

Intelligence (from lat. intellectus - knowledge, understanding, reason) - the ability to think, rational knowledge.

The explanatory psychological lexicon is close, but differs more precisely in the definition.

Intelligence (from lat. intellectus - understanding, cognition) - the ability to carry out the process of cognition and effectively solve problems, especially when coping with a new set of life problems.

In other words, definitions do not define anything, but can sometimes stimulate the right associations, while the term "intelligence" is very vague and not sufficient enough. In particular, it is impossible to understand the nature of intuition , the mechanism of belief , the nature of other irrational relationships 

(love, dislike) and so on.

The word "intelligence" itself didn't quite legally find its way into the term "artificial intelligence". The fact is that the originally original term artificial intelligence (see paragraph 0) has a much softer meaning. The word intelligence still means a quick wit rather than a thoughtful mind, as a basic human quality. But it is difficult to offer another translation into Russian, and it is already too late, so let's use the existing translation and give it the following meaning.

The subject of this book is applied artificial intelligence (AI), and here we are talking about practical and useful projects, avoiding the Plato-Diogenes “naked tail” style [\[3\]](#part0005.xhtml#_ftn3). The concept of AI is consistent with the concept of natural intelligence, but actually has little to do with the latter. It is important to understand that AI is not a model of human thinking [\[4\]](#part0005.xhtml#_ftn4), just as rubber, for example, is not a chemical model of rubber, even though it shares a number of similar physical properties. In fact, an artificial intelligence program uses some algorithms that are also inherent in human thinking (after all, every program is written by humans). But in real life, a person will solve the same problem differently than the program (performing different operations, using different algorithms, using the structures of the psyche, which have not yet been sufficiently studied and therefore cannot be translated into mathematical formulas and program code). The frontal approach - representing "human" algorithms in "machine" language is ineffective, as we shall see later. In other words, if we classify a task as intellectual, then every solution, by our definition , indicates some kind of intelligence. If the solution is obtained programmatically, then this program contains elements of intelligence.

A program that can solve problems in a subject traditionally classified as intellectual is called 5 artificial intelligence. Application system with elements

Another definition: An applied system with AI elements is a program whose algorithm cannot (yet!) be found in a university textbook. For example, in the early days of programming, programs that could create other programs (the first compilers) were considered "intelligent". Modern compilers are not considered intelligent programs, although they "know" much more about programming and use very sophisticated algorithms to solve compilation and optimization problems. Other examples can be cited. In each individual case, a concretely applied AI system is the know-how of the creators of such software, but each new idea in a specific subject area significantly advances the development of artificial intelligence systems in general. At the same time, as development progresses, the traditions of assigning subject areas to the intellectual sphere and assessing the degree of “intelligence” of many tasks are also changing. For example, the calculation of the structure of the Eiffel Tower at the end of the 19th century required a lot of work, remarkable intelligence and ingenuity, and now such a calculation can be performed by an ordinary designer using a ready-made software package quickly, reliably and without much mental effort. Experience and intelligence of designers, extensive knowledge of

                                                          

5 We have included the cautious word "Elements" in our definition to emphasize that the program solves some problems in a specific area and does not claim to be a universal "mind faculty, rational cognition". Less cautious or more arrogant authors use the term "applied artificial intelligence systems". We also use this term, for example, in the title of the first chapter, but choose to understand it in a cautious and minimal sense.

Mechanics, strength of materials and other engineering disciplines are largely accumulated in modern design packages. Such a package undoubtedly shows intelligent behavior, but we do not consider it an applied AI system, since all calculations in the design package are performed according to known, predefined, unique algorithms.

In order to support the above theses and to clarify the main definition of an applied system with AI elements, we consider some of the topic areas typical of artificial intelligence applications.

### 1.1. AI APPS AT A GLANCE

Some typical applications with AI elements are:

\-                     natural language understanding and machine translation;

\-                     intelligent databases and question-answer systems;

\-                     expert systems and automatic theorem proving; - Planning robot actions and pattern recognition; - mind games.

This list is neither complete nor orthogonal. This is just a selection of our favorite examples.

#### 1.1.1. Natural language understanding and machine translation

The process of understanding natural language is the process of transferring knowledge from one native speaker to another.

For all its apparent simplicity and familiarity, this process is extremely complex. This implies the existence of a common domain of knowledge for both partners and agreed mechanisms for representing knowledge in the form of data, as well as the existence of an inverse mechanism for extracting knowledge from data.

The computer implementation of the natural language understanding process requires powerful computational resources controlled by non-trivial (intelligent) software systems. Let's see what's the problem here. Suppose we have two intelligent agents, let them be human first. The first is the source of knowledge, let's call it A, and the second is the receiver of knowledge, let's call it B. Two mechanisms are involved in the process of understanding. First, A has an algorithm that allows you to turn hypothetical knowledge into data, a signal (text, speech, or other forms of natural language expression [\[5\]](#part0005.xhtml#_ftn5)) —a knowledge representation mechanism . Second, B has a mechanism that allows you to turn the received signal back into knowledge - the extraction (knowledge) mechanism . If we accept that these mechanisms are implemented by algorithms [\[6\]](#part0005.xhtml#_ftn6), then it is clear that each of them has a domain and a range of values, an input and an output. Understanding occurs when the output of the knowledge representation algorithm and the input of the knowledge extraction algorithm overlap at least in a common interpretation; and full understanding is achieved when these realms coincide.

Let's give some examples. Let us, the author, be Agent A and you, dear reader , Agent B. The next sentence: "ovelan avarps her ilasipaz otsorp ym" will most likely confuse and misunderstand you at first moment. Here Agent A uses a non-standard method of representing knowledge, making it difficult for Agent B to extract knowledge . Another example. If A uses a language that B doesn't speak (let's say if the text of this paragraph was read to you in Chinese by a Chinese who knows Russian, if you don't know Chinese), then this is what happens: the knowledge representation mechanism works, the Mechanism extraction works, but proper understanding does not occur.

Russian-speaking agent B could evaluate the musicality of the language, the unusualness of sound combinations ... and in the end come to the conclusion that he, agent B , nothing (!) there is an empty general interpretation. And here is an example of an "orthogonal [\[7\]](#part0005.xhtml#_ftn7)" general interpretation. A Russian girl asks her boyfriend (Bulgarian): Do you love me? - In response, he shakes his head (from shoulder to shoulder). - The girl is crying with sorrow when she should be jumping with happiness! – The fact is that among the Bulgarians, our affirmative nod is a gesture of denial, and shaking our heads from side to side means affirmation.

It is enough for a sage to say a word for another sage to understand. In other words, for sages, the total amount of data transferred can be significantly less than for average people, due to more powerful knowledge representation and extraction mechanisms.

A common interpretation is a set of semantic rules that are interpreted equally by both sides and that connect linguistic constructions with their semantic load.

Now let's turn to computers. In computers, knowledge representation mechanisms and knowledge retrieval are trivial, understanding is reduced to data transfer. Thus, when computers are linked by a communication channel and data formats are agreed upon, then understanding is easy to achieve, otherwise understanding cannot be achieved in any way. The critical case that is the focus of our attention is the mutual understanding of humans and computers. There are two fundamentally different ways of human communication with a computer. The first of these is when a person is able to understand a computer. This is not the merit of a computer, but the ability of a person that everyone around them calls a programmer. The second is when a computer can understand a person. Such a computer must contain elements of AI. Since intelligence, even artificial intelligence, is difficult to fit into the hardware of a conventional computer, it is clear that understanding must be provided in software. And such programs have been created for a relatively long time, although all of them, without exception, are very, very limited in understanding natural language or even a more or less broad fragment of language.\\

 

 

![](Images/image00325.jpeg)

   

 

  .one. General context of understanding

One of the first applied AI systems that understood natural language was the ELIZA program, developed by J. Weizenbaum in 1966.

More recently, Terry Winograd wrote the book The Natural Language Understanding Program describing the ELIZA program \[2\]. The structure of the ELIZA program was extremely simple, containing only a few dozen heuristic rules designed to recognize grammatical structures (by simple pattern matching) and convert incoming questions into "natural" answers. As a result, this program was able to conduct a completely plausible dialogue, often answering a question with a question at the same time. An example of a dialogue with the ELIZA program:

— ELIZA, you are a computer program.

Why do you think I'm a computer program?

"Because Weizenbaum put you together.

“Tell me about Weizenbaum.

Despite its simplicity, this program has applications in psychotherapy. The psychotherapist's conversation with the patient can take quite a long time before the therapeutic effect occurs. ELIZA successfully simulated a dialogue with a Rogerian psychologist for many hours (the essence of this method is that the therapist listens to the patient and asks guiding questions, thereby improving the mental state of the latter ... or not improving ). Many patients remarked that these sessions were extremely useful to them and refused to believe that a computer program was speaking to them and not a professional human psychologist.

Weizenbaum himself, shocked by the behavior of his descendants, soon came to the conclusion that "the main ideology of the development of artificial intelligence - artificial intelligence - is immoral". Joseph Weizenbaum (1923-2008) is a well-known figure in the field of artificial intelligence, Professor Emeritus at MIT (Massachusetts Institute of Technology). Founder of Computer Professionals for Social Responsibility. He earned a reputation as a dissident and heretic among computer scientists for his views on the responsibility of programmers to humanity. "There are tasks that shouldn't be left to computers, whether computers can be made for them or not." 

Machine translation is a particular refinement of the problem of understanding natural language. "Special" is primarily determined by the type of information exchange - a monologue instead of a dialogue.

Systems for automatically translating texts from one natural language to another form an important class of software systems with elements of artificial intelligence.

Translating from one natural language to another is undoubtedly an intellectual task. Automated machine translation has attracted the attention of researchers almost earlier than other fields due to the obvious practical relevance of this task.

Importantly, as in other cases of AI, a number of categories of increasing complexity stand out in the class of machine translation systems:

\-                     electronic dictionary;

\-                     Interlinear of technical texts; - literary translation of poems; - Simultaneous translation of speech.

It is clear that these problems cannot be solved uniformly, which means that their solutions appear at different times and rely on different technologies.

For each new area of AI application, the same characteristic pattern can be observed (Fig. Error! The text of the specified style is missing in the document. .2 ), which we will illustrate using the example of the history of the development of machine translation. After the emergence of a new idea, increased interest in it appears, inflated expectations arise, users are waiting for a miracle. But the miracle does not happen - AI methods are tedious, complex and their development requires considerable natural intelligence. Disillusionment sets in, the reorientation leaves the sphere of hectic interest and is sometimes even unreasonably hindered. If the idea was fruitful, then despite the decline in media interest, the underlying painstaking work in academic circles continues and after a while (not immediately!) begins to yield practical results. Interest reappears, but no longer idle, but factual and justified.

![](Images/image00326.jpeg)

 

  .2. The history of the popularity of machine translation

In March 1947, Warren Weaver (1894-1978), Director of Science at the Rockefeller Foundation, in correspondence with Andrew D. Booth and Norbert Wiener, first formulated the concept of machine translation, which was later (1949) further developed in his memorandum addressed to the Fund .

In 1952 the first conference on machine translation was held at the Massachusetts Institute of Technology and in 1954 at the Massachusetts Institute of Technology

first machine translation system, IBM Mark II, developed by IBM in conjunction with Georgetown University, was unveiled in New York (this event went down in history as the "Georgetown Experiment").               A very limited program was presented (it had a dictionary of 250 units and 6 rules of grammar), translated into English from Russian. After that, such developments spread to Italy, France, England, Japan, and an international professional journal was also created.

In 1959, the philosopher Yohoshua Bar-Hillel argued that high-quality, fully automatic machine translation was, in principle, impossible to achieve. This achievement had the most unfavorable impact on the development of machine translation in the United States. A sharp decline in 1966 was associated with a report by ALPAC (Automatic Language Processing Advisory Committee) specially established by the US National Academy of Sciences. The commission came to the conclusion that machine translation is unprofitable: the ratio of the cost and quality of machine translation was clearly not in favor of the latter, and there were enough human resources for the translation of technical and scientific texts. Therefore, the Ministry of Defense decided to stop funding such projects. The topic was no longer fashionable, and only qualified enthusiasts and professionals continued the work.

With the development of computer technology in the late 1970s (the advent of microcomputers, the development of networks, the increase in storage resources), machine translation entered the renaissance. At the same time, the focus has shifted somewhat: the researchers have now set themselves the goal of developing "realistic" machine translation systems in which humans are involved in various phases of the translation process. As a result, the first industrial machine translation systems for mass use came onto the market in the 1980s.

In 1990, when machine translation systems again became one of the priority areas for the development of the computer industry, reaching a new qualitative level after a difficult period of rethinking and mutual integration, Larry Childs proposed their classification. He divided all "electronic translators" into three groups:

1.               FAMT (Fully Automated Machine Translation) are tools for fully automated machine translation.

Input Text  Text Analysis / Synthesis  Output Text

2.               HAMT (Human-Assisted Machine Translation) is an application for automated machine translation of texts, performed with the participation of a human. Input Text  Editor  Text Analysis / Synthesis  

Editor  Output text

3.               MAHT (Machine-Assisted Human Translation) are tools for performing human translations with the help of a computer.

Input Text  Translator  Interlinear  Editor  

output text

However, real-life practice shows that the functioning of all machine translation systems that exist today more or less requires the involvement of a human editor.

Conceptually, the machine translation system is built as follows (Fig. Error! The text of the specified style is missing from the document. .3 , left): First, the text in the source language is analyzed, that is, the data is interpreted in order to “understand the meaning” , and then the understood meaning is presented in the form of text in the target language. Ideally, the analysis is performed "to the point of complete comprehension", when the entire meaning of the source text is expressed in a hypothetical universal metalanguage. Traditionally, this universal metalanguage is called interlingua. It should be noted that the ideal has not yet been reached. Modern machine translation systems have a three-layer architecture (Fig.

Mistake! The text of the specified style does not exist in the document. .3 , right). First, the input language is analyzed until a certain level of understanding is reached, and this understanding is expressed in the construction of various structures over the source text, often specific to a particular language. Then, using heuristic algorithms, the partially understood structures of one language are transformed into partially understood structures of another language. The set of these algorithms is traditionally called transfer (from English transfer). Transmission rules are large, using huge information resources and very sophisticated algorithms. Finally, the text is synthesized in the target language based on the transferred structures of the target language (they are not necessarily isomorphic to the structures of the source language!). Of course, the transfer phase is the most complex, important and knowledge-intensive.

 

 

  .3 Structure of the machine translation system

But the dreams with which mankind embraced machine translation half a century ago remain largely dreams - high-quality ("artistic") translation of texts on the most diverse subjects is still unattainable. What is undisputed, however, is the acceleration of the translator's work and the improvement in quality when using machine translation systems.

With the advent of more and more new algorithms, techniques and software solutions aimed at computer translation of textual information, reliable facts are that such systems have a number of advantages over traditional ones.

handmade translation:

\-                     high speed of translation (the use of machine translation can significantly reduce the time required to translate large amounts of text, by 50-70% according to modern estimates);

\-                     Reduction of translation costs (with the help of machine translation you can save on the costs of the services of professional translators, and when translating “simple” texts you can refuse them altogether);

\-                     Confidentiality of the information to be translated (the involvement of a computer in the processing of confidential documents guarantees the non-disclosure of their content to a much greater extent than the involvement of a translator);

\-                     Universalization of the translation process (even the most qualified translator, as a rule, specializes in certain areas of knowledge and subject areas, while MT systems are quite universal and their work depends only on the necessary settings - connection of the necessary electronic dictionaries, etc.).

There are currently many commercial machine translation projects: Systran, IBM, L&H (Lernout & Hauspie), Language Engineering Corporation, Atril, Trados, Caterpillar Co., LingoWare. In Russia, a group led by Prof. RG Piotrovsky (Russian State Pedagogical University named after Herzen, St. Petersburg). Now the automatic translator developed by PROMT (PROgrammer's Machine Translation) has received the well-deserved recognition that meets the expectations of most users.

#### 1.1.2. Intelligent databases and question-answer systems

At the beginning of the use of computers, data storage formats and means of their manipulation were invented by programmers individually for each case. This is inconvenient and inefficient, and unified data storage methods (data models) were soon proposed and unified data access systems (database management systems - DBMS) were developed. Looking at the concept of a database (DB) from the most general point of view, it can be stated that the database supports three main groups of operations: entering data into the database, searching for data in the database and extracting data from the database, and the previously entered data is retrieved [\[8\]](#part0005.xhtml#_ftn8). Several ideas have been proposed and used that do not have this limitation. One of them is the idea of an intelligent database.

An intelligent database provides an efficient way to store, search, and retrieve more facts than originally loaded into the database.

Let's consider a simple case. A relational database (see Database equipped with such rules is intelligent.

Table 1 ): A table whose rows correspond to objects and whose columns correspond to some attributes of objects. All objects are of the same type and differ only in the attribute values. This allows you to answer factual questions. For example, you can ask: “In which department does Davison work?” And get the answer: Department of Applied Mathematics. However, if you add information there that is not presented as a table, it can usually answer questions that are not answered in the database. The idea is that in addition to ordinary relational tables, some rules are also stored in the database, for example these:

if (x.Position = "Head" & (x.Department = y.Department) then x boss y

database equipped with such rules is intelligent.              

In fact, if you ask the question "Who is Davison's boss?", a simple built-in inference engine will easily find the answer: "Claudius". This example allows you to find out the relationship at the boss-subordinate level. In this case, it is obvious that Klavdiev is the head not only of Davison, but also of every other employee of the Department of Applied Mathematics. Therefore, an intelligent database can return a fact that is not stored in it. In addition, such foundations make it possible to answer questions that require deductive reasoning, which consists not of one application of the rule but of many applications, so that the facts extracted may not be so obvious and very far removed from those originally introduced.

An intelligent database in which questions can be asked and answered in (limited) natural language is called a question \-answer system.

The first question and answer systems appeared in the 1960s. Questions and answers in these systems were naturally formulated in a very limited subset of natural language, simplified both in terms of the dictionary and in terms of the grammatical forms used. The information source - the database from which the answers were extracted - each of these systems had its own local system tailored to a narrow subject area. The usefulness and scope of such systems was not great, although they enjoyed a certain popularity.

At present, the idea of question-answer systems in the form of intelligent search engines on the Internet has been greatly developed. Relying on all of humanity's global information resources and using fairly sophisticated new algorithms to analyze and synthesize text in a limited natural language, such search engines have proven more than useful. It is no exaggeration to say that these systems are vital to everyone today.

#### 1.1.3. Expert systems and automated theorem proving

The methods of intelligent databases have been further developed in the development of automatic advisory systems. Such expert systems (expert systems) are able to give the user a competent answer to a specific question. The first expert systems were created, for example, for applications in medicine (diagnosis of diseases) and in geology (assessment of deposits).

One of the most important problems in this area is the representation and use of expert knowledge, which by its very nature is quite heterogeneous and contradictory data.

Expert systems are artificial intelligence systems that contain knowledge about a specific weakly structured and narrow subject area that is difficult to formalize and are able to offer and explain reasonable solutions to the user.

It is currently generally accepted that the structure of expert systems consists of five blocks (Fig. Error ! The text of the specified style is missing in the document. .4 ). The combination of three blocks - rules, situation model and conclusion - is indeed an intelligent database. Modules that allow you to extract knowledge and explain the conclusions turn an intelligent database into an expert system.

![](Images/image00327.jpeg)

 

  .four. expert system architecture

Nowadays the knowledge base for an expert system is mostly a set of rules. The simplest case is when the rules are deterministic [\[9\]](#part0005.xhtml#_ftn9)and allow new facts to be derived from existing facts, as in an intelligent database. This option is discussed in detail in the second chapter, where we talk about the representation of knowledge by production systems.

The Output Explain block actually presents the machine output of the result in a human-readable form so that the user can understand what reasoning steps the expert system used to solve the problem. Thus, the user's confidence in the answer increases.

The most important and complex is the knowledge extraction block. The result of the work of this block is clear - this is the replenishment and modification of the knowledge base. But the source data can be different. Don't expect a subject matter expert to formulate effective reasoning rules "from scratch" in the format required by the system. This is an amazing miracle. One of the most reliable is the method of gradually replenishing and changing the knowledge base, and the reason for the change is always when the system could not or incorrectly solve the problem. In this case, the expert analyzes the history of the machine reasoning using the explanation block, determines which rule failed or which rule is missing, and adds them to the knowledge base using the knowledge extraction block. We can say that an expert system, like a human, learns from mistakes.

The inference block is at the center of the structure of expert systems. In this block, the rules are applied to the facts from the situation model, thereby new facts are obtained, to which the rules are also applied, and so on, until the goal, i.e. the required fact, is reached. This process is essentially the process of finding a derivation in formal theory. In fact, the first facts from the model

                                                                                                                                                                                     

Probability p ". Most of the conclusions that the expert system makes according to probabilistic rules are of a probabilistic nature. The user receives several different answers to his question, each of which is assigned its own reliability probability.

Situations are axioms. We apply rules to them, we get new facts, and each new fact is gained from previously gotten facts. In the end we reach (or not) the objective fact, that is, in the language of logical theories, we get the conclusion of the objective proposition. Thus, the core of any expert system can be viewed as a system for automatically searching for conclusions in any formal theory, ie proving theorems.

The proof of theorems certainly involves intellectual effort that requires not only deductive skill but also largely intuitive guessing (e.g. which lemmas are necessary for a given theorem). In other words, proving theorems implies, among other things, searching for already proven theorems and solved sub-problems that may be useful to reach the final goal. So far, several programs with AI elements have been developed that can work in this direction, i.e. programs for automatic theorem proving (Automatic Theorem Proving).

When we first look at the subject, we immediately notice the circumstances known from the course of mathematical logic.

1.               The language of first-order predicate calculus, enriched with things like equality and non-logical predicates and functions, is the accepted vehicle for axiomatization in most disciplines (i.e. almost any statement can be formulated as a formula for the applied predicate calculus).

2.               Tarski's algorithm for enumerating well-formed formulas allows hypotheses to be generated in an exhaustive way (that is, all well-formed formulas can be enumerated).

3.               The solving method is partially correct (that is, for any provable formula, the derivative can be found automatically, and for an unprovable formula, the algorithm may not be able to complete its work).

The following idea emerges, which impresses with its simplicity. Let us write down the axioms of the domain in the language of the first order calculus. Let's run an algorithm like Tarski's algorithm that generates new hypotheses one by one. We will try to prove each hypothesis automatically by the solving method, and if it succeeds, the computer itself will extract more and more new knowledge. The process can run in code 24 hours a day, 7 days a week, 365 days, not on one machine, but on all currently idle machines. By the way, PCs are now idle 90% of the time on average, and their total idle computing power is quite large, so humanity has enough idle resources.

Thus, an automatic theorem proof is possible and easy to program, but such a simple approach turns out to be hopelessly inefficient. Complicated, interesting theorems cannot be proved automatically in the frontal approach because the enumeration space is so large that even the fastest computers are unable to do anything in a reasonable amount of time.

However, to tell the truth, there are so far few examples of how, in a very narrow class of mathematical theories, it has been possible with very specific methods to automatically find and prove non-trivial meaningful theorems that were previously unknown. Such an example is many, many years old \[3\]. Corresponding member of the Russian Academy of Sciences VM Matrosov developed an amazing way of listing and proving mathematical facts in a narrow field related to the theory of differential equations. Co-programmers compiled a program that generated hypotheses and automatically created proofs for them. In this way some really new non-trivial theorems were found and proved. At the same time, the results (theorems and proofs) were published in a renowned mathematical journal as new scientific results in mathematics. The world community does not yet know how to deal with this fact, but there is a precedent.

It should be emphasized that the automatic theorem proof is the main tool of all applied systems with elements of artificial intelligence that use logical calculation formulas to some extent to represent knowledge. Predicate calculus formulas are almost always used - this is the main form for formally writing all statements known to mankind. Therefore, we can safely say that proving theorems automatically is a fundamental topic of AI . In the following chapters it will be shown that all AI methods we consider, and possibly all AI methods in general, directly or indirectly amount to automatic theorem proving.

#### 1.1.4. Automatic robot control and pattern recognition

Robot (robot) - an automatic or remote-controlled device that partially or completely replaces a person in certain work.

The word "robot" was coined by Czech writer Karel Capek and his brother Josef and first used in Capek's play RUR ("Rossum's Universal Robots", 1920).

Robots are most commonly used when performing work in life-threatening conditions or when the facility is relatively inaccessible. Everyone has heard of the success of unmanned lunar and mars rovers, military robots used for reconnaissance and disposal of explosive objects. Recently (2009) another international exhibition of robots was held in Japan, where most of the models presented household and medical robots (Fig. Error! The text of the specified style is missing in the document. .5 ). For example, a pain-sensitive “robot patient” for training dentists was presented to the public. Another example is a "robotcop" who can memorize the faces of people the police are looking for. Upon identification, the robot immediately warns the security personnel via radio. Entertainment robots are becoming increasingly popular . A "robot dance partner" was presented at the same exhibition. This is a human-sized "woman" who, with the help of special sensors, sensitively detects the direction in which the dancer is moving and moves in time with him. She can also perform a short solo dance, move smoothly, and move her arms, head, and body. It seems that the dreams of the future of robots described by 20th century science fiction writers are about to come true.

![](Images/image00328.jpeg) ![](Images/image00329.jpeg) 

  .5. Examples of robots: ping pong robot, dancer robot, patient robot

In fact, robot planning is an extremely difficult task. It seems that there is nothing easier than getting around on two legs. Everyone's development begins with the ability to see and walk. Studying the timeline (Fig. Error! The text of the specified style is missing from the document. .6 ) one gets the idea that these skills do not seem to require any significant intellectual effort. At first glance, speaking, thinking and programming seem much more difficult. However, if you look at the development of robots and robotics, you can easily see the opposite. Robots first learned to program and reason, then talk, then walk, and still haven't learned to see properly.

  .6. Comparing the skill development of a robot and a human

Successfully walking a double robot is quite a difficult task even for the current level of development of science and technology. The fact is that when walking, the center of gravity of our body is almost never above the support area. From the point of view of mechanics, we do not walk, but we fall continuously, but not quite, but successfully with our foot to the right place and move on. The 19th-century frontal approach—constructing a mechanical model with the required number of degrees of freedom and solving the appropriate system of differential equations at each step—does not work. Even the fastest modern computer does not have time to perform the necessary calculations in real time. It is quite clear that when we walk, we do not solve a system of equations in our heads. Completely different techniques are also used to make robots walk. Any new achievement in this field is considered a significant success, as can be seen from the list of exhibits at the International Exhibition presented above. In terms of fast running and jumping (at the level of professional athletes), a two-legged fast running and jumping robot is still an almost unrealistic task today [\[10\]](#part0005.xhtml#_ftn10). Fortunately, a Terminator robot that can move and shoot as adeptly as Schwarzenegger in the famous film is not yet possible.

No adequate apparatus has yet been created that would allow the robot to “see” the world around it and respond to “visual” changes in it as well as a human. The way we see the world is the result of long learning based on intellectual activity. It is known that the child already has stereoscopic color vision in the third week of development. As a result of interacting with objects and accumulating observational experiences, a new ability based on stereoscopic color vision is formed in a child - object perception. It is important to emphasize that this ability is not explained by physiological but by intellectual reasons [\[11\]](#part0005.xhtml#_ftn11). On the other hand, the researchers found that when a person is placed in a completely unusual artificial environment (where the lighting is unusually arranged, familiar objects are unusually large, processes are unusually paced, etc.), the ability for adequate perception is present three-dimensional reality through a person is lost. Object perception is therefore an ability of the psyche and not of the eye. In fact, we see a model that the brain creates very quickly, in tenths of a second, from the information received by the eye. Sometimes this model can differ slightly from reality.

(see e.g. Fig. Error! Text of the specified style in the document

absence. .7 and bugs! Source not found. in error! Source not found. paragraph 0). The problem of technical vision does not lie in the resolution of the cameras, nor in their number, but in the complexity of the algorithms that adequately reconstruct the three-dimensional model from the flat images received by the cameras. There are good technical solutions for specific conditions and special tasks, for example robots recognizing human faces in security systems or robots recognizing the position and orientation of small parts on a watchmaker's strap, but these systems are not interchangeable and not compatible. A universal system of technical vision comparable in breadth of capabilities to human has not yet been designed [\[12\]](#part0005.xhtml#_ftn12).

Computer vision is an example of a broad application of AI techniques called pattern recognition.

Pattern recognition is a branch of cybernetics that develops methods for classifying and identifying objects, processes, and signals that are characterized by a finite set of properties and features.

This area includes, for example, the problem of crossing a street at traffic lights. Recognizing the color of a glowing traffic light and knowing the traffic rules will allow you to make the right decision about whether to cross the road straight or not.

One of the first artificial neural networks capable of perception (perception) and forming a response to a perceived stimulus was Frank Rosenblatt 's perceptron . Perceptron was not considered by its author as a specific technical computing device, but as a model of the brain. It should be noted that after several decades of research, modern work on artificial neural networks rarely pursues such a goal.

Using the example of pattern recognition, we again observe the characteristic curve of the development of the AI direction (see Fig. Error!

The text of the specified style does not exist in the document. .2 and related explanations). After the appearance of Rosenblatt's pioneering work, interest in the subject rose sharply, followed by a cold shower in the form of a book by M. Minsky and S. Papert, which, among other things, reveals the fundamental limitations of the Rosenblatt perceptron. It seemed as if perspectives were lost, but now interest in this topic has increased again. To date, the original idea has been transformed into neural networks and neurocomputers, which are currently more than successful.

One of the greatest achievements in pattern recognition is associated with Logica's development of a fingerprint recognition system in 1982, which has found wide application not only in forensics, but also in various security systems, for example, in laptops. Other application examples of artificial intelligence systems are: speech recognition, recognition of scanned text (OCR), license plate recognition or environmental monitoring from aerial photographs.

It should be clear that synthesizing an information object is always much easier than analyzing the same object . A good example is handwriting. It is very easy to write but extremely difficult to read at times. We all probably know the situation when on the Internet, when registering on a website, when sending a message and similar operations, it is necessary to “decrypt” the code in the figure. This is considered a fairly reliable test that distinguishes a real user from a robot. Modern recognition programs cannot analyze a complex picture in which the contours of letters and numbers are not closed, the lines are bizarrely distorted and there is a lot of “noise”, and a person can do this with almost no effort. So far, pattern recognition is an undeniable competitive advantage of a human over a robot - for how much longer?

We end this section with image examples (Fig.

Mistake! The text of the specified style does not exist in the document. .7 ), which show that the task of pattern recognition is by no means easy for humans either.

 

![](Images/image00330.jpeg)

 

Donkey head or nude figures?

An old man or a couple in love?

![](Images/image00331.jpeg) ![](Images/image00332.jpeg)

One face or two? Young woman or old woman?

  .7.

Examples of complex images for pattern recognition

#### 1.1.5. mind games

One of the most famous and popular uses of application systems with elements of artificial intelligence is a variety of intellectual games (intelligent games). Almost everyone has come across artificial intelligence used in this particular field. Checkers, chess, backgammon can be found both in a mobile phone and as more serious programs for sufficiently powerful computers.

Of all intellectual games, chess has historically attracted the most attention from programmer-researchers. Even today, the best computer chess programs outperform the well-known grandmasters of the world. We can say that in chess the computer has outplayed the person. At the same time, it should be emphasized that there are no miracles in chess programs. They use well-known and carefully implemented algorithms, such as those discussed in Chapter 3. However, if we accept the claim that playing chess at grandmaster level requires intelligence, then we have to admit that the best chess programs are intelligent. At the same time, computer chess is not just entertainment, but also a way to teach new chess players, create chess databases, analyze endgames, and modify the rules [\[13\]](#part0005.xhtml#_ftn13). But the most important thing for us is that this is definitely one of the most interesting cases of knowledge representation.

The task of representing knowledge in mind games is a challenge for the natural intelligence of programmers. The fact is that some of the games are extremely complex from a quantitative point of view. For example, chess has about 1040 possible positions and about 10120 possible games. These are huge numbers, larger than the number of atoms in the universe (from 10 67 to 10 80 according to various estimates ) and than the number of seconds that have passed since the universe began to exist [\[14\]](#part0005.xhtml#_ftn14). No information devices can and will never be able to see or remember all positions and play all games - this is physically impossible. So the developers of intellectual gaming software have a lot of work to do!

MM Botvinnik made a major contribution to the algorithmic understanding of chess. Mikhail Moiseevich Botvinnik (1911-1995) - Doctor of Technical Sciences, the sixth world chess champion, holding this title for a total of 13 years. He was the first to pay special attention to the issues of training chess players, created his own method of preparing for competitions, in which an important place was given to physical exercises and strengthening mental stability. He made a valuable contribution to the theory of multiple beginnings, developed a number of original opening systems and enriched endgame theory with valuable analyses. “I gave the chess everything that was possible, in my opinion. Now I just don't have time to prepare for big tournaments. When I was alone in electrical engineering, I managed to combine work with chess. But for several years I have also been dealing with the problem of playing chess on a computer, and I have become so immersed in this problem that it has become impossible to combine all three activities .

After completing his sporting achievements in 1970 (the “match of the century” between the USSR national team and the world team), Botvinnik dealt with the problems of artificial intelligence and worked on the computer chess program Pioneer. The idea of developing an "electronic chess player" came to him as early as 1958. In 1968, Botvinnik's book was published, in which he formulated a method to model a chess master's thinking when choosing a move, based on a positional evaluation that included all sides and unnecessary ones Sweeps moves and variations aside. Unfortunately, the Pioneer program was never implemented, but Botvinnik's valuable ideas and solutions remained in chess theory and found their way into the later developments of domestic AI specialists.

For several decades, world championships have been held regularly among the chess programs. The championship is currently hosted by the International Computer Gaming Association and is open to all types of computers with no more than eight cores (ie excluding supercomputers and large clusters). It is gratifying to note that the national program Kaissa was developed under the direction of

GM Adelson-Velsky and MV Donskoi. The champion of the last three years is the Rybka program, developed by the Czech-American chess player Vasik Rajlich.

### 1.2. PLACE OF REPRESENTATION OF KNOWLEDGE IN ARTIFICIAL INTELLIGENCE

In the intellectual realm, it is impossible to come up with a universal algorithm suitable for solving any problem. This is how intellectual tasks differ from other, non-intellectual tasks, where there are “do one, do two, do three…” algorithms. The method of solving a problem in the intellectual sphere is always a search for new approaches, new ways, in the end, if nothing can be invented, it's a banal enumeration of all possibilities in search of a solution.  

#### 1.2.1. Iterative nature of problem solving

The general scheme for solving the problem with a computer is shown in fig. Error! The text of the specified style does not exist in the document. .8 . The top-down arrows are deterministic, the bottom-up arrows are non-deterministic. In general, the solution to a problem is always non-deterministic. This is a trial and error method, a search method that often requires you to go back to previous steps.

If the feedback in such a process (arrows from bottom to top) is realized by a person (and this happens quite often), then such a process cannot be described as computer-aided knowledge processing. In order to be able to speak specifically of computer-aided knowledge processing, all or some feedback loops must be closed by the computer.

 

  .eight. Scheme of the process of solving a problem on a computer

With traditional procedural programming (top down), the solution depends entirely on the problem. Each problem has its own individual solution, and the solution to one problem cannot be used directly to solve another without additional work. In artificial intelligence (non-procedural programming), the same search method can be applied to a whole range of problems.

Our summary is this. If the task does not have a direct solution algorithm, it is solved by enumeration, and the return is not made by the programmer's head, but by the program itself, then it is an applied system with elements of artificial intelligence. If the problem has a direct solution algorithm that the programmer finds (perhaps in several attempts), but not the program itself, then there is no artificial intelligence (perhaps the programmer's natural intelligence is present). But in fact there is no insurmountable boundary between these cases. The artificial intelligence of a program is not a discrete property that only takes the values 0 or 1, all or nothing. In contrast, artificial intelligence is a continuous value that takes on any value from the interval (0, 1). The more feedback loops in Fig. Error! The text of the specified style does not exist in the document. .8 does not go through the head of the programmer but through the computer, the higher the level of intellectuality of the program.

#### 1.2.2. knowledge and ignorance

It is impossible to show an explicit boundary between knowing and not knowing . In fact, there is no precise limit to the representation of knowledge in a computer - every program and data reflects some kind of knowledge. On the other hand, the most subtle philosophical considerations can be written (in natural language) into a computer, and they are represented there by a meaningless string of bytes. Bytes will be in the computer, but philosophical knowledge? More specifically , nothing in computers is knowledge without our own interpretation, and knowledge can be extracted from almost anything if you try hard enough. Strictly speaking, in this book (unless expressly stated otherwise) we mean the following interpretation of the term "knowledge":

Knowledge (computer) is a set of strictly defined information structures and well-defined rules and strategies for processing these structures (interpretation rules) .

Let's look at it with a model example.

Let's say we want the computer to sort a set of numbers in ascending order. We humans certainly know how to do this. Think about it, can we teach this to a computer, that is, can we represent the necessary knowledge in a computer? Let us know in advance that there are three of these numbers and they are equal to 3, 5 and 7. You can teach the computer to solve this problem by just writing a statement:

Write(3, 5, 7)

So we have provided the computer with enough knowledge to solve this particular specific problem. Knowledge is presented in the form of a single programming language operator.

Let's complicate the task. Let there be three more numbers, but their value is arbitrary. Let's write a procedure that can sort these numbers in ascending order:

proc Sort3 (x, y, z) if x > y then x :=: y end if                if y > z then y :=: z end if                if x > y then x :=: y end if 

 Write (x,y,z) end perc 

So, we taught the computer to solve a fairly large number of tasks related to sorting three numbers in ascending order, without making the data set too long. In any case, this entry is much smaller than all possible Write statements with all possible combinations of arguments [\[15\]](#part0005.xhtml#_ftn15). Knowledge is presented in the form of a procedure with parameters. In other words, the mechanism of procedures in programming languages is already a method of knowledge representation. It's just that this is quite an old method, we're used to it, and we don't perceive it as a mechanism for representing knowledge.

Another question arises: Where did the Sort3 procedure come from ?

We can say that, as usual, it was invented by a programmer. But we will give a not quite familiar answer and show how it is possible to present in the program sufficient knowledge for the computer to come up with a procedure similar to Sort3 .

Sort3 procedure code fragments similar to each other and there are more than two of them, special refactoring (transformation of the program text that does not change the function performed by the program) should be applied, which is called proceduralization. Proceduralization is a refactoring in which repeated or similar fragments of a program are replaced by calling a newly introduced procedure. By rewriting the procedure Sort3 , by entering the procedure Sort2 we get the procedure Sort3' .

proc Sort3' (x,y,z)

 sort2(x,y)

 Sort2(y,z)

 sort2(x,y)

 Write (x, y, z) end perc proc Sort2(u,v)

 if u > v then u :=: v end if End perc 

But the Sort2 procedure is formally easy to specify:

x, y { Sort2(x, y) } x < y

Here the precondition is written out before the title of the procedure (enclosed in curly brackets) and the postcondition after the title. The Sort2 method is very simple and obviously useful in many cases. It can be assumed that this procedure, together with the specification (pre- and post-condition), is contained in a library of ready-made procedures available to the compiler.

A precondition is a formal statement about a fragment's input parameters in a programming language (e.g., a procedure) that must be satisfied before the fragment is executed in order for the fragment to function correctly.

A postcondition is a formal statement about the input and output parameters of a programming language fragment that is guaranteed to be executed after fragment execution is complete if the precondition is met.

Then, using this specification, the translator can derive the Sort3' procedure :

x, y, z

{Sort2(x, y)} x < y, z

{Sort2(y, z)} y < z, x < z {Sort2(x, y)} x < y < z.

Therefore, we made the translation mechanism a little more complicated (allowing for the possibility of inferences during translation) and got a system of automatic program synthesis. In other words, we didn't compactly write a Sort3 procedure , but a whole class of procedures. In this case, knowledge is presented in the form of a set procedure and an inference algorithm built into the translator.

It seems that the terms "knowledge" and "process" are orthogonal. If there is a procedure, no knowledge is required - do what the procedure says and the problem will be solved. The above example shows that the terms "knowledge" and "process" (or rather algorithm) are not only not opposites, but are in fact inextricably linked.

Any algorithm necessarily contains knowledge, and all knowledge is ultimately represented by algorithms. 

#### 1.2.3. Solution search algorithms and knowledge representation

The first stage in the development of AI was associated with the development of methods for solving problems - algorithms for finding a solution and constructing a logical conclusion. Currently, this is already a well-researched and studied topic. The most important classical results are presented in the third chapter.

For non-trivial cases, however, the complexity of finding a solution is very high. The complexity of finding a solution is a fast-growing function (in most cases exponentially or faster-growing) whose argument is the total volume of the knowledge base. Considering specific algorithms below , we prove accurate estimates for , but here we informally convince the reader of the validity of this remark . The solution sought is a combination of a finite number of given elements, of which n . Then there are a total of 2 n \-1 non-empty combinations [\[16\]](#part0005.xhtml#_ftn16)if we take elements without repetitions, and if we take elements with repetitions then even more. We don't know in advance which combination is the solution, this is the search nature of the algorithm, which means that in the worst case we have to go through all the combinations!

One of the ways to reduce the complexity of finding a solution is to change the search algorithms to increase their internal efficiency, which does not depend on the problem to be solved. However, for many AI-typical problems, their NP- completeness has been proven. Creating an efficient (more efficient than exponential) algorithm is absolutely incredible to them. If an efficient (e.g. polynomial) algorithm is suddenly discovered for a still unexplored AI problem, the problem is often no longer qualified as an AI problem and is shifted to the area of conventional programming. Therefore, no significant improvement in increasing the internal efficiency of search algorithms can currently be expected.

A much more productive method to reduce the complexity of finding a solution is to increase the efficiency of knowledge representation. If choosing a sophisticated representation makes it possible to reduce the size of the knowledge base, then the same standard search algorithm becomes much more efficient in the sense that the limits of its applicability are expanded. Let's explain this with a numerical model example that compares two hypothetical ways of representing knowledge. Let the same problem be of size n in the first representation , and - n /2 in the second. The enumeration algorithm is the same and has a complexity of 2 k , where k is the size of the problem. At the same time, a more compact representation is not given for nothing: each step of the enumeration takes ten times longer and another 100 time units are irretrievably lost for preprocessing. In fact, we are comparing two functions: 2 n and 100 + 10\*2 n /2 . For small n , the first function is smaller, but after n \= 8 the second function becomes smaller, and its benefit only increases with n (Fig. Error! The text of the specified style is missing in the document. .9 ). Even a small gain in the value of the exponential function's argument outweighs any other losses!

![](Images/image00333.jpeg)

  .9. Comparison of search complexity depending on the compactness of the knowledge base

The compactness of the knowledge base is a decisive factor for the performance of an artificially intelligent system and thus for the limits of its applicability. This circumstance determines the structure of this book. The chapters are structured according to methods of knowledge representation, not according to methods of finding solutions. When solving a problem in the intellectual domain, one should first choose a knowledge representation and then choose an appropriate solution-seeking algorithm. The fact is: If an unsuccessful representation of knowledge is chosen, then no tricks with algorithms will help. Most likely, if a particularly successful representation of knowledge is invented, the most common algorithm for finding a solution will give fairly satisfactory results.

### 1.3. HISTORY OF ARTIFICIAL INTELLIGENCE

A digression into history is often absolutely necessary, otherwise it is incomprehensible why the modern regulations under consideration are exactly what they are. Finally, for historical and psychological reasons, the definitions and concepts of AI are largely subjective. The specifications of the AI differ noticeably from the objectively determined laws of physics or chemistry. We have divided the history of AI development into several periods (prehistoric , when even the term "artificial intelligence" is not yet a essence, but some works can be retrospectively and with some distance attributed to this direction [\[17\]](#part0005.xhtml#_ftn17);

\-                    pioneering , when the advent of computers and other technological advances of the 20th century dramatically broadened the horizons of possible research, when almost every proposed idea stunned with its novelty and opened up new perspectives, and ideas popped up like fireworks, one after the other;

\-                    academic , as the direction of AI emerged as a distinct research area in academia, with its own terminology, agencies, research centers, and the formation of the international community; when research was conducted primarily in the interest of developing direction itself, and practical applications were of interest primarily through the most basic way of implementation, and not through tactics

technical characteristics;

\-                    Industry , which continues and develops into our days, where the increased capabilities of technology have paved the way for the industrial mass deployment of artificial intelligence systems.

Of course, one should not think that these periods followed and followed one another strictly sequentially, like five-year plans for the development of a socialist economy. Both the pioneering and academic eras had separate industrial designs that shaped history, and even in our mercantile era scientific breakthroughs occur, albeit not often, that abruptly lead to a 'paradigm shift'.

#### 1.3.1. Artificial intelligence background

Reliably recorded first attempts by Raymond Lull more than 700 years ago to create a machine simulating some aspects of the human mind. Lull believed that it was possible to discover a special method or art by which one could, with reasonable necessity, derive all sorts of truths from general concepts, and especially the truths of Christian dogma. Based on his ideas, he created the first logical engine in the form of several concentric circles of paper divided into compartments in which general concepts and categories were placed. By rotating the circles relative to each other, various more or less complex combinations of the given concepts could be obtained. Lull believed that in this way new true truths could be discovered. Of course, no new truths were discovered, but the idea that reasoning can be done mechanically sounded!

We now know that logical operations can be treated algebraically and performed arithmetically, but this was not nearly so obvious until the work of G. Boole in the 19th century. Therefore, the first designers of intelligent machines focused their attention on the construction of computational machines. Logical thinking seemed to be more of a challenge. Several such "computers" were built in the 17th and 18th centuries, and here the Leibniz calculator must be mentioned, which was the first machine in the world that could efficiently perform all four arithmetic operations.

G. Leibniz started work on this machine in 1670; two years later he made a new sketch description, on the basis of which the copy was apparently produced, which the scientist demonstrated at a meeting of the Royal Society of London in February 1673. Leibniz admitted that his instrument was not yet perfect and promised to improve it as soon as he returned to Paris. Although he made significant improvements to the machine in the years that followed, it was not until 1694 that he came up with its final version. As a result, Leibniz came back to his invention several times and offered new, improved possibilities.

The crowning prehistory of computers is the work of Charles Babbage. Babbage began with a mechanical contraption designed to automate computations by approximating functions with polynomials and computing finite differences. The possibility of an approximate representation of logarithms and trigonometric functions by polynomials allows us to consider this machine as a fairly universal computing device. This difference engine had to be able to compute the values of polynomials up to the sixth degree with an accuracy of up to the 18th digit. In the same year, 1822, Babbage built a model of a differential motor consisting of rollers and gears rotated manually with a special lever. The following year the British government gave him a subsidy of £1,500. In developing the machine, Babbage did not show all the technical and mechanical difficulties associated with its implementation, and not only did not fulfill the promised three years, but had to stop work nine years later. However, part of the machine still began to function, performing calculations with even greater accuracy than expected.

In 1834 Babbage invented the Analytical Engine . It consisted of a "warehouse" for storing numbers (storage device), a "mill" for performing arithmetic operations with numbers (arithmetic device), a "drum" that controlled the operations of the machine in a certain order (controller), and data inputs and output devices. . The register memory of Babbage's machine could store at least 10 decimal numbers of 40 characters each, but could theoretically be expanded to a thousand 50-bit numbers. The arithmetic unit had hardware support for all four arithmetic operations. The machine performed addition in 3 seconds, multiplication and division in 2 minutes. The machine's entrance was to receive two streams of punched cards, which Babbage called "operative cards" and "variable cards": the first controlled the processing of data recorded on the second. Information was recorded on punched cards by punching holes. It was possible to create a function library from operating maps. Thus, all the main elements of the architecture of Babbage's first computers were fully anticipated. The Analytical Engine was never implemented. The main reason for failure is technological. The technologies of the time did not allow the necessary complex parts to be manufactured in sufficient quantities and with sufficient accuracy. The inventor wrote in 1851: " All developments in connection with the Analytical Engine have been carried out at my expense. I've done a number of experiments and gotten to the point where my skills are no longer sufficient. In this respect, I feel compelled to refuse further work .

#### 1.3.2. frontier research \_

The serious development of artificial intelligence as a scientific direction began in the 1940s, after the advent of computers. In 1948 Norbert Wiener published the book "Cybernetics, or Control and Communication in the Animal Kingdom and the Machine" and thus founded a new science - cybernetics .

Although the title of Wiener's book makes no mention of thinking, the hated question "Can machines think?" [\[18\]](#part0005.xhtml#_ftn18)first appeared two years later in Turing's famous article. (In this article in particular, a constructive criterion for the presence of AI in a machine, the so-called Turing test, was formulated for the first time ).

Regarding this topic, opinions differed not only among external observers, journalists and the general public, but also among the scientists themselves who have started working in the field of AI. Of course, the overall reaction from the working researchers was positive. The subtlety is that two similar questions can be asked:

Can a machine think like a human?

Can a machine think rationally?

The search for a constructive answer to the first question leads to the modeling of human thought, in which it is considered important not only to obtain an answer to an intellectual question, but also to analyze the means of obtaining an answer. This direction is called "neurocybernetics".

The main method of neurocybernetics is the mathematical modeling of the human brain. As early as 1943, American scientists Warren McCulloch and Walter Pitts proposed a mathematical model for the operation of a human brain neuron - an artificial neuron \- and methods for combining artificial neurons into a neural network.

This was followed by the pioneering work of Rosenblatt, Minsky and other researchers. However, in the 70s, work in this direction slowed down somewhat due to the low quantitative capabilities of computers of that time. The fact is that in the human brain there are 10 to 14 billion (10 9 ) neurons working in parallel and each has an average of about seven thousand (10 3 ) connections to other neurons. The number of artificial neurons in the first networks was measured in hundreds, at best thousands, but such large quantitative differences (millions of times) create a qualitative abyss - it is impossible to study large systems on small models. Note that the human brain's quantitative indicators in neural networks have not yet been reached [\[19\]](#part0005.xhtml#_ftn19), but the scale is gradually becoming appropriate

In answering the second question we come to the cybernetics of the "black box" when only entry and exit, stimulus and reaction are observed and the inner structure of the "thinking agent" remains hidden from observation. Unlike neurocybernetics, "black box" cybernetics does not care how the "thinking" device works. The main thing is that it reacts to the given input actions in the same way as the human brain, i.e. rationally.

Researchers in this field immediately switched from highly complex parallel nondeterministic neurocybernetic networks to relatively simple algorithmic models that manipulate abstract symbols rather than real-world signals. That's why we prefer the term symbolic AI (see fig. Error! Text of the specified style is missing in the document. .10 ).

The most notable pioneering work in this direction was the Logic Theorist program developed by A. Newell, G. Simon, and J. Shaw in 1955-1956. Working in the field of automatic theorem proving, the program was able to automatically find the derivation for 38 of the 52 propositional calculus theorems given in Russell and Whitehead's seminal book Principia Mathematica . in addition, in one case a shorter ending was found compared to the original.

So many different and sometimes surprising opinions and assessments have been expressed in the literature about this undoubted achievement that we consider it permissible to give our conclusions on universal programs for automatic proving of theorems, and therefore on universal mental programs, using the example of the logic-theoretical program in general (see also paragraph 0).

1.               Automatically proven theorems contain no new mathematical insights: in the case of the Logic Theorist program, these are simple technical theorems of propositional calculus. Their validity can easily be checked by creating truth tables. The only task is to find a formal derivation (sequence of formulas) in a given axiomatic and with given rules of inference. The search for a conclusion does not require any new ideas or methods, but relies on fairly routine techniques. Among the derivations discussed, there are no derivations shorter than three applications of the inference rules, and no derivations longer than two dozen applications of the inference rules. The results of the logic theorist program have no practical meaning.

2.               The author's long-term observations on students studying propositional calculus, who in the process of education are forced to seek and find similar conclusions, allow us to assert that the average person "off the street" without special training will not find any of the formal proofs, found by the program "Logic Theorist". A person "off the street" simply will not understand what to do, because obviously they have never done anything like this. In this art, then, the unprepared is inferior to the “logic theorist” program. At the same time, after three or four practice sessions with the teacher, diligent students can find any of these conclusions, as well as the conclusions that the program could not find. It should be noted that the conclusions found by the students may not be as elegant as those of Russell and Whitehead and may not be found very quickly. Still, it can be argued that a person who is able to pass the entrance exams to the university can also learn to look for formal inferences no worse than the Logic Theorist program.

3.               From a qualitative point of view, the results of the Logic Theorist program have not improved significantly over the past half century. The point is that the problem of automatically searching for a derivation in propositional calculus is exhaustive in character (see Section 0). Modern computers are millions and billions of times more powerful than the computer used by Shaw, but modern universal inference search programs can only draw tens, at most hundreds of times more complex conclusions, so on a qualitative level the first two remarks in this list remain valid even today and not only not applicable to the "logic theorist" program, but to any modern program that claims to automatically prove any theorem in a sufficiently rich calculus.

#### 1.3.3. emergence and development

In 1956, a two-month seminar was held at Dartmouth College (one of the oldest universities in the United States), attended by ten leading researchers in the new direction:

\-                     John McCarthy, Dartmouth College;

\-                     Marvin Minsky, Harvard University;

\-                     Claude Shannon, Bell Laboratories;

\-                     Nathaniel Rochester, IBM;

\-                     Arthur Samuel, IBM;

\-                     Allen Newell, Carnegie Mellon University;

\-                     Herbert Simon, Carnegie University

mellon;

\-                     Trenchard Moore, Princeton University;

\-                     Ray Solomonoff, Massachusetts

technological institute;

\-                     Oliver Selfridge, Massachusetts Institute of Technology.

This seminar is considered the beginning of artificial intelligence as an independent direction, and the term artificial intelligence itself was proposed and adopted . No particular scientific results

The Dartmouth seminar did not. Other important events took place on it: artificial intelligence was recognized as a separate branch of science, the first impressive results were demonstrated (similar to the Logic Theorist program), and the scientific community was formed as a result of personal acquaintance of the leaders.

After that, research in the field of AI was not only carried out in the USA on a broad front. The first publications began to appear, trying to generalize the collected material. Among the experts presenting such work were J. McCarthy, M. Minsky, E. Feigenbaum (E. Feigenbaum, USA), D. Michie (UK), AA Lyapunov and VM Glushkov (USSR). Of course, the results were not long in coming - many ideas were proposed, most of which are still used today.

In the late 1950s a graph search model was proposed. In this approach, the task is represented as a search for a path in a graph whose vertices are the states of the task and the arcs are all possible feasible transformations. The solution to the problem is to find a way from the initial state to the target state. In the early 1960s heuristic programming became widespread (see Chapter 3). A heuristic is a rule, usually obtained empirically, that reduces the scope of the enumeration in the solution space. Heuristic programming is the development of strategies for finding a solution based on already known heuristics. In the late 1960s General methods for the automatic proof of theorems in first-order calculi were developed (notably the solution method by J. Robinson and the inverse method by S. Yu. Maslov, see Chapter 4) and based on them in the early 1970s . Numerous programming tools for solving intellectual problems have been proposed. Thus, in 1973, the Prolog language was created, which is still a popular tool for logic programming. Virtually the entire body of ideas and concepts currently used in AI have been proposed or identified during this period. It is impossible to list all ideas , nor is it necessary if the general development scheme is clear (see fig. Error! The text of the specified style is missing in the document. .10 ) .

#### 1.3.4. Scientific deepening and industrial implementation

In our view, the most important event for AI in the 80s. was the birth of the concept of knowledge engineering. This concept was presented in 1982 by E. Feigenbaum.

Knowledge engineering is an area of artificial intelligence that studies the methods and means of extracting, representing, structuring, and using knowledge.

The separation of knowledge representation methods from solution search methods , the construction of more and more effective specialized knowledge representation methods in certain subject areas made it possible to obtain sufficiently effective representations to solve practically significant problems using the available methods on real computers. At the same time, different approaches and directions within AI, having found a common methodological basis, began to interlock more closely, since there was no need to prove the "purity of the theory" or the "originality of the approach", but it was necessary to achieve a practical result in some way.

During this time, computer systems appeared that were far from passing the Turing test, but positively answered such questions: Can a machine solve some intellectual problems cheaper than a human being? Faster than a human? More reliable than a human?

The power of computing has increased significantly, and it has become clear that if we put aside the philosophical, ethical, and moral issues of "artificial intelligence," it is not only possible, but useful, in many specific, narrowly specialized fields, them to replace a person with a machine. Applied artificial intelligence systems began to make profits. Investments in academic research immediately started to increase , which brought new results introduced to industry , which generated revenue partially invested in research ... There was a positive feedback and the time of the rise of AI is not over yet!

The second significant event of this period, after a certain lull, was the revival of neurocybernetics with the concepts of neural networks and neurocomputers. The renewed interest was not caused by a sudden miraculous revelation from above with a popular explanation of exactly how the human brain is constructed and works. Of course, physiologists, psychologists, linguists, philosophers and other researchers didn't sit idly by, but learned and found out a lot of new things about our human nature, but that wasn't the reason. Even within neurocybernetics itself, no groundbreaking discoveries were made. Modern neural networks use mathematical models that are very close to the original ones, although of course they are far more developed and improved. The obvious reason for the resurgence of neurocybernetics lies in the amazing advances in microelectronics. In pioneering work such as Rosenblatt's perceptron, quantitative differences between artificial and natural neural networks were measured many billions of times, and there was no question of a qualitative comparison. Now quantitative differences are being measured thousands of times, and designers of superneurocomputers have new possibilities never seen before. Qualitative changes are to be expected, which the ongoing quantitative changes should lead to.

As a third notable event of the relatively recent past, we consider the introduction of the well-deserved philosophical notion of "ontology" into the fresh soil of computer science.

An ontology is a formalization of a particular field of knowledge using a conceptual schema. Typically, such a schema consists of a data structure containing all relevant object classes, their relationships, and the constraints imposed on the objects and relationships.

Ontologies are used in the programming process as a form of knowledge representation about the real world or its part, i.e. as a domain model . Although originally philosophical in nature, the term "ontology" [\[20\]](#part0005.xhtml#_ftn20)has taken on a meaning of its own in computer science. There are two main differences here:

\-                     Ontology in computer science is a form of knowledge representation, a form that a computer can easily process;

\-                     Information ontologies are always created with concrete goals to solve practical problems; They are judged more on applicability than completeness, completeness, and correctness.

The author is firmly convinced that the analysis, construction, development and use of domain models is currently the most important and promising task in computer science, not only in AI but also in other information technologies.

Examples include the concept of business process management systems (BPMS) in the field of information management systems, the concept of the semantic web (semantic web) on the Internet or the concept of domain-specific languages (domain-specific languages) in application programming. All of these promising concepts address the notion of ontology [\[21\]](#part0005.xhtml#_ftn21).

  .10 reflects our vision of the history of AI development and summarizes the section.

  .ten.

Development history of artificial intelligence

### 1.4. CLASSIFICATIONS OF APPLIED ARTIFICIAL INTELLIGENCE SYSTEMS

The applications and areas in which artificial intelligence is used are very diverse - Section 0 only offers a small selection of case studies, not an encyclopedic overview. In fact, thousands of applied AI systems are used in real practice, and each has its own characteristics and peculiarities. Such a heterogeneous collection of objects and methods must be classified, even multiple classifications, one is essential.

#### 1.4.1. types of knowledge

The knowledge that we are going to represent in a computer is very diverse.

According to SS Lavrov \[4\], knowledge can be divided into three fundamentally different types:

1.               Conceptual, conceptual knowledge . This group includes concepts and relationships between them, e.g. B. Rules, laws, immutable relationships, as well as heuristic knowledge \- informal reasoning rules that reflect practical experience in solving problems in the problem area.

2.               procedural error ! The bookmark is not defined. , algorithmic knowledge . These include various skills, technologies, procedures, algorithms, their software implementations, and typical problem-solving approaches—that is, those forms of knowledge that are almost always used explicitly for the computational solution of any problem.

3.               factual knowledge . These are the most diverse quantitative and qualitative characteristics of certain objects, that is, data. For example, various data in databases, constants in programs, etc.

Of course, there is no impenetrable boundary between the types of knowledge (see also paragraph 0). In addition, it sometimes happens that knowledge is difficult to assign to a specific type. For example, algorithms for calculating mathematical functions (sin, cos, etc.) are represented as a set of expansion coefficients in special polynomials for the sake of efficiency. These coefficients are of course data, i.e. factual knowledge, but are used as algorithmic knowledge. Nevertheless, this knowledge classification is very useful and effective when it comes to applied artificial intelligence systems, because you can focus on the issues of conceptual knowledge representation important for AI, using the methods of representation of algorithmic and factographic knowledge as ready -Foundation made.

Lavrov's classification of knowledge is accepted as fundamental in this book.

Lavrov Sviatoslav Sergeyevich , 1923–2004, Russian scientist, corresponding member of the Russian Academy of Sciences. Author of works on mechanics, automatic control, computer mathematics and programming. Winner of the Lenin Prize in 1957. Lavrov's scientific biography is in a sense unique. At a very young age he became the founder of missile and space ballistics in the USSR and an undeniable authority on controlled flight dynamics and automatic piloting. The advent of digital computing technology caused a sharp turn in SS Lavrov's activities and within a few years made him a programming classic in the USSR.

#### 1.4.2. Classification according to the degree of use of different types of knowledge

Depending on what types of knowledge are used and how it is done, artificial intelligence systems can be classified in different ways.

1.               If a software system uses only factual knowledge, then such a software system is called a database (DB) and is not usually considered artificial intelligence under modern conditions.[\[22\]](#part0005.xhtml#_ftn22)  

2.               If a software system mainly uses algorithmic knowledge, then such a software system is usually referred to as an application software package . The assignment of such a software package to an AI system is usually stated explicitly. If an application package is used simply as a library of procedures, it is not classified as an artificially intelligent system. For example, if it uses AI methods, if the program to solve a specific problem is created not by the user, but by an automatic planner, then such a package of application programs can be considered an artificial intelligence system.

3.               If conceptual knowledge is used in some form in a software system, then such a system is said to be artificially intelligent.

Note that advanced application packages usually include or actively use an external database, and AI application systems almost always use both software packages and databases (Fig. Error! The text of the specified style is missing from the document. . 11 ) . For example, a developed chess program has a huge database of openings and endgames, a special software package for working with positions and moves during a game, and a set of strategic move-selection rules related to conceptual knowledge.

![](Images/image00334.jpeg)

  .eleven. Classification of applied systems with elements of artificial intelligence according to the type of knowledge used.

The subject of this book is precisely the applied systems of artificial intelligence. At the same time, we believe that the reader is sufficiently familiar with the concepts of software packages and databases that all attention is focused on the presentation of conceptual knowledge.

#### 1.4.3. Classification according to the form of knowledge representation

When the need is recognized and felt to share knowledge about all three types, a way must be chosen to represent them in a computer. The powerful mechanisms that a person uses to represent knowledge: natural languages, mathematics, visual images, are suitable for representing all types of knowledge, but are unsuitable for implementation in a computer. More precisely, on the contrary, modern computers are not adapted to use these mechanisms - computers are too primitive and unintelligent.

There is therefore a need to invent such types of knowledge representation that, on the one hand , enable the representation of knowledge of all kinds and, on the other hand, would be feasible in modern computers .

Mechanisms for representing factual and algorithmic knowledge in computers are well understood and established. For factual knowledge, these are database management systems (DBMS), in modern conditions mostly relational. For algorithmic knowledge, these are libraries of procedures, mostly object-oriented under modern conditions, ie libraries of types and classes.

The classification according to the form of knowledge representation thus first considers the representation of conceptual knowledge.

Many different mechanisms for representing conceptual knowledge are proposed. Currently, the following three are most commonly used (Fig. Error! The text of the specified style is missing in the document. .12 ).

rules or products . Rule-based artificial intelligence systems are currently the most widespread. From a mathematical point of view, such systems use computability models that approximate normal Markov algorithms. Production systems are covered in detail in Chapters 2 and 3 of this book.

Formulas of Logical Calculus . Artificial intelligence systems based on logical formulas are currently the second most common. From a mathematical point of view, such systems use calculi close to the first-order predicate calculus and in some cases to Church's  -calculus . The representation of knowledge with formulas of logical calculus is considered in the fourth chapter.

Frames and Semantic Networks . Now this mechanism is used relatively rarely, although in the recent past it was not. From a mathematical point of view, such systems use the apparatus of graph theory.

All three common mechanisms are comparable in terms of expressiveness and other general mathematical properties.

The preference for one or another knowledge representation mechanism is often given on the basis of considerations of familiarity, ease of programming, familiarity with the theory of developers of applied systems. It is particularly important how compact the representation of knowledge about a specific task is, see paragraph

#### 1.4.4. Classification by type of response when solving problems

When solving a specific problem, the applied AI system receives knowledge in one form or another at the input and gives an answer at the output, which also has a certain form and represents (new) knowledge. According to the introduced classification of knowledge types, systems of artificial intelligence can be classified according to the level of the given answer.

0.               Logical answer (yes or no); not very convenient to use, rarely used now.

1.               Factual answer (answer-fact); If a question is answered specifically, such systems are often referred to as information systems. Currently the most common class of systems.

2.               procedural response ; When solving a problem, the system can create and execute a procedure ( program synthesis system , automatic programming ). This is a very interesting and promising direction that is attracting the attention of a large number of researchers.

3.               Conceptual Response ; The answer is the law, not a solution is built but a scheme for solving a class of problems that may not even be feasible on a computer. Full implementations are not known at this time.

Let's give examples of answers at different levels using the paradigm with sorting numbers from paragraph 0 (remember, the problem is as follows: we want the computer to sort a set of three numbers in ascending order ).

(0)          2 5 7 yes

5 2 7 no

(1)          5 2 7 2 5 7

(2)          { x , y , z }?{ x < y < z }  Sort3 

### ![](Images/image00335.jpeg)(3) sort { x i }   i , j ( i < j  x i < xj\_ \_ )

At level 0 we present a sequence and the system only checks if it is sorted or not. At level 1 we present a sequence and the system obediently sorts it. At level 2, the system creates a sorting procedure similar to that shown in paragraph 0. Finally , at level 3, the hypothetical system tells us what it means to sort an array of numbers [\[23\]](#part0005.xhtml#_ftn23).

#### 1.4.5. Classification according to the degree of universality

First, each new idea of knowledge representation tied to a specific subject area is born. The fact is that in the field of AI it is common to accompany the publication of new ideas with at least one concrete practical example that demonstrates the advantages of the novelty. If the idea is good, it finds new applications in related areas and grows into a problem-oriented method. In the future, there will be a temptation to make the knowledge representation system as universal as possible for solving a wide variety of problems. However, this wish is practically useless, since with increasing universality the applicability of such knowledge representations decreases sharply.

Let's explain in more detail the terminology we use [\[24\]](#part0005.xhtml#_ftn24).

Universality (of a given knowledge representation system in a given subject) is the proportion of representable tasks in the subject.

Therefore , we call universal (in a particular subject) a way of representing knowledge that allows us to formulate all tasks .

Applicability (of a given knowledge representation system in a given domain) is the fraction of representable problems in the domain that can be solved.

Therefore , we call applicable everywhere or total (in a certain subject) such a way of representing knowledge that allows us to solve all problems considering real quantitative constraints . It is clear that universal and at the same time total knowledge representation systems are hardly possible for sufficiently broad subject areas. Furthermore, observations show that there is an inverse relationship between universality and applicability 

The concept of representing the world in discrete states and looking for a sequence of transformations from the initial state to the target state is surprisingly broadly applicable. The graph search algorithm is applicable in all cases. However, this versatility comes at the cost of sheer search inefficiency.

![](Images/image00336.jpeg)

Rice. Mistake!               The text of the specified style in the document

absence. .13. Relationship between universality and applicability

Note that in practice, neither in databases, nor in application packages, nor in applied artificial intelligence systems, the goal of achieving universality is usually set. Typically, the goal is to increase applicability, even at the cost of reducing versatility. The reasons are very simple. First, the possibilities of manipulating knowledge depend on the subject, and only by taking into account the characteristics of the subject one can hope to build a compact representation of knowledge that will provide effective solution to problems and increase applicability. Second, meta-knowledge (management strategy) is weak in universal systems; Knowledge of the order in which certain rules should be applied, what is important and what can be neglected when solving a problem.

#### 1.4.6. Classification by architecture and tools

When analyzing the architecture of applied systems with elements of artificial intelligence, it is logical to single out:

\-                     System manipulated objects ( other

given words);

\-                     Actions by these manipulations

produced (what can be done with this data);

\-                     Control strategy that determines when and what manipulations to perform (in what order, on what objects, what actions to apply).

Such an idea of the architecture of an artificial intelligence system is not a dogma - it arises from the analysis of typical modern artificial intelligence systems. Highly specialized systems sometimes have a different architecture. This means a logical analysis and not an analysis at the machine code level, where the architectural structure is already indistinguishable.

Now we are talking about these three components (especially if they are clearly separated in the software implementation): data (object properties), algorithms (object methods in the sense of object-oriented programming) and meta-knowledge .

The first work in the field of AI already showed the need for special tools for the development of applied systems. This is due to a number of features of the software implementation of artificially intelligent systems, some of which we will discuss in the third chapter. Be that as it may, for the development of applied artificial intelligence systems, various programming languages and tools have been and are used, which cannot escape a given system. The tool used in the development of the AI system is a classification feature.

### CONCLUSIONS ON CHAPTER 1

1.               Artificial intelligence is a branch of science that has a clearly defined theme – the modeling of thinking, understood as rational behavior, using a range of methods from computer science and mathematics.

2.               The history of the development of artificial intelligence shows that the time for reorientation is over and the time for practical application is now upon us.

3.               An analysis of the achievements of artificial intelligence shows that the most important methods for practical application are methods of knowledge representation.

# CHAPTER 2. KNOWLEDGE REPRESENTATION THROUGH PRODUCT SYSTEMS

Knowledge representation by production systems (Production Rules Knowledge Representation) is one of the most frequently used knowledge representation mechanisms in intelligent systems. This mechanism is conceptually simple, its idea is naturally perceived and easily implemented in software.

In fact, there is no sharp boundary between artificial intelligence applications and other software. Production systems are just another way for a computer to organize a process of information processing. This method is fundamentally different from the usual procedural and object-oriented programming, but has no fewer features .

### 2.1. PRODUCT SYSTEMS

several definitions of production systems (or production systems or rules-based systems ) are proposed, [\[25\]](#part0005.xhtml#_ftn25)viewed from different angles. Ultimately, different definitions lead to the same object, although they come from different angles and differ in some details. We consider three definitions:

\-                     product systems in their structure;

\-                     production systems from an algorithmic point of view; - Production systems as a logical calculation.

Before proceeding to a systematic presentation of the techniques and methods of handling products as information units, we consider it necessary to organize the accompanying terminology, systematize different interpretations and explicitly "highlight" possible areas of application.

#### 2.1.1. Terminological conventions and meaningful interpretation

The title of the paragraph contains the word "sensible", indicating the author's deliberate retreat from the point of view of the

"Strictness" and "algorithm" in the presentation of the material, but this digression is temporary - within the confines of this paragraph . The digression is explained by the authors' desire to emphasize the "confusion" in terms, ideas and justifications present in the discussion area, which, in turn, is an almost necessary sign of the "youth" of the research direction and the intensity of its development.

Substantively (from a common sense and natural language perspective), the term “production” is most commonly associated with a complex sentence of the “if premise , then conclusion ” conditional type. For now, without going into detail, let's define precisely these terms: premise and conclusion . Again, without further explanation, we will write the production in symbolic form for the sake of simplicity

p  q , (\*)

where p and q represent premise and conclusion, respectively. We draw the attention of the reader to the fact that in a symbolic notation, in contrast to a verbal example, the third and very important element of production is clearly recorded - a bundle , marked with an arrow. Each of the three elements of the product can and should have some semantic load (interpretation, semantics, meaning, etc. - different versions are used in different literature sources) so that the meaning can be compared for all products and used accordingly (product) in the solution a specific problem. Depending on the combination of interpretations chosen in an individual case, the applicable mathematical foundations as well as algorithms and strategies for working with products can change significantly. At the same time, an attentive and careful reader should note that each product, regardless of the accepted interpretations, defines a certain rule of behavior or transformation. in a certain subject area.

Despite the "meaningfulness" declared in this paragraph, we will not analyze all possible combinations of semantic loads, but will limit ourselves to the subject area determined by the title and purpose of the book.

By their very nature, productions can be divided into two non-overlapping classes: homogeneous and non \-homogeneous . This division is determined by the way in which the interpretation of the premise and the conclusion of the enactment are specified. In the first case, p and q are given a "similar" meaning (words in a common alphabet, numerical values, logical expressions, etc.). The second type includes products in which the premise and conclusion are interpreted differently (condition - action, state of the environment - transition, stimulus - response, other combinations).

Remember another important point: all the mechanisms and techniques that make up the contents of this book are designed to describe and analyze changes in a specific subject. We usually call a fixed situation in the subject the current . condition ( environment or environment ). We will (unless expressly stated otherwise) always denote the set of all possible states by the letter D , and individual states from this set are denoted by the letters d with indices and assume that this state is described by a set of definite values ( statements) of something (about something). or). The method of storing (organizing) the current state d is not critical (list, array, set of tables). We also denote the mechanism for storing the current state with the letter D (it's always easy to distinguish from the context what it is - a set of states or a mechanism for representing a set in a program) with the letter D and call it " base Facts "(less often -" base data " and sometimes " search space ").

The set of all possible states of the database D is called the search space .

Given the dynamics of development (changing the situation) of the analyzed area, we can also speak of the transition from one state to another, while assuming the existence of an initial state (necessarily!) and a final state (not always). The sequence of transitions leading from the initial state to the final state is called an inference in the search space, and the process of going from one state to the one immediately following it is called an inference step.

In Table 1 we present typical examples of systems of homogeneous and heterogeneous productions, indicate the subject area, the formal theory that acts as the theoretical basis, decipher the formula (\*), as well as the goal and (if any) the problems that arise. In some places we link to what we consider to be worthy sources (including paragraphs of this book).

Table 2. Examples of product systems

 
| Subject area and link || Mathematical basis and goal || Product type and format |
| --- | --- | --- |
| Analyze \[5\] || Normal Markov algorithms,automatic recognition || Homogeneous, chain  chain |
| computer algebra || term replacement systems,expression reduction || Homogeneous concept  concept |
| computer models || Intuitionistic propositional calculus, program || Homogeneous, arguments  results |
| systemsinference\[6\] || Calculus of first-order predicates, proof of the theorem || Homogeneous, predicates  predicates |
| expertsystems (section1.1.3) || No basis, diagnosis || Heterogeneous, symptoms  diagnosis |
| control systems || No basis, homeostasis or other control objective || Heterogeneous, condition + stimulus   |

We see that there is no generally accepted mathematical basis for inhomogeneous systems. At best, Dijkstra's restrained commands \[7\], which have not become a strict formal theory, can serve as a justification for second-class systems.

#### 2.1.2. The structure of the system of heterogeneous products

emergence of production systems. As already mentioned, (or almost all) applied systems with AI elements reflect (model) some aspects of human thinking to some extent . Product systems are no exception. Initially, the approach was used in building so-called expert systems (see Section 1.1.3), which mimic the behavior of an expert in a particular specialty when solving various situations, be it making a diagnosis for a patient, a conclusion about the feasibility of the development of a mineral deposit (based on geological exploration data) or something else. A person solving such problems tends to build chains of syllogisms [\[26\]](#part0005.xhtml#_ftn26). This way of thinking in everyday life is often referred to as deductive. It was he who brilliantly owned and successfully used one of the greatest literary detectives - an expert in the field of solving crimes - Sherlock Holmes.

The “everyday” caveat is not accidental – we wanted to emphasize the elements of subjectivity of an expert opinion obtained from an individual. This subjectivity is due to many factors:

\-                     completeness and detail of the anamnesis [\[27\]](#part0005.xhtml#_ftn27)(using medical terminology) - a smoker's cough can cause suspicion of an oncologist, and a non-smoker athlete most likely has a banal acute respiratory disease;

\-                     the experience of an expert - some know that seagulls peacefully walking along the coast portend a storm, others do not even know that the same seagulls swimming in the sea guarantee calm and calm weather;

\-                     the ability to apply knowledge in the most appropriate order (use the best inference strategy!), etc.

The conclusion is often non-categorical (ambiguous) - "The patient is more likely alive than dead" (a medical anecdote, or perhaps not a joke). It often happens that two different experts draw different (sometimes contradictory) conclusions from the same premises – see the example of “orthogonal interpretation” about a Bulgarian man and his girlfriend (Section 1.1.1).

All these features are to some extent inherent in modern computer expert systems that use the production mechanism in implementation.

Formally, a system of heterogeneous productions is an eclectic union of the apparatuses of several independent mathematical disciplines: first-order logic, theory and probability, graph theory, possibly measure theory, and something else ... The axiomatics of most systems of production ( in the part reflecting a particular specialty - see Examples above about a Bulgarian and seagulls) may be contradictory, the conclusions drawn may be unreliable, and the cost of the conclusion may be unreasonably high. Nevertheless (and this is sometimes admirable!) modern expert systems can not only make life easier for doctors, geologists, chemists and specialists of other disciplines, but also "give out" completely unexpected and extremely productive solutions.

It should also be noted that intensive research is currently being carried out to improve the mechanisms for representing and processing knowledge for production systems. In particular, the so-called modal logic is proposed as a logical apparatus (and the probability theory connected to it), which explicitly includes the quantifiers possibility, certainty and personification of knowledge as well as the recognition of the property of the non-monotony of the conclusion and the semantics of possible worlds (see Fig.

\[9, 10\]).

The production system (SP) is determined by four: the fact base, the production quantity, the control system, the condition for completing the preparation of an expert opinion.

In this book, the database is systematically denoted by the letter D , the production quantity by R , the control strategy (system) by C and the termination condition by t . Once we have the notation established, the above definition can be rewritten in standard mathematical form:

SP = < D , R , C , t \> .               (\*\*)

The termination condition must not be specified, so below we give some explanatory comments on the last element of the four.

So we see that application systems with elements of artificial intelligence, based on the formalism of productions, have a clear division into three parts mentioned in the previous chapter (see section 1.3.4):

\-                     factual knowledge (a fact base usually implemented in the form of a database);

\-                     algorithmic knowledge (rules);

\-                     conceptual knowledge (management strategy).

This is why product systems generally reflect AI applications so well. Let's take a closer look at the elements of the production system. 

Many products R. \_ The elements of this set are usually called production rules or production rules or simply productions .

Heterogeneous Production (Production) is a "condition - action" pair that establishes part of the knowledge required to complete a step of preparing an expert opinion. The production rule can be written as: r \= def if p ( d ) then d := f ( d ) end if, (\*\*\*) 

where p is the condition and f is the action.

Then the rules look like this:

R \= { r | r \= ( p , f \[, w \]) } .

The conditional part of the rule p determines when this rule can be applied depending on the state of the environment (fact base). The implementation of p is usually determined by the truth or falsity of the predicate about the set of facts reliably established at the given point in time. The production part f defines the mapping f : D  D and defines the effect on the environment [\[28\]](#part0005.xhtml#_ftn28). Sometimes a real number w is used that characterizes the price (or weight, -weight ) of the application of the rule. In this case, one can set oneself, for example, the task of not only finding an order of application of products that leads to the goal , but an order with a minimum total price.  

fact base D contains a description of the current state of the "world" in the process of thinking. This description is a template that is compared to the condition part of the product to select the appropriate actions to resolve the issue. If the current content of the database meets the condition of a rule, the action specified in that rule can be taken. In such a case, the rule applies . But the ability to apply a rule does not mean that it must be applied. Whether the applicable rule is actually applied is determined by the rule strategy.

If the rule is applicable and the control strategy selects it, the rule is applied. After applying the rule, the database changes its state.

management strategy C. \_ The control structure of a production system is simple: the fact base is initialized with an initial task description. The current status of problem solving is also reflected in the fact base. The current contents of the fact base are matched against the conditions of the production rules, generating a subset of applicable rules, sometimes called the conflict set [\[29\]](#part0005.xhtml#_ftn29). Next, one of the productions r  R Conflict set (conflict resolution is performed) and action f this rule is performed. As a result of applying the rule, not only does the state of the fact base change, but possibly the conflict set as well. The fact is that after changing the state of the database, the conditions of some rules may no longer be met, and these rules will have to be excluded from the conflict set. On the other hand, the conditions of previously unenclosed rules can become true and must be enclosed. At the same time, conflict resolution strategies (control strategies ) can be both quite simple, for example choosing the first applicable rule, and quite complex, for example using complex heuristics. According to the rule strategy, the rules are applied, for example, until either the end condition is reached or there are no more applicable rules.

end condition t . There is usually a condition for the end of the solution process t : D  bool , ie a predicate whose argument is the facts from the database. If the condition t ( d ) is met, then it is assumed that no more products need to be applied and the current state of the database d is the answer. Sometimes the end condition is not given as a formula, but directly as a set of database states that satisfy the end condition. In such a case, this set is commonly denoted by T :

T \= { d  D | t ( d ) } .

It is possible that no end condition is specified because the system must run continuously. These are, for example, automatic control systems for technological objects and continuous processes. Here it makes sense to place the explanation promised above about the last element of the quadruple in the formula (\*\*). The last element, the much-discussed termination condition for t , cannot be removed from the dataset (because of the mathematical "constraints" in place), so we agree that for the production systems discussed in this paragraph, the constant holds Action, let's just assume that t is equal to false .

Having discussed the components of production systems, we turn to the structure of the production system as a whole. The organization of an applied AI system in the form of a product system has a very important advantage – the modularity or algorithmic nature of the knowledge. The difference between a production system and hierarchically organized programs is as follows.

1.               There is no direct relationship between the rules in terms of control . In other words, the rules don't call each other. All control of the rules is placed in control strategy C.

2.               According to the data, there is no direct link between the rules . The rules don't say anything, all the data is in database D .

An important conclusion follows from this – the rules are functional and information-rich modules .

In an applied system with elements of artificial intelligence, modularity is crucial, since in such programs the action algorithm is often not clear in advance. So you need modifiability to try different ways to solve the problem. This is exactly what can be achieved with production systems, since we can add and remove rules in set R without affecting the other rules in any way! In addition, in the limit one can dynamically modify the set R , directly in the process of solving the problem.

Glenford Myers recommends only the two highest strength classes of modules for use in software development.

A functionally strong module is a module that only performs (implements) a specific function.

Such a module can use other modules when implementing this function.

An information-persistent module is a module that performs (implements) multiple operations on the same data structure (information object) that is considered unknown outside of that module.

For example, an information-safe module can implement an abstract data type or class in object-oriented programming.

A module's cohesion is a measure of its data dependency on other modules.

The coupling of modules is characterized by the type of data transmission. The weaker the coupling of a module with other modules, the stronger its independence from other modules. To assess the degree of linkage, Myers proposed an ordered set of different types of module linkages. The worst type of module chaining is content chaining . This is the concatenation of two modules when one of them has direct references to the content of the other module (e.g. to a constant contained in the other module). This type of module coupling is not recommended. Shared area chaining is a concatenation of modules where multiple modules share the same memory area [\[30\]](#part0005.xhtml#_ftn30). The best type of module chaining recommended for use by modern programming technology is parametric chaining \- this is the case when data is passed to one module, either when accessed as argument values, or as a result of calling another module to evaluate any function. This type of module chaining is implemented in programming languages by calling procedures and functions.

#### 2.1.3. Algorithm of the system of heterogeneous products

Imagine a kind of AI application that returns the simplest result, namely only a yes/no answer (level 0, see Section 1.3.5.) corresponding to whether the termination condition t ( d ) is satisfied or not. At the same time, we believe that the order in which the rules are applied is not of interest to us. The positive answer "yes" is referred to as OK in the programs below , the negative answer as "no" - not passed . In this case, the operation of the production system is stopped by the algorithm error               !               The text               of the specified style does not exist in the document. .one.

Algorithm error ! The text of the specified style does not exist in the document. .one. Interpreter for production systems.

proc production(d, R , t ) during  t (d) do  

r := selection(d, R )

  when r = zero then Return ( Fail ) end if                d := rf (d)               end while                return ( OK ) end perc 

This algorithm takes as input the initial state of the base d , the set of productions R , and the termination condition t . Furthermore, until the termination condition is met, the applicable rule is selected with the Select function and the status of the database is changed with its help until the termination condition is met. If no applicable rule is found, the process is aborted and a negative response is returned.

The Select function is the heart of this system, it determines the choice of the applied rule, i.e. the strategy of the production system C. Usually in an artificially intelligent system there is not enough information to apply the best rule at each step. Therefore, the process of selecting a rule is a search process .

For example, the crudest search strategy is the "first fit" presented in the Error! algorithm. The text of the specified style does not exist in the document. .2. Examples of more elaborate strategies are given below.

Algorithm error ! The text of the specified style does not exist in the document. .2. First-Fit Rule Selection Strategy.

procSelect (d, R )

 for r  R do   if rp(D) then return (r) end if                End to the                return ( null ) end perc 

This is a good example of a bad strategy. It's hard to expect intelligence from a machine unless we put some of our own intelligence into it . 

Let's take a closer look at the production system from an algorithmic point of view. In fact, the algorithm error! The text of the specified style does not exist in the document. .1 We have defined and documented a way of interpreting knowledge presented as a series of productions. Algorithm error! The text of the specified style does not exist in the document. .1 is purely mechanical in nature, it has no signs of "intelligence", neither artificial nor natural, it simply executes a set of rules R on the input data d , without any analysis of the base's state change history, without evaluating whether we are moving towards or moving away from a solution. Ordinary computers behave the same way: they mindlessly run the embedded program and don't try to understand if what they're doing makes sense at all. In other words: algorithm error! The text of the specified style does not exist in the document. .1 is an emulator virtual machine, and the set of R rules is a program for that machine. The select function has a special place . In this function lies the "intelligence", i.e. conceptual knowledge in the terminology of section 1.3.2. This function is intended to direct the calculation process (basic transformations) to a solution, while the algorithmic knowledge concentrated in the set of rules R lives separately and is not responsible for anything.

#### 2.1.4. Production system as a logical calculation

The word "production" in artificial intelligence itself comes from logic and not in the most direct way. The rule of production or inference is a logical rule that says that if we have premises of a certain type, then a conclusion follows, also of a certain type. For example, the modes ponens rule states that the conclusion is true if two premises are true: the statement A and the implication that says B follows from A

B. \_ In formulaic notation, such a rule is written as follows:

A , A  B

B

From the point of view of mathematical logic, the production system can thus be viewed as a formal theory (the concept of a formal theory is described in detail in Section 4.1.1). In this formal theory:

\-                     the initial fact base is part of a set of axioms (problem-oriented [\[31\]](#part0005.xhtml#_ftn31)) of a formal theory of the form  A ( c 1 ,..., c k ), where A is a predicate symbol (usually associated with a property of objects of the subject under consideration) - and all c i are constant terms;

\-                     Products is an addition to a number of problematic

oriented axioms in an implicit form of the form  d & p ( d )  

M ( f ( d )), moreover, the predicate p over the fact set d is a kind of “trigger” of production, and the notation M ( f ( d )) sensibly means that the execution of actions occurs on the fact basis D (base modification ) is initiated, defined by the function f : D  D , and successful execution of these actions sets the predicate M () to true ;

\-                     the only rule of inference is the rule Modes ponens already mentioned;

\-                     Intermediate states of the fact base are sets of formulas obtained from problem-oriented axioms as a result of modifications of the base D ;

\-                     the state of the database that satisfies the termination condition is the objective theorem to be proved in the given formal theory.

Thus the solution of a certain problem with the help of a production system can be treated as a search for a proof of the corresponding theorem in a special formal theory. This interpretation of production systems reinforces the observation made in Chapter 1 (see Section 1.1.5) that the vast majority of AI problems can be treated as theorem proof problems .

All of this would be fine if there wasn't a "but"! Practically not a single result in the field of AI can do without such “buts”, even taking into account the limitations we made in the introduction and the first chapter. The heterogeneous production systems listed in Section 0, in addition to the deficiencies identified there, create additional (and significant!) headaches for developers and users, both because of the heterogeneity and the domains for which they are designed. The fact is that in a given situation the facts are not absolutely true, and the application of this or that rule is only partially justified. Let's refer to the same medical diagnostics [\[32\]](#part0005.xhtml#_ftn32). Based on the observed reddening of the rainbow and a slight increase in temperature, do you think it is possible to say with absolute certainty that the patient has, for example, blepharitis? - Of course not! Such a conclusion is permissible only with a certain probability (in production systems, the terms “reliability coefficient”, “validity”, “trust index”, etc. are used for this and these coefficients are processed, sometimes in the most incredible way). Let's say more - the validity of the application of a particular product to the current state of the environment is also not absolute.

On a more formal level, let's explain the application of one of the currently popular techniques for working with partially reliable information. Let Q 1 ( a 1 ),…, Q n ( a n ) be facts from a certain d  D , v i , i \=1,…, n are the values of the validations of these facts from the domain (0,1) , and v r from the same domain is the validity (of the application!) of production r of the form (\*\* \*). The modifying component of the production rf in real systems is generally determined by a function, which of course takes arguments (be they facts Q i ( a i ), i \=1,…, n ) and a result (let's say Q 0 ( a 0 )). The problem is to determine the validity of the modified fact Q 0 — the value v 0 .

Draw               the reader's attention to the use of the word

"modified" - rf can not only add/remove a fact, but also increase/decrease the reliability of an existing fact! If a fact is deleted from the database, there are no queries. Discussion of the actual change, the previous value of the validity of the fact Q 0 we denote by v 0( pred ) .

Most commonly, certain combinations of minimax and probabilistic estimates are used to determine new reliability values. The first (and perhaps the worst) thing that can come to mind is to assign a sign of appropriateness to a new (added) fact as a minimum (rarely maximum) v 0 \=MIN( v 1 ,v 2 ,…, v n ,v r ) , the reliability of the modified fact is calculated in this approach by the formula: v 0 \=( v 0( pred ) +MIN( v 1 ,v 2 ,…, v n ,v r ))/2 .

Using a probabilistic apparatus looks more attractive, while the validity of a new fact can be defined as a conditional probability v 0 \= P ( g ( v 1 ,v 2 ,…, v n )| v r ) = v r \* (1– g ( v 1 ,v 2 ,…, v n )), where g is a more or less reasonable function not exceeding the range (0,1), it can be MIN or MAX, arithmetic mean, weighted average [\[33\]](#part0005.xhtml#_ftn33)or still more exotic options. The methods for determining the reliability of a modified fact are just as varied. We note a very important circumstance - we cannot speak of the reliability of a certain state of the fact base as a whole (integral) \- it is the same as calculating the "average temperature in the hospital".

In recent years, developers have increasingly sought a more rigorous (and consistent) formal basis for dealing with heterogeneous products. There are known attempts to use fuzzy logic \[11\], descriptive logic \[12\] and other theories.

The laudable claim of the developers of applied product systems is almost completely belied by the fact that the assessments of the reliability of the initial facts and rules in a given subject are not themselves reliable - they are given by experts (persons with considerable experience, but still people!) , which, as you know, are "fallible". No matter how thoughtful and balanced the implementation of the system with AI elements is, and no matter how strong and rigorous the theoretical foundation it is based on, but if the source material is not fully reliable and has a touch of subjectivity , then the solution has been found will also have the character of a possible (but not absolute !). This thesis is perhaps one of the most important in the book, and if the reader learns it, it will help to avoid the deepest disappointments in the future and to feel safe in the "boiling waters of the ocean of artificial intelligence"!

#### 2.1.5. game at eight

The effectiveness of the artificially intelligent system is primarily determined by how well the knowledge representation is chosen for all components D , R , C. Here we look at some examples of simple puzzles, focusing on good and bad knowledge representation choices.

Consider the game of eight (an example is taken from the book \[13\]), which is known to many in analogy to the well-known game of fifteen. The essence of the game is to move the chips numbered from 1 to 8 so that they are in ascending order in a clockwise direction. In this case, one of the squares of the 3  3 square is always free, and any adjacent chip can be moved to it. Chips cannot "jump" over each other - they can only be moved to an adjacent free space.

Suppose we have the following source (left) and destination (right) positions shown in Fig. Error! The text of the specified style does not exist in the document. .14 .

 
|  

 
| 2 || eight || 3 |
| --- | --- | --- |
| one || 6 || four |
| 7 ||   || 5 |

 ||   ||    |
| --- | --- | --- |

 ![](Images/image00337.jpeg)

 
| one || 2 || 3 |
| --- | --- | --- |
| eight ||   || four |
| 7 || 6 || 5 |

 

 

 

 

 

 

 

 

 

 

 

 

Fourteen. Starting and finishing position of the eight game

Imagine knowledge of the game of eight based on production systems.

The representation of the database offers itself from the physical sense. Let's call an empty cell a chip number 0. As a result, D looks like this:

D : Array \[1..3,1..3\] from 0..8

R rules are also written as expected. For example, the rule “move chip 1 down” is:

if D\[i,j\]=1 & i<3 & D\[i+1,j\]=0 then D\[i+1,j\]:=1;

D\[i,j\]:=0

Due to the fact that each of the eight parts can be moved in a maximum of four directions, there are a total of 32 rules. This is a natural but not the best representation of knowledge about the game.

Let's try to improve the original version. The basic idea is that every movement of a chip can be viewed as a movement of an empty cell. This is where we use a little of our intelligence.

a few more numbers {i,j} to the database - the coordinates of empty space. Let's determine the directions of movement according to the cardinal points - north, west, south and east.

if i > 1 then D\[i,j\] := D\[i-1,j\]; i: = i-1 ( ↑ N to the north) if j < 3 then D\[i, j\]: = D\[i, j + 1\]; j: = j + 1 ( → E in the east) if i < 3 then D\[i,j\]: = D\[i+1,j\]; i: = i + 1 ( ↓ S on юг) if j > 1 then D\[i,j\] := D\[i,j-1\]; j: = j-1 ( ← W West)

As a result, a knowledge representation for the game of eight was created, in which there are only 4 rules instead of 32. This is a fundamental result, because the number of rules n (4 or 32) is the argument of the exponential search function for finding a solution. For n \= 4, the power of an average computer is probably sufficient to quickly perform an exhaustive search and find a solution, but for n \= 32, it may not be sufficient.

#### 2.1.6. Farmer, wolf, goat and cabbage

The second example is a known problem with a farmer who needs to transport a wolf, a goat, and a cabbage to the other side so they don't eat each other (Fig. Error! The text of the specified style is missing in the document. .15 ). A pawn may not take more than one item into the boat.

![](Images/image00338.jpeg) 

Rice. Mistake!               Text of the specified style in the document

absence. .fifteen. Farmer, wolf, goat and cabbage: problem statement

Of course, this task can be simplified. The idea is that the farmer and the boat are indistinguishable and form a whole. You can also consider any coast-to-coast movement to be instantaneous. Let's renumber the objects: 0 - farmer, 1 - wolf, 2 - goat, 3 - cabbage. The presence of an object on the right (destination) bank is denoted by "1", on the left (source) by "0". In this case it is obvious that the database D should have the form

D : array \[0..3\] of 0..1

At the same time, D\[0\] is the position of a farmer, D\[1\] a wolf, D\[2\] a goat, and D\[3\] a cabbage. We write the array D in the form of a four-digit bit scale. For example, 0101 means that a farmer with a goat is on the left bank and a wolf with cabbage is on the right bank. Then the initial state of the base is d 0 \= 0000 and the goal state is d k \= 1111 .

What should the rules look like? Approaching the solution of this problem directly, we can argue as follows. There are a total of 16 possible base states [\[34\]](#part0005.xhtml#_ftn34). Consider pairs of states of basis such that it is possible to go from the first state to the second in one go. For example 1011  0011 - a pawn swam from the right bank to the left. It is easy to see that there are 16\*4=64 such pairs. Note that some basic states are valid, e.g. 0101 , while other states are invalid, e.g. B. 0011 - the goat eats the cabbage. It is easy to verify that there are 10 valid states and 6 invalid states. Let's discard those pairs of states where the target state is invalid. The remaining pairs, and there are 40 of them, are the rules of our system.

It is easy to see that this is purely mechanical, formal work that can be entrusted to a computer. However, the result will not be very good (four dozen rules). Such a representation of knowledge cannot be called successful.

Let's try to be creative. Creativity, in this case, consists of attracting general knowledge that was not contained in the original problem statement.

1.               If the initial state is valid and all rules remain valid, then every reachable state is valid (principle of complete induction).

2.               In order to solve this problem, it suffices to consider only permissible states of the basis (invalid ones cannot be included in the solution even in intermediate stages).

Note that the initial state is legal (as is the final state). It remains to single out the rules that will preserve admissibility. To do this, we note that there are essentially only four possible moves in the problem: moving a pawn without an object, moving a pawn with a wolf, with a goat, and with a cabbage. Now it remains to write down simple conditions for the admissibility of these moves and to obtain a set of rules R :

 
| if D\[1\]<>D\[2\] & D\[2\]<>D\[3\] || then D\[0\]:= 1 - D\[0\] |
| --- | --- |
| if D\[2\]<>D\[3\] & D\[0\]=D\[1\] || then D\[0\]:= 1 - D\[0\]; |
|          ||  D\[1\]:= 1 - D\[1\] |
| if D\[0\]=D\[2\]   || then D\[0\]:= 1 - D\[0\]; |
|         ||  D\[2\]:= 1 - D\[2\] |
| if D\[1\]<>D\[2\] & D\[0\]=D\[3\] || then D\[0\]:= 1 - D\[0\]; |

               D\[3\]:= 1 - D\[3\]

So in this case, a creative approach to the problem improved the representation of knowledge tenfold.

#### 2.1.7. Knight's move

In chess, a knight can move in a "G" pattern - two squares horizontally or vertically and one square in a vertical direction. At the same time, it should not go beyond the limits of the chessboard. Thus, in the most general case, there are at most eight possible moves of the knight from those given

positions (![](Images/image00339.jpeg) 

Rice. error ! The text of the specified style does not exist in the document. .16 ). When the knight is on the edge of the board, there are fewer possible moves.

![](Images/image00339.jpeg) 

Rice. Mistake!               The text of the specified style in the document

absence. .16. Possible knight moves

The traditional formulation of the problem is to find such a sequence of knight moves, starting from any square, that the knight enters each square of the board only once.

Then the database D looks like this:

D : Array \[1..8,1..8\] of 1..0, where D\[i,j\] = 1 means that the knight was on square (i,j) and 0 was not.[\[35\]](#part0005.xhtml#_ftn35)  

Then the initial state of the base D is 0 \- all elements of the array D are zeros and the target state D k \- all elements of D are ones.

Let's calculate how many different knight moves there are in chess (on an empty board). There are 8 moves for each of the 16 squares in the middle of the board. For the squares of the adjacent layer - 6 moves each, except for squares b2, b7, g2, g7, in which there are only 4 moves.

Furthermore, 4 moves are possible from the squares at the edge of the board, with the exception of the corner squares, of which there are only 2 moves, and squares a2, b1, a7, b8, g8, h7, h2, g1, from which the knight moves to 3 others can jump fields. In total we have: 16\*8 + 16\*6 + 4\*4 + 16\*4 + 8\*3 +4\*2 = 336 knight moves.

Obviously there is no point in numbering all possible moves and comparing rules with them: there are too many of them. Let's replace real moves with a series of eight productions that produce legal moves of the knight led by

![](Images/image00339.jpeg) 

Rice. error ! The text of the specified style does not exist in the document. .16 . At the same time, we can introduce directly into the rules a check of the condition of the problem that the knight can enter the given square only once. The current coordinates of the jumper are stored in the variables i and j .

if i <= 6 & j <= 7 & D\[i+2,j+1\] = 0 then D\[i+2,j+1\] = 1 & i = i+2 & j = j+1 if i <= 7 & j <= 6 & D\[i+1,j+2\] = 0 then D\[i+1,j+2\] = 1 & i = i+1 & j = j+2 if i >= 1 & j <= 6 & D\[i-1,j+2\] = 0 then D\[i-1,j+2\] = 1 & i = i-1 & j = j+2

if i >= 2 & j <= 7 & D\[i-2,j+1\] = 0 then D\[i-2,j+1\] = 1 & i = i-2 & j = j+1 if i >= 2 & j >= 1 & D\[i-2,j-1\] = 0 then D\[i-2,j-1\] = 1 & i = i-2 & j = j-1 if i >= 1 & j >= 2 & D\[i-1,j-2\] = 0 then D\[i-1,j-2\] = 1 & i = i-1 & j = j-2 if i <= 7 & j >= 2 & D\[i+1,j-2\] = 0 then D\[i+1,j-2\] = 1 & i = i+1 & j = j - 2 if i <= 6 & j > = 1 & D\[i+2,j-1\] = 0 then

 D\[i+2,j-1\] = 1 & i = i+2 & j = j-1

saving over the "frontal" approach

336:8 = 42 times.

### 2.2. MANAGEMENT STRATEGIES

variety of control strategies can be proposed for production systems. The most important observation is that there is not and cannot be one best management strategy for all occasions. The same strategy can work well for one class of problems and be totally unsatisfactory for another .

In anticipation of the main material of the section, we will make a number of comments. At first glance, these remarks may seem insignificant, but we consistently try to adhere to the principle of necessity ( necessity , usefulness ) of all the material contained in the book - this applies equally to annotations, additions and jokes in the text.

Let's talk about the naturalness of terms, the uniqueness of definitions, and the uniqueness of interpretations. Let's start perhaps with graphs, more specifically with a class important for understanding the subject matter of the book called the class of oriented trees. Let's ask ourselves where the tree grows - above or below ? Of course, the first answer that comes to mind is "up," but is that so obvious and correct? What if you are upside down (changing the coordinate system)? or remember the roots [\[36\]](#part0005.xhtml#_ftn36)(look at the big picture)? Finally, you can easily redefine [\[37\]](#part0005.xhtml#_ftn37)the concepts of top and bottom, mutually changing their meaning (e.g. based on convenience [\[38\]](#part0005.xhtml#_ftn38)in representing an object of previously unknown size).

There are countless examples of this kind [\[39\]](#part0005.xhtml#_ftn39), and all of them convince only by one thing – the directions (as well as their naming ) are very relative, and whenever this is not clear from the context, it is necessary to fix frames of reference.

Armed with these observations, let's return to output control strategies. Remember that these are production systems where the base object is an expression of the form (\*). In the production log p  q There is a symbol “  ” that in a way defines the reporting system: the movement from arguments to results (from data to target) is, so to speak, in the forward direction and from target to data in the opposite direction respectively. Such a classification of strategies is typical, first of all, for the following areas of artificial intelligence: expert systems, automatic program synthesis, verification systems and a number of others. At the same time, in the more "basic" area of automatic theorem proving (also called logical programming), the opposite classification is adopted: goal-oriented strategies [\[40\]](#part0005.xhtml#_ftn40)(from goal formula to axioms) are called direct, and those that lead from axioms to goal statement are called inversions. The latter include an extremely interesting and promising inverse method proposed by the Leningrad logician S.Yu. Maslow \[16\].

Therefore, we can assume (with some assumptions, of course) that the inverse Maslov method and the direct wave implement the same strategy, despite the radical difference in the names.

#### 2.2.1. Criteria for comparing strategies

Since the strategies are different, criteria are needed to compare them. There are also many comparison criteria that we present here that appeal to us.

Some control strategy options are shown in Fig. Error! The text of the specified style does not exist in the document. .17 . Two criteria are used here:

\-                     what proportion of the information already obtained during the search for a solution is stored for later use;

\-                     to what extent returns are allowed (the database is not transferred to a new, but to one of the old states).

Note that these criteria are not actually completely independent. In fact, in order to return the base to one of the already passed states, it is necessary at least to store information about the passed state.

17\. Control strategy options

Obviously, the previously given "First Fit" strategy (see Section 0, Algorithm 2.2) is the simplest and corresponds to the bottom left corner at the strategy level in Fig. Fehler! The text of the specified style does not exist in the document. .17 . This strategy belongs to the group of irreversible search strategies .

In addition to irreversible search, this book covers two other popular groups of strategies:

1.               Search on the graph where all the available information is stored and any return is possible, even to the initial state.

2.               Backtracking is an intermediate option that preserves some information but not all, and uses backtracking but is not arbitrary.

Any strategy can be evaluated on two criteria - the cost of choosing the rules and the cost of applying the rules. In this case, of course, two extreme cases are possible - a stupid but fast strategy and a clever but slow strategy. Too quick a strategy doesn't spend a lot of time picking rules, but immediately runs ahead and applies them. But perhaps this is a run in the wrong direction, leading to an increase in the cost of aimlessly applying the rules. Too smart a strategy measures seven times before truncating and applying the rule. Maybe this is a good rule that goes straight to the point, but what's the cost of taking your time before picking it? As always , there is a happy medium where the overall complexity of the process is minimal (Fig. Error! Text of the specified style is missing from the document. .18 ). The point is that in both cases the costs do not grow linearly, but rather faster, that is, the cost functions are convex downwards, as in Fig. Fehler!

The text of the specified style does not exist in the document. .18 , so the sum of such functions necessarily has a minimum. The whole art of a successful strategy is to find that minimum in each and every case .

![](Images/image00340.jpeg)

stupid smart

number of examples

 

Eighteen. Components of the cost of applying the management strategy

#### 2.2.2. irreversible search

Irreversible search , as the name suggests, is such a search algorithm when we don't go back to previous states of the database, which means we can't store any information about those states.

The simplest case of an irreversible search is the "first fit" strategy described in section 0 above. In this case, the search is blind, random, and the result depends significantly on the order in which the rules are passed through (and therefore applied) in the check. If we don't know anything about the problem and the search space is large, we shouldn't expect the first fit strategy to give a good result.

As in other cases, you can introduce a rating function in an irreversible search F : D   \+ , where  \+ is the set of nonnegative               real numbers. The               F ( d ) record is an               estimate of the state of the database d . The function F is chosen in such a way that the function at the end nodes (those states of the base where the termination condition is met) assumes the minimum value t ( dk )= def F ( d k ) = min { d  D | F ( d )}.

Select function that implements the first-fit-reduce-estimation strategy, as in Algorithm Error! The text of the specified style does not exist in the document. .3 . It is clear that such a strategy is at least as good as the "first fit" strategy, and if the evaluation function is well chosen, then such a strategy will be much better.

Algorithm error ! The text of the specified style does not exist in the document. .3. The strategy for selecting the "fit first, reduce guess" rule. proc Choose (d, R ) for r  R do 

if rp(d) & F(rf(d)) ≤ F(d) then  

 return (r) end if 

 End to the  return ( nil ) end proc

It is possible to improve the method by choosing a rule that not only reduces the estimate, but reduces it the most. Such a strategy is often called the steepest descent method or the gradient method , which belongs to the class of greedy search algorithms. The algorithm error! The text of the specified style               does not exist in the document. .four               The simplest implementation of the steepest descent method is presented.

Algorithm error ! The text of the specified style does not exist in the document. .four. The strategy for choosing the rule "the fastest descent".

proc Select (d, R ) m := F(d) r' := nil                for r  R do                              if rp (d) & F(rf(d)) < m then 

 r':= r

 m := F(rf(d)) end if end for               return (r') end proc

It is known from computer mathematics that methods of this type have a significant disadvantage - sometimes local minima and plateaus can occur when searching for a solution, which are generally difficult to recognize, which requires very complex calculations. Once in a local minimum, the steepest descent method will stop there without finding a solution. Once on a plateau, the method results in aimless random walks across the plateau.

The method of steepest descent works well when the estimator is unimodal , i.e. when it has a single global minimum and no plateau. But in order to choose a unimodal scoring function one needs to know the properties of the search space fully, and they are usually unknown .

Consider an example. In a game of eight we take the evaluation function F \- this is the number of stones that are not in place. As a result, the search graph for this game looks like this (Fig. Error! The text of the specified style is missing from the document. .19 ).

![](Images/image00341.jpeg)

 

19\. Scoring function F : Number of stones out of place

Here the nodes of the graph represent the states of the database and the numbers in the nodes are the value of the evaluation function in the given state.

In this case, the rating function proved to be very successful - the fastest search method quickly found a solution. But there is an element of luck here: from a node with a score of 3, the search went north instead of west, simply because the north rule ended up before the west rule in our rules list.

#### 2.2.3. reverse search

Irreversible search implies that if an inappropriate rule is applied, the solution will either become fundamentally impossible, or the search process will be significantly slowed down. You can base the search algorithm on the following idea: If it is clear from the current state of the database that if you continue with the solution you have started, either no solution can be found or this search promises to take too long, then you can try to go back and do it on a to try another way.

A search strategy that involves backtracking and applying a different rule when applying the rule is inappropriate is called backtracking [\[41\]](#part0005.xhtml#_ftn41).

Consider the backtracking procedure (Algorithm Error!

The text of the specified style does not exist in the document. .5 ).

Algorithm error ! The text of the specified style does not exist in the document. .5. Backtracking search method for the product system.

proc Backtracking (d, R , t ) if t (d) then return ( OK ) end if                if Deadend (d) then return ( fail ) end if                R' := Alles auswählen (d, R)                für r  R' tun 

  if Backtracking (rf(d), R , t ) = OK then return ( OK )

end if 

end for return ( error )

end process

The idea of the backtracking search method is very simple and consists of the following. If any of the termination conditions are met, work must stop and the result returned. Otherwise, you should determine the set of rules in effect in that state (conflict set, see Section 0) using the SelectAll function . Next, the same backtracked search procedure is recursively referred to in a loop according to the applicable rules, but using the state obtained after applying the selected rule as the database state.

It is advisable to include the deadend function in this process - breaking up "dead" paths (dead ends), otherwise the program may loop.

The deadend procedure can check a variety of conditions, for example:

\-                     Correspondence of the current state of the database D with that previously created;

\-                     search depth limit etc.

An example of a reverse search for the wolf, goat, and cabbage problem is shown in Fig. Fehler! The text of the specified style does not exist in the document. .20 . In this figure, the nodes from which the return is made are marked in gray because they are identical to the nodes already built. We should also mention node 0001 separately, this is a dead end node - it is impossible to continue the search from there. Fortunately, there is no need to continue, because. At this point, the algorithm finds the destination node 1111.

![](Images/image00342.jpeg)

 

Twenty. Tracing for the wolf, goat and cabbage problem

Here the Deadend function is used to check if the new state of the database matches what was previously created on this path.

Various modifications of reverse search are known. For example, if not all are saved during the search, but only the most important states of the database, and the return is not one step, but several steps back to the last saved state.

When searching with backtracking, the tree is traversed and not the entire tree is saved, only the currently constructed path in this tree. Moving down the tree corresponds to recursive calls. Upward movements correspond to yields. On fig error! 

The text of the specified style does not exist in the document. .21 shows a fragment of a search tree with returns for the knight move problem.

![](Images/image00343.jpeg)

 

  .21. Fragment of a backtracking search tree for the knight's move problem

We place the knight on any square of the board. In this case the angular field a1 is taken as the first field. We alternately arrange the knight on different squares, looking for one where the horse was not before. If there are no such fields at all, we return to the previous field and so on.

Note that the actual structure of the rules involves storing information about the squares of the board that the knight has already visited (see Section 0). Therefore, here in the Deadend function there is no need to check whether the new state of the database matches what was previously created along this path. At the expense of storing some additional information in the database, the computational load of the backtracking procedure can be reduced .

#### 2.2.4. Look in the graphic

Graph search belongs to the group of informed strategies that store all available previously obtained information. A so-called search graph is created for this purpose.

The search graph is a directed graph G(V,E) in which the set of vertices V is the set [\[42\]](#part0005.xhtml#_ftn42)of database states and the set of arcs E is the set of rule applications.

This graph has an initial node d 0 and a set (possibly empty) of terminal nodes T \= { d  D | t ( d )} . The elements of the set of terminal nodes are denoted by d t , d t  T . arc from node d 1 to node d 2 is executed if and only if there is a rule that is applicable in state d 1 and, because of its application, transitions the basis to state d 2 .

d1 → d2 \_  E   r \_ R ( rp ( d 1 ) & rf ( d 1 ) = d 2 ). 

In the general case, the search graph can contain cycles, loops, multiple arcs. It may not be related etc.

To search in a graph, the following two main methods are used, which are specified in the algorithms: Algorithm error ! The text of the specified style does not exist in the document. .6 Algorithm error! The text of the specified style does not exist in the document. .7 :

Algorithm error ! The text of the specified style does not exist in the document. .6. The main search method in the graph.

proc GraphSearch(d, R , t )

 O := {d} { list of "open" nodes } C :=  { list of "closed" nodes }               while  t (d) do                d := select (O)

  when d = zero then return ( fail ) end if               Open (d, R );               end during                return ( OK ) proc. break up

Algorithm error ! The text of the specified style does not exist in the document. .7. Node Disclosure Procedures.

proc Open (d, R ) for r  R do 

  if rp(d) then 

   if rf(d)  O & rf(D)  C then 

 O := O + rf (D) end if   End if End for O := O - {D}

C := C + {D} end perc 

Here the + sign means adding an item to the list, and the - sign means removing an item from the list.

List O is traditionally called the list of open nodes (from English Open), and list C is traditionally called the list of closed nodes (from English Close). However, these traditional names can be misleading. In fact, List O is a list of nodes that we haven't opened yet but will open (to open) and List C is a list of nodes that we already have opened and won't reopen (already opened). .

There are two basic ways to search on a chart: breadth-first search and depth-first search.

If the list O is a stack, i.e. the last placed node is selected for expansion, then one speaks of a depth-first search in this case .

a breadth-first search in this case .

Breadth-first search and depth-first search have their advantages and disadvantages.

The main advantage of breadth-first search is that it always finds a solution if it exists . Breadth-first search scans all nodes without exception and gradually moves away from the starting node. On the other hand, if the search graph is infinite or very large, a depth-first search may miss the solution, go deep, and not return.

The main advantage of depth-first search is that it can sometimes be faster . For example, suppose the desired node is a distance k from the starting node. In such a situation, breadth-first search will necessarily first reveal all nodes that are at a distance less than k , and only after that will it begin to reveal nodes at a distance k , among which is the desired one. While depth-first search, if you're lucky, can go to the desired node and uncover the minimum number of nodes on the direct path to the goal (at best, it will uncover a total of k \-1 nodes). In general, it can be shown that a depth-first search finds a solution about twice as fast on average as a breadth-first search. On fig error! The text of the specified style does not exist in the document. .22 clearly illustrates the causes of this phenomenon. In this image, the nodes that will be expanded are highlighted in black, and the curly arrow indicates the order in which the nodes will be expanded. It can be clearly seen that breadth-first search, moving in a spiral, can get close to the solution and get to the "penalty circle", and depth-first search, if lucky, can "stumble" on the solution almost immediately.

![](Images/image00344.jpeg)

.22. Breadth-first search (left) and depth-first search (right)

Notice the innermost if statement in Algorithm 2.7. When solving a problem with the search method in a diagram, there is always a dilemma - to check the duplication of nodes or not? Duplication can occur as the same database state can result from different sequences of rule application. Checking this will take extra time looking for a match, but there will be no duplicate nodes and no extra work to reopen them. If we don't check it, on the contrary we won't waste time checking, but maybe we'll waste time reworking with the nodes we've already met.

Consider breadth-first search for the problem of a farmer, a wolf, a goat, and a cabbage 

![](Images/image00345.jpeg)

  .23. Search graph for the wolf, goat, and cabbage problem with matching nodes

Let us note an important fact. Contrary to popular belief, breadth-first search can form fewer nodes than backward search when searching for matches..20 and Fig. Error! Text of specified style is missing from document..23 .in the first case 14 knots were built, in the second only 10). In other words, breadth-first search on a graph (brute-force search) can be more efficient than backtracking in some cases! 

However, if you do not check the matches, many additional nodes can be created that repeat the existing ones. On fig error! The text of the specified style does not exist in the document. .24 shows a section of the corresponding search graph for this generally infinite problem. Ellipses in this figure indicate extensions of the graph, not shown. Breadth-first search will find a solution, although it takes a lot of unnecessary work, and depth-first search may “miss” the solution.

 

 

![](Images/image00346.jpeg)

 

  .24. Search graph for the wolf, goat, and cabbage problem with no matching nodes

It is impossible to give a general mathematically rigorous recommendation as to whether or not to search for matches. Informally, it can be assumed that if there are few coincidences, it is better not to check them, and if there are many, as in the farmer, the wolf, the goat, and the cabbage problem, then it is better to check it.

Another important observation about the properties of the search graph can be made using the example of the game of eight. As you know, there are 8! = 40 320 possible permutations of eight chips and therefore there are 8!9 = 9! = 362,880 database states (number of chippermutations multiplied by number of empty cell positions). It can be proved that all DB states are divided into two sets: with an even number of inversions and with an odd number of inversions, and the moves necessarily preserve parity. Thus, the search graph for the game of eight consists of two connected components, with each component being strongly connected. If the initial and end states of the basis belong to different connected components then the solution is impossible, and if they belong to the same component then the solution necessarily exists.

We see that in the general case a finite set of rules R implicitly defines a possibly infinite search graph, and it can be either connected or disconnected, contain or not contain cycles. No conclusions can be drawn about the properties of the search graph based on the form of individual rules.

In terms of a search graph, we can figuratively say that a backward search is a probe that we stick into the search graph hoping to stumble upon d t . As a result, part of the diagram is revealed and part of the diagram remains hidden. Graph search is the systematic, incremental manifestation of the entire graph, leaving nothing hidden.

### 2.3. SPECIAL PRODUCT SYSTEMS

Here we discuss various special cases of production systems. Using special properties of special cases can and usually does lead to unexpected benefits.

### 2.3.1 Reverse Production Systems

The production systems considered always started the search from the initial state and worked until the target state was reached as a result. Such production systems are usually (see beginning of section 2.2) called directly . It is logical to do the opposite - apply the reverse rules and move from the target state to the base state. Such systems are often referred to as inverse . There are cases when the reverse system is more efficient, there are cases when the direct (Fig. Error! The text of the specified style is missing from the document. .25 ). Figuratively speaking, it all comes down to where the target is bigger - the bigger target is easier to hit!

25\. Direct and reverse production systems

To compare direct and inverse production systems, consider the following number theory model problem. In this problem you must determine whether a given number can be broken down into given factors.

The target number is 60 and the factors are 2, 3, 5. The direct system looks like this.

d 0 := {2,3,5}, t (d) := 60  d

R := if x  d & y  d & xy  d & xy<61 then d:= d  {xy}

Breadth-first search returns the following results (19 rule applications).

2 3 5                 (original multipliers) 

4 6 9 10 15 25 (products in pairs) 

8 12 18 20 30 50 (second line \*2) 

27 45                  (second line \*3 )

                     (second line \*5 - no new ones) 

16 24 36 40 60 (third line \*2 - goal reached) 

Depth-first search yields the following results (4 rule applications).

2 3 5

15 45 30 60

The reverse system will be like this.

d 0 := {60}, t (d) := 1  d

R := { if x  d & x:2 then d := d\\{x}  {x/2} if x  d & x:3 then d := d\\{x}  {x/3} if x  d & x:5 then d := d\\{x}  {x/5} }

Depth-first search yields the following results (4 rule applications).

60

30 15 5 1

Breadth-first search returns the following results (11 rule applications).

60

30 20 12

15 10 6 4

5 3 2

one

There is only one target and three dates here, so the reverse system yields slightly better results than the direct, but comparable results, as expected.

But if we set ourselves a different, vague goal: Which numbers are less than or equal to 60 can be obtained from the factors 2, 3, 5,               then a system comparison shows a completely different picture. In fact, the direct system is characterized by the lack of a termination condition and must continue until it terminates due to the lack of applicable rules. The accumulated state of the database will be the answer to the question of the problem.

d0 := {2,3,5 }

R := if x  d & y  d & xy  d & xy<61 then d:= d  {xy}

Breadth-first search returns the following results (22 rule applications).

2 3 5                 (original multipliers) 

4 6 9 10 15 25 (products in pairs) 

8 12 18 20 30 50 (second line \*2) 

27 45                  (second line \*3) 

                     (second line \*5) 

16 24 36 40 60 (third line \*2) 

54                   (third line \*3) 

32 48                  (sixth line \*2) 

Depth-first search returns the same results, only the numbers are found in a different order. This follows from the fact that in this case both search types traverse the same graph and visit each node only once. Note that the quantitative results of the extended formulation of our problem practically agree with the results of the original one - in the first case only three nodes were not constructed by the breadth-first search algorithm. That is, in the original formulation of the breadth-first search problem, the direct system was not aimed at the goal, but the system of production solved a more general problem and not the one that was required.

Now let's try to answer the question what numbers less than or equal to 60 can be obtained from the factors 2, 3, 5 using the inverse production system. It is immediately clear that we must ask ourselves 60 times whether the next number is representable. In this case, for example, using depth-first search, the answer is found for each number, and the number of rule applications is minimal = 0 (if the checked number is prime), maximal = 5. On average, about two applications of the rules to one number to check. This means that the reverse system in this case is an order of magnitude worse, and there is no need to overload the book with a boring description of how it works and columns of unnecessary numbers. On the other hand, if you just want to factor the number 60, the inverse system is obviously more efficient.

The conclusion               from this example is as follows: artificial

In intelligent systems, it is very important to consider the details of the tasks. Sometimes it's more important to consider the details than to follow the general principles .

#### 2.3.2. Bilateral production systems

Direct and reverse systems are called one-way systems , since the search moves in strictly one direction—toward or away from the target. However, if there is only one target state and one source state, then the directions are equivalent (e.g. in a game of eight). In this case, you can go from data to goals and from goals to data at the same time and see if there is a common state that indicates a solution has been found. This is the working principle of a two \-way production system .

It is to be expected that when using an uninformed control strategy, the two-way production system will be more efficient than the one-way production system, since fewer nodes will be uncovered overall in e.g. breadth-first search (Fig. Error! Text of the specified style is missing from the document ..26 ) .

![](Images/image00347.jpeg)

 

Rice. Mistake!               The text of the specified style in the document

absence. .26. The advantage of the two-way production system

However, this is not always the case. If very good heuristics are used that purposefully lead from data to goals and from goals to data, but in different ways, then a two-way system may turn out to be worse than any one-way system 

27\. Two-way system with directed heuristics

#### 2.3.3. commutative production systems

A production system with a set of rules R is called commutative if the following three conditions are satisfied:

dD \_ \_ \_ ( r 1\. p ( d ) & r 2\. p ( d )  r 2\. p ( r 1\. f ( d )) ) 

\-                     if two rules apply, the other remains applicable when one is applied;

dD \_ \_ \_ ( r . p ( d ) & t ( d )  t ( r . f ( d )) ) 

\-                     if the goal is achieved, then forever, the application of the rules does not negate the achievement of the goal;

 d  D ( r 1\. p ( d ) & r 2\. p ( d )  r 2\. f ( r 1\. f ( d )) = r 1\. f ( r 2\. f ( d )) ) 

\-                     When two rules apply, they can be applied in any order.

The system of number production considered in section 0 is commutative. Another example of a commutative production system is the game of eight, but the farmer, wolf, goat, and cabbage problem is a non-commutative system.

Note that the third condition, the commutativity condition, does not mean that the order of the rules, i.e. the statement, can be rearranged at will

 d ( r 2nd f ( r 1st f ( d )) = r 1st f ( r 2nd f ( d ))) is false in general. However , the current rules can be applied in any order .

One of the important advantages of the commutative production system is the possibility of always using the irrevocable mode, since the application of the rule does not spoil anything.

set . Every SP can be transformed into a commutative one.

proof . The production system S = < D , R , C \> with the initial state of the basis d 0 is given . Consider its search graph G. We construct a new production system S' =< D' , R' , C' > . The database of system S' becomes the search graph of system S. The rules R' of the new system are different ways to transform the search graph, which can be done with strategy C in the old system (               node expansion). The new production system is commutative.

For real:

\-                     in the old system, if two nodes are in the list O , the expansion of one node does not prevent the expansion of the second node, so the first commutative condition is satisfied;

\-                     in the old system, if a terminal node is built into the search graph, then expanding other nodes will not exclude the terminal node from the graph, so the second commutativity condition is satisfied;

\-                     In the old system, if there are two nodes in the list O , they can be expanded in any order, the same result is obtained, so the third commutative condition is satisfied. Ch.td 

The proven theorem is of little use in practice. Although the resulting new system is commutative, the transformation greatly increases its volume compared to the original one. The gain from using the irreversible search is less than the loss from the growth of the systems during the transformation.

We will support general value judgments with an example of a commutative system for simplifying algebraic expressions, built up of: variable x , natural coefficients, addition, multiplication and power operations (polynomials of one variable). There are a number of transformation rules:

1.               expand brackets 

2.               bring something similar 

3.               Sort by completion 

These rules are well known to everyone at school, so we didn't write them down formally. Let's try to simplify the expression 1 \+ x (1 \+ x (3 \+ x + x )) (Fig. Error! The text of the specified style is missing in the document. .28 ).

![](Images/image00348.jpeg)

 

28\. expression simplification

If the rule changes something, we apply it. With polynomials, the final result does not depend on the order in which the rules are applied. In fact, the production system here contained no conditions - this is an example of a term substitution system or a system of paraphrasing rules (term paraphrasing rules) related to homogeneous production systems.

A term paraphrasing system is a finite set of paraphrasing rules R that defines a binary relation → (reduction relation) on the term set.

The system for rewriting rules R is said to have the Church-Rosser property if, for arbitrary terms t 1 and t 2 , the equivalence t 1 \= t 2 is satisfied , and only if there is a unique term t 3 exists such that t 1 → t 3 and t 2 → t 3 . In this case, the SPT is called complete or canonical , and the result of applying the R-rules to the original formula is called the canonical form .

In this case the system has the Church-Rosser property. This is a very powerful, useful and rare property that allows you to automatically solve many problems, e.g. Eg checking equality, solving equations, etc. However, not all classes of algebraic expressions have canonical forms. There are canonical forms for one-variable polynomials and for Boolean formulas that are likely to be familiar to the reader. At the same time, for example, there is no normal form for elementary functions of mathematical analysis (broken-rational functions, logarithm, exponent and their superpositions) [\[43\]](#part0005.xhtml#_ftn43).

Let us show the essentiality of the Church-Rosser property by a, at first sight, easy complication of the considered example of simplifying algebraic expressions. Let's try to simplify the expression x (1+1/ x ), which should result in x + 1, for this we need to add a division operation and two rules to our example:

4.               Reduce to a common denominator 

5.               Shorten the numerator and denominator 

It's easy to see that the result now depends on the order in which the rules are applied! The production system is therefore no longer commutative. In addition, deadlocks are possible in some cases during the search. As a result, one of the paths is not reduced by rules 1-

![](Images/image00349.jpeg)

 

Rice. Mistake!               The text of the specified style in the document

absence. .29. Dead ends in the search

To solve this problem related to the formation of dead ends, let's add inverse operations:

6.               Take it out of the brackets 

If only rule 6 (parentheses) is introduced, then there are two mutually inverse rules: opening parentheses and parentheses, which means that a loop is possible, ie the Church-Rosser property is not yet satisfied. Into the dead end in Fig. error! The text of the specified style does not exist in the document. .29 make reducible, rule 7 needs to be added:

7.               Expand a fraction 

( u \+ v ) / w \= u / w \+ v / w 

But then an endless loop may appear, which cannot be detected during an irreversible search (in fig. Error! The text of the specified style is missing in the document. .30 one of the possible loops is circled with an oval).

![](Images/image00350.jpeg)

 

thirty. Loops when searching

The conclusion from this example is that the commutativity of a production system is a very powerful and useful property . One should try to construct commutative systems of production, and in the cases where this is not possible, it is worth checking whether it is possible to restrict the problem somewhat, but in such a way that it becomes possible to construct a commutative system . 

#### 2.3.4. Degradable production systems

The commutativity of the production system offers the freedom to choose the rule applied. This is not the only quality that gives such freedom.

(split) into a sum of production systems that can be considered independently of one another , this is referred to as a decomposable production system .

A good example of a decomposable production system are formal generative grammars. Let's look at a simple example on this topic. Let there be rules

A→BC

A→CT

C→TT.

to get a string containing only the symbol T from the word AC ? Below are the search graphs for regular (Fig. Error! The text of the specified style is missing from the document. .31 ) and composite (Fig. Error! The text of the specified style is missing from the document. .32 ) production systems. In the first case we make all possible transitions from the initial expression. In the second case, we first split the original database (word AC ) into two parts (word A and word C ) and then create search graphs for each part. Here are the complete search graphs and from them it is clear that a solution can be obtained. Indeed, in fig. error! The text of the specified style does not exist in the document. .31 there are paths (there are three of them, leaf nodes are highlighted in color) leading from the start node to the end node, and in Fig. Fehler! The text of the specified style does not exist in the document. .32 for each of the two parts of the decomposition there is a pair of paths leading to the end nodes . The nodes contained in the solution are shown in Fig. Fehler! The text of the specified style does not exist in the document. .32 circled with an oval.

![](Images/image00351.jpeg)

 

31\. Search graph for a conventional production system

![](Images/image00352.jpeg)

 

Rice. Mistake!               The text of the specified style in the document

absence. .32. Search graph for a decomposable production system

Let's compare the numbers in Fig. Error! The text of the specified style does not exist in the document. .31 and Fig. Error ! The text of the specified style does not exist in the document. .32 it is easy to see that in the first case a lot of unnecessary work is done: the result of applying the rules in the left branch leads to a dead end. Using the decomposition in this example halves the search graph!

The basic procedure for a decomposable production system is shown in the Error! algorithm. The text of the specified style does not exist in the document. .8 .

Algorithm error ! The text of the specified style does not exist in the document. .eight. Interpreter of a decomposable production system.

proc split (d, R , t )

  := disassemble (d) during Is correct do                              for d  do 

   if t (d) then  :=  \\ {d} end if                              end for

  if  =  then return ( OK ) end if                d := SelectD (  )

   :=  \\ {d} r := choose (d, R )               when r = zero then return ( fail ) end if 

   :=   Decompose (rf(d)) end while 

end process

Production method , the very first and most general (see Section 0). The Decompose procedure decomposes the database into multiple parts (or leaves them as is if the database cannot be decomposed in this state). In a sense, this is similar to the operation of opening a node, but still different, hence Error in Fig.! The text of the specified style does not exist in the document. 0.32 arcs that correspond to the extent, not the extent, are highlighted in gray. Also, the SelectD function is similar to the Select function , it actually selects a node for further work.

Let's make an important remark. From the point of view of graph theory, the arc that appears in the search graph as a result of applying the decomposition rule is a hyperarc – an arc that starts from the decomposable basis and leads simultaneously to several bases that are parts of the decomposition. To come to a solution you have to find a solution for the first part AND for the second part and so on. Therefore, such a hyper-arc is called an I-arc. If ordinary arcs arise from the knot, corresponding to the application of the rules, then they have the following meaning: to find a solution, you must apply the first rule OR, the second rule OR, etc. Therefore such arcs are called OR arcs. If only such arcs are used in a graph, it is called an AND/OR graph . In the next two chapters we will come back to these concepts and discuss them in more detail, see Sections 3.3 and 4.5.1.

The theory of formal grammars developed by AN Khomsky is used successfully to describe programming languages and other artificial languages. In short, its essence is as follows. We consider a finite alphabet A (a set of symbols) and a language over this alphabet. Here, a language is simply a set of sequences of alphabetic characters (strings). In other words, among all possible chains (of which there are obviously infinitely many), one must be able to single out those and only those that are chains of language (they also say “include in language”, “belong to the language", "are expressions of language").

To describe the (infinite) set of strings, Chomsky proposed using a formal generative grammar — a finite set of rules of the form called non-terminal). The left side of the rule (i.e. the string  ) must contain at least one non-terminating character. Among all the nonterminal symbols, one stands out and is called the initial symbol (or axiom) of the grammar.

In addition, everything is very simple. Taking the axiom of the grammar as a basis, it is legal to construct new chains by replacing each occurrence of the left-hand side of any rule in the already constructed chain with the right-hand side of that rule. And so on until only terminal symbols remain in the chain. Any chain of terminal symbols that can be constructed by such a process enters the language by definition, and if the chain cannot be constructed in this way then it does not enter the language.

Of course, all of this is as simple as that, until various tricky questions are asked. Can any language be defined like this? Given a grammar and a specific ending string, how do you know if it belongs to the language or not? Is the chain generation process unique? Do the answers to the previous questions depend on the type (form) of the rules?

But if the main idea is clear, then we can leave these (rather difficult) questions to the mathematicians and accept that the syntax of the vast majority of programming languages can be easily described by a subclass of formal grammars called context-free (the left-hand side of all rules consists of a single non-terminal symbol). For this subclass of grammars, all questions related to detecting the membership of a string in a language (this is called parsing or parsing) are reliably solved.

### CONCLUSIONS ON CHAPTER 2

1.               Production systems are historically the first and still frequently used form of representing knowledge.

2.               Production systems are effectively implemented programmatically and are the foundation of many practical software systems.

3.               The use of product systems can only make sense if the associated limitations and disadvantages are fully understood.

# CHAPTER 3. 

# SOLUTION ALGORITHMS

Solution-seeking algorithms are so numerous and varied that the use of this term without proper comment can be misleading. In the general case , the search algorithm searches for a solution to the problem in a specific search space . The search space can be discrete or continuous; can be finite or potentially infinite; the metric properties of space may be given or unknown; the properties of the solution sought can be fixed or change during the search. In all these and many other cases, a wide variety of algorithms are used, some of which have little in common. In our opinion, an exhaustive test of all search algorithms is technically hardly possible and the value of such a hypothetical test would be questionable. Therefore, we limit ourselves to a special area – algorithms for finding solutions in applied systems with elements of artificial intelligence .

Even with this limitation, a detailed analysis of all algorithms used seems too extensive. We allow ourselves to narrow the scope further by restricting ourselves to an analysis of the most popular and representative approaches to search for inference in systems based on productions , ie with as basic constructions of the form p  q introduced in the second chapter. In the agreements made, it is natural to represent the search space as a graph (or mesh) of a particular form, where the nodes represent the states of the fact base and the arcs correspond to the application of productions [\[44\]](#part0005.xhtml#_ftn44). The result of a search for a solution on a graph is always a route (chain, output) leading from the start node to the goal node . Of course, the new narrowing of the study area simplifies our task, but even now we cannot single out a best universal algorithm for finding a solution! The fact is that a very important (if not decisive) role in the search for a solution is played by the specific properties of the nodes and arcs of the search graph, which are determined by the purpose of the application and, consequently, by the nature of the productions themselves.

Thus the problem of finding a solution in a system of productions can be reduced to the problem of finding a route on a graph . When choosing a suitable algorithm for solving a particular problem on a graph, we need to take into account many properties of the search graph (for example, to decipher the terms, we refer to the book \[17\]), namely: whether the graph is directed (digraph), whether cycles are allowed in it (and what are these cycles of nature), can two nodes be connected by more than one arc (multigraph), is the graph multipart (and to what extent), what do we know about the connectivity and degrees of the corners of the graph , what is the cardinality of the sets of nodes and arcs (is the graph finite), whether the graph is labeled, weighted (and what combination of these properties) and much more. It is important to understand that all of these properties are determined by the formulation of the problem, more specifically by the choice of representing the problem, and are not arbitrary. For example, if we have a good acyclic graph algorithm, but the search graph for a given problem contains cycles, then this algorithm is of little use.

Recently, considerable attention has been focused on what is characterized in its most general form as the problem of constructing an optimal route . Examples of relevant application areas can be logistics (minimizing the transport time of goods between warehouses) and administration movement Robot (in an environment with restrictions and obstacles), strategic games and more. Search graphs for such tasks are "pretty decent" - oriented monopartite digraphs - the node of the graph is usually just a name (or a point in space usually with metric and small dimensions), the density is low (far from all nodes are directly connected to each other), the degree of a node d is always estimated by a bounded constant (deg( d ) < const << n , where n is the number of graph nodes), which determines the weight on the arc only the cost of moving from one node to another, the source and destination nodes are uniquely determined. At the same time, it is considered that the constructed part of the search graph necessary to solve the problem can be placed entirely in the computer's "fast" (operational) memory. The main problem addressed in this chapter is to construct an optimal (resource minimizing) route from the source node to the destination node.

The chapter covers five algorithms:

\-                     general algorithm for heuristic solution search for systems of heterogeneous production (section 0);

\-                     formal properties of the historically first and most

known search algorithm on the graph (section 0);

\-                     a nice way to increase the efficiency and practicality of the general algorithm for finding a solution (section error! link source not found. )

\-                     an algorithm for searching on AND/OR graphs, which is a specialization of the general algorithm that occurs, for example, when using decomposable production systems (Section 0);

\-                     Search algorithms on game trees, which on the one hand represent a further specialization of general algorithms, since game trees are a special case of AND/OR graphs, and on the other hand the most developed practical algorithms for real programs are discussed with previous AI elements at the beginning of the chapter of classes (Section 0).

Such a set of well-thought-out algorithms forms a system sufficient for the reader, after reading the chapter, to confidently navigate in a sea of various specific search algorithms - we have named the main beacons.

### 3.1. HEURISTIC SEARCH

Historically, one of the first and most well-known algorithms in AI for finding optimal (in terms of total weight or length) paths in a search space graph is the A\* algorithm (read as "A-star" or "A-star". ). This algorithm was first described in 1968 by Peter Hart, Nils Nilsson and Bertram Raphael \[18\]. In their work it is referred to as "Algorithm A". In the classical version, the A\* algorithm is applicable in a discrete search space represented by a search graph with charged arcs. This heuristic search sorts the nodes of a graph by the value of a function that evaluates the length of the shortest path that passes through a given node and goes from the start node to one of the destination nodes. Thus , this algorithm combines consideration of the lengths of optimal paths from the already explored part of the search graph from Dijkstra's algorithm with the steepest descent heuristic [\[45\]](#part0005.xhtml#_ftn45)for the as yet unexplored part of the graph .

#### 3.1.1. General Algorithm

For clarity of further presentation we repeat the definition of the search graph, make some important remarks and write the general form of the search algorithm on the graph.

The search graph is a directed graph G (V, E) in which the node set V = { d | d \_ D } is the set of possible states of the fact base (in the sense of the previous chapter), and the set of arcs E is defined as follows:

E. \= { d 1  d 2 | d 1 , d 2  D &  r  R ( rp ( d 1 ) & d2 \_ \= rf ( d 1 ) } }.

In the case where the search graph is essentially finite, it can be explicitly specified using the usual ways of representing graphs in a computer. In such cases, the search graph is often chosen as the mechanism for representing knowledge - marks on spirals are products, there is no need to indicate a set of productions separately.

In the case of an infinite (or very large) graph, we cannot use these simple representations simply because the entire graph does not fit in the computer's memory. Instead, starting from the initial state of the database d 0 , we generate a part of the search graph using a finite set of rules R until either the allocated resources are exhausted or the generated part contains the target state of the database dt . \_ Thus, an implicit (implicit) representation of the graph in the computer is used. A graph can be specified implicitly using the node expansion operation.

each rule has r costs associated with its application, denoted by r . w and named the cost or weight ( weight ) of applying the rule. In this case, each arc in the search chart has a weight. In other words, the arcs are loaded, and the loading value can be taken as positive: r \= ( p , f , w ), w \> 0.

The cost of a path in a graph is defined as the sum of the costs of its arcs. The general graph search algorithm, which computes the cost of paths from the initial node and (under certain conditions!) determines the minimum-cost path [\[46\]](#part0005.xhtml#_ftn46), is as follows.

Algorithm error ! The text of the specified style does not exist in the document. .9. General search algorithm in a diagram.

GS (d0, R , t )

 O := {d0}; g(d0) := 0

 C :=  ; P(d0) := zero  while Is correct do                  d := select (O)

  when d = zero then Return ( Fail ) end if                              if t(d) then return ( OK ) end if 

 Open (d) end while 

End perc  

 proc Open (d) for r  R do   if rp(d) then {rule holds}               d' := rf(d) c' := g(d)+rc

   if d'  O  d'  C then {old node}                               if c' < g(d') then {better way}

 g(d') := c' P(d') := d end if 

   else {new node}

O := O+{d'} g(d') := c' P(d') := d end if   End if End for O := O - {d} C := C + {d} end perc where O is the list of "open" nodes, C is the list of "closed" nodes (see Fig.

Paragraph 2.2.4).

In addition to the usual parameters and the lists of open and closed nodes already discussed, the method uses two other data structures. The first of these is g ( d ) - the length of the shortest path from d 0 to d of those explored so far. Note that g ( d 0 ) = 0, for other nodes at the beginning of the work g ( d ) is unknown, and as the algorithm runs, the value of g ( d ) for a given node d can only decrease.

P ( d ) deserves a special discussion - this structure stores for node d the previous node on the found shortest path from d 0 to d . This technique allows to effectively store the set of paths leading from node d 0 to all examined nodes at once.

This graph search algorithm has two functions - Select and Open . Informally speaking, the first of them is “search” and the second is “on the graph”.

The Select function somehow determines the next node to expand. If the Select (O) function works according to the FIFO principle (First In First Out), that is, if the list O is a queue, then a breadth-first search is performed. This method ensures that a path to the destination node is found if such a path exists. If the Select (O) function works according to the LIFO principle (Last In First Out), that is, if the list O is a stack, then a depth-first search is performed; this method is similar to a backtracking search, but not only the current path is saved, but all paths visited.

Breadth-first search and depth-first search are examples of uninformed search methods. If nothing is known about the task, uninformed procedures must be employed, but not much can be relied upon. In order to effectively find a solution, it is necessary to use additional information about the problem. Such additional information is often referred to as a heuristic. The meaning of this term is explained in the next paragraph.

#### 3.1.2. Heuristic Algorithms

The ancient Greek word "heuristics" ( ευρίσκω \- I seek, I discover) has many similar but different meanings and uses in modern language. The following interpretations of this term can be found in the literature.

Heuristic methods are special methods for solving problems, which are mostly in contrast to formal solution methods, which are based on exact mathematical models. Using heuristic methods does not guarantee that the resulting solutions will be the best, unsuccessful heuristics can lead to the worst result! At the same time, there are many successful heuristics (for solving specific problems) that provide [\[47\]](#part0005.xhtml#_ftn47)acceptable solutions at an acceptable cost.

Heuristic activity is the organization of the process of productive creative thinking. In this sense, heuristics are understood as a set of inherent human mechanisms for solving creative problems. These mechanisms are universal in nature and do not depend on the specific problem to be solved.[\[48\]](#part0005.xhtml#_ftn48) 

Heuristic programming is a way of writing programs in which the programmer does not code a ready-made mathematical solution method, but tries to formalize the intuitively understandable method of solving a problem that he thinks a person uses when solving such problems. Like heuristic methods, heuristic programs do not give an absolute guarantee for the achievement of the set goal and the optimality of the result.

Heuristic learning is a special method of learning ( Socratic conversations ) or collective problem solving that historically goes back to Socrates. The method consists of asking the students a series of guiding questions and examples, which in a manner of speaking make them search for a solution themselves.

In our case, we understand the term "heuristic" in the narrower sense.

A heuristic is a [\[49\]](#part0005.xhtml#_ftn49)rule of thumb that simplifies or limits the enumerating of options when searching for a solution in a specific domain.

Moreover, since we are considering here a very specific solution path in a given domain - a search in a graph for a production system - we can make the definition even more specific.

Heuristic is a set of rules for choosing the next node to expand, which, according to the author of the heuristic, should lead to a solution to the problem.

Unfortunately, heuristics rely on guesswork and intuition rather than exact knowledge; Heuristics use available but limited information, such as a description of the set of currently open nodes, and cannot guarantee that the choice is actually the best. A heuristic is just a suggestion for choosing the next step based on experience and common sense.

An algorithm that uses heuristics is called a heuristic algorithm .

Heuristics reduce the computational cost of applying the rules by reducing the total number of times the rules are applied. But even the application of the heuristics themselves requires some kind of calculation and has its own costs. In addition, manipulating the search graph, especially when it is large, is also costly (see Figure 2.5 again).

In fact, we are interested in the sum total of the cost of applying the rules, the cost of checking and expanding nodes, and the cost of heuristics. More specifically, we want to minimize the average of this sum over all cases where the heuristic algorithm is applied.

In order to formulate the problem accurately it is necessary to give definitions and introduce notations, which we will do in the next section.

#### 3.1.3. rating function

The heuristic information can take any form. It is common in AI to represent heuristic information in the form of a scoring function F ( d ).

The evaluation function F is defined on the set of permissible environmental states (fact bases) and assumes real numerical values F : D   . In addition, the evaluation function is usually chosen in such a way that its value at the end nodes is minimal F ( d t ) = min { d  D | is F ( d )}. Given such an evaluation function, it is possible to write the Select function with the idea of steepest descent (algorithm error! Text of specified style is not in document. .10 ).

Algorithm error ! The text of the specified style does not exist in the document. .ten. The function to select a node to expand.

Process selection (O) m :=   d' := zero  for d o do \_                            if F(d) < m then  

 d' := dm := F(d)

  End if  End to the  return (d') end perc 

Or short:

Choose (O) := min F(d), d  O

Many different implementation ideas have been proposed for the evaluation function F. The word "estimated" means that F (probably) is close to an important search feature. The following is a list of some characteristic properties that are often attempted to use when choosing an estimator:

\-                     the reciprocal of the probability that d belongs to the optimal path;

\-                     Distance from node d to the target set of node T ;

\-                     the weight of the path from the source node d 0 to the destination node d t via the current node d .

In this section we consider the latter case.

We consider the evaluation function in the following form:

F(d) = g(d) + h(d), where g(d) is the actual cost of the path from the initial node d 0 to d (already defined by us in the Open procedure ); h(d) is a heuristic estimate of the cost of the path from d to the destination node d t .

Consider the process of choosing an evaluation function using the example of the game in 8 \[13\] (we already discussed it in section 2.1.4). We introduce the evaluation function F(d) as the sum of the depth in the tree (corresponds to the function g(d)) and the number of missing stones (corresponds to the function h(d)). We see (Fig. Error! The text of the specified style is missing in the document. .33 ) that with such an evaluation function the search on the graph is very efficient and quickly leads to a solution.

Let's make some observations about this example:

\-                     h(d t ) = 0, since in the target position, by definition, all stones are in place;

\-                     h(d) does not exceed the minimum number of moves to go from d to d t ;

\-                     the value of the function F(d) for expanded nodes does not decrease; if we take the function F only as the depth in the tree, ie

If you set h = 0, you only get breadth-first search.

In the next section we summarize and interpret these empirical observations.

![](Images/image00353.jpeg)

  .33. Search graph for an 8-player game with an evaluation function F .

### 3.2. PROPERTIES OF ALGORITHM A\*

Algorithm A\* has a number of remarkable and useful properties that explain its wide applicability.

The most important property is the fact that, despite the algorithm's heuristic nature, a sufficient [\[50\]](#part0005.xhtml#_ftn50)condition is known under which the algorithm A\* is guaranteed to find the optimal solution, if one exists. This is strictly shown in the first paragraph of this section. The second paragraph shows that the algorithm A\*, figuratively speaking, "remembers well" - the more informed the scoring function provided to the algorithm, the "better" the algorithm behaves. Finally, in the third paragraph of the section, it is shown that if the evaluation function is chosen sensibly and is consistent with the metric properties of the search space, the A\* algorithm not only finds the optimal solution in the end, but all intermediate states are on the optimal path. In other words, in some cases the A\* algorithm behaves just perfectly: in the best possible way. In the last paragraph we note that ideal behavior is not always guaranteed: sometimes A\* leaves a lot to be desired.

#### 3.2.1. consistency set

Let's give the necessary definitions and introduce the notation. The length of the shortest path [\[51\]](#part0005.xhtml#_ftn51)from node d 1 to node d 2 is denoted by s(d 1 , d 2 ). Let F\* ( d ) = g\* ( d ) \+ h\* ( d )

is the exact length of the shortest path from node d 0 to node dt , which goes through node d . Here g\* ( d ) is the length of the shortest path from d 0 to d, h\* ( d ) is the length of the shortest path from d to d t , i.e. g\* ( d ) \= s(d 0 , d ) , h\* ( d ) \= s(d, dt ) .

Using the definitions it can easily be shown that  d F\* ( d )  s(d0 , dt ) .

In fact, a path consisting of two shortest segments passing through a given node d cannot be shorter than the shortest path itself. Denote M \= F\* ( d 0 ) \= h\* ( d 0 ) = s(d 0 , d t ) is the optimum, the length of the shortest path, without restrictions.

Note that the functions F\* , g\* , h\* and the number M in general are unknown to us.

Recall that we consider the evaluation function in the following form:

F ( d ) \= g ( d ) \+ h ( d ),

where the function g is already defined by us in the Open procedure . During the operation of the A\* algorithm, g ( d ) has the following estimate: g ( d ) ≥ g\* ( d ) since it is possible that not all paths have been built yet, and when opening nodes and constructing new ones For paths, the estimate g ( d ) can decrease, but not become smaller than g\* ( d ).

The question remains the function h ( d ) \- a heuristic estimate of the distance from the current position to the solution. It is clear that in the general case we cannot specify this function mathematically exactly, we can only invent it more or less successfully in individual cases . For example, the function selected in paragraph 0 for playing the 8 has turned out to be very successful. She made it possible to find a solution quickly.

How random is that? What properties should the evaluation function that determines the order in which the nodes are expanded have, so that the algorithm is guaranteed to find a solution? The following theorem gives an [\[52\]](#part0005.xhtml#_ftn52)answer to these questions.

Search algorithm               should be               consistent error!

The bookmark is not defined. (or partially correct) when it finds an optimal path, assuming such a path exists.

Sentence. When a d \_ h ( d )  h \*( d ), then Algorithm A\* is consistent .

The proof of the theorem is based on a set of lemmas. All lemmas are proved under the condition that h  H\*. Lemma 1 and the theorem are proved under the condition that  r  R ( r . w \> 0), ie the weight of the application of the rule is strictly positive. It follows that according to the sense of the problem all functions F\* , g\* , h\* , F , g , h and the number M are nonnegative.

lemma 1. If algorithm A\* does not finish its work, the estimate of the augmented node increases indefinitely. That is,  N  k F ( d k ) > N.

remark . Here k is the step number of the A\* algorithm and dk is the node expanded in this step.

prove. Let e \= min { r  R | r . w } > 0 is the minimum rule weight and m \=| R | - the number of rules. Let p be the depth [\[53\]](#part0005.xhtml#_ftn53)of node dk in the tree . Note that the node has the least depth when all previously opened nodes are on the previous levels of the tree and the levels are completely filled. In the limit, the level p \-1 of an m \-ary tree contains 1 + m \+ m 2 \+ ... + m p - 1 \= ( m p \- 1)/( m \-1) nodes. Hence k < ( m p \-1)/( m \-1) < m p (for m \> 2). Then p \> log m k . Now let's take k \> m N / e . We have: F ( d k ) > g ( d k ) > ep \> e log m k \> e log m mN / e\_ \= N Ch.td 

Lemma 2. If there is an optimal path, then the list of open nodes always contains a node belonging to this path whose estimate is not exceeded M\_ \_

prove. Let A \= < d 0 , …, d t \> be the optimal path.

Furthermore, induction on the steps of the algorithm.

Basis of induction: d 0   A and F ( d 0 ) = h ( d 0 ) < h \* ( d 0 ) = M .

inductive transition. Opening a node of A leaves an heir at O. This means that the list O always contains a node of A , at least one but there can be more. Now let d'   O , d'   A , and d' is the left node of these nodes (see fig. Error! The text of the specified style is missing in the document. .34 ), ie all nodes to the left of d' on the path are already open and are in the list C. \_ Then g ( d' ) = g \*( d' ) since the segment of the optimal path is also optimal. We have F ( d ) = g ( d' )+ h ( d' ) = g \*( d' )+ h ( d' )  g \*( d' )+ h \*( d' ) = F \*( d' ) = M , because d \_   A F \*( d ) \= M 

![](Images/image00354.jpeg)

  .34. To prove Lemma 2.

Lemma 3. If there is an optimal path, then a node whose estimate does not exceed M is always opened .

prove. By Lemma 2  d  OF(d)  M, but the function

Select always selects the minimum. Ch.td\_ \_

proof of the theorem. Proof by contradiction in three steps.

First step. Let  A be the optimal path and the algorithm does not finish its work. Then by Lemma 1  k F ( d k ) > M , which contradicts Lemma 3. The algorithm then completes its work.

Second step. The algorithm can end with fail or OK . The result error is only possible if the list O is empty. But by Lemma 2, the list O is not empty, which means that the algorithm ends with the result OK .

Third step. Let the algorithm A\* end with the result OK , but the path P found is not the optimal path. Consider the last call to the Select function before the algorithm finishes. Leave the selector selected as expandable

Eckpunkte d t . Aber h \*( d t )=0, also h ( d t )=0. Also F ( d t ) = g ( d t )+ h ( d t ) = g ( d t ) > g \*( d t ) = F \*( d t ) = M ,

that is, a vertex was chosen with a score greater than M , what

contradicts Lemma 3 . 

This proves that algorithm A\* terminates with the result OK and finds the optimal path. Ch.td\_ \_ 

Corollary 1. Every node d  O for which F(d) < M is revealed.

prove. The node d t with score F ( d t ) = M is chosen last for expansion, and at each step the node with the minimum score is expanded. Ch.td 

Episode 2. Breadth-first search is consistent. 

proof . Breadth-first search: h \= 0 , F \= g, and consistency condition for h : 0  H\*. Ch.td

Consider the example of playing at 8 given in paragraph 0. It can be seen that the proposed heuristic function satisfies the consistency condition. In fact, the proposed function h —the number of pieces that are out of place—cannot exceed the number of steps required to put all the pieces in place. After all, we don't use more than one stone in one move!

#### 3.2.2. Comparison of the evaluation functions

Two evaluation functions are given:

F 1 ( d ) = g 1 ( d ) \+ h 1 ( d ), F 2 ( d ) = g 2 ( d ) \+ h 2 ( d ).  

In addition, the conditions of the consistency theorem are satisfied: h 1 ( d )  h\* ( d ), 

h 2 ( d )  h\* ( d ).

We will say that the function h 2 ( d ) is more informed than h 1 ( d ) if  d  dt h2 ( d ) > h1( d) . Let h 2 ( d ) be a more informed function than h 1 ( d ). Then no more nodes are revealed when using F 2 than when using F 1 , ie a more informed evaluation function finds a solution more quickly.

As an example, consider the game of eight presented in Section 2.1.4. and 0. In our terminology, g ( d ) is the depth in the game tree, h ( d ) is the estimated function of the number of misplaced pieces. So the chosen function h ( d ) in game 8 is obviously more informed than the function h ( d ) in breadth-first search ( h \= 0).

Sentence. If there is an optimal path and the function F 2 is more informed than the function F 1 , then by the end of the search every node extended by F 2 is also extended by F 1 . 

prove. Induction on k \- the depth of the node d in the search tree by F 2 (Fig. Error! The text of the specified style is absent in the document. .35 ) . 

basis of induction. The depth is zero ( d 0 ). In this case, either both algorithms open node d 0 , or both do not open it (for d 0 \= d t ) . 

inductive transition. Let d be the node chosen in step k for the F 2 \-expansion. Let S 1 and S 2 be the sets of nodes opened to d by F 1 and F 2 , respectively. By inductive assumption, S 1 contains at least nodes than S 2 , which means that S 1 may have more nodes from which you can get to d than S 2 (Fig. Error! The text of the specified style is missing in the document .35 ). So g 1 ( d )  g 2 ( d ). Farther on the contrary. The algorithm is completed and d is not extended by F 1 . By Corollary 1 to the consistency theorem F 1 ( d ) ≥ M . But at F2 node d is open, so F 2 ( d )  M \_ We have g 1 ( d ) \+ h 1 ( d ) ≥ M ≥ g2 ( d ) \+ h2 ( d ) \_ ≥ g 1 ( d ) \+ h 2 ( d ) , hence h 1 ( d ) ≥ h 2 ( d ), which contradicts the condition. Ch.td 

![](Images/image00355.jpeg) 

  .35. To prove the theorem about the comparison of evaluation functions.

Consider again the example of playing 8 in paragraph 0. It can be seen that the proposed heuristic function is very good: not only does it satisfy the consistency condition as shown in the previous paragraph, but it is also "extremely informed". In fact, the proposed function h \- the number of misplaced stones - cannot be significantly improved, ie it is impossible to offer a heuristic h' such that  d h' ( d ) > h ( d ).

Actually from fig error! The text of the specified style does not exist in the document. .33 it can be seen that there are nodes d in which h ( d ) = h \*( d ), which means that the hypothetical majorant h' violates the consistency condition.

#### 3.2.3. monotonous constraint

You say               that the function h fills the               monotony

Constraint (or triangle inequality ) if

i.e. ( d ) \_  h ( rf ( d )) \+ rw & h ( d t ) = 0,

where r is the rule to go from node d to node rf ( d ) . 

In other words, the heuristic function is locally consistent with the weight of the arcs (rules).

Sentence. If the consistency condition is satisfied, the evaluation function satisfies the monotonic constraint, and there is an optimal path, then algorithm A\* for expansion always chooses a vertex to which the optimal path has already been found, i.e. g ( d ) = g \* ( d ) .

prove. Induction on the length of the optimal path. Basis of induction: g ( d 0 ) = g\* ( d 0 ) = 0.

inductive transition. Let node d  d 0 and let A \= d 0 , d 1 , …, d i , …, d be the optimal path. We have

i \_ g \*( di i )+ h ( di i )  g \* ( di ) + w ( di , di \+ 1 ) \+ h ( di +1 ) by the monotonic restriction . Next d i , d i+ 1  A  g\* ( d i ) \+ w ( d i , d i +1 ) = g\* ( d i +1 ).

We have

i \_ g\* ( di i ) + h ( di i )  g \*( d i+ 1 ) \+ h ( d i+ 1 ) and by transitivity

 i g \*( d i ) + h ( d i )  g \*( d ) + h ( d ).

Now let dk be the first open node on the path A , ie dk  A , dk  O &  j<kd j  C \_ Such a node exists because d0 \_  C, d O. All nodes on path A to the left of d k , ie all closed nodes before d k on path A are already open, so g ( d k ) \= g\* ( d k ) . 

Since the algorithm A\* when opening the next node consists of two nodes d and d k choose node d , then F ( d )  F ( d k ). So we have:

g ( d ) \+ h ( d ) \= F ( d )  F ( d k ) \= g ( d k ) \+ h ( d k ) \= g \* ( d k ) \+ h ( d k )  g \* ( d ) \+ h ( d ). 

So g ( d )  g\* ( d ). But  dg ( d ) ≥ g\* ( d ) and therefore g ( d ) \= g\* ( d ). Ch.td 

Consequence. When the scoring function satisfies a monotonic constraint, the sequence of values of the scoring function for the selected nodes does not decrease.

prove. The nodes d 1 , d 2 are open (in a row). If at the moment of opening the node d 1 is already d 2  O , then by constructing A\* we have

F ( d 1 )  F ( d2 ) . Otherwise, d 2 must fall in O when expanding d 1 . We have: F ( d 2 ) \= g ( d 2 ) \+ h ( d 2 ) \= g\* ( d 2 ) \+ h ( d 2 ) \= g\* ( d 1 ) \+ w ( d 1 , d 2 ) \+ h ( d 2 ) \= = g ( d 1 ) \+ w ( d 1 , d 2 ) \+ h ( d 2 ) ≥ g ( d 1 ) \+ h ( d 1 ) \= F ( d 1 ). Ch.td

#### 3.2.4. Scope of Algorithm A\*

For all its merits and virtues, the A\* algorithm has a number of inherent characteristics that can manifest as disadvantages under certain conditions.

1.               In the worst case, the A\* algorithm has exponential time and memory complexity estimates . Suppose we don't have an informed scoring function that satisfies the consistency condition. In this case you have to use breadth-first search, h \= 0. Assume (in the worst case!) that all rules hold in each state and give n of these rules . Also let the number of arcs [\[54\]](#part0005.xhtml#_ftn54)in the optimal path from d 0 to d t be s .

Then, as is easy to see, the total number of constructed nodes of the search graph is at least 1+ n \+ n 2 …+ n s \-1 \= ( n s \-1 \-1)/( n \-1) .

2.               The efficiency of the algorithm crucially depends on the heuristic function F. In fact, we noted above that without heuristics, the worst-case algorithm executes the number of steps that depends exponentially on the number of arcs of the optimal path. If we simultaneously have an extremely informed estimator such that  d ( h ( d ) = h \*( d )) and additionally a monotonic constraint is satisfied, then the A\*-algorithm becomes (in in the worst case!) ns +1 Construct knots, since according to the theorem of the previous paragraph, in this case, knots are opened one after the other on the optimal path. Thus, in the case of an ideal [\[55\]](#part0005.xhtml#_ftn55)heuristic, the algorithm A\* can have a complexity that is linear in the number of arcs of the optimal path.

3.               Algorithm A\* does not take into account the structure of the fact base and always uses it in full . This is extremely memory intensive and proves unacceptable for a great many practical problems. For example, when solving the problem of robot movement in an environment with obstacles, the fact base is very small - the coordinates of the robot's current position, and the A \* algorithm shows good results. But when A\* is applied to a large relational database in an expert system, then formally each node in the graph corresponds to a complete snapshot (dump) of the database, and the neighboring ones may differ by only one record.

4.               Algorithm A\* does not take into account the structure of the conditions in the rules and re-evaluates conditions that may have already been checked in previous steps . This is very time consuming . In the example above, when checking the position of the robot, the calculations made for the previous position cannot be reused because the coordinates have changed. However, if you are checking a complex condition in a large relational database, 99% of the work is already done if you check that condition in an earlier state, since most of the data hasn't changed.

5.               Algorithm A\* is unsuitable for the dynamic search case . In fact, if the productions or the goal or the weights of the rules are allowed to change dynamically during the search, [\[56\]](#part0005.xhtml#_ftn56)all the arguments of the previous three paragraphs become invalid. The consistency of the A\* algorithm comes from the fact that choosing another path from a given node does not depend on how we got to that node. This is not the case with dynamic search: the length of the path from the current node to the target node can also differ, depending on how we got to the current node.

What has been said in this section does not mean that algorithm A\* is worthless and should not be used. On the contrary, the A\* algorithm is the best known solution when there is no additional specific information about the properties of the problem. If there is additional information, A\* can and should be modified considering a specific task. One of the most elegant modifications is discussed in the next section.

### 3.3. SEARCH IN GRAPHICS AND/OR

When considering decomposable production systems, the concept of AND/OR graphs was introduced. In such a graph, the nodes are the states of the database or parts of it, which are obtained in two ways: either by applying a rule or by decomposing the database into components. This is exactly a graph and not necessarily just a search tree. The same vertex d can also appear as a result of decomposing d 1 and applying the rule to d 2 . AND/OR graphs are widely used in AI. Search algorithms like A\* are specialized and refined for use with AND/OR graphs. In addition, even more efficient algorithms are known for certain special cases of hypergraphs.

#### 3.3.1. Count AND/OR

Let's refine the definitions.

The AND/OR graph is a hypergraph, i.e. a pair consisting of a set of vertices { d } and a set of k-arcs, and the k-arc is a pair d  ( d 1 ,…,d k ) , where d is the starting node of k -arcs and { d 1 ,…,d k } is the set of ending nodes.

In terms of this definition, an ordinary directed graph is a hypergraph in which every arc is a 1-arc. Just as in an ordinary digraph, one can define the notion of a path (hyperpath) in a hypergraph.

A hyperpath in a hypergraph is a sequence of node sets, <S 1 , …, S n \>, and for every node d  S i , 1  i  n–1 there is exactly one k-arc d  (d 1 , …, d k ) such that  1  j  k

( d j  S i+ 1 ) .

The definition of a hyperpath is a direct generalization of the definition of a path, but a hyperpath in a hypergraph looks more like a diagram than a single alternating sequence of nodes and arcs. Exactly one k-arc is selected from each vertex . Exactly one k -arc is again selected from each vertex obtained, and so on.

Among the various hyperpaths, we are interested in those that begin in the initial state of the database and end in final states.

The decision graph G(d 0 , T) is a hyperpath from d 0 to the set of terminal nodes T.

One can give an equivalent recursive definition of the decision graph G ( d 0 , T ):

1.               if d0 \_  T , then G = d 0 .

2.               if d0 \_  T , and k-arc d 0  ( d 1 ,…, dk ) starts from d 0 , and there are solution graphs G 1 , G 2 , … , G k for vertices d 1 , d 2 , …, dk , then is G \= d 0  ( d 1 ,…, d k )  G 1  G 2  …  G k . 

The cost (weight) of the decision graph (i.e. the length of the path in the hypergraph) is determined using the inductive definition: w ( G ( d,T )) \= w ( d  ( d 1 ,…,d k )) +  w ( G ( di , T ) ). 

Thus the same k arc can be counted many times when calculating the length.

Let's consider an example (Fig. Error! The text of the specified style is missing from the document. .36 ). Let's assume that nodes 5 and 6 are terminal and node 0 is initial. We can claim that there are two decision graphs here (they are circled in the figure).

![](Images/image00356.jpeg)

36 . Decision hypergraphs and k \-arcs

If we assume that the length of the k \-arc is equal to k , then

\- length of the first solution graph = 1+(2+(2)+(2)) = 7, - length of the second solution graph = 2+(2+(1+2)) = 7,

since by inductive definition some k \-arcs

can be counted multiple times.

#### 3.3.2. Search algorithm on the AND/OR diagram

To search for paths in a hypergraph, there are algorithms that generalize depth- and breadth-traversals to ordinary graphs. The fundamental difference between generalizing algorithms is that the search procedure does not stop when a separate terminal node is reached. Not only do we need to reach a separate terminal node, but we need to build a decision graph whose branches all end in terminal nodes.

In general, AND/OR graph search algorithms can work without additional information. However, in the presence of a scoring               function, heuristic search algorithms can be used.

The heuristic search algorithm for the AND/OR diagram is as follows.

The graph is acyclic, there is an evaluation function F , and h satisfies the monotony condition (monotonic constraint): h ( d )  w ( d, ( d 1 ,…,d k )) \+  h ( d i ) 

and the consistency condition (i.e. is the lower bound for the exact solution):

h ( d )  h\* ( d ). 

Search procedures on AND/OR graphs are defined as follows.

Algorithm error ! The text of the specified style does not exist in the document. .eleven. Basic search procedure on the AND/OR graph.

proc GS and/or (d 0 , R, T)

 G := d 0 {partial solution graph} s(d 0 ) := d 0  T {node}

F(d 0 ):= h(d 0 ) during  s(d 0 ) do  d := select(G)

  when D = zero then Return ( Fail ) end if 

  Open (d, G) end while 

End perc 

Here s(d): bool is the label of the node, indicating whether a hyperpath leading to the terminal nodes was found for this node. If s(d)= true , the hyperpath is found, then the node is called resolved .

The selection procedure , based on the constructed search graph, considers a partial decision graph and selects an unexpanded minimum cost node for expansion on that graph.

Algorithm error ! The text of the specified style does not exist in the document. .12. The procedure for selecting a node to expand.

proc Choose (G) O := {d 0 } for d  O do                 for q = (d  d 1 ,…,d k )  Q(d) do                if x(d  d 1 ,…,d k ) then {marked arc}               O:=O - {d} {delete start} O:=O + ({d 1 ,…,d k }\\T) { end }

   End if   End to the  End to the                m :=                 d ' := zero                do for d  O                if F(d)<m then  

 d' := dm := F(d) end if 

 End to the  return (d') end perc  

Here O are the end nodes of the subgraph of the solution, Q(d) is the arc set of the node d , x(q) is the label of the arc q .

In fact, with this method, the decision front is traversed again each time from d 0 to the end nodes along the marked k \-arcs.

The Open procedure is much more complicated. It extends the selected vertex, recalculates the vertex values, marks the k arcs , and marks the allowed vertices, that is, the vertices for which a hyperpath to the ending vertices is found. These changes can affect the entire graph.

Algorithm error ! The text of the specified style does not exist in the document. .13. open procedure.

proc Open (d,G){node open} for r  R do                              if rp(d) then  

 G := G + (d  d 1 ,…,d k )  do for i from 1 to k                if d i  G then F(d i ):=h(d i ) end if                s(d i ) := d i  T                              End to the                               End if                 End to the  

 {recalculation of grades and grades} C := {d}               while C   do  

 {choice of vertices to recalculate} for d'  C do                if P(d')  C =  then d:=d' end if                              End to the 

 C := C - {d} m :=  

 for q=(d  d 1 ,…,d k )  Q(d) do  w':=w(q) +  F( di )                              if w' < m then                x( q (d)) := false                x(q) := true                s(d):= & s(d i )               m := w'               end if                               End to the 

 if s(d)  F(d)  m then  

 F(d):=m

   C := C + U(d) End if                 End while 

End perc 

The following notation is used here.

Q(d) is the set of emanating from d arcs (in G ), P(d) is the set of descendants of d in G , q (d) is a labeled arc of d , x(q) is the label of the arc,

U(d) is the set of ancestors of d in G along the marked arcs, s(d) is the node's label, meaning it is built from it

hyperpath to the goal.

Let's reiterate the main conclusions about these three procedures. The GS and/or procedure alternately calls the Select and Open procedures until either no node is found to expand (the result of fail ) or the original node d 0 is resolved. The Select procedure builds the front of the current partial decision graph along the marked arcs and selects the lowest-scoring node in that front. The Open procedure first opens the selected vertex, and then recalculates node estimates, marking arcs and vertices. In this case, this method can overestimate the entire graph. In these procedures we consider that the concept of a rule generalizes both the application of a rule and the sharing of a database with a k \-arc.

#### 3.3.3. An example of applying the search method to the AND/OR graph

On fig error! The text of the specified style does not exist in the document. .37 - Fig. Error! The text of the specified style does not exist in the document. 41 shows an example of the operation of the search algorithm on the AND/OR graph with respect to the graph shown in FIG. Mistake!

The text of the specified style does not exist in the document. .36 .

The following symbols are used in these figures. The states of the basis, i.e. the nodes of the AND/OR graph, are marked by circles. If the circle is filled, it means that the condition s(d) = 1 was obtained for it, i.e. the graph of the solution from the given node to the end nodes (in this example nodes 5 and 6 ) was found. 1 arcs are denoted by regular arrows, k arcs (in this example k \= 2) are denoted by denser arrows and have a small dash connecting the branches of the k arc. The number next to a node is the node's current rating. In this case, it is assumed that the function h has the value 0 for the terminal nodes, and for all others - 1. Such a function obviously satisfies the consistency condition. The length of the k arc is equal to k . A marked arc emanating from a given node is marked with a thick bar. The following series of figures form an explanation of the search procedures on the AND/OR graph. 

1D0 \_ \_

37\. Step 1. Initial state

In the initial state the decision graph consists of a single node d 0 , the same node forms the front of the decision, it is chosen by the Select function because there is nobody else to choose from, and the Open procedure opens this node.

D0 \_

![](Images/image00357.jpeg)

 

38\. Step 2: Expanding the node for the first time

After the first step, recalculating the grades returns the following to the d 0 node:

\-                     left = 1 (node count d 1 ) + 1 ( arc cost d 0  d 1 ) = 2;

\-                     right = 1 (estimate of node d 2 ) + 1 (estimate of node d 3 ) + 2 (cost of arc d 0  ( d 2 , d 3 ) ) = 4.

The guess on the left is preferable, so arc d 0  d 1 is marked, and node d 1 is opened next .

![](Images/image00358.jpeg)

 

39\. Step 3. Extension of the second node

After the second step, recalculating the grades returns the following to the d 0 node:

\-                     left = 1 (estimate of node d 4 ) + 1 (estimate of node d 2 ) + 2 (cost of arc d 1  ( d 4 , d 2 ) ) + 1 (cost of arc d 0  d 1 ) = 5 - Estimate increased;

\-                     right = 1 (estimate of node d 2 ) + 1 (estimate of node d 3 ) + 2 (cost of arc d 0  ( d 2 , d 3 ) ) = 4 - the estimate does not change.

Now the right guess is preferable, so the arc d 0  ( d 2 , d 3 ) is marked, and the node d 2 is opened next .

![](Images/image00359.jpeg)

 

40\. Step 4. Expansion of the third node

After the third step we get to the end nodes d 5 , d 6 . Since these are both nodes to which the 2-arc d 2  ( d 5 , d 6 ) leads, the node d 2 is also marked as allowed. Moreover, his estimate is equal to 2 (the cost of the outgoing 2 arc). Recalculating grades to node d 0 returns:

\-                     left = 1 (estimate of node d 4 ) + 1 (estimate of node d 2 ) + 2 (cost of arc d 1  ( d 4 , d 2 ) ) + 1 (cost of arc d 0  d 1 ) = 5 - the estimate does not change; - right = 2 (estimate of node d 2 ) + 1 (estimate of node d 3 ) + 2 (cost of arc d 0  ( d 2 , d 3 ) ) = 5 - the estimate does not change , and therefore the remains the Marking of arc d 0  ( d 2 , d 3 ) preserved.

Next, node d 3 opens .

![](Images/image00360.jpeg)

 

41\. Step 5. Creating a Decision Diagram

In the last step, node d 3 is opened . Since the arc d 3  d 2 leads to the already allowed node, the node d 3 , followed by the node d 0 , gets the label s=1 . Recomputing the estimates returns the following at node d 0 : 2 (estimate of node d 4 ) + 3 (estimate of node d 3 ) + 2 (cost of arc d 0  ( d 2 , d 3 ). ) ) = 7. The algorithm is complete.

### 3.4. SEARCH ON PLAY TREES

The idea of searching on AND/OR graphs is used particularly often when programming mind games. In this case, a special case of an AND/OR graph called a game tree is commonly considered .

#### 3.4.1. play trees

Suppose there is an antagonistic (there is one opponent) discrete (the number of positions is at most countable) game with complete information (all rules are known in advance and the position is open). It is played by two players, Max and Min , who take turns moving, with Max moving first.

Let's try to come up with a winning strategy for Player Max . To do this, we construct a search graph whose nodes are the allowed positions of the game. In this graph, if B is obtained from A by applying a game rule to position A, an arc leads from the node corresponding to position A to the node corresponding to position B. The root of the tree corresponds to the starting position of the game, and the leaves correspond to positions where the outcome of the game is uniquely determined (i.e. the winner is determined or a tie is established). Then the problem of determining player Max 's winning strategy is reduced to finding a path in the game tree from the root to the leaf corresponding to Max 's winning position . Also, from a position for a Max move it is enough to find at least one solvable node (because we develop a strategy for player Max and we can choose the move we want), while for a Min move all the descendants must be solvable (because we cannot influence player Min 's move choice and must consider all possible moves). Thus the game tree is an AND/OR graph with 1-arcs of nodes for the first player Max (AND) and k- arcs of nodes for the second player Min (OR).

The rules of the game determine the rating F \* of all final positions: F\* \= +  if Max won , F\* \= -  if Min won and F\* \= 0 if the game ended in a draw.

Usually the game is represented not only by an AND/OR diagram, but by a hypertree, so that every position, except the starting position, contains exactly one arc. In this case, of course, there may be some memory loss, as the matching positions resulting from different move orders are stored in multiple instances. Practical observations show, however, that such situations are relatively rare in the most common mind games. On the other hand , several very efficient algorithms for finding a solution for game trees have been proposed (see the following sections) that are not applicable to general graphs. Therefore, when programming intellectual games, memory is usually sacrificed in order to increase the speed of algorithms.

As an example, consider the simplified game of Nîmes [\[57\]](#part0005.xhtml#_ftn57). There are five coins in the stack. One, two or three coins can be taken per turn. You cannot skip a train. Whoever takes the last coin loses. We fig error! The text of the specified style does not exist in the document. .42 shows the complete tree of the game. Below the final positions is who won.

![](Images/image00361.jpeg)

 42\. Nim game tree

#### 3.4.2. mini max

One of the algorithms for finding a solution for game trees is known as the MiniMax method, which was proposed by O. Morgenstern and J. von Neumann back in 1945. J. von Neumann is best known as the forefather of modern computer architecture (von Neumann architecture) and as the creator of game theory and the concept of cellular automata.

If we had a complete game tree, we would start at the bottom, at the end nodes whose rating is given by the game rules (the F \* function for end positions), and everything would be quite simple - e.g. the max player's move, we choose the child vertex with the maximum value evaluation function, and we shift this estimate up, and for the min move \- from the minimum. If the initial vertex as a result of the algorithm had a guess of +  then Max won, if - then Min . That would have decided the game.

For example in Fig. error! The text of the specified style does not exist in the document. .42 Next to the nodes are written static estimates obtained in the indicated way. The illustration shows that Min can always win this simple game if he plays correctly.

But the complete game tree is mostly too big. For example, there are 1040 positions for checkers and 10120 for chess (paragraph 1.1.8). It is physically impossible to build a complete game tree for practically interesting games . But you can apply this idea (starting from the bottom) to a subtree. To do this, you need to build a subtree, evaluate the nodes at the lower level with the scoring function, and go back up the tree, i.e. high.

The minimax method is as follows. Suppose there is a static scoring function of position F , and if the position is considered favorable to Max , then F \> 0, if the position is considered favorable to Min , then F < 0. If Max is chosen among the terminal nodes has then he would choose the position with the highest guess, and if you chose Min then the lowest guess. Also in the minimax method. In the constructed subgame tree (when the full tree cannot be constructed), the leaf positions are evaluated by an invented evaluation function (since the game rules do not provide for evaluation of intermediate positions) and then estimates are propagated up the tree just as in a static evaluation of the whole tree. If the scoring function is well thought out and the tree is built deep enough, the minimax method often yields a truly optimal solution or a solution that is close to optimal.

As an example, consider a Tic-Tac-Toe game on a 3  3 board. Players take turns placing Tic-Tac-Toe in empty squares. The winner is the one who first gets three of their symbols in a row: in the same horizontal, vertical or diagonal row.

The application of the minimax method with a partial game tree depth of 2 is shown in Fig. Fehler! The text of the specified style does not exist in the document. .43 (“Crosses” are denoted by the number 1 and “zeros” by the number 0). The number after the "=" sign in a position is the score.

 

 

![](Images/image00362.jpeg)

 

Rice. Mistake!               The text of the specified style in the document

absence. .43. Part of the Tic-Tac-Toe game tree

We see that the best move for Max when evaluating by the minimax method with a depth of 2 is towards the central cell. As you can see, this is indeed a winning strategy for Max .

However, the minimax method is not always able to select the really best or even good move, it all depends on how well the evaluation function is put together. As an example, consider a slight complication of Nim's game from the previous paragraph. Let the moves allowed and the ending condition remain the same, and the initial number of coins is unfixed and equal to n . We need to come up with a rating function. This is usually done on the basis of observations. Look at Fig Error! The text of the specified style does not exist in the document. .42 as a basis for observations. We see that Max loses at n =1, at n \=2,3,4 Max wins, and at n \=5 Max loses again. That is, for n \= 1 and n \= 5 the weighting function must be negative and for n \= 2, 3, 4 positive. One is tempted to choose as simple a formula as possible that is consistent with observational data and to declare it a “law of nature”, in this case an evaluation function [\[58\]](#part0005.xhtml#_ftn58). The temptation becomes simply irresistible as the residual knowledge of the school algebra course emerges from the depths of memory. In fact, the function has at least two roots, one between 1 and 2 and the second between 4 and 5. As taught in school, consider the product ( n \- 1.5) and ( n \- 4.5) and after rounding the function F ( n ) = - n 2 + 6n\_ \_ \- 7 demonstrating the desired behavior, fully consistent with the available observations: F (1) = -2, F (2) = +1, F (3) = +2, F (4) = +1, F (5 ) = -2. Let's use this evaluation function in the minimax method of playing Nim for n \= 7 with tree expansion to depth 2 (Fig. Error! The text of the specified style is missing in the document. .44 ). This figure shows the initial estimates of the selected function, the estimates calculated using the minimax method, and the thicker arrows of the moves the method selects. We see that the method suggests the right step!

![](Images/image00363.jpeg)

 

Rice. Mistake!               The text of the specified style in the document

absence. .44. Successful application of the minimax method in the game Nim

However, if we try to extrapolate the estimator and go beyond the original observation base, we get a completely useless result. On fig error! The text of the specified style does not exist in the document. .45 shows the tree for the case n \= 10 in the same notation as in Fig. . Mistake! The text of the specified style does not exist in the document. .44 . Minimax gives bad advice, and the move that actually wins is rated the worst by the minimax method!

![](Images/image00364.jpeg)

F=-23 F=-14 F=-7 F=-14 F=-7 F=-2 F=-7 F=-2 F=+1

 

Rice. Mistake!               The text of the specified style in the document

absence. .45. Unsuccessful application of the minimax method in the game Nim

#### 3.4.3.  \-  Cut off

In Minimax, position generation and its evaluation are separate. Generation takes place first, and only then is this generation evaluated. It is possible to carry out the simultaneous evaluation already at the time of the generations in order not to generate anything superfluous. This process is referred to as  -  cutout .

This mechanism was apparently so necessary and relevant in the mid-20th century that many scientists around the world took up its development. Now it is difficult to say who is the author of this procedure, apparently it was repeatedly invented. Samuel (A. Samuel), Richards (DJ Richards), Hart (TP Hart), and others independently proposed early versions of this algorithm. John McCarthy also put forward similar ideas at the 1956 Darmud seminar. Our compatriot Alexander Lvovich Brudno independently discovered the algorithm and published his results in 1963.

Let's consider a simple model example that explains the basic idea  -  cutout . Let there be a game whose search subtree looks like bugs! Source not found. (Left). Suppose we have only expanded and evaluated the left subtree of the node in question (it has a single position and its score is 7). Since player Max always chooses the node with the highest value of the evaluation function, the root position estimate is ≥ 7 regardless of the unexpanded subtree on the right-hand side. Now consider the choice of a move for player Min (Fig. Error! Text of the given style is missing in the Document .46 , right) . Have only one of the two possible positions revealed (her score is 4). Since the Min player chooses the node with the smallest function value, the score of the chosen move is  4.

![](Images/image00365.jpeg)

 

Rice. Mistake!               The text of the specified style in the document

absence. .46. subtrees of a game

Let's continue these considerations and look at Fig. error! The text of the specified style does not exist in the document. .47 .

![](Images/image00366.jpeg)

 

Rice. Mistake!               The text of the specified style in the document

absence. .47. An example of pruning a subtree of a specific game

After considering the right subtree of the node corresponding to the movement Min, it is known that its score will not exceed 4. However, looking at part of the left subtree, it turns out that the score of its root will be ≥ 7\. This means that further expansion of nodes in the left subtree makes no sense since player Min already has a known best option. Therefore, the rest of the left subtree is truncated.

The above example is formalized as follows.

Let  be the lower bound on the value of the score at a given node,  be the upper bound on the value of the score at that node.

Note that the value of  for the Max node cannot decrease and the value of  for Min cannot increase as the nodes are opened. Therefore, the following rules apply.

1.               Min node if its upper bound  is less than or equal to the lower bound  for any of its Max parents. 

2.               Max node if its lower bound  is greater than or equal to the upper bound  for any of its min parents.

Please note that the formula for the cutoff inequality to be tested is formally the same: in the first case    , in the second case    , but these formulas have different meanings.

In the first case, we take the estimate  just obtained for the node Min and compare it with the estimates  for the nodes Max above it . In the second case, we take the estimate  just obtained for node Max and compare it with the estimates  for the nodes Min above it . But in both cases, the fulfillment of the inequality is the basis for truncation.

An example of playing Tic-Tac-Toe is shown in Fig. Error!

The text of the specified style does not exist in the document. .48 .

![](Images/image00367.jpeg)

 

48\.  -  Tic-Tac-Toe Cutoff

Generation and evaluation are carried out as follows. First, three nodes of the second level are generated. Then five third level nodes are created in the left subtree and a score of -1 is obtained for the second level node. In this case, the lower estimate  = -1 can be determined immediately for the root node of the first level . Next, the generation of third-level nodes in the middle subtree begins. The first node has an estimate of -1, giving the upper estimate  = -1 and the cutoff inequality. We see that four nodes cannot be generated at the third level - their generation will not change the estimates of the remaining nodes. There is no pruning in the right subtree – the inequality is not satisfied.

#### 3.4.4. Efficiency  \-  \-Shutdown

How effective is  -  clipping? Let's try to answer this question. In the analyzed example, we saved 4 out of 16 nodes or 25% of the work. Is this indicator restrictive? Is it always achieved?

Let's answer the second question first, it's easier. Answers:

No not always. In fact (in the worst case!) child nodes are generated in descending order for the Min node and in ascending order for the Max node . If, for example, in Fig. Error! The text of the specified style does not exist in the document. .48 Third level nodes in the middle subtree are generated in this order: 0, 0, -1, -1, -2, then only two nodes are pruned (12.5% saving) if the evaluation function fails and estimates of 0 , 0, 0, 0, 0, then no clipping will occur at all.

Let's now answer the first question: what can  -  cutoff yield in the best case? The depth of the tree in question (without pruning) is h , and each node has exactly d children. Then there are exactly N \= d h nodes underneath. Let (best case!) generate vertices for Min - nodes in ascending order and for Max \- in descending order of the values of the evaluation function.

Then it can be shown that using  -  Pruning the number of nodes generated is the same:

N  O ( d

h / 2 )  d 2 ( i.e. h h  / 1 2 ) , / if 2  d ( hh \_  even 1)/ 2  1 if h is odd 

Therefore, the answer to our question is as follows: In the ideal case, the  -  method enables a double search depth compared to the minimax and in any case does not deliver a poorer result.

So we see that the order in which positions are generated and the order in which moves are considered are one of the key factors in programming intellectual games. Unfortunately (or maybe fortunately?) there are no general methods of shunting trains. The enumeration methods in all game programs are roughly the same and similar to those described (published a long time ago and well studied), but the heuristics of the order of considering moves for each game are different (and constitute the author's know-how of the game program).

Practice shows that the strength of the game program is directly proportional to the search depth. For example, a beginner chess player rarely scans a position more than three or four moves ahead. This. The depth of the search tree for a beginner is about 3. Chess masters build a tree in their mind for a dozen half-moves, and if a forced variation is planned, then more. Grandmasters and champions see even further, two dozen half moves. Since they are in the middlegame, they can already predict the endgame.

Modern chess programs, taking advantage of the dramatically increased capabilities of computers, build and evaluate huge game trees, including millions of positions. How come sometimes people still don't lose chess against computers? [\[59\]](#part0005.xhtml#_ftn59)The fact is that a human chess player builds a much narrower tree in his head. In a complex chess position, a strong chess player immediately sees 2-3 best moves out of two dozen possible moves and only analyzes and calculates them in detail. And a chess program discards on average only half of the possible moves , even with the most well-known tricks like  -  cutting . If we conditionally assume that the human branch width in the game tree is constant and equal to 2, and the program is constant and equal to 10, then to search to a depth of 10 using the minimax method, the person must look through 2 = 11 2048 positions and the program 10 11 \= 100,000,000,000 items.

### CONCLUSIONS ON CHAPTER 3

1.               There are a variety of algorithms for finding a solution, also for production systems. Each of the algorithms has an area of application where it is most effective and useful.

2.               In artificial intelligence, heuristic algorithms are used to find solutions, with the efficiency of the algorithm decisively depending on the quality of the evaluation function, which actually determines the heuristic.

3.               Directed graphs and graphs (trees) AND/OR are most commonly used to represent the search space.

## CHAPTER 4

The material in this chapter is based primarily on mathematical logic, the basic concepts of which are assumed to be familiar to the reader. However, all necessary definitions and some theorems are briefly repeated in the first sections. However, we would like to warn the reader that this chapter is by no means a short textbook on mathematical logic. Many important, interesting, and technically complex theorems and concepts of formal mathematical logic are either omitted here, not proved, or given in a simplified formulation. The reason for this is that in this chapter we consider mathematical logic and its main object - the logical calculus - not at all as a goal, but only as a means to represent knowledge in a computer. Our approach to the fine art of mathematical logic in this chapter is extremely pragmatic: we simply use the ready-made language and apparatus without considering the cost to humanity. Of course, the use of logical calculus in AI is only considered on concrete examples. Formal constructions in the main text of the chapter are kept to a minimum. The reader who needs formal constructions is referred to the classic textbook \[19\].

### 4.1. METHOD OF DECISIONS

The representation of knowledge through logical formulas is based on the following idea. We will set up certain formal theories, look for formal proofs in them and interpret the results we have obtained in the subject area in which the intellectual program works. As formal theories we use applied calculus based on the first-order predicate calculus, and as proof-finding method we use the solution method. There are other classes of formal theories and other methods of proof that are used successfully, and we refer to them in Supplements and Digressions, but in the main body of this chapter we confine ourselves to this classic case.

#### 4.1.1. formal theories

Historically, the notion of a formal theory was developed during a period of intense research in the foundations of mathematics in order to formalize logic proper and proof theory. An outstanding German mathematician, David Hilbert, made an enormous, perhaps crucial, contribution to the formation and development of the apparatus of formal theories. Now this device is widely used to create special calculi for solving specific applied problems in the field of AI. David Hilbert wrote: "The theory of proof... gives us a high sense of conviction that at least the mathematical mind knows no bounds and is capable of pursuing the laws of its own thought...".

The predicate calculus we use below is an example of a formal theory, so we start with a brief description of the general concept of a formal theory.

A formal theory is a structure that has the following four necessary components:

\-                     the set A of symbols forming the alphabet of the formal theory;

\-                     the set F of words in the alphabet A, F  A\*, which are called formulas of the theory;

\-                     a subset B of formulas, B  F, called the axioms of the formal theory;

\-                     the set of relations R on the set of formulas, R  F n+1 , which are called the inference rules of the formal theory.

The symbol set A can be finite or infinite (countable). A finite set of letters is usually used to form symbols, which may be assigned natural numbers as indices.

The set of formulas F is usually given by an inductive definition, for example using a generative formal grammar. This set is usually infinite. In addition to the term "formula", the term "suggestion" can also be used. Sentences conforming to the strict definition are sometimes called well-formed sentences, as opposed to arbitrary combinations of characters from A (simple sentences or character strings) . In some formal theories, the status of a well-formed sentence may depend on context or external circumstances. In the following , a formula , unless otherwise specified, means a well-formed formula of the formal theory under consideration. 

The sets A and F together define a language or formal theory signature , traditionally denoted as

 = ( A , F ).

The set of axioms B can be finite or infinite (but countable). When the set of axioms is infinite, it is usually specified using a finite set of axiom schemas and the rules for generating particular axioms from the axiom schema. The most common rule for generating specific axioms from an axiom schema is the substitution rule .

Let's give an explanatory example. The textbook \[19\] says (we quote with slight abbreviations and in the notation used in this book): "Whatever the formulas A , B and C are, the following formulas are axioms:

(A1) ( A  ( B  A ))

(A2) (( A  ( B  C ))  (( A  B )  ( A  C )))

(A3) ((  B   A )  (()  B  A )  B )) »

This is to be understood in the following sense. Let lowercase Latin letters, connectors  and  , and brackets ( and ) be included in the alphabet of the considered formal theory, and uppercase Latin letters are not included. Then the written expressions denoted by the names (A1), (A2) and (A3) are not, strictly speaking, formulas of a formal theory and therefore cannot be axioms. These are precisely the schemes of the axioms. Any formulas can be substituted for the parameters A , B , and C , and the same formula must be substituted for all occurrences of any parameter, and the resulting expression, which is already a formula of this formal theory (note in parentheses that this is the propositional calculus) is declared an axiom. In particular, if we substitute the formula ( b  a ) in Scheme A1 instead of the parameter A , and the formula a instead of the parameter B , (this is briefly denoted as: {( b  a )// A , a // B }), then the formula is (( b  a )  ( a  ( b  a ))), which is a well-formed formula and an axiom of propositional calculus. If we apply the substitution {( a  a )// A , a // B } to the same circuit A1, then we get the formula (( a  a )  ( a  ( a  a ))) which is also an axiom of calculus statements. The set of axioms of the propositional calculus is infinite, although it can only be given by three schemata of axioms.

For applied theories, axioms are often divided into two types:

\-                     logical axioms , borrowed directly from basic formal theory (in our case from first-order predicate calculus);

\-                     non-logical axioms (also called technical or proprietary axioms) that reflect the application specifics and content of a particular application area.

Let's introduce two more concepts related to formulas and axioms.

If there is an algorithm that, according to the presented formula of the theory (a string of characters of the alphabet of the theory), allows us to conclude in finite time that this string belongs (or does not belong) to the class. of well-formed formulas, then the theory is called knowable .

If, in addition, the time is limited by a polynomial in the length of the formula, then the theory is considered effective recognizable .

If there is an algorithm which, according to the formula presented, allows us to conclude in finite time that this formula may or may not be related to the set of axioms, then the formal theory is called axiomatizable .

If, in addition, the time is limited by a polynomial in the length of the formula, then the theory is considered effective is axiomatizable .

The set of inference rules R is usually finite.

The signature, axioms, and inference rules can in general be chosen arbitrarily, subject to the restrictions specified in the definition. However, constructing formal theories just for the sake of formal theories is unproductive [\[60\]](#part0005.xhtml#_ftn60). In the context of this book, we are interested in those formal theories that describe some real objects and relationships between them. The set of real-world objects and the relationships between them is often referred to as a domain . Three important terms - derivability, logical consequence and interpretation - form a circle of terms through which a formal description of informal things takes place .

The formula G is said to be derivable directly from the formulas of the set F 1 , … , F n if among the derivation rules there is such a rule R that (F 1 , … , F n , G)  R.

The formulas F 1 , ... , F n are called premises and the formula G is the conclusion of the inference rule R . In this book, we will usually write direct derivability by separating premises and conclusion with a horizontal bar and specifying the name of the inference rule, if applicable:

F 1 , , F n R .

G

derivable from the formulas of the set F 1 , …, F n in a given formal theory if there is a sequence of formulas

<A 1 , A 2 , …, A i , …, A n \>,

where A n \= G [\[61\]](#part0005.xhtml#_ftn61), and each formula A i is either an axiom or one of the formulas F 1 , …, F n or derivable directly from some earlier formulas according to one of the inference rules R .

That the formula G can be derived from the formulas F 1 , ..., F n is written as follows:

F 1 , …, F n  g\_ \_

The formulas F 1 , …, F n are called conclusion hypotheses , and the sequence itself < A 1 , A 2 , …, A i , …, A n \> is called a (formal) conclusion [\[62\]](#part0005.xhtml#_ftn62).

If the formula G can only be derived from the axioms – without using hypotheses, then G is called a formal theoretical proposition . This fact is indicated by the notation  G.

Above we defined the terms (effective) knowability and (effective) axiomatizability . We think it necessary to make a similar remark on the notion of a theorem, quoting E. Mendelssohn \[19\] almost verbatim: formula whether its derivation exists in the theory. A theory for which such an algorithm exists is called decidable, otherwise the theory is called undecidable. Roughly speaking, a decidable theory is one such a theory for which one can invent a machine that tests formulas for the property of being a theorem of that theory, while in an undecidable theory more and more independent acts of invention are required to accomplish the same task .

We see that the terms derivation, derivation and theorem are purely syntactic, they do not appeal to the semantic notion of truth. When a formal theory claims that a theorem is derivable from axioms, this in no way implies that the theorem is "true" or "correct" in any substantive sense. It simply means that we have found a formal sequence of formulas that begins in a certain way (axioms), ends in a certain way (theorem) and all intermediate formulas are related in a certain way (rules of inference). In order to move on to semantics, it is necessary to introduce the concept of interpretation.

interpretation I of a formal theory into a domain M is a set of functions that map the constructions of a formal theory into a set of objects and statements about objects of the domain M.

Many functions are needed and not one function, since each type of formal construction used in formulas needs its own function. For example, in interpreting the formulas of the predicate calculus (see next paragraph), each formal constant must be associated with an actual object, formal function symbols - specific mappings, formal predicates - specific relations. After that, the formula becomes a meaningful statement, and from a meaningful point of view we can try to check whether the statement is true or false.

The truth value of the formula A in the interpretation of I is denoted by A | denotes I or, if the context clearly shows that it is an interpretation of I , simply by the name of the formula itself with the interpretive feature: A| . The truth value of a formula is always determined by one of the constants true or false in order not to be tied to data records of type A | to be bound I \= true , we write A | I (  A | I ), meaning that the formula is true ( false ) or simply A| yields (  A| ) — taking into account the remark on uniqueness made above.

A formula is called valid (or tautology ) if it is true in any interpretation:  I ( A | I ) .

A formula is said to be satisfiable if there is at least one interpretation of I in which it is true:  I ( A | I ) .

A formula is called unsatisfiable (or contradiction ) if it is false in any interpretation:  I (  A| I ) .

Let there be a formal theory, a specific subject, and a given interpretation . Let T be the set of theorems of the formal theory and P the set of true statements of the subject. If the sets T and P turn out to correspond one-to-one under the interpretation of I , then nothing could be better: all formally derivable statements are meaningfully true, and all meaningfully true statements are formally derivable. In this case, the formal theory is said to be appropriate to the subject. Appropriateness is a powerful and rare quality. In practice, one often has to be satisfied with weaker properties.

A domain is called a model of a formal theory if there is an interpretation I under which all derived formulas in this interpretation are true:  G (  G  ( G | I ) .

A formal theory is considered complete for the subject if there is an interpretation I under which all true formulas can be derived:  G (( G| I )  G ) .  

An adequate theory has a model and is complete in its model.

It must be clearly understood that formal theories are not divine revelations or inherent innate laws of the human mind - formal theories are invented by humans to formalize particular subject areas, and these inventions prove more or less successful depending on the ingenuity of the inventor. One can come up with different formalizations for the same subject area, and this often happens: different formalizations compete with and change each other [\[63\]](#part0005.xhtml#_ftn63).

The semantic concept of interpretation leads to the concept of logical consequence.

follow logically. One says that the formula G follows logically from the formulas F 1 , …, F n (notation F 1 , …, F n  G) if the formula G is true in every interpretation in which the formulas F 1 , …, F n are true :

F1 | \_ I &…&F n | I G | I. \_

Logical consequence is a semantic concept. Derivability is a syntactic concept. They may be related, and they are clearly related if the theory is appropriate, or they may not be so directly related. It all depends on R 's inference rules .

One says that the rules of inference R are consistent if the formal derivability yields a logical consequence: F 1 , …, F n  R G  F 1 , …, F n  G.

The inference rules R are said to be complete 66 if some logical consequence is confirmed by formal deducibility: F 1 , …, F n  G  F 1 , …, F n R G \_

                                                                                                                                                                                     

a theory that served as a model for two millennia, although from today's point of view it was not constructed rigorously and formally enough. Many               mathematicians tried to improve Euclid's constructions. Lobachevsky               , for example, led to the discovery of non-Euclidean geometries. A little over a hundred years ago, David Hilbert wrote the book Fundamentals of Geometry, and this work has become a new quality standard in formal theory. Already at the end of the 20th century, the domestic mathematician AV Pogorelov proposed his axiomatics of geometry, which was very successful and modern, so even the question of introducing this variant of the formal theory as the main variant in secondary education was considered. All these formal theories are different, but the subject matter - a set of meaningfully true statements about the properties of geometric objects - is one!

66 More often the notion of consistency is not used, and completeness is interpreted as equivalence of provability and follows: F 1 , …, F n  G  F 1 , …, F n R \_ G. \_ We found it useful to name and consider separately the two implications that make up this equivalence.

#### 4.1.2. First order predicate calculus language

The main tools of knowledge representation considered in this chapter are the formulas of applied first-order predicate calculus. Even David Hilbert pointed out that "the calculus of first-order predicates is sufficient in all reasonable cases". Here we consider the predicate calculus as a language, as a notation system for writing logical statements. Furthermore, we believe that this language is familiar to the reader at the level of concepts such as logical operators ("AND", "OR", "IF ... THEN") and quantifiers ("for all", "exists"). [\[64\]](#part0005.xhtml#_ftn64).

We consider a language that includes logic operations, quantifiers, and atomic formulas built on a set of function symbols, object variables, and constants. Below is the formal grammar of the first-order predicate calculus language. The following distinguishable sets of symbols are taken as given: the set of constant symbols (notation const ), the set of variable symbols (notation vari ), the set of function symbols (notation func ) and the set of predicate symbols (notation predicate ).

 
| Expression:  || const | Change | Radio (Term List) |
| --- | --- |
| Term list: ||  Therme | term, list of terms |
| Atom:  || predicate | predicate (term list) |
| Literally:  || Atom |  Atom |
| Formula:  || Atom |  ( formula ) | |
|      || (Formula-Bundle-Formula) | |
|      || Perem quantifier (formula) |
| Bundle up:  ||  |  |    |
| Quantifier: ||   |   |

The concept of a literal (atom or the negation of an atom) is generally grammatically redundant. We introduced it to keep that term handy. A predicate with no arguments is also redundant. We introduced it to make the propositional calculus syntactically a special case of the predicate calculus.

A few remarks are necessary on the grammar of this language.

1.               First, in this language we think of our function and predicate symbols as having fixed names and a fixed number of arguments, just like in traditional programming systems. This is a fairly strong assumption and, in principle, it cannot be looked at in that way. In this case we would have to deal with  -expressions and mixed calculations, which is beyond the scope of this course.

2.               Second, the language we use is classified as a first-order language in the logical hierarchy. In other words, this means that only object variables can be put under quantifiers, ie no function symbols and no predicates. Otherwise, i.e. if it is assumed that the quantifier cannot only bind subject variables, it is not a first-order calculus. Such calculi are used in real modern AI systems. For example, the model checking trend is based on temporal logics that look like first-order logics, but are actually reduced to standard non-first-order logics.

3.               Third, the above grammar of the predicate calculus assumes the formal writing of statements in a certain syntax, with all the necessary brackets, etc. Of course, when considering examples, we will greatly simplify the formal syntax and write formulas more conveniently, but in such a way that one can always guess , which syntactic simplifications are used in individual cases . In particular , the usual precedence of connectors and quantifiers is used, additional parentheses are systematically omitted.

4.               Fourth, it is known that the pure first-order predicate calculus has a limited expressiveness. In other words, many meaningful theories are inexpressible or difficult to express in pure first-order calculi, extralogical assumptions are required. Of course we allow constants, function symbols and predicates that are needed to describe the subject area. That being said, however, it is believed that natural numbers and other well-known concepts can be used in any formula without attempting to describe axiomatically what they really are.

5.               Fifth, there are enough closed formulas and open formulas cannot be considered, because if there is an open formula then it is satisfiable if and only if the corresponding closure is satisfiable. Therefore, formulas are written in open form, assuming that all free variables are closed by the universal quantifier.

#### 4.1.3. Offers

In 1965, John Alan Robinson proposed the resolution method to prove the validity of logical formulas . The idea for this method is based on the work of Herbrand, but since he did not think of applying his method to computers (which was not surprising in 1930), Herbrand's method was not very suitable from a computational point of view. Robinson made it suitable for real-world applications and developed a unification algorithm that forms the basis of the method.

The solving procedure is applicable to logical calculi using formulas of a special form called theorems.

Sentence (clause) is a quantifier-free disjunction of literals.

Any formula for the first-order predicate calculus can be reduced to theorems by successively applying the following steps:

1.              removing the implication. The implication is replaced by a disjunction with the negation of the first operand. A  B \=  A  B 

2.              Pull out the negative. Negatives are left only in front of atoms. It follows de Morgan's rules using the property of quantifiers and the involutivity of negation.  ( A & B ) = (  A  B ),  ( A  B ) = (  A &  B ),  x (A) =  x (  A),

 x ( A ) =  x (  A ),   A = A

3.              Separation of Related Variables . Bound variables are renamed so that they don't accidentally match different quantifiers.  x (…  x (… x …)…)=

\=  x (…  y (… y …)…) and similarly for all other combinations of quantifiers.

4.              Reduction to the preform . Convert a formula so that it begins with a quantifier prefix, followed by a non-quantifier matrix. A  x ( B ) =  x ( A  B ) and similarly for all other combinations of quantifiers and connectors.

5.              skolemization . Elimination of existential quantifiers by introducing new function symbols and constants.  x ( A (… x …)) = A (… a …),  x (  y ( A (… y …)))=  x ( A (… f ( x )…)), where a — a new constant and f a new function symbol.

6.              Elimination of universal quantifiers . Since only closed formulas are considered, the remaining universal quantifiers are omitted as they are implied.  x ( A (… x …)) = A (… x …).

7.              Reduction to conjunctive normal form . The main operation in the conjunctive normal form is the conjunction, it connects groups of disjunctions.

A  ( B & C ) = ( A  B )&( B  C ).

8.              Breakdown into Sentences . The formula is broken down into many sentences. A & B = A , B 

This is not the only way to reduce predicate calculus formulas to theorems, there are other equivalent ways. The reduction to propositions is not logically equivalent, but the following assertion is true, which we give without proof.

set . Those formulas that are obtained by reducing the original formulas to sets form an inconsistent set if and only if the original set of formulas does not hold .

Let's consider examples of reducing first-order predicate calculus formulas to propositions using the sequence of actions given above.

Let's reduce the formula to sentences:  x (P(x)  y Q(x, y)).

1)               x (  P ( x )  y\_ \_ Q ( x , y ))

2)              Formula unchanged

3)              Formula unchanged

4)              x \_  y (  P ( x )  Q ( x , y ))

5)               x (  P ( x )  Q ( x , f ( x )))

6)              P ( x )  \_ Q ( x , f ( x ))

7)              Formula unchanged

8)              Formula unchanged

Now let's reduce the negation of the previous formula to theorems:  x ( P ( x )  y Q ( x , y )).

1)                x (  P ( x )  y\_ \_ Q ( x , y ))

2)               x ( P ( x ) &  y (  Q ( x , y )))

3)              Formula unchanged

4)              x \_  y ( P ( x ) &  Q ( x , y ))

5)               y ( P ( a ) &  Q ( a , y ))

6)              P ( a ) &  Q ( a , y )

7)              Formula unchanged

8)              P ( a ),  Q ( a , y )

#### 4.1.4. resolution rule

The solving method uses not only a special kind of formulas, but also a special inference rule.

The solution rule is the rule for deriving a new formula (theorem) from two theorems. Resolution \- A new proposal resulting from the application of the resolution rule.

The resolution rule applies only to sentences containing opposite -equal literals ( P and  P ) and is as follows. Given two sentences (which contain counter-unifying literals), a new sentence can be derived from that pair of sentences by combining the original sentences and eliminating (eliminating) the counter-literals:

![](Images/image00368.jpeg)P  Q 1   Q n ,  P  R 1   R m .

Q 1   Q n  R 1   R m

Remember that we really like to write the inference rules "multi-story", ie like this: the premises ( antecedent ) of the rule are placed above the line, the conclusion ( succedent ) is placed below the line.

The resolution is the union (more precisely, the disjunctive union) of all literals except for a pair of opposites. In this case, both the index n and the index m can have any value. In particular, if sentences are resolved that contain only contraliterals, then the resolution is an empty sentence . Note that by definition, an empty sentence is considered identically false.

The resolution rule is a very powerful rule! Many rules (such as modus ponens [\[65\]](#part0005.xhtml#_ftn65)) are particular manifestations of the resolution rule. Table 4.1 below shows some well-known rules in the traditional form and written in the constraints of the resolution method when premises and conclusions are non-quantifier disjunctions of literals. These examples show that the resolution rule is no weaker than the traditional ones, and anything that can be derived in the traditional way using modus ponens can also be derived using the resolution rule!

table error !               The text of the specified style in the document

absence. .2. Traditional and resolving form of inference rules

Rule Name Traditional Form Operational Form

method setting AA , B A ,  AB 

B B

A BB ,  C \_ \_  AB ,   BC 

A → C → AC

Merger ABA  ,  B AB  ,   AB 

B B

The settlement rule alone forms a complete and consistent set of rules (see point 0). Let us prove this assertion for the case of the propositional calculus by giving suitable simplified definitions.

An inference rule is consistent if the conclusion is a logical consequence of the premises.

Sentence. The resolution rule is consistent .

prove. Let I be any interpretation, C 1 and C 2 are sentences that are resolved according to the resolution rule, P is the literal that is resolved. For clarity, assume that the predicate P enters sentence C 1 positively and enters C 2 negatively . Let ' 1 ' and ' 2 ' be what you get after eliminating the counterliterals from the sentences.

By the condition of theorem I (C 1 ) & I (C 2 ). Then if I (P), then

From 1 '   & I (С 1 ' ), meaning I (С 1 '  С 2 ). If I (  P), then C 2 '   & I (С 2 ' ), which means I (С 1 '  С 2 ' ) anyway. Ch.td

A derivation rule is complete if a valid formula can be derived from this rule.

Sentence. The resolution rule is complete .

prove. As is known, the modus ponens rule for propositional calculus is complete and a special case of resolution, as can be seen from Table 4.1. Ch.td

#### 4.1.5. Union

To apply the resolution method, we need to find the counter literals. This problem does not exist with propositional calculus. Every variable and the same variable with a negation is a pair of counter literals. With the first-order predicate calculus this is not so easy. Even if we found two occurrences of the same predicate, positive and negative, it doesn't mean that an opposite pair was found. Various arguments can follow the predicate letter, which can be different in each case. In some cases it is possible to unify literals by substitution , that is, to make such changes to variables that the atoms of the literals become the same, but in other cases this is not possible. There are algorithms (in particular Algorithm 4.1) that check whether two formulas (particularly two atoms) can be unified and find a set of unifying substitutions if unification is possible. Let's refine the definitions.

A special case of a formula is the result of substituting a specific formula into a given formula in place of all occurrences of a specific variable in the original formula.

Unification is a method of computing a general special case for two formulas (if any).

A unifier is such a set Substitutions of certain formulas for variables, when applied to given formulas, will preserve their general special case.

The least common unifier is the minimal substitution theorem that unifies formulas.

Let's make some general comments about the definitions.

1.               In many formal theories, a special case of a formula is its logical consequence . This applies in particular to propositional calculus formulas and to sentences (quantifier-free disjunctions of literals).

2.               In the vast majority of cases, the formulas have no general special case . Therefore, during unification, it is important to receive a negative response as soon as possible.

3.               In general, instead of replacing a variable, you can substitute a term that contains the same variable. However , such a substitution can never result in union , so such substitutions are forbidden in unifiers.

4.               If  is the most general unifier (standard abbreviation NOU) and  is an arbitrary unifier, then there is a permutation  such that  =  , where  is the sign of composition of substitutions.

For example, two formulas P ( x , f ( a )) and P ( g ( b ), y )) are unifiable, NOU \[ P ( x , f ( a )), P ( g ( b ), y ))\] = { g ( b )// x , f ( a )// y }.

At the same time, the formulas P ( x , f ( a )) and P ( y , g ( b )) are not unified, because f ( a )  g ( b ) for any substitution of formulas instead of variables. Also, the formulas P ( x , f ( a )) and P ( g ( b ), x )) are not unified, since unification requires replacing formula f ( a ) and formula g ( b) instead of the variable x , which is obviously impossible.

We present the classical unification algorithm proposed by Robinson (Algorithm 4.1) in a somewhat simplified formulation. We immediately note that this algorithm is far from the most efficient of them that is currently known. The input of the algorithm are two expressions A and B written in prefix (functional) form, the output is false if the expressions are not unified, or the value is true and NOU  .

Algorithm error ! The text of the specified style does not exist in the document. .fourteen. Union of two formulas.

proc Unify ( in A, B; out  ): boolean

  :=   while doing A  B 

  \[A',B'\] := FirstNeqTerms(A, B)               if  IsSubst(A',B',t,v) then back ( wrong )                            End if

   :=  {t//v}

 A := Subst(A, t, v) B := Subst(B, t, v) end while                return ( true ) end perc  

This algorithm uses the following functions and operations.

1.               The FisrtNeqTerms function compares its arguments from left to right and finds the first subformulae in which the compared formulas differ. For example, if you compare the formulas P ( x , f ( a )) and P ( g ( b ), y )), the FisrtNeqTerms function returns the pair \[ x , g ( b )\].

2.               The IsSubst(A',B',t,v) function checks whether the first argument pair A' and B' forms a valid substitution, ie whether one of these arguments is a variable v and the second is a formula t using this variable v does not contain . For example, if the first and second arguments of the function are x and g ( b ), respectively, the function returns true with the third argument t set to g ( b ) and the fourth argument v set to x .

3.               The Subst(A, t, v) function replaces the formula t in formula A for all occurrences of the variable v . For example, if the function arguments are P ( x , f ( a )), g ( b ), x , then the result of the function is the formula P ( g ( b ), f ( a )).

4.               The operation  is a composition of substitutions. Its execution consists in applying all substitutions of the right argument to all substitution formulas of the left argument, after which the sets of substitutions are combined and the matching and trivial substitutions are removed.

Let's consider an example – protocol of Algorithm 4.1 for a pair of formulas P ( a , x , f ( g ( y ))) and P ( z , f ( z ), f ( u )). In this example, the current values of variables A and B are written on each row, with mismatched subformulae found by the FirstNeqTerms function underlined. The constructed unifier is written out on the right.

P ( ein , x , f ( g ( y ))) P ( z , f ( z ), f ( u ))                               = { ein // z }

P ( a , x , f ( g ( y ))) P ( a , f ( a ) , f ( u ))                             = { a // z, f ( a )// x }

P ( a , f ( a ), f ( g ( y ) )) P ( a , f ( a ), f ( u ))                = { a // z, f ( a )// x, g ( y )// u } P ( a , f ( a ), f ( g ( y ))) P ( a , f ( a ), f ( g ( y )))

We see that the algorithm is ready in just four steps and finds the most common unifier. However, one should not delude oneself into thinking that the task of unification is an easy task. In fact, all the "elementary" operations used in this algorithm - finding mismatched subformulae, checking the admissibility of a substitution, performing a substitution, and even computing the composition of substitutions - are by no means elementary in implementation, and their actual complexity depends substantially on the selected representation of formulas. Meanwhile, the representation of formulas for Algorithm 4.1 is undefined.

Consider another unification algorithm where the formula structure is more explicitly fixed. Regarding the considered method of resolution, we need to check the unification of atomic formulas, the syntax of which is described in paragraph 0. In order not to obfuscate the idea of the algorithm, we leave only functional symbols and variables in the language [\[66\]](#part0005.xhtml#_ftn66).

Algorithm 4.2 assumes that the op function analyzes the formula and returns the sign of the main operation (predicate name, function symbol, or variable name), the var function checks whether its argument is a variable name, and the args function returns the main operation's argument list. The substitution set (unifier) is represented as a global array S , whose index values are variable names and whose element values are formulas that replace the corresponding variables.

Algorithm 4.2 is based on the following idea. Any substitution of formulas instead of variables leaves the main operation (predicate or function symbol) of the formula unchanged. Therefore, if the main operations of the formulas are different, then the formulas are certainly not unified. Otherwise, ie if the main operations match, the formulas are unified if and only if all sub-formulae that are arguments of the main operation are unified. This recursion ends when the match reaches the variables. A variable is unified with any formula that does not contain that variable (especially with another variable) simply by replacing that formula with the variable. But substitutions for all occurrences of a variable must match.

Algorithm error ! The text of the specified style does not exist in the document. .fifteen. Recursive union of two formulas.

proc Unify ( in A, B): bool

 a := f(A); b := f(B)

 // обе формулы суть переменные  if var(a) & var(b) then                                            if a = b then return Is correct End if                              if S\[a\]=  & S\[b\]  then S\[a\] := S\[b\]

return Is correct End if 

 if S\[b\]=  & S\[a\]  then S\[b\] := S\[a\]

return true end if

 if S\[a\]   & S\[b\]  then Unify(S\[a\], S\[b\]) end if

  S\[a\] := b // или S\[b\] := a end if  

 // One formula is variable and the other is not               if var(a)  var(b) then                               if var(a) & a  B then return NOT CORRECT different                                if S\[a\] =  then S\[a\] := B;

return Is correct  

different return (S\[a\] = B) end if  

End if 

  if var(b) & b  A then return NOT CORRECT different                                if S\[b\] =  then S\[b\] := A; return Is correct  

else return (S\[b\] = A) end if  

End if 

 End if 

 // both formulas are not variables if a  b then return false end if

// main operations are different for a  args(A) || b  args(B) do                if  Unify(a, b) then returns false tail if

 end for return Is correct end process

In this algorithm, the loop head for a  args(A) || b  args(B) do means parallel loop through argument lists.

#### 4.1.6. Refutation by the Method of Resolutions

The proof procedure according to the method of resolutions is actually a refutation procedure, i.e. instead of proving the validity of the formula, proving that its negation is largely contradictory, this approach was adopted due to "technical convenience" considerations. This is a typical proof-by-contradiction scheme. Let us prove a theorem that proves the correctness of this schema for the case of the propositional calculus. Sentence. If A ,  G  F , where F is a contradiction, then A  g\_ \_

prove. According to the deduction rate, [\[67\]](#part0005.xhtml#_ftn67)if A ,  G  F , then

 A &  G  F , i.e. A &  G  F is a tautology. But A & G \_  F \=

 ( A &  G )  F \=  A  G \= A  G. \_ So A  G is a tautology and  A  G , which again using the deduction theorem, gives us A  g\_ \_

Ch.td

Since we are considering disjunctive forms, empty disjunctions must be considered identically false. Therefore, it is convenient to use an empty disjunction containing no disjunctive terms as the unsatisfiable formula F mentioned in the previous theorem. This is traditionally done in the solution method, and the empty disjunction is traditionally .

Consequence. When a A ,  G  , where is an empty formula , then A  g\_ \_

With this we can formulate the definition of the solution method.

The solution method is a method for automatic theorem proving based on refuting the set of premises A and negating the objective theorem G using the solution rule.

Consider the procedure for applying the solution method: Suppose it is necessary to find the derivative of A  g\_ \_

1.               Each formula of formula set A and formula  G are independently converted into sets of sets.

2.               Resolvable sentences are found in the resulting set of sentences.

3.               The resolution rule is applied to them, and the resolution is added to the set until an empty set is obtained .

In this case, the following results are possible:

1.               As a result of applying the solving method, an empty formula is obtained. The theorem is proved. We constructed the derivation of formula G from formulas A.

2.               As a result of applying the solving method, no empty formula is obtained, and there are no solvable ones among the current set of sets. We have thus disproved the theorem, which means that the formula G cannot be derived from the set of formulas A.

3.               The process doesn't end. The resolution rule is applied, many proposals are added, among them there are no empty ones, and there are solvable ones. It means nothing .

In other words, the resolution method is a partially correct procedure . The third result cannot be called a loop because there is no way to determine why the resolution procedure produces new resolvents, but it does not produce an empty set. Does this mean that the theorem is true, but we just didn't wait for its completion? Not known. Does this mean that the result will never be an empty formula? And we don't know that either. This is a logically unsolvable problem. In principle, it is impossible to say how long you will have to wait for an answer to this question.

#### 4.1.7. Software implementation of the solution method

All of this can be written in terms of Algorithm 4.3.

Algorithm error ! The text of the specified style does not exist in the document. .16. resolution method.

proc R(S)

 C := S during   Do \_

 Choose (C, p1, p2, l1, l2, s) if p1, p2 = nil then return fail End if                p := Res(p1, p2, l1, l2, s) C := C + p               end while                return OK End perc 

 proc Res (p1, p2, l1, l2, s) p1 := p1{s}; p2 := p2{s} p1 := p1 – l1; p2 := p2 – l2               return p1  p2 end perc 

 

proc Select(C, p1, p2, l1, l2, s)

From the set of sentences C choose two sentences p1, p2, which contain the counterliterals l1, l2, united by the most common unifier ending perc 

Writing these procedures, we use our standard practice of compiling algorithms to solve enumeration problems - what can be fixed is fixed. In particular, the Res method is defined. The floating procedure is the select procedure . The control strategy has been moved to this function, which selects two sets to solve.

example .

Every programmer knows the resolution method.

The solution method is unknown to the students.

Some students are smart people.

So some smart people aren't programmers.

Logically , the last statement is true. Let's check it mechanically using the dissolution method.

Let's introduce a set of predicates describing statements used in the above statements:

P - "to be a programmer",

P - "to know the solution method", C - "to be a student",

U - "to be a smart person."

In the formula language of the first-order predicate calculus, the initial statements (premises) look like this:

 x Ï ( x )  P( x ),  x C( x )   P( x ),  x C( x )Y( x ).

:  x Y( x )  P( x ).

Negation of the goal formula:  x  U( x )  P( x ).

Let's refute it with the method of resolutions.

1\. We reduce the original formulas to sentences:

 x P( x )  P( x ) is converted to  P( x )  P( x ),

 x C( x )   P( x ) is converted to  C( x )  P( x ),

 x C( x )Y( x ) is converted to C( a ) and Y( a ),  x  U( x )  P( x ) is converted to               U( x )  P( x ).

Thus we have the following set of sentences S :

S \= {  P( x )  P( x ),  C( x )  P( x ), C( a ), Y( a ),  U( x )  P( x )}

2\. Apply the resolution rule to the 4th and 5th sentences and add them to the sentence sentence:

S \= {  P( x )  P( x ),  C( x )  P( x ), C( a ), Y( a ),  U( x )  P( x ), P( a )}

3\. Apply the resolution rule to the 1st and 6th sentences and add them to the sentence sentence:

S \= {  P( x )  P( x ),  C( x )  P( x ), C( a ), Y( a ),  U( x )  P( x ),

P( a ), P( a )}

4\. Apply the resolution rule to the 7th and 2nd sentences and add them to the sentence sentence:

S \= {  P( x )  P( x ),  C( x )  P( x ), C( a ), Y( a ),  U( x )  P( x ),

P( ein ), P( ein ),  C( ein )}

5\. Apply the resolution rule to the 8th and 3rd sentences and add them to the sentence sentence:

S \= {  P( x )  P( x ),  C( x )  P( x ), C( a ), Y( a ),  U( x )  P( x ), P( a ),

Р( a ),  С( a ), }

We got an empty sentence, i.e. a refutation of the negation of the goal formula, i.e. the goal formula is proven.

Usually, the output of the resolution procedure is written in abbreviated form: sets are numbered, the set is written out as a sequence of               added resolvents, and for each resolvent the numbers of the resolved sets are given. For example, in abbreviated form, the constructed output looks like this:

1.                P( x )  P( x )

2.                C( x )  P( x )

3.               C( a )

4.               U( a )

5.                U( x )  P( x )

6.               P( a ) (4, 5)

7.               P( a ) (1, 6)

8.                С( a ) (2, 7)

9.                 (3, 8)

In the following examples, resolution method conclusions are written in abbreviated form.

### 4.2. Strategies for seeking refutation through the method of resolutions

One of the main questions about the resolution method is where to get the Select function that selects a pair of resolvable sets. This is the key question. A well-chosen function can quickly lead to the goal. An unsuccessful one will generate more and more non-empty resolutions without giving a solution. 

The manner in which proposals are selected for decision-making is known as the decision-making strategy .

#### 4.2.1. Complete Strategies

The key concept related to strategies is the idea of completeness. We keep returning to the concept of “ completeness ” – in its various manifestations – and do so quite consciously. We are absolutely sure that the use of this or that tool (in any sphere of human activity, including programming) should always be accompanied by a clear understanding of all the possibilities and limitations inherent in this tool. We sincerely hope that after carefully reading this book, the reader will be able to use the remarkable results in the field of knowledge processing not as a "magic wand", but with an understanding of all the intricacies of the tool and the ability to function if necessary to introduce even more new ones. wonderful improvements.

A complete strategy is               such a search strategy

Refutation knowing that if there is any refutation by the solution method, there is also refutation by this strategy.

Consider two well-known complete strategies.

1\. Breadth search strategy ( brute force search ) . 

all possible resolutions at each step (the strategy is obviously complete since each derivation will be contained in a complete enumeration).

Let's consider exhaustive search using the example of a problem about programmers and students who know or don't know the solution method (see section 0).

 
|  P( x )  P( x ) ||  С( x )  Р( x ) С( a ) || U( a ) ||  U( x )  P( x ) |
| --- | --- | --- | --- |
|  P( x ) С( x ) || P( x )  Y( x )  P( a ) || П( a ) ||   |
|  P( a ) ||  C( x ) P( a ) Y( x ) ||  C( a ) P( a ) ||  U( a ) |
|  C( a ) ||     ||   ||   |

The first line consists of the original five sentences. Recall that these are sentences obtained by converting the conditions of the problem into the form of sentences and negating the goal sentence.

The second line contains a full enumeration of all sets obtained by solving the first line (the original sets). The third line contains any new sentences obtained by resolving the sentences contained in the first two lines. An empty square appears in the fourth row when solving Y( a ) from the first row and  Y( a ) from the third row.

As a result, after the third complement of the initial propositional sentence, an empty proposition is constructed and the conclusion is completed, but before that quite a lot of propositions are constructed that do not participate in the output, they are certainly redundant. This is the exhaustive search strategy. It's not efficient like most complete strategies, but it always ends in a positive result for us - we get the answer if there is one.

2. linear strategy. 

In the case of a linear strategy, at each step except the first, one of the solvable sets is the last set received, the last solver. The very first set is called the top one. The set obtained from the previous step (for the first step this is the top set, for the subsequent steps it is the last resolution obtained) is called the central . The second solvable set is called lateral . Thus, the side set is either the original set or one of the previously received central sets.

Linear resolution seems to be more efficient than brute force for the same problem. We choose the first sentence from the original set of sentences as the top sentence

 P(x)  P(x)  S(x)  P(x) S(a) Y(a)  U(x)  P(x).

We choose the first matching clause for the subordinate clause and write the output as a sequence of clause pairs: the central one on the left, the lateral one on the right.

 
|  P(x)  P(x)  S(x)  P(x) ||   |
| --- | --- |
|  P(x)  S(x) S(a)  ||   |
|  P(a)  P(x)  P(x)  P(a) ||  U(x) oder P(x) |
| P(a) → C(x) → P(x) Y(a) U(a) ||   |
|  С(а) С(a)   ||   |

All suggestions that are received in the course of the solution are advertised here. There are slightly fewer of them (11) than the exhaustive search (16). In this case, however, an empty supply only appears on the sixth replenishment level. However, this means nothing. In another case, an exhaustive search may be more efficient.

Of course, there are other examples of complete strategies that are widely reported in the literature \[6\].

#### 4.2.2. Incomplete Strategies

An incomplete strategy is a strategy that does not have the completeness property.

If the algorithm of the resolution method does not complete its work with an incomplete strategy, then this does not mean that the proof does not exist, but that it cannot be found with the chosen strategy.

However, such strategies are often used because incomplete strategies are often more efficient than complete strategies. In fact, incomplete strategies may not get proof even if there is one, but when they do, they work faster.

Furthermore, a strategy that is incomplete in the general case can turn out to be complete if we restrict the original class of theorems.

Let's look at three examples.

1.               Single resolution ( search from data ).

This is a strategy where one of the solvable sentences is a positive literal (fact).

2.               Negative resolution ( search from target ).

This is a strategy where one of the solvable sets is a negative literal (target).

3.               input resolution.

This is a strategy in which one of the resolvable sentences is selected from those entered, i.e. first suggestions are made.

In the general case, all these strategies are incomplete. In particular, the input strategy, which is a special case of a complete linear strategy, is not itself complete.

An example demonstrating the incompleteness of the input strategy:

1)              PQ \_ \_

2)              P  Q

3)               P  Q

4)              P  \_ Q \_

5)              P (1, 2)

6)              Q (5, 3) 7)  P (6, 4)

8)   (7, 5)

Note that the derivation is constructed but is not a derivation according to the input strategy - the clause P is not an input. It is easy to see that for the set of sentences 1-4 there is no refutation by the input strategy.

#### 4.2.3. horn suggestions

There is a subclass of proposals that is very important from the point of view of the practical application of the decision-making process. Let's try to syntactically describe the common properties of the following sentences:

A                 Data

A 1 &…& A N  B  Rules

B                 Goals

When translated into sentence form, these formulas look like this:

A

 A 1  ...  A N  B 

B \_ 

Horn remarked at the time that these three formulas in the form of sentences have the following syntactic feature: they contain no more than one positive literal. The above are all three possible cases: a positive literal (fact), a positive literal and several negative (rule), no positive literals (a negative literal - goal).

Sentences containing at most one positive literal are called hornian .

In addition, the set of such propositions (Horn formulas) is closed according to the resolution rule. If we solve the Horn sets, we get another Horn set because we delete one positive and one negative literal, for a total of at most one positive literal in the solution.

The approach to applying the resolution method to programming was not developed by Horn but later by Robert Kowalski. It turned out that the search method from targets and the search method from data, which are not complete in the general case, are complete in the Horn case. If there is a derivation, then there is a derivation of goals for the Horn case.

Based on Horn's case, the Prolog language was developed and is sometimes referred to as logic programming . However, the concepts of prolog and logic programming should not be identified. The Prolog language is a special case of logical programming, namely an implementation of the solution method for the Horn case with the "search for goals" strategy. You can use other approaches: either apply a different strategy, or take a different subclass of formulas, or even consider non-first-order calculi - and all this will be logic programming, but not Prolog.

#### 4.2.4. Notes on implementation

It is easy enough to develop a simple logic programming system or an automatic theorem proving system. However, all these naive implementations turn out to be practically useless. This is because several important factors are not taken into account:

1.               The decisive factor is not the choice of resolution strategy, but the quality of the settlement process. The unification procedure tests whether two literals are unifiable and, if so, creates a substitution that unifies them. More than 90% of the logic programming system's machine resources are devoted to unification. The unification procedure specified in section 0 is not effective at all.

2.               Most programmers try to write a unification program that gives the answer as quickly as possible - a series of replacements. And in this case (for unification) it is necessary to create a program that would not get an answer as soon as possible, since most literals are not unified. You have to fail as soon as possible , stop executing the procedure, you don't have to calculate the answer. It probably doesn't need to be calculated. This requires subtle programming tricks.

3.               Most operations and relations encountered in real problems have special properties: commutativity, transitivity, and so on. If they are not used, what is actually essentially unified will turn out to be ununified. And when they are used at the logical level, the number of axioms increases many times. Of course, the consideration of things like transitivity and commutativity must be done at the level of unification of concepts and not at the level of logical axioms.

### 4.3. GET RESULT

The resolution procedure forms the proof of the theorem. Answers (knowledge) of any kind can be extracted from the proof with the help of special techniques. Special techniques are required for the following reason. The solution method works only with sentences, but the user sets the actual task not in the form of sentences, but in the form in which it is convenient for him. Before applying the solution method, it is necessary to transform the problem in the form of proposals. Returning a mere proof as an answer is not very user-friendly, it is necessary to extract from the proof what the user expects as an answer.

#### 4.3.1. Get result (yes/no)

The strategies of the solution method considered so far have given an answer to the question whether the solution is derivable or not, ie a binary answer to the question is obtained, yes or no.

example .

Consider the following statements.

1) All students of group 5057 know the solution method.

Vlasenko [\[68\]](#part0005.xhtml#_ftn68)is a student of group 5057.

Does Wlassenko know the solution method?

When translated into sentence form and resolved, we get the following output:

1)               5057( x )  P( x )

2)              5057 (Vlasenko)

3)               P(Vlasenko)}

4)              P(Vlasenko)} (1, 2) 5)    (3, 4)

The answer is yes since we received an empty set.

2) All students of group 5057 know the solution procedure.

Khalepsky does not know the method of resolutions.

Is Khalepsky a student of Group 5057?

1)               5057( x )  P( x )

2)               P(Khalepsky)

3)               5057 (Chalepsky)

4)               5057 (Khalepsky) (1, 2) - coincides with 3

The answer is no , since there are no solvable sentences and no empty sentence.

This is the extraction of the result. With the help of the chosen strategy we were able to get an answer to the question asked.

It may seem that the "yes-no" answer is an edge case, considered for educational purposes only. In fact, this is far from the case. Here are some examples of expert systems that give a simple "yes-no" answer while being both quite real and very complex.

1)              environmental monitoring. Received such and such data from observations. Is there a threat that requires the evacuation of the population?

2)              missile defense system. A moving object has been detected. Is this object an enemy missile?

3)              exploration system. Collected indirect data about a specific area. Are there oil reserves in the area?

#### 4.3.2. Extracting Results ( Facts ) 

And now let's try to pose the question in such a way that we don't get an answer in the form of yes or no, but in the form of a fact. To do this, you need to modify the resolution method by introducing a special predicate, traditionally called the ANS predicate [\[69\]](#part0005.xhtml#_ftn69). An ANS predicate is a predicate that accumulates the answer value. This predicate is considered equivalent to an empty clause. If there is a sentence containing only ANS predicates, then it is an empty sentence.

example :

All students of group 5057 know the resolution procedure.

Vlasenko is a student of group 5057.

Korolev is a student of group 5057.

Who knows the solution method?

the target sentence P( x ) looks like this: if P( x ), then ANS( x ), i.e. if x knows the solution method, then x is the answer. In the formal notation in the form of sentences, the question has the form

 P( x )  ANS( x ). We remind you that in terms of output control, ANS = .

We carry out a final conclusion and get 6 proposals, the last of which is ANS (Vlasenko), that is, we get the answer:

1)               5057( x )  P( x )

2)              5057 (Vlasenko)

3)              5057 (Korolev)

4)               P( x )  ANS( x )

5)               5057(x) ANS (x) (1, 4)

6)              ANS (Vlasenko) (5, 2)

They can stop doing this or continue building new syllogisms               , as can logical programming systems based on the Prolog language. Then all the answers that can be obtained from the conditions of the problem are obtained.

7)              ANS (Queen) (5, 3)

#### 4.3.3. Retrieving Results (Terms)

With the ANS predicate technique one can obtain not only facts but also results at the procedural level. Based on this, it is possible to synthesize an expression (term) that calculates a function.

example :

There is a relationship between father and grandfather. The axioms describing this situation are as follows: Every human being has a father, and the father's father is the grandfather.

O( x , y ) = x father of y

D (x, y) = x äää y 

 x , y , z O ( x , y ) & O ( y , z )  D ( x , z )  y  x O ( x , y ).

Then we ask the question: Who is the grandfather of x ? ? D( y , x )  ANS( y )

As a result of applying the resolution method, the following conclusion is drawn:

1)               O( x , y )  O( y , z )  D( x , z )

2)              O( f ( y ), y )

3)               D( y , x )  ANS( y )

4)               O( y , z)  D( f ( y ), z ) (1, 2, f ( y )// x )

5)              D( f ( f ( y )), y ) (4, 2, f ( y )// y , y//z)

6)              ANS( f ( f ( x ))) (3, 5)

where f is the father computation function obtained by skolemizing (eliminating existence) the second axiom of this example.

The answer is that the grandfather of xf is ( f ( x )) .

Thus, from the point of view of knowledge representation, the solution method is a thoroughly adequate means. It allows you to get meaningful answers to meaningful questions.

### 4.4. RULES-BASED DEDUCTION SYSTEMS

consider together the different types of knowledge representation that we have discussed in the previous chapters, namely knowledge representation based on the production system and knowledge representation based on the first-order predicate calculus. In fact, there is no insurmountable line between them. These are all reducible variations on the same theme, giving reason to believe that it is in fact a subject called Representation of Knowledge. If these were absolutely disparate things, then it would be completely incomprehensible why they should be combined in one course. We shall now easily ascertain that they are not disparate at all [\[70\]](#part0005.xhtml#_ftn70).

First, we will analyze what motivates us to combine different systems of knowledge representation. Then look at the AND/OR form from a different perspective, which has already appeared twice in this textbook under different names: the first name was "decomposable production systems", the second "search on game trees". We will revisit this aspect of knowledge representation and try to show through three examples that there is a common content and deep inner relationships between the techniques and techniques used here. At the end of this chapter, three variants of a particular technique called the "rule-based deduction system" are demonstrated.

#### 4.4.1. Loss of Implicitivity

Let's examine the shortcomings inherent in the solution method. This method has two main characteristics, which in some cases can be considered as disadvantages.

The first feature is that the resolution method works with applications - with quantifier-free disjunctions of literals. These disjunctions have no direction. In fact, the order in which the letters appear in a sentence is very important because all algorithms linearly scan and analyze the information in the order in which the letters appear in the formulas. This order can be important.

If we compare the solution method with the usual proof method based on the modus ponens rule, then this rule itself contains an explicit reasoning. The modus ponens rule looks like this:

A , A  B

![](Images/image00369.jpeg) 

B

It is clear that in this case you must start with A , and then we come to B. There is an explicit reasoning given by the arrow itself. But if we eliminate the implication arrows when reducing formulas to propositions, this direction can be lost.

example .

( A \_   B )  C   A  B  C 

( B\_ \_   C )  A   AB \_ \_  C 

The above are two completely different implicative rules reflecting different semantics, and after converting them into sentences, this difference disappeared. The resolution method doesn't know where to start and where to go. He has all the letters the same, he just sorts them mechanically, tries to deduce an empty sentence, but in which direction to move in order to output an empty sentence - this information is not available, it is lost, although it may be in the original formulation of the problem were present.

Setting up a problem for an automatic proof system is the job of an expert filling the knowledge base. He knows which way to use the implication and could prompt the system. For example, an expert may know that instead of a direct rule  A  B should use the contrapositive form  B  A. But when they are reduced to sentences, clues are forgotten. The resolution method only sees Formula A  b . This is the first disadvantage of the dissolution method. This property is called loss of implicitivity .

#### 4.4.3. propagation of literals

The second disadvantage of this method is the following. When converting into sentences, we use the subjunctive form, and at the same time the formula can be expanded, that is, the total number of occurrences of predicates in formulas can increase. In other words, what is known as literal multiplication can occur. With the resolution method it can turn out (and turns out in the worst case)               that the coefficient of expansion observed here is exponential in nature.

example :

Vlasenko is a distinguished student in group 5057.

All who study in this group are students, all students know the solving method.

High performers are smart.

Let's try to show the following fact: There is a student who knows the solving method and is either a programmer or a smart guy.

We introduce the corresponding predicates and write down the formulas.

0)              .  x Ð ( x )  (Ï( x )  Ó ( x )) Target

 
| 1) .5057 (Vlasenko)  || fact |
| --- | --- |
| 2) .O(Vlasenko)  || fact |
| 3)  x 5057( x )  C( x ) || Regel |
| 4)  x C( x )  P( x )  || Regel |
| 5)  x Þ ( x )  Ó ( x )  || Regel |

Let's turn formulas into sentences. According to the rule of resolution method, a negation must be attributed to the target in front. In this assignment, the first statement is split in two, and the predicate P, which was present once in the original version, appears               twice after the transformation of p.               Now let's start with the resolution.

1)               P ( x )   Ï ( x ) 2)  P ( x )   In ( x )

3)               Ñ ( x )  Ð ( x )

4)               5057 ( x )  С ( x )

5)              5057 (Vlasenko)

6)               ( x ) О  У ( x )

7)              About (Vlasenko)

8)               P ( x ) (  C( x ) (1, 3)

9)               P ( x )  5057 ( x ) (8, 4)

 
| 10)  P ( x )   || (9, 5) |
| --- | --- |
| 11)  Ó ( x ) (  C ( x )  || (2, 3) |
| 12)  Ó ( x ) (  5057 ( x ) || (11, 4) |
| 13)  U (Vlasenko)  || (12, 5) |
| 14)  O (Vlasenko)  || (13, 6) |
| 15)      || (14, 7) |

Points 8, 9 and 10 are deductions, resolutions obtained in the simplest way. We take the first two matching sets and start solving, points 8, 9 and 10 in this example are the first matching, and it's easy to figure out that we don't need the resulting  P( x ) at all. This result is then not used anywhere. Programmers were not mentioned at all in the source data. This is a waste of machine time and memory running unneeded output. Paragraph 11 (dissolution of sentences 2 and 3) had to be started immediately; sentence 1 did not have to be taken into account. The atomic formula  P( x ) that appeared in Theorem 1 resulted from the multiplication of literals and of course proved detrimental to solving the problem.

The conclusion is built, but along the way there was a false move caused by the multiplication of literals that follows from the conversion to conjunctive normal form taking place. As a result, the number of occurrences of literals in sentences increased and the output lengthened. In the worst case, such an increase can be exponential.

#### 4.4.3. Natural withdrawal direction

Let's look at the same problem from the other side. We will not reduce the original formulas to propositions and apply the resolution rule, but we will apply the usual modus ponens rule. We omit the proof by contradiction, but instead use the direct deduction. This makes everything much better, easier and faster:

1)  x Ð ( x )  (Ï( x )  Ó ( x ))               target

 
| 2) 5057 (Vlasenko)  || fact |
| --- | --- |
| 3) O (Vlasenko)  || fact |
| 4)  x 5057( x )  C( x ) || Rule |
| 5) x C( x )  P ( x )  || Regel |
| 6 ) x ( x ) Ó ( x )  || Regel |
| 7) Mit (Wlassenko)  || Method of setting 1, 3 |
| 8) P (Wlasenko)  || Setting Mode 6, 4 |
| 9) U (Wlassenko)  || Mode setting 2, 5 |

10)        P (Vlasenko)  U (Vlasenko) Regel  +, 8

11)        P (Wlasenko)  (P (Wlasenko)  U (Wlasenko)) Regel & +, 7.9

12)         x Ð ( x )  (Ï ( x )  Ó ( x )) Regel  +, 10

Sets 1 and 3 of modus ponens give C (Vlasenko), 6 and 4 give P (Vlasenko), 2 and 5 give U (Vlasenko) and apply rules that have no analogue in the method of resolution, but which are apparently consistent are , we get the goal. We see that the direct system (ordinary reasoning and not a method of proof by contradiction) is simple reasoning according to the modus ponens rule, and the introduction of additional connectors much faster than in the first case allows you to get the same answers.

Here lies the main idea. We want to keep the advantages that the representation of knowledge by sentences offers us and eliminate the disadvantages that this representation gives us. We want to get rid of literal multiplication and keep the direction of implication so that we can make efficient and short derivations as in the second case compared to inefficient and long derivations in the first case.

#### 4.4.4. Form AND/OR

Let's try to convert the original formulas with which our knowledge of the subject is written (arithmetic formulas of the first order) not into the form of sentences, but into the so-called AND/OR form , by simply carrying out fewer conversion steps. Just as when reducing to sentences in the resolution method we eliminate the implication, pull in the negation, eliminate the existential quantifier, construct the prenex form, eliminate the universal quantifier and separate the variables in the main conjunctions (see paragraph 0).

As you have noticed, the subjunctive phase has been skipped. Whatever form it was, that form has remained, we just got rid of quantifiers and separated the variables. It is easy to see that the number of literals is conserved as a result of eliminating the implication, drawing the negation, eliminating the existential quantifier, constructing the prenex form, eliminating universality, and renaming variables.

Note that the AND/OR form can be obtained from any predicate calculus formula .

Example:

The formula is given (Fig. Error! The text of the specified style is missing from the document. .49 ):

 u  v (Q( v , u )   (( R ( v )  P ( v ))  S ( u , v )).

In order to use the AND/OR form, it is proposed to represent the formula in the form of a hypergraph as follows. Where the main operation is  , two separate 1-arcs are placed, where the main operation is  , a 2-arc is placed. The justification is very simple. If that is known  B , you can take the argument one way by using what 's given to A , and you can go the other way by using what 's given to B. If given a  B, we don't know which direction to move concretely, we have to move in both directions at the same time.

 u  v ( Q ( v , u )  (( R ( v )  P ( v ))  S ( u , v )) Q ( w , A )  ((  R ( v )  P ( v ))  S ( A , v ))

![](Images/image00370.jpeg)

 

Rice. Mistake!               The text of the specified style in the document

absence. .49. Hypergraph representations in AND/OR form

Obviously, the set of propositions into which the root formula is transformed can be read as the set of terminal vertices of all solution graphs lying on this hypergraph (Fig. Error! The text of the specified style is missing in the document. .49 ). There are three solution graphs on this hypergraph. One goes from the root to Q , the second goes from the root to the next level and then needs to be connected to S since there is a 2 arc. We are interested in terminal nodes. If the original form is reduced to sentences, there are three of them: Q ,  R   S ,  P   p \_

Note this circumstance, the AND/OR form stores the same information that we had in the solution method, as well as other information.

Consider the following way of constructing a proof engine—the core of an intelligent inference system in the form of a rule-based deduction system.

#### 4.4.5. direct trigger system

As is usual in logic programming, we need to divide the entire set of formulas, all the information we have on a given topic, into three classes: facts, rules, and goals.

This results in the following syntactic restrictions:

\-                     What we consider facts is actually not limited by anything and can be presented in any form AND/OR;

\-                     What we consider rules must necessarily be of the form L  W , where L is a literal and W is any formula represented in the form AND/OR;

\-                     the target must be a disjunction of literals, that is, it must be a sentence. In other words, one can formulate a termination condition: the target formula is a sentence, the solution graph ends in the target literals.

The meaning of the method of growing the AND/OR graph using rules is simple. Let's take a fact (or set of facts) and represent it in AND/OR form. Get a hypergraph. Let's start by attaching rules to the leaf nodes of this diagram. Each leaf node of the constructed graph is unified with the left-hand side of the rule. If the union is successful, we grow the graph (or tree) AND/OR around the right-hand side of the rule until a decision graph appears in this graph whose leaves fall in the goal nodes (i.e. with which goal literals are unified). If the left side of the rule is identified with a leaf node in the diagram, some substitutions may need to be made to unify. It is clear that when different rules are applied in different decision columns, they are applied independently. But in a solution graph it is impossible to replace the same variable with different terms at the same time. Such cases should therefore be ruled out. In fact, the mechanism now described is a special case of the resolution method performed using graph rebuilding.

let's look at this with an example.

Fact: Vlasenko is smart and knows the solution method or he is not a student:

 S(V)  (R(V)  U(V)).

Rule 1: All students in group 5057 are students:  C( x )   5057( x ).

Rule 2: He who knows the method of dissolution is an excellent student:

P( y )  O( y ).

Objective: There is someone who is either not studying in group 5057 or is an excellent student:

z \_  5057( z )  O( z ).

The example of rule 1 shows the advantage of a direct rule-based system. The designer of the knowledge representation system for a specific department can write down this rule – “all students in group 5057 are students” in a counter-positive form: “If he is not a student, then he is not studying in group 5057”. Therefore, the designer of the knowledge representation system (human) gives the inference program a hint: in deductive systems it is more profitable to infer from the general to the particular, and not from the particular to the general. That's exactly what Rule 1 does. That's why staying implicit is so important and useful.

We build direct deductive reasoning and do not use the method of proof by contradiction. Unlike the resolution method, negation should not be applied to the target. The goal should be used as it is in the problem statement. In this case it is clear that after Skolemization the goal will be a quantifier-free disjunction of literals, which is required in the syntactic condition of the direct deduction system.

The rationale is as follows (Fig. Error! The text of the specified style is missing from the document. .50 ).

![](Images/image00371.jpeg)

 

Rice. Mistake!               The text of the specified style in the document

absence. .fifty. Extending a form AND/OR applying rules 

Initially, the fact graph has the following list of leaf nodes:  C(B), P(B), and Y(B). We use our rule 1 to grow the tree. The left-hand side of the rule is unified with the "B" substitution for x . The tree is incremented by the right side that is merged with the first target literal. This isn't a solution yet because we haven't created a decision graph that ends with target literals yet. So we continue to apply the rules. Rule 2 is triggered and the result is identified with the second target literal.

A decision graph is created ending with goal literals (circled in the figure). In order to save information about the substitutions, we introduce suitable arcs (in the figure they are represented by thick unfilled arrows) connecting the literals to be replaced and the left parts of the rules.

Let's consider another example.

Given a fact: P(x)  Q(x)

Rule 1: P(A)  R(A)

Rule 2: Q(B) → R(B), where A and B are concrete constants.

Target: R(A)  R(B)

Note that the goal is not a logical consequence of the facts. This example explains the meaning of the condition that the substitutions on the matching arcs in the same decision graph must be consistent (Fig. Error! The text of the specified style is missing from the document. .51 ).

![](Images/image00372.jpeg)

Rice. Mistake!               The text of the specified style in the document

absence. .51. Inconsistent substitutions on matching arcs 

It can be seen that the replacements are incompatible: you have to replace A with x and B with x at the same time . As a result, the substitutions are not consistent, the decision graph is not constructed as it should be because the goal is not a logical sequence of facts and rules.

The example discussed in the previous section was quite instructive. We have performed resolving inference in the technique of graphs, but the applicability of this technique is limited by the fact that we have syntactic restrictions on the form of facts, syntactic restrictions on the form of rules, and syntactic restrictions on the form of gates.

#### 4.4.6. Reverse trigger system

Let's recall some definitions and facts familiar to the reader from the study of discrete mathematics.

If f(x 1 , …, x n ) is a boolean function, then the boolean function is f\*(x 1 , …, x n ) =  f(  x 1 , …,  x n )

is called the dual Boolean function .

dual resolution method, in which sentence-like elements are not literal disjunctions but literal conjunctions. In the dual solution method, not existence but universality is skolemized, and disjunctive normal form is used instead of conjunctive normal form ( k is a connective for conjunction, 1 is a connective for disjunction). The main operation is the disjunction. In the dual resolution method, we will reduce the negation of the target formula along with the original ones to an identically true formula, which will also have an empty form because the empty conjunction is identically true.

We omit the obvious technical details of these formal logical constructions since our goal in this section is not to work with logical formulas but with AND/OR graphs.

Now we can also construct a syntactically limited, but on the other hand rule-based derivation system. You can go from the facts to the goal, or you can, and sometimes it is more convenient, to go from the goals back to the facts following the reverse rules . As a result, we see that we now have an unlimited form of goals - this is any form of AND / OR. We have a limited form of rules, but in a very different way. In the rules, the right part must now be literal and the left part can be arbitrarily complex. In addition, the form of facts is limited. This must of course be a conjunction of literals and not a disjunction as in the case of the direct system.

The termination condition is the same: fact is a conjunction of literals, the agreed decision graph ends in facts. The original goal, represented in the form of AND / OR, can be built up with the help of inverse rules until it is based on facts.

Let's consider an example: we will build an inverse deduction system based on rules that solve inequalities.

 
| P1: x \> 0 & y \> 0 ||   || xy \> 0 |
| --- | --- | --- |
| П2: x \> 0 & y \> z  ||   || x \+ y \> z  |
| П3: x \> w & y \> z  ||   || x \+ y \> w \+ z  |
| П4: x \> 0 & y \> z  ||   || xy \> xz  |
| П5: 1 > w & x \> 0 ||   || x \> xw  |
| П6: x \> ( wz \+ yz ) ||   || x \> ( w \+ y ) z  |
| П7: x \> wy & y \> 0 ||   || x / y \> w  |

There are seven rules. In each of them there is a literal on the right-hand side, since in general only one predicate is considered in the problem. The left side can be a single predicate or a conjunction of predicates. Thus, in their syntactical form, these rules are suitable for application in the reverse deduction system.

There is a conjunction of facts that is as follows. Facts:               A, B, C, D > 0 C > D

The goal is such a non-obvious statement.

Goal: B(A+C)/D > B

The course of the argument is shown in Fig. Fehler! The text of the specified style does not exist in the document. .52 .

D ![](Images/image00373.jpeg)/ z2 \_

 

  .52. Solving an inequality with an inverse deduction system 

Let's consider the first inequality. Here the main operation is division. Of course, for union, rule 7 works, there are no other rules with division on the right-hand side. This is the first

corresponding rule. Rule 7 is x \> wy & y \> 0  x / y \> w ,

where x is identified with B(A+C) while y is identified with D; w is identified with B. We replace the right side of the rule. We get two new goals: D > 0 (this is given) and B(A+C) > BD. Here the fourth rule is applied, multiplying on the right side.

Two sub-goals appear: B > 0 and A + C > D. Two rules apply to the second part - the third and the second. In this case, the third rule reduces to the second if w \= 0 and we have only three variables in the subgoal A + C > D, then applying each of these rules is equivalent. The problem is different - we can do the union in different ways because of the commutativity property. The first substitution leads to the result and the second leads to a dead end, and nothing can be done about it. We check that all substitutions are consistent, which means that a solution graph has been created. Note that we've used each instance of the rules with their own private variables, so there aren't accidentally identical variables among different quantifiers.

#### 4.4.7. Combination of direct and reverse system

We have considered a limited case (direct system) and another limited case (reverse system). A natural idea arises: to combine these two bounded cases in the hope of obtaining an unbounded one.

Combining direct and inverse rule-based inference systems gives the following: There are facts represented in the form AND/OR, there are goals represented in the form AND/OR, and there are two types of rules: Direct rules in the Form L  W , backward rules in the form W  L . You will build solution graphs to each other until these graphs collide.

In other words, we introduce three types of resolutions:

1.               resolution of facts and direct rules, which is a special case of Robinson's method of resolution, which we discussed earlier;

2.               Solving goals and inverse rules, which is a special case of the dual solving method;

3.               Resolution of facts and goals.

The latter is called the extinction rule.

The deletion rule is: Two nodes delete each other when they either merge or the k-connections emanating from them are deleted.

The termination condition in this case is as follows: the root of the facts deletes the root of the goals, and the substitutions on the matching arcs are consistent.

Let's look at a positive example to understand the advantages of the combined forward and reverse system (this example was already discussed in section 0):

Fact:               There are smart students

Inverse rule: programmers know the solution method

Direct rule: Students do not know the solution method

Purpose:               There are smart non-programmers

We decide for ourselves which rule is direct and which rule is reversed. This places additional responsibilities on the expert who enters this information into the knowledge base, but on the other hand allows what the resolution method does not allow: to preserve implicativity, to show in which direction the reasoning should be applied.

This makes the solution quite easy to find (Fig.

Mistake! The text of the specified style does not exist in the document. .53 ). In this figure, quenching is indicated by thicker arrows.

![](Images/image00374.jpeg)

  

  .53. Combination of forward and reverse trigger systems. 

An application of the rule to building facts, an application of the reverse rule to building goals - and delete immediately. In other words, unlike the solve method, this system works in three steps and performs only three unions. At the same time, she did not have to think about which rules to apply, no strategy was required. All applicable rules have been applied and the result is a decision.

Unfortunately, there is a complication with this rather spectacular example. The settlement rule is consistent and complete, and the rule applying direct rules as a special case of the settlement rule is consistent and complete, and the rule applying reverse rules as a special case of the dual settlement procedure is consistent and complete. However, the situation with the extinction rule is not so simple and good. It's not universal; it is rich but not complete. There are such conclusions that cannot be reached using the suppression rule (Fig. Error! The text of the specified style is missing from the document. .54 ).

![](Images/image00375.jpeg)

but

A &( B  C )& D

![](Images/image00376.jpeg)( A & B )  ( C & D )

 

Rice. Mistake!               The text of the specified style in the document

absence. .54. Incomplete suppression rule 

The formula below is a logical consequence of the formula above

(A & B)  (C & D)  A & (B  C) & D

Also, trees grow very well towards each other, I really want to erase them - the letters are the same in both cases. But this is not possible, since the inductive definition is: either unified, or their k bundles are canceled. And in this case, k bonds just don't get annihilated. These are different structures in terms of the number of arcs: there are three decision graphs at the top and two at the bottom.

In this case, the combined deduction system didn't work, and the reason is that the AND/OR representation itself is not universal. Nevertheless, we lose something if we translate the general formula of the predicate calculus into the forms y AND / OR. Such a remarkable fact that takes place in the method of resolutions that after the reduction to propositions, the union of the initial premises and the negation of the proposition is not feasible precisely when the goal proposition unfortunately follows from the premises not here.

It remains open whether the AND/OR form can be adapted in such a way that the resolution of facts and objectives is just as consistent and complete as the resolution of facts and rules and the resolution of rules and objectives.

#### 4.4.8. Metaknowledge in deduction systems

Rule-based inference systems are good at representing facts, rules, and goals, and leave almost complete freedom in deciding what to consider facts, what rules, and what goals.

However, there is very important control knowledge (meta-knowledge) for PSII that is difficult to integrate into rule-based derivation systems. We give three typical examples of meta-knowledge. Some of them were implicitly applied in the previous examples.

1\. Consideration of the possible branching width.

Suppose there is a set of classification rules in the deduction system. For example dog(x)  animal(x) cat(x)  animal(x)

and so on, there can be many such rules. Formally, such rules can be applied in both forward and backward directions. Which direction is more suitable? It depends on the subject, on the type of tasks that the system solves. An expert building a deduction system has knowledge of the appropriate direction of application of the rules. For example, the examiner knows that the classification rules should not be applied as inverse rules. The fact is that applying such rules in the opposite direction gives a very large branch width as the target graph grows.

Such rules should be applied directly.

If the expert thinks that the classification rules in this deduction system still need to be applied in reverse, he should rewrite them in a contra-positive form:

 Animal (x)   Dog (x)

 Animal (x)   Cat (x) and so on.

2\. The order of application of the rules.

Suppose the deduction system has direct rules of form

P  ( Q 1  …  qk ) \_

or reverse rules of the form

( Q 1 & … & Q k )  P 

Applying such rules enlarges the graph with k arcs. Of great importance is the order in which the nodes Q 1 & ... & Q k are considered further . For example, in a rule-based inverse deduction system for solving inequalities (see Section 0, Fig. Error! Text of specified style is missing from document. .52 ), after applying rule 4, the expression B > 0 should be considered first, and not the expression A + C > D. The fact is that this expression is already in the form of a fact. The expert understands that when we need a certain fact in order to prove it, two cases are possible: either this fact is given in the terms of the problem or not. You can't take a fact out of thin air. When a fact is given (as in Example 0), other expressions should be considered in the hope of reducing them to given facts. If there isn't a fact that isn't confirmed, then you have to stop considering other expressions, because considering them yields nothing - that k \-connection still doesn't get included in the decision graph.

This type of information is meta-knowledge that is introduced into deductive systems with the help of special techniques. For example with the help of evaluation functions, as in production systems.

3\. Conditional application of rules.

Consider again the example with the solution of inequalities (cf.

Paragraph 0, Fig. Error! The text of the specified style does not exist in the document. .52 ). For reasons of transitivity I want to say that the fact C > O is superfluous. One is tempted to insert the eighth rule: x \> y & y \> z  x \> z . A very dangerous rule! The fact is that his right side is always applicable and is united with everything in this system. Here two simple variables are connected by the only predicate present in the system. Whatever node is in the AND/OR column, it can always be unified with the right-hand side of the transitivity rule. And this means that such a rule will be used all the time. It can be said that the transitivity rule is too applicable! Such rules should not be used directly. They can be hidden in the union (as they usually are), or (a very nice solution) we can add meta-knowledge to our algorithm by saying that there are rules that can be applied whenever applicable, and that there are rules that apply only under special circumstances. These are some conditions about the structure of the current knowledge base governing the application or non-application of rules. Meta-knowledge for transitivity is this: The rule of transitivity can be applied if and only if one of the conjunctions on the left is a fact. If this is not the case, goals are multiplied by applying the transitivity rule. When this is the case (when one of the conjunctions on the left-hand side of the transitivity rule is comparable to a fact), then the result is simply movement through the facts. In this case the decision tree remains linear. The tree does not branch, but simply winds along the transitivity chain, which is necessary for the application of the transitivity rule. If used just like that, it generates y which is not known what to do with. One can only agree to produce that y if one manages to get rid of x in return.

The conclusion from the above examples of meta-knowledge is as follows: meta-knowledge is not knowledge about the subject for which the inference system is built, it is knowledge about knowledge, how to apply and use knowledge about the subject, what properties the knowledge has about that subject has, etc. .d.

The two-stage rule-based deduction system delivers very good results. Such a top-level system contains meta-knowledge that is also represented, for example, in the form of rules. Facts in a higher-level system are descriptions of the current state of the lower-level system. The aim is to build (synthesize) a control strategy for a subordinate system. At the second level is the usual reasoning system, whose rules, facts, and goals are adopted from the subject. The higher-level system determines for the lower-level system in which direction the rules are to be applied, in what order the nodes are to be considered, under what conditions the rules can be applied, and so on.

### CONCLUSIONS ON CHAPTER 4

1.               The first-order predicate calculus with extralogical functions and predicates suffices to represent knowledge in all reasonable cases

2.               Evidence-seeking procedures are semipermissive procedures whose effectiveness depends on the strategy used.

3.               AND/OR graphs and similar structures can be used to search for inference in the same way as in production systems.

## CONCLUSION

In half a century of the development of artificial intelligence, a whole range of different approaches to the representation and processing of knowledge have been proposed and tested in practice. Among them, three groups, three clusters, naturally stand out, differing in the basis used - the formal apparatus used explicitly or implicitly in the implementation of specific applications [\[71\]](#part0005.xhtml#_ftn71). These three groups are:

\-                     production systems based on graph theory;

\-                     logical calculus based on mathematical

logic

\-                     others (e.g. neural and evolutionary systems).

It is these three groups of methods that underlie the structure of the book. It should be noted that all new approaches to representing knowledge that have been proposed recently clearly tend towards one of these groups. There is no insurmountable border between production systems and inference: In the last chapter we give some examples for the reduction of methods of one group to methods of another group. On the other hand, other methods of representing knowledge, such as frames, semantic networks, neural networks, and the like, are eclectic in nature and ultimately rely on the basic mathematical apparatus discussed in the manual.

Therefore, familiarity with the ideas of knowledge representation and processing within the identified approaches is quite sufficient to keep up with the main trends in artificial intelligence.

* * *

[\[1\]](#part0002.xhtml#_ftnref1) 

[\[2\]](#part0002.xhtml#_ftnref2) 

[\[3\]](#part0003.xhtml#_ftnref3) 

[\[4\]](#part0003.xhtml#_ftnref4) 

[\[5\]](#part0003.xhtml#_ftnref5) 

[\[6\]](#part0003.xhtml#_ftnref6) 

[\[7\]](#part0003.xhtml#_ftnref7) 

[\[8\]](#part0003.xhtml#_ftnref8) 

[\[9\]](#part0003.xhtml#_ftnref9) 

[\[10\]](#part0003.xhtml#_ftnref10) 

[\[11\]](#part0003.xhtml#_ftnref11) 

[\[12\]](#part0003.xhtml#_ftnref12) 

[\[13\]](#part0003.xhtml#_ftnref13) 

[\[14\]](#part0003.xhtml#_ftnref14) 

[\[15\]](#part0003.xhtml#_ftnref15)Note that since the number of distinct numbers that can be represented in a computer is finite, so is the number of distinct operators

Write with different arguments is of course too, albeit quite large.

[\[16\]](#part0003.xhtml#_ftnref16) 

[\[17\]](#part0003.xhtml#_ftnref17) 

[\[18\]](#part0003.xhtml#_ftnref18).

[\[19\]](#part0003.xhtml#_ftnref19) 

[\[20\]](#part0003.xhtml#_ftnref20) 

[\[21\]](#part0003.xhtml#_ftnref21) 

[\[22\]](#part0003.xhtml#_ftnref22) 

[\[23\]](#part0003.xhtml#_ftnref23) 

[\[24\]](#part0003.xhtml#_ftnref24) 

[\[25\]](#part0004.xhtml#_ftnref25) 

[\[26\]](#part0004.xhtml#_ftnref26) 

[\[27\]](#part0004.xhtml#_ftnref27) 

[\[28\]](#part0004.xhtml#_ftnref28) 

[\[29\]](#part0004.xhtml#_ftnref29) 

[\[30\]](#part0004.xhtml#_ftnref30) 

[\[31\]](#part0004.xhtml#_ftnref31) 

[\[32\]](#part0004.xhtml#_ftnref32) 

[\[33\]](#part0004.xhtml#_ftnref33) 

[\[34\]](#part0004.xhtml#_ftnref34) 

[\[35\]](#part0004.xhtml#_ftnref35) 

[\[36\]](#part0004.xhtml#_ftnref36) 

[\[37\]](#part0004.xhtml#_ftnref37) 

[\[38\]](#part0004.xhtml#_ftnref38) 

[\[39\]](#part0004.xhtml#_ftnref39) 

[\[40\]](#part0004.xhtml#_ftnref40) 

[\[41\]](#part0004.xhtml#_ftnref41) 

[\[42\]](#part0004.xhtml#_ftnref42) 

[\[43\]](#part0004.xhtml#_ftnref43).

[\[44\]](#part0005.xhtml#_ftnref44) 

[\[45\]](#part0005.xhtml#_ftnref45) 

[\[46\]](#part0005.xhtml#_ftnref46) 

[\[47\]](#part0005.xhtml#_ftnref47) 

[\[48\]](#part0005.xhtml#_ftnref48) 

[\[49\]](#part0005.xhtml#_ftnref49) 

[\[50\]](#part0005.xhtml#_ftnref50) 

[\[51\]](#part0005.xhtml#_ftnref51) 

[\[52\]](#part0005.xhtml#_ftnref52) 

[\[53\]](#part0005.xhtml#_ftnref53) 

[\[54\]](#part0005.xhtml#_ftnref54) 

[\[55\]](#part0005.xhtml#_ftnref55) 

[\[56\]](#part0005.xhtml#_ftnref56) 

[\[57\]](#part0005.xhtml#_ftnref57) 

[\[58\]](#part0005.xhtml#_ftnref58)For the reader who has not lost interest in our example, we strongly recommend that you stop reading at this point and solve the problem yourself. We even propose an answer: Max loses if and only if n Mod 4 = 1.

[\[59\]](#part0005.xhtml#_ftnref59)By the way, only grandmasters and champions don't lose anymore. The average chess fan will have a 100% chance of losing against the best modern chess program. Even Kasparov is already losing, it's only going to get worse! It can be argued that the competition of a person (anyone!) with a software and hardware complex in chess will soon become hopeless!

[\[60\]](#part0005.xhtml#_ftnref60).

[\[61\]](#part0005.xhtml#_ftnref61) 

[\[62\]](#part0005.xhtml#_ftnref62).

[\[63\]](#part0005.xhtml#_ftnref63)l

[\[64\]](#part0005.xhtml#_ftnref64).

[\[65\]](#part0005.xhtml#_ftnref65)The Latin phrase modus ponendo ponens, usually abbreviated to modus ponens, is now translated into Russian as

"Separation Rule". According to medieval tradition, logical terms are used in the original language without translation.

[\[66\]](#part0005.xhtml#_ftnref66) 

[\[67\]](#part0005.xhtml#_ftnref67) 

[\[68\]](#part0005.xhtml#_ftnref68).

[\[69\]](#part0005.xhtml#_ftnref69) 

[\[70\]](#part0005.xhtml#_ftnref70).

[\[71\]](#part0005.xhtml#_ftnref71)