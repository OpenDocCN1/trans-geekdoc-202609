# 14.7. DISLAYING GALLERIES

```
usersC := controllers.NewUsers(services.User)
// We also need to update this function call to provide the
// router
galleriesC := controllers.NewGalleries(services.Gallery
```

Next we need to define a name for our show galleries route. We will do that inside of the galleries controller source file, and will store it in a constant named ShowGallery.

```
$ atom controllers/galleries.go
```

```
const {
ShowGallery = "show_gallery"
)
```

Next we need to go back to our main source file where we declare the route and name it.

```
$ atom main.go
```

Find the route in your main function that is coded similar to the one below.

```
r.HandleFunc("/galleries/{id:[0-9]+}", galleriesC.Show).Methods("GET")
```