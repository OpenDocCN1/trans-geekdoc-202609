
In a logical reasoning system that uses conjunctive normal form (`CNF`), we can see that the linguistic forms `¬(A ∨ B)` and `¬A ∧ ¬B` are the same because we can look inside the system and see that the two sentences are stored as the same canonical `CNF` form. It is starting to become possible to do something similar with the human brain. Mitchell et al . (2008) put subjects in a functional magnetic resonance imaging (`fMRI`) machine, showed them words such as “celery,” and imaged their brains. A machine learning program trained on (`word`, `image`) pairs was able to predict correctly 77% of the time on binary choice tasks (e.g., “celery” or “airplane”). The system can even predict at above-chance levels for words it has never seen an `fMRI` image of before (by considering the images of related words) and for people it has never seen before (proving that `fMRI` reveals some level of common representation across people). This type of work is still in its infancy, but `fMRI` (and other imaging technology such as intracranial electrophysiology (Sahin et al., 2009)) promises to give us much more concrete ideas of what human knowledge representations are like.

From the viewpoint of formal logic, representing the same knowledge in two different ways makes absolutely no difference; the same facts will be derivable from either representation. In practice, however, one representation might require fewer steps to derive a conclusion, meaning that a reasoner with limited resources could get to the conclusion using one representation but not the other. For nondeductive tasks such as learning from experience, outcomes are necessarily dependent on the form of the representations used. We show in [Chapter 19](#Chapter19-00.xhtml) that when a learning program considers two possible theories of the world, both of which are consistent with all the data, the most common way of breaking the tie is to choose the most succinct theory—and that depends on the language used to represent theories. Thus, the influence of language on thought is unavoidable for any agent that does learning.

## 8.1.2 Combining the best of formal and natural languages

We can adopt the foundation of propositional logic—a declarative, compositional semantics that is context-independent and unambiguous—and build a more expressive logic on that foundation, borrowing representational ideas from natural language while avoiding its drawbacks. When we look at the syntax of natural language, the most obvious elements are nouns and noun phrases that refer to objects (squares, pits, wumpuses) and verbs and verb phrases along with adjectives and adverbs that refer to relations among objects (is breezy, is adjacent to, shoots). Some of these relations are functions—relations in which there is only one “value” for a given “input.” It is easy to start listing examples of objects, relations, and functions:

Object
Relation
Function

•Objects: people, houses, numbers, theories, Ronald McDonald, colors, baseball games, wars, centuries ...

•Relations: these can be unary relations or properties such as red, round, bogus, prime, multistoried ..., or more general n -ary relations such as brother of, bigger than, inside, part of, has color, occurred after, owns, comes between, . . .

Property

•Functions: father of, best friend, third inning of, one more than, beginning of . . .

Indeed, almost any assertion can be thought of as referring to objects and properties or relations. Some examples follow:

•“One plus two equals three.”

Objects: one, two, three, one plus two; Relation: equals; Function: plus. (“One plus two” is a name for the object that is obtained by applying the function “plus” to the objects “one” and “two.” “Three” is another name for this object.)

•“Squares neighboring the wumpus are smelly.”

Objects: wumpus, squares; Property: smelly; Relation: neighboring.

•“Evil King John ruled England in 1200.”

Objects: John, England, 1200; Relation: ruled during; Properties: evil, king.

The language of first-order logic, whose syntax and semantics we define in the next section, is built around objects and relations. It has been important to mathematics, philosophy, and artificial intelligence precisely because those fields—and indeed, much of everyday human existence—can be usefully thought of as dealing with objects and the relations among them. First-order logic can also express facts about some or all of the objects in the universe. This enables one to represent general laws or rules, such as the statement “Squares neighboring the wumpus are smelly.”

The primary difference between propositional and first-order logic lies in the ontological commitment made by each language—that is, what it assumes about the nature of reality.Mathematically, this commitment is expressed through the nature of the formal models with respect to which the truth of sentences is defined. For example, propositional logic assumes that there are facts that either hold or do not hold in the world. Each fact can be in one of two states—true or false—and each model assigns true or false to each proposition symbol (see [Section 7.4.2](#Chapter07-04.xhtml#sec7-4-2)). First-order logic assumes more; namely, that the world consists of objects with certain relations among them that do or do not hold. (See [Figure 8.1](#Chapter08-01.xhtml#fig8-1).) The formal models are correspondingly more complicated than those for propositional logic.

Ontological commitment

×![](images/Fig-123.jpg)

Figure 8.1Formal languages and their ontological and epistemological commitments.

This ontological commitment is a great strength of logic (both propositional and firstorder), because it allows us to start with true statements and infer other true statements. It is especially powerful in domains where every proposition has clear boundaries, such as mathematics or the wumpus world, where a square either does or doesn’t have a pit; there is no possibility of a square with a vaguely pit-like indentation. But in the real world, many propositions have vague boundaries: Is Vienna a large city? Does this restaurant serve delicious food? Is that person tall? It depends who you ask, and their answer might be “kind of.”

One response is to refine the representation: if a crude line dividing cities into “large” and “not large” leaves out too much information for the application in question, then one can increase the number of size categories or use a `Population` function symbol. Another proposed solution comes from `Fuzzy logic`, which makes the ontological commitment that propositions have a degree of truth between 0 and 1. For example, the sentence “Vienna is a large city” might be true to degree 0.8 in fuzzy logic, while “Paris is a large city” might be true to degree 0.9. This corresponds better to our intuitive conception of the world, but it makes it harder to do inference: instead of one rule to determine the truth of `A ∧ B`, fuzzy logic needs different rules depending on the domain. Another possibility, covered in [Section 25.1](#Chapter25-01.xhtml#sec25-1), is to assign each concept to a point in a multidimensional space, and then measure the distance between the concept “large city” and the concept “Vienna” or “Paris.”

Fuzzy logic
Degree of truth
