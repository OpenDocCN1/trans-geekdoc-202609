
*   ```
    or not exists Seating1.endtTime)
    ```

*   **then no** `Table` was used by `Seating[1]` **and** was used by `Seating[2]`.

For a detailed discussion of more complex examples of dynamic rules for state transitions expressed in a proposed dynamic rule language for ORM as well as a formalization in terms of logging semantics, see [Balsters and Halpin (2016)](#Ch010_401-479_B9780443237904000244.xhtml#bb0045).

A *guarded transition diagram* allows a guard condition expressed as a formula to be applied to a transition. In practice, many different diagrams and formalisms are used to specify various kinds of dynamic constraints. These include state charts, activity diagrams, state nets, colored Petri nets, process algebra-based task structures, and *Event-Condition-Action* (*ECA*) declarations. ECA languages allow statements of the form **If** *event* **then on** *condition* **then** *action1* \[**else** *action2*\]. This provides a general framework for *controlling the action to be taken on violation of a constraint*. An update is an example of an event, and a constraint violation is an example of a condition.

An extreme version of a transition constraint is to make a fact *immutable* (unchangeable). In other words, once an elementary fact is entered it cannot be deleted. This kind of constraint is best considered in connection with dynamic aspects of subtyping, which we soon discuss.

As mentioned before, some dynamic rules reference states that are separated by a specified period rather than being successive. In practice, many of these rules are *deontic* in nature. For example, consider the rule that invoices *ought* to be paid within 30 days of being issued. This rule may be formally expressed as follows, assuming that the relevant fact types are declared in the schema.

*   ```
    It is obligatory that
    ```

*   ```
    each Invoice that was issued on some Date1
    ```

*   ```
                        is paid on some Date2
    ```

*   ```
    where Date2 <= Date1 + 30 days.
    ```

As the final segment of this section on temporal issues in modeling, we now turn to *dynamic aspects of subtyping*. This assumes that you are familiar with the static aspects of subtyping in ORM and UML discussed in [Sections 6.5](#Ch006_211-271_B9780443237904000025.xhtml#s0040) and [6.6](#Ch006_211-271_B9780443237904000025.xhtml#s0050).

Some proposals from the ontology engineering community have employed type metaproperties to ensure that subtyping schemes are well formed from an ontological perspective. For example, [Guarino and Welty (2002)](#Ch010_401-479_B9780443237904000244.xhtml#bb0505) argue that every property in an ontology should be labeled as rigid, nonrigid, or antirigid.

*Rigid* properties (e.g., being a person) necessarily apply to all their instances for their entire existence. *Nonrigid* properties (e.g., being hard) necessarily apply to some but not all their instances. *Antirigid* properties (e.g., being a patient) apply contingently to all their instances. One may then apply a meta constraint (e.g., antirigid properties cannot subsume rigid properties) to impose restrictions on subtyping (e.g., `Patient` cannot be a supertype of `Person`).

[Guizzardi et al. (2004)](#Ch010_401-479_B9780443237904000244.xhtml#bb0515) proposed a UML profile to stereotype classes into kinds, subkinds, phases, roles, categories, roleMixins, and mixins, together with a set of meta constraints, to help ensure that UML class models are ontologically well formed. [Guizzardi (2005)](#Ch010_401-479_B9780443237904000244.xhtml#bb0510) used this modeling profile in his doctoral thesis on ontological foundations for conceptual information models.

While the aforementioned research provides valuable contributions, we have some reservations about its use in industrial information systems modeling. Our experience with industrial data modelers suggests that the seven-classes scheme would seem overly burdensome to the majority of them.

A simpler alternative that we are currently considering for ORM 2 *classifies each subtype as either a rigid subtype or a role subtype*. A *type is rigid* if and only if each instance of that type must belong to that type for its whole lifetime (in the business domain being modeled). Examples include `Person`, `Animal`, and `Book`.

In contrast, an instance of a *role type* need not always be an instance of that type during its lifetime (in the business domain). Here, we use “role” liberally to include a role played by an object (e.g., `Manager`, `Student`, `Patient`—assuming that these are changeable in the business domain) as well as a phase or state of the object (e.g., `Child`, `Adult`, `FaultyProduct`—assuming changeability).

Although this rigid/role classification scheme applies to any type, we typically require this distinction to be made only for subtypes (to control subtype migration and reduce the classification burden for modelers). As an example, [Fig. 10.32](#Ch010_401-479_B9780443237904000244.xhtml#f0165) depicts `Dog` and `Cat` as rigid subtypes in ORM and UML.

![Fig. 10.32 Rigid subtypes depicted in (a) ORM and (b) UML.](images/B9780443237904000244/f10-32-9780443237904.jpg)

[Fig. 10.32](#Ch010_401-479_B9780443237904000244.xhtml#B-f0165) Rigid subtypes depicted in (a) ORM and (b) UML.

The rigidity notation suggested for ORM is square bracketing of the subtype name (violet for alethic; blue with ^("o") for deontic, e.g., changing from male to female might be possible but forbidden).

The NORMA tool does not yet support this notation to classify subtypes, but it may be informally noted in the subtype’s Note property. For UML, we chose a rigid stereotype. Rigidity is a *dynamic constraint* rather than a static constraint because it restricts state changes (e.g., no dog may change into a cat).

In the previous, the subtypes are asserted. If we add the fact type `Animal is of AnimalKind`, we can use that to derive the `Dog` and `Cat` subtypes. If the fact type `Animal is of AnimalKind` is made *unchangeable* (an animal can’t change its kind), the rigidity of the derived subtypes is now derivable. ORM does not yet support changeability status of fact types. UML recognizes four changeability settings: unrestricted, readOnly, addOnly, and removeOnly. If we derive `Dog` and `Cat` subclasses of `Animal` from its `Animal.kind` attribute, and declare that attribute read-only, the rigidity of the subclasses is implied.

To avoid explicitly declaring role subtypes as such, ORM subtypes may be assumed to be role subtypes by default. Unlike rigid subtypes, *migration between role subtypes is often permitted*. As a simple example, a person may play the role of child, teenager, and adult at different times in his/her lifetime (see [Fig. 10.33](#Ch010_401-479_B9780443237904000244.xhtml#f0170)).

![Fig. 10.33 Migration between role subtypes is allowed.](images/B9780443237904000244/f10-33-9780443237904.jpg)

[Fig. 10.33](#Ch010_401-479_B9780443237904000244.xhtml#B-f0170) Migration between role subtypes is allowed.

Various data model patterns cater for such *historical subtype migration*. The simplest pattern deals with linear state transitions. For example, in [Fig. 10.34](#Ch010_401-479_B9780443237904000244.xhtml#f0175)(a) each role has specific details, and we wish to maintain these details of a person (e.g., favorite toy, favorite pop group) as he/she passes from one role to another.

![Fig. 10.34 Retaining history of subtype-specific details as a person changes roles.](images/B9780443237904000244/f10-34-9780443237904.jpg)

[Fig. 10.34](#Ch010_401-479_B9780443237904000244.xhtml#B-f0175) Retaining history of subtype-specific details as a person changes roles.
