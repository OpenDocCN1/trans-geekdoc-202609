details about skill level. We discuss objectified relationship types and association classes later.

Another problem with multivalued attributes is that queries on them need to extract the components, and hence complicate the query process for users. As an example, compare queries Q1, Q2 expressed in ConQuer (an ORM query language) with their counterparts in object query language (OQL, proposed by the ODMG). Although this example is trivial, the use of multivalued attributes in complex structures can make it harder for users to express their requirements.

+   (Q1) List each Color that is of Flag 'USA'.
+   (Q2) List each Flag that has Color 'red'.
+   (Q1a) select x.colors from x in Flag where x.country = “USA”
+   (Q2a) select x.country from x in Flag where “red” in x.colors

For such reasons, multivalued attributes should normally be avoided in analysis models, especially if the attributes are based on classes rather than data types. If we avoid multivalued attributes in our conceptual model, we can still use them in the actual implementation. Some UML and ORM tools allow schemas to be annotated with instructions to override the default actions of whatever mapper is used to transform the schema to an implementation. For example, the ORM schema in Fig. 9.9 might be prepared for mapping by annotating the roles played by NickName and Color to map as sets inside the mapped Flag structure. Such annotations are not a conceptual issue, and can be postponed until mapping.

# 9.4 Associations

UML uses Boolean attributes instead of unary relationships, but allows relationships of all other arities. Optionally, each association may be given at most one name. Association names normally start with a capital letter. Binary associations are depicted as lines between classes. Association lines may include elbows to assist with layout or when needed, for example, for ring relationships. Association roles appear as line ends instead of boxes, but may be given role names. Once added, role names may not be suppressed. Verbalization into sentences is possible only for infix binaries, and then only by naming the association with a predicate reading (e.g., “Employs”) and using an optional marker “▶” to denote the direction.

Fig. 9.10 depicts two binary associations in UML and ORM. On the UML diagram, the association names, their directional markers, and some role names are displayed. In UML, association names are optional, but role names are mandatory. If a role name is not supplied, the role’s name is assumed to be the name of its class (e.g., “employee”). If two or more roles are played by the same class, the roles must be given different names to distinguish them (e.g., “buyer”, “acquisition”). In the ORM diagram, forward and inverse predicate readings are shown; at most one of these may be omitted. Role names are optional in ORM, and their display (in square brackets) may be toggled on or off.