
```
memc_set(concat('users:email:', username), email): 0
memc_set(concat('users:firstname:', username), firstname): 0
memc_set(concat('users:surname:', username), surname): 0
```

在此示例中，使用的是表名:列:唯一标识符 的键。此外，由于 uid 和 username 都是唯一的，你可以使用两者创建键，尤其是在存储时，这样就可以根据另一方查找各自。例如，如果你缓存 user:uid:captofu 的值为 1，而 user:username:1 的值为 captofu，那么就可以根据任一键进行查找。

要查看这些值是否已存储，可以在一行中全部查询出来：

```
mysql> select memc_get('users:uid:captofu') as uid,
  -> memc_get('users:username:1') as username,
  -> memc_get('users:email:captofu') as email,
  -> memc_get('users:firstname:captofu') as firstname,
  -> memc_get('users:surname:captofu') as surname;
```

| uid | username | email | firstname | surname |
|---|---|---|---|---|
| 1 | captofu | captofu@captofu.org | Patrick | Galbraith |

...这就是如何在不使用序列化的情况下进行缓存的方法。你只需要保持键的顺序！

此外，你还可以使用 SELECT™ 的威力一次性缓存多条记录！

如果记得，某些内容例如程序执行开始时可以预先缓存的地理数据如州，UserApp 示例就做了这件事。这可以用一条简单的 SQL 语句完成，如下所示：

```
mysql> select state_abbr, state_name,
  -> memc_set(concat('states:state_abbr:',state_name), state_abbr),
  -> memc_set(concat('states:state_name:', state_abbr), state_name),
  -> memc_set(concat('states:state_flower:',state_abbr), state_flower)
  -> from states\G
```

```
*************************** 1. row ***************************
                  state_abbr: AL
                  state_name: Alabama
memc_set(concat('states:state_abbr:',state_name), state_abbr): 0
memc_set(concat('states:state_name:', state_abbr), state_name): 0
memc_set(concat('states:state_flower:',state_abbr), state_flower): 0
*************************** 2. row ***************************
                  state_abbr: AK
                  state_name: Alaska
memc_set(concat('states:state_abbr:',state_name), state_abbr): 0
memc_set(concat('states:state_name:', state_abbr), state_name): 0
memc_set(concat('states:state_flower:',state_abbr), state_flower): 0
*************************** 3. row ***************************
                  state_abbr: AR
                  state_name: Arkansas
memc_set(concat('states:state_abbr:',state_name), state_abbr): 0
memc_set(concat('states:state_name:', state_abbr), state_name): 0
memc_set(concat('states:state_flower:',state_abbr), state_flower): 0
...
```
```
...
***************************** 49. row *****************************
state_abbr: WI
state_name: Wisconsin
memc_set(concat('states:state_abbr:',state_name), state_abbr): 0
memc_set(concat('states:state_name:', state_abbr), state_name): 0
memc_set(concat('states:state_flower:',state_abbr), state_flower): 0
***************************** 50. row *****************************
state_abbr: WY
state_name: Wyoming
memc_set(concat('states:state_abbr:',state_name), state_abbr): 0
memc_set(concat('states:state_name:', state_abbr), state_name): 0
memc_set(concat('states:state_flower:',state_abbr), state_flower): 0
***************************** 51. row *****************************
state_abbr: DC
state_name: District of Columbia
memc_set(concat('states:state_abbr:',state_name), state_abbr): 8
memc_set(concat('states:state_name:', state_abbr), state_name): 0
memc_set(concat('states:state_flower:',state_abbr), state_flower): 0
```

此查询使用连接来创建键，对 memc_set 中指定的列缓存所有州，就像之前的示例一样，不同之处在于结果集中有 51 条记录，所有记录现在都已缓存！

要使用对 states 表的查询结果从 memcached 中选择数据，请运行以下命令：

```
mysql> select memc_get(concat('states:state_abbr:',state_name)) as state_abbr,
memc_get(concat('states:state_name:',state_abbr)) as state_name,
memc_get(concat('states:state_flower:',state_abbr)) from states limit 20;
```

