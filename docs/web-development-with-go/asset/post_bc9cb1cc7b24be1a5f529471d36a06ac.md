
# CHAPTER 16. DEPLOYING TO PRODUCTION

- https://pocketgophers/json-references/ - A list of many valuable Go + JSON articles that will likely address any questions you have when learning to encode and decode JSON data in Go

Now that we have a way to load a JSON config, we are going to update our main function to use it.

```go
func main() {
  cfg := LoadConfig()
  dbCfg := cfg.Database
  // the rest of this is unchanged
}
```

Try updating your config file to verify it works; change something obvious the port and restart your server. Check that it starts up on a new port and prints out a message with that port.

> Note: Remember you need to go run *.go instead of main.go

We have a working JSON config, but we still need to add one more thing - a flag dictating whether we are in production or development.

Wait a minute, isn't that a field in our config file?

Well, yes... technically it is, but what happens if we forget to provide a JSON config file in production? Our application will start up using the default config!

This is great for development, but in production we absolutely want to make sure we use a JSON config file, as our default values are unlikely to secure for production use.

## 16.6. CONFIGURING OUR APPLICATION

After adding a production flag to our application, we are going to use it to ensure that all production deployments of our application MUST use a JSON config file, otherwise they will panic when starting up.

We'll start updating our LoadConfig function to accept a parameter dictating whether or not the config is required.

```bash
$ atom config.go
```

```go
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

# CHAPTER 16. DEPLOYING TO PRODUCTION

```go
var port = flag.Int("port", 3000, "the port of the server")
```

If the port flag was provided, it would use whatever value you provided, otherwise it would default to 3000. The last part of the flag.Int function call is the help help message that is displayed when a user provides the -help flag. The flags package automatically sets this flag for us when we use it.

In our case we only need a single boolean flag dictating whether we are in production or not. Open up your main source file where we will be adding it.

```bash
$ atom main.go
```

This will need to be the first thing we run inside our main function, and we will also need to call the Parse function provided by the flag package to ensure our flags are all parsed correctly.

```go
func main() {
    boolPtr := flag.Bool("prod", false, "Provide this flag " +
    "in production. This ensures that a .config file is " +
    "provided before the application starts.")
    flag.Parse()
    //boolPtr is a pointer to a boolean, so we need to use
    //boolPtr to get the boolean value and parse it into our
    // LoadConfig function
    cfg := LoadConfig(boolPtr)
    dbCfg := cfg.Database

    // ... nothing else changes
}
```

We can provide the -help flag to our application to verify that our flag is being parsed correctly.

```bash
$ go run *.go --help
Usage of /var/.../exe/config:
-prod

Provide this flag in production. This ensures that a
  .config file is provided before the application starts.
```

## Box 16.4. Whats the deal with the "Usage of..." part?

The long "Usage of" string looks odd because go run will build a temporary binary and then execute it. go run doesn't interpret your code like python or ruby would, but instead build then runs it.

If you wanted to build a binary named app you could instead use the following commands:

```bash
$ go build -o app *.go
$ ./app --help
Usage of ..app:
-prod

Provide this flag in production. This ensures that a
  .config file is provided before the application starts.
```

Now when we want to start our application we can provide the -prod flag which ensures we load a .config JSON file. We can verify this by deleting or moving our .config file and trying to run our application with the prod flag.

```bash
$ mv .config unused.config
$ go run *.go -prod
panic: open .config: no such file or directory
```

# Source code

The links below are source code (Note: No links provided in source).

## 16.7. Setting up server

We are finally ready to setup! This will be split into five major steps:

1. Initializing the server
2. Installing PostgreSQL
3. Creating Caddy
4. Setting up the domain
5. Deploying the application

Each of these steps is detailed in the following sections.

## 16.7. SET UP A SERVER

In this section we will discuss how to set up the server. If you have a Digital Ocean account, you want to navigate to the droplet page. From here you want to select the following options:

| Setting | Values to select |
| --- | --- |
| Image | Under the "Distributions" tab select Ubuntu 16.04. If the version has a minor version number, eg 16.04.3, that should be fine. |
| Size | Under the "Standard" tab select the cheapest server. |
| Block storage | We won't need this feature. |
| Datacenter region | Pick whichever you prefer. The closest to your physical location is probably ideal, but if you plan to target customers in another region you may want to select differently. |
| Additional options | None of these are required for our app right now, and *might* be charged for a few of these (like backups), but I typically select the IPv6 and Monitoring options. |
| SSH keys | If you have any SSH keys set, these will enable you to login without a password but instead with your SSH key. This is by far the simplest option, but you may need to follow a tutorial explaining how to set this up (https://book.usegalong.com/do-ssh-tut). If you opt not to do this you will be emailed a password what is required to login to your server and will likely be required every time you deploy your server. |
| How many droplets? | We will only need |
| Hostname | Whatever you want. I often use something like the domain name I plan to use, eg "www.lenslocked.com" but anything is fine. |

Now if you want to use a domain name, we need to setup an “A” record map-

> *https://support.dnimple.com/articles/a-record/
