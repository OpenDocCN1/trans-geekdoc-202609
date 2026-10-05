# 16.6. CONFIGURING OUR APPLICATION

for production use. After adding a production flag to our application, we are going to use it to ensure that all production deployments of our application MUST use a JSON config file, otherwise they will panic when starting up.

We'll start updating our LoadConfig function to accept a parameter dictating whether or not the config is required.

```
$ atom config.go
```

```
func LoadConfig(configReq bool) Config {
    f, err := os.Open(".config")
    if err != nil {
        // This, and the new parameter, are the only changes
        // necessary.
        if configReq {
            panic(err)
        }
        fmt.Println("Using the default config...")
        return DefaultConfig()
    }
    // ... the rest remains unchanged
}
```

Now we need to create our flag, which means we need to take a moment to explore the flag⁷ package.

Note: Take a moment to actually look at the docs for the flag package. See you can discover how it works on your own. It may take some practice, but learning to use new packages with only their official docs is a valuable skill to have.

The flag package can be used to write applications that accept flags whenever they run. For instance, you might pass the -port=123 flag to dictate the port of an application if it had a flag defined like below.

> ⁷https://golang.org/pkg/flag/