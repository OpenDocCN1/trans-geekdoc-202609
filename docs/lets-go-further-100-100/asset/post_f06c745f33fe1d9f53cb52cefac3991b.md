
```
claims.Issuer = "greenlight.alexedwards.net"
claims.Audiences = []string{"greenlight.alexedwards.net"}

// Sign the JWT claims using the HMAC-SHA256 algorithm and the secret key from the
// application config. This returns a []byte slice containing the JWT as a base64-encoded string.
jwtBytes, err := claims.HMACSign(jwt.HS256,
[]byte(app.config.jwt.secret))
if err != nil {
    app.serverErrorResponse(w, r, err)
    return
}

// Convert the []byte slice to a string and return it in a JSON response.
err = app.writeJSON(w, http.StatusCreated,
envelope{"authentication_token": string(jwtBytes)}, nil)
if err != nil {
    app.serverErrorResponse(w, r, err)
}
}
...
```

Go ahead and vendor the new `github.com/pascaldekloe/jwt` dependency and run the API like so:

```
$ make vendor
$ make run/api
```

Then when you make a request to the `POST /v1/tokens/authentication` endpoint with a valid email address and password, you should now get a response containing a JWT like this (line breaks added for readability):

```
$ curl -X POST -d '{"email": "faith@example.com", "password": "pa55word"}'
localhost:4000/v1/tokens/authentication
{
    "authentication_token":
"eyJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJncmVlbmxpZ2h0LmFsFsZXhlZHDcm
RzLm5ldCIsInN1YiI6IjciLCJhdWQiOlsiz3JlZW5saWdodC5hbGV4ZWR3YXJkcy5uZXQiXSwizXh
wIjoxNj
E4OTM4MjY0L jgxOTIwNSwib mJmIjoxNjE4ODUxOD Y0L jgxOTIwNSwiaWF0IjoxNjE4ODUxOD Y0L jg
xOTIwND
    h9.zNK1bJPl5rIr_Yvjy0XuimJwaC3KgPqmW2M1u5RvgeA"
}
```

If you’re curious, you can decode the base64-encoded JWT data. You should see that the content of the claims matches the information that you would expect, similar to this:

```
{"alg":"HS256"}{"iss":"greenlight.alexedwards.net","sub":"7","aud":
["greenlight.alexedwards.net"],
"exp":1618938264.819205,"nbf":1618851864.819205,"iat":1618851864.819204}...
```

Next you’ll need to update the `authenticate()` middleware to accept JWTs in an `Authorization: Bearer <jwt>` header, verify the JWT, and extract the user ID from the `subject` claim.

When we say “verify the JWT”, what we actually mean is the following four things:

- Check that the signature of the JWT matches the contents of the JWT, given our secret key. This will confirm that the token hasn’t been altered by the client.
- Check that the current time is between the “not before” and “expires” times for the JWT.
- Check that the JWT “issuer” is "greenlight.alexedwards.net".
- Check that "greenlight.alexedwards.net" is in the JWT “audiences”.

Go ahead and update the `authenticate()` middleware as follows:

```
File: cmd/api/middleware.go

package main

import (
    "errors"
    "expvar"
    "fmt"
    "net/http"
    "strconv"
    "strings"
    "sync"
    "time"

    "greenlight.alexedwards.net/internal/data"
)
```

```
"github.com/felixge/httpsnoop"
"github.com/pascaldekloe/jwt" // New import
"github.com/tomasen/realip"
"golang.org/x/time/rate"
)

...

func (app *application) authenticate(next http.Handler) http.Handler {
    return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
        w.Header().Add("Vary", "Authorization")

        authorizationHeader := r.Header.Get("Authorization")

        if authorizationHeader == "" {
            r = app.contextSetUser(r, data.AnonymousUser)
            next.ServeHTTP(w, r)
            return
        }

        headerParts := strings.Split(authorizationHeader, " ")
        if len(headerParts) != 2 || headerParts[0] != "Bearer" {
            app.invalidAuthenticationTokenResponse(w, r)
            return
        }

        token := headerParts[1]

        // Parse the JWT and extract the claims. This will return an error if
        // the JWT contents doesn't match the signature (i.e. the token has been
        // tampered with) or the algorithm isn't valid.
        claims, err := jwt.HMACCheck([]byte(token),
        []byte(app.config.jwt.secret))
        if err != nil {
            app.invalidAuthenticationTokenResponse(w, r)
            return
        }
    }
```

