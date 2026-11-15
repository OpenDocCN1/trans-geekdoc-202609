
Because you can hold a report (or at least a copy of a report) in your hand, it is natural to think of it first as an object and later ask yourself how to identify it. In this case, we use both the year and the department to coreference it, as in Fig. 14.22(a). The nested approach in Fig. 14.22(b) treats a report as a relationship between Department and Year. The authors find this unnatural, but because both map the same way, you may choose which one suits your taste.

![](img/1344db3eba3d550e6edb009556fcd95c_723_0.png)

If at least one of the object types used for the composite identification is a value type, then coreferencing is often more natural than nesting. Recall the following coreferenced example: Subject (is offered by Department, has SubjectTitle). We could model this instead by objectifying the association Department offers a subject with SubjectTitle, but this seems unnatural. As another example, consider the composite reference scheme Account (is at Branch, has AccountNr).

![](img/1344db3eba3d550e6edb009556fcd95c_723_1.png)

For efficiency, we sometimes introduce a new, simple identifier to replace a composite one, such as Subject(.code). In this case, the former reference types become elementary fact types. For example, in Fig. 14.23(a) a report number is introduced to identify annual reports. We could use a plain serial number (e.g., 1, 2, ...) or a coded number for humans to derive the semantics (e.g., “RES-2008”, “SAL-2008”, ...). Though unnatural, a simple identifier may be introduced for Report even though it remains objectified, as shown in Fig. 14.23(b).

Fig. 14.23(a) includes the relationship types Report is for Year; Report is by Department. These were reference types in Fig. 14.22(a), but are now elementary fact types. For example, two fact instances might be Report “RES-2008” is for Year 2008; Report “RES-2008” is by Department “Research”. If the semantic basis of such introduced identifiers is unstable, then plain serial numbers might be preferred (e.g., suppose departments are often split, merged, or renamed). However, if the semantic basis is stable, such “information-bearing” identifiers can lead to efficiency gains by reducing the need to perform relational joins when information about the object is spread over many tables.

For example, suppose one table is used to store the data in Table 14.3 as well as an extra column for reportNr, and a separate table is used to store the m:n fact type Employee.(nr) authored Report.(nr). To find out who authored what reports, most users would be content with a listing of this second table, if meaningful report identifiers such as “RES-2008” are used, because this would be enough for them to deduce the year and department. However, if plain serial numbers are used, most users would want the year and department listed too, requiring a join to the first table. As another example, consider the use of subject codes (e.g., “CS115”) in listing results.

If a new identifier is introduced, the new schema is no longer strictly equivalent to the original one. For example, the schemas in Fig. 14.23 are stronger than the schemas in Fig. 14.22. Any schema strengthening or weakening should result from a conscious decision of the modeler. However, shifting between a coreferenced and a nested approach (as in Fig. 14.22) may be treated as an equivalence transformation.

![](img/1344db3eba3d550e6edb009556fcd95c_724_0.png)

The general theorem, called N/CR (nest/coreference), is set out in Fig. 14.24. Here, the objectified predicate R has n roles, where n is at least 2. The object types A1...An are not necessarily distinct. Although not shown in the figure, we assume the nested and coreferenced object types have at least one role attached.

An object type is independent if the disjunction of its fact roles is optional. If independent, the object type must be explicitly marked so by appending “!” to its name. For example, look back at Fig. 14.21(b) and (c), and suppose that enrollments are recorded before any results are known. The mandatory role constraint must now be removed from the rating association, and the Enrollment object type renamed “Enrollment!”. As shown shortly, a more drastic change is needed to the schema in Fig. 14.21(a) to maintain a flattened approach.

As long as the nested or coreferenced object type plays only one fact role, and this role is mandatory, we may transform to a single, flattened fact type. Recall the example in Fig. 14.21. In such a case, the flattened approach is usually recommended because it gives a simpler diagram, is easier to verbalize, and it sometimes avoids arbitrary decisions about which part of the predicate to objectify.

When a ternary or longer predicate has just one uniqueness constraint, and this spans all but one of its roles, the subpredicate spanned by this UC provides the best choice for objectifying. This was our choice in Fig. 14.21. In principle, we could pick any subpredicate to objectify. For example, suppose in Fig. 14.25(a) that we objectify the subpredicate comprising the first and third roles, instead of the first two roles. This yields the awkward schema shown in Fig. 14.25(b).

The external UC is needed to capture the UC in the flattened version (i.e., each student obtains at most one rating for each subject). Notice also that the UC on the outer predicate is compound. Although it maps to the same relational schema as the others, Fig. 14.25(b) is more difficult for a human to understand.

![](img/1344db3eba3d550e6edb009556fcd95c_725_0.png)

If a ternary or longer predicate has overlapping UCs, then any objectification is best based on one of these. Each other UC in the flattened version is then captured by an external UC. See Figs. 4.40 and 4.41 for an earlier example.

With overlapping UCs, there is more than one “natural” choice of a subpredicate to objectify. This is also true if a ternary or longer predicate has a spanning UC, such as Lecturer visits Country in Year. Here, we could objectify any of three role pairs: roles 1 and 2; roles 1 and 3; or roles 2 and 3. Unless there are additional facts about the subpredicates, the flattened fact type provides the simpler approach.

Fig. 14.26 shows the ternary version of the N/F (nest/flatten) equivalence theorem. Here A, B, and C need not be distinct. A spanning UC over the roles in the nested object type S is assumed. Typically, a UC spans the A and B roles in R; this is equivalent to a UC over the first role of T. For equivalence, the predicates must be formally related by the condition shown in the where clause.

In Fig. 14.26, if a UC spans all the roles of R, then a UC spans both roles of T. We do not bother stating this corollary in the figure because each predicate has an implied UC spanning its full length. Recall that for generality, schemas used to depict theorems may omit constraints that are not relevant to the transformation.

![](img/1344db3eba3d550e6edb009556fcd95c_726_0.png)

Corollaries: A UC exactly spans the A, B roles of R iff a simple UC spans the first role of T. A binary UC over the A, C (or B, C) roles of R is equivalent to an external UC over the A, C (or B, C) roles, respectively, in the nested version.

![](img/1344db3eba3d550e6edb009556fcd95c_726_1.png)

FIG. 14.26 N/F: The nested version is equivalent to the flattened version.

Our equivalence theorems state formal connections between predicates in the different versions, but do not specify how predicate names used in one schema might help choose the different predicate names used in the other. A computer-aided software engineering (CASE) tool could generate suggested names, but humans can often provide more natural ones (cf. generation of table names in relational mapping).

In choosing identifiers, we should ensure that their background meaning agrees with the formal connection required by the transformation rule. This still leaves many possibilities. In Fig. 14.25(a), for example, instead of “... for ... scored ...” we might use “... enrolled in ... obtaining ...”.

Note that because nesting can always be replaced by coreferencing, we could specify CR/F (coreference/flatten) equivalence theorems analogous to any N/F theorem. For example, consider transforming between the two schemas in Fig. 14.21. To save space, however, we limit our unflattening discussion to nesting.

The ternary nest/flatten equivalence may be generalized to flattened fact types of any arity above two. Note that nesting always introduces an extra role (to be played by the objectified association). If we objectify m roles of an n-ary predicate, the outer predicate will have n – m + 1 roles. This is shown in Fig. 14.27(a), where other object types and role connectors are omitted for simplicity.

Recall that each UC of an elementary predicate must span at least all but one of its roles. If a UC exactly spans all but one role of a predicate, and we objectify on this UC, the outer predicate in the nested version has two roles, with a simple UC on its first role (Fig. 14.27(b)).
