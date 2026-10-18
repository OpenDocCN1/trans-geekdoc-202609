
> In this chapter, I have sketched some ideas from recent work in psychology regarding the mental mechanisms by which humans understand and act appropriately in the situations they encounter. We have core knowledge—some of it innate and some of it learned during development and throughout life. Our concepts are encoded in the brain as mental models that we can “run” (that is, simulate) in order to predict what is likely to happen in any situation or what `could` happen given any alteration we might imagine. Our concepts, ranging from simple words to complex situations, are formed via abstraction and analogy.

> I certainly don’t claim to have covered all of the components of human understanding. Indeed, many people have noted that the terms `understanding` and `meaning` (not to mention `consciousness`) are merely ill-defined terms that we use as placeholders, because we don’t yet have the correct language or theory to talk about what’s actually going on in the brain. The AI pioneer Marvin Minsky put it this way: “Though prescientific idea germs like ‘believe,’ ‘know,’ and ‘mean’ are useful in daily life, they seem technically too coarse to support powerful theories.… Real as ‘self’ or ‘understand’ may seem to us today … they are only first steps towards better concepts.” Minsky went on, pointing out that our confusions about these notions “stem from a burden of traditional ideas inadequate to this tremendously difficult enterprise.… This is still a formative period for our ideas about mind.”^()

> Until recently, the question of what mental mechanisms allow people to understand the world—and whether machines could have such understanding as well—was almost exclusively the province of philosophers, psychologists, neuroscientists, and theoretically minded AI researchers who have engaged in academic debates on these issues for decades (and in some cases centuries), without much attention to real-world consequences. However, as I’ve described in previous chapters, AI systems that lack humanlike understanding are now being widely deployed for real-world applications. Suddenly what were once only academic questions have started to matter very much in the real world. To what extent do AI systems need humanlike understanding, or some approximation of it, in order to do their jobs reliably and robustly? No one knows the answer. But essentially everyone in AI research agrees that core “commonsense” knowledge and the capacity for sophisticated abstraction and analogy are among the missing links required for future progress in AI. In the next chapter, I describe some approaches to giving machines these capabilities.

# [15](contents.xhtml#c_ch15)

# [Knowledge, Abstraction, and Analogy in Artificial Intelligence](contents.xhtml#c_ch15)

Since the 1950s, many people in the AI community have explored ways to make crucial aspects of human thought—such as core intuitive knowledge, abstraction, and analogy making—part of `machine` intelligence, and thus to enable AI systems to actually understand the situations they encounter. In this chapter, I’ll describe a few efforts in these directions, including some of my own past and current work.

## Core Knowledge for Computers

In the early days of AI, before machine learning and neural networks dominated the landscape, AI researchers manually encoded the rules and knowledge that a program would need to perform its tasks. To many of the early AI pioneers, it seemed entirely reasonable that this “build it in” approach could capture enough of human commonsense knowledge to achieve human-level intelligence in machines.

The most famous and longest-lasting attempt to manually encode commonsense knowledge for machines is Douglas Lenat’s Cyc project. Lenat, a PhD student and later professor in Stanford University’s AI Lab, made a name for himself in the AI research community of the 1970s by creating programs that simulated how humans invent new concepts, particularly in mathematics.^()

The name Cyc (pronounced “syke”) is meant to evoke the word `encyclopedia`, but unlike the encyclopedias we’re all familiar with, Lenat’s goal was for Cyc to contain all the `unwritten` knowledge that humans have, or at least enough of it to make AI systems able to function at the level of humans in vision, language, planning, reasoning, and other domains.

Cyc is a symbolic AI system of the kind I described in chapter 1—a collection of statements (“assertions”) about specific entities or general concepts, written in a logic-based computer language. Here are some examples of Cyc’s assertions (translated from logical form into English):^()

• An entity cannot be in more than one place at the same time.

• Objects age one year per year.

• Each person has a mother who is a female person.

The Cyc project also includes sophisticated algorithms for performing logical inferences on assertions. For example, Cyc could determine that if I am in Portland, then I am not also in New York, because I am an entity, Portland and New York are places, and an entity cannot be in more than one place at a time. Cyc also has extensive methods for dealing with inconsistent or uncertain assertions in its collection.

Cyc’s assertions have been hand coded into the collection by humans (namely, the employees of Cycorp) or logically inferred by the system from existing assertions.^()

The philosophy underlying Cyc has much in common with that of the `expert systems` of AI’s earlier days. You might recall my discussion from chapter 2 of the MYCIN medical-diagnosis expert system. “Experts”—physicians—were interviewed by MYCIN’s developers to obtain rules that the system could use to make diagnoses. The developers then translated these rules into a logic-based computer language to allow the system to perform logical inference. In Cyc, the “experts” are people manually translating their knowledge about the world into logic statements. Cyc’s “knowledge base” is larger than MYCIN’s, and Cyc’s logical-reasoning algorithms are more sophisticated, but the projects share a core faith: intelligence can be captured via human-programmed rules operating on a sufficiently extensive collection of explicit knowledge. In today’s AI landscape dominated by deep learning, the Cyc project is one of the last remaining large-scale symbolic AI efforts.^()

Is it possible that with enough time and effort the engineers of Cycorp could actually be successful in capturing all, or even a sufficient portion, of human commonsense knowledge, whatever `sufficient` might mean? I’m doubtful. If commonsense knowledge is the knowledge that all humans have but is not written down anywhere, then much of that knowledge is `subconscious`; we don’t even know that we have it. This includes much of our core intuitive knowledge of physics, biology, and psychology, which underlies all our broader knowledge about the world. If you aren’t consciously aware of knowing something, you can’t be the “expert” who explicitly provides that knowledge to a computer.

In addition, as I argued in the previous chapter, our commonsense knowledge is governed by abstraction and analogy. What we call common sense cannot exist without these abilities. However, humanlike abstraction and analogy making are not skills that can be captured by Cyc’s massive set of facts or, I believe, by logical inference in general.
