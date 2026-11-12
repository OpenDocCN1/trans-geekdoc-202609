The examples we'll discuss here will use the following database tables:

+   A table for users:

```
CREATE TABLE user (
  user_id   INT(11)     NOT NULL AUTO_INCREMENT,
  login     VARCHAR(50) NOT NULL DEFAULT '',
  password  VARCHAR(50) NOT NULL DEFAULT '',
  email     VARCHAR(50) DEFAULT NULL,
  firstName VARCHAR(50) DEFAULT NULL,
  lastName  VARCHAR(50) DEFAULT NULL,
  signature TEXT        NOT NULL,
  PRIMARY KEY (user_id),
  UNIQUE KEY user_login (login)
)
```

+   A table to store images:

```
CREATE TABLE image (
  image_id  INT(11)      NOT NULL AUTO_INCREMENT,
  name      VARCHAR(100) NOT NULL DEFAULT '',
  size      INT(11)      NOT NULL DEFAULT '0',
  type      VARCHAR(50)  NOT NULL DEFAULT '',
  contents  BLOB         NOT NULL,
  PRIMARY KEY (image_id)
)
```

+   And last of all, a table to store a site menu:

```
CREATE TABLE menu (
  menu_id     INT(11)      NOT NULL auto_increment,
  parent_id   INT(11)      NOT NULL default '0',
  name        VARCHAR(255) NOT NULL default '',
  description TEXT         NOT NULL,
  location    VARCHAR(255) NOT NULL default '',
  PRIMARY KEY (menu_id),
  UNIQUE KEY location (location)
)
```

You'll find the MySQL queries that create these tables and sample data included
in the code archive in the sql/ directory.