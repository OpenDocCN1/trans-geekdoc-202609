# Additional Information

# Non-simple configuration and more information

As mentioned above, you can also use a language-specific configuration for full-text searches instead of the `simple` configuration that we’re currently using. When you create lexemes or query terms using a language-specific configuration, it will strip out common words for the language and perform word stemming.

So, for example, if you use the `english` configuration, then the lexemes generated for "`One Flew Over the Cuckoo's Nest`" would be '`cuckoo`' '`flew`' '`nest`' '`one`'. Or with the `spanish` configuration, the lexemes for "`Los lunes al sol`" would be '`lun`' '`sol`'.

You can retrieve a list of all available configurations by running the `\dF` meta-command in PostgreSQL:

```
postgres=# \dF
        List of text search configurations
 Schema |   Name   |          Description
--------+----------+-------------------------------
 pg_catalog | arabic | configuration for arabic language
 pg_catalog | danish | configuration for danish language
 pg_catalog | dutch  | configuration for dutch language
```