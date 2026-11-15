
Room to Building (i.e., Room is on a Floor that is in Building), adding the condition “= 67” for Building (implicitly applied to BuildingNr), and then requesting Floor and count(Room) for each Floor.

At the relational level, the query may be formulated in SQL using a group-by clause; for example, select floorNr, count(*) from Room where buildingNr=67 group by floorNr. The SQL language is discussed in detail in Chapters 12 and 13.

Choosing reference schemas for entity types is an important aspect of modeling. As a strict guideline, an entity type’s preferred identification scheme must 1:1 map each entity of that type to a tuple of one or more values (either directly or indirectly). So, each preferred reference scheme provides an injection (mandatory, 1:1 mapping). For example, in Fig. 5.26, each building maps directly to a unique building number, and each room maps (indirectly via the reference predicates) to a unique triple of values (building number, floor number, serial number).

In everyday life, weaker kinds of identification schemes are used in some contexts. For example, some people have identifying nicknames (e.g., “the Great White Shark” denotes the golfer Greg Norman). However, in a typical application not everybody has a nickname, so nicknames are not used for preferred reference (they are not mandatory).

Sometimes a 1:many reference scheme is used. For example, a plant or animal type may have more than one identifying common name. For instance, the bird species with the scientific name of *dacelo gigas* may also be identified by any of the following common names: “kookaburra”, “laughing jackass”, “great brown kingfisher”, or “bushman’s clock”. As a botanical example, “gorse” and “furze” refer to the same plant.

In Fig. 5.27(a), common names are used as the preferred identifier for bird species. This choice is signified by the double uniqueness constraint bar. A sample population is included to illustrate the 1:many nature of this reference type. Do you spot any problem with this reference scheme?

This association must not be used for preferred reference because it is not 1:1. Imagine the problems that would arise if we used “kookaburra” to identify a bird species in

![](img/1344db3eba3d550e6edb009556fcd95c_209_0.png)

one part of a database and “laughing jackass” in another part. In the absence of any standard identifier like a scientific name, how would we know that we were talking about the same bird species?

For preferred reference, we must choose a mandatory, 1:1 scheme. Such a scheme may already exist, such as ScientificName as in Fig. 5.27(b). If not, we create one with the help of the domain expert. This might be partly artificial (e.g., standard common name) or completely artificial (e.g., BirdkindNr). Whatever we choose, we need to get the users of the information system to agree upon it.

The scientific name for a bird species is actually a semantic name with two components. For example, in *dacelo gigas*, the “dacelo” is the name of the genus, and “gigas” is a species name. By itself, a species name such as “gigas” or “americana” does not identify a species. For instance, *certhia americana* (the brown creeper) is a different bird species from *parula americana* (the northern parula).

If we wish to query about the genus or species name, we should unpack the naming semantics into a two-part reference scheme, as shown in Fig. 5.28; otherwise we can use the simple reference scheme shown in Fig. 5.27(b).

![](img/1344db3eba3d550e6edb009556fcd95c_210_0.png)

Notice that we can still include facts about common names. Once this schema is fully populated, we could let users interact with the system via the common names, still using the scientific naming convention to establish identity.

Simple 1:1 naming schemes relate entities directly to values (e.g., subjects to subject codes). In life, we sometimes identify entities by 1:1 relating them to other entities (e.g., “the Olympics that were held in the Year 1992,” “the Warehouse that is located in the City ‘Brisbane,’” “the Director who heads the Department ‘Sales’”). Such identification schemes may be chosen for primary reference, and depicted as mandatory 1:1 binaries (e.g., Olympics was held in Year (CE:)). These binaries are then regarded as reference types, not elementary fact types.

This practice is rare. Instead, such binary associations are usually modeled as elementary fact types, and other primary reference schemes are chosen, such as Olympics(.SequenceNr), Warehouse(.Nr). Alternatively, the relevant entity types may be removed by using suitably descriptive predicates. For example, the assertion “The Olympics of Year 2020 were located in City ‘Tokyo’” may be portrayed as a binary association between the entity types Year and City. If the original referential semantics are not needed, another alternative is to use simple value reference, but this is usually a last resort. For example, “Warehouse(.Name ‘Brisbane’)” loses the semantics that this warehouse is located in the city Brisbane.

