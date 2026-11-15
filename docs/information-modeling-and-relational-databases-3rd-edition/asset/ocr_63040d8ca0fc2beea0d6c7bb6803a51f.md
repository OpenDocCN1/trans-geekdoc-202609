# ## 5.2 Mandatory and Optional Roles

Consider the output report of Table 5.1. Patients are identified by a patient number. The question mark “?” denotes a null, indicating that an actual value is not recorded. For instance, patient 002 may have a phone but it is not recorded, or he/she may simply have no phone. Different patients may have the same name and even the same phone number, so the table population is not significant.

We must record each patient’s name, but it is optional to record a phone number. Fig. 5.4 shows a preliminary conceptual model for this situation. Conceptual facts are elementary, so they cannot contain nulls. The null in Table 5.1 is catered for by omitting a fact for patient 002 in the fact type Patient has PhoneNr.

In step 5 of the design procedure, each role is classified as mandatory or optional. A **role is mandatory** if and only if, for all states of the database, the role must be played by every member of the population of its object type; otherwise, the role is **optional**. A mandatory role is also called a *total role* because it is played by the total population of its object type.

# ### Table 5.1 Details about hospital patients.

| Patient Nr | Patient Name | Phone |
|---|---|---|
| 001 | Adams C | 2057642 |
| 002 | Brown S | ? |
| 003 | Collins T | 8853020 |

![](bbox=[0.27, 0.545, 0.705, 0.64])

# **FIG. 5.4** A populated schema for Table 5.1.

Which of the four roles in Fig. 5.4 are mandatory and which are optional? If the diagram includes all the fact types for the universe of discourse (UoD), and its sample population is significant, we can easily determine which roles are mandatory.

In practice, however, we mostly work with subschemas rather than the complete, or global schema; and sample populations are rarely significant. In such cases, we should check with the domain expert as to whether the relevant information must be recorded for all instances of the object type (e.g., must we record the name of each patient?).

Consider the two fact roles played by Patient. For the database state shown, the populations of these roles are {001,003} and {001,002,003}. If these are the only fact roles of Patient, then pop(Patient) = {001, 002, 003}. The role of having a name is played by all recorded patients, and the role of having a phone number is played by only some.