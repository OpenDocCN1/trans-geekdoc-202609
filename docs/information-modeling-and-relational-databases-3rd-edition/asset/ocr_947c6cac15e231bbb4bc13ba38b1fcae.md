Our examples so far have avoided nested fact types. Recall that nesting is not the same as splitting. If nesting is used, the following spanning rule can be used to avoid splittable fact types: the UC on an objectified association should normally span all its roles.

This rule simply adapts earlier results to the nested case. Suppose the objectified predicate has a UC over only some of its roles. If an attached, outside role has a UC on it, when the outer predicate is flattened we have at least two roles not spanned by a UC.

If an attached role has no UC, then flattening generates a predicate with an embedded FD not expressed as a UC (consider the cases of Figs. 4.49 and 4.50). In either case, the flattened version must split because it is not elementary. Hence, to be elementary in this sense, the nested version must obey the spanning rule.

In the previous version of ORM, the only exception to the spanning rule was to allow 1:1 binaries to be objectified (e.g., Person is husband of / is wife of Person may be objectified as “Marriage”).

The second-generation ORM discussed in this book allows any fact type to be objectified regardless of its UC pattern, and is similar to UML in this aspect (e.g., n:1 associations may be objectified). Although allowed for pragmatic reasons, such exceptions violate elementarity and require special treatment when mapped to logical models. Moreover, objectification without spanning uniqueness often makes the model more complicated than needed.

Consider the output report of Table 4.12. Here, the credit for a given subject is measured in points. The “?” on the second row is a null, indicating that a real value is not recorded (e.g., a lecturer for CS109 might not yet have been assigned).

# Table 4.12 Subject details.

| Subject | Credit | Lecturer |
|---|---|---|
| CS100 | 8 | DBJ |
| CS109 | 5 | ? |
| CS112 | 8 | TAH |
| CS113 | 8 | TAH |

Recall that elementary fact tables can’t contain nulls (because you can’t record half a fact). However, because output reports can group facts of different kinds in the one table, they often do contain nulls (indicating absence of a fact instance).

Now, let’s play the part of an inexperienced—and not very clever—schema designer, so that we can learn by the mistakes made. Looking just at the first row, we might be tempted to treat the information as a ternary:

Subject (.Code) ‘CS100’ worth Credit (.Points) 8 is taught by Lecturer (.Initials) ‘DBJ’.

If we drew the schema diagram now and populated it, we would discover an error because the second row doesn’t fit this pattern (because we don’t allow nulls in our fact