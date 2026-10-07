Putting a name on our spaces.

```
<?php
use Symfony\Component\Console\Application;
...
myApp = new Application();
```

There. Clarity has returned to our coding once more. The intent of the line $myApp = new Application(); is clear without requiring us to mentally parse the namespace path. This is because the use keyword imports that definition for us.

However, while we've solved the long class name problem, we've reintroduced the name collision problem again. Using the word “Application” as a class name isn't unique to the Symfony Console component, just like User it's a pretty popular choice. Indeed, there's every possibility that we might want to use the very same word ourselves.

```
<?php
namespace CompanyName\AppName;

use Symfony\Component\Console\Application;

class Application {
    private $app;

    public function __construct(Application $app) {
        $this->app = $app;
    }
}
myApp = new Application(new Application());
```

Even if PHP allowed you to do this, you would have a devil of a job trying to decipher what was supposed to be going on in there. All sense of clarity has been lost again because you could only assume that the author's intent here was to instantiate an instance of his own Application class by passing an instance of the Symfony