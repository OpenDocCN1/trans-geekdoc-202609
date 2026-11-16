# Nested templates

It's really important to note that when you're invoking one template from another template, dot needs to be explicitly passed or _pipelined_ to the template being invoked. You do this by including it at the end of each {{template}} or {{block}} action, like so:

```
{{template "main".}}
{{block "sidebar".}}{{end}}
```

As a general rule, my advice is to get into the habit of always pipelining dot whenever you invoke a template with the {{template}} or {{block}} actions, unless you have a good reason not to.

# Calling methods

If the type that you're yielding between {{ }} tags has methods defined against it, you can call these methods (so long as they are exported and they return only a single value — or a single value and an error).

For example, our .Snippet.Created struct field has the underlying type time.Time, meaning that you could render the name of the weekday by calling its Weekday() method like so:

```
<span>{{.Snippet.Created.Weekday}}</span>
```

You can also pass parameters to methods. For example, you could use the AddDate() method to add six months to a time like so:

```
<span>{{.Snippet.Created.AddDate 0 6 0}}</span>
```

Notice that this is different syntax to calling functions in Go — the parameters are _not_ surrounded by parentheses and are separated by a single space character, not a comma.

# HTML comments

Finally, the html/template package always strips out any HTML comments you include in your templates, including any conditional comments.

The reason for this is to help avoid XSS attacks when rendering dynamic content. Allowing conditional comments would mean that Go isn't always able to anticipate how a browser