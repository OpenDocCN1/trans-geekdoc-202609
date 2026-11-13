# Listing 3-2: A create Statement for the users Table

```
CREATE TABLE users (
userid int(10) unsigned NOT NULL auto_increment,
fname varchar(25) NOT NULL,
lname varchar(25) NOT NULL,
addr varchar(255) NOT NULL,
addr2 varchar(255),
city varchar(40) NOT NULL,
state char(2) NOT NULL,
zip varchar(5),
lastchanged timestamp(14),
PRIMARY KEY (userid)
);
```

To get things started, we loaded up the database with a few rows of information. The insert statements that load this data are shown in Listing 3-3.

# Listing 3-3: insert Statements for the users Table

```
INSERT INTO users (userid, fname, lname, addr, addr2, city, state,
zip, lastchanged) VALUES (1,'Jason','Greenspan','555 5th
St','apt 204','San Francisco','CA','94118',20020626134625);
INSERT INTO users (userid, fname, lname, addr, addr2, city, state,
zip, lastchanged) VALUES (2,'Brad','Bulger','666 6th St','apt
17','San Francisco','CA','94116',20020626134704);
INSERT INTO users (userid, fname, lname, addr, addr2, city, state,
zip, lastchanged) VALUES (3,'John','Doe','279 66th St',NULL,'New
York','NY','11100',20020627120644);
INSERT INTO users (userid, fname, lname, addr, addr2, city, state,
zip, lastchanged) VALUES (4,'Jane','Doe','987 67th
St',NULL,'Windsor','MA','14102',20020627120644);
INSERT INTO users (userid, fname, lname, addr, addr2, city, state,
zip, lastchanged) VALUES (5,'Jean','Banks','4 Elm
St','','Eugene','OR','98712',20020627120644);
INSERT INTO users (userid, fname, lname, addr, addr2, city, state,
zip, lastchanged) VALUES (6,'Donny','Alphonse','25 14th
St',NULL,'New York','NY','11104',20020627120644);
INSERT INTO users (userid, fname, lname, addr, addr2, city, state,
zip, lastchanged) VALUES (7,'Meghan','Garcix','44 Maple
Dr',NULL,'Nashville','TN','37114',20020627120644);
INSERT INTO users (userid, fname, lname, addr, addr2, city, state,
zip, lastchanged) VALUES (8,'Kenny','Clark','General
Delivery',NULL,'Waseghan','VT','10048',20020627120644);
INSERT INTO users (userid, fname, lname, addr, addr2, city, state,
zip, lastchanged) VALUES (9,'Danny','Briggs','8 Palm Way','ste
222','Miami','FL',NULL,20020627120644);
```