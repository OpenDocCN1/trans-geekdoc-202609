# Movie ( movieNr, movieTitle, releaseYear, director )

# Starred ( movieNr, star )

**Movie:**

| movieNr | movieTitle | releaseYear | director |
|---|---|---|---|
| 1 | Cosmology | 2006 | Lee Lafferty |
| 2 | Kung Fu Hustle | 2004 | Stephen Chow |
| 3 | The Secret Garden | 1987 | Alan Grint |
| 4 | The Secret Garden | 1993 | Agnieszka Holland |
| 5 | Crater | 2023 | Kyle Patrick Alvarez |

**Starred:**

| movieNr | star |
|---|---|
| 2 | Stephen Chow |
| 3 | Gennie James |
| 3 | Barret Oliver |
| 4 | Kate Maberly |
| 4 | Heydon Prowse |
| 5 | Isaiah Russell-Bailey |
| 5 | Mckenna Grace |
| 5 | Billy Barratt |

FIG. 1.1 A relational database representation of Table 1.1.

In this case, we chose movieNr as the primary way to identify movies throughout the database. This is shown here by doubly underlining the movieNr column to indicate that it is the primary key of the Movie table. If a table has only one candidate key, a single underline denotes the primary key.

The constraints that each movie has only one title, release year, and director are enforced by checking that each movie number occurs only once in the Movie table. The constraints that each movie must have a title, release year, and director are enforced by checking that all movies occur in the Movie table and excluding nulls from the title, release year, and director columns. In the schema, this is captured by the dotted arrow (indicating that if a movie is listed in the Starred table, it must be listed in the Movie table) and by not marking any columns as optional. In relational database terms, this arrow depicts a foreign key constraint, where the movieNr column in the Starred table is a foreign key referencing the primary key of the Movie table. The primary key of the Starred table is the combination of its columns, indicated here by underlining.

These concepts and notations are fully explained later in the book. Even with this simple example, care is needed for database design. With complex cases, the design problem is much more challenging. The rest of this book is largely concerned with helping you to meet such challenges.

Designing databases is both a science and an art. When supported by a good method, this design process is a stimulating and intellectually satisfying activity, with tangible benefits gained from the quality of the database applications produced. The next section explains why object-role modeling (ORM) is chosen as our first modeling method. Later