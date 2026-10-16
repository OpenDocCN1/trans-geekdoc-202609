The database design is as follows:

**Database name:** MemberDirectory

**Table 3-5 Database Table 1: Member**

| Variable Name | Type | Description |
|---|---|---|
| loginName | VARCHAR(20) | User-specified login name (primary key) |
| password | CHAR(255) | User-specified password |
| createDate | DATE | Date member registered and created login account |
| lastName | VARCHAR(50) | Member's last name |
| firstName | VARCHAR(40) | Member's first name |
| street | VARCHAR(50) | Member's street address |
| city | VARCHAR(50) | Member's city |
| state | CHAR(2) | Member's state |
| zip | CHAR(10) | Member's ZIP code |
| email | VARCHAR(50) | Member's e-mail address |
| phone | CHAR(15) | Member's phone number |
| fax | CHAR(15) | Member's fax number |

**Table 3-6 Database Table 2: Login**

| Variable Name | Type | Description |
|---|---|---|
| loginName | CHAR(20) | Login name specified by user (primary key 1) |
| loginTime | DATETIME | Date and time of login (primary key 2) |

# Developing the Application

After you develop a plan listing the tasks that your application is going to perform and you develop a database design, you're ready to create your