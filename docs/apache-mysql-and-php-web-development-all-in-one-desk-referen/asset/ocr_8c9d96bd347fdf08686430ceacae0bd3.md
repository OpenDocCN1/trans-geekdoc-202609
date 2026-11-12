```
email varchar(50) unique,
password char(34),
lastaccess date,
signup date,
themeID integer,
key(email),
primary key(loginID)
);
```

```
create table usertheme (
    themeID integer NOT NULL,
    name varchar(15),
    backgroundcolor char(6),
    primary key(themeID)
);
```

```
insert into usertheme
values (1, 'pink', 'FFCCFF');
insert into usertheme
values (2, 'blue', 'CCFFFF');
insert into usertheme
values (3, 'yellow', 'FFFFCC');
insert into usertheme
values (4, 'salmon', 'FFCCCC');
insert into usertheme
values (5, 'green', 'CCFFCC');
insert into usertheme
values (6,'purple', 'CCCCFF');
```

The login table consists of a unique loginID, an e-mail address, a password (which will be encrypted), the signup date, the last access date, and the user-selected theme.

For the table creation, I chose to include a loginID, even though I don't use it much in the examples in this chapter. As your system grows, you may want to allow users to know their unique IDs for quick lookups and such.

After the table creation, Listing 7-1 includes six entries for the usertheme table. In this simple example, the themes consist of six possible colors, and the theme name is the name of the color. You can put other information in this file, such as the filename of a graphic to display at the top of each page or the name of graphics set for use in navigating the site. Then each user sees a color and graphics set depending on the chosen theme.