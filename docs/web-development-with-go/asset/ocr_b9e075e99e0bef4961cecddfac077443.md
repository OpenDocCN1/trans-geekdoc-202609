# 8.3. USING POSTGRES WITH GO AND RAW SQL

information about connecting to our database.

Listing 8.6: Constants for connecting to Postgres
```go
const (
host = "localhost"
port = 5432
user = "postgres"
password = "your-password"
dbname = "lenslocked_dev"
)
```

These values should come from the ones you wrote down while gathering information about your Postgres installation (see Table 8.1).

It is typically frowned upon put things like passwords directly in your code because means that any developer who share your code with access your password, but in this case we are going to make an exception because we will generally be connecting to a database that is hosted locally and isn't exposed to the public.

Later in the book when we discuss deploying to a production server we will look at ways to take values like these and move them outside of our code and instead provide them to our code flags that we pass in when we execute the code.

Next we put all of this together to create a connection string that we use to connect to our database. We will only be using a few of the possible values, but you can read about every possible parameter in the docs github.com/lib/pq.

# Listing 8.7: Creating the connection string

sqlInfo := fmt.Sprintf("host=%s port=%d user=%s " + "password=%s dbname=%s sslmode=disable",
host, port, user, password, db)