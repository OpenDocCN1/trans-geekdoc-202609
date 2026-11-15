
order of the components, and looks only at the total effect. So even if the add operation had been specified before the delete, this would have been accepted with the same result.

Note that the CIP cannot accept just part of a compound transaction: it is a case of “all or nothing”. Here are a few more simple interactions:

```
add: Person ‘Linda’ lives in Country ‘AU’.           Accepted.
add: Person ‘Selena’ lives in Country ‘AU’.         Accepted.
add: Person ‘Terry’ is a parent of Person ‘Linda’.  Accepted.
add: Person ‘Terry’ is a parent of Person ‘Selena’. Accepted.
nrChildren of Person ‘Terry’?                       2.
list each Person who is a brother of Person ‘Paul’. Terry.
list each Person who lives in Country ‘AU’.         Linda
                                                    Paul
                                                    Selena
list each Person who is an uncle of Person ‘Selena’. No Person.
add: Person ‘Paul’ is a brother of Person ‘Terry’.  Accepted.
list each Person who is an uncle of Person ‘Selena’. Paul.
list each Person who is an aunt of Person ‘Selena’.  Rejected. Unknown fact type.
```

Now suppose the UoD is changed by adding the following constraint:

### C6 Each Person was born in some Year.

Our current database fails to meet this constraint. Suppose we start over with an empty database and try to add the following fact. How would the CIP respond?

```
add: Person ‘Bernard’ is a brother of Person ‘John’.
```

This update request is rejected. It violates two constraints (C1 and C6), as all people listed in the database must have both their country and birth year recorded. Chapter 5 uses the terminology “mandatory roles” to describe such constraints.

In general, the order in which constraints are listed does not matter. However, if an update request violates more than one constraint, this order may determine which constraint is reported as violated if the CIP is configured to report at most one violation. In this case, the CIP would respond thus to the previous request: “Rejected. C1 violated”. If the CIP is configured to report all constraint violations, it would instead respond “Rejected. C1, C6 violated”. As an exercise, convince yourself that with C6 added, the following update requests are processed as shown:

```
add: Person ‘Ken’ lives in Country ‘GB’.             Rejected. C6 violated.
begin
  add: Person ‘Ken’ lives in Country ‘GB’.
  add: Person ‘Ken’ was born in Year 1960.
end                                                   Accepted.
add: Person ‘Ken’ was born in Year 1959.              Rejected. C3 violated.
```

```
begin
    del: Person 'Ken' was born in Year 1960.
    add: Person 'Ken' was born in Year 1959.
    add: Person 'Erik' lives in Country 'NL'.
    add: Person 'Erik' was born in Year 1970.
    add: Person 'Ken' is a brother of Person 'Erik'.
end                          Accepted.
```

The CIP uses the conceptual schema to supervise updates of the database and to respond to questions. Think of the designer of the conceptual schema as the “law giver” and the schema itself as the “law book” containing the laws or ground rules for the UoD. The CIP is the “law enforcer”, as it ensures that these laws are adhered to whenever the user tries to update the database. Like any friendly police person, the CIP is also there to provide information on request.

Whenever we communicate to a person or an information system, we have in mind a particular UoD. Typically, this concerns some small part of the real universe, such as a particular business. In rare cases, we might choose a fictional UoD (e.g., one populated by comic book characters) or perhaps a fantasy world we have invented for a novel that we are writing. Fictional worlds may or may not be (logically) possible.

You can often rely on your own intuitions as to what is logically possible. For instance, a world in which the Moon is colored green is possible, but a world in which the Moon is simultaneously green all over and red all over is not. A possible world is said to be *consistent* and an impossible world is *inconsistent*.

As humans, we carry prodigious amounts of information around in our minds. It is highly likely that somewhere in our personal web of beliefs, some logical contradictions are lurking. In most cases, it does not matter if our belief web is globally inconsistent. When reasoning about a particular UoD, however, consistency is essential. It is easy to show that once you accept a logical inconsistency, it is possible to deduce anything (including rubbish) from it—an extreme case of the garbage in garbage out (GIGO) principle.

There are basically two types of garbage: logical and factual. Inconsistent designs contain logical garbage. For example, we might declare two constraints that contradict one another. A good design method supported by a CASE tool that enforces metarules can help to avoid such problems. Many factual errors can be prevented by the enforcement of constraints on the database. For example, a declared constraint that “Each Person was born in at most one Country” prevents us from assigning a person more than one birth country.

Even if the schema is consistent, and the CIP checks that the database is consistent with this world design, it is still possible to add false data into the database. For example, if we tell the CIP that Einstein was born in France it might accept this even though Einstein was actually born in Germany. If we want our knowledge base to remain factually correct, it is still our responsibility to ensure that all the sentences we enter into the database express propositions that are actually true.

The following exercise provides practice with the concepts discussed in this section and introduces some further constraint types treated formally later.

## Exercise 2.2

- 1. (a) Assuming the conceptual schema is already stored, what are the two main functions of the CIP?
- (b) What are the three main components of the conceptual schema?
- (c) "The CIP will reject a compound transaction if any of its component update operations is inconsistent with the conceptual schema". True or false?

- 2. Assume the following conceptual schema is stored. Constraints apply to each database state. C1 means that each person referred to in the database must have his/her fitness rating recorded. C3 says the possible fitness values are whole numbers from 1 to 10. C4 means that no person can be recorded as an expert at more than one sport, and C5 says a person can be recorded as being an expert at a sport only if that person is also recorded as playing the same sport.

Reference schemes: Person.(Firstname); Sport.(Name); FitnessRating.(Nr)

Base fact types:
- F1 Person has FitnessRating.
- F2 Person plays Sport.
- F3 Person is expert at Sport.

Constraints:
- C1 Each Person has some FitnessRating.
- C2 Each Person has at most one FitnessRating.
- C3 The possible values of FitnessRating are 1 to 10.
- C4 Each Person is expert at at most one Sport.
- C5 Each Person who is expert at some Sport also plays that Sport.

Derivation rules:
- D1 Person is a martial artist if Person plays Sport 'judo' or Person plays Sport 'karatedo'.
- D2 nrPlayers of Sport = count each Person who plays that Sport.

The database is initially empty. The user now attempts the following sequence of updates and queries. For each update, circle the letter if the update is accepted (based on the cumulative state of the database). In cases of rejection, supply a reason (e.g., state which part of the schema is violated). For queries, supply an appropriate response from the CIP.

- (a) add: Person 'Ann' has FitnessRating 9.
- (b) add: Person 'Fred' plays Sport 'tennis'.
- (c) add: Person 'Bob' has FitnessRating 7.
- (d) add: Person 'Ann' has FitnessRating 8.
- (e) add: Person 'Chris' has FitnessRating 7.
- (f) add: Person 'Fred' has FitnessRating 15.
- (g) add: Person 'Ann' plays Sport 'judo'.
