
1 for rows.Next() {
    var uid int
    var name string
    var lastname string
    var created time.Time
    err = rows.Scan(&uid, &name, &lastname, &created)
}

Run prepared statements. Prepared statements are SQL statements where we can provide parameter values at a later point. You call the `Prepare()` function with `?` as placeholders where there will be data inserted:

stmt, err := db.Prepare("UPDATE person set lastname=? where uid=?")

To run the statement against the database, you can call `Exec()`:

res, err := stmt.Exec("smith", 1)

The `res` instance coming back has a function `RowsAffected()` that returns the number of affected rows:

affected, _ := res.RowsAffected()

Getting affected rows is a good indicator that you actually changed something.

Close the database connection. You should close the database when you’re done with it like so:

db.Close()

Create the database and populate it

We will create our database using the sqlite executable in the console.

1. Run `sqlite` to create the database and initialize the sqlite shell:

sqlite3 mydb.db
sqlite3SQLite version 3.32.3 2020-06-18 14:16:19
Enter ".help" for usage hints.

At this point, you have a database created. Next, we need some tables in there.

2. Run the following SQL command in the sqlite shell:

CREATE TABLE `person` (
        `uid` INTEGER PRIMARY KEY AUTOINCREMENT,
        `name` VARCHAR(64) NULL,
        `lastname` VARCHAR(64) NULL,
        `created` DATE NULL
    );

You know have the table “person” created. Next, we need some data in the table that we will interact with later in our Go code.

3. Run this SQL command to insert data into “person” table:

insert into person(name,lastname, created) values ("joe", "schmoo", '2021-01-01');

Great, we now have data in our table. Time to focus on the Go code next.

4. Run .exit to exit the database.

Create a project

Now we will create a Go project and some code able to access our database.

1. Create *db.go* and give it this content:

package main

import (
    "database/sql"
    "fmt"
    "log"
    _ "github.com/mattn/go-sqlite3"
)

func main() {
    db, err := sql.Open("sqlite3", "./mydb.db")
    if err != nil {
        log.Fatal(err)
    }
    fmt.Println("database open")

    fmt.Println("bye")

    fmt.Println("closing db")
    db.Close()
}

Next, lets initialize our Go project.

Run the following commands to create our project:

go mod init sql-demo

Run `go mo tidy`, to install the needed packages you specified in the import section of your program (this will download and add “github.com/mattn/go-sqlite3” to your project):

go mod tidy

Read data

Next, we will add a function capable of reading data.

Add a function `Read()` like so:

func Read(db *sql.DB) {
    rows, err := db.Query("SELECT * FROM person")

}

At this point, we have read the response into `rows`. Next, we need iterate on the response.

Add the following code, in `Read()` to iterate over the response:

for rows.Next() {
    var uid int
    var name string
    var lastname string
    var created time.Time
    err = rows.Scan(&uid, &name, &lastname, &created)
    if err != nil {
        log.Fatal(err)
    }
    fmt.Println(uid)
    fmt.Println(name)
    fmt.Println(lastname)
    fmt.Println(created)
}

Create data

Now we will create code that will allow us to create data in our database.

Add a function `Create`:

func Create(db *sql.DB) {
    stmt, err := db.Prepare("INSERT INTO person(name, lastname, created) values(?,?,?)\
    ")

    if err != nil {
        log.Fatal(err)
    }
    res, err := stmt.Exec("Mrs", "Smith", "2022-01-01")
    if err != nil {
        log.Fatal(err)
    }
    affected, _ := res.RowsAffected()
    log.Printf("Affected rows %d", affected)
}

Update and delete data

Updating and deleting data takes on very similar approach to how to create data. You will use a statement that you prepare and then send in the real values. Below is the code for performing both these actions:

Update

func Update(db *sql.DB) {
    stmt, err := db.Prepare("UPDATE person set lastname=? where uid=?")
    if err != nil {
        log.Fatal(err)
    }
    res, err := stmt.Exec("smith", 1)
    if err != nil {
        log.Fatal(err)
    }
    affected, _ := res.RowsAffected()
    log.Printf("Affected rows %d", affected)
}

Delete

func Delete(db *sql.DB) {
    stmt, err := db.Prepare("delete from person where uid=?")
    if err != nil {
        log.Fatal(err)
    }
    res, err := stmt.Exec(1)
    if err != nil {
        log.Fatal(err)
    }
    affected, _ := res.RowsAffected()
    log.Printf("Affected rows %d", affected)
}
