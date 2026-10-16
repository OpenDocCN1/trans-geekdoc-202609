
you moved this route before the reverse-proxy route, all requests would match it, and no requests would ever make their way to the reverse proxy.

Whenever you specify a route with no matches, make sure you put it at the end of your routes array, as you do here.

As with the file server in the preceding chapter, you want to protect against accidentally serving sensitive files prefixed with a period. Therefore, you include your restrict_prefix middleware 2 in the array of handlers before the file_server handler 3. You add more configuration options to serve files found in the *files* subdirectory 4 and return the *index.html* file 5 if the request didn’t specify a file.

***Checking Your Work***

Everything is in place. Start Caddy and verify that your configuration works as expected. Since some of the static files are images, I recommend you use a web browser to interact with Caddy while it runs on your computer.

Start Caddy by using the *caddy.toml* file and the *toml* adapter:

$ **./caddy start --config caddy.toml --adapter toml**

**236** Chapter 10

On Windows, the command looks like this:

\> **caddy start --config caddy.toml --adapter toml**

Now, run the backend web service:

$ **cd backend**

$ **go run backend.go**

Listening on localhost:8080 ...

Open your web browser and visit *http://localhost:2020/*. Caddy will send your request to the file server handler, which in turn will respond with the *index.html* file, since you didn’t indicate a specific file in the request. Your browser then asks Caddy for the *style.css* and *sage.svg* files to finish rendering the page. If everything succeeds, you should now be looking at a sage gopher.

Now, let’s test the reverse proxy to the backend web service. Visit *http://* *localhost:2020/backend*. This request matches the reverse-proxy route’s matcher, so the reverse-proxy handler should handle it, sending the request onto the backend service. The backend web service responds with HTML that instructs your browser to retrieve the *style.css* and *hiking.svg* files from Caddy, where the file server handler happily serves them up. You should now be looking at a hiking gopher rendered using HTML from the back-end web service and static files from Caddy.

If you copied the *files* subdirectory from this book’s source code repository, it should contain *./files/.secret* and *./files/.dir/secret* files. Your middleware should block access to both files. In other words, both *http://localhost:2020/* *files/.secret* and *http://localhost:2020/files/.dir/secret* will return a 404 Not Found status if you try to request them.

***Adding Automatic HTTPS***

Now let’s add Caddy’s key feature to your web server: automatic HTTPS.

I once used Caddy to stand up a website with full HTTPS support, using certificates trusted by all contemporary web browsers, in a matter of minutes. The server has been rock-solid ever since, happily rotating Let’s Encrypt keys every few months with no intervention on my part.

This isn’t to say I couldn’t replicate this functionality in my own Go-based web server; my time was simply best spent building services and leaving the web serving to Caddy. If Caddy lacked any functionality, I could add it as a module.

Caddy automatically enables TLS when it can determine what domain names you’ve configured it to serve. The *caddy.toml* configuration created in this chapter didn’t give Caddy enough information to determine which domain it was serving. Therefore, Caddy didn’t enable HTTPS for you. You told Caddy to bind to localhost, but that tells Caddy only what it’s listening to, not what domains it’s serving.

Caddy: A Contemporary Web Server **237**

The most common way to enable automatic HTTPS is by adding a host matcher to one of Caddy’s routes. Here’s an example matcher:

\[\[apps.http.servers.server.routes.match\]\]

host = [

'example.com',

]

This host matcher supplies enough information for Caddy to determine that it is serving the *example.com* domain. If Caddy doesn’t already have a valid certificate for *example.com* to enable HTTPS, it will go through the process of validating the domain with Let’s Encrypt and retrieving a certificate. Caddy will manage your certificate, automatically renewing it, as necessary.

Caddy’s file-server subcommand tells Caddy you want it to exclusively serve files over HTTP. The file-server’s --domain flag is enough information for Caddy to invoke its automatic HTTPS and allow you to serve files over HTTPS as well.

Caddy’s reverse-proxy subcommand allows you to put Caddy into a reverse-proxy-only mode, where it will send all incoming requests onto the socket address specified by the --to flag. Caddy will retrieve a TLS certificate and enable automatic HTTPS if you specify a hostname with the --from flag.

I encourage you to read more about Caddy’s automatic HTTPS in production environments at *https://caddyserver.com/docs/automatic-https*.

**N O T E** 

*Caddy defaults to using Let’s Encrypt as its certificate authority for non-localhost* *names and IP addresses. But Caddy supports its own internal certificate authority* *for enabling HTTPS over localhost, which you may want to do for testing purposes.*

*If you specify* localhost *as your hostname in the earlier settings to enable automatic* *HTTPS, Caddy will use its internal certificate authority for its TLS certificate. It* *will also try to install its root certificate in your operating system’s root certificate trust store, which is where your operating system keeps track of all root certificates* *it inherently trusts.*

**What You’ve Learned**

Caddy is a contemporary web server written in Go that offers security, per-formance, and extensibility through modules and configuration adapters.

Caddy can automatically use HTTPS through its integration with Let’s Encrypt, a nonprofit certificate authority that supplies free digital certificates. Together, Caddy and Let’s Encrypt allow you to stand up a web server with seamless HTTPS support.

Caddy uses JSON as its native configuration format, and it exposes an API on localhost port 2019 that allows you to post JSON to change its configuration. The configuration changes take immediate effect. But since JSON isn’t an ideal configuration format, Caddy makes use of configuration adapters. Configuration adapters translate configuration files from more configuration-friendly formats, like TOML, to JSON. If you don’t want to use JSON for your Caddy configuration or if you don’t find a configuration adapter that meets your needs, you can also write your own, as you did in this chapter.

You can also extend Caddy’s functionality with the use of modules. This chapter shows how to write a middleware module, compile it into Caddy, configure the module, and put it to effective use.

Finally, this chapter showed you how to integrate Caddy into your network architecture. You’ll often make Caddy the first server in your network, using it to receive client requests before sending the requests onto their final destinations. In this chapter, you configured an instance of Caddy to reverse-proxy client requests to your backend web service and serve static files on behalf of the backend web service. As a result, you kept your backend web service as simple as possible and saved it from having to manage its static content. Your backend web service can use Caddy for HTTPS support, caching, and file serving.

Now that you have some experience with Caddy, you should be able to determine whether your web services would do better when served by a comprehensive web server solution or a comparatively minimal net/http web server implementation. If you expect to make your web service available to the public, using a proven web server like Caddy at the edge of your application will free up time you can better spend on your backend web service.
