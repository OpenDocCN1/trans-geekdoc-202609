# 3.1. ROUTING WITH IF/ELSE STATEMENTS

Once we have the path we use it to determine what page to render. When the user is visiting the root path (/) we return our Welcome page. If the user is visiting our contact page (/contact) we return a page with information on how to contact.

If neither of these criteria are met, we write the 404 HTTP status code and then write an error message to the response writer. The NotFound variable is really just a constant representing the HTTP status code 404, and the WriteHeader method is one way to write HTTP status codes in Go.

> Box 3.3. Exporting common constants

As stated above, http.StatusNotFound is really just a constant that represents the 404 status code. This isn't actually necessary, and you could replace it with 404 in your code, but constants StatusNotFound are often exported by packages to make code easier to read and maintain.

# Source code

The links below have the completed source code and a diff of all the code changed in this section.

+   - Completed - book.usegolang.com/3.1

+   - Changes - book.usegolang.com/3.1-diff