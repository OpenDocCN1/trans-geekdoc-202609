+   - We have two applications, a command line application and a web server.
+   - Both these applications rely on a `PlayerStore` to record winners
+   - The web server can also display a league table of who is winning the most games
+   - The command line app helps players play a game of poker by tracking what the current blind value is.

# time.Afterfunc

A very handy way of scheduling a function call after a specific duration. It is well worth investing time looking at the documentation for time as it has a lot of time saving functions and methods for you to work with.

Some of my favourites are

+   - `time.After(duration)` returns a `chan Time` when the duration has expired. So if you wish to do something *after* a specific time, this can help.
+   - `time.NewTicker(duration)` returns a `Ticker` which is similar to the above in that it returns a channel but this one "ticks" every duration, rather than just once. This is very handy if you want to execute some code every `N duration`.

# More examples of good separation of concerns

*Generally* it is good practice to separate the responsibilities of dealing with user input and responses away from domain code. You see that here in our command line application and also our web server.

Our tests got messy. We had too many assertions (check this input, schedules these alerts, etc) and too many dependencies. We could visually see it was cluttered; it is **so important to listen to your tests**.