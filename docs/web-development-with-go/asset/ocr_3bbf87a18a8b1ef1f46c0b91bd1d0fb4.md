# 13.8. RECOVERING FROM VIEW RENDERING ERRORS

Putting that all together, our Render method should look like the shown below.

```
import (
    "bytes"
    "io"
)

func (v *View) Render(w http.ResponseWriter, data interface{}) {
    w.Header().Set("Content-Type", "text/html")
    switch data.(type) {
    case Data:
        // do nothing
    default:
        data = Data{
            Yield: data.data,
        }
    }
    var buf bytes.Buffer
    err := v.Template.ExecuteTemplate(&buf, v.Layout, data)
    if err != nil {
        http.Error(w, "Something went wrong. If the problem " +
            "persists, please email support@lenslocked.com",
            http.StatusInternalServerError)
        return
    }
    io.Copy(w, &buf)
}
```

After finishing the Render method we need to update any code that expected it to return an error. We will start off by updating the ServeHTTP method.

```
func (v *View) ServeHTTP(w http.ResponseWriter, r *http.Request) {
    v.Render(w, nil)
}
```

Next is the New method in the users controller.

```
$ atom controllers/users.go
```