# 548 CHAPTER 14. CREATING THE GALLERY RESOURCE

```
// In the Create method, inside a second if block:
g.New.Render(w, r, vd)

// In the Delete method, inside an if block:
g.EditView.Render(w, r, vd)
```

```
$ atom controllers/users.go
```

```
// In the New method:
u.New.Render(w, r, nil)
// Technically you don't need the handler and could just
// use the NewView as the handler when declaring the route.
```

```
// In the Create method, inside an if block:
u.New.Render(w, r, vd)
// In the Create method, inside a second if block:
u.New.Render(w, r, vd)

// In the Login method, inside an if block:
u.LoginView.Render(w, r, vd)
// In the Login method, inside a second if block:
u.Login.Render(w, r, vd)
// In the Login method, inside a third if block:
u.LoginView.Render(w, r, vd)
```

We are finally ready to update our templates. We'll start by updating the boot-strap layout template, telling it to pass all the data it has into the navbar tem-plate.

```
$ atom views/layouts/bootstrap.gohtml
```

Find the line where we call the navbar template and update it to add the dot ( ) as the last argument.