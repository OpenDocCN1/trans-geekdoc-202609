
Most versions of ER do not allow subset, equality, or exclusion constraints between role sequences, or attributes, to be included on the schema diagram (see [Chapter 8](#Ch008_309-346_B9780443237904000177.xhtml)). Unified modeling language (UML) includes graphic symbols for subset constraints only between whole associations, and exclusion constraints only in the context of an exclusive-or constraint between roles (see [Chapter 9](#Ch009_347-399_B9780443237904000013.xhtml)). Recent versions of entity-relationship modeling (ER) as well as UML offer basic support for subtyping, but ignore the need for formal subtype definitions or context-dependent reference (see [Chapters 8](#Ch008_309-346_B9780443237904000177.xhtml) and [9](#Ch009_347-399_B9780443237904000013.xhtml)).

Some versions of ORM restrict subtypes to derived, active subtypes. Context-dependent reference is not supported in some versions. The PSM variant adopts a different approach to generalization in which the supertype uses a disjunction of the identification schemes of its subtypes (e.g., see [ter Hofstede et al., 1993](#Ch006_211-271_B9780443237904000025.xhtml#bb1240)). Although this raises additional implementation problems when a common query is executed on overlapping subtypes, this does provide another viable approach.

For early discussion of subtyping from an ORM perspective, an informal treatment can be found in [Halpin (1995)](#Ch006_211-271_B9780443237904000025.xhtml#bb9015) and a formal treatment in [Halpin and Proper (1995b)](#Ch006_211-271_B9780443237904000025.xhtml#bb0760). An early treatment updated for ORM 2 is provided in [Halpin (2007b)](#Ch006_211-271_B9780443237904000025.xhtml#bb0660); this paper also distinguishes rigid subtypes from role subtypes, a distinction examined later in [Section 10.3](#Ch010_401-479_B9780443237904000244.xhtml#s0020). [Halpin (2009a)](#Ch006_211-271_B9780443237904000025.xhtml#bb0685) discusses some further enrichments to subtyping. [Halpin and Curland (2013)](#Ch006_211-271_B9780443237904000025.xhtml#bb0745) discuss more recent enhancements to ORM, including constraints on supertype link roles, a topic discussed in [Section 10.8](#Ch010_401-479_B9780443237904000244.xhtml#s0050).

## References

*   [Bakema G., Zwart J., van der Lek H.](#Ch006_211-271_B9780443237904000025.xhtml#B-bb0030) *Fully communication oriented NIAM.* In: Nijssen G.M., Sharp J., eds. *NIAM-ISDM 1994 Conf. Working Papers*, Albuquerque, NM; 1994:L1–35.

*   [Halpin T.](#Ch006_211-271_B9780443237904000025.xhtml#B-bb9015) Subtyping: conceptual and logical issues. In: Ross R., ed. *Database Newsletter.* Database Research Group, Inc.; 3–9. 1995;vol. 23(6) \*.

*   [Halpin, 2007](#Ch006_211-271_B9780443237904000025.xhtml#B-bb0660) Halpin, T. 2007-2009, ‘Temporal modeling: parts 1–7’, *Bus. Rules J.*, 8 and 9. Accessible at: [www.BRCommunity.com](http://www.BRCommunity.com) and Modeling Issues page of [www.orm.net](http://www.orm.net).

*   [Halpin, 2009](#Ch006_211-271_B9780443237904000025.xhtml#B-bb0685) Halpin, T. 2009-2013, ‘Ontological modeling: parts 1–15’, *Bus. Rules J.*, 10–14. Accessible at [www.BRCommunity.com](http://www.BRCommunity.com) and Modeling Issues page of [www.orm.net](http://www.orm.net).

*   [Halpin T., Curland M.](#Ch006_211-271_B9780443237904000025.xhtml#B-bb0745) Recent enhancements to ORM. In: Demey Y.T., Panetto H., eds. *On the Move to Meaningful Internet Systems 2013: OTM 2013 Workshops.* Springer LNCS 8186; 2013:467–476.

*   [Halpin T., Proper H.](#Ch006_211-271_B9780443237904000025.xhtml#B-bb0760) Subtyping and polymorphism in object-role modeling. *Data Knowl. Eng.* 1995;15:251–281 \*.

*   [ter Hofstede A., Proper H., van der Weide T.](#Ch006_211-271_B9780443237904000025.xhtml#B-bb1240) Formal definition of a conceptual language for the description and manipulation of information models. *Inform. Syst.* 1993;18(7):489–523.

---

# 7 Other Constraints and Final Checks

## Abstract

This chapter provides an overview of step 7 of ORM’s conceptual schema design procedure, then discusses frequency constraints (internal and external), ring constraints, value-comparison constraints, type cardinality constraints, textual constraints, and derivation rules. It then discusses checks on consistency, redundancy, and completeness.

### Keywords

ORM; Frequency constraint; Ring constraint; Value-comparison constraint; Type cardinality constraint; Textual constraint; Derivation rule; Consistency check; Redundancy check; Completeness check

## Chapter Outline

*   7.1 **Introduction to CSDP Step 7**
*   7.2 **Frequency Constraints**
*   7.3 **Ring Constraints**
*   7.4 **Other Constraints and Rules**
*   7.5 **Final Checks**
*   7.6 **Summary**

## 7.1 Introduction to CSDP Step 7

In previous steps of the `Conceptual Schema Design Procedure (CSDP)`, we verbalized familiar examples in terms of elementary facts, sketched the fact types on a diagram, and then added various constraints and derivation rules. Most applications include uniqueness, mandatory role, value, set-comparison, and subtyping constraints. Although less common, other kinds of constraint may also apply. Some of these have graphic notations. The rest are specified textually. Once all the constraints are specified, some final checks can be made to help ensure that our information model is consistent and free of redundancy. This concludes the basic conceptual schema design procedure.

This chapter deals with step 7 in detail. The next three sections discuss some important graphic constraints (frequency constraints, ring constraints, cardinality constraints, and value-comparison constraints). After that, we consider some constraints that must be declared textually. Finally, we examine some ways of checking that the schema is consistent and redundancy free.

## 7.2 Frequency Constraints

Let *n* be a positive integer. To indicate that each entry in a fact column must occur there *exactly n times*, the number *n* is attached by a dashed line to the role (see [Fig. 7.1](#Ch007_273-308_B978044323790400013X.xhtml#f0010)). This is an example of a **frequency constraint** (a.k.a. occurrence frequency constraint). If *n* = 1, this is equivalent to a uniqueness constraint—in this case, the usual bar notation for uniqueness should be used instead of a “1” mark.

![Fig. 7.1 A simple occurrence frequency constraint on role r.](images/B978044323790400013X/f07-01-9780443237904.jpg)

[Fig. 7.1](#Ch007_273-308_B978044323790400013X.xhtml#B-f0010) A simple occurrence frequency constraint on role *r*.

Like uniqueness constraints, frequency constraints are *local* constraints on the role(s), not global constraints on the object type. The constraint in [Fig. 7.1](#Ch007_273-308_B978044323790400013X.xhtml#f0010) means that for each state of the database, *if* an instance of *A* plays role *r*, it must do so *n* times. It does *not* mean that each instance of *A* must play that role *n* times. If the role is optional, some instances of *A* might not play the role at all.

One use of frequency constraints is to ensure that if details are recorded, they must be recorded for all instances of an enumerated type. Suppose a company stocks and sells three kinds of computer drives (C = CD drive, D = DVD drive, H = hard drive) and operates in just two cities (Sydney and Tokyo). Consider the conceptual model shown in [Fig. 7.2](#Ch007_273-308_B978044323790400013X.xhtml#f0015). The UC on the first two roles ensures that each City-Drivekind pair appears on only one row. The frequency constraint of 3 on the first role requires each city that occurs in the first column to do so three times.

![Fig. 7.2 If stock figures are recorded, they are recorded for each city and drive kind.](images/B978044323790400013X/f07-02-9780443237904.jpg)

[Fig. 7.2](#Ch007_273-308_B978044323790400013X.xhtml#B-f0015) If stock figures are recorded, they are recorded for each city and drive kind.
