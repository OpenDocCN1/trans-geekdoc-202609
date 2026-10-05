# 7.4. PROCESSING THE SIGN UP FORM

```
type SignupForm struct {
  Email string
  Password string
}
```

The last thing we need to add will be new for many readers. We are going to add some struct tags¹¹² to our type.

# Struct 7.9. Struct tags

Struct tags are a form of metadata that can be added to the fields of any struct that you create. When coding them in they will be in the format `key: "value"` and are found directly after the field's (see Listing 7.23 for an example).

Later, when your program is running, other packages can use the reflect to look up each struct tag and then use data to determine how it should proceed. For example, the `encoding/json` package uses this data to determine which key you wanted for each field when converting a struct to JSON.

While it isn't a requirement, most packages will use their package name as the key for all of their struct tags. This makes it easier to determine what package each struct tag is for when reading your source code.

In Listing 7.23 each struct tag starts with the key `schema` which denotes that it is used by a package named schema. Similarly, all struct tags for the encoding/json package use the key `json`.

We are going to need struct tags because we don’t currently have a way to tell the schema package how to map our data in our form to fields in our Signup-Form struct. We have both "email” and "password” input in our sign form’s HTML, but the schema package doesn’t know about them.

> ¹²https://golang.org/pkg/reflect/#StructTag