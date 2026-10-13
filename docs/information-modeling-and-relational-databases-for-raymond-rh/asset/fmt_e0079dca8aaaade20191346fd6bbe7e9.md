
Each client selects one insurance coverage (currently `$25,000`, `$50,000`, or `$100,000`) and pays a monthly premium for this coverage. Premiums are determined by coverage, age, and smoking status, as shown in the following schedule. This schedule is stored in the database (it is not computed by a formula). From time to time, this schedule may change in premiums charged, coverages offered, or even age groups. Premiums for both smokers and nonsmokers are always included for each age group/coverage combination. For simplicity, only the latest version of the schedule is stored (a history of previous schedules is not kept). Moreover, payments must be for 1 year at a time and are calculated as 12 times the relevant premium current at the date of payment (using the age of the client at that date). The computer system has an internal clock, which may be viewed conceptually as providing an always up-to-date instance of the fact type Date is today. You may use `today` as an initialized date variable in derivation rules.

![](images/B9780443237904000141/u11-19-9780443237904.jpg)

Although not shown in the schedule, age groups are identified primarily by an age group number (currently in the range `1..4`). Assume that all clients have paid their 12-month fee by completing a form like that shown here (details such as name and address are omitted for this exercise). The first four fields are completed by the insurance agency and the rest by the client. Records of any previous payments are outside the UoD.

![](images/B9780443237904000141/u11-09-9780443237904.jpg)

Choose suitable codes to abbreviate payment methods and card types. Each credit card is used by at most two clients (e.g., husband and wife). In practice, the card type could be derived from the starting digits of the card number, but ignore this possibility for this question.

1.  **(a)** Specify a conceptual schema for this UoD. Include **all** graphic constraints and any noteworthy textual constraints. Include subtype definitions and derivation rules. If a derived fact type should be stored, include it on the diagram with an `**` mark to indicate it is both derived and stored.
2.  **(b)** Should the payment by a client be derived only, stored only, or both? Discuss the practical issues involved in making this decision.
3.  **(c)** Map your conceptual schema to a relational schema, absorbing subtypes while maintaining subtype constraints. Underline keys and mark optional columns with square brackets. Include **all** constraints. As an optional exercise, map any derivation rules.

## 11.4 Advanced Mapping Aspects

The previous section discussed the main steps in the default relational mapping procedure (`Rmap`). Step 0 of this procedure may be refined as shown here. This section discusses these refinements in order and clarifies some fine points. If desired, this section may be safely skipped on a first reading.

| *Rmap Step 0:* | | |
| --- | --- | --- |
| `0.1` | | `Transform opposite unaries; map unaries based on their open/closed semantics.` |
| `0.2` | | `Mentally erase all reference (preferred identification) predicates.` |
| | | `Treat compositely identified object types as "black boxes".` |
| `0.3` | | `Indicate any absorption overrides (separation or partition) for subtypes.` |
| `0.4` | | `Identify any derived fact types that must be stored.` |
| `0.5` | | `Indicate mapping choices for symmetric 1:1 cases.` |
| `0.6` | | `Consider replacing any disjunctive reference schemes by using an artificial or concatenated identifier or mandatory defaults.` |
| `0.7` | | `Indicate mapping choice where required for any objectified associations that have no spanning uniqueness constraint.` |

As background to step 0.1, see the discussion of open/closed world semantics in [Section 10.6](#Ch010_401-479_B9780443237904000244.xhtml#s0060). Two unaries with opposite meaning (e.g., `Person is male`, `Person is female`) should be replaced by a single closed world unary (e.g., `Person is male`) or a mandatory binary (e.g., `Person is of Gender {'M', 'F'}`).

After that, mutually exclusive unaries should be replaced by a binary. For example, in [Fig. 11.33](#Ch011_481-537_B9780443237904000141.xhtml#f0170)(a) the disjunction of the unaries is optional, so it is possible that some applications are pending a decision. In [Fig. 11.33](#Ch011_481-537_B9780443237904000141.xhtml#f0170)(b), the unaries are transformed to a single binary, where the status of the application is identified by a code (`S = Succeeded`, `F = Failed`, `P = Pending`). This transformation is understood to be performed automatically as a preprocessing stage to the rest of `Rmap`.

![Fig. 11.33 Replacing exclusive unaries by a binary.](images/B9780443237904000141/f11-33-9780443237904.jpg)

[Fig. 11.33](#Ch011_481-537_B9780443237904000141.xhtml#B-f0170) Replacing exclusive unaries by a binary.

The final result of the mapping is shown at the bottom of [Fig. 11.33](#Ch011_481-537_B9780443237904000141.xhtml#f0170)(b). For analysis purposes, you may still work with the original conceptual schema.

Remaining unaries are mapped according to their open/closed world assumption. [Fig. 11.34](#Ch011_481-537_B9780443237904000141.xhtml#f0175) shows a simple example, with cases (a), (b), and (c) corresponding to closed world, simple open world, and OWN, respectively. Typically, `Person` would play other mandatory roles and not be independent. In practice, CWA leading to a mandatory Boolean and OWN leading to an optional Boolean are the most useful cases.

![Fig. 11.34 Basic mapping patterns for unobjectified unaries.](images/B9780443237904000141/f11-34-9780443237904.jpg)

[Fig. 11.34](#Ch011_481-537_B9780443237904000141.xhtml#B-f0175) Basic mapping patterns for unobjectified unaries.

[Fig. 11.35](#Ch011_481-537_B9780443237904000141.xhtml#f0180) shows how to map an objectified unary, with cases (a), (b), and (c) corresponding to closed world, simple open world, and OWN, respectively. This mapping preprocesses the functional fact type attached to `Smoking` by attaching it directly to `Person`, renaming the role name `startdate` to `smokingStartdate`, and then mapping as usual, resulting in a single table rather than two. Simple variations apply if the attached role is mandatory (e.g., in the CWA case replace `only if` by `iff`).

![Fig. 11.35 Basic mapping patterns for objectified unaries.](images/B9780443237904000141/f11-35-9780443237904.jpg)

[Fig. 11.35](#Ch011_481-537_B9780443237904000141.xhtml#B-f0180) Basic mapping patterns for objectified unaries.

Step 0.2 involves mentally erasing any reference predicates and treating objectified associations as simple object types. The previous section discussed typical cases. [Fig. 11.36](#Ch011_481-537_B9780443237904000141.xhtml#f0185) depicts a special case. Here, each Olympic Games is identified by the year in which it is held. There are three fact types (`Athlete competes in Games`; `Athlete was born in Year`; `City hosts Games`) and one reference type (`Games is held in Year`).

![Fig. 11.36 Games is identified by a single, explicit reference type.](images/B9780443237904000141/f11-36-9780443237904.jpg)

[Fig. 11.36](#Ch011_481-537_B9780443237904000141.xhtml#B-f0185) Games is identified by a single, explicit reference type.

The reference type must be shown explicitly because `Year` is an entity type, not a value type. One instance of the hosts fact type is The City with name "Sydney" hosts the Games that is held in the Year 2000 CE.
