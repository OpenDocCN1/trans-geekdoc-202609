
```
cost := bcrypt.DefaultCost
res, err := bcrypt.GenerateFromPassword(input, cost)
if err != nil {
    http.Error(w, fmt.Sprintf("Error: %s", err), http.StatusInternalServerError)
    return
}

h := HashResponse{
    Hash: string(res),
    Cost: cost,
}

hBytes, _ := json.Marshal(h)

w.WriteHeader(http.StatusOK)
w.Write(hBytes)
}
```

We could break this code into types.go and handler.go:

types.go

```
package types

type HashResponse struct {
    Hash string
    Cost int
}
```

And handler.go:

```
package function

import (
    "encoding/json"
    "fmt"
    "io"
    "net/http"
    "golang.org/x/crypto/bcrypt"
)

func Handle(w http.ResponseWriter, r *http.Request) {
    var input []byte

    if r.Body != nil {
        defer r.Body.Close()
        body, _ := io.ReadAll(r.Body)
        input = body
    }

    cost := bcrypt.DefaultCost
    res, err := bcrypt.GenerateFromPassword(input, cost)
    if err != nil {
        http.Error(w, fmt.Sprintf("Error: %s", err), http.StatusInternalServerError)
        return
    }

    h := HashResponse{
        Hash: string(res),
        Cost: cost,
    }
    hBytes, _ := json.Marshal(h)

    w.WriteHeader(http.StatusOK)
    w.Write(hBytes)
}
```

Notice that both files started with package function so they can access each other's methods. The same is the case for any unit tests you want to add to this package.

You can add files within the same package without adding sub-packages. Sub-packages are better suited to sharing code between functions, or logical separation of concerns.

## Introduce a sub-package

Taking the previous example, create a new folder named types, then create types/types.go:

```
package types

type HashResponse struct {
    Hash string
    Cost int
}
```

Then for handler.go:

```
package function

import (
    "encoding/json"
    "fmt"
    "handler/function/types"
    "io"
    "net/http"

    "golang.org/x/crypto/bcrypt"
)

func Handle(w http.ResponseWriter, r *http.Request) {
    var input []byte

    if r.Body != nil {
        defer r.Body.Close()
        body, _ := io.ReadAll(r.Body)
        input = body
    }

    cost := bcrypt.DefaultCost
    res, err := bcrypt.GenerateFromPassword(input, cost)
    if err != nil {
        http.Error(w, fmt.Sprintf("Error: %s", err), http.StatusInternalServerError)
        return
    }

    h := types.HashResponse{
        Hash: string(res),
        Cost: cost,
    }
    hBytes, _ := json.Marshal(h)

    w.WriteHeader(http.StatusOK)
    w.Write(hBytes)
}
```

Notice that h := HashResponse{ changed to h := types.HashResponse{ to access the new package. The package was imported as handler/function/types, which is a standard for the template.

At this point faas-cli build will work, but go test may not resolve the function, so enter the go.mod directory and run the following:

```
cd bcrypt-fn

# Should fail
go build

go mod edit -replace=handler/function=./
go get handler/function
cd ..

# Should resolve the error
go build
```

That tells the local system to look for handler/function in the top level directory.

## Working with secrets and databases

In the “Store data with a database” chapter we covered how to connect to a database. Run those steps again to create a database table named todo with the specified schema.

Here we'll focus on how to define the secrets and configuration for accessing the database from the function, and how to keep the connection open between requests.

Both of these concepts are configured through your function's YAML file.

- For confidential data, always use a secret
- For non-confidential configuration, you can use an environment variable

Confidential data is anything that you want to keep secret and that you would not be comfortable sharing with others, such as your database host, password and username.

Non-confidential configuration is something like: “debug: true” or “output: json”.

## Create the todo-fn example

Create a new function:

```
export GH_USERNAME="alexellis"
mkdir -p $GOPATH/src/github.com/$GH_USERNAME/todo-fn/
cd $GOPATH/src/github.com/$GH_USERNAME/todo-fn/
```

Now scaffold a new function using the golang-middleware template:

```
faas-cli template store pull golang-middleware

faas-cli new --lang golang-middleware \
    todo-fn
```

My connection string from the DigitalOcean dashboard was: postgresql://doadmin:ildkq2my7g7lqqxh@todo-pg11-do-user-2197152-0.b.db.ondigitalocean.com:25060/defaultdb?sslmode=require

Split it up to create a number of secrets using faas-cli secret create command.

```
faas-cli secret create db-user --from-literal $DBUSER
faas-cli secret create db-pass --from-literal $DBPASS
```

After creating a function, you can add it to the secrets: section of its YAML file, so that it will be attached at run-time.

The secret will be mounted at /var/openfaas/secrets/<NAME>. Both text strings and binary files are supported.

Then edit todo-fn.yml and add the following secrets and environment sections.

```yaml
version: 1.0
provider:
  name: openfaas
  gateway: http://127.0.0.1:8080
functions:
  todo-fn:
    lang: golang-middleware
    handler: ./todo-fn
    image: docker.io/alexellis2/todo-fn:latest
    secrets:
    - db-user
    - db-pass
    environment:
      db_host: "todo-pg11-do-user-2197152-0.b.db.ondigitalocean.com"
      db_port: "25060"
      db_name: "defaultdb"
      db_ssl_mode: "require"
```

Create todo-fn/types.go and add the following:

```
package function

import (
    "time"

    _ "github.com/lib/pq"
)

type Todo struct {
    ID            int       `json:"Id"`
    Description   string    `json:"description"`
    CreatedDate   time.Time `json:"created_date"`
    CompletedDate *time.Time `json:"completed_date,omitempty"`
}
```

I've added json annotations to each field to output the JSON with similar names to the database fields. This is optional.

Create db.go. The code is largely the same as the previous chapter. I’ve just changed the input to a Todo struct, instead of a plain string.

```go
package function

import (
    "database/sql"
    "fmt"

    _ "github.com/lib/pq"
)

func connect(user, password, host, dbName, sslMode string, port int) (*sql.DB, error) {
    connStr := "postgres://" + user + ":" + password + "@" + host + ":" + fmt.Sprintf("%d",
        port) + "/" + dbName + "?sslmode=" + sslMode

    db, err := sql.Open("postgres", connStr)
    if err != nil {
        return nil, err
    }

    err = db.Ping()
    if err != nil {
        return nil, err
    }

    return db, nil
}

func create(db *sql.DB, todo Todo) error {
    if len(todo.Description) == 0 {
        return fmt.Errorf("description is required")
    }

    res, err := db.Query(`INSERT INTO
        todo
        (id, description, created_date)
        VALUES
        (DEFAULT, $1, now());`,
        todo.Description)

    if err != nil {
        return err
    }

    defer res.Close()
    return nil
}

func list(db *sql.DB) ([]Todo, error) {
    rows, err := db.Query(`SELECT
        id,
        description,
        created_date,
        completed_date
FROM todo;`)

    if err != nil {
        return []Todo{},
            fmt.Errorf("unable to get from todo table: %w", err)
    }

    todos := []Todo{}
    defer rows.Close()
    for rows.Next() {
        result := Todo{}
        err := rows.Scan(&result.ID,
            &result.Description,
            &result.CreatedDate,
            &result.CompletedDate)
        if err != nil {
            return []Todo{}, fmt.Errorf("row scan error: %w", err)
        }
        todos = append(todos, result)
    }
    return todos, nil
}
```

## Exploring the request

Now we need to write a handler to exercise the code above. In the previous chapter we used a CLI flag to determine which operation to perform.

We don't have any CLI flags, but we do have the whole HTTP request that we can use to determine what to do:
- The HTTP body (parsed as a JSON type)
- The HTTP query string
- The HTTP method
- The HTTP path
- Some other custom HTTP header

Or we could combine any of the above, such as a “GET” and a certain path “/todo/list” or “DELETE” and “/todo/delete/1”. This part is up to you.

I'll try to keep it as simple as possible, so that you can see at least one approach in action.

The following reads the various secrets and environment variables from the function's YAML file and creates a connection to the database.

```
var (
    dbUser   string
    dbPass   string
    host     string
    dbName   string
    sslMode  string
    port     int
    dbConn   *sql.DB
)

// init reads the various secrets and configuration required
// and then opens a DB connection, or panics if this fails.
// In the case of a failure, see the container's logs
func init() {
    var err error
```
