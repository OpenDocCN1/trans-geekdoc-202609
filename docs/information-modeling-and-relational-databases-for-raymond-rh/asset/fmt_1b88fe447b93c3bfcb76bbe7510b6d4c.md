
# Sequences and Sets

## Sequences

Usually, when order is made significant, so is repetition. In this case, we have a **sequence** (also called a list, permutation, or tuple). Thus, a sequence is an ordered bag. Sequences are often delimited by parentheses or angle brackets, for example, `(1,2)` or `〈1, 2〉`. The sequence `(6, 3, 6)` has three members and differs from the sequence `(3, 6, 6)`. The cardinality of a sequence is its member count, including duplicates. For example, `#(3, 6, 6) = 3`. In practice, several different delimiting notations are used. For example, `[`, `]` are used as set delimiters in Pascal and list delimiters in Prolog.

## Set Enumeration and Ranges

If a set is enumerated in full, the ordering does not matter. However, a natural ordering often provides an obvious pattern; in such cases, a partial enumeration can define the set. For example, the set of decimal digits may be shown as `{0..9}`, where the `..` indicates the missing digits. Here, `0..9` is often called a **range**. Infinite sets may be represented with `..` at one or both ends. For example, the set of natural numbers may be shown as `{1, 2, 3..}`.

## Extensional and Intensional Definitions

The preceding set definitions enumerate, wholly or partially, the extension of the set and are thus examples of an **extensional definition**. A set may also be defined by an **intensional definition**. Here, the *intension* or meaning is declared using a property that applies to just the members of the set. That is, a description is given that constitutes both a necessary and a sufficient condition (an "iff condition") for an item to belong to the set.

For example, the set *A*, defined extensionally as `{1,2,3}`, may be defined intensionally as *A* = the set of natural numbers less than 4. This definition may be recast in set builder notation as `{x: x is a natural number less then 4}` or more briefly as `{x: x ∈ ℕ & x < 4}`, where `∈` abbreviates "is a member of" and `ℕ` is the set of natural numbers. In set builder notation, a stroke `∣` may be used instead of a colon, for example, `{x∣ x < 4}`.

## Proposition-Forming Operators

Some set operations result in propositions while others result in sets. Note the following **proposition-forming operators**: `=`, `≠`, `⊆`, `⊂`, `⊇`, and `⊃`. These are read respectively as "equals", "is not equal to", "is a subset of", "is a proper subset of", "is a superset of", and "is a proper superset of".

## Subsets and Supersets

Given any sets *A* and *B*, we say that *A* is a **subset** of *B* iff every member of *A* is also a member of *B*. For example, `{1,3} ⊆ {1, 2, 3}`. An equivalent definition is *A* is a subset of *B* iff *A* has no members that are not in *B*. This second definition makes it easy to see that the **null set** is a subset of every set. The null or empty set has no members and may be represented as `{}` or `∅`.

Every set is a subset of itself. For example, `{1, 3} ⊆ {1, 3}`. We say that *A* is a *proper subset* of *B* if and only if *A* is a subset of *B* but not equal to *B*. For instance, `{1, 3} ⊂ {1, 2, 3}`. We say that *A* is a **superset** of *B* iff *B* is a subset of *A*, and that *A* is a *proper superset* of *B* iff *B* is a proper subset of *A*. For example, `{1, 2, 3}` is both a superset and a proper superset of `{1, 3}`.

## Euler Diagrams

