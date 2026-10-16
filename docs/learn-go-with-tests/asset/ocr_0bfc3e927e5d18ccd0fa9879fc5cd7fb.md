```
}
defer close()

server := poker.NewPlayerServer(store)

if err := http.ListenAndServe(":5000", server); err != nil {
    log.Fatalf("could not listen on port 5000 %v", err)
}
}
```

Notice the symmetry: despite being different user interfaces the setup is almost identical. This feels like good validation of our design so far. And notice also that `FileSystemPlayerStoreFromFile` returns a closing function, so we can close the underlying file once we are done using the Store.

# Wrapping up

# Package structure

This chapter meant we wanted to create two applications, re-using the domain code we've written so far. In order to do this, we needed to update our package structure so that we had separate folders for our respective `mains`.

By doing this we ran into integration problems due to unexported values so this further demonstrates the value of working in small "slices" and integrating often.

We learned how `mypackage_test` helps us create a testing environment which is the same experience for other packages integrating with your code, to help you catch integration problems and see how easy (or not!) your code is to work with.

# Reading user input