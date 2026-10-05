# 15.2. PROCESSING IMAGE UPLOADS

```
// If we can't parse the form just render an error alert on the
// edit gallery page.
vd.SetAlert(err)
g.EditView.Render(w, r, vd)
return

```

Note: Our current code will have a bug where new images won't be added to the gallery, so when we render the gallery page again we won't see newly uploaded images unless we navigate back to the edit page and reload. We will address this bug in the next two chapters.

After this we would like to iterate over all the uploaded files and store them somewhere, so we need to create a directory to store our files. Rather than keeping all of our images in a single directory, we are going to create one for each gallery.

Having a unique folder for each gallery will make it easier for us to keep all of our images without having to worry about filename collisions. It will also make it easier to find all of the images for a specific gallery; all we would need to look up all the images in that gallery's directory.

In order to create a directory we will be using the MkdirAll function⁴, which is provided by the os package in the standard library. This function will create all of the folders in a path, meaning that if we wanted to create the following folders:

```
folder-a/nested-folder-b/nested-further-c
```

The MkdirAll function would create any of these folders that do not exist. If you are familiar with Linux at all, this is similar to using mkdir -p. 

MkdirAll also requires a FileMode, which is basically just a set of permissions for the directory. We will be using 0755, which gives the current user

> ⁴https://golang.org/pkg/os/#MkdirAll