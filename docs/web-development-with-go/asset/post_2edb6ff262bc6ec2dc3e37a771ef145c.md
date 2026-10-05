
## 7.4. PROCESSING THE SIGN UP FORM

```go
type SignupForm struct {
  Email string
  Password string
}
```

The last thing we need to add will be new for many readers. We are going to add some struct tags¹¹² to our type.

## Struct 7.9. Struct tags

Struct tags are a form of metadata that can be added to the fields of any struct that you create. When coding them in they will be in the format `key: "value"` and are found directly after the field's (see Listing 7.23 for an example).

Later, when your program is running, other packages can use the reflect to look up each struct tag and then use data to determine how it should proceed. For example, the `encoding/json` package uses this data to determine which key you wanted for each field when converting a struct to JSON.

While it isn't a requirement, most packages will use their package name as the key for all of their struct tags. This makes it easier to determine what package each struct tag is for when reading your source code.

In Listing 7.23 each struct tag starts with the key `schema` which denotes that it is used by a package named schema. Similarly, all struct tags for the encoding/json package use the key `json`.

We are going to need struct tags because we don’t currently have a way to tell the schema package how to map our data in our form to fields in our Signup-Form struct. We have both "email" and "password" input in our sign form’s HTML, but the schema package doesn’t know about them.

> ¹²https://golang.org/pkg/reflect/#StructTag

## CHAPTER 7. CREATING A SIGN UP PAGE

To fix this, we simply need to add struct tags that let the schema package know about the input fields. The code for this is shown in Listing 7.23.

Listing 7.23: Sign up form struct
```go
type Signup struct {
    Email string `schema:"email"`
    Password string `schema:"password"`
}
```

We are now ready to start using the schema package to decode our HTML form and set the data to fields in our SignupType. To do this we first need to initialize a decoder and a SignupForm. Once we have both of these we are going to call the Decode method on our decode and pass in the SignupForm as our destination and r.PostForm as our data source. While we are at it, we will also check for errors.

The code for this is in Listing 7.24.

Don't forget to call r.ParseForm() in your code! If you forget to do this then r.PostForm won't have any values for our decoder to work with.

Listing 7.24: Using gorilla/schema in the create method
```go
// Add gorilla/schema to your imports
import (
    "fmt"
    "net/http"

    "github.com/gorilla/schema"

    "lenslocked.com/views"
)

// ... We are only editing the Create method.
func (u *Users) Create(w http.ResponseWriter, r *http.Request) {
    if err := r.ParseForm(); err != nil {
        panic(err)
    }
}
```

## 7.4. PROCESSING THE SIGN UP FORM

```go
dec := schema.NewDecoder()
form := SignupForm()
if err := dec.Decode(&form, r.PostForm); err != nil {
    panic(err)
}
fmt.Println(w, form)
```

Stop and restart your web app, then head over to the sign up page and submit it. It shouldn't be a lot different from last time, but now we should have our SignupForm type being printed out instead of two string slices.

## Source code

The links below have the completed source code and a diff of all the code changed in this section.

- Completed - book.usegolang.com/7.4.4
- Changes - book.usegolang.com/7.4.4-diff

## 7.4.5 Keeping your parsing code DRY

Programmers don't like to write the same code over and over again, so at some point they came up with the saying “Don't repeat yourself”. Or in acronym form - DRY.

What it basically means is if you find yourself writing code that you are likely to write several times, you should consider breaking it into a function or some reusable piece of code. This helps avoid bugs where we fix the same code in four places, but miss the fifth and final place where we wrote that code.

While working on our users controller we wrote some code inside our Create method that parses a form and decodes it, but if you look closely at the code you will notice that almost all of the code used to parse the HTML form and code it is pretty generic.

In this section we are going to look at how to move code out of Our Create method and instead move it into its own function so that we can reuse moving forward. We don't really have a great place to store this yet, so we are going to create a new source file named helpers.go inside of our controllers package and store the code there. This isn't the best name in the world, but it will work for now.

```bash
$ atom controllers/helpers.go
```

Next we will write the package declaration code import the packages we will need. Normally I would import packages until I use them, but because many of you won't have an auto-importer setup I I want to cover this before we get into the code.

```go
package controllers

import (
  "net/http"

  "github.com/gorilla/schema"
)
```

Now that we have our imports we are going to create a function named parseForm that will take two arguments. The first will be a *http.Request because we want our helper function to handle calling the ParseForm method and checking for any errors. This will also be necessary if we want to access the HTML form data.

The second argument our function is going to accept the destination where we want to store the information we parse from the HTML form. For this we will use the empty interface type (interface{}), which is our way of saying that it can be any type. This will allow us to pass a pointer to a SignupForm any other form types we declare later in our code.

Accepting the empty interface type also means that it is possible to pass in a variable that can't be decoded by the schema package. There isn't a way to prevent this at the compiler level, so instead we are going to have our function return an error when this happens. We will also return errors when any other issues arise, like an issue when initially parsing the HTML form.

Putting that all together, our initial function definition should look like the code in Listing 7.25.

**Listing 7.25:** Initial parseForm definition
```go
func parseForm(r *http.Request, dst interface{}) error {
}
```

We need to implement the parseForm function. Luckily we already wrote most of this code in the Create method inside of our users controller. We just need to copy it over and make a few changes to it. Open up your users controller...

```bash
$ atom controllers/users.go
```

And look for the code we wrote earlier that parses a form and decodes it using the schema package. It should be most of the code inside the code inside of the Create method.

```go
if err := r.ParseForm(); err != nil {
    panic(err)
}
dec := schema.NewDecoder()
form := SignupForm{}
if err := dec.Decode(&form, r.PostForm); err != nil {
    panic(err)
}
```

## CHAPTER 7. CREATING A SIGN UP PAGE

Copy this code and paste it into your parseForm function you just created.

Our parseForm function won't ever panic and instead return an error when occurs, so find the two lines of code that call panic and change them to instead return the error. We also need to return nil whenever no errors occur, so add that to the end of the function.

```go
func parseForm(r *http.Request, dst interface{}) error {
	if err := r.ParseForm(); err != nil {
		return err
	}
	dec := schema.NewDecoder()
	form := SignupForm()
	if err := dec.Decode(&form, r.PostForm); err != nil {
		return err
	}
	return nil
}
```

Our code won't work as intended just yet because we aren't decoding into the dst argument that is provided. We still have the old SignupForm variable being used.

Delete the line that creates the form variable, and then update the Decode method to use the dst argument. We don't need an ampersand (&) because we are going to expect the dst argument to already be a pointer.

```go
func parseForm(r *http.Request, dst interface{}) error {
	if err := r.ParseForm(); err != nil {
		return err
	}
	dec := schema.NewDecoder()
	if err := dec.Decode(dst, r.PostForm); err != nil {
				return err
	}
	return nil
}
```

Now we can update the Create method in the users controller to use the parseForm function we just created.