Comparison relationships between two sets are often depicted by **Euler diagrams**. As developed by the Swiss mathematician Leonhard Euler (1707–1783 CE), these were *spatial* and *existential*. Each set is pictured as a set of points inside an ellipse. This enables the relationship between the sets to be "seen" by the spatial arrangement of the ellipses. For example, placing ellipse *A* inside *B* shows that *A* is a proper subset of *B* (see [Fig. 6.1](#Ch006_211-271_B9780443237904000025.xhtml#f0010)). Here, we see that every element of *A* is also an element of *B* (so *A* is a subset of *B*). The existential viewpoint implies that each of the regions in the Euler diagram contains some elements. So, *B* has some elements not in *A*. Hence *A* is a proper subset of *B*.

![Fig. 6.1 Standard Euler diagram for A is proper subset of B.](images/B9780443237904000025/f06-01-9780443237904.jpg)

[Fig. 6.1](#Ch006_211-271_B9780443237904000025.xhtml#B-f0010) Standard Euler diagram for *A* is proper subset of *B.*

To show that *A* is a subset of *B* on standard Euler diagrams, we use a disjunction of two diagrams, as in [Fig. 6.2](#Ch006_211-271_B9780443237904000025.xhtml#f0015). The right-hand diagram caters for the case *A* = *B*.

![Fig. 6.2 A disjunction of standard Euler diagrams denotes A is a subset of B.](images/B9780443237904000025/f06-02-9780443237904.jpg)

[Fig. 6.2](#Ch006_211-271_B9780443237904000025.xhtml#B-f0015) A disjunction of standard Euler diagrams denotes A is a subset of B.

## Hypothetical Euler Diagrams (HEDs)

The notion of subsethood is more useful than proper subsethood. Partly to depict such relationships on a single diagram, we use **hypothetical Euler diagrams** (HEDs). In an HED, an asterisk is placed in a region to show something exists there while shading the region indicates that it is empty. If a region is unmarked, the question of whether any elements exist there is left open or hypothetical. [Fig. 6.3](#Ch006_211-271_B9780443237904000025.xhtml#f0020) shows the HEDs for the six most important comparisons between two sets.

![Fig. 6.3 Hypothetical Euler diagrams for set comparisons.](images/B9780443237904000025/f06-03-9780443237904.jpg)

[Fig. 6.3](#Ch006_211-271_B9780443237904000025.xhtml#B-f0020) Hypothetical Euler diagrams for set comparisons.

[Fig. 6.3](#Ch006_211-271_B9780443237904000025.xhtml#f0020)(a) shows *equality* or *identity* (e.g., *A* = *B* = {1,2}). In [Fig. 6.3](#Ch006_211-271_B9780443237904000025.xhtml#f0020)(b), *A* and *B* are *disjoint* or *mutually exclusive*; that is, they have no members in common (e.g., *A* = {1}, *B* = {2}). In [Fig. 6.3](#Ch006_211-271_B9780443237904000025.xhtml#f0020)(c), *A* is a *subset* of *B* (equivalently, *B* is a superset of *A*). In [Fig. 6.3](#Ch006_211-271_B9780443237904000025.xhtml#f0020)(d), *A* is a *proper subset* of *B* (so *B* is a proper superset of *A*). For example both *A* = {1}, *B* = {1, 2} and *A* = {1}, *B* = {1} are instances of subsethood, but only the former is an instance of proper subsethood. [Fig. 6.3](#Ch006_211-271_B9780443237904000025.xhtml#f0020)(e) shows *overlap*: the sets have some members in common. [Fig. 6.3](#Ch006_211-271_B9780443237904000025.xhtml#f0020)(f) shows *proper overlap*: the sets have common as well as extra members. For example, both *A* = {1, 2}, *B* = {2,3} and *A* = {1}, *B* = {1, 2} are instances of overlap, but only the former is a case of proper overlap.

## Set-Forming Operations

Let's now consider **set-forming operations**, where the result is a set. Given any sets *A* and *B*, we define *A* ∪ *B* (i.e., *A union B*) to be the set of all elements in *A* or *B*, reading "or" in the inclusive sense. *A* ∩ *B* (i.e., *A intersect B*) is the set of all elements common to both *A* and *B*. Each of these operations is commutative, so the order of the operands doesn't matter. That is, *A* ∪ *B* = *B* ∪ *A* and *A* ∩ *B* = *B* ∩ *A*.

The **set difference** (or relative complement) operation is defined thus: *A* − *B* (i.e., A minus B) is the set of all elements that are in *A* but not in *B*. This operation does not commute (i.e., cases may arise where *A* − *B* ≠ *B* − *A*). If we let U = the **universal set** (i.e., the set of all elements under consideration), we define the **complement** of *A* as *A′* = U − *A*. The **symmetric difference** between *A* and *B* is the set of elements in just one of *A* or *B* (i.e., the union minus the intersection).

The three most important set-forming operations are union, intersection, and difference. These are depicted in [Fig. 6.4](#Ch006_211-271_B9780443237904000025.xhtml#f0025) by means of **Venn diagrams**, named after their inventor, the English logician John Venn (1834–1923 CE). Here, shading indicates the result of the operation.

![Fig. 6.4 Venn diagrams for three set-forming operations.](images/B9780443237904000025/f06-04-9780443237904.jpg)
