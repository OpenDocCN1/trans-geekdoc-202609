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
	CurrentYear int
	Snippet	models.Snippet
	Snippets	[]models.Snippet
	Form		any
	Flash		string
	IsAuthenticated	bool // Add an IsAuthenticated field to the templateData struct.
}

...
```

And the second step is to update our `newTemplateData()` helper so that this information is automatically added to the `templateData` struct every time we render a template. Like so:

```
File: cmd/web/helpers.go

package main

...

func (app *application) newTemplateData(r *http.Request) templateData {
	return templateData{
		CurrentYear: time.Now().Year(),
		Flash: app.sessionManager.PopString(r.Context(), "flash"),
		// Add the authentication status to the template data.
		IsAuthenticated: app.isAuthenticated(r),
	}
}

...
```

Once that's done, we can update the `ui/html/partials/nav.tmpl` file to toggle the navigation links using the `{{if .IsAuthenticated}}` action like so: