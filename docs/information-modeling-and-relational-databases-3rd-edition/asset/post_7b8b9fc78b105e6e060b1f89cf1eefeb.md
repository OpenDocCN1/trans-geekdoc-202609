
Olympics held in Seoul, South Korea, in 1988 (ordered alphabetically by Country). For this application, only three kinds of medals are allowed: gold, silver, and bronze, denoted by the codes “G”, “S”, and “B”, respectively. This constraint is specified by listing the set of possible values {“G”, “S”, “B”} next to the entity type MedalKind.

In the 1988 Olympics, there were 237 events, with one gold, silver, and bronze medal to be awarded for each event (assume that there are no ties). It is possible (although highly unlikely) that the same country wins all medals of a given kind. So the role played here by Quantity (we could name this role “medal kind quantity”) has a maximum possible value of 237, assuming that we exclude other Games (which could have more events) from the domain.

What is the smallest possible value of medal kind quantity? If we want to record that a country won no medals of a given kind, the lowest medal kind quantity is 0. To reduce the size of the database, we could store only facts about actual wins—this approach is suggested by our sample data. In this case, medal kind quantity has a lower limit of 1. Taking the closed world assumption, the fact that a country has won 0 gold medals could then be derived from the absence of an asserted fact about that country winning some gold medals. So, this value constraint has the value range {1..237}.

Because Quantity may well play other roles in the global schema, the {1..237} value constraint applies only to Quantity’s role in this fact type rather than Quantity itself. We call this a role value constraint rather than an object type value constraint. Role value constraints are displayed attached by a dashed line to the role to which they apply, as shown for {1..237} in Fig. 6.8.

An alternative would be to introduce a more specific object type (e.g., MedalKindQuantity) and place the value constraint on that; however, such a move may lead to awkward verbalization, so role value constraints are quite handy.

As a fine point, an object value constraint displayed next to an entity type with a reference mode is actually a role value constraint on the referential role played by the value type. In the NORMA tool, you can display explicitly in this way by toggling ExpandRefMode to True.

In this example, “Country” denotes the set of all nations on Earth, or perhaps just nations competing in the Olympics. Should we add a value constraint for Country or Country’s role? This would be impractical, because the list of country names is too long (e.g., 161 nations competed in the 1988 summer Olympics) and unstable (e.g., in 1991 the former Soviet Union fragmented into 15 nations). If the schema is reused for many games, this value constraint would need to be updated continually.

Because the list of countries is both large and unstable, we will not specify a list of values for CountryName as a constraint (we’ll see shortly another way to supply such lists). However, we can declare a syntactic data type as a weak form of “value constraint”. For example, we might require each country name to be a string of at most 30 characters.

Although choosing syntactic data types is not the most conceptual or exciting aspect of modeling, it’s something you need to do before you implement the model. Otherwise, you’ll get whatever default data type the system provides, and this won’t always be what you want.

Now suppose that our Olympics information system is required to answer the following questions. Which countries competed? Which countries didn’t compete? The first question could be addressed by adding the unary predicate “competed” to Country in Fig. 6.8. The competing countries would then all be entered in the single-column table for this unary fact type. Alternatively, we could explicitly record zero for each competing country not winning a given kind of medal.

But what about the second question? This effectively asks: Which countries exist but didn’t compete? This list is usually small, but could be large (e.g., because of a boycott). So, somehow we need a way to record all the existing countries, whether or not they competed. As discussed earlier, putting this list of countries in a constraint is unwise because the list is large and unstable. Although schemas often do evolve, we usually try to design them to be as stable as possible. A classic strategy used is to model the feature so that the changes occur in the database population rather than the schema itself. How can we do this for the current example?

You might be tempted to add a unary predicate “exists” to Country. But such a predicate would apply to all object types in the schema. Moreover, there are formal problems with treating “exists” (an existential quantifier) as a predicate. In principle, we could address the problem by adding another unary predicate “did not compete” for Country and storing noncompetitors here. But such an approach is awkward—Country might play several roles (birthplace, location, etc.) and it may be arbitrary which role is negated to cater for the rest of the countries.

A cleaner approach is to list all existing countries in a reference table for Country. A country may appear in this table without playing any elementary fact roles in the schema. Such a country is said to be independent because it exists in our model independently of doing anything. An independent entity type is a primitive entity type whose elementary fact roles (if any) are collectively optional. An independent value type may contain some values that play in no facts (elementary or existential).

The term “independent” is not used for subtypes. If an independent object type plays some fact roles, the disjunction of its roles is not mandatory (implicitly or explicitly).

To signify that an object type is independent, an exclamation mark “!” is appended to its name. Fig. 6.9 depicts Country as independent. Its reference table lists all existing nations. To save space, only the first six countries are listed. The first entry may be verbalized as “The Country with name ‘Afghanistan’ exists”; this is a reference or existential fact.

Win counts of zero are included. The first role in the ternary is optional because some nations don’t compete (the data here are fictitious). If wins of zero were excluded (as in Fig. 6.8) and the unary “competed” were added, the disjunction of this role and the wins

![](img/1344db3eba3d550e6edb009556fcd95c_244_0.png)

| Afghanistan | Algeria | G | 0 |
|---|---|---|---|
| Albania | Algeria | S | 0 |
| Algeria | Algeria | B | 0 |
| Angola | Argentina | G | 0 |
| Argentina | Argentina | S | 1 |
| Armenia | Argentina | B | 1 |
| ... | ... | ... | ... |

## FIG. 6.9 In this schema, Country is an independent object type.

role would be optional (and a subset constraint would run from the wins to the competed role—subset constraints are treated later). So, the implied mandatory role rule does not apply to independent object types.

The reference scheme of an independent entity type is mandatory, so no country may be recorded to compete or win unless it is recorded in the population of Country. To fully populate Country with a list of all nations is a tedious task; however, once done it can be imported into many applications as needed. In practice, most independent object types have fewer instances. As a minor point, the value constraint on Quantity’s role may need to be updated to allow for more events.

If we did not want to know about noncompeting countries, then as an alternative to adding the unary “competed”, we could restrict the meaning of Country to “Competing nation”, mark it as independent, and record only nonzero wins.

Objectified associations are often independent, as we often wish to record an association before recording other facts about it. For example, the schema in Fig. 6.10 allows us to record the fact that a student has enrolled in a subject before knowing the rating resulting for that enrollment (e.g., at the end of semester).

![](img/1344db3eba3d550e6edb009556fcd95c_244_1.png)

## FIG. 6.10 Objectified associations are often independent.
