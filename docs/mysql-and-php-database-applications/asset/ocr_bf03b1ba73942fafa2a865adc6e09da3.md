# Part IV: Not So Simple Applications

Notice that the Product object contains and array of related styles. That array, named styles, contains Style objects. So at some point in this class, you can expect some code that will manufacture this structure. Specifically, somewhere in this class, we can expect the Product class to make calls to the Style class, in order to create these sub-objects.

Additionally, if you look at Figure 10-II, you will notice that the Catalog object contains an array of Product objects. You can probably now see the parallel structure we had mentioned. This is particularly important because as you look through the product you should expect to see places where the Catalog class would be making calls to the Product class in order to create this structure. In fact, you will see that in the constructor of the Product class.

# METHOD() This is the constructor of the class. It is very brief.

```
function Product($parent="","atts="")
{
    $this->styles = array();
    $this->Base($parent,$atts);
}
```

Remember that we said this will be called from the Category class. The Spar variable will contain the name of the parent, and Satts will be a row retrieved from the database. Though it's not important to show all of the code that will call to do this method, you should have an idea of what is needed to create the data structure in Figure 10-12.

Somewhere in the Category class, a query to the database will retrieve a list of all the products associated with a category_id, something like * from products where category_id =category_id. The result set of this query will be looped through each time the loop will be assigned to the second argument in the call to the Product object. You will see an example of this later in the chapter, when the Product class makes calls to the Styles class.

The call to Base() will take each of the elements in the associative array and assign them to object properties.

Note that this constructor will also run if a product object is instantiated within a script. But before being instantiated, the information with the product_id will not be automatically loaded. The FetchProduct() or LoadProduct() methods will be needed for that. It is the LoadProduct() method that will make the Style class. But before we break that, you need to see the FetchProduct() method.

# METHOD FETCHPRODUCT() This method grabs the forms table associated with the given product id. It includes some error handling, for the event that no product_id or a bad product_id was given. Then, using the Construct method from the Base class, each of the returned fields is turned into a property of the Product object.