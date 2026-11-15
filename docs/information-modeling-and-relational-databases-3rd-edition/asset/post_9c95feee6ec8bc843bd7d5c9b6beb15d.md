
constraint to be awkward to think about. This constraint says that on each row of the Academic table, there is exactly one nonnull value in the last three columns.

The column “dept_where_lec” means the department (if any) where that academic is a lecturer, “dept_where_sen_lec” means the department (if any) where that academic is a senior lecturer, and “dept_where_prof” means the department (if any) where that academic is a professor. Here is one sample row from each table (“?” denotes a null):

```
Subject: ("CS115", 8)
Teaches: (30572, “CS115”)
Academic: (30572, ?, “Computer Science”, ?)
AwardedBy: (30572, “PhD”, “UQ”)
AwardedIn: (30572, “PhD”, 1990)
```

```
Subject   ( subjectCode, credit )
           ^
Teaches   ( empNr, subjectCode )
           ≤ 2
Academic  ( empNr, [dept_where_lec]^1, [dept_where_sen_lec]^1, [dept_where_prof]^1 )
           ^
AwardedBy ( empNr, degree, university )
           ^
AwardedIn ( empNr, degree, yr )

1 means non-null in {dept_where_lec, dept_where_sen_lec, dept_where_prof}
```

Reengineer the model to improve its performance and clarity, using the following steps.

- (a) Reverse engineer the relational schema to an ORM schema. Include all constraints.
- (b) Optimize the conceptual schema to prepare it for relational mapping.
- (c) Forward engineer your new conceptual schema by mapping it to a relational schema. Include all constraints.
- (d) Populate the new relational schema with the sample data provided.

## 14.9 Data Migration and Query Transformation

Data migration, the fourth phase of reengineering, can sometimes be challenging. When the original database is populated with massive amounts of data, it is typically impractical to convert and reenter the data manually into the new database schema. While most DBMSs provide tools to assist with data migration, these tools usually handle only simple data transformations, so you need to write your own transforms for more complex cases. Such data transformations are normally written in SQL, although XSLT could be used if the data is available in XML form.

Once the data migration is completed, any stored queries on the old database need to be recoded to perform equivalent queries on the new databases. This section illustrates the tasks of data migration and query transformation using a small reengineering example. The exercise at the end of this section provides a larger example for you to try out yourself.

Fig. 14.82(a) shows a fragment of a relational schema about martial arts clubs. In martial arts (e.g., judo and karatedo), there are exactly two kinds of rank: dan (black belt grade) and kyu (below black belt). The ClubNrRankedPlayers table stores facts about how many dan and kyu graded players belong to certain clubs. For example, the tuples (“KDK”, dan, 300) and (“KDK”, kyu, 250) would mean that the club with the clubcode “KDK” has 300 dan grades and 250 kyu grades.

![](img/1344db3eba3d550e6edb009556fcd95c_790_0.png)

### FIG. 14.82 (a) Original relational schema and (b) reengineered relational schema.

Suppose that the original database has a stored query to list the code and name of each club, together with the number of black belt players (if known). This query may be formulated in SQL as query Q1.

```
Q1: select Club.clubCode, clubName, nrPlayers as nrDanGrades
from Club left outer join ClubNrRankedPlayers
on Club.clubCode = ClubNrRankedPlayers.clubCode
and ClubNrRankedPlayers.rankType = 'dan'
```

Now suppose that in reengineering the original database, these two table schemes are replaced by the equivalent single table scheme in Fig. 14.82(b). This optimization is based on the predicate specialization transform discussed in Section 14.2.

Suppose the original schema is called MartialArts1 and the new schema is called MartialArts2. We may now migrate the data from the original two tables into the new table using the following SQL command.

```
insert into MartialArts2.Club
select Club.clubCode, clubName, cityname, ClubDans.nrPlayers, ClubKyos.nrPlayers
from MartialArts1.Club left outer join MartialArts1.ClubNrRankedPlayers as ClubDans
on Club.clubCode = ClubDans.clubCode
and ClubDans.rankType = 'dan'
left outer join MartialArts1.ClubNrRankedPlayers as ClubKyos
on Club.clubCode = ClubKyos.clubCode
and ClubKyos.rankType = 'kyu'
```

The original query Q1 may now be reformulated to work with the new database, as shown in Q2.

```
Q2: select clubCode, clubName, nrDanGrades
from Club
```

Even with this simple example, you can see that writing the code to do the data migration can require a little thought. In practice, it can get much more difficult than this. The following exercise, which covers most aspects of the data reengineering process, includes several more challenging data migration tasks. The solutions to this exercise (and all other odd-numbered questions) are available online.

## Exercise 14.9

- 1. The SQL Server diagram shown depicts the main aspects of a relational database schema CarSale1 used by a car retailer to record details about cars and sales. The developers do not fully understand the schema, and suspect that some aspects of the schema are incomplete or even unsafe. Also, the database has performance problems mainly because of the number of table joins required for common queries.

![](img/1344db3eba3d550e6edb009556fcd95c_791_0.png)

The tables were originally thrown together with little design discipline by someone who has now left the application team. You are asked to provide a new relational design that is both normalized and efficient.

Although the schema includes some primary key declarations, it is missing several constraints that need to be enforced. Moreover, it includes some nonimplied FDs due to denormalization. Some missing constraints are “obvious” and some others may be inferred from the incomplete description that follows. In addition, some rows of data are provided for each table so you can apply ORM CSDP step 1. The sample data are not fully significant (i.e., not all constraints may be deduced from them).

For this UoD, each car is identified by a vehicle identification number (vin) and has exactly one color (identified by a code). Car models are back wheel drive (bwd), front wheel drive (fwd), four-wheel drive (4wd), or all-wheel drive (awd). Each car color has a unique name, and optionally its RGB (Red, Green, Blue) composition may be recorded. At most two phone numbers are recorded for each customer.

There is no restriction on what criteria may be used by magazines to rate car models, but each rating must be in the range 1...7 (the higher the rating the better). Whether a customer is an employee of the car retailer is not of interest. An SQL Server database with sample data for this question is available online.

- (a) Which table schemes in the original schema are not fully normalized? Explain briefly what design flaws cause them to be denormalized.
- (b) Reverse engineer the relational schema to an ORM conceptual schema. Do *not* concern yourself with efficiency or optimization at this stage. Your ORM schema, while being redundancy free with all fact types elementary, should in other respects directly reflect the design decisions made in the original relational schema. *Include all constraints* (graphical or textual) that apply to the application domain, including those constraints omitted from the original relational schema.

Formulate the following queries in SQL:

- (c) For each car model that is reviewed, list its id and the magazines in which it is reviewed, as well as its economy rating(s) (if known).
- (d) For each employee who has made a car sale and is a novice or an expert in Spanish, list their employee number, name, and gender as well as their sales total (i.e., the total amount they have earned for the company from car sales).
- (e) For each car whose color has an equal measure of red and green, list its vehicle identification number, color code, car model id, and drive kind.

Criterion is now constrained to the values “Safety”, “Economy”, “Performance”, and “Style”.

- (f) Transform the ORM schema to an “optimized conceptual schema” that minimizes the number of tables obtained if the Rmap procedure is applied.
- (g) Forward engineer your optimized ORM schema to a new relational schema CarSale2. Ensure that all tables and columns are named well. Annotate the relational schema diagram to display all constraints, using footnote numbers and text boxes where needed. Value constraints should appear in braces after relevant column name(s).
