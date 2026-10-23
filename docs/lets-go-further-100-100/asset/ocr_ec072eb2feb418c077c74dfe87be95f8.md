```
1/u create_movies_table (11.782733ms)
2/u add_movies_check_constraints (23.109006ms)
3/u add_movies_indexes (30.61223ms)
4/u create_users_table (39.890662ms)
5/u create_tokens_table (48.659641ms)
6/u add_permissions (58.23243ms)
Connection to 45.55.49.87 closed.
```

Let’s quickly connect to our droplet and verify that everything has worked.

```
$ make production/connect
ssh greenlight@'45.55.49.87'
Welcome to Ubuntu 20.04.2 LTS (GNU/Linux 5.4.0-65-generic x86_64)
...
greenlight@greenlight-production:~$ ls -R
.:
api  migrations

./migrations:
000001_create_movies_table.down.sql
000001_create_movies_table.up.sql
000002_add_movies_check_constraints.down.sql
000002_add_movies_check_constraints.up.sql
000003_add_movies_indexes.down.sql
000003_add_movies_indexes.up.sql
000004_create_users_table.down.sql
000004_create_users_table.up.sql
000005_create_tokens_table.down.sql
000005_create_tokens_table.up.sql
000006_add_permissions.down.sql
000006_add_permissions.up.sql
```