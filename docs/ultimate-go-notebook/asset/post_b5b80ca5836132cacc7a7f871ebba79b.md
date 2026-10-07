
Listing 4.34

```go
type user struct {
    name string
    email string
}

type admin struct {
    person user // NOT Embedding
    level string
}
```

This is embedding.

Listing 4.35

```go
type user struct {
    name string
    email string
}

type admin struct {
    user // Value Semantic Embedding
    level string
}
```

The person field is removed and just the type name is left. I can also embed a type using pointer semantics.

Listing 4.36

```go
type user struct {
    name string
    email string
}

type admin struct {
    *user // Pointer Semantic Embedding
    level string
}
```

In this case, a pointer of the type is embedded. In either case, accessing the embedded value is done through the use of the type's name.

The best way to think about embedding is to view the user type as an inner type and admin as an outer type. It's this inner/outer type relationship that is magical because with embedding, everything related to the inner type (both fields and methods) can be promoted up to the outer type.

# Listing 4.37

```go
type user struct {
    name string
    email string
}

func (u *user) notify() {
    fmt.Printf("Sending user email To %s<%s\n",
    u.name,
    u.email)
}

type admin struct {
    *user
    level string
}

func main() {
    ad := &admin{
        user: &user{
            name: "john smith",
            email: "john@yahoo.com",
        },
        level: "super",
    }

    ad.user.notify()
    ad.notify() // Outer type promotion
}
```

Output:
Sending user email To smith<john@yahoo.com>
Sending user email To john smith<john@yahoo.com>

Once I add a method named notify for the user type and a small main function, I can see the output is the same whether I call the notify method through the inner pointer value directly or through the outer type value. The notify method declared for the user type is accessible directly by the admin type value.

Though this looks like inheritance, I must be careful. This is not about reusing state, but about promoting behavior.

# Listing 4.38

```go
type notifier interface {
    notify()
}

func sendNotification(n notifier) {
    n.notify()
}
```

Now I add an interface and a polymorphic function that accepts any concrete type that implements the full set of behavior defined by the notifier interface. Which is just a method named notify.

Because of embedding and promotion, values of type admin now implement the notifier interface.

# Listing 4.39

```go
func main() {
    ad := admin{
        user: &user{
            name: "john smith",
            email: "john@yahoo.com",
        },
        level: "super",
    }
    sendNotification(&ad)
}
```

Output:
Sending user email To john smith<john@yahoo.com>
```

I can send the address of the admin value into the polymorphic function since embedding promotes the notify behavior up to the admin type.

# Listing 4.40

```go
type admin struct {
    *user // Pointer Semantic Embedding
    level string
}

func (a *admin) notify() {
    fmt.Printf("Sending admin Email To %s<%s\n",
        a.name,
        a.email)
}
```

When the outer type implements a method already implemented by the inner type, the promotion doesn't take place.

# Listing 4.41

```go
func main() {
    ad := admin{
        user: &user{
            name: "john smith",
            email: "john@yahoo.com",
        },
        level: "super",
    }
    sendNotification(&ad)
}
```

Output:
Sending admin email To john smith<john@yahoo.com>
```

I can see the outer type's method is now being executed.

## 4.14 Exporting

Exporting provides the ability to declare an identifier is accessible to code outside of the package it's declared in. A package is the basic unit of compiled code in Go. It represents a physical compiled unit of code, usually as a compiled library on the host operating system. Exporting determines access to identifiers across package boundaries.

Listing 4.42

```go
package counters
type AlertCounter int
```

In this case, since a capital letter is being used to name the type AlertCounter, the type is exported and can be referenced directly by code outside of the counters package.

Listing 4.43

```go
package counters
type alertCounter int
```

Now that I changed the type's name to start with a lowercase letter, the type is unexported. This means only code inside the counters package can reference this type directly.

Listing 4.44

```go
package counters
type alertCounter int
func New(value int) alertCounter {
  return alertCounter(value)
}
```

Even though the code above is legal syntax and will compile, there is no value in it. Returning a value of an unexported type is confusing since the caller (who will probably exist in a different package) can't reference the type name directly.

# Listing 4.45

```go
package main

import (
    "fmt"
    "github.com/ardanlabs/example/exporting"
)

func main() {
    counter := counters.New(10)
    fmt.Printf("Counter: %d\n", counter)
}
```
*(Note: The OCR for 4.45 was heavily garbled; I have reconstructed the logical code based on the context of the previous pages)*

# Listing 4.46

```go
package users

type User struct {
    Name string
    ID int

    password string
}

type Manager struct {
    Title string
    user
}
```

In this scenario, code outside of package users can construct a Manager, but since the embedded type is unexported, the fields for those type are accessible. Marshallers won't work otherwise.
