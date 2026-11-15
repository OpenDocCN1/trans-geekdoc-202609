While the role name “account classifier” *informally* suggests these additional semantics, this has no formal force (other examples in the UML specification use different role names such as “vehicle category,” etc.). So *we need to distinguish the categorization association itself*, for example, by appending a colon to the relationship reading (e.g., “is of:”) and/or the relevant association role names.

![](bbox=[0.302, 0.212, 0.678, 0.328])

FIG. 10.64 Powertype example from the UML 2.0 Superstructure specification.

Even if generalization relationships are annotated with the relevant powertype name, this does not always formally guarantee the required semantics. For example, suppose we classify employees as part-time or full-time, and record their preferred employment status (part-time or full-time), if any. The UML model in Fig. 10.65 has two associations between Employee and EmployeeType, but there is no formal way to know which association is used as the basis for membership in the subtypes.

![](bbox=[0.302, 0.512, 0.65, 0.642])

FIG. 10.65 Powertypes do not guarantee an unambiguous classification scheme.

To solve this problem, we could require role names in the annotation, or adopt the ORM practice of supplying formal subtype definitions. The types Employee, ParttimeEmployee, and FulltimeEmployee are time deictic because their sense is determined in part by the time when their terms are uttered/inscribed.

UML allows generalization annotations to include names for the generalization set (presumably prepended to powertype names when powertypes are involved, but the UML specification does not clarify this possibility). However, such names are treated as informal comments. There is no formal requirement to link these back to properties (attributes or far roles) of the supertype, as done in those database modeling techniques that use discriminators to indicate a basis for subtyping.