```
$aDBPrettyNames ['mssql'] = 'Microsoft SQL Server';
$aDSNValues ['mssql'] = 'mssql://user:pass@dbserver/book_test';
$aCreateTableCmds['mssql'] = array( 'CREATE TABLE [dbo].[Employees] ( [id] [int] NOT NULL , [last_name] [char] (50) COLLATE SQL_Latin1_General_CP1_CI_AS NULL , [first_name] [char] (50) COLLATE SQL_Latin1_General_CP1_CI_AS NULL , [phone_ext] [char] (5) COLLATE SQL_Latin1_General_CP1_CI_AS NULL , [mgr_id] [int] NULL , [dept_id] [int] NULL ) ON [PRIMARY]', 'ALTER TABLE [dbo].[Employees] WITH NOCHECK ADD CONSTRAINT [PK_Employees] PRIMARY KEY CLUSTERED ( [id] ) ON [PRIMARY] ');

$aDBPrettyNames ['mysql'] = 'MySQL';
$aDSNValues ['mysql'] = 'mysql://bt_user:bt_pass@207.44.182.3/book_test';
$aCreateTableCmds['mysql'][] = "CREATE TABLE Employees ( id int(11) NOT NULL default '0', last_name varchar(50) NOT NULL default '', first_name varchar(50) NOT NULL default '', phone_ext varchar(5) NOT NULL default '', mgr_id int(11) NOT NULL default '0', dept_id int(11) NOT NULL default '0', PRIMARY KEY (id), KEY mgr_id (mgr_id), KEY dept_id (dept_id) ) TYPE=InnoDB";

$aDBPrettyNames ['odbc'] = 'ODBC with Access DB';
$aDSNValues ['odbc'] = 'odbc:///book_test';
$aCreateTableCmds['odbc'][] = 'CREATE TABLE [Employees] ( [id] integer NOT NULL , [last_name] char(50) NULL, [first_name] char(50) NULL, [phone_ext] char(5) NULL, [mgr_id] integer NULL , [dept_id] integer NULL )';
$aCreateTableCmds['odbc'][] = 'ALTER TABLE [Employees] ADD CONSTRAINT [PK_Employees] PRIMARY KEY ( [id] )';

$aDBPrettyNames ['sqlite'] = 'SQLite';
$aDSNValues ['sqlite'] = 'sqlite:///c:/temp/PEAR/sqlite_employees.dat';
$aCreateTableCmds['sqlite'][] = 'CREATE TABLE Employees ( id [integer] NOT NULL PRIMARY KEY, last_name [char(50)], first_name [char(50)], phone_ext [char(5)], mgr_id [integer], dept_id [integer] )';

$aDBPrettyNames ['ibase'] = 'Borland Interbase';
$aDSNValues ['ibase'] = 'ibase://sysdba:masterkey@localhost/c:/temp/PEAR/book_test.gdb';
$aCreateTableCmds['ibase'][] = 'CREATE TABLE Employees ( id integer NOT NULL PRIMARY KEY, last_name char(50), first_name char(50), phone_ext char(5), mgr_id integer, dept_id integer )';

$aDBPrettyNames ['msql'] = 'Mini SQL';
```