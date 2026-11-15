![](bbox=[0.18, 0.1, 0.82, 0.28])

Now suppose the fact type Employee lived first in Country is used to record where people lived first (e.g., Einstein lived first in Germany). This fact type is n:1 rather than m:n. In ORM and UML, such associations may be objectified, and we may attach the temporal information as previously (see Fig. 10.19(a) and B).

ORM currently allows objectification of any fact type. This is fine for a unary fact type, as it has a spanning uniqueness constraint (asserted or implied). However, objectification of a binary or longer fact type without spanning uniqueness constraint is best avoided. For example, it might result in fact types that are not atomic, and lead to awkwardness or confusion (Halpin, 2020). Moreover, remodeling to avoid such objections typically results in a better schema. For example, Fig. 10.19(c) is arguably simpler than Fig. 10.19(a). This schema is also easier to emulate in modeling approaches such as Barker ER that do not allow such objectification, as shown in Fig. 10.19(d).

![](bbox=[0.18, 0.575, 0.82, 0.905])