|-- tape.go
|-- tape_test.go

We now effectively have a separation between our application and the library code but we now need to change some package names. Remember when you build a Go application its package must be main.

Change all the other code to have a package called poker.

Finally, we need to import this package into main.go so we can use it to create our web server. Then we can use our library code by using poker.FunctionName.

The paths will be different on your computer, but it should be similar to this:

```
```go
//cmd/webserver/main.go
package main

import (
    "github.com/quii/learn-go-with-tests/command-line/v1"
    "log"
    "net/http"
    "os"
)

const dbFileName = "game.db.json"

func main() {
    db, err := os.OpenFile(dbFileName, os.O_RDWR|os.O_CREATE, 06
    if err != nil {
        log.Fatalf("problem opening %s %v", dbFileName, err)
    }

    store, err := poker.NewFileSystemPlayerStore(db)

    if err != nil {
        log.Fatalf("problem creating file system player store, %
    }
```
```