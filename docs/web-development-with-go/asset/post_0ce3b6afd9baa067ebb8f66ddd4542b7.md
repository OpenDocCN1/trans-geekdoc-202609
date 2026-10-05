
## 16.3. CSRF PROTECTION

could try to write this ourselves but in my experience it is better to write a battle-tested security library like this than to write it itself. It is easy to introduce a bug otherwise, and in my experience most web developers don't ever write a CSRF library themselves but instead learn to use trusted libraries to do this for them.

First we need to install the package.

```go
$ go get github.com/gorilla/csrf
```

Once you install it it may want to reference the docs a bit. They can be found at: https://github.com/gorilla/csrf

In the docs we can find the following example:

```
CSRF := csrf.Protect([][]byte("32-byte-long-auth-key"))
http.ListenAndServe(":8000", CSRF(r))
```

The csrf package provides us with a Protect function that is used to create a CSRF middleware. We then apply this middleware to our router (or whatever top level handler we use) so that the CSRF protection happens before any other handlers get called. By doing this, we ensure that all incoming requests have their CSRF tokens validated before we run any custom code.

When creating the middleware we need a random 32 byte authentication key. This is used to make sure our application isn’t generating predictable CSRF tokens.

We are going to use this example as a starting point and add the CSRF middleware to our own application.

```go
$ atom main.go
```

We will tweak a name bit, and we will also be using the rand package created to generate 32 bytes.

```go
csrfMw := csrf.Protect(rand.Bytes(32))
```

Note: This may invalidate any existing CSRF tokens in forms when we restart our server, but I haven't seen this issue pop up frequently. We don't restart our server too often, and if you are really concerned you could add a static token into our config when we cover config files in this chapter.

Once we have our csrfMw function we can apply it to our router to make sure it runs before any other handlers.

```go
http.ListenAndServe(":3000", csrfMw.Apply(r))
```

Now any time a form is submitted or our server gets an HTTP POST request we csrfMw will check for a valid CSRF token. If it is present, the next handler will be called, otherwise the entire request will be rejected before it even gets to our handlers. This enables us to write our handlers assuming this security issue has already been implemented for us.

We need to make one final tweak to our code, which is telling the csrf package whether we are running in production or not. We are going to do this with a temporary variable that will eventually be replaced by a configuration variable when we introduce those.

Find the line where you instantiated your csrfMw variable and update it with the following code.

```go
// TODO: Update this to be a config variable
isProd := false
b, err := rand.Bytes(32)
if err != nil {
    panic(err)
}
csrMw := csrf.Protect(b, csrf.Secure(isProd))
```

The csrf package also provides us with a helper to generate tokens for our HTML forms. The package's docs then explain their recommended way of providing this to your HTML forms is to add it as a data field that you pass in to your templates. For instance, we might add this field to our views.Data type.

We are going to take a slightly different approach where we instead add it as a template function. The primary benefit to this approach over the recommended approach is that we can access it in any template, even if no data was passed into the template. This makes it easier to generate forms without having to worry about or not the CSRF token was provided as data to the form.

To do this we are going to look at the Funcs function¹ by the template package. With it we can introduce new functions that are available inside of our templates.

We are going to name the function csrfField and we will start by adding it to all of our templates that we need. We are going to assume that calling the function csrfField will return everything we need to generate a CSRF token hidden input field; that is, we are assuming it returns the entire HTML blob we need, not just a token.

```go
$ atom views/galleries/edit.gohtml
```

In the edit gallery template we need to add this function call for every form we create. All four of these templates are shown below, but it is important to note that we are only adding the csrfField function call directly after the form tag. Everything else remains unchanged.

```html
{{"editGalleryForm"}}
<form action="/galleries/{{.ID}}/update" method="POST" class="form-horizontal">
<!--
  This line will return:
  <input type="hidden">
with the CSRF token as its value.
-->
{{csrfField}}
<!-- remains unchanged --
</form>
{{end}}

{{define deleteGalleryForm}}
<form action="galleries/{{.ID}}/delete" method="POST" class="form-horizontal">
{{csrfField}}
<!-- remains unchanged --
</form>
{{end}}

{{define uploadImageForm}}
<form action="galleries/{{.ID}}/images" method="POST" enctype="multipart/form-data" class="form-horizontal">
{{csrfField}}
<!-- remains unchanged --
</form>
{{end}}

{{define deleteImageForm}}
<form action="galleries/{{.GalleryID}}/images/{{.Filename}}/delete" method="POST">
{{csrfField}}
<!-- remains unchanged --
</form>
{{end}}
```

Next up is the new gallery form.

```go
$ atom views/galleries/new.gohtml
```

```html
{{define galleryForm}}
<form action="/galleries" method="POST">
{{csrfField}}
<!-- remains unchanged --
</form>
{{end}}
```

And then the login form.

```go
$ atom views/users/login.gohtml
```

```html
{{define "loginForm"}}
<form action="/login" method="POST">
{{csrfField}}
  <!--... remains unchanged -->
</form>
{{end}}
```

Finally, the sign up form.

```go
$ atom views/users/new.gohtml
```

```html
{{define "signupForm"}}
<form action="/signup" method="POST">
{{csrfField}}
  <!--... remains unchanged -->
</form>
{{end}}
```

If we try to restart our server at this point we will see an error message equivalent to:

```
function "csrfField" not defined
```

Whenever we first parse our templates they will check to see if all the functions we are defined. At this point our csrfField function isn’t defined, but we can’t truly define it until a web request is made. This is due to the fact that we need to read the user’s CSRF token so we know which token to include in the form.

To handle this, we are creating a stubbed version of the csrfField function before we parse our templates, and then later when we get a web request we will update the template function before executing it for real.

Note: This technique is a little more advanced, but is incredibly useful once you understand it fully as it enables us to create template-wide functions with userspecific data. For instance we could replace the .User field of our views.Data type with function like isLoggedIn isAdmin and use those in any template, even if the .User field wasn't provided.

```go
$ atom views/view.go
```

We will start with new imports.

```go
import (
    "errors"
    "github.com/gorilla/csrf"
)
```

After that we will update the NewView function so that it provides a stubbed csrfFieldError. If this actually gives us without being replaced it will result in an error, but we will be replacing it when we call the Render method of our views.

```go
func NewView(layout string, files ...string) +View {
    addTemplatePath(files)
    addTemplateFiles(files)
    files = append(files, layoutFiles)
    // We are giving how we create a template that we can add a function to
    // New("")
    // finally passing in files to parse as part of the template
    t, err := template.New("layout").Funcs(template.FuncMap{
        csrfFieldError: func() error {
            // If this is called without being replace with a proper implementation
            // returning an error as the second argument will cause the template
            // package to return an error when executed.
            return errors.New("csrfFieldError is not implemented")
        },
        // Once we have our template with a function we are going to pass in files
        // to parse, much like we were previously.
    }).ParseFiles(files...)
    if err != nil {
```