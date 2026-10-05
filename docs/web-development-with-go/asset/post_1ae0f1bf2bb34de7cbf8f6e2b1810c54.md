
[PAGE 477]

# CHAPTER 13. DISPLAYING ERRORS TO THE END USER

```go
var buf bytes.Buffer
```

Buffer is a type that implements the Read and Write interface from the io package. There are many use cases for Buffer, but in this situation we are going to be using the buffer as a temporary location to execute our templates into. Once we have confirmed that there weren't any errors executing the template we will have the entire template stored inside of our Buffer, and we can copy it over to the ResponseWriter.

Remember: We are using a buffer because writing any data to Response will result in a 200 status code and we can't undo that write. By writing to a buffer first we can confirm that the entire template executes before we start writing any data to the ResponseWriter.

```
var buf bytes.Buffer
err := v.Template.Execute(&buf, v.Layout, data)
if err != nil {
    // We will handle this in a moment
}
// If we get that means our template executed correctly
// and we can copy the buffer to the ResponseWriter
io.Copy(w, &buf)
```

On the last line of our code we use the Copy¹³ function provided by the io package. This function takes in a Writer and a Reader, and then copies all the data in the Reader over to the Writer. In our code we are copying all of the data from the Buffer over to the ResponseWriter.

The last thing we need to implement is what to do when an error occurs executing our template. In this situation we are going to utilize the Error function provided by the net/http package, and we will set the message to be a generic “Something went wrong” message, along with a 500 HTTP status code signaling that we had an internal server error.

> ¹³https://golang.org/pkg/io/#Copy

[PAGE 478]

# 13.8. RECOVERING FROM VIEW RENDERING ERRORS

Putting that all together, our Render method should look like the shown below.

```go
import (
    "bytes"
    "io"
)

func (v *View) Render(w http.ResponseWriter, data interface{}) {
    w.Header().Set("Content-Type", "text/html")
    switch data.(type) {
    case Data:
        // do nothing
    default:
        data = Data{
            Yield: data.data,
        }
    }
    var buf bytes.Buffer
    err := v.Template.ExecuteTemplate(&buf, v.Layout, data)
    if err != nil {
        http.Error(w, "Something went wrong. If the problem " +
            "persists, please email support@lenslocked.com",
            http.StatusInternalServerError)
        return
    }
    io.Copy(w, &buf)
}
```

After finishing the Render method we need to update any code that expected it to return an error. We will start off by updating the ServeHTTP method.

```go
func (v *View) ServeHTTP(w http.ResponseWriter, r *http.Request) {
    v.Render(w, nil)
}
```

Next is the New method in the users controller.

```bash
$ atom controllers/users.go
```

[PAGE 479]

```go
func (u *Users) New(w http.ResponseWriter, r *http.Request) {
  u.NewView.Render(w, nil)
}
```

Rebuild and restart your server to verify that everything is working again. We are officially done rendering errors for now, and we are ready to move on to much more interesting things!

In the next chapter we will learn how to add the Gallery resource, allow users to create new galleries, limit access to each individual gallery based on the the currently logged in user, how middleware works, and much more.

# Source code

The links below have the completed source code and a diff of all the code changed in this section.

- Completed - book.usegolang.com/13.8
- Changes - book.usegolang.com/13.8-diff

[PAGE 480]

# Chapter 14

# Creating the gallery resource

In this chapter we are going to take everything we have learned so far and start putting it to use to build out the Gallery resource. We will need to create a new model, a new controller, new actions, and new views, just like we did when creating the user resource.

In our application galleries are going to serve as a container resource. They will have a little bit of data on their own - such as the gallery name - but for the most part they are used to organize images and dictate permissions.

When a user goes to create a gallery, they will first tell us the name of the gallery, and then they will start adding images to the gallery. We will start by only supporting image uploads, but our code could be extended to support Dropbox syncing and much more.

After a user has added images to a gallery they will be able to share a URL to that gallery which others can visit in their browser and view the gallery. Only the author will be able to edit the gallery, but everyone will be able to view it.

Let's get started by defining the data we are going to store in our database.

[PAGE 481]

# 14.1 Defining the gallery model

We will be creating our gallery model in a new source file inside the models package.

```bash
$ atom models/galleries.go
```

We can start off by defining the package.

```go
package models
```

Our gallery resource may change over time, but for the now it needs the following data:

1. Normal model information
2. A way to track which user owns the gallery
3. A title for the gallery
4. A way to link images to the gallery

[PAGE 482]

# 14.1. DEFINING THE GALLERY MODEL

After that we need to track which user owns the gallery. The easiest way to do this is to store the ID of whatever user owns the gallery. User IDs are always integers (uint), so we will name this field UserID and give it the type. We want to require this field, so we will add “not-null” and “index” tags to inform GORM that we require this field and we want to index by UserID.

```go
import "github.com/jinzhu/gorm"

type Gallery struct {
	gorm.Model
	UserID uint `gorm:"not-null;index"`
	Title string `gorm:"not-null"`
}
```

While we will eventually want a way to link images to our gallery, we don't have any image resources yet so we are going to skip that for now. Once our users can create galleries with a Title and share then we will look at adding images to our galleries.

[PAGE 483]

# Source code

The links below have the completed source code and a diff of all the code changed in this section.

- Completed - book.usegolang.com/14.1
- Changes - book.usegolang.com/14.1-diff

# 14.2 Introducing the GalleryService

We need a way to interact with galleries, so our next step is to create a Gallery-Service. This will be an interface that exposes a set of functions which can be used to interact with our galleries data store.

Open the galleries source file inside the models package.

```bash
$ atom models/galleries.go
```

We will define the GalleryService interface and the GalleryDB interface. We don't have any specific methods we need to offer in our gallery service just yet, but we know that will be creating galleries shortly so we can start off with just the Create method and stub it out for the time being.

```go
type GalleryService interface {
	GalleryDB
}
type GalleryDB interface {
	Create(gallery *Gallery) error
}
type galleryGorm struct {
	db *gorm.DB
}

func (gg *galleryGorm) Create(gallery *Gallery) error {
	return gg.db.Create(gallery).Error
}
```
