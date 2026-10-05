
The first thing we are going to do is add a variable that stores the directory where all of our variables are stored. We will call this TemplateDir. The code for this is shown in Listing 7.33.

## Listing 7.33: Template variables in view.go

```go
var (
    LayoutDir string = "views/layouts/"
    TemplateDir string = "views/"
    TemplateExt string = ".gohtml"
)
```

What we need is a function that can take the files that are provided to the NewView function and update them to automatically prepend the views/prefix, and append the .gohtml suffix. We are going to name this function addTemplatePath and it will take in one argument - a slice of strings that represent our template files. addTemplatePath will iterate over every string in the slice and set a new value for each entry in the slice that has the views/ string prepended to it. The code for this is shown in Listing 7.34.

### Box 7.10. Why don't we need a slice pointer?

Most of the time if we wanted to alter data passed into a function we would need to use a pointer variable, so why we don't need to do this with our slice passed into the addTemplatePath function?

Behind the scenes slices actually reference an array via a pointer. When you attempt to alter the size of the slice the changes won't be persisted, but if you instead alter some of the data inside of the slice you end up altering the data in the referenced array.

## 7.5. CLEANING UP AND CREATING A STATIC CONTROLLER

You can read more about this here: https://www.calhoun.io/why-are-slices-sometimes-altered-when-passed-by-value-in-go/

## Listing 7.34: Prepending the views directory

```go
// addTemplatePath takes in a slice of strings
// representing file paths for templates, and it prepends
// the TemplateDir to each string in the slice
// Eg the input ("home") would result in the output
// ("views/home" if TemplateDir == "views/
func addTemplatePath(files []string) {
  for i, f := range files {
    files[i] = TemplateDir + f
  }
}
```

Next, we are going to write a similar function, but instead of prepending the views directory we are going to append the template extension suffix. We are going to name this function addTemplateExt. This code is shown in Listing 7.35.

## Listing 7.35: Appending the .gohtml extension

```go
// addTemplateExt takes in a slice of strings
// representing file paths for templates and it appends
// the TemplateExt extension to each string in the slice
// Eg the input ("home") would result in the output
// ("home.gohtml" if TemplateExt == ".gohtml"
func addTemplateExt(files []string) {
  for i, f := range files {
    files[i] = f + TemplateExt
  }
}
```

We aren't using either of these functions yet, so let's update NewView to take advantage of them. This code is shown in Listing 7.36.

## CHAPTER 7. CREATING A SIGN UP PAGE

### Listing 7.36: Using the view file path helpers

```go
func NewView(layout string, files ...string) *View {
    addTemplatePath(files)
    addTemplateExt(files)
    files = append(files, layoutFiles()...)
    t, err := template.ParseFiles(files...)
    if err != nil {
        panic(err)
    }

    return &View{
        Template: t,
        Layout: layout,
    }
}
```

Finally, we need to update the controllers so that they don't pass in unnecessary data when creating a view.

```bash
$ atom controllers/users.go
```

Update the NewUsers function in the users controller so that the call to the NewView function doesn't pass in the views prefix or the .gohtml extension. This is shown in Listing 7.37.

## Listing 7.37: Cleaning up the NewUsers() function

```go
func NewUsers() *Users {
    return &Users{
        NewView: views.NewView("bootstrap", "users/new")
    }
}
```

We need to do the same thing to the views in the static controller.

## 7.5. CLEANING UP AND CREATING A STATIC CONTROLLER

```bash
$ atom controllers/static.go
```

This time we will be updating the NewStatic function. Both the home and contact views needed. The code for this is in Listing 7.38.

## Listing 7.38: Cleaning up the NewStatic() function

```go
func NewStatic() *Static {
  return &Static{
    Home: views.NewView("bootstrap", "static/home"),
    Contact: views.NewView("bootstrap", "static/contact"),
  }
}
```

Our code should be in a good state to restart the server and test everything out, so go ahead and do that.

```bash
$ go run main.go
```

If there is an error you will likely see an error as soon as the server starts, but visit the home, contact, and sign up pages to verify they all work. If the page is blank, check your server logs for any errors.

### Box 7.11. Potential errors

If you get an error with a message like “no such file or directory” this likely means that you didn’t update all of the views being created in the controllers, or that you have a bug in your view.go source file.

Look at the file your code is trying to open and this should give you a clue about what is going wrong. For example, if the file it is trying to access starts with

views/views/... (duplicate “views” directories) it likely means that your call to NewView is passing in the views/ prefix, and then the NewView function is calling the addTemplatePath prefix resulting in duplicate prefixes.

Likewise, if the file ends with .gohtml it probably means that you are passing in the extension with your files and then NewView function is appending another extension.

## Source code

The links below have the completed source code and a diff of all the code changed in this section.

Completed - book.usegolang.com/7.5.2

## 7.6 Exercises

We covered a lot in this chapter, but towards the end we started to repeat a lot of things that we learned earlier in the chapter. For example, creating a static controller wasn't much different than creating a users. While we aren't technically using a framework, what we are doing is very similar to building our own. Doing this also gives us lot of the benefits of a framework.

With that in mind, we are going to focus on some exercises that will help you reinforce what we are learning. You will need to edit a few files for each of these tasks, but you shouldn't need to make a large number of changes. Instead you should be doing some simple tasks like creating a method on a controller, updating main.go to inform the router, and creating a simple view, gaining experience with our application.

### 7.6.1 Ex1 - Add the FAQ page to the static controller

Just like many web applications have a contact page, our application might eventually need an FAQ page. Create a template (.html) for the FAQ page, and then add the new view to the static controller.

Once you have added it to the static controller, update your code in main.go so that the router sends visitors to this page when they visit the /faq path.

### 7.6.2 Ex2 - Create a new controller for galleries

We are eventually going to create a galleries resource, including a controller for it, but in the meantime we are going to use the galleries controller as an exercise.

Create a new galleries controller that has one action, the new action, represented by the New method.

You will first need to create a file where you will be declaring your galleries controller. Inside of that file you will want to create a type for the galleries controller, and then create a function that can be used to create a new galleries controller.

After that you will need to create the New () method on the type you created to represent your galleries controller. You could technically do this with just a view like we did with the FAQ page, but instead I would like you to write a method so that you get some practice doing that as well.

Inside of the New method you will need to render a view, so you will need to create one. I would recommend using the New user template as a guide for this.

Finally, you will need to register the New method with the router. Use the path /galleries/new with the HTTP GET method.

### 7.6.3 Exercise cleanup

We won't be using any of the code from our exercises moving forward, so free to delete it all once you have completed the exercises. These were just meant to help reinforce what we are learning.
