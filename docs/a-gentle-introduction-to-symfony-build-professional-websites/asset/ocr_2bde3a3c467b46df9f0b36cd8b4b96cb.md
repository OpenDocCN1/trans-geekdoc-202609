# Where To Register Listeners?

Event listeners need to be registered early in the life of a symfony request. In practice, the right place to register event listeners is in the application configuration class. This class has a reference to the event dispatcher that you can use in the configure() method. Listing 17-6 shows how to register a listener on one of the rest_request events of the above examples.

Listing 17-6 - Registering a Listener in the Application Configuration Class, in apps/frontend/config/ApplicationConfiguration.class.php

```
class frontendConfiguration extends sfApplicationConfiguration
{
    public function configure()
    {
        // ...

        $this->dispatcher->connect('rest_request.method_not_found',
        array('sfRestRequestExtension', 'listenToMethodNotFound'));
    }
}
```

Plug-ins (see below) can register their own event listeners. They should do it in the plug-in's config/config.php script, which is executed during application initialization and offers access to the event dispatcher through $this->dispatcher.

# Factories

A factory is the definition of a class for a certain task. Symfony relies on factories for its core features such as the controller and session capabilities. For instance, when the framework needs to create a new request object, it searches in the factory definition for the name of the class to use for that purpose. The default factory definition for requests is sfWebRequest, so symfony creates an object of this class in order to deal with requests. The great advantage of using a factory definition is that it is very easy to alter the core features of the framework: Just change the factory definition, and symfony will use your custom request class instead of its own.

The factory definitions are stored in the factories.yml configuration file. Listing 17-7 shows the default factory definition file. Each definition is made of the name of an autoloaded class and (optionally) a set of parameters. For instance, the session storage factory (set under the storage: key) uses a session_name parameter to name the cookie created on the client computer to allow persistent sessions.

Listing 17-7 - Default Factories File, in frontend/config/factories.yml

```
- prod:
    logger:
      class: sfNoLogger
      param:
        level: err
        loggers: ~

test:
  storage:
    class: sfSessionTestStorage
    param:
      session_path: %SF_TEST_CACHE_DIR%/sessions
```