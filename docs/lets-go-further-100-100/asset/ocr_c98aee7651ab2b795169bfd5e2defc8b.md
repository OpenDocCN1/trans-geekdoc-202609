Chapter 4.

# Parsing JSON Requests

So far we’ve been looking at how to create and send JSON responses from our API, but in this next section of the book we’re going to explore things from the other side and discuss how to *read and parse JSON requests* from clients.

To help demonstrate this, we’re going to start work on the `POST /v1/movies` endpoint and `createMovieHandler` that we set up earlier.

| Method | URL Pattern | Handler | Action |
|---|---|---|---|
| GET | /v1/healthcheck | healthcheckHandler | Show application information |
| POST | /v1/movies | createMovieHandler | Create a new movie |
| GET | /v1/movies/:id | showMovieHandler | Show the details of a specific movie |

When a client calls this endpoint, we will expect them to provide a JSON request body containing data for the movie they want to create in our system. So, for example, if a client wanted to add a record for the movie *Moana* to our API, they would send a request body similar to this: