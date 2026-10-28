# # How to work with large text columns

When you develop a database-driven application, you often need to store large amounts of text in the columns of the database. For example, the description column for each product may consist of several paragraphs and may include bulleted lists and other types of formatting. This topic presents a simple but effective approach for working with columns like that.

# ## A simple content management system

When you store large amounts of text in a column, you need to format it before you can display it on a web page. If, for example, the text contains multiple paragraphs, you need to add <p> tags to the paragraphs before you display them on a web page. Similarly, if the text contains an unordered list, you need to add <ul> and <li> tags to the items in the list. In addition, you may need to add other types of HTML formatting to the text such as tags for headings, links, boldfacing, italics, and so on.

One solution to this problem is to store the HTML tags that format the text in the database along with the text. From the programmer’s point of view, this is an easy solution. All the programmer has to do is to *not* use the htmlentities or htmlspecialchars function to convert special characters to their equivalent HTML entities. That way, the HTML tags are stored in the database. However, when you use this approach, the person who enters the text must know HTML and must be able to code the HTML tags without making errors. Since that’s a lot to ask, this usually isn’t the way you want your website to work.

To get around this problem, you can create a *content management system* for your website. A content management system is a series of web pages that make it easy for users with little knowledge of HTML to manage the content of the website. Figure 20-1 shows how a simple content management system works. This content management system allows the user to enter a large amount of text for the description column of a products table.

When the user enters text, he or she can use two returns to start a new paragraph, an asterisk to mark items in an unordered list, and standard HTML tags for bold and italics. This stores the end of line characters in the database, and it stores the HTML tags in the database.

When the application gets this text from the database, it uses PHP to apply the rest of the HTML tags. In particular, it adds the appropriate <p> tags when it finds two return characters, and it adds the appropriate <ul> and <li> tags when it finds a line that begins with an asterisk.

In this example, the content management system is a hybrid system that requires that the user have some knowledge of HTML tags. In particular, it requires that the users know how to use HTML tags to identify text that should be displayed in bold or italics. However, this system automatically handles the tags for paragraphs and unordered lists.