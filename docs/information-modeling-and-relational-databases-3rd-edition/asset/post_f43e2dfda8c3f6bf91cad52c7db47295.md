

| ClientNr | Referrer | Birth date | Smoking status | Emp. status | Job | Work phone | Acct. firm |
|---|---|---|---|---|---|---|---|
| 101 | ? | 15/2/46 | NS | EA | lecturer | 3650001 | – |
| 102 | ? | 15/2/46 | S | SE | builder | 9821234 | Acme |
| 103 | 101 | 1/1/70 | NS | NE | – | – | – |
| 104 | 103 | 3/4/65 | S | EA | painter | ? | – |
| 105 | ? | 1/1/70 | NS | SE | painter | 2692900 | ? |

For each client, a record of major illnesses (if any) is kept; one recovery figure and hospital is noted for each client illness. The extract for clients 101–105 is shown.

| ClientNr | Illness | Degree (%) of recovery | Hospital treated |
|---|---|---|---|
| 102 | Stroke | 90 | Wandin Valley |
| | Diabetes | 80 | Burrigan |
| 103 | Diabetes | 95 | Wandin Valley |

Each client selects one insurance coverage (currently $25,000, $50,000, or $100,000) and pays a monthly premium for this coverage. Premiums are determined by coverage, age, and smoking status, as shown in the following schedule. This schedule is stored in the database (it is not computed by a formula). From time to time, this schedule may change in premiums charged, coverages offered, or even age groups. Premiums for both smokers and nonsmokers are always included for each age group/coverage combination. For simplicity, only the latest version of the schedule is stored (a history of previous schedules is not kept). Moreover, payments must be for 1 year at a time and are calculated as 12 times the relevant premium current at the date of payment (using the age of the client at that date). The computer system has an internal clock, which may be viewed conceptually as providing an always up-to-date instance of the fact type Date is today. You may use “today” as an initialized date variable in derivation rules.

| Age (y) | Nonsmoker: 25,000 coverage | Nonsmoker: 50,000 coverage | Nonsmoker: 100,000 coverage | Smoker: 25,000 coverage | Smoker: 50,000 coverage | Smoker: 100,000 coverage |
|---|---|---|---|---|---|---|
| 21–39 | 5.00 | 7.50 | 12.50 | 6.50 | 10.50 | 18.50 |
| 40–49 | 6.50 | 10.50 | 18.50 | 10.00 | 17.50 | 32.50 |
| 50–59 | 13.00 | 23.50 | 34.00 | 24.00 | 45.50 | 88.50 |
| 60–69 | 36.50 | 70.50 | 138.50 | 57.50 | 112.50 | 222.50 |

Although not shown in the schedule, age groups are identified primarily by an age group number (currently in the range 1..4). Assume that all clients have paid their 12-month fee by completing a form like that shown here (details such as name and address are omitted for this exercise). The first four fields are completed by the insurance agency and the rest by the client. Records of any previous payments are outside the UoD.

ClientNr: ......... Date: ..........
Insurance coverage: $ .........
Payment for next 12 months' insurance: $ ................
Method of payment (Please check one): ☐ cash   ☐ check   ☐ credit card
If paying by credit card, complete the following:
☐ Visa   ☐ Mastercard   ☐ Bankcard
Card Number: [ ][ ][ ][ ][ ][ ] [ ][ ][ ][ ][ ] [ ][ ][ ][ ]
Card expiration date: [ ][ ]/[ ][ ]

Choose suitable codes to abbreviate payment methods and card types. Each credit card is used by at most two clients (e.g., husband and wife). In practice, the card type could be derived from the starting digits of the card number, but ignore this possibility for this question.

- (a) Specify a conceptual schema for this UoD. Include **all** graphic constraints and any noteworthy textual constraints. Include subtype definitions and derivation rules. If a derived fact type should be stored, include it on the diagram with an “***” mark to indicate it is both derived and stored

- (b) Should the payment by a client be derived only, stored only, or both? Discuss the practical issues involved in making this decision.

- (c) Map your conceptual schema to a relational schema, absorbing subtypes while maintaining subtype constraints. Underline keys and mark optional columns with square brackets. Include **all** constraints. As an optional exercise, map any derivation rules.

