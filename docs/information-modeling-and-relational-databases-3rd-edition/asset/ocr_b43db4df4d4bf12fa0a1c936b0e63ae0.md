The **not between** formulation is easier to read. For example, the following query returns just the tuple (‘Terry’, 1946).

```
select firstname, birthyr from Person
where birthyr not between 1950 and 1974
```

In the pure relational model, column values are atomic. However, SQL provides a number of ways of accessing substrings within character string values. In particular, the **like** operator may be used for *pattern matching* with character strings. The general form of the condition in SQL-89 may be set out in BNF thus:

```
char-col [not] like quoted-string [escape quoted-char]
```

Here, char-col is the name of a column based on a character string data type. The quoted string is a character string, surrounded by single quotes, which may contain *wildcard characters*. You may be familiar with the use of wildcards for matching filenames at the operating system level (e.g., “*” in Microsoft Windows).

In the absence of an escape clause, SQL gives the percentage character “%” and the underscore character “_” the following special meanings if included in a quoted string operated on by **like**:

+   - % means zero or more characters
+   - _ means any single character

The “%” is generally more useful, but “_” is needed if the character’s position in the string is important. Fig. 12.4.7 provides a few examples based on Table 12.9. The **like** operator has priority over logical operators, so “x not like s” means “not (x like s)”.

```
select distinct starsign from Person
where starsign like 'A%'
```

| starsign |
|----------|
| Aquarius |
| Aries |

```
select distinct starsign from Person
where starsign like '%a%'
```

| starsign |
|----------|
| Aquarius |
| Taurus |

```
select distinct starsign from Person
where starsign like '_a%'
```

| starsign |
|----------|
| Taurus |

```
select firstname from Person
where name not like '%e%'
```

| firstname |
|-----------|
| Bob |
| Norma |