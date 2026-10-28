![](bbox=[0.12, 0.08, 0.88, 0.34])

Figure 2. Representation in FLINT of the regulations for lending and returning books. Blue rectangles are instances of AtomicFact, green rounded rectangles are instances of Act, yellow hexagons are instances of Duty. Actions are omitted for readability.

# 5. Example: library regulations

To illustrate how we intend the FLINT ontology to be used, we describe a toy example of a simple set of library regulations:

+   1. Books can be loaned to library members if they have no outstanding fines.
+   2. Library members who borrow books are obligated to return them.
+   3. Failure to return a book results in a fine.

In our interpretation of these rules, we distinguish three acts: lending a book, returning a book, and giving a fine. The latter act is not found explicitly in the rules, but its existence follows from the assumption that changes to normative states never happen without an act taking place. Therefore, a fine is not viewed as something automatically happening when a book has not been returned, but as the result of an act that has its own pre- and postconditions.⁴

A schematic view of the first two acts and their related facts is shown in Figure 2. This schema shows that a valid performance of the act Lend a book creates a duty Return book, which can be terminated by a valid performance of the act Return a book. That the two operations are related to the same Book node as an object, determines that the duty is removed only by returning the same book that was borrowed. Figure 3 shows the act of giving a fine, which has a complex precondition, and terminates the duty to return the book while creating a new duty to pay the fine. Of course, this duty should have a corresponding terminating act in the full picture.

This example illustrates how the FLINT ontology can be used to transform a set of rules into acts and facts, providing insight into what is possible and expected behavior for a particular agent in a given situation. Of course, resolving disputes over what constitutes lawful conduct often requires a much larger graph, in which all parts of laws relevant to the dispute are interpreted as acts and facts.

⁴Note that the rules are not explicit about how much time may elapse before the fine can be given. This could be specified as an additional precondition for the Give a fine act.