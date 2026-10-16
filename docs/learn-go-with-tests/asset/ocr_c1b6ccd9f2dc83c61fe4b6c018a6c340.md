```
}
func (p *PlayerServer) game(w http.ResponseWriter, r *http.Reque
    p.template.Execute(w, nil)
}
```

By changing the signature of NewPlayerServer we now have compilation problems. Try and fix them yourself or refer to the source code if you struggle.

For the test code I made a helper called mustMakePlayerServer(t *testing.T, store PlayerStore) *PlayerServer so that I could hide the error noise away from the tests.

```
func mustMakePlayerServer(t *testing.T, store PlayerStore) *Play
    server, err := NewPlayerServer(store)
    if err != nil {
        t.Fatal("problem creating player server", err)
    }
    return server
}
```

Similarly, I created another helper mustDialWS so that I could hide nasty error noise when creating the WebSocket connection.

```
func mustDialWS(t *testing.T, url string) *websocket.Conn {
    ws, _, err := websocket.DefaultDialer.Dial(url, nil)

    if err != nil {
        t.Fatalf("could not open a ws connection on %s %v", url,
    }

    return ws
}
```

Finally, in our test code we can create a helper to tidy up sending messages