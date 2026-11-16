```
File: ui/html/pages/account.tmpl

{{define "title"}}Your Account{{end}}

{{define "main"}}
<h2>Your Account</h2>
{{with .User}}
<table>
<tr>
<th>Name</th>
<td>{{.Name}}</td>
</tr>
<tr>
<th>Email</th>
<td>{{.Email}}</td>
</tr>
<tr>
<th>Joined</th>
<td>{{humanDate .Created}}</td>
</tr>
</table>
{{end}}
{{end}}
```

```
File: cmd/web/handlers.go

...

func (app *application) accountView(w http.ResponseWriter, r *http.Request) {
userid := app.sessionManager.GetInt(r.Context(), "authenticatedUserID")

user, err := app.users.Get(userID)
if err != nil {
if errors.Is(err, models.ErrNoRecord) {
http.Redirect(w, r, "/user/login", http.StatusSeeOther)
} else {
app.serverError(w, r, err)
}
return
}

data := app.newTemplateData(r)
data.User = user

app.render(w, r, http.StatusOK, "account.tmpl", data)
}
```

# Suggested code for step 5