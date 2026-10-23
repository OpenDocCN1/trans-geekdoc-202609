
```
app.requireActivatedUser(app.showMovieHandler)
    router.HandlerFunc(http.MethodPatch, "/v1/movies/:id",
app.requireActivatedUser(app.updateMovieHandler))
    router.HandlerFunc(http.MethodDelete, "/v1/movies/:id",
app.requireActivatedUser(app.deleteMovieHandler))

    router.HandlerFunc(http.MethodPost, "/v1/users", app.registerUserHandler)
    router.HandlerFunc(http.MethodPut, "/v1/users/activated",
app.activateUserHandler)

    router.HandlerFunc(http.MethodPost, "/v1/tokens/authentication",
app.createAuthenticationTokenHandler)

    return app.recoverPanic(app.rateLimit(app.authenticate(router)))
}
```

## Demonstration

Alright, let’s try out these changes!

We’ll begin by calling the GET /v1/movies/:id endpoint as an anonymous user. When doing this you should now receive a 401 Unauthorized response, like so:

```
$ curl -i localhost:4000/v1/movies/1
HTTP/1.1 401 Unauthorized
Content-Type: application/json
Vary: Authorization
Www-Authenticate: Bearer
Date: Fri, 16 Apr 2021 15:59:33 GMT
Content-Length: 66

{
"error": "you must be authenticated to access this resource"
}
```

Next, let’s try making a request as a user who has an account, but has not yet activated. If you’ve been following along, you should be able to use the `alice@example.com` user to do this, like so:

```
$ BODY='{"email": "alice@example.com", "password": "pa55word"}'
$ curl -d "$BODY" localhost:4000/v1/tokens/authentication
{
    "authentication_token": {
        "token": "204YHHWDHVWWDNKN2UZR722BU",
        "expiry": "2021-04-17T18:03:09.598843181+02:00"
    }
}

$ curl -i -H "Authorization: Bearer 204YHHWDHVWWDNKN2UZR722BU"
localhost:4000/v1/movies/1
HTTP/1.1 403 Forbidden
Content-Type: application/json
Vary: Authorization
Date: Fri, 16 Apr 2021 16:03:45 GMT
Content-Length: 76

{
    "error": "your user account must be activated to access this resource"
}
```

Great, we can see that this now results in a `403 Forbidden` response from our new `inactiveAccountResponse()` helper.

Finally, let’s try making a request as an activated user.

If you’re coding-along, you might like to quickly connect to your PostgreSQL database and double-check which users are already activated.

```
$ psql $GREENLIGHT_DB_DSN
psql (13.2 (Ubuntu 13.2-1.pgdg20.04+1))
SSL connection (protocol: TLSv1.3, cipher: TLS_AES_256_GCM_SHA384, bits: 256,
compression: off)
Type "help" for help.

greenlight=> SELECT email FROM users WHERE activated = true;
        email
--------------------
 faith@example.com
(1 row)
```

In my case the only activated user is faith@example.com, so let’s try making a request as them. When making a request as an activated user, all the checks in our requireActivatedUser() middleware will pass and you should get a successful response. Similar to this:

```
$ BODY='{"email": "faith@example.com", "password": "pa55word"}'
$ curl -d "$BODY" localhost:4000/v1/tokens/authentication
{
  "authentication_token": {
    "token": "ZFIKQ344EYM5KEP6JL2RHL RPJQ",
    "expiry": "2021-04-17T18:04:57.513348573+02:00"
  }
}

$ curl -H "Authorization: Bearer ZFIKQ344EYM5KEP6JL2RHL RPJQ"
localhost:4000/v1/movies/1
{
  "movie": {
    "id": 1,
    "title": "Moana",
    "year": 2016,
    "runtime": "107 mins",
    "genres": [
      "animation",
      "adventure"
    ],
    "version": 1
  }
}
```

## Splitting up the middleware

At the moment we have one piece of middleware doing two checks: first it checks that the user is authenticated (not anonymous), and second it checks that they are activated.

But it’s possible to imagine a scenario where you only want to check that a user is authenticated, and you don’t care whether they are activated or not. To assist with this, you might want to introduce an additional requireAuthenticatedUser() middleware as well as the current requireActivatedUser() middleware.

