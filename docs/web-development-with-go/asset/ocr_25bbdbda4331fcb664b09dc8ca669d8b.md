# CHAPTER 14. CREATING THE GALLERY RESOURCE

# Source code

The links below have the completed source code and a diff of all the code changed in this section.

+   Completed - book.usegolang.com/14.5.3

+   Changes - book.usegolang.com/14.5.3-diff

# 14.5.4 Validating galleries

Just like validated users, we also need to validate our galleries before we store them in our database. Specifically, we want to validate that a UserID is always set so we know which user created each gallery, and we will also want to require a title.

We’ll start defining a type for our gallery validation functions along with a function to run them, just like we did with the user validations.

```
$ atom models/galleries.go

type galleryValFn func(*Gallery) error

func runGalleryValns(gallery *Gallery, fns ...galleryValFn) error {
	for _, fn := range fns {
		if err := fn(gallery); err != nil {
			return err
		}
		return nil
}
```

Now we can get started writing validation functions for our galleries, starting with one to to ensure a UserID is set.