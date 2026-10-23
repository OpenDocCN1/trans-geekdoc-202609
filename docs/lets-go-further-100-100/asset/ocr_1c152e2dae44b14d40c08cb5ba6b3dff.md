```
package main

...

// Define an envelope type.
type envelope map[string]interface{}

// Change the data parameter to have the type envelope instead of
interface{}.
func (app *application) writeJSON(w http.ResponseWriter, status int, data envelope, headers http.Header) error {
    js, err := json.MarshalIndent(data, "", "\t")
    if err != nil {
        return err
    }

    js = append(js, '\n')

    for key, value := range headers {
        w.Header()[key] = value
    }

    w.Header().Set("Content-Type", "application/json")
    w.WriteHeader(status)
    w.Write(js)

    return nil
}
```

Then we need to update our showMovieHandler to create an instance of the envelope map containing the movie data, and pass this onwards to our writeJSON() helper instead of passing the movie data directly.

Like so: