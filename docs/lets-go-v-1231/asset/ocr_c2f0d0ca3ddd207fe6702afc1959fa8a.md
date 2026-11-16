# Latest Snippets

| Title | Created | ID |
| :--- | :--- | :--- |
| The wren | 05 Apr 2022 at 16:21 | #6 |
| From time to time | 05 Apr 2022 at 14:59 | #5 |
| 0 snail | 05 Apr 2022 at 07:32 | #4 |
| First autumn morning | 05 Apr 2022 at 07:20 | #3 |
| Over the wintry forest | 05 Apr 2022 at 07:20 | #2 |
| An old silent pond | 05 Apr 2022 at 07:20 | #1 |

Feel free to have a play around with this, and try logging in and out until you’re confident that the navigation bar is being changed as you would expect.

# Restricting access

As it stands, we’re hiding the ‘Create snippet’ navigation link for any user that isn’t logged in. But an unauthenticated user could still create a new snippet by visiting the https://localhost:4000/snippet/create page directly.

Let’s fix that, so that if an unauthenticated user tries to visit any routes with the URL path /snippet/create they are redirected to /user/login instead.

The simplest way to do this is via some middleware. Open the cmd/web/middleware.go file and create a new requireAuthentication() middleware function, following the same pattern that we used earlier in the book: