
`Married(Father(Richard), Mother(John))` states that Richard the Lionheart’s father is married to King John’s mother (again, under a suitable interpretation).[5](#Chapter08-06.xhtml#sup08-5)

An atomic sentence is true in a given model if the relation referred to by the predicate symbol holds among the objects referred to by the arguments.

## 8.2.5 Complex sentences

We can use logical connectives to construct more complex sentences, with the same syntax and semantics as in propositional calculus. Here are four sentences that are true in the model of [Figure 8.2](#Chapter08-02.xhtml#fig8-2) under our intended interpretation:

$\\begin{array}{l} {\\neg Brother(LeftLeg(Richard),John)} \\\\ {Brother(Richard,John)\\operatorname{\\,\\land}Brother(John,Richard)} \\\\ {King(Richard) \\vee King(John)} \\\\ \\left. \\neg King(Richard)\\ \\Rightarrow\\ King(John)\\ . \\right. \\\\ \\end{array}$

## 8.2.6 Quantifiers

Once we have a logic that allows objects, it is only natural to want to express properties of entire collections of objects, instead of enumerating the objects by name. Quantifiers let us do this. First-order logic contains two standard quantifiers, called universal and existential.

Quantifier

### Universal quantification (∀)

Recall the difficulty we had in [Chapter 7](#Chapter07-00.xhtml) with the expression of general rules in propositional logic. Rules such as “Squares neighboring the wumpus are smelly” and “All kings are persons” are the bread and butter of first-order logic. We deal with the first of these in [Section 8.3](#Chapter08-03.xhtml#sec8-3). The second rule, “All kings are persons,” is written in first-order logic as

`∀x King(x) ⇒ Person(x)`.

The universal quantifier ∀ is usually pronounced “For all ...”. (Remember that the upside- down A stands for “all.”) Thus, the sentence says, “For all `x`, if `x` is a king, then `x` is a person.” The symbol `x` is called a variable. By convention, variables are lowercase letters. A variable is a term all by itself, and as such can also serve as the argument of a function—for example, `LeftLeg(x)`. A term with no variables is called a ground term.

Universal quantifier
Variable
Ground term

Intuitively, the sentence `∀x P`, where P is any logical sentence, says that P is true for every object `x`. More precisely, `∀x P` is true in a given model if P is true in all possible extended interpretations constructed from the interpretation given in the model, where each extended interpretation specifies a domain element to which `x` refers.

Extended interpretation

This sounds complicated, but it is really just a careful way of stating the intuitive meaning of universal quantification. Consider the model shown in [Figure 8.2](#Chapter08-02.xhtml#fig8-2) and the intended interpretation that goes with it. We can extend the interpretation in five ways:

$\\begin{array}{l} \\left. x\\rightarrow\\text{Richard~the~Lionheart}\\text{.} \\right. \\\\ \\left. x\\rightarrow\\,\\text{King~John,} \\right. \\\\ \\left. x\\rightarrow\\,\\text{Richard}'\\text{s}\\,\\text{left~leg,} \\right. \\\\ \\left. x\\rightarrow\\,\\text{John}'\\text{s}\\,\\text{left~leg,} \\right. \\\\ \\left. x\\rightarrow\\,\\text{the~crown}\\text{.} \\right. \\\\ \\end{array}$

The universally quantified sentence `∀x King(x) ⇒ Person(x)` is true in the original model if the sentence `King(x) ⇒ Person(x)` is true under each of the five extended interpretations. That is, the universally quantified sentence is equivalent to asserting the following five sentences:

$\\begin{array}{l} \\left. \\text{Richard~the~Lionheart~is~a~king}\\,\\,\\Rightarrow\\,\\,\\text{Richard~the~Lionheart~is~a~person}\\text{.} \\right. \\\\ \\left. \\text{King~John~is~a~king}\\,\\,\\Rightarrow\\,\\,\\text{King~John~is~a~person}\\text{.} \\right. \\\\ \\left. \\text{Richard's}\\,\\text{left~leg~is~a~king}\\,\\,\\Rightarrow\\,\\,\\text{Richard}'\\text{s}\\,\\text{left~leg~is~a~person}\\text{.} \\right. \\\\ \\left. \\text{John}'\\text{s}\\,\\text{left~leg~is~a~king}\\,\\,\\Rightarrow\\,\\,\\,\\text{John}'\\text{s}\\,\\text{leftleg~is~a~person}\\text{.} \\right. \\\\ \\left. \\text{The~crown~is~a~king}\\,\\,\\Rightarrow\\,\\,\\text{the~crown~is~a~person}\\text{.} \\right. \\\\ \\end{array}$

Let us look carefully at this set of assertions. Since, in our model, King John is the only king, the second sentence asserts that he is a person, as we would hope. But what about the other four sentences, which appear to make claims about legs and crowns? Is that part of the meaning of “All kings are persons”? In fact, the other four assertions are true in the model, but make no claim whatsoever about the personhood qualifications of legs, crowns, or indeed Richard. This is because none of these objects is a king. Looking at the truth table for `⇒` ([Figure 7.8](#Chapter07-04.xhtml#fig7-8) on [page 237](#Chapter07-04.xhtml#page_237)), we see that the implication is true whenever its premise is false—regardless of the truth of the conclusion. Thus, by asserting the universally quantified sentence, which is equivalent to asserting a whole list of individual implications, we end up asserting the conclusion of the rule just for those objects for which the premise is true and saying nothing at all about those objects for which the premise is false. Thus, the truth-table definition of `⇒` turns out to be perfect for writing general rules with universal quantifiers.

A common mistake, made frequently even by diligent readers who have read this paragraph several times, is to use conjunction instead of implication. The sentence

`∀x King(x) ∧ Person(x)`

would be equivalent to asserting

Richard the Lionheart is a king ∧ Richard the Lionheart is a person,

King John is a king ∧ King John is a person,

Richard’s left leg is a king ∧ Richard’s left leg is a person,

and so on. Obviously, this does not capture what we want.

### Existential quantification (∃)

Universal quantification makes statements about every object. Similarly, we can make a statement about some object without naming it, by using an existential quantifier. To say, for example, that King John has a crown on his head, we write

Existential quantifier

`∃x Crown(x) ∧ OnHead(x, John)`.

`∃x` is pronounced “There exists an `x` such that...” or “For some `x`...”.

Intuitively, the sentence `∃x P` says that P is true for at least one object `x`. More precisely, `∃x P` is true in a given model if P is true in at least one extended interpretation that assigns `x` to a domain element. That is, at least one of the following is true:

Richard the Lionheart is a crown ∧ Richard the Lionheart is on John’s head;

King John is a crown ∧ King John is on John’s head;

Richard’s left leg is a crown ∧ Richard’s left leg is on John’s head;

John’s left leg is a crown ∧ John’s left leg is on John’s head;

The crown is a crown ∧ the crown is on John’s head.

The fifth assertion is true in the model, so the original existentially quantified sentence is true in the model. Notice that, by our definition, the sentence would also be true in a model in which King John was wearing two crowns. This is entirely consistent with the original sentence “King John has a crown on his head.” [6](#Chapter08-06.xhtml#sup08-6)

Just as `⇒` appears to be the natural connective to use with ∀, `∧` is the natural connective to use with ∃. Using `∧` as the main connective with ∀ led to an overly strong statement in the example in the previous section; using `⇒` with ∃ usually leads to a very weak statement, indeed. Consider the following sentence:

`∃x Crown(x) ⇒ OnHead(x, John)`.
