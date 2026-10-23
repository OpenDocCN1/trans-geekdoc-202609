```
// Include the metadata in the response envelope.
    err = app.writeJSON(w, http.StatusOK, envelope{"movies": movies,
"metadata": metadata}, nil)
    if err != nil {
        app.serverErrorResponse(w, r, err)
    }
}
```

Feel free to restart the API and try out this new functionality by making some different requests to the GET /v1/movies endpoint. You should find that the correct pagination metadata is now included in the response. For example:

```
$ curl "localhost:4000/v1/movies?page=1&page_size=2"
{
    "metadata": {
        "current_page": 1,
        "page_size": 2,
        "first_page": 1,
        "last_page": 2,
        "total_records": 3
    },
    "movies": [
        {
            "id": 1,
            "title": "Moana",
            "year": 2015,
            "runtime": "107 mins",
            "genres": [
                "animation",
                "adventure"
            ],
            "version": 1
```