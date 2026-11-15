the same derivations are required many times with large volumes of stable data. In such cases, it can be much more efficient to store the derived information so that it can be accessed immediately at later times without having to be recomputed. Typically, in such cases a “drive on update” (eager evaluation) approach is used so that as soon as the base data is updated, the derived information is computed and stored. Recall the bank balance example from Exercise 6.4.

In step 0.4 of the mapping procedure, any derived fact types to be stored should be included on the schema diagram and marked “***”, with the derivation rule also declared. The fact type should then be grouped into a table in the normal way, and the derivation rule mapped as well. For example, the Window schema in Fig. 11.47(a) uses the default mapping so that no column for area is included in its base table. However, the area fact type in Fig. 11.47(b) is marked “***” for storage, so it maps to a base table column.

The rule for computing area may be included in insert and update triggers, or a generated column declaration, a view, or a stored procedure. Care is required with storing derived data. For example, unless the derivation rule is fired every time the relevant base data is updated, the derived values can become outdated.

![](bbox=[0.28, 0.45, 0.52, 0.58])

| Window |
|---|
| PK windowNr |
| height |
| width |

*For each Window, area = height * width.

![](bbox=[0.28, 0.64, 0.52, 0.76])

| Window |
|---|
| PK windowNr |
| height |
| width |
| area |

**For each Window, area = height * width.

FIG. 11.47 Derived fact types may be evaluated lazily (a) or eagerly (b).