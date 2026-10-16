
associated with the prefix key in the JSON configuration and assign it to the struct’s Prefix field. The RestrictPrefix struct also has a logger field so you can log events, as necessary.

Your module needs to register itself with Caddy upon initialization.

The caddy.RegisterModule function accepts any object that implements the caddy.Module interface. For that, you add the CaddyModule method to return information to Caddy about your module. Caddy requires an ID for each module. Since you’re creating an HTTP middleware handler, you’ll use the ID http.handler.restrict_prefix, where restrict_prefix is the unique name of your module. Caddy also expects a function that can create a new instance of your module.

Now that you can register your module with Caddy, let’s add more functionality so you can retrieve the logger from Caddy and validate your module’s settings. Listing 10-6 picks up where we left off.

*--snip--*

// Provision a Zap logger to RestrictPrefix.

func (p *RestrictPrefix) 1Provision(ctx caddy.Context) error {
	p.logger = 2ctx.Logger(p)
	return nil
}

// Validate the prefix from the module's configuration, setting the default prefix "." if necessary.

func (p *RestrictPrefix) 3Validate() error {
	if p.Prefix == "" {
		p.Prefix = "."
	}
	return nil
}

*Listing 10-6: Implementing various Caddy interfaces*

You add the Provision method 1 to your struct. Caddy will recognize that your module implements the caddy.Provisioner interface and call this method. You can then retrieve the logger from the given caddy.Context 2.

Likewise, Caddy will call your module’s Validate method 3 since it implements the caddy.Validator interface. You can use this method to make sure all required settings have been unmarshaled from the configuration into your module. If anything goes wrong, you can return an error and Caddy will complain on your behalf. In this example, you’re using this method to set the default prefix if one was not provided in the configuration.

You’re almost done. The last piece of the puzzle is the middleware implementation itself. Listing 10-7 rounds out your module’s implementation by adding support for the caddyhttp.MiddlewareHandler interface.

*--snip--*

// ServeHTTP implements the caddyhttp.MiddlewareHandler interface.

func (p RestrictPrefix) ServeHTTP(w http.ResponseWriter, r *http.Request, next caddyhttp.Handler) error {
	for _, part := range strings.Split(r.URL.Path, "/") {
		if strings.HasPrefix(part, p.Prefix) {
			http.Error(w, "Not Found", http.StatusNotFound)
			if p.logger != nil {
				p.logger.Debug(fmt.Sprintf("restricted prefix: %q in %s", part, r.URL.Path))
			}
			return nil
		}
	}
	return 4next.ServeHTTP(w, r)
}

var (
	_ caddy.Provisioner = (*RestrictPrefix)(nil)
	_ caddy.Validator = (*RestrictPrefix)(nil)
	_ caddyhttp.MiddlewareHandler = (*RestrictPrefix)(nil)
)

*Listing 10-7: Implementing the MiddlewareHandler interface*

The logic is almost identical to the middleware from the preceding chapter. You loop through the URL path components, checking each one for the prefix 1. If you find a match, you respond with a 404 Not Found status 2 and log the occurrence for debugging purposes 3. If everything checks out, you pass control onto the next handler in the chain 4.

It’s a good practice to guard against interface changes by explicitly making sure your module implements the expected interfaces 5. If one of these interfaces happens to change in the future (for example, if you add a new method), these interface guards will cause compilation to fail, giving you an early warning that you need to adapt your code.

The final steps are to tidy up your module’s dependencies and publish it:

$ **go mod tidy**

go: finding module for package github.com/caddyserver/caddy/v2

go: finding module for package github.com/caddyserver/caddy/v2/modules/

caddyhttp

go: finding module for package go.uber.org/zap

go: found github.com/caddyserver/caddy/v2 in github.com/caddyserver/caddy/v2

v2.0.0

go: found go.uber.org/zap in go.uber.org/zap v1.15.0

go: downloading github.com/golang/mock v1.4.1

go: downloading github.com/onsi/gomega v1.8.1

go: downloading github.com/smallstep/assert v0.0.0-20200103212524-b99dc1097b15

go: downloading github.com/onsi/ginkgo v1.11.0

go: downloading github.com/imdario/mergo v0.3.7

go: downloading github.com/chzyer/test v0.0.0-20180213035817-a1ea475d72b1

go: downloading github.com/golang/glog v0.0.0-20160126235308-23def4e6c14b

go: downloading github.com/alangpierce/go-forceexport v0.0.0-20160317203124-8f1d6941cd75

go: downloading github.com/chzyer/logex v1.1.10

go: downloading github.com/hpcloud/tail v1.0.0

go: downloading gopkg.in/tomb.v1 v1.0.0-20141024135613-dd632973f1e7

go: downloading gopkg.in/fsnotify.v1 v1.4.7

Publish your module to GitHub or a similar version-control system supported by go get.

**230** Chapter 10

 ***Injecting Your Module into Caddy***

The module and adapter you wrote are both self-registering. All you need to do to include their functionality in Caddy is to import them at build time.

To do that, you need to compile Caddy from source. Start by making a directory for your build:

$ **mkdir caddy**

$ **cd caddy**

Building Caddy from source code requires a small amount of boiler-plate code, to which you’ll include your modules. Your modules register themselves with Caddy as a side effect of the import. Create a new file named *main.go* and add the code from Listing 10-8 into it.

package main

import (
	cmd "github.com/caddyserver/caddy/v2/cmd"
	_ "github.com/caddyserver/caddy/v2/modules/standard"
	_ "github.com/awoodbeck/caddy-restrict-prefix"
	_ "github.com/awoodbeck/caddy-toml-adapter"
)

func main() {
	cmd.Main()
}

*Listing 10-8: Injecting custom modules into Caddy*

First, you import the Caddy command module 1 into your build. This has the Main function that starts the caddy server. Then, you import the standard modules 2 that you’ll find in Caddy’s binary distribution. Finally, you include your restrict prefix module 3 and your TOML configuration adapter 4.

All that’s left to do now is initialize the caddy module and build it:

$ **go mod init caddy**

$ **go build**

At this point, you should have a binary named caddy in the current directory. You can verify that it has your custom imports by looking for them in the caddy binary’s list of modules. The following command is specific to Linux and macOS:

$ **./caddy list-modules | grep "toml\|restrict_prefix"**

caddy.adapters.toml

http.handlers.restrict_prefix

Caddy: A Contemporary Web Server **231**

For my Windows friends, run this command instead:

\> **caddy list-modules | findstr "toml restrict_prefix"**

caddy.adapters.toml

http.handlers.restrict_prefix

The caddy binary you built can read its configuration from TOML files and deny clients access to resources whose path includes a given prefix.

**Reverse-Proxying Requests to a Backend Web Service**

You now have all the building blocks to create something meaningful in Caddy. Let’s put everything you’ve learned together by configuring Caddy to reverse-proxy requests to a backend web service and serve up static files on behalf of the backend web service. You’ll create two endpoints in Caddy.

The first endpoint will serve up only static content from Caddy’s file server, showing Caddy’s static file-serving abilities. The second endpoint will reverse-proxy requests to a backend web service. This backend service will send the client HTML that will prompt the client to retrieve static files from Caddy, which will show how your web services can lean on Caddy to serve static content on their behalf.

Before you start building, you need to set up the proper directory structure.
