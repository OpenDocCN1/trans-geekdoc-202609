![](bbox=[0.12, 0.09, 0.85, 0.28])

FIG. 9.56 Step 2: Map selected n:1 and 1:1 associations to attributes.

![](bbox=[0.12, 0.33, 0.8, 0.49])

FIG. 9.57 Step 2: Rare cases of value types mapping to classes.

In step 3, we map unaries to Boolean attributes or to subclasses. The example in Fig. 9.58 assumes the usual CWA interpretation for the unary, so anyone not explicitly asserted to smoke is understood to be a nonsmoker. With an *open world approach* (OWA), failure to assert that a given person smokes means it is unknown whether that person smokes.

![](bbox=[0.12, 0.66, 0.85, 0.78])

FIG. 9.58 Step 3: Map unaries to Boolean attributes or subclasses (CWA approach).

If we need to explicitly record that an employee is a smoker or is a nonsmoker, and this might be unknown for some employees, the UML class diagrams are modified so that the smokes attribute has a multiplicity of [0..1] and the {complete} constraint is changed to {incomplete}.