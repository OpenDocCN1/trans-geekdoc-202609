
### 示例代码

```
def inCourseHasNrEnrollments(s, c, n): n = count[(e): isanEnrollmentByStudent(s, e) and isanEnrollmentInCourse(e, c)]
ic (s, c, n) requires inCourseHasNrEnrollments(s, c, n) implies n <= 2
```

The *external frequency constraint* in example (d) ensures that for each country, at most two politicians are both in its government and are a coregent. This constraint may be formulated using the count function or instead simply thus:

```
ic (p1, p2, p3, c) requires (isaCoregent(p1) and servesOnGovtOf(p1, c) and isaCoregent(p2) and servesOnGovtOf(p2, c) and isaCoregent(p3) and servesOnGovtOf(p3, c)) implies p1 = p2 or p1 = p3 or p2 = p3
```

*Ring constraints* are easy to specify in Rel. The *reflexive* ring constraint that people know themselves may be expressed as: `ic(p) requires Person(p) implies knows(p, p)`. The *irreflexive* ring constraint that nobody is a parent of himself/herself may be expressed as: `ic (p) requires not isaParentOf(p, p)`. The *symmetric* constraint on siblinghood may be specified thus: `ic (p1, p2) requires isaSiblingOf(p1, p2) implies isaSiblingOf(p2, p1)`. The *asymmetric* ring constraint that nobody is a parent of himself/herself may be expressed thus: `ic (p1, p2) requires isaParentOf(p1, p2) implies not isaParentOf(p2, p1)`.

The *transitive* nature of the `isOlderThan` relation may be formulated as follows: `ic (p1, p2, p3) requires (isOlderThan(p1, p2) and isOlderThan(p2, p3)) implies isOlderThan(p1, p3)`. The *intransitive* constraint on the direct precedence relation may be formulated as follows: `ic (e1, e2, e3) requires (directlyPrecedes(e1, e2) and directlyPrecedes(e2, e3)) implies not directlyPrecedes(e1, e3)`.

The ancestorhood relation may be defined as follows: `def isanAncestorOf(p1, p2): isaParentOf(p1, p2) or isaParentOf(p1, p3) and isanAncestorOf(p3, p2)`. The *acyclic constraint* on ancestorhood may be specified thus: `ic (p) requires not isanAncestorOf(p, p)`.

The pair-*subset constraint* in Figure 17.20(a) ensures that each student who passed a course also enrolled in that course. This may be expressed in Rel thus: `ic (s, c) requires passedCourse(s, c) implies enrolledInCourse(s, c)`.

The *subset constraint over a join path* in [Fig. 17.20](#Ch017_875-933_B9780443237904000050.xhtml#f0105) ensures that each advisor who serves in a country must speak at least one language that is used in that country. This constraint may be expressed as follows:

![Fig. 17.20 Some subset constraints.](images/B9780443237904000050/f17-20-9780443237904.jpg)

[Fig. 17.20](#Ch017_875-933_B9780443237904000050.xhtml#B-f0105) Some subset constraints.

```
ic (a, c) requires servesInCountry(a, c) implies (speaksLanguage(a, l) and isaLanguageUsedBy(l, c))
```

The simple examples give some idea of the expressive power of Rel for modeling ORM constraints. Large, highly complex ORM models can also be mapped to Rel structures.

### Other Database Varieties

Specialized database varieties are sometimes invoked to deal with certain types of applications. *Spatial databases* require efficient management of spatial data, such as maps (roads, land, etc.), two-dimensional designs (circuits, town planning, etc.), and three-dimensional designs (visualization of medical operations, molecular structures, flight paths, etc.). They provide built-in support for spatial data types (points, lines, polygons, etc.), spatial operators (overlap, contains, intersect, etc.), and spatial indexes (R-trees, quad trees, etc.). This allows efficient formulation and processing of spatial queries, such as, How many houses are there within 5 km of the proposed shopping center? Which flights fly over the greater LA area? Which diagrams are similar to diagram 37?

Previously, special systems were used for spatial data while a relational DBMS was used for alphanumeric data. The current trend is to manage both standard and spatial data in the one system. A typical application of a geographic information system (GIS) might proceed as follows: standard data on traffic accidents is entered; the road maps are displayed to highlight the accident sites; and this is now used to determine regions where extra precautions need to be taken (e.g., radar traps).

Historically, GIS vendors adopted three main approaches: hybrid (georelational-objects in a spatial file store are given identifiers that can be referenced in relational tables); integrated (spatial and nonspatial data are stored in relational tables); and object-oriented (all data is stored in an ODB). More recently, many spatial database applications as well as other applications using nonstandard data have been implemented using object-relational technology.

Although time has only one dimension, unlike space's three dimensions, the efficient management of *temporal information* is no easy task. If historical rather than snapshot records need to be maintained about objects, time will feature largely in the modeling.

As discussed in [Chapter 10](#Ch010_401-479_B9780443237904000244.xhtml), a variety of approaches may be adopted for modeling time. In some cases, we simply include object types such as Time and Period on the conceptual schema and map these like other object types. Distinctions may be needed between transaction time (when the system records a fact) and valid time (when the fact is true in the UoD being modeled). Often, we need to make use of temporal relations (such as before and after) and temporal operations (e.g., to compute an interval between two time points).

The SQL standard currently includes only basic support for temporal data, and sometimes an ordinary relational database does not allow temporal aspects to be implemented efficiently. For such applications, special DBMSs known as "temporal database systems" are sometimes used; these provide in-built support for automatic time stamping and the various temporal operators.

Most work on temporal databases focuses on maintaining relevant histories of application objects through time, with the assumption that the conceptual schema itself is fixed. Moving up one level, the problem becomes more complicated if we allow the conceptual schema itself to change with time. This is one aspect of the schema evolution problem.

Moving up another level, we might allow the conceptual metaschema itself to change with time (e.g., we might decide at a later stage to allow constructors for complex object types in our conceptual schema language). The management of such higher-order evolution has been addressed in research on evolving information systems. This topic provides one motivation for the discussion on metamodeling in [Chapter 18](#Ch018_935-1005_B9780443237904000104.xhtml).

Centralized and distributed databases were discussed earlier in this chapter. A further dimension is offered by *federated databases*. These deal with situations where there is a need for data sharing between several different database systems, possibly heterogeneous (e.g., some relational, some column-oriented, some key-value, and so on). In this framework, each individual system maintains its local autonomy and communicates with other systems on an as-needs basis. As the heterogeneity problem requires translation between different data models, the control of federated systems is nontrivial.

Interest in federated databases has been accelerated by the advent of cloud computing. Most organizations find that management of a collection of heterogeneous databases can be a headache, but this can be greatly eased by outsourcing functionality to a cloud service provider. Three levels of service are typically offered:

*Infrastructure as a Service (IaaS)* provides basic processing, storage, and networking functionality, based on dedicated or virtual hardware. This essentially replicates an in-house data center but within the cloud service. Users remain responsible for standard management functions.
