Chapter 13.3.

# Registering a User

Now that we’ve laid the groundwork, let’s start putting it to use by creating a new API endpoint to manage the process of registering (or *signing up*) a new user.

| Method | URL Pattern | Handler | Action |
|---|---|---|---|
| GET | /v1/healthcheck | healthcheckHandler | Show application information |
| GET | /v1/movies | listMoviesHandler | Show the details of all movies |
| POST | /v1/movies | createMovieHandler | Create a new movie |
| GET | /v1/movies/:id | showMovieHandler | Show the details of a specific movie |
| PATCH | /v1/movies/:id | updateMovieHandler | Update the details of a specific movie |
| DELETE | /v1/movies/:id | deleteMovieHandler | Delete a specific movie |
| POST | /v1/users | registerUserHandler | Register a new user |

When a client calls this new `POST /v1/users` endpoint, we will expect them to provide the following details for the new user in a JSON request body. Similar to this: