```
$ atom views/users/new.gohtml
```

The password field and email address fields will remain unchanged. We simply need to add a new field with the type text for the name field.

```
{{define signupForm}}
<form action="/signup" method="POST">
  <div class="form-group">
    <label for="name">Name</label>
    <input type="text" name="name" class="form-control" id="name" placeholder="Your full name">
  </div>
  <!-- ... Everything else remains unchanged -->
</form>
{{end}}
```

After this you should start (or restart) your server to verify that the form was updated and include the field correctly. This is shown in Figure 9.1.

```
$ go run main.go
```