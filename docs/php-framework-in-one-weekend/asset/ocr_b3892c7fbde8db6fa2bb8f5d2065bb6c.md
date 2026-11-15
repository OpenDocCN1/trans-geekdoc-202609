# # Chapter 10

Reuse

At the moment our framework is not very useful because it’s tied very closely to the example app we’ve been building. The point of building a framework is to have a collection of reusable code. We should be able to include this in a project when we want to do something similar, to save us having to do all the ground work again. In order to be able to do that we need to make our code as reusable as possible.

Up until now, we have put all our PHP code into the srcfolder. We also have PHP code, managed by Composer, in the vendorfolder. Eventually, we could make our framework a separate project and include it via Composer, but for now we will store it in a separate folder in our project. This will allow us to identify and separate out the reusable bits of our framework.

Create a folder called lib/weekendand move all the code that is currently in the srcfolder into this new location. If you try to access the application now you will get an error, like: “Uncaught Error: Class Weekend\App not found”. We need to tell Composer that we’ve move the code for the namespace Weekendand update it’s autoloader. Edit the autoload section of composer.jsonas per listing 10.1. Notice how we also add our srcfolder to the autoloader config so it can find our site’s code. In this example, I’m not using a namespace for my site-specific code.

```
19 "autoload":{
20 "psr-4":{
21 "Weekend\": "lib/weekend",
22 "": "src/"
23 }
24 }
```

# Listing 10.1: composer.json

Use Composer’s update or dump-autoload commands to recreate the autoloader. You should now find that the site is working again (assuming you still have PHP’s built-in webserver running).

We can now put our site-specifc code into the src folder. First, move the both of the controllers back into srcas they are specific to this site. This creates an new error, as the dependency injection container can no longer find them. To get around this we add a services.ymlfiletothe srcfolder for site-specific configuration. Refer to 10.2 to see how we update the constructor in Appso that it can find our extra configuration. Listing 10.3 shows the new file with the additional configuration.

Notice that we are loading the services.ymlfile that is local to the Appinto the dependency injection container first. This allows us to specify the dependencies that are core to our framework. We then load a second services.ymlConfiguration from the srcfolder. This allows our app to supply additional configuration, such as site-specific controllers, to the dependency injection container. This is a useful mechanism as it will also allow us to