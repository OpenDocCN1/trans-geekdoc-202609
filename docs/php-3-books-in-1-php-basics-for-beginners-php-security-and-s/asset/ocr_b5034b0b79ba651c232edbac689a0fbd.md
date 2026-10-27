```
```php
$template_body->display();
}
}
}
public function Footer()
{
require_once('views/show/templates/footer_template.html');
}
}
?>
```
```

As you can see, the Show feature's Display() class contains only three methods: Header(), Body(), and Footer(). All of the data from the data model that is required to present the customer with a restaurant carte is saved in the input variable $viewmodel, which is passed to the Body() method for our purposes because this is where all of the dynamic formatting would occur in our situation.

Now, we can use a model and controller to link everything together and display the carte. The controllers contain methods that directly correspond to the user-defined actions indicated in the URL; consequently, the action specified in the URL is really the name of the controller method to be invoked. Additionally, the URL specifies the caller's controller's name, which is a class containing the action (method). The controller's actions/methods are responsible for instantiating the proper model, which enables data to be delivered to the appropriate view.

The controller and its associated model should be saved in different directories as identical files. In this example, we'll display a controller named "show.PHP" in the controller's directory and a model named "show.PHP" in the model's directory, as we'll be displaying carte data.

# Controller

As the name implies, the Controller is in charge of communication between the application's main components. It acts as a "switchboard operator," relaying requests and answers between the model and the view. Our restaurant carte application's "Show" controller extends the BaseController class, which accepts actions from the Interpreter and executes them with the ExecuteAction() method. The BaseController class has a subclass called The "show" controller., which takes actions from the Interpreter and executes them using the ExecuteAction() method. Remember the URL command that was used to "show" the carte:

http://localhost/show/Display

The Interpreter runs this URL and executes that the Display() method of the Show controller class should be called, at which time it creates a Show class instance in /htdocs/controllers/show.PHP and calls the Display() method. The Display() method carries out three tasks. To begin, it creates a $viewmodel instance of the ShowModel that corresponds. Following that, it executes the $viewmodel object's Display() method. Finally, it uses the ReturnView() method of the BaseController to transmit the ShowModel's response to the