```
// Check if the JWT is still valid at this moment in time.
if !claims.Valid(time.Now()) {
    app.invalidAuthenticationTokenResponse(w, r)
    return
}

// Check that the issuer is our application.
if claims.Issuer != "greenlight.alexedwards.net" {
    app.invalidAuthenticationTokenResponse(w, r)
    return
}

// Check that our application is in the expected audiences for the JWT.
if !claims.AcceptAudience("greenlight.alexedwards.net") {
    app.invalidAuthenticationTokenResponse(w, r)
    return
}

// At this point, we know that the JWT is all OK and we can trust the data in
// it. We extract the user ID from the claims subject and convert it from a
// string into an int64.
userID, err := strconv.ParseInt(claims.Subject, 10, 64)
if err != nil {
    app.serverErrorResponse(w, r, err)
    return
}

// Lookup the user record from the database.
user, err := app.models.Users.Get(userID)
if err != nil {
    switch {
    case errors.Is(err, data.ErrRecordNotFound):
        app.invalidAuthenticationTokenResponse(w, r)
    default:
        app.serverErrorResponse(w, r, err)
    }
```

```
```
}
return
}

// Add the user record to the request context and continue as normal.
r = app.contextSetUser(r, user)

next.ServeHTTP(w, r)
})
}
```
```

Lastly, to get this working, you’ll need to create a new `UserModel.Get()` method to retrieve the user details from the database based on their ID.

```
```go
File: internal/data/users.go

package data

...

func (m UserModel) Get(id int64) (*User, error) {
    query := `
        SELECT id, created_at, name, email, password_hash, activated, version
        FROM users
        WHERE id = $1`

    var user User

    ctx, cancel := context.WithTimeout(context.Background(), 3*time.Second)
    defer cancel()

    err := m.DB.QueryRowContext(ctx, query, id).Scan(
        &user.ID,
```

```
&user.CreatedAt,
&user.Name,
&user.Email,
&user.Password.hash,
&user.Activated,
&user.Version,
)

if err != nil {
    switch {
    case errors.Is(err, sql.ErrNoRows):
        return nil, ErrRecordNotFound
    default:
        return nil, err
    }
}

return &user, nil
}
```

You should now be able to make a request to the one of the protected endpoints, and it will only succeed if your request contains a valid JWT in the Authorization header. For example:

```
$ curl -H "Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJncmlbmxpZ..." localhost:4000/v1/movies/2
{
    "movie": {
        "id": 2,
        "title": "Black Panther",
        "year": 2018,
        "runtime": "134 mins",
        "genres": [
            "sci-fi",

```
"action",
    "adventure"
],
    "version": 2
}
}

$ curl -H "Authorization: Bearer INVALID" localhost:4000/v1/movies/2
{
    "error": "invalid or missing authentication token"
}
```

> **Note:** Because JWTs are base64-encoded, you may be able to change the final character in the JWT and it will still be accepted as valid. This is OK, and a detailed explanation of why can be found in this StackOverflow post and this GitHub issue.

If you’re planning to put a system into production which uses JWTs, I also recommend spending some time to read and fully understand the following two articles:

- JWT Security Best Practices
- Critical vulnerabilities in JSON Web Token libraries

## Chapter 22.4.

## JSON Encoding Nuances

### Nil and empty slices are encoded differently

Nil slices in Go will be encoded to the null JSON value, whereas an empty (but not nil) slice will be encoded to an empty JSON array. For example:

```
var nilSlice []string
emptySlice := []string{}

m := map[string][]string{
    "nilSlice": nilSlice,
    "emptySlice": emptySlice,
}
```

Will encode to the following JSON:

```
{"emptySlice":[],"nilSlice":null}
```

### Using omitempty on a zero-valued struct doesn’t work

The omitempty struct tag directive never considers a struct to be empty — even if all the struct fields have their zero value and you use omitempty on those fields too. It will always appear as an object in the encoded JSON. For example, the following struct:

```
```go
s := struct {
    Foo struct {
        Bar string `json:",omitempty"`
    } `json:",omitempty"`
}{}
```
```

Will encode to the JSON:

```
```json
{"Foo":{}}
```
```

There’s a long-standing proposal which discusses changing this behavior, but the Go 1 compatibility promise means that it’s unlikely to happen any time soon. Instead, you can get around this by making the field a pointer to a struct, which works because omitempty considers nil pointers to be empty. For example:

```
```go
s := struct {
    Foo *struct {
        Bar string `json:",omitempty"`
    } `json:",omitempty"`
}{}
```
```