| state_abbr | state_name | memc_get(concat('states:state_flower:',state_abbr)) |
|---|---|---|
| AL | Alabama | Camellia |
| AK | Alaska | Forget Me Not |
| AR | Arkansas | Apple Blossom |
| AZ | Arizona | Saguaro Cactus Blossom |
| CA | California | California Poppy |
| CO | Colorado | Rocky Mountain Columbine |
| CT | Connecticut | Mountain Laurel |
| DE | Delaware | Peach Blossom |
| FL | Florida | Orange Blossom |
| GA | Georgia | Cherokee Rose |
| HI | Hawaii | Pua Aloalo |
| ID | Idaho | Syringa - Mock Orange |
| IA | Iowa | Wild Prairie Rose |
| IN | Indiana | Peony |
| IL | Illinois | Purple Violet |
| KS | Kansas | Sunflower |
| KY | Kentucky | Goldenrod |
| LA | Louisiana | Magnolia |
| ME | Maine | White Pine Cone and Tassel |
| MD | Maryland | Black-Eyed Susan |

太棒了！你现在可以从 memcached 中进行多键数据获取。表 *states* 本质上提供了键的列表。还请注意，任何 SQL 语句条件都可以使用，在此例中为 `LIMIT` 子句。

好吧，你以为本章就结束了，可以去睡觉了（如果你还没睡的话）？好吧，还有一个技巧要向你展示！

## Updates

考虑一个简单的表 `foo`，它只有一个列 `a`，该列为 `int`（除了用于展示此示例外并不重要）。要使用 `memc_replace()` 与 `UPDATE` 语句一起更新表和 memcached，请按以下步骤操作：

- 1. 向此表插入四个值，然后使用映射到表的键在 memcached 中设置一个值：

```
mysql> INSERT INTO foo VALUES (1), (2), (3), (4);
Query OK, 4 rows affected (0.00 sec)
Records: 4  Duplicates: 0  Warnings: 0

mysql> SELECT memc_set('foo:3', 3);
+-------------------+
| memc_set('foo:3', 3) |
+-------------------+
|                 0 |
+-------------------+
```
- 2. 获取该值以验证是否已设置：

```
mysql> SELECT memc_get('foo:3');
+-----------------+
| memc_get('foo:3') |
+-----------------+
| 3               |
+-----------------+
```
- 3. 现在更新表 *和* memcached！请注意，这里对 `memc_replace()` 的调用返回 true，因此它与 `AND` 连接一起包含在 `WHERE` 子句中。

```
mysql> UPDATE foo SET a = 33 WHERE a = 3 AND memc_replace('foo:3', 33);
Query OK, 1 row affected (0.00 sec)
Rows matched: 1  Changed: 1  Warnings: 0
```
- 4. 验证是否已替换：

```
mysql> SELECT memc_get('foo:3');
+-----------------+
| memc_get('foo:3') |
+-----------------+
| 33              |
+-----------------+
```

确实如此！

这里的技巧是，你可以在更新语句中使用连接——只要条件求值为 true。回想一下，`memc_set()` 和 `memc_replace()` 在数据存储成功时返回 false，即零。因此，为了使条件被求值为 true 从而使更新语句执行，你需要取 `memc_replace()` 的返回值之反。

## SUMMARY

在数据库层与 memcached 交互可以提供一系列好处，如果你的交互仅限于应用层，你可能无法获得这些好处。由于 MySQL 是一个关系型数据库管理系统，你可以利用数据库的关系和管理能力以及 memcached 提供的快速缓存功能，使用 MySQL 的 Memcached 函数将数据库的持久数据存储与 memcached 的缓存层连接起来。这将原本存在于 PHP 应用代码中的部分复杂性移到了更低的层次。

本章向你介绍了 MySQL 的 Memcached 函数，展示了如何从 MySQL 内部获取、安装和配置这些函数以供使用。如第 4 章中 PECL/memcached 所示，各种函数提供了 memcached 所提供的操作。接下来，你看到了使用触发器根据对数据库表执行的操作自动缓存、替换/更新和删除 memcached 中值的示例。阅读完本章后，你现在应该对如何利用这些用户定义函数提供的功能有一个概念！
