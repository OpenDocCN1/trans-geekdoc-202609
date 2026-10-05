
# CHAPTER 14. CREATING THE GALLERY RESOURCE

```go
// Closes the database connection
func (s *Services) Close() error {
    return s.db.Close()
}
```

Next up is the AutoMigrate method, which will be similar to the AutoMigrate method we wrote as part of the UserGorm type, but will attempt to automatically migrate all of our models.

```go
// AutoMigrate will attempt to automatically migrate all tables
func (s *Services) AutoMigrate() error {
    return s.db.AutoMigrate(&User(), &Gallery()).Error
}
```

Finally we have the DestructiveReset method, which will try to drop database table and then reconstruct it with the AutoMigrate method.

```go
// DestructiveReset drops all tables and rebuilds them
func (s *Services) DestructiveReset() error {
    err := s.db.DropTableIfExists(&User(), &Gallery()).Error
    if err != nil {
        return err
    }
    return s.AutoMigrate()
}
```

Now that we have a way to close and migrate all of services at once we can update our main function to use the new methods.

```bash
atom main.go
```

```go
func main() {
    psqlInfo := fmt.Sprintf("host=%s port=%d user=%s " +
    "password=%s dbname=%s sslmode=disable",
    host, port, user, password, dbname)
```

## 14.4. CLOSING AND MIGRATING ALL MODELS

```go
services, err := models.NewServices(psqlInfo)
if err != nil {
    panic(err)
}
defer services.Close()
services.AutoMigrate()

// ... The rest remains unchanged
```

And now we can remove any unused code we have left, such as the Close, AutoMigrate, and DestructiveReset methods we wrote as part of the UserService. Those methods are no longer necessary there, and removing them will help simplify the UserService bit.

```bash
atom models/users.go
```

First we will remove the methods from the UserDB interface.

```go
type UserDB interface {
  // Methods for querying single users
  ByID(id uint) (*User, error)
  ByEmail(email string) (*User, error)
  ByMember(token string) (*User, error)

  // Methods for altering users
  Create(user *User) error
  Update(user *User) error
  Delete(id uint) error
}
```

And we need to find the three method implementations associated with the Galleryorm type and delete them.

```go
// Delete these three functions
func (ug *userorm) Close() error { ... }
func (ug *userorm) DestructiveReset() error { ... }
func (ug *userorm) AutoMigrate() error { ... }
```

Restart your server and you should see logs indicating that the galleries table is created by the call to AutoMigrate. Your logs will be slightly different, but should have similarly to the ones below.

```sql
CREATE TABLE "galleries" (...)
CREATE INDEX idx_galleries_deleted_at ...
CREATE INDEX idx_galleries_user_id ...
```

# Source code

- Completed - book.usegolang.com/14.4
- Changes - book.usegolang.com/14.4-diff

## 14.5 Creating new galleries

Writing the code necessary to create a new gallery involves touching lot of different areas of our application. We need to write code in our models package to handle writing data to the database, validations for that data, an HTML template used to render the gallery form, and we will need to add a new controller and actions to parse the form once it is submitted.

Rather than trying to do this all at once we are going to break it into four steps:

- The first thing we are going to do is write a working GalleryService implementation that allows us to insert galleries into our database.
- Once we have a working GalleryService implementation we will focus on creating the galleries controller and a view to render the gallery form.
- After that we will write the code to parse the gallery form and use that data to create a new gallery.
- Finally we will add validations to our gallery service so we can ensure we are only saving valid data to the database.

### 14.5.1 Implementing the gallery service

The layers used in the gallery service are going to match the ones used in the user service. We will have a galleryService that implements the GalleryDB interface, a galleryValidator for validations, and a galleryGorm for interacting with our database. We already have the galleryGorm, so let's start off by adding the galleryService and galleryValidator.

```bash
atom models/galleries.go
```

```go
type galleryService struct {
  GalleryDB
}

type galleryValidator struct {
  GalleryDB
}
```

After that we are going to ensure that our galleryGorm always implements our GalleryDB interface.

```go
var GalleryDB = &galleryGorm()
```

We haven't implemented the galleryGorm's Create method yet, so we can add that. This source code is nearly identical to the code used in userorm's Create method because GORM uses the resource we are saving to determine which table to insert into.

```go
func (gg *galleryGorm) Create(gallery *Gallery) error {
  return gg.Create(gallery).Error
}
```

It is also handy to have a way to construct a GalleryService with each of these layers in place, so we are going to add a NewGalleryService function as well.

```go
func NewGalleryService(db *gorm.DB) GalleryService {
  return &GalleryService{
    GalleryDB: &galleryValidator{
      GalleryDB: &galleryGorm{
        db: db,
      },
    },
  }
}
```

We can then update our NewServices function to use the NewGalleryService function.

```bash
atom models/services.go
```

```go
func NewServices(connectionInfo string) (*Services, error) {
  db, err := gorm.Open("postgres", connectionInfo)
  if err != nil {
    return nil, err
  }
  db.LogMode(true)
  return &Services(
    User: NewUserService(db),
    Gallery: NewGalleryService(db),
    db,
    nil
  )
}
```

With that we have a working gallery service and can insert new galleries into our database's galleries table with the Create method we implemented. We don't validate the data yet, but we can wait to do that until we implement the controller and actions needed to render and process a new gallery form.

# Source code

- Completed - book.usegolang.com/14.5.1
- Changes - book.usegolang.com/14.5.1-diff

## 14.5.2 The galleries controller

In this section we are going to introduce the galleries controller, along with a New view used to render the new gallery form. We will look at the source code to process the form in the next section - for now we just want to render it and get our controller setup.

We are going to start by creating the template for our view, which means we need to create a directory to store our gallery views and then create a template file there.

```bash
$ mkdir views/galleries
$ atom views/galleries/new.gohtml
```

Inside the template we are going to define a "yield" template like we normally do, and in it we will render the form much like we did for the sign up page.

```html
{{define "yield"}}
<div class="row">
  <div class="col-md-6 col-md-offset-3">
    <div class="panel panel-primary">
      <div class="panel-heading">
        <h3 class="panel-title">Create a gallery</h3>
      </div>
      <div class="panel-body">
        {template "galleryForm"}
      </div>
    </div>
  </div>
</div>
{{end}}

{{define "galleryForm"}}
<form action="/galleries" method="POST">
  <div class="form-group">
    <label for="title">Title</label>
    <input type="text" name="title" class="form-control" id="title" placeholder="What is the title?" />
  </div>
  <button type="submit" class="btn btn-primary">Create</button>
</form>
{{end}}
```

Our form needs a single input field for the title of the gallery, and we will use the 'title' name for that field. Aside from the rest of data about our gallery will be derived from the currently logged in (the UserID field) or set automatically by GORM in the database (ID, CreatedAt, etc.).

When we submit the form we will send it to the /galleries path which we will setup in our router in the next section, and we will do this via the POST method.

Next we need a controller to contain this view and help us render it. We will
