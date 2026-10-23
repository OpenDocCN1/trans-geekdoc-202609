```
        return nil, ErrRecordNotFound
    default:
        return nil, err
    }
}

    return &movie, nil
}
...

```

If you restart the application and make a request to the GET `/v1/movies/:id` endpoint, you should find that the request hangs for 10 seconds before you finally get a successful response displaying the movie information. Similar to this:

```
$ curl -w '\nTime: %{time_total}s \n' localhost:4000/v1/movies/1
{
  "movie": {
    "id": 1,
    "title": "Moana",
    "year": 2015,
    "runtime": "107 mins",
    "genres": [
      "animation",
      "adventure"
    ],
    "version": 1
  }
}

Time: 10.013534s
```