In most compound reference schemes, each reference predicate is mandatory, so each entity of the same type is identified using the same number of values. In the real world, however, we sometimes encounter identification schemes where only some of the reference roles are optional, but their disjunction is still mandatory. This is called *disjunctive reference*. In these cases, different entities of the same type may be referenced by different numbers of values. For example, consider the botanical identification scheme depicted in Fig. 5.29.

![](img/1344db3eba3d550e6edb009556fcd95c_211_0.png)

FIG. 5.29 With botanical identification, some reference roles are optional.

Some kinds of plants are identified simply by a genus (e.g., *agrostis*). Many other plant varieties are referenced by a combination of genus and species names (e.g., *acacia interior*). Still others are identified by combining genus, species, and infraspecies, where the infraspecies itself is identified by a rank and infraname (e.g., *Eucalyptus fibrosa* ssp. *nubila*). So, depending on the kind of plant, there may be one, two, or four values required to identify it.

The external uniqueness constraint over three roles indicates that each (genus, species, infraspecies) tuple refers to at most one plant kind. In PlantKind reference scheme, only the genus is mandatory. The “o” in the uniqueness constraint symbol indicates that *outer join semantics* applies (see Section 10.1), so for each genus there is at most one plant kind with only a genus name, and for each genus-species combination there is at most one plant kind with no infraspecies. In a relational database, each plant kind maps to a sequence of four values, three of which may be null, and each quadruple is unique (treating null just like any other value). The other external uniqueness constraint declares that the (rank, infraname) pair identifies infraspecies.

Years ago, when Peter Ritson and one of us formalized disjunctive reference within ORM, we added a percentage sign next to the external uniqueness marker, suggesting that “partial” sequences of components are allowed. Nowadays, the basic external uniqueness symbol is used for both ordinary and disjunctive reference. We know the reference scheme is disjunctive if at least one reference role is optional. The minimum requirement for a legal reference scheme is that it provides a mandatory 1:1 mapping to a sequence of one or more values. So, the disjunction of the reference roles must still be mandatory.

The arrow with a subset symbol running from the first role of Plant has Infraspecies to the first role of Plant has SpeciesName denotes the subset constraint that infraspecies is recorded only if species is. Subset constraints are discussed in detail in the next chapter. The reference scheme of Fig. 5.29 is a simplified version of the actual identification scheme used in botany, where complications such as hybrids and cultivars also need to be catered for. Life can be messy!

In practice, try to avoid using a disjunctive reference scheme for preferred reference. With the current example, we should consider introducing an alternative simple identifier (e.g., PlantkindNr). If the users agree to use this in their normal communication, this change can be made to the conceptual model. If not, we can still consider using it in the logical design. If we do this, we still need to model the disjunctive information as a “secondary reference” scheme. Although still messy to implement, moving the disjunction from a primary to a secondary reference simplifies and improves the performance for most implementations.

Another way to avoid disjunctive reference is to concatenate the reference components into a single name. Because this makes it difficult to issue queries about individual components, this is unlikely to be viable with our current example.

Another way to avoid disjunctive reference is to use special default values in the identification scheme. For example, if we use a symbol such as “–” or “#” for “does not exist”, all the reference roles become mandatory, and this special value is treated like any other value in enforcing uniqueness. Although this approach can work in some cases, it is hardly conceptual and may be impractical if you require the user community to use the special values or if you need the same symbol to work with different data types (e.g., numbers as well as strings).

Sometimes, reference chains can get lengthy. A value is identified by a constant. Each entity is referenced directly using a sequence of one or more objects, which in turn may be values or entities. In the latter case, the reference chain continues, recursively, until finally the referencing objects are all values. In this way, each object is ultimately referenced by one or more values that appear as entries in named columns of output reports or database tables.

Candidate identifiers for the same entity are said to be synonyms. Some people use the term “homonym” for a label that refers to more than one entity. For example, the same surname “Jones” may refer to more than one person. Because “homonym” has different grammatical senses, another term such as “nonidentifying label” is preferable. At any rate, the “problem of homonyms” is solved either by augmenting the reference scheme until identification is achieved (e.g., combining surname and initials) or by using a completely different preferred identification scheme (e.g., Social Security number).

In our examples so far, an object’s reference scheme is the same throughout the whole schema. The next chapter examines some cases involving subtypes where this assumption is removed; this leads to context dependent reference. To end this section, we consider the case of variable reference where different units are used for the same physical quantity in the same application domain.
