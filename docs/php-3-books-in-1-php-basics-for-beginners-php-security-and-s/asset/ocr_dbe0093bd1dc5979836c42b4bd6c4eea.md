```
require_once('views/add/templates/body_addcarteProduct.html');
}
public function Footer()
{
require_once('views/add/templates/footer_addcarteProduct.html');
}
}
?>
```

It's now only a matter of inserting references to our new model and controller to the index.PHP file:

```
<?PHP
ini_set('display_errors',1);
error_reporting(E_ALL);

//require the general classes
require("helperclasses/Interpreter.PHP");
require("helperclasses/BaseController.PHP");
require("helperclasses/Template.PHP");
require_once("helperclasses/Database.PHP");

//require the data model
require("models/CarteModel.PHP");

//require the model classes
require("models/show.PHP");
require("models/add.PHP");

//require the controller classes
require("controllers/show.PHP");
require("controllers/add.PHP");

//create the controller and execute the action
$interpreter = new Interpreter($_GET);
$controller = $interpreter->CreateController();

$controller->ExecuteAction();
?>
```

We can now add new carte Products to the database via the user interface. Furthermore, we'll need a way for the user to assign new carte Products to one or more available cartes, so let's create the markup for a page that does this:

```
<html>
<head>
<title>Assign Carte Products to Cartes</title>
</head>
<body>
<form method="POST" action="index.PHP/assign/Save">
<table>
<tr><td>Select a Single Carte Product:</td></tr>
<tr>
<td>
<select name="carteProductid">
<option value="{carteProductid}">{Productname}</option>
</select>
</td>
```