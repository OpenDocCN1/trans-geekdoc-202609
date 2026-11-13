```
print "<br />Checkout code goes here<br />";
}
function getAttribute($xml, $name)
{
foreach($xml->attributes() as $key=>$val)
{
if($key == $name)
{
return (string)$val;
}
}
return false;
}
?>
```

The example is now complete; it is just a matter of placing the PHP on an active Web server. From this point you can extend the example to have multiple categories, products, and images. Realistically, building the application in a class format offers greater expandability, but don't just take my word for it. Experiment and extend the example.

# Using PHP and Flash to Build an Amazon Search Application

Amazon offers a very powerful set of tools designed to work with its site data. This section covers the building of a search application using Amazon.com as the data source. This example uses the ECS (Amazon E-Commerce Service), which provides direct access to Amazon's amazing searching and inventory system.

In order to use the ECS you need to have a valid Amazon access ID, which is provided when you create a developer's account. This registration process is quick and free; all you need is a valid e-mail address and an active account.

# Using the Amazon Web Service

To get started with creating a developers account, visit the Amazon Web Service (AWS) page at www.amazon.com/gp/aws/landing.html.

> Be sure to activate the account via e-mail before you begin to use it.

The AWS is set up to be accessed from different mediums. The format used for this example is Representational State Transfer (REST), which is basically a formatted URL with all of the necessary information provided in GET format.