However, there would be some overlap between these two middlewares, as they would both be checking whether a user is authenticated or not. A neat way to avoid this duplication is to have

If you only have a couple of endpoints where you want to perform authorization checks, then rather than using middleware it can often be easier to do the checks inside the relevant handlers instead. For example:

```
func (app *application) exampleHandler(w http.ResponseWriter, r *http.Request) {
    user := app.contextGetUser(r)

    if user.IsAnonymous() {
        app.authenticationRequiredResponse(w, r)
        return
    }

    if !user.Activated {
        app.inactiveAccountResponse(w, r)
        return
    }

    // The rest of the handler logic goes here...
}
```

| Method | URL Pattern | Required permission |
|---|---|---|
| GET | /v1/movies/:id | movies:read |
| PATCH | /v1/movies/:id | movies:write |
| DELETE | /v1/movies/:id | movies:write |
| POST | /v1/users | - |
| PUT | /v1/users/activated | - |
| POST | /v1/tokens/authentication | - |

## Relationship between permissions and users

The relationship between permissions and users is a great example of a *many-to-many* relationship. One user may have *many permissions*, and the same permission may belong to *many users*.

The classic way to manage a many-to-many relationship in a relational database like PostgreSQL is to create a *joining table* between the two entities. I'll quickly explain how this works.

Let's say that we are storing our user data in a `users` table which looks like this:

| id | email | ... |
|---|---|---|

| id | email | ... |
|---|---|---|
| 1 | alice@example.com | ... |
| 2 | bob@example.com | ... |

And our permissions data is stored in a `permissions` table like this:

| id | code |
|---|---|
| 1 | movies:read |
| 2 | movies:write |

Then we can create a joining table called `users_permissions` to store the information about *which users have which permissions*, similar to this:

| user_id | permission_id |
|---|---|
| 1 | 1 |
| 2 | 1 |
| 2 | 2 |

In the example above, the user `alice@example.com` (user ID `1`) has the `movies:read` (permission ID `1`) permission only, whereas `bob@example.com` (user ID `2`) has both the `movies:read` and `movies:write` permissions.

Just like the one-to-many relationship that we looked at earlier in the book, you may want to query this relationship from both sides in your database models. For example, in your database models you might want to create the following methods:

```
PermissionModel.GetAllForUser(user)      → Retrieve all permissions for a user
UserModel.GetAllForPermission(permission) → Retrieve all users with a specific permission
```

## Creating the SQL migrations

Let’s put this into practice and make a SQL migration which creates new `permissions` and `users_permissions` tables in our database, following the pattern that we’ve just described above.

Go ahead and run the following command to create the migration files:

```
$ migrate create -seq -ext .sql -dir ./migrations add_permissions
/home/alex/Projects/greenlight/migrations/000006_add_permissions.up.sql
/home/alex/Projects/greenlight/migrations/000006_add_permissions.down.sql
```

And then add the following SQL statements to the ‘up’ migration file:

```
File: migrations/000006_add_permissions.up.sql
```

```
CREATE TABLE IF NOT EXISTS permissions (
    id bigserial PRIMARY KEY,
    code text NOT NULL
);

CREATE TABLE IF NOT EXISTS users_permissions (
    user_id bigint NOT NULL REFERENCES users ON DELETE CASCADE,
    permission_id bigint NOT NULL REFERENCES permissions ON DELETE CASCADE,
    PRIMARY KEY (user_id, permission_id)
);

-- Add the two permissions to the table.
INSERT INTO permissions (code)
VALUES
    ('movies:read'),
    ('movies:write');
```

There are a couple of important things to point out here:

- The PRIMARY KEY (user_id, permission_id) line sets a composite primary key on our users_permissions table, where the primary key is made up of both the users_id and permission_id columns. Setting this as the primary key essentially means that the same user/permission combination can only appear once in the table and cannot be duplicated.
- When creating the users_permissions table we use the REFERENCES user syntax to create a foreign key constraint against the primary key of our users table, which ensures that any value in the user_id column has a corresponding entry in our users table. And likewise, we use the REFERENCES permissions syntax
