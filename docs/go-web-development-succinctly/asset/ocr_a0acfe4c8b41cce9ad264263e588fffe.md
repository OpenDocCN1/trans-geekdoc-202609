```
package main
\import (
    "net/http"
    "strconv"
    "time"
)

func CheckLastVisit(w http.ResponseWriter, r *http.Request) {
    c, err := r.Cookie("lastvisit") //
    expiry := time.Now().AddDate(0, 0, 1)

    cookie := &http.Cookie{
        Name: "lastvisit",
        Expires: expiry,
        Value: strconv.FormatInt(time.Now().Unix(), 10),
    }
    http.SetCookie(w, cookie)

    if err != nil {
        w.Write([]byte("Welcome to the site!"))
    } else {
        lasttime, _ := strconv.ParseInt(c.Value, 10, 0)
        html := "Welcome! You last visited at: " +
        html = html + time.Unix(lasttime, 0).Format("15:04:05")
        w.Write([]byte(html))
    }
}

func main() {
    http.HandleFunc("/", CheckLastVisit)
    http.ListenAndServe(":8999", nil)
}
```

The first line of code in the handler tries to drop the cookie to the user's browser. If it succs, it records the current time in the cookie's **Value** field and displays a "Welcome to the site!" message. If there is an error, this will occur because the cookie already exists, which means all it do is update the time in the **Value** field and display it to users as the time they last visited.

If we run the application and visit the root of the application, we'll see the message in Figure 30.