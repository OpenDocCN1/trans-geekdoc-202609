Our final requirement was to return an error if Racer takes longer than 10 seconds.

# Write the test first

```
t.Run("returns an error if a server doesn't respond within 10s",
    serverA := makeDelayedServer(11 * time.Second)
    serverB := makeDelayedServer(12 * time.Second)

    defer serverA.Close()
    defer serverB.Close()

    _, err := Racer(serverA.URL, serverB.URL)

    if err == nil {
        t.Error("expected an error but didn't get one")
    }
})
```

We've made our test servers take longer than 10s to return to exercise this scenario and we are expecting Racer to return two values now, the winning URL (which we ignore in this test with _) and an error.

# Try to run the test

```
./racer_test.go:37:10: assignment mismatch: 2 variables but 1 values
```

# Write the minimal amount of code for the test to run and check the failing test output