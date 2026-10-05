# CHAPTER 9. CREATING THE USER MODEL

Eventually we will pull these constants out of our code and provide them via flags to our application when we start it up, but in the meantime just be aware that this isn't a great way to do things, but we are doing it to simplify our code a bit until we start talking about how to get production ready.

Next we need to create our connection string. Again you can copy that from the experimental code before. This will go inside of the `main` function.

```
func main() {
// Create a DB connection string and then use it to
// create our model services.
psqlInfo := fmt.Sprintf("host=%s port=%d user=%s " + 
"password=%s dbname=%s sslmode=disable",
host, port, user, password, dbname)
// ... the controllers and routing code is unchanged
}
```

After that we need to create a user service using this connection string. Right creating the user service we will also want to check for an error, defer closing it until our main function exits, and call the `AutoMigrate` function we wrote earlier to make sure our database is migrated properly.

```
import (
"fmt"
"net/http"

"lenslocked.com/controllers"
"lenslocked.com/models"

"github.com/gorilla/mux"
)
// ...

func main() {
// ... the psqlInfo code comes first
```