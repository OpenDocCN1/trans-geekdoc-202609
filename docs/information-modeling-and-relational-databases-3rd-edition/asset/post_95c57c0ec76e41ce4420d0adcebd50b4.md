
case) or not. A state of affairs may be possible or impossible. Some possible states of affairs may be actual (occur in the actual world).

States of affairs are thus *truth makers*, in that true propositions are about actual states of affairs. In sympathy with the correspondence theory of truth, we treat the relationship between propositions and states of affairs as one of *correspondence* rather than identity.

Although natural language may be ambiguous as to what a given usage of a nominalization phrase denotes (a state of affairs or a proposition), the intended meaning can usually be determined from the context in which the nominalization is used (i.e., the logical predicate applied to talk about it).

Consider the following examples:

- Elvis sang the song “Hound Dog” -- original proposition
- Elvis's singing of the song “Hound Dog” is popular -- actual state of affairs
- That Elvis sang the song “Hound Dog” is well known -- true proposition
- That Elvis sang the song “Hound Dog” is a false belief -- false proposition
- It's snowing outside -- original proposition
- It's true that it's snowing outside -- proposition
- That snowing is beautiful -- state of affairs

The first three uses of the demonstrative pronoun “that” result in propositional nominalization. In the final example, “that” is used in combination with the gerund “snowing” to refer to a state of affairs (propositions aren’t beautiful). In the previous two sentences, “snowing” is a present participle, not a gerund.

As indicated earlier, states of affairs may be actual or not, and propositions may be true or false. In ordinary speech, the term “fact” is often used to mean a true proposition, but when modeling information in ORM, the term “fact” is used in the weaker sense of “proposition taken to be true” (epistemic commitment) by users of the business domain.

Fig. 10.46(a) displays a typical case of objectification in information modeling in ORM. Here, the fact type Country plays Sport is objectified as the object type Playing, which itself plays in another fact type Playing is at Rank. The exclamation indicates that Playing is independent, so Playing instances may exist without participating in other fact types.

![](img/1344db3eba3d550e6edb009556fcd95c_469_0.png)

FIG. 10.46 Objectification of country plays sport as playing in (a) ORM and (b) UML.

Fig. 10.46(b) depicts the same example in UML, with the association between Country and Sport reified into the association class Playing, and the rank fact type modeled as an optional attribute.

Now, consider the question, *Are the objects resulting from objectification identical to the relationships that they objectify?* The UML metamodel answers yes to this question by treating AssociationClass as a subclass of both Association and Class. Because relationships are typically formalized in terms of propositions, this affirmative choice may be appropriate for propositional normalization.

However, we believe that *the objectification process used in modeling information systems is typically situational normalization*, where the object described by the nominalization is a state of affairs rather than a proposition. For situational normalization, we answer this question in the negative, treating fact instances and the object instances resulting from their objectification as nonidentical. An intuitive argument in support of this position follows, based on the information model in Fig. 10.46.

Consider the relationship instance expressed by the sentence: “Australia plays Cricket”. Clearly this relationship is a proposition, which is either true or false. Now, consider the object described by the definite description: “The Playing by Australia of Cricket” or, more strictly, “The Playing by the Country that has CountryCode ‘AU’ of the Sport named ‘Cricket’”. Clearly, this Playing object is a state of affairs (e.g., an activity). It makes sense to say that Australia’s playing of cricket is at rank 1, but it makes no sense to say that Australia’s playing of cricket is true or false.

Therefore, the Playing instance (The Playing by Australia of Cricket) is an object that is ontologically distinct from the fact/relationship that Australia plays Cricket. Our experience is that the same may be said of any typical objectification example that one finds in information system models. In this case, so-called “objectified relationships” are in 1:1 correspondence with the relationships that they objectify, but they are not identical to those relationships. Compare this with first-order logic, where predicate formulae are often tested for equivalence (≡) but not identity (=). Terms or individuals may be identical, but not equivalent.

In information models, one may sometimes encounter propositional nominalizations, where the noun phrase refers to a proposition rather than a state of affairs (e.g., [the fact] that Australia plays cricket is well known; the proposition that Australia plays cricket is true). A related although different case is where the noun phrase refers to a communication act rather than a proposition (e.g., the assertion that Australia plays cricket was made by Don Bradman). We delay discussion of such cases until the end of this section.

To facilitate high-level declaration of rules and queries on information models that make use of objectification, ORM includes (implicitly or explicitly) *link fact types* that link or relate the objectification result to the objects in the relationship that has been objectified. For example, the definite description “The Playing that: is by the Country that has CountryCode ‘AU’; and is of the Sport that has SportName ‘Cricket’” makes use of the *linking fact types* Playing is by Country and Playing is of Sport, as shown in Fig. 10.47(a).

![](img/1344db3eba3d550e6edb009556fcd95c_471_0.png)

FIG. 10.47 Objectification in ORM uses linking fact types for relational navigation.

Internally, link fact types connect objectified associations to their component object types. By default, display of link fact types is suppressed. If displayed, dashed lines are used. The external uniqueness constraint indicates that each (Country, Sport) pair projected from the attached roles relates to at most one Playing object.

Default predicate readings for the linking predicates are assigned, such as “involves”, appended by numbers if needed to distinguish linking fact types that link back to the same object type (which plays more than one role in the fact type being objectified). The modeler may edit these default readings to provide more meaningful readings for the link fact types, as shown in Fig. 10.47.

The diagram in Fig. 10.47(a) is best understood as an abbreviation of the diagram in Fig. 10.47(b). Here, Playing is a normal object type that is related back to the Country and Sport object types using the linking fact types mentioned earlier. The equality constraint depicted by a circled “=” indicates that the (Country, Sport) pairs in the population of the Country plays Sport fact type must be identical to the population of the (Country, Sport) pairs projected from the Country and Sport roles in the join path Playing is by Country and is of Sport. For clarification purposes, the role sequence numbers for the equality constraint are displayed here.

A similar analysis applies to the objectification of ternary and longer facts. For example, we might objectify Country plays Sport in Year as an object type Playing that has a third link fact type Playing is in Year whose year role adds a third component to the composite reference scheme for Playing.

With respect to our example in Fig. 10.47, this equivalence might be introduced to the model in one of three ways: (1) Start with the fact type Country plays Sport, and then objectify it as Playing; (2) start with the fact types Playing is by Country and Playing is of Sport and then define Country plays Sport as a fully derived fact type in terms of them; or (3) start with the three fact types Country plays Sport, Playing is by Country, and Playing is of Sport and then assert the equality constraint (corresponding to the equivalence) between them. Regardless of which way is used, the model fragment is internally stored in terms of the structure shown in Fig. 10.47(b).

Although ORM treats objectification in this way internally, by default the link fact types and 1:1 correspondence are not displayed on the diagram. So, diagrammatically objectification normally appears simply as in Fig. 10.46(a).
