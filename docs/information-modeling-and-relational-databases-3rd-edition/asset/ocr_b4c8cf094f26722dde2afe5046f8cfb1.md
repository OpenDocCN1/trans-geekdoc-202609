“virtual object type” to the schema of Fig. 14.1(a), and by specifying how the predicates of each are translated into the predicates of the other. For example, facts expressed in the first model may be expressed in the second model using the following translations:

+   Patient smokes iff Patient indulges in Vice ‘S’
+   Patient drinks iff Patient indulges in Vice ‘D’

and facts in the second model may be expressed in the first model using the following translation. Like the schemas, these translations can be mapped into formulae of predicate logic. Formal logic may then be used to prove schema equivalence.

+   Patient indulges in Vice iff Patient smokes and Vice has ViceCode ‘S’
+   or
+   Patient drinks and Vice has ViceCode ‘D’

The equivalence just considered is an example of contextual equivalence because it adds definitional context to the original schemas. It also requires formal recognition of “virtual object types” (e.g., Vice exists implicitly in the first schema). This notion is called “object relativity” because it effectively allows that “objects lie in the eye of the beholder”. This permits classical logic proof techniques to be applied to such cases.

The next few sections discuss some theorems that can help us decide whether two schemas are equivalent. These theorems can also help us to transform one schema into an alternative schema that is either equivalent, or at least acceptable close to being equivalent (sometimes we may wish to strengthen or weaken our schema a little by adding or deleting information). The act of reshaping a schema like this is said to be a conceptual schema transformation.

![](bbox=[0.17, 0.575, 0.85, 0.69])

FIG. 14.2 The schema equivalence example in unified modeling language (UML).

Although the conceptual transformations are specified in object-role modeling (ORM), they can be translated into other modeling notations. For example, the previous equivalence (minus definitional context) may be set out in unified modeling language (UML), as shown in Fig. 14.2, using “$\Leftrightarrow$” for “is equivalent to”. Using ORM enables many more complex transformations to be captured graphically, without needing to supplement the diagram with textual constraints. But if you want to work in a non-ORM notation, you should be able to translate the transformation theorems into your preferred notation without much trouble.