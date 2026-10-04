# Part IV: Not So Simple Applications

authorize.net returns a string of comma-separated values. The script will compare the results from the returned string against their known meanings (supplied by authorize.net). In the code that follows, the first element in the returned string is tested. If it has a value of 1, this method will return TRUE, meaning the transaction was successful.

```
$this->rvars = explode("", \$buffer);
$this->auth_result = \$this->rvars[0];
$this->error = \$this->rvars[3];
if ($this->auth_result != 1) ( return FALSE; )
return TRUE;
```

# CLASS ITEM

This class is at the base of the hierarchy.

Default Properties:

+   - none

Methods:

+   - Item. The class constructor. Takes two arguments: \$parent and \$atts. Calls the Base() method, assigning each element of the \$atts array to Object properties.

+   - Saveltem. Takes no arguments, assumes \$this->item_id exists. Will both update existing styles and create new ones as needed.

# CLASS CATEGORY

This is the first of the new classes that directly extend the classes created for the catalog application.

Class Name: CartCategory
Extends Category

Default Properties:

+   - none

Methods:

+   - CartCategory. The class constructor. Calls the Base() method, assigning each element of the \$atts array to Object properties.

+   - AddProduct. This method overwrites the AddProduct() method that is the parent (Category) class. It creates an array, called \$Products, each member of which is an object formed by calling the CartProducts() class.