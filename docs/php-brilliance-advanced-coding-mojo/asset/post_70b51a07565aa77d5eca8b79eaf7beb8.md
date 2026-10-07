
## Finding Closure.

When you write up the code for this particular method in one of your classes, you make the objects of this type callable. As a result, wherever you can employ a closure as a callback, you can substitute this for an object instance that also supports __invoke() method.

Whether you take this approach is up to you of course. If a closure on its own doesn't cut it for you, you can pass your own object instance to something like the array_walk() function.

```$php
$callback = new MegaArrayTransformer();
array_walk($_POST, $callback);
```

Although you'd probably still be better served by providing a closure that bridges the array_walk process with the MegaArrayTransformer anyway.

## Building your objects

Nevertheless, the notion of seeding existing objects with new, unnamed, methods can be quite an attractive proposition. Albeit in very restricted circumstances, the technique we're about to look at has only the one vaguely justifiable use case that I know of. If you do know of more, I'd be very keen to hear of them.

In an attempt to honour the correct definition of the Model-View-Controller pattern (MVC), it's the controller's job to ask for a model, which it then presents to the view to allow the view to update itself. The stop-start nature of http protocol makes it difficult to follow the pattern correctly, which has resulted in the view layer being “the bit that builds an html page for sending to the browser”. (Ignoring Ajax for the moment)

Nevertheless, we still have the opportunity to honour the first part of the process. For a GET request, your controller's going to go to the model layer (possibly via a service) and retrieve the model it needs to pass to the view.

In the event that our view is going to display data from multiple sources, this presents us with a bit of an issue.

It isn’t the controller’s job to retrieve that data from different model sources and mangle it together into a unit that the view can access. In spite of this, there are literally hundreds of examples presented across the web where this practice is shown as the correct way: the action method in the controller collects the data and then prepares it for the view.

We can illustrate this with a not-too-uncommon example.

Let’s say that we needed a page to display customer details, along with any orders that they had placed and the corresponding status of the invoices attached to those orders. Doing the wrong way might look like this.

```php
// In the controller
$customerDetails = $this->modelService->fetch('Customers', $customerId);
$orderDetails = $this->modelService->fetch('Orders', $customerId);

$orderIds = [];
foreach ($orderDetails as $order) {
  $orderIds[] = $order->OrderId();
}

$invoiceDetails = $this->modelService->fetch('Invoices', $orderIds);

$this->view->render(array(
  'customer' => $customerDetails,
  'orders' => $orderDetails,
  'invoices' => $invoiceDetails
));
```

I’m not saying for one moment that everybody does it this way but I have certainly seen this approach taken on a regular basis. The problem with having a controller method mangle model data into a view consumable unit like this is that we are inevitably setting ourselves up for code duplication. It’s a DRY violation waiting.

Why?

Our assumption here is that particular controller method will be the only way to trigger the rendering of this data. If this is truly the case, now and forever always, then we can get away with it.

But only until the credit controllers in the finance department make a request to have the same information emailed to them on a monthly basis. Head office wants to be able to grab this data as a json payload from an API call.

Consequently, it would make much more sense for the model layer to perform the data preparation and return a single usable unit that contains all of the relevant information. The question is, does this requirement warrant the creation of a whole new model object to carry only data to a rendering process?

That's not necessarily a question that we can answer in these pages. However, it doesn't prevent us from exploring some possible alternatives.

The first alternative is to go ahead and build a specific CustomerOrdersInvoices model object, which can be populated with the relevant data and passed back to the controller/API call/cron job. The problem with this approach is that we need a dedicated class for each unit of complex data. That potentially quite a lot of coding and really makes sense when we need to take advantage of a properly defined interface and the logical controls we can impose upon it. In a read-only scenario, that is less important since the when and how of rendering that data is not a responsibility of our model layer should be concerning itself with.

Another alternative to consider then is the ability to build up a dynamically created object classes instead of hard coded methods. This concept starts with an appropriately reusable skeleton class as this one

```php
class ViewData {
    private $methods = array();

    public function addMethod($methodName, Callable $func)
    {
        $this->methods[$methodName] = $func;
    }

    public function __call($methodName, $args)
    {
        if (is_callable($this->methods[$methodName])) {
            return call_user_func_array(
                $this->methods[$methodName],
                $args
            );
        }
    }
}
```

With such a skeleton object, we can load it up as many “public” methods as required. For our Customer/Orders/Invoices unit, we might employ some code that looks a little like.

```php
// Inside the model layer
$viewData = new ViewData();

$viewData->addMethod('getCustomerName', function() use ($customerModel) {
    return $customerModel->getName();
});

array_walk($orderDetails, function($order) use ($viewData, $invoiceCollection) {
    if ($order->getOrderId() === $order->getId()) {
        $viewData->setInvoice($order);
    }
});

$viewData->addMethod('getOrders', function() use ($orderDetails) {
    return $orderDetails;
});

return $viewData;
```

For brevity, I’ve left it to your imagination as we acquire the $customerModel, $orderDetails and $invoiceCollection variables. Also for brevity, we have closures here that return the original models. For a read only consumer the return statements could be fashioned into sending back scalar values or arrays quite readily.

“But isn’t that simply duplicating code anyway?”, I hear shout. We would certainly be right to question an approach that involves creating what are little than proxy methods. In the case of extracting the customer's information from the $customerModel instance, virtually every closure that we created would be one of proxies.

Fortunately, we don't have to duplicate the code at all. We can use reflection for simple return values that don't require the same sort of mangling as the array_walk() process conducted on the $orderDetails and $invoiceCollection objects.

Doing so lets us pluck existing methods from other objects and build our ViewData instance with them.

```php
$reflectedMethod = new ReflectionMethod($customerModel, 'getName');
$viewData->addMethod('getName', $reflectedMethod->getClosure($customerModel));
```

That's just two lines of code for every method that we wish to lift the $customerModel instance and add to our ViewData instance. The first line generates the reflected method, whereas the second line provides with an active closure scope bound to the original model.

In this way we can dynamically build our new object with methods drawn from a variety of source models. Since each closure retains its original scope, it behaves precisely as if we're invoking the method on the original object itself.

Without the need for processing the return data, we can simply cherry-pick the relevant getters from the models that we're working and present a purely “read only” composite object back to the controller.

In any case, once we've populated $viewData instance with the appropriate methods it can be returned to the controller and consequently passed to the view ready, willing and able to provide the elements of data required to complete the page.

It's the implementation of the magic __call() method allows this to pretend that it's a regular object.
