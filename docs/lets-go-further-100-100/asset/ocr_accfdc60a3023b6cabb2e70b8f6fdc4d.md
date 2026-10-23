```
nextval('users_id_seq'::regclass)
  created_at     | timestamp(0) with time zone |  | not null | now()
  name           | text                        |  | not null |
  email          | citext                      |  | not null |
  password_hash  | bytea                       |  | not null |
  activated      | boolean                     |  | not null |
  version        | integer                     |  | not null | 1
Indexes:
  "users_pkey" PRIMARY KEY, btree (id)
  "users_email_key" UNIQUE CONSTRAINT, btree (email)
```

One important thing to point out here: the `UNIQUE` constraint on our `email` column has automatically been assigned the name `users_email_key`. This will become relevant in the next chapter, when we need to handle any errors caused by a user registering twice with the same email address.