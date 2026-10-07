# Listing 4.45

```
package main

import (
    "fmt"

    "github.com/ardanlabs/.../exporting/example3/counters"
)

func main() {
    counter := counters.New(10)
    fmt.Printf("Counter: %d\n", counter)
}
```

In this case, the main function in package main calls the counters.New function successfully and the compiler can declare and construct a variable of the unexported type. This doesn't mean I should do or does not mean I'm getting any real protections for this. This should be avoided, and if New will return a value, it should be of an exported type.

# Listing 4.46

```
package users

type User struct {
    Name string
    ID int

    password string
}
```

When it comes to fields in a struct, the first letter declares if the field is accessible to code outside of the package it's declared in. In this case, Name and ID are accessible, but password is not. It's an idiom to separate exported and unexported fields in this manner if this is reasonable or practical to do. Normally all fields would be one or the other.

# Listing 4.47

```
package users

type user struct {
    Name string
    ID int
}

type Manager struct {
    Title string
    user
}
```

In this scenario, even though the user type is unexported, it has two exported fields. This means that when the user type is embedded in the exported Manager type, the user fields promote and are accessible. It's common to have types that