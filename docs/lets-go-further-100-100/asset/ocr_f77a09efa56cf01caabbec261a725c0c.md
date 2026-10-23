You should now get responses formatted like the ones below.

```
$ curl localhost:4000/v1/movies/123
{
    "movie": {
        "id": 123,
        "title": "Casablanca",
        "runtime": 102,
        "genres": [
            "drama",
            "romance",
            "war"
        ],
        "version":1
    }
}

$ curl localhost:4000/v1/healthcheck
{
    "status": "available",
    "system_info": {
        "environment": "development",
        "version": "1.0.0"
    }
}
```

# Additional Information

# Response structure