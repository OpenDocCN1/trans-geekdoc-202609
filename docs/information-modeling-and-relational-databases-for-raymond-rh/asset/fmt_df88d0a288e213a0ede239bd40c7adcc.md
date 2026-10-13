
# Conceptual Schemas and Relational Mapping

Conceptual schemas are normally implemented by mapping them to a logical schema (e.g., relational), refining this, and then generating internal and external schemas (including access rights). Updates and queries may then be performed on the databases and schema(s).

A *relational (database) schema* is a set of table definitions (stored base tables or derived views), constraints, and derivation rules. A *table scheme* is a named set of *attributes* (columns) that draws values from *domains*. Each column, or column set, spanned by a minimal uniqueness constraint is a *candidate key*. Keys are underlined. Each table row is identified by its *primary key* (doubly underlined if another key exists). The *entity integrity* rule requires primary keys to have no nulls. Optional columns allow nulls and are enclosed in square brackets. For example: `Employee( empNr, empName, address, gender, [phone] )`.

Mandatory roles map to nonoptional columns, with subset constraints running from any other tables that contain facts about that object type. A *referential integrity constraint* is a subset constraint from a foreign key to some primary key. Subset constraints between tables appear as dotted arrows. Other constraint notations are used.

The relational mapping procedure (`Rmap`) groups each fact type into a single table, using two basic ideas: each fact type with a compound uniqueness constraint (e.g., an *m:n* association or a ternary association) is mapped to a separate table; fact types with functional roles attached to the same object type are grouped into the same table, keyed on the object type's identifier.

The *basic Rmap procedure* may be summarized as follows. Absorb subtypes into their top supertype. Mentally erase all explicit preferred identification schemes, treating compositely identified object types as "black boxes". Map each fact type with a compound UC to a separate table. Group fact types with functional fact roles attached to the same object type into the same table, keyed on the object type's identifier. Map 1:1 cases to a single table, generally favoring fewer nulls. Map each independent object type with no functional fact roles to a separate table. Unpack each "black box column" into its component attributes. Map all other constraints and derivation rules. Subtype constraints on functional roles map to qualified optional columns, and those on nonfunctional roles map to qualified subset constraints.

If the total population of an object type is included in one table, this is called a total table for the object type. See the *total table procedure* for more details.

Advanced mapping aspects in the *Rmap step 0 procedure* may be summarized as follows. Transform opposite unaries and then map unaries according to their open/closed world semantics. Mentally erase all reference (preferred identification) predicates. Treat compositely identified object types as "black boxes". Indicate any absorption overrides (e.g., separation or partition) for subtypes. Identify any derived fact types that must be stored. Indicate mapping choices for symmetric 1:1 cases. Consider replacing any disjunctive reference schemes by using an artificial or concatenated identifier or mandatory defaults. Indicate mapping choice where required for any objectified associations with no spanning uniqueness constraint.

## Chapter Notes

Many database textbooks discuss mapping ER schemas to relational schemas (e.g., [Batini et al., 1992](#Ch011_481-537_B9780443237904000141.xhtml#bb0080)) and mapping UML class diagrams to relational schemas (e.g., [Blaha and Premerlani, 1998](#Ch011_481-537_B9780443237904000141.xhtml#bb0105)). The mapping extensions to the old ONF algorithm to develop the original version of Rmap were developed jointly by Peter Ritson and Terry Halpin. The version of Rmap discussed in this chapter includes several revisions to cater for new features in ORM 2, such as further options for objectification and open/closed world semantics.

## References[^(13)](#fn13)

*   [Batini C., Ceri S., Navathe S.](#Ch011_481-537_B9780443237904000141.xhtml#B-bb0080) *Conceptual Database Design: An Entity-Relationship Approach.* Redwood City, CA: Benjamin Cummings; 1992.
*   [Blaha M., Premerlani W.](#Ch011_481-537_B9780443237904000141.xhtml#B-bb0105) *Object-Oriented Modeling and Design for Database Applications.* New Jersey: Prentice Hall; 1998.

---

# 12 Relational Languages

## Abstract

This chapter provides a detailed discussion of relational algebra and its operations (union, intersection, difference, Cartesian product, selection, projection, join, division, and renaming). It then discusses relational database systems, and how to specify queries and updates in SQL.

### Keywords

Relational algebra; Relational database; SQL; Queries; Updates

## Chapter Outline

*   12.1 **SQL: Relational Algebra**
*   12.2 **Relational Database Systems**
*   12.3 **SQL: Historical and Structural Overview**
*   12.4 **SQL: Identifiers and Data Types**
*   12.5 **SQL: Choosing Columns, Rows, and Order**
*   12.6 **SQL: Joins**
*   12.7 **SQL: in, between, like, and is null Operators**
*   12.8 **SQL: Union and Simple Subqueries**
*   12.9 **SQL: Scalar Operators and Bag Functions**
*   12.10 **SQL: Grouping**
*   12.11 **SQL: Correlated and Existential Subqueries**
*   12.12 **SQL: Recursive Queries**
*   12.13 **SQL: Updating Table Populations**
*   12.14 **Summary**

## 12.1 SQL: Relational Algebra

Previous chapters discussed how to design a conceptual schema and map it to a relational schema. This chapter discusses how to implement a relational schema in a relational database management system (`DBMS`) and then populate its tables with data. To retrieve information from the resulting database, we need to issue queries. In practice, the most popular query languages are `SQL` (popularly but incorrectly called "structured query language") and `QBE` (query by example). Both these languages are based, at least partly, on a formal query language known as *relational algebra*, which is discussed in this section. Studying this algebra first clarifies the basic query operations without getting distracted by the specific syntax of commercial query languages.

With relational algebra under our belt, we can define what is really meant by the term "relational database system". The following sections then cover SQL in some depth, starting with the basics and moving on through intermediate to advanced concepts. Although our focus is on the SQL standard(s), some additional details will be included about commercial dialects of SQL. We begin with relational algebra.

In the relational model of data, all facts are stored in *tables* (or *relations*). New tables may be formed from existing tables by applying relational algebra operations. The tables resulting from these operations may be named and stored, using relational assignment. The original relational algebra defined by Codd contained eight *relational operators*: four based on traditional set operations (*union*, *intersection*, *difference*, and *Cartesian product*) and four special operations (*selection*, *projection*, *join*, and *division*). Relational algebra now includes a *rename* operator to define aliases for the table scheme of a query result. Each of the nine relational operators is a table-forming operator on tables. For example, the union of two tables is itself a table.
