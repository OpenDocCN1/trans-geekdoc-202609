
## 2. The empty set has no elements added into it
The empty set has no elements added into it. In other words, there is no way to decompose `{}` into a smaller set and an element:
`¬∃x, s Add(x, s) = {}`

## 3. Adding an element already in the set has no effect
Adding an element already in the set has no effect:
`∀x, s x∈s ⇔ s = Add(x, s)`

## 4. The only members of a set are the elements that were added into it
The only members of a set are the elements that were added into it. We express this recursively, saying that x is a member of s if and only if s is equal to some element y added to some set s2,, where either y is the same as x or x is a member of s2:
`∀x, s x∈s ⇔ ∃y, s[2] (s = Add(y, s[2]) ∧ (x = y ∨ x∈s[2]))`

## 5. A set is a subset of another set
A set is a subset of another set if and only if all of the first set’s members are members of the second set:
`∀s[1], s[2] s[1] ⊆ s[2] ⇔ (∀x x∈s[1] ⇒ x∈s[2])`

## 6. Two sets are equal if and only if each is a subset of the other
Two sets are equal if and only if each is a subset of the other:
`∀s[1], s[2] (s[1] = s[2]) ⇔ (s[1]⊆s[2] ∧ s[2]⊆s[1])`

## 7. An object is in the intersection of two sets
An object is in the intersection of two sets if and only if it is a member of both sets:
`∀x, s[1], s[2] x∈(s[1] ∩ s[2]) ⇔ (x∈s[1] ∧ x∈s[2])`

## 8. An object is in the union of two sets
An object is in the union of two sets if and only if it is a member of either set:
`∀x, s[1], s[2] x∈(s[1] ∪ s[2]) ⇔ (x∈s[1] ∨ x∈s[2])`

## Lists
Lists are similar to sets. The differences are that lists are ordered and the same element can appear more than once in a list. We can use the vocabulary of Lisp for lists: `Nil` is the constant list with no elements; `Cons`, `Append`, `First`, and `Rest` are functions; and `Find` is the predicate that does for lists what `Member` does for sets. `List` is a predicate that is true only of lists. As with sets, it is common to use syntactic sugar in logical sentences involving lists. The empty list is `[]`. The term `Cons(x, Nil)` (i.e., the list containing the element x followed by nothing) is written as `[x]`. A list of several elements, such as `[A, B, C]`, corresponds to the nested term `Cons(A, Cons(B, Cons(C, Nil)))`. Exercise 8.LIST asks you to write out the axioms for lists.

> List

## 8.3.4 The wumpus world
Some propositional logic axioms for the wumpus world were given in Chapter 7. The firstorder axioms in this section are much more concise, capturing in a natural way exactly what we want to say.

Recall that the wumpus agent receives a percept vector with five elements. The corresponding first-order sentence stored in the knowledge base must include both the percept and the time at which it occurred; otherwise, the agent will get confused about when it saw what. We use integers for time steps. A typical percept sentence would be
`Percept([Stench, Breeze, Glitter, None, None], 5)`
Here, `Percept` is a binary predicate, and `Stench` and so on are constants placed in a list. The actions in the wumpus world can be represented by logical terms:
`Turn(Right)`, `Turn(Left)`, `Forward`, `Shoot`, `Grab`, `Climb`.
To determine which is best, the agent program executes the query
`ASK VARS(KB, BestAction(a, 5))`
which returns a binding list such as `{a/Grab}`. The agent program can then return `Grab` as the action to take. The raw percept data implies certain facts about the current state. For example:

```
∀t, s, g, w, c Percept([s, Breeze, g, w, c], t) ⇒ Breeze(t)
∀t, s, g, w, c Percept([s, None, g, w, c], t) ⇒ ¬Breeze(t)
∀t, s, b, w, c Percept([s, Glitter, w, c], t) ⇒ Glitter(t)
∀t, s, b, w, c Percept([s, None, w, c], t) ⇒ ¬Glitter(t)
```

and so on. These rules exhibit a trivial form of the reasoning process called perception, which we study in depth in Chapter 27. Notice the quantification over time t. In propositional logic, we would need copies of each sentence for each time step.

Simple “reflex” behavior can also be implemented by quantified implication sentences. For example, we have
`∀t Glitter(t) ⇒ BestAction(Grab, t)`
Given the percept and rules from the preceding paragraphs, this would yield the desired conclusion `BestAction(Grab, 5)`—that is, `Grab` is the right thing to do.

We have represented the agent’s inputs and outputs; now it is time to represent the environment itself. Let us begin with objects. Obvious candidates are squares, pits, and the wumpus. We could name each square—`Square1,2` and so on—but then the fact that `Square1,2` and `Square1,3` are adjacent would have to be an “extra” fact, and we would need one such fact for each pair of squares. It is better to use a complex term in which the row and column appear as integers; for example, we can simply use the list term `[1, 2]`. Adjacency of any two squares can be defined as

```
∀x, y, a, b Adjacent([x, y], [a, b]) ⇔
((x = a ∧ (y = b - 1 ∨ y = b + 1)) ∨ (y = b ∧ (x = a - 1 ∨ x = a + 1)))
```

We could name each pit, but this would be inappropriate for a different reason: there is no reason to distinguish among pits.[9] It is simpler to use a unary predicate `Pit` that is true of squares containing pits. Finally, since there is exactly one wumpus, a constant `Wumpus` is just as good as a unary predicate (and perhaps more dignified from the wumpus’s viewpoint).

The agent’s location changes over time, so we write `At(Agent, s, t)` to mean that the agent is at square s at time t. We can fix the wumpus to a specific location forever with `∀t At(Wumpus, [1,3], t)`. We can then say that objects can be at only one location at a time:
`∀x, s[1], s[2], t At(x, s[1], t) ∧ At(x, s[2], t) ⇒ s[1] = s[2]`

Given its current location, the agent can infer properties of the square from properties of its current percept. For example, if the agent is at a square and perceives a breeze, then that square is breezy:
`∀s, t At(Agent, s, t) ∧ Breeze(t) ⇒ Breezy(s)`

It is useful to know that a square is breezy because we know that the pits cannot move about. Notice that `Breezy` has no time argument.

Having discovered which places are breezy (or smelly) and, very importantly, not breezy (or not smelly), the agent can deduce where the pits are (and where the wumpus is). Whereas propositional logic necessitates a separate axiom for each square (see R2 and R3 on page 238) and would need a different set of axioms for each geographical layout of the world, first-order logic just needs one axiom:

```
∀s Breezy(s) ⇔ ∃r Adjacent(r, s) ∧ Pit(r)   (8.4)
```
