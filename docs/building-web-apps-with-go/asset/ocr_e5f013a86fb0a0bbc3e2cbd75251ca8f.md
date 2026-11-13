# # Deployment

Heroku makes deploying applications easy. It is a perfect platform for small to medium size web applications that are willing to sacrifice a little bit of flexibility in infrastructure to gain a fairly pain-free environment for deploying and maintaining web applications.

I am choosing to deploy our web application to Heroku for the sake of this tutorial because in my experience it has been the fastest way to get a web application up and running in no time. Remember that the focus of this tutorial is how to build web applications in Go and not getting caught up in all of the distraction of provisioning, configuring, deploying, and maintaining the machines that our Go code will be run on.

# # Getting setup

If you don't already have a Heroku account, sign up at id.heroku.com/signup. It's quick, easy and free.

Application management and configuration is done through the Heroku toolbelt, which is a free command line tool maintained by Heroku. We will be using it to create our application on Heroku. You can get it from toolbelt.heroku.com.

# # Changing the Code

To make sure the application from our last chapter will work on Heroku, we will need to make a few changes. Heroku gives us a `PORT` environment variable and expects our web application to bind to it. Let's start by importing the "os" package so we can grab that `PORT` environment variable:

```
import (
	"net/http"
	"os"

	"github.com/russross/blackfriday"
)
```

Next, we need to grab the `PORT` environment variable, check if it is set, and if it is we should bind to that instead of our hardcoded port (8080).