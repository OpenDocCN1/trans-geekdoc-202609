Our call to template.ParseFiles("game.html") will run on every GET /game which means we'll go to the file system on every request even though we have no need to re-parse the template. Let's refactor our code so that we parse the template once in NewPlayerServer instead. We'll have to make it so this function can now return an error in case we have problems fetching the template from disk or parsing it.

# Here's the relevant changes to PlayerServer

```
type PlayerServer struct {
    store PlayerStore
    http.Handler
    template *template.Template
}

const htmlTemplatePath = "game.html"

func NewPlayerServer(store PlayerStore) (*PlayerServer, error) {
    p := new(PlayerServer)

    tmpl, err := template.ParseFiles(htmlTemplatePath)

    if err != nil {
        return nil, fmt.Errorf("problem opening %s %v", htmlTemp
    }

    p.template = tmpl
    p.store = store

    router := http.NewServeMux()
    router.Handle("/league", http.HandlerFunc(p.leagueHandler))
    router.Handle("/players/", http.HandlerFunc(p.playersHandler
    router.Handle("/game", http.HandlerFunc(p.game))
    router.Handle("/ws", http.HandlerFunc(p.webSocket))

    p.Handler = router

    return p, nil
}
```