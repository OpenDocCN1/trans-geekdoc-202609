# Understanding the Privilege System in Detail

Table_priv set('Select', 'Insert', 'Update', 'Delete', 'Create', 'Drop',

'Grant', 'References', 'Index', 'Alter', 'Create View', 'Show view', 'Trigger');

Column_priv set ('Select', 'Insert', 'Update', 'References')

# #### Table 12.4 Schema of the columns_priv Table in the mysql Database

| Field | Type |
|---||
| Host | char(60) |
| Db | char(64) |
| User | char(16) |
| Table_name | char(64) |
| Column_name | char(64) |
| Timestamp | timestamp |
| Column_priv | set('Select', 'Insert', 'Update', 'References') |

# #### Table 12.5 Schema of the procs_priv Table in the mysql Database

| Field | Type |
|---||
| Host | char(60) |
| Db | char(64) |
| User | char(16) |
| Routine_name | char(64) |
| Routine_type | enum('FUNCTION', 'PROCEDURE') |
| Grantor | char(77) |
| Proc_priv | set('Execute', 'Alter Routine', 'Grant') |
| Timestamp | timestamp |