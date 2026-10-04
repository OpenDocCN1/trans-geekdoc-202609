

## 构建数据库

| id* | name | real name | power* | lair address | city | st | zip |
|---|---|---|---|---|---|---|---|
| 3 | The Dustmite | Dustin Hare | Strength | 452 Elm Street #3D | Burlington | OH | 45201 |
| 3 | The Dustmite | Dustin Hare | Dirtness | 452 Elm Street #3D | Burlington | OH | 45201 |
| 3 | The Dustmite | Dustin Hare | Laser vision | 452 Elm Street #3D | Burlington | OH | 45201 |

看起来好多了，但其中仍然存在重复数据。事实上，power 列是导致数据重复的原因。让我们将 power 列分离出来，并使用外键与原始表建立联系。我们还对 power 列进行了进一步的归一化处理，以消除重复数据。这是“第二次”尝试。请看下面的三个表：

| id* | name | real name | lair address | city | st | zip |
|---|---|---|---|---|---|---|
| 1 | Clean Freak | John Smith | 123 Poplar Avenue | Townsburg | OH | 45293 |
| 2 | Soap Stud | Efram Jones | 123 Poplar Avenue | Townsburg | OH | 45293 |
| 3 | The Dustmite | Dustin Hare | 452 Elm Street #3D | Burlington | OH | 45201 |

| id* | power |
|---|---|
| 1 | Strength |
| 2 | X-ray vision |
| 3 | Flight |
| 4 | Speed |
| 5 | Dirtness |
| 6 | Laser vision |

| char_id* | power_id* |
|---|---|
| 1 | 1 |
| 1 | 2 |
| 1 | 3 |
| 2 | 4 |
| 3 | 1 |
| 3 | 5 |
| 3 | 6 |

如你所见，我们的重复数据比之前少了许多。能力已经被分离出来，并创建了一个链接表来将每个能力连接到相应的角色上。

## 第 9 章

这看起来可能有点吹毛求疵，但在角色表中你仍然有一些可以处理的重复数据。多个角色可能处于同一个巢穴，例如 Clean Freak 和 Soap Stud 就是如此。让我们创建一个表，并通过键将其与角色关联起来。我们还在角色表中添加了一个新列用于对齐（阵营）。请看下面的两个表。

| id* | lair_id | name | real name | align |
|---|---|---|---|---|---|
| 1 | 1 | Clean Freak | John Smith | Good |
| 2 | 1 | Soap Stud | Efram Jones | Good |
| 3 | 2 | The Dustmite | Dustin Hare | Evil |

| id* | lair address | city | st | zip |
|---|---|---|---|---|
| 1 | 123 Poplar Avenue | Tompkins | OH | 45293 |
| 2 | 452 Elm Street #3D | Burgtown | OH | 45201 |

我们可能会添加阵营列来说明一个观点。如果你正处于归一化过程中，发现有其他其他需要添加的数据，这并不困难。如果你需要，完全可以添加一个全新的表。这就是关系型设计的精妙之处。

城市（City）和州（State）字段不仅是重复的，而且与邮政编码（其本身就代表了城市/州）。城市和州并不直接于巢穴（因为同一个城市可能存在其他巢穴）。由于这些原因，邮政编码是数字，是城市/州的直接表示，我们将邮政编码设置为主键。这是下面三个表中的“第三次”尝试。

| id* | lair_id | name | real name | align |
|---|---|---|---|---|---|
| 1 | 1 | Clean Freak | John Smith | Good |
| 2 | 1 | Soap Stud | Efram Jones | Good |
| 3 | 2 | The Dustmite | Dustin Hare | Evil |

| id* | zip_id | lair address |
|---|---|---|---|
| 1 | 45293 | 123 Poplar Avenue |
| 2 | 45201 | 452 Elm Street #3D |

| id* | city | st |
|---|---|---|
| 45293 | Tompkins | OH |
| 45201 | Burgtown | OH |

## 构建数据库

你可能已经注意到，我们在角色和他们的能力之间建立了多对多（M:N）关系（一个角色可以有多种能力，而许多角色可能拥有相同的能力）。有两个带有主键的表，它们之间的链接表包含外键，每个表对应一个外键。外键的组合作为 char_power 表的主键。这实现了 M:N 关系。

为了好玩，让我们添加一个包含超级英雄和反派的小表，反之亦然。这是另一个 M:N 关系，因为任何超级英雄都可以有多个反派敌人，而任何反派都可以有多个超级英雄。

