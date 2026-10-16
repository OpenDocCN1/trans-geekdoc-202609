This test has forced us to actually look at the request's URL and make a decision. So whilst in our heads, we may have been worrying about player stores and interfaces the next logical step actually seems to be about *routing*.

If we had started with the store code the amount of changes we'd have to do would be very large compared to this. **This is a smaller step towards our final goal and was driven by tests.**

We're resisting the temptation to use any routing libraries right now, just the smallest step to get our test passing.

`r.URL.Path` returns the path of the request which we can then use `strings.TrimPrefix` to trim away `/players/` to get the requested player. It's not very robust but will do the trick for now.

# Refactor

We can simplify the `PlayerServer` by separating out the score retrieval into a function

```
//server.go
func PlayerServer(w http.ResponseWriter, r *http.Request) {
    player := strings.TrimPrefix(r.URL.Path, "/players/")

    fmt.Fprint(w, GetPlayerScore(player))
}

func GetPlayerScore(name string) string {
    if name == "Pepper" {
        return "20"
    }

    if name == "Floyd" {
        return "10"
    }
}
```