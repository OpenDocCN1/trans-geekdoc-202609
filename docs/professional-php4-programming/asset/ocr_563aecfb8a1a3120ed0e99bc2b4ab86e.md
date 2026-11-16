A few screenshots of the finished product:

![](bbox=[0.306, 0.113, 0.688, 0.242])

![](bbox=[0.306, 0.257, 0.688, 0.409])

![](bbox=[0.222, 0.424, 0.768, 0.651])

Although this is a lot of code to perform a simple task it, is not always necessary to write all this code ourselves. Luckily, PHP-GTK supports an application known as Glade, which is a GUI builder. You can use Glade to design your GUI and store the design as an XML file. You then load the XML file into PHP-GTK by declaring it as a new instance of a GladeXML object class, and it will run the GUI you designed. Covering Glade is beyond the scope of this introductory chapter, but there is information about it in the PHP-GTK manual, and there is also a very good chapter on using Glade in Professional Linux Programming from Wrox Press (ISBN 1-861003-01-3).

I hope that this insight into PHP-GTK has got you as excited as I was when I heard that it was possible to create GUI applications with PHP. It adds a whole new dimension to the language, and will hopefully prove to be a useful asset to the PHP community.