
Under the resulting semantics, [Equation (8.3)](#Chapter08-02.xhtml#eq8-3) does indeed state that Richard has exactly two brothers, John and Geoffrey. We call this database semantics to distinguish it from the standard semantics of first-order logic. Database semantics is also used in logic programming systems, as explained in [Section 9.4.4](#Chapter09-04.xhtml#sec9-4-4).

*Database semantics*

It is instructive to consider the set of all possible models under database semantics for the same case as shown in [Figure 8.4](#Chapter08-02.xhtml#fig8-4) ([page 277](#Chapter08-02.xhtml#page_277)). [Figure 8.5](#Chapter08-02.xhtml#fig8-5) shows some of the models, ranging from the model with no tuples satisfying the relation to the model with all tuples satisfying the relation. With two objects, there are four possible two-element tuples, so there are 2^4 = 16 different subsets of tuples that can satisfy the relation. Thus, there are 16 possible models in all—a lot fewer than the infinitely many models for the standard first-order semantics. On the other hand, the database semantics requires definite knowledge of what the world contains.

Description
Each of the five circular sections represents a model. Each circular section contains two dots labeled R and J. The constant symbols outside the models are labeled R and J. In all the models, an arrow from the constant R points to the dot R and an arrow from constant J points to the dot J. In the second model, an arrow starts and ends with dot R. In the third model, an arrow starts from dot J and ends in dot J. An arrow starts from dot R and ends in dot J in the fourth model. In the fifth model, an arrow between dots R and J points in both directions. An arrow starts and ends on dot J and an arrow starts and ends on dot R in the fifth model. There is a continuation symbol between the fourth and the fifth models.

×![](images/Fig-127.jpg)

Figure 8.5 Some members of the set of all models for a language with two constant symbols, R and J, and one binary relation symbol, under database semantics. The interpretation of the constant symbols is fixed, and there is a distinct object for each constant symbol.

This example brings up an important point: there is no one “correct” semantics for logic. The usefulness of any proposed semantics depends on how concise and intuitive it makes the expression of the kinds of knowledge we want to write down, and on how easy and natural it is to develop the corresponding rules of inference. Database semantics is most useful when we are certain about the identity of all the objects described in the knowledge base and when we have all the facts at hand; in other cases, it is quite awkward. For the rest of this chapter, we assume the standard semantics while noting instances in which this choice leads to cumbersome expressions.

## 8.3 Using First-Order Logic

Now that we have defined an expressive logical language, let’s learn how to use it. In this section, we provide example sentences in some simple domains. In knowledge representation, a domain is just some part of the world about which we wish to express some knowledge.

*Domain*

We begin with a brief description of the `TELL`/`ASK` interface for first-order knowledge bases. Then we look at the domains of family relationships, numbers, sets, and lists, and at the wumpus world. [Section 8.4.2](#Chapter08-04.xhtml#sec8-4-2) contains a more substantial example (electronic circuits) and [Chapter 10](#Chapter10-00.xhtml) covers everything in the universe.

## 8.3.1 Assertions and queries in first-order logic

Sentences are added to a knowledge base using `TELL`, exactly as in propositional logic. Such sentences are called assertions. For example, we can assert that John is a king, Richard is a person, and all kings are persons:

*Assertion*

```
TELL(KB, King(John)).
TELL(KB, Person(Richard)).
TELL(KB, ∀x King(x) ⇒ Person(x)).
```

We can ask questions of the knowledge base using `ASK`. For example,

`ASK(KB, King(John))`

returns true. Questions asked with `ASK` are called queries or goals. Generally speaking, any query that is logically entailed by the knowledge base should be answered affirmatively. For example, given the three assertions above, the query

`ASK(KB, Person(John))`

should also return true. We can ask quantified queries, such as `ASK(KB, ∃x Person(x))`.

`ASK(KB, ∃x Person(x))`.

The answer is true, but this is perhaps not as helpful as we would like. It is rather like answering “Can you tell me the time?” with “Yes.” If we want to know what value of x makes the sentence true, we will need a different function, which we call `ASKVARS`,

`ASKVARS(KB, Person(x))`

*Substitution Binding list*

and which yields a stream of answers. In this case there will be two answers: `{x/John}` and `{x/Richard}`. Such an answer is called a substitution or binding list. `ASKVARS` is usually reserved for knowledge bases consisting solely of Horn clauses, because in such knowledge bases every way of making the query true will bind the variables to specific values. That is not the case with first-order logic; in a `KB` that has been told only that `King(John) ∨ King(Richard)` there is no single binding to x that makes the query `∃x King(x)` true, even though the query is in fact true.

## 8.3.2 The kinship domain

The first example we consider is the domain of family relationships, or kinship. This domain includes facts such as “Elizabeth is the mother of Charles” and “Charles is the father of William” and rules such as “One’s grandmother is the mother of one’s parent.”

Clearly, the objects in our domain are people. Unary predicates include `Male` and `Female`, among others. Kinship relations—parenthood, brotherhood, marriage, and so on—are represented by binary predicates: `Parent`, `Sibling`, `Brother`, `Sister`, `Child`, `Daughter`, `Son`, `Spouse`, `Wife`, `Husband`, `Grandparent`, `Grandchild`, `Cousin`, `Aunt`, and `Uncle`. We use functions for `Mother` and `Father`, because every person has exactly one of each of these, biologically (although we could introduce additional functions for adoptive mothers, surrogate mothers, etc.).

We can go through each function and predicate, writing down what we know in terms of the other symbols. For example, one’s mother is one’s parent who is female:

`∀m,c Mother(c)=m ⇔ Female(m) ∧ Parent(m,c)`.

One’s husband is one’s male spouse:

`∀w,h Husband(h,w) ⇔ Male(h) ∧ Spouse(h,w)`.

Parent and child are inverse relations:

`∀p,c Parent(p,c) ⇔ Child(c,p)`.

A grandparent is a parent of one’s parent:

`∀g,c Grandparent(g,c) ⇔ ∃p Parent(g,p) ∧ Parent(p,c)`.

A sibling is another child of one’s parent:

`∀x,y Sibling(x,y) ⇔ x≠y ∧ ∃p Parent(p,x) ∧ Parent(p,y)`.

We could go on for several more pages like this, and Exercise 8.KINS asks you to do just that.
