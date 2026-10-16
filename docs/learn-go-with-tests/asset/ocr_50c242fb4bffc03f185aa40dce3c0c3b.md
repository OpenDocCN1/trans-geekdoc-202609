# Next lets assign it in our constructor

```
```
func NewPlayerServer(store PlayerStore, game Game) (*PlayerServe
    p := new(PlayerServer)

    tmpl, err := template.ParseFiles(htmlTemplatePath)

    if err != nil {
        return nil, fmt.Errorf("problem opening %s %v", htmlTemp
    }

    p.game = game

    // etc
}
```
```

Now we can use our Game within webSocket.

```
```
func (p *PlayerServer) webSocket(w http.ResponseWriter, r *http.
    conn, _ := wsUpgrader.Upgrade(w, r, nil)

    _, numberOfPlayersMsg, _ := conn.ReadMessage()
    numberOfPlayers, _ := strconv.Atoi(string(numberOfPlayersMsg)
    p.game.Start(numberOfPlayers, ioutil.Discard) //todo: Don't

    _, winner, _ := conn.ReadMessage()
    p.game.Finish(string(winner))
}
```
```

Hooray! The tests pass.

We are not going to send the blind messages anywhere just yet as we need to have a think about that. When we call game.Start we send in ioutil.Discard which will just discard any messages written to it.

For now start the web server up. You'll need to update the main.go to pass a Game to the PlayerServer