## 11.4 Advanced Mapping Aspects

The previous section discussed the main steps in the default relational mapping procedure (Rmap). Step 0 of this procedure may be refined as shown here. This section discusses these refinements in order and clarifies some fine points. If desired, this section may be safely skipped on a first reading.

### Rmap Step 0:

- 0.1 Transform opposite unaries; map unaries based on their open/closed semantics.
- 0.2 Mentally erase all reference (preferred identification) predicates.
  Treat compositely identified object types as “black boxes”.
- 0.3 Indicate any absorption overrides (separation or partition) for subtypes.
- 0.4 Identify any derived fact types that must be stored.
- 0.5 Indicate mapping choices for symmetric 1:1 cases.
- 0.6 Consider replacing any disjunctive reference schemes
  by using an artificial or concatenated identifier or mandatory defaults.
- 0.7 Indicate mapping choice where required for any objectified associations
  that have no spanning uniqueness constraint.

As background to step 0.1, see the discussion of open/closed world semantics in Section 10.6. Two unaries with opposite meaning (e.g., Person is male, Person is female) should be replaced by a single closed world unary (e.g., Person is male) or a mandatory binary (e.g., Person is of Gender {‘M’, ‘F’}).

After that, mutually exclusive unaries should be replaced by a binary. For example, in Fig. 11.33(a) the disjunction of the unaries is optional, so it is possible that some applications are pending a decision. In Fig. 11.33(b), the unaries are transformed to a single binary, where the status of the application is identified by a code (S=Succeeded, F=Failed, P=Pending). This transformation is understood to be performed automatically as a preprocessing stage to the rest of Rmap.

![](img/1344db3eba3d550e6edb009556fcd95c_544_0.png)

FIG. 11.33 Replacing exclusive unaries by a binary.

The final result of the mapping is shown at the bottom of Fig. 11.33(b). For analysis purposes, you may still work with the original conceptual schema.

Remaining unaries are mapped according to their open/closed world assumption. Fig. 11.34 shows a simple example, with cases (a), (b), and (c) corresponding to closed world, simple open world, and OWN, respectively. Typically, Person would play other mandatory roles and not be independent. In practice, CWA leading to a mandatory Boolean and OWN leading to an optional Boolean are the most useful cases.

(a) CWA:
Person ! (.Firstname) smokes [isSmoker] -> Box: Bill
Ann
Bill
Colin
Implicit storage of negations (Ann and Colin don't smoke)
=> Person ( [firstname], isSmoker )
This requires explicit storage of negations

(b) OWA:
Person ! (.Firstname) smokes [isSmoker] -> Box: Bill
Ann
Bill
Colin
It is unknown whether Ann or Colin smoke
=> Person ( [firstname], [isSmoker] )
This forbids explicit storage of negations

(c) OWN:
Person ! (.Firstname) smokes [isSmoker] -> Box: Bill
Ann
Bill
Colin
~ Colin
Colin doesn't smoke.
It is unknown whether Ann smokes.
=> Person ( [firstname], [isSmoker] )
This allows explicit storage of negations

FIG. 11.34 Basic mapping patterns for unobjectified unaries.

(a) CWA:
"Smoking !"
Person ! (.Id) smokes [isSmoker] began on [startdate] Date (mdy)
=> Person ( [personId], isSmoker, [smokingStartdate]¹ )
¹not null only if isSmoker = true

(b) OWA:
"Smoking !"
Person ! (.Id) smokes [isSmoker] began on [startdate] Date (mdy)
=> Person ( [personId], [isSmoker], [smokingStartdate] )

(c) OWN:
"Smoking !"
Person ! (.Id) smokes [isSmoker] began on [startdate] Date (mdy)
=> Person ( [personId], [isSmoker], [smokingStartdate]¹ )
¹not null only if isSmoker = true

FIG. 11.35 Basic mapping patterns for objectified unaries.

Fig. 11.35 shows how to map an objectified unary, with cases (a), (b), and (c) corresponding to closed world, simple open world, and OWN, respectively. This mapping preprocesses the functional fact type attached to Smoking by attaching it directly to

