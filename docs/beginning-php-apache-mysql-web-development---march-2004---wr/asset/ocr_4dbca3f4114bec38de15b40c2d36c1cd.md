# Building Databases

| id* | name | real name | power* | lair address | city | st | zip |
|---|---|---|---|---|---|---||}{
| 3 | The Dustmite | Dustin Hare | Strength | 452 Elm Street #3D | Burlington | OH | 45201 |
| 3 | The Dustmite | Dustin Hare | Dirtness | 452 Elm Street #3D | Burlington | OH | 45201 |
| 3 | The Dustmite | Dustin Hare | Laser vision | 452 Elm Street #3D | Burlington | OH | 45201 |

Looking better, but there is still repeated data in. In fact, the power column is what is causing the duplicate data. Let's separate out the power column and use a foreign key to relate to the original table. We will also further normalize the power column so that we get rid of duplicate data. This is pass number “two.” See the three tables that follow:

| id* | name | real name | lair address | city | st | zip |
|---|---|---|---|---|---||}{
| 1 | Clean Freak | John Smith | 123 Poplar Avenue | Townsburg | OH | 45293 |
| 2 | Soap Stud | Efram Jones | 123 Poplar Avenue | Townsburg | OH | 45293 |
| 3 | The Dustmite | Dustin Hare | 452 Elm Street #3D | Burlington | OH | 45201 |

| id* | power |
|---||}{
| 1 | Strength |
| 2 | X-ray vision |
| 3 | Flight |
| 4 | Speed |
| 5 | Dirtness |
| 6 | Laser vision |

| char_id* | power_id* |
|---||}{
| 1 | 1 |
| 1 | 2 |
| 1 | 3 |
| 2 | 4 |
| 3 | 1 |
| 3 | 5 |
| 3 | 6 |

As you can see, we have much less repeated data than we did before. The powers have been separated out, and a link table has been created to link each power to each appropriate character.

243