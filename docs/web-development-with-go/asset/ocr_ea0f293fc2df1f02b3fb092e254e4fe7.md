# 14.11. IMPROVING THE USER EXPERIENCE AND CLEANING UP 537

up our code a bit.

While it might be possible to create new galleries, view them on the index page, and edit/delete them bar, none of this is very intuitive and we could improve our application a bit. For example, we don't even have a link to our galleries in the navigation bar, so without knowing the proper URL a user could never create a gallery. We also don't want to render the galleries link unless a user is signed in, as this page doesn't work for users who aren't signed in.

In this section we will update our code to:

+   1. Clean up a few redirects to make the process of creating, editing, and deleting galleries more intuitive for users.

+   2. Only render certain navigation bar links when a user is signed in.

# 14.11. Adding intuitive redirects

When a user creates or deletes a gallery we currently respond by redirecting them to the show gallery page, or rendering a text “success” message. While these two responses aren't invalid, they aren't very useful. Chances after a user creates a new gallery they aren't going to edit the gallery, but would instead like to upload new images and otherwise edit the gallery.

Likewise, when a user deletes a gallery a plain-text “success” message isn't very helpful. It would make more sense to redirect the user to the galleries index, allowing them to continue working with their remaining galleries.

In this section we will once again use gorilla/mux's named routes to make both of these happen. We will start by adding constants for our route names and then updating our router to use these names.