# Source code

The links below have the completed source code and a diff of all the code changed in this section.

Completed - book.usegolang.com/6.5.3

Changes - book.usegolang.com/6.5.3-diff

# 6.5.4 Moving our footer to the layout

The last thing we need to do in our cleanup phase is remove the footer template calls from the home and contact templates.

While this code isn't incorrect, the footer template really belongs in the bootstrap layout template that we created earlier, and moving it is pretty simple.

Open up both the home and contact templates and remove the line that reads:

```
{{template "footer"}}
```

| Listing 6.32: home.gohtml without the footer |

{{define "yield"
<h1>Welcome to my awesome site!</h1>
{{end}}

| Listing 6.33: contact.gohtml without the footer. |

{{define "yield"
To get in touch, please send an email to
<a href="mailto:support@lenslocked.com">support@lenslocked.com</a>
{{end}}