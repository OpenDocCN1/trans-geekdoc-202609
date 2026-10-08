# Chapter 12 Advanced MySQL Administration

| Field | Type |
| --- | --- |
| File_priv | enum('N', 'Y') |
| Grant_priv | enum('N', 'Y') |
| References_priv | enum('N', 'Y') |
| Index_priv | enum('N', 'Y') |
| Alter_priv | enum('N', 'Y') |
| Show_db_priv | enum('N', 'Y') |n| Super_priv | enum('N', 'Y') |n| Create_tmp_table_priv | enum('N', 'Y') |n| Lock_tables_priv | enum('N', 'Y') |n| Execute_priv | enum('N', 'Y') |n| Repl_slave_priv | enum('N', 'Y') |n| Repl_client_priv | enum('N', 'Y') |n| Create_view_priv | enum('N', 'Y') |n| Show_view_priv | enum('N', 'Y') |n| Create_routine_priv | enum('N', 'Y') |n| Alter_routine_priv | enum('N', 'Y') |n| Create_user_priv | enum('N', 'Y') |n| Event_priv | enum('N', 'Y') |n| Trigger_priv | enum('N', 'Y') |n| Create_tablespace_priv | enum('N', 'Y') |n| ssl_type | enum('', 'ANY', 'X509', 'SPECIFIED') |n| ssl_cipher | blob |n| x509_issuer | blob |n| x509_subject | blob |n| max_questions | int(11) unsigned |
| max_updates | int(11) unsigned |
| max_connections | int(11) unsigned |
| max_user_connections | int(11) unsigned |
| plugin | char(64) |
| authentication_string | text |
| password_expired | enum('N', 'Y') |