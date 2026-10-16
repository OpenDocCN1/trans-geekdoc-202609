when you use it with a `PlayerServer` you should get the following responses.

# Run the application

Now our tests are passing the last thing we need to do to complete this refactor is to check if our application is working. The program should start up but you'll get a horrible response if you try and hit the server at http://localhost:5000/players/Pepper.

The reason for this is that we have not passed in a `PlayerStore`.

We'll need to make an implementation of one, but that's difficult right now as we're not storing any meaningful data so it'll have to be hard-coded for the time being.

```
//main.go
type InMemoryPlayerStore struct{}

func (i *InMemoryPlayerStore) GetPlayerScore(name string) int {
    return 123
}

func main() {
    server := &PlayerServer{&InMemoryPlayerStore{}}
    log.Fatal(http.ListenAndServe(":5000", server))
}
```

If you run `go build` again and hit the same URL you should get "123". Not great, but until we store data that's the best we can do. It also didn't feel great that our main application was starting up but not actually working. We had to manually test to see the problem.

We have a few options as to what to do next

+   - Handle the scenario where the player doesn't exist
+   - Handle the `POST /players/{name}` scenario