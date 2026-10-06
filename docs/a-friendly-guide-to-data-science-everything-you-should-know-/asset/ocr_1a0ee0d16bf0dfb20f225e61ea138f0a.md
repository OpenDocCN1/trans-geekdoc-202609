# CHAPTER 12 TRYING NOT TO MAKE A MESS: DATA COLLECTION AND STORAGE

The diagram shows four tables. The STUDENT_MAJOR table stores the student name along with their major, advisor, and school. Three other tables hold only an ID and a value for major, advisor, and school. The lines show relationships between the tables. STUDENT_MAJOR stores a major ID that is linked to the MAJOR table and does the same thing for advisor and school.

This diagram is over-simplified as normally more information is conveyed, especially about the relationships between fields. Also, note that this kind of diagram is also called an entity-relationship (ER) diagram in the relational database world.

From a historical perspective, the majority of database systems used the relational organizing paradigm and a language called SQL to interact with it. More recently, non-relational databases that use a paradigm called NoSQL have become more available because they are well-suited to certain types of data. As we saw, Flutter used a NoSQL database system in the example above. However, despite the availability of NoSQL, most data still lives in relational database systems. I'll talk about both types below.

Data scientists who work with data in databases primarily query the database by writing code that will bring back specific data from its tables, but they also create, modify, and manage tables. Every DBMS has some mechanism for interacting with the database in some way.

# Relational Database Systems

Relational database management systems (usually abbreviated RDBMSs) are well-suited to structured data and rely on the relational data model (see the sidebar for more info). These and other database systems are ubiquitous in almost all organizations, as is SQL, the language that lets people interact with the data.