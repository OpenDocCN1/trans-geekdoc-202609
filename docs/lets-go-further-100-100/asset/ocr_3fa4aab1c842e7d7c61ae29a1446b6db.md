Chapter 7.

# CRUD Operations

In this next section of the book we’re going to focus on building up the functionality for *creating, reading, updating and deleting* movies in our system.

We’ll make quite rapid progress over the next few chapters, and by the end of this section we’ll have the following API endpoints finished and working in full:

| Method | URL Pattern | Handler | Action |
|---|---|---|---|
| GET | /v1/healthcheck | healthcheckHandler | Show application information |
| POST | /v1/movies | createMovieHandler | Create a new movie |
| GET | /v1/movies/:id | showMovieHandler | Show the details of a specific movie |
| PUT | /v1/movies/:id | updateMovieHandler | Update the details of a specific movie |
| DELETE | /v1/movies/:id | deleteMovieHandler | Delete a specific movie |

In this section you’ll learn:

+   - How to create a *database model* which isolates all the logic for executing SQL queries against your database.