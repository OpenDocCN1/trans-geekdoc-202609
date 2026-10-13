
# Independent Object Types

In this example, “Country” denotes the set of all nations on Earth, or perhaps just nations competing in the Olympics. Should we add a value constraint for Country or Country’s role? This would be impractical, because the list of country names is too long (e.g., 161 nations competed in the 1988 summer Olympics) and unstable (e.g., in 1991 the former Soviet Union fragmented into 15 nations). If the schema is reused for many games, this value constraint would need to be updated continually.

Because the list of countries is both large and unstable, we will not specify a list of values for `CountryName` as a *constraint* (we’ll see shortly another way to supply such lists). However, we can declare a syntactic *data type* as a weak form of “value constraint”. For example, we might require each country name to be a string of at most 30 characters.

Although choosing syntactic data types is not the most conceptual or exciting aspect of modeling, it’s something you need to do before you implement the model. Otherwise, you’ll get whatever default data type the system provides, and this won’t always be what you want.

## Answering Queries About Participation

Now suppose that our Olympics information system is required to answer the following questions: *Which countries competed? Which countries didn’t compete?* The first question could be addressed by adding the unary predicate “competed” to Country in [Fig. 6.8](#Ch006_211-271_B9780443237904000025.xhtml#f0045). The competing countries would then all be entered in the single-column table for this unary fact type. Alternatively, we could explicitly record zero for each competing country not winning a given kind of medal.

But what about the second question? This effectively asks: Which countries exist but didn’t compete? This list is usually small, but could be large (e.g., because of a boycott). So, somehow we need a way to record all the existing countries, whether or not they competed. As discussed earlier, putting this list of countries in a constraint is unwise because the list is large and unstable. Although schemas often do evolve, we usually try to design them to be as stable as possible. A classic strategy used is to model the feature so that the changes occur in the database population rather than the schema itself. How can we do this for the current example?

You might be tempted to add a unary predicate “exists” to Country. But such a predicate would apply to all object types in the schema. Moreover, there are formal problems with treating “exists” (an existential quantifier) as a predicate. In principle, we could address the problem by adding another unary predicate “did not compete” for Country and storing noncompetitors here. But such an approach is awkward—Country might play several roles (birthplace, location, etc.) and it may be arbitrary which role is negated to cater for the rest of the countries.

## Reference Tables and Independence

A cleaner approach is to list all existing countries in a *reference table* for Country. A country may appear in this table without playing any elementary fact roles in the schema. Such a country is said to be *independent* because it exists in our model independently of doing anything. An **independent entity type** is a *primitive entity type whose elementary fact roles (if any) are collectively optional*. An *independent value type* may contain some values that play in no facts (elementary or existential).

The term “independent” is not used for subtypes. If an independent object type plays some fact roles, the disjunction of its roles is not mandatory (implicitly or explicitly).

To signify that an object type is independent, an *exclamation mark* “!” is appended to its name. [Fig. 6.9](#Ch006_211-271_B9780443237904000025.xhtml#f0050) depicts Country as independent. Its reference table lists all existing nations. To save space, only the first six countries are listed. The first entry may be verbalized as “The Country with name ‘Afghanistan’ exists”; this is a reference or existential fact.

![Fig. 6.9 In this schema, Country is an independent object type.](images/B9780443237904000025/f06-09-9780443237904.jpg)

[Fig. 6.9](#Ch006_211-271_B9780443237904000025.xhtml#B-f0050) In this schema, Country is an independent object type.

Win counts of zero are included. The first role in the ternary is optional because some nations don’t compete (the data here are fictitious). If wins of zero were excluded (as in [Fig. 6.8](#Ch006_211-271_B9780443237904000025.xhtml#f0045)) and the unary “competed” were added, the disjunction of this role and the wins role would be optional (and a subset constraint would run from the wins to the competed role—subset constraints are treated later). So, *the implied mandatory role rule does not apply to independent object types*.

The reference scheme of an independent entity type is mandatory, so no country may be recorded to compete or win unless it is recorded in the population of Country. To fully populate Country with a list of all nations is a tedious task; however, once done it can be imported into many applications as needed. In practice, most independent object types have fewer instances. As a minor point, the value constraint on Quantity’s role may need to be updated to allow for more events.

If we did not want to know about noncompeting countries, then as an alternative to adding the unary “competed”, we could restrict the meaning of Country to “Competing nation”, mark it as independent, and record only nonzero wins.

## Objectified Associations

*Objectified associations are often independent*, as we often wish to record an association before recording other facts about it. For example, the schema in [Fig. 6.10](#Ch006_211-271_B9780443237904000025.xhtml#f0055) allows us to record the fact that a student has enrolled in a subject before knowing the rating resulting for that enrollment (e.g., at the end of semester).

![Fig. 6.10 Objectified associations are often independent.](images/B9780443237904000025/f06-10-9780443237904.jpg)

[Fig. 6.10](#Ch006_211-271_B9780443237904000025.xhtml#B-f0055) Objectified associations are often independent.

In this example, the simple object type Subject is also independent. In this universe of discourse (UoD), it is possible that all we know about a subject is its subject code. It is not necessary that all subjects be taught. However, *simple object types are rarely independent*.

In most academic domains, we need to know the title of any subject, not just its code. This more realistic situation is depicted in [Fig. 6.11](#Ch006_211-271_B9780443237904000025.xhtml#f0060)(a), where Subject is no longer independent because it has a mandatory fact role. Similarly, in our Olympics example, if all countries had codes as well as names, and we chose code for preferred reference, then Country has CountryName becomes a mandatory fact type, and Country is no longer independent (see [Fig. 6.11](#Ch006_211-271_B9780443237904000025.xhtml#f0060)(b)).

![Fig. 6.11 Simple object types are rarely independent.](images/B9780443237904000025/f06-11-9780443237904.jpg)

[Fig. 6.11](#Ch006_211-271_B9780443237904000025.xhtml#B-f0060) Simple object types are rarely independent.

## Flexibility and FCO-IM

The use of an independent object type or unary predicates instead of a value constraint adds flexibility because the data can be changed without recompiling the schema (and relevant forms, etc.). However, the responsibility for this is now in the hands of the person entering the data rather than the schema designer. Typically, write-access to such reference tables is granted only to database administrators.

A Dutch version of ORM known as Fully Communication Oriented Information Modeling (FCO-IM) treats all entity types, independent or not, as objectified predicates. For example, in [Fig. 6.12](#Ch006_211-271_B9780443237904000025.xhtml#f0065) the entity type Country is depicted as the objectification of a role played by the value type CountryName. The notion of an entity type can then be treated as a derived, rather than a base construct.
