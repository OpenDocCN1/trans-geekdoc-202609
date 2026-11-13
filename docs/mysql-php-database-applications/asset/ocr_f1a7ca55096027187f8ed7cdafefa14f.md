# The user table

Every user who needs to get at MySQL must be listed in the user table. Rights might be granted elsewhere, but without a listing here the user is refused a connection to the database server. Here is the listing of columns in the user table:

```
mysql> show columns from user;
```

| Field | Type | Null | Key | Default | Extra |
| --- | --- | --- | --- | --- | --- |
| Host | varchar(60) binary | | PRI | | |
| User | varchar(16) binary | | PRI | | |
| Password | varchar(16) binary | | | | |
| Select_priv | enum('N','Y') | | | N | |
| Insert_priv | enum('N','Y') | | | N | |
| Update_priv | enum('N','Y') | | | N | |
| Delete_priv | enum('N','Y') | | | N | |
| Create_priv | enum('N','Y') | | | N | |
| Drop_priv | enum('N','Y') | | | N | |
| Reload_priv | enum('N','Y') | | | N | |
| Shutdown_priv | enum('N','Y') | | | N | |
| Process_priv | enum('N','Y') | | | N | |
| File_priv | enum('N','Y') | | | N | |
| Grant_priv | enum('N','Y') | | | N | |
| References_priv | enum('N','Y') | | | N | |
| Index_priv | enum('N','Y') | | | N | |
| Alter_priv | enum('N','Y') | | | N | |
| Show_db_priv | enum('N','Y') | | | N | |
| Super_priv | enum('N','Y') | | | N | |
| Create_tmp | enum('N','Y') | | | N | |
| _table_priv | | | | | |
| Lock_tables_priv | enum('N','Y') | | | N | |
| Execute_priv | enum('N','Y') | | | N | |
| Repl_slave_priv | enum('N','Y') | | | N | |
| Repl_client_priv | enum('N','Y') | | | N | |
| ssl_type | enum('','ANY','X509','SPECIFIED') | | | | |
| ssl_ cipher | blob | | | | |
| x509_issuer | blob | | | | |
| x509_subject | blob | | | | |
| max_questions | int(11) unsigned | | | 0 | |
| max_updates | int(11) unsigned | | | 0 | |
| max_connections | int(11) unsigned | | | 0 | |