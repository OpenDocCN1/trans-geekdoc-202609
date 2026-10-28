# The code for the Product class

Figure 14-2 shows the code for the Product class. This code is similar to the code for the Category class. To start, this code defines five private properties. Then, it defines a constructor method that sets four of these properties. Next, it defines get and set methods for all of the properties.

As you review this code, note that the getCategory and setCategory methods can get and set an object that’s created from the Category class defined in figure 14-1. In other words, you can nest one class within another class. As you progress though this chapter, you’ll learn more about how this works.

The getPriceFormatted method works a little differently than the previous get methods. This method uses the number_format method to convert the price to a string that has two digits and stores the string in a variable named $formatted_price. Then, the second statement returns the string for the formatted price. As a result, you can use the getPriceFormatted method to get a formatted string for the price, and you can use the getPrice method to get a numeric value for the price.