
NORMA Professional (NORMA Pro) has additional features such as multipage relational schemas and formal support for derivation rules. For details on how to get a licence for the professional version of NORMA, contact Matt Curland at [mcurland@live.com](mailto:mcurland@live.com).

Other tools supporting different flavors of fact-oriented modeling include CaseTalk, CogNIAM tools, ActiveFacts, and Boston. Links to these tools may be found in the Useful Websites section that is included at the back of this book.

## Acknowledgments

We greatly appreciate the editorial assistance of Chris Katsaropolous and Palak Gupta at Elsevier.

Some of this book’s content is based on articles written for *The Business Rules Journal*, the *Journal of Conceptual Modeling*, and material from editions of the earlier book *Conceptual Schema and Relational Database Design*, previously published by Prentice Hall Australia and WytLytPub. The first edition of that book was coauthored by Dr. Sjir Nijssen, who wrote the final four chapters (since replaced).

The ORM approach discussed in this book is based on our revisions and extensions to the NIAM method, which was largely developed in its original form by Dr. Eckhard Falkenberg, Nijssen, and Prof. Robert Meersman, with other contributions from several researchers. Some of the work discussed in this book was developed jointly with current or former colleagues, including Dr. Anthony Bloesch, Dr. Linda Bird, Dr. Peter Ritson, Dr. Erik Proper, Dr. Andy Carver, and Dr. Herman Balsters. It has been a pleasure working with these colleagues as well as with the hundreds of information modeling students and practitioners. We also gratefully acknowledge permission by The University of Queensland and Neumont University to include a small selection of our past assessment questions within the exercises.

Finally, we thank our wives, Norma and Gwen, for being so understanding and supportive while we were busily occupied in the writing task.

# 1 Introduction

## Abstract

This book provides a modern introduction to database systems, with the emphasis on information modeling. At its heart is a very high-level semantic approach that is fact-oriented in nature. This chapter provides an overview of information modeling and modeling approaches, discussing some historical background and the relevant skills required.

### Keywords

Information; Modeling approaches; Fact-orientation; ORM; ER; UML

## Chapter Outline

*   1.1 **Information Modeling**
*   1.2 **Information Modeling Approaches**
*   1.3 **Historical Background**
*   1.4 **The Relevant Skills**
*   1.5 **Summary**

## 1.1 Information Modeling

Information adds meaning to data. It’s an unfortunate fact of life that names and numbers are sometimes misinterpreted. This can prove costly, as experienced by senior citizens in the United States who had their Social Security benefits cut off when government agencies incorrectly pronounced them dead because of misreading “DOD” on hospital forms as “date of death” rather than the intended “date of discharge”.

In 1999, NASA’s $125 million Mars Climate Orbiter burned up in the Martian atmosphere. Apparently, errors in its course settings arose from a failure to make a simple unit conversion. One team working in US customary units sent its data to a second team working in metric, but no conversion was made. If a man weighs 180, does he need to go on a drastic diet? Not if his mass is 180 lb., but yes if it’s 180 kg. *Data* by itself is not enough. What we really need is *information*, the meaning or *semantics* of the data. Because computers lack common sense, we need to pay special attention to semantics when we use computers to model some aspect of reality.

This book provides a modern introduction to database systems, with the emphasis on information modeling. At its heart is a very high-level semantic approach that is *fact-oriented* in nature. If you model databases using either traditional or object-oriented approaches, you’ll find that fact orientation lifts your thinking to a higher level, illuminating your current way of doing things. Even if you’re a programmer rather than a database modeler, this semantic approach provides a natural and powerful way to design your data structures.

A **database** is basically a collection of related data (e.g., a company’s personnel records). When interpreted by humans, a database may be viewed as a set of related *facts*—an *information base*. In the context of our semantic approach, we’ll often use the popular term “database” instead of the more technical “information base”. Discovering the facts that underlie a business domain, and the rules that apply to the facts, is interesting and revealing. The quality of the database *design* used to capture these facts and rules is critical. Just as a house built from a good architectural plan is more likely to be safe and convenient for living, a well-designed database simplifies the task of ensuring that its facts are correct and easy to access. Let’s review some basic ideas about database systems, and then see how things can go wrong if they are poorly designed.

Each database models a *business domain*—we use this term to describe any area of interest, typically a part of the real world. Consider a library database. As changes occur in the library (e.g., a book is borrowed), the database is updated to reflect these changes. This task could be performed manually using a card catalog, or be automated with an online catalog, or both. Our focus is on automated databases. Sometimes these are implemented by means of special-purpose computer programs, coded in a general-purpose programming language (e.g., C# or Java). More often, database applications are developed using a **database management system** (DBMS). This is a software system for maintaining databases and answering queries about them (e.g., DB2, Oracle, SQL Server). The same DBMS can handle many different databases.

Typical applications use a database to house the persistent data, an in-memory object model to hold transient data, and a friendly user interface for users to enter and access data. All these structures deal with information and are best derived from an information model that clearly reveals the underlying semantics of the domain. Some tools can use information models to automatically generate not just databases, but also other kinds of models (object, logical, etc.) and user interfaces.

If an application requires maintenance and retrieval of lots of data, a DBMS offers many advantages over manual record keeping. Data may be conveniently captured via electronic interfaces (e.g., screen forms), then quickly processed and stored compactly on disk. Many data errors can be detected automatically, and access rights to data can be enforced by the system. People can spend more time on creative design rather than on routine tasks more suited to computers. Finally, developing and documenting application software can be facilitated by the use of *computer-assisted software engineering* (CASE) tool support.

In terms of the dominant employment group, the Agricultural Age was supplanted late in the 19th century by the Industrial Age, which has now been replaced by the Information Age. With the ongoing information explosion and mechanization of industry, the proportion of information workers is steadily rising. Most businesses achieve significant productivity gains by exploiting information technology. Imagine how long a newspaper firm would last if it returned to the methods used before word processing and computerized typesetting. Apart from its enabling employment opportunities, the ability to interact efficiently with information systems empowers us to exploit their information content.
