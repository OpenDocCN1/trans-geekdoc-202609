
## Bad Request

To make the form submissions work, we need to use the nosurf.Token() function to get the CSRF token and add it to a hidden csrf_token field in each of our forms. So the next step is to add a new CSRFToken field to our templateData struct:

```
File: cmd/web/templates.go

package main

import (
	"html/template"
	"path/filepath"
	"time"

	"snippetbox.alexedwards.net/internal/models"
)

type templateData struct {
	CurrentYear	 int
	Snippet		 models.Snippet
	Snippets	 []models.Snippet
	Form		 any
	Flash		 string
	IsAuthenticated bool
	CSRFToken	 string // Add a CSRFToken field.
}

...
```

And because the logout form can potentially appear on every page, it makes sense to add the CSRF token to the template data automatically via our newTemplateData() helper. This will mean that it will be available to our templates each time we render a page.

Please go ahead and update the cmd/web/helpers.go file as follows:

```
File: cmd/web/helpers.go

package main

import (
	"bytes"
	"errors"
	"fmt"
	"net/http"
	"time"

	"github.com/go-playground/form/v4"
	"github.com/justinas/nosurf" // New import
)

...

func (app *application) newTemplateData(r *http.Request) templateData {
	return templateData{
		CurrentYear: time.Now().Year(),
		Flash: app.sessionManager.PopString(r.Context(), "flash"),
		IsAuthenticated: app.isAuthenticated(r),
		CSRFToken: nosurf.Token(r), // Add the CSRF token.
	}
}

...
```

Finally, we need to update all the forms in our application to include this CSRF token in a hidden field.

Like so:

```
File: ui/html/pages/create.tpl

{{define "title"}}Create a New Snippet{{end}}

{{define "main"}}
<form action='/snippet/create' method='POST'>
    <!-- Include the CSRF token -->
    <input type='hidden' name='csrf_token' value='{{.CSRFToken}}'>
    <div>
        <label>Title:</label>
        {{with .Form.FieldErrors.title}}
            <label class='error'>{{.}}</label>
        {{end}}
        <input type='text' name='title' value='{{.Form.Title}}'>
    </div>
    <div>
        <label>Content:</label>
        {{with .Form.FieldErrors.content}}
            <label class='error'>{{.}}</label>
        {{end}}
        <textarea name='content'>{{.Form.Content}}</textarea>
    </div>
    <div>
        <label>Delete in:</label>
        {{with .Form.FieldErrors.expires}}
            <label class='error'>{{.}}</label>
        {{end}}
        <input type='radio' name='expires' value='365' {{if (eq .Form.Expires 365)}}checked{{end}}> One Year
        <input type='radio' name='expires' value='7' {{if (eq .Form.Expires 7)}}checked{{end}}> One Week
        <input type='radio' name='expires' value='1' {{if (eq .Form.Expires 1)}}checked{{end}}> One Day
    </div>
    <div>
        <input type='submit' value='Publish snippet'>
    </div>
</form>
{{end}}
```

```
File: ui/html/pages/login.tmpl

{{define "title"}}login{{end}}

{{define "main"}}
<form action='/user/login' method='POST' novalidate>
<!-- Include the CSRF token -->
<input type='hidden' name='csrf_token' value='{{.CSRFToken}}'>
{{range .Form.NonFieldErrors}}
<div class='error'>{{.}}</div>
{{end}}
<div>
<label>Email:</label>
{{with .Form.FieldErrors.email}}
<label class='error'>{{.}}</label>
{{end}}
<input type='email' name='email' value='{{.Form.Email}}'>
</div>
<div>
<label>Password:</label>
{{with .Form.FieldErrors.password}}
<label class='error'>{{.}}</label>
{{end}}
<input type='password' name='password'>
</div>
<div>
<input type='submit' value='Login'>
</div>
</form>
{{end}}
```

