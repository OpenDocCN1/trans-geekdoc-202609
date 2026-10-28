
## Exercise 19-1 Use PHP to work with a database

This exercise lets you use some of the skills that were presented in this chapter. In particular, it lets you use the functions from the product_db.php file that’s presented in this chapter.

### Review and test the code

1. Run the application in the ex_starts/ch19_ex1 directory. This should display the names of the products in the Basses category, a delete message, and an insert message.
2. Open the database.php file, the product_db.php file, and the index.php file. Then, review the code. Note that this code uses PDO.
3. If you want to use mysqli instead of PDO, replace the database.php and product_db.php files with the database.php and product_db.php files that are in the book_apps/ch20_guitar_shop_mysqli/model directory.

### Modify the code

4. Modify the index.php file so it displays the products that are in the Guitars category.
5. Modify the index.php file so it uses a function from the model to add a product. When you do that, use the sample data that’s already in the index.php file. Make sure this code displays an appropriate message that indicates whether the product was inserted. Note that the products table requires a unique product code for each product. As a result, you can’t insert the same product code twice.
6. Add a function to the model named get_product_by_name. This function should have a parameter for the product name and it should return a product array for the product with the specified name. This provides a way to get the product ID and other product data that corresponds to the product name.
7. Modify the index.php file so it uses a function from the model to delete the product named “Fender Telecaster”. To do that, you can use the function that you created in the previous step to get the product ID. Make sure this code displays an appropriate message that indicates whether the product was deleted.
8. Test the code to make sure it works correctly. If it does, it should display the products, delete a product, add a product, and display appropriate messages.

## 20

## A database-driven website

The last chapter showed how to use PHP to code the model for a database-driven web application. Now, this chapter shows how to use that model to build a database-driven website for a store, and it presents enhanced versions of the two primary applications within that website: the Product Catalog and Product Manager applications. But first, this chapter shows you how to work with database columns that store large amounts of text.

| Section | Page |
|---|---|
| How to work with large text columns | 652 |
| A simple content management system | 652 |
| How to add HTML tags to text | 654 |
| The include files for the Guitar Shop website | 656 |
| The Home page | 656 |
| The directory structure | 656 |
| The utility files | 658 |
| The view files | 658 |
| The Product Catalog application | 664 |
| The user interface | 664 |
| The controller | 664 |
| The view | 664 |
| The Product Manager application | 668 |
| The user interface | 668 |
| The controller | 670 |
| The view | 672 |
| Perspective | 676 |

## How to work with large text columns

When you develop a database-driven application, you often need to store large amounts of text in the columns of the database. For example, the description column for each product may consist of several paragraphs and may include bulleted lists and other types of formatting. This topic presents a simple but effective approach for working with columns like that.

### A simple content management system

When you store large amounts of text in a column, you need to format it before you can display it on a web page. If, for example, the text contains multiple paragraphs, you need to add <p> tags to the paragraphs before you display them on a web page. Similarly, if the text contains an unordered list, you need to add <ul> and <li> tags to the items in the list. In addition, you may need to add other types of HTML formatting to the text such as tags for headings, links, boldfacing, italics, and so on.

One solution to this problem is to store the HTML tags that format the text in the database along with the text. From the programmer’s point of view, this is an easy solution. All the programmer has to do is to *not* use the htmlentities or htmlspecialchars function to convert special characters to their equivalent HTML entities. That way, the HTML tags are stored in the database. However, when you use this approach, the person who enters the text must know HTML and must be able to code the HTML tags without making errors. Since that’s a lot to ask, this usually isn’t the way you want your website to work.

To get around this problem, you can create a *content management system* for your website. A content management system is a series of web pages that make it easy for users with little knowledge of HTML to manage the content of the website. Figure 20-1 shows how a simple content management system works. This content management system allows the user to enter a large amount of text for the description column of a products table.

When the user enters text, he or she can use two returns to start a new paragraph, an asterisk to mark items in an unordered list, and standard HTML tags for bold and italics. This stores the end of line characters in the database, and it stores the HTML tags in the database.

When the application gets this text from the database, it uses PHP to apply the rest of the HTML tags. In particular, it adds the appropriate <p> tags when it finds two return characters, and it adds the appropriate <ul> and <li> tags when it finds a line that begins with an asterisk.

In this example, the content management system is a hybrid system that requires that the user have some knowledge of HTML tags. In particular, it requires that the users know how to use HTML tags to identify text that should be displayed in bold or italics. However, this system automatically handles the tags for paragraphs and unordered lists.

### The text that's entered by the user

The Fender Stratocaster is <i>the</i> electric guitar design that changed the world. This guitar features a thicker bridge block for increased sustain and a more stable point of contact with the strings.

Features:

- Thicker bridge block
- 3-ply parchment pick guard
- Tinted neck

### The HTML that's generated by the content management system

```
<p>The Fender Stratocaster is <i>the</i> electric guitar design that changed the world. This guitar features a thicker bridge block for increased sustain and a more stable point of contact with the strings.</p>
```

```
<p>Features:</p>
```

```
<ul>
    <li>Thicker bridge block</li>
    <li>3-ply parchment pick guard</li>
    <li>Tinted neck</li>
</ul>
```

### The rules for this content management system

- Use two returns to start a new paragraph.
- Use an asterisk to mark items in a bulleted list.
- Use one return between items in a bulleted list.
- Use standard HTML tags for bold and italics.

### Description

- A content management system for a website is a series of web pages that make it easy for users with little knowledge of HTML to manage the content of the website.
- To allow the user to use HTML tags, you must not use the htmlentities or htmlspecialchars function to convert special characters to their equivalent HTML entities.
- Bulletin Board Code (BBCode) is a markup language that’s used by many bulletin board or message board systems to format text. BBCode is similar to HTML, but it has a simplified syntax that uses square brackets ([ ]) instead of angled brackets (< >).
