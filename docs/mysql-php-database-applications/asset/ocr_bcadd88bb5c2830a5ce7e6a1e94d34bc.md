```
release_dt datetime default NULL,
notes text,
modify_dt timestamp(14) NOT NULL,
PRIMARY KEY (domain),
KEY block_by (block_by),
FOREIGN KEY ('block_by') REFERENCES 'survey.admin' ('username') ON
DELETE SET NULL
) TYPE=InnoDB;
```

```
--
-- Table structure for table 'questions'
--

CREATE TABLE questions (
question_id int(11) NOT NULL auto_increment,
question text NOT NULL,
PRIMARY KEY (question_id)
) TYPE=InnoDB;
```

```
--
-- Table structure for table 'responses'
--

CREATE TABLE responses (
user_id int(11) NOT NULL default '0',
answer_id int(11) NOT NULL default '0',
PRIMARY KEY (user_id,answer_id),
KEY answer_id (answer_id),
FOREIGN KEY ('user_id') REFERENCES 'survey.users' ('user_id') ON
DELETE CASCADE.
FOREIGN KEY ('answer_id') REFERENCES 'survey.answers'
('answer_id') ON DELETE CASCADE
) TYPE=InnoDB;
```

```
--
-- Table structure for table 'states'
--

CREATE TABLE states (
state char(2) NOT NULL default '',
statename varchar(30) NOT NULL default '',
PRIMARY KEY (state)
) TYPE=InnoDB;
```