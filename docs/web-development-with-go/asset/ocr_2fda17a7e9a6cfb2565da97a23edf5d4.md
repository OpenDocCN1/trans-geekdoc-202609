# # Chapter 15

# # Adding images to galleries

Next on our agenda adding images to our galleries. This will entail adding new forms, handler functions to process those forms, and even adding a new service to our models package.

What makes the image resource unique is that it will give us a chance to look at a resource that doesn't necessarily map to an item in our database, but instead maps to an images stored on our hard drive (or possibly another service like Amazon S3 in the future). Many developers, even experienced ones, allow themselves to start believing that each model maps directly to an item in the database because this is often the case. While models will often have some data, even if just metadata, stored in the database, you can introduce a new model to an application that doesn't interact with the database at all.

In this chapter we are going to be doing just - adding an image resource that isn't persisted in our database at all. Instead, we will be storing images uploaded by end users on our hard drive and learning how to lookup and serve those images by interacting directly with our file system.