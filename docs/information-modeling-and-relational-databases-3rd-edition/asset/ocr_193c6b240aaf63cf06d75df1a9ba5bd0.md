true in practice!). Countries are identified by codes (e.g., “CU” for Cuba). Years are identified by CE (Common Era) values (e.g., World War II ended in 1945 CE). Years are time segments, so they are entities, not values.

The fact types section declares which kinds of facts are of interest. This indicates how object types participate in relationships. In this book, object type names in English are shown with their first letter in capitals, and role names start with a lowercase letter. Because database columns have attribute names such as “birthyear”, you may feel it is better to reword “Person was born in Year” as “Person has Birthyear”.


However, suppose we add the fact type “Person has Deathyear”. The formal connection between Birthyear and Deathyear is now hidden. Expressing the new fact type as “Person died in Year” reveals the semantic connections to “Person was born in Year” and makes comparisons between years of birth and death meaningful (the underlying domain is Year).


Attribute names are often used in ER, UML, and relational schemas to express facts, but this can be unnatural (compare “Person has deathyear” with “Person died in Year”), and is incomplete unless domain names such as “Year” are added.

The constraints section declares constraints on the fact types. The examples here are all static constraints (i.e., each is true for each state of the database). Reserved words in the schema language are shown in bold. Constraint C1 means that for each person referenced in the database, we know at least one country where they live. C2 says nobody can live in more than one country (at the same time). C3 says nobody was born in more than one year; note that we might not know their year of birth. Constraint C4 says that nobody is his/her own brother, and C5 says that nobody is his/her own parent (brotherhood and parenthood are irreflexive).

The derivation rules section declares a logical rule for unclehood and a function for computing the number of children of any person. The unclehood rule is specified in relational style, using fact type readings. The nrChildren rule is specified in attribute style using a role name.

At the conceptual level, each fact in the database is a simple or elementary fact. Basically, this means it can’t be split up into two or more simpler facts without loss of information. We may add or insert a fact into the database, and we may delete a fact from it. However, we may not modify or change just a part of a fact. By “fact” we mean “fact instance” not “fact type”.


The operation of adding or deleting a single fact is an elementary update or simple transaction. In our sample conceptual query language, add and delete requests start with “add:” and “del:” and queries start with “list” or end with “?”. The CIP either accepts updates or rejects them with an indication of the violation. The CIP answers legal queries and rejects illegal ones.

To explain the conceptual notions underlying database transactions, we now discuss some examples of CIP interactions. If this seems tedious, remember that we are talking about the conceptual level, not the external level where the user actually interacts with the system. At the external level, the user typically enters, deletes, or changes values in