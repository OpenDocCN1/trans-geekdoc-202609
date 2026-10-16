```
server := NewPlayerServer(&StubPlayerStore{})

request := newGameRequest()
response := httptest.NewRecorder()

server.ServeHTTP(response, request)

assertStatus(t, response, http.StatusOK)
})
}
```

You'll also notice I changed `assertStatus` to accept `response` rather than `response.Code` as I feel it reads better.

Now we need to make the endpoint return some HTML, here it is

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Let's play poker</title>
</head>
<body>
<section id="game">
    <div id="declare-winner">
        <label for="winner">Winner</label>
        <input type="text" id="winner"/>
        <button id="winner-button">Declare winner</button>
    </div>
</section>
</body>
<script type="application/javascript">
    const submitWinnerButton = document.getElementById('winner-k
    const winnerInput = document.getElementById('winner')
    if (window['WebSocket']) {
        const conn = new WebSocket('ws://' + document.location.r
    submitWinnerButton.onclick = event => {
```