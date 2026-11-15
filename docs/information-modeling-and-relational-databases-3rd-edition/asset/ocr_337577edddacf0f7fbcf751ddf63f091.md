# 3.5 CSDP Step 3: Trim Schema; Note Basic Derivations

Having drawn the fact types and performed a population check, we now move on to step 3 of our design procedure. Here, we check to see if there are some entity types that should be combined. We also check to see if some fact types can be derived from the others by arithmetic computation.

> CSDP step 3: Check for entity types that should be combined;
> note any arithmetic derivations.

UoD are classified into types. Fig. 3.22 shows the basic division of objects into entities (nonlexical objects) and values (lexical objects). Entities are identified by definite descriptions and may typically change their state, whereas _values_ are constants (typically character strings or numbers). Values might include other objects directly representable on a medium (e.g., sounds), but such possibilities are ignored in this book.

These subdivisions are **mutually exclusive** (i.e., they have no instance in common). For example, no character string can be an entity. The division of a whole into exclusive parts is called a **partition**. You may think of it as cutting a pie up into slices. The slices are _exclusive_ (they don't overlap) and _exhaustive_ (together they make up the whole pie).

Fig. 3.22 gives an example of how the object types might be divided into entity types and value types for a particular business domain. Which kinds of objects exist depends on the UoD. Basically, objects are grouped into the same type if we want to record similar information about them.

For any UoD, there is always a top-level partitioning of its entities into exclusive types: these are called **primitive entity types**. We may introduce _subtypes_ of these primitive types, especially if they have some specific roles to play. In ORM, subtypes are shown connected by an arrow to their supertype. Although shown separately, it is possible that subtypes of a given entity type may overlap.

![](bbox=[0.335, 0.655, 0.695, 0.75])

**FIG. 3.22** Partitioning objects into types of entities and values.

However, _primitive entity types never overlap_. For example, no person can be a city. On a conceptual schema diagram, the visual separation of primitive entity types indicates that these types are mutually exclusive. The same is not true of subtypes. In Fig. 3.23, for example, Person and City are mutually exclusive but Manager and Woman need not be. Subtypes are discussed in detail in Chapter 6.