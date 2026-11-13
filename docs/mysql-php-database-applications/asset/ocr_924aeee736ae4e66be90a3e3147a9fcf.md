# Methods:

+   - fetch_from_db: Retrieve all data about this product from the database
+   - write_to_db: Write a new or updated product record to the database
+   - delete_from_db: Remove a product from the database
+   - print: Display a product to the browser

Knowing this information, and really nothing else, you could write a new script that displayed a product. The script that follows assumes that a product_id was passed through the querystring or via a POST.

```
$p = new Product(array('product_id'=>$product_id));
$p->fetch_from_db();
$p->print();
```

But if we left it at this, your learning experience would be only a fraction of what it should be. Of course, in the next section, we go over the code in depth. For one thing, in this application the display of an object is left to the user of the object—we use regular functions, rather than having a print method in each object.

# Classes

We designed the classes in this application so that most of them look and behave similarly. As you look at the classes, you should notice that all but the Base class have methods with similar names. Our hope is that once you understand one class, the workings of the others will be pretty clear. For this reason, we're only going to break down two classes in this chapter. Note that the each method in each class is extensively commented on the CD. If you have a specific question as to the working of a snippet of code, you will likely find the answer within the comments.

In the following pages we break down code in the following classes: Base and Product. For the other classes we describe only how to use the methods and properties. But once you understand the Product class, the other classes should be easy enough to figure out.

![](bbox=[0.1, 0.77, 0.195, 0.835])

Please be sure that you have mastered the concepts in Chapter 7 before reading this section.

Breaking the classes into includes also enables you to selectively reuse specific classes when you need them. This becomes important in Chapter 14, when we reuse some of these classes in creating the shopping cart.