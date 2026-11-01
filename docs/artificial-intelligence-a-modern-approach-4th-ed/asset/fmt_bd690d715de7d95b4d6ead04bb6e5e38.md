
The inheritance network from bottom to top is as follows. Two arrows labeled `Member of` points from `Mary` and `John` to `Female persons` and `Male persons` category, respectively. An arrow labeled `Legs` points from `John` to `1` while another arrow labeled `Sister of` points from `Mary` to `John`. Two arrows labeled `Subset Of` from each category, `Male persons` and `female persons`, points to the category labeled `Persons`. An arrow labeled `Has Mother` from `Persons` points back to `Female Persons`. Another arrow labeled `Legs` points from `Persons` to `2`. An arrow labeled `Subset Of` points from the `Persons` category to the category labeled `Mammals`.

×![](images/Fig-144.jpg)

Figure 10.4 A semantic network with four objects (`John`, `Mary`, `1`, and `2`) and four categories. Relations are denoted by labeled links.

The semantic network notation makes it convenient to perform inheritance reasoning of the kind introduced in [Section 10.2](#Chapter10-02.xhtml#sec10-2). For example, by virtue of being a person, `Mary` inherits the property of having two legs. Thus, to find out how many legs `Mary` has, the inheritance algorithm follows the `MemberOf` link from `Mary` to the category she belongs to, and then follows `SubsetOf` links up the hierarchy until it finds a category for which there is a boxed `Legs` link—in this case, the `Persons` category. The simplicity and efficiency of this inference mechanism, compared with semidecidable logical theorem proving, has been one of the main attractions of semantic networks.

Inheritance becomes complicated when an object can belong to more than one category or when a category can be a subset of more than one other category; this is called multiple inheritance. In such cases, the inheritance algorithm might find two or more conflicting values answering the query. For this reason, multiple inheritance is banned in some object-oriented programming (`OOP`) languages, such as `Java`, that use inheritance in a class hierarchy. It is usually allowed in semantic networks, but we defer discussion of that until [Section 10.6](#Chapter10-06.xhtml#sec10-6).

<p class="sidebar">Multiple inheritance</p>

The reader might have noticed an obvious drawback of semantic network notation, compared to first-order logic: the fact that links between bubbles represent only binary relations. For example, the sentence `Fly(Shankar, NewYork, NewDelhi, Yesterday)` cannot be asserted directly in a semantic network. Nonetheless, we can obtain the effect of n-ary assertions by reifying the proposition itself as an event belonging to an appropriate event category. [Figure 10.5](#Chapter10-05.xhtml#fig10-5) shows the semantic network structure for this particular event. Notice that the restriction to binary relations forces the creation of a rich ontology of reified concepts.

Description

An arrow labeled `Member Of` points from the bubble `Fly subscript 17` to the `Fly Events` bubble. An arrow labeled `Agent` from `Fly subscript 17` points to the bubble labeled `Shankar`. An arrow labeled `Origin` points from `Fly subscript 17` to the bubble labeled `New York`. An arrow labeled `Destination` from `Fly subscript 17` points to the bubble labeled `New Delhi`. An arrow labeled `During` from `Fly subscript 17` points to the bubble labeled `Yesterday`.

×![](images/Fig-145.jpg)

Figure 10.5 A fragment of a semantic network showing the representation of the logical assertion `Fly(Shankar, NewYork, NewDelhi, Yesterday)`.

Reification of propositions makes it possible to represent every ground, function-free atomic sentence of first-order logic in the semantic network notation. Certain kinds of universally quantified sentences can be asserted using inverse links and the singly boxed and doubly boxed arrows applied to categories, but that still leaves us a long way short of full first-order logic. Negation, disjunction, nested function symbols, and existential quantification are all missing. Now it is possible to extend the notation to make it equivalent to first-order logic—as in Peirce’s existential graphs—but doing so negates one of the main advantages of semantic networks, which is the simplicity and transparency of the inference processes. Designers can build a large network and still have a good idea about what queries will be efficient, because (a) it is easy to visualize the steps that the inference procedure will go through and (b) in some cases the query language is so simple that difficult queries cannot be posed.

In cases where the expressive power proves to be too limiting, many semantic network systems provide for procedural attachment to fill in the gaps. Procedural attachment is a technique whereby a query about (or sometimes an assertion of) a certain relation results in a call to a special procedure designed for that relation rather than a general inference algorithm.

<p class="sidebar">Procedural attachment</p>

One of the most important aspects of semantic networks is their ability to represent default values for categories. Examining [Figure 10.4](#Chapter10-05.xhtml#fig10-4) carefully, one notices that `John` has one leg, despite the fact that he is a person and all persons have two legs. In a strictly logical KB, this would be a contradiction, but in a semantic network, the assertion that all persons have two legs has only default status; that is, a person is assumed to have two legs unless this is contradicted by more specific information. The default semantics is enforced naturally by the inheritance algorithm, because it follows links upwards from the object itself (`John` in this case) and stops as soon as it finds a value. We say that the default is overridden by the more specific value. Notice that we could also override the default number of legs by creating a category of `OneLeggedPersons`, a subset of `Persons` of which `John` is a member.

<p class="sidebar">Default value</p> <p class="sidebar">Overriding</p>

We can retain a strictly logical semantics for the network if we say that the `Legs` assertion for `Persons` includes an exception for `John`:

∀ `x` `x`∈`Persons`∧`x`≠`John`⇒`Leg`(`x`,2).

For a fixed network, this is semantically adequate but will be much less concise than the network notation itself if there are lots of exceptions. For a network that will be updated with more assertions, however, such an approach fails—we really want to say that any persons as yet unknown with one leg are exceptions too. [Section 10.6](#Chapter10-06.xhtml#sec10-6) goes into more depth on this issue and on default reasoning in general.

## 10.5.2 Description logics

The syntax of first-order logic is designed to make it easy to say things about objects. Description logics are notations that are designed to make it easier to describe definitions and properties of categories. Description logic systems evolved from semantic networks in response to pressure to formalize what the networks mean while retaining the emphasis on taxonomic structure as an organizing principle.

<p class="sidebar">Description logic</p>

The principal inference tasks for description logics are subsumption (checking if one category is a subset of another by comparing their definitions) and classification (checking whether an object belongs to a category). Some systems also include consistency of a category definition—whether the membership criteria are logically satisfiable.

<p class="sidebar">Subsumption</p> <p class="sidebar">Classification</p> <p class="sidebar">Consistency</p>

The `CLASSIC` language (`Borgida et al., 1989`) is a typical description logic. The syntax of `CLASSIC` descriptions is shown in [Figure 10.6](#Chapter10-05.xhtml#fig10-6).[6](#Chapter10-08.xhtml#sup10-6) For example, to say that bachelors are unmarried adult males we would write

×![](images/Fig-146.jpg)

Figure 10.6 The syntax of descriptions in a subset of the `CLASSIC` language.

`Bachelor` = `And`(`Unmarried`, `Adult`, `Male`).

The equivalent in first-order logic would be