```
File: ui/html/pages/signup.tmpl

{{define "title"}}Signup{{end}}

{{define "main"}}
<form action='/user/signup' method='POST' novalidate>
    <!-- Include the CSRF token -->
    <input type='hidden' name='csrf_token' value='{{.CSRFToken}}'>
    <div>
        <label>Name:</label>
        {{with .Form.FieldErrors.name}}
            <label class='error'>{{.}}</label>
        {{end}}
        <input type='text' name='name' value='{{.Form.Name}}'>
    </div>
    <div>
        <label>Email:</label>
        {{with .Form.FieldErrors.email}}
            <label class='error'>{{.}}</label>
        {{end}}
        <input type='email' name='email' value='{{.Form.Email}}'>
    </div>
    <div>
        <label>Password:</label>
        {{with .Form.FieldErrors.password}}
            <label class='error'>{{.}}</label>
        {{end}}
        <input type='password' name='password'>
    </div>
    <div>
        <input type='submit' value='Signup'>
    </div>
</form>
{{end}}
```

```
File: ui/html/partials/nav.tmpl

{{define "nav"}}
<nav>
    <div>
        <a href='/'>Home</a>
        {{if .IsAuthenticated}}
            <a href='/snippet/create'>Create snippet</a>
        {{end}}
    </div>
    <div>
        {{if .IsAuthenticated}}
            <form action='/user/logout' method='POST'>
                <!-- Include the CSRF token -->
                <input type='hidden' name='csrf_token' value='{{.CSRFToken}}'>
                <button>Logout</button>
            </form>
        {{else}}
            <a href='/user/signup'>Signup</a>
            <a href='/user/login'>Login</a>
        {{end}}
    </div>
</nav>
{{end}}
```

Go ahead and run the application again, then view source of one of the forms. You should see that it now has a CSRF token included in a hidden field, like so.

![](img/c3e650db0d8dfdecc0f8e34a67719f65_322_0.png)

And if you try submitting the forms, it should now work correctly again.

## Additional information

## SameSite 'Strict' setting

If you want, you can change the session cookie to use the SameSite=Strict setting instead of (the default) SameSite=Lax. Like this:

```
sessionManager := scs.New()
sessionManager.Cookie.SameSite = http.SameSiteStrictMode
```

But it's important to be aware that using SameSite=Strict will block the session cookie being sent by the user’s browser for all cross-site usage — including safe requests with HTTP methods like GET and HEAD.

While that might sound even safer (and it is!) the downside is that the session cookie won’t be sent when a user clicks on a link to your application from another website. In turn, that means that your application would initially treat the user as ‘not logged in’ even if they have an active session containing their "authenticatedUserID" value.

So if your application will potentially have other websites linking to it (or links to it shared in emails or private messaging services), then SameSite=Lax is generally the more appropriate setting.

## SameSite cookies and TLS 1.3

Earlier in this chapter I said that we can’t solely rely on the SameSite cookie attribute to prevent CSRF attacks, because it isn’t fully supported by all browsers.

But there is an exception to this rule, due to the fact that no browser exists which supports TLS 1.3 and does not support SameSite cookies.

In other words, if you were to make TLS 1.3 the minimum supported version in the TLS config for your server, then all browsers able to use your application will support SameSite cookies.

```
tlsConfig := &tls.Config{
	MinVersion: tls.VersionTLS13,
}
```

So long as you only allow HTTPS requests to your application and enforce TLS 1.3 as the minimum TLS version, you don’t need to make any additional mitigation against CSRF attacks (like using the justinas/nosurf package). Just make sure that you always:

- Set SameSite=Lax or SameSite=Strict on the session cookie; and
- Use the POST, PUT or DELETE HTTP methods for any state-changing requests.

## Using request context

At the moment our logic for authenticating a user consists of simply checking whether a "authenticatedUserID" value exists in their session data, like so:

```
func (app *application) isAuthenticated(r *http.Request) bool {
	return app.sessionManager.Exists(r.Context(), "authenticatedUserID")
}
```

We could make this check more robust by querying our users database table to make sure that the "authenticatedUserID" value is a real, valid, value (i.e we haven't deleted the user's account since they last logged in).

But there is a slight problem with doing this additional database check.

Our isAuthenticated() helper can potentially be called multiple times in each request cycle. Currently we use it twice — once in the requireAuthentication() middleware and again in the newTemplateData() helper. So, if we query the database from the isAuthenticated() helper directly, we would end up making duplicated round-trips to the database during every request. And that's not very efficient.

A better approach would be to carry out this check in some middleware to determine whether the current request is from an authenticated user or not, and then pass that information down to all subsequent handlers in the chain.

So how do we do this? Enter request context.

In this section you'll learn:

- What request context is, how to use it, and when it is appropriate to use it.
- How to use request context in practice to pass information about the current user between your handlers.
