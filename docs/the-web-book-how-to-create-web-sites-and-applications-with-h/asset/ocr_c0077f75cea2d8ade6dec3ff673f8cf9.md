![](bbox=[0.12, 0.11, 0.82, 0.48])

You now have 7 lines (one for each field) into which you can enter the field name, its type, its length, and a few other things too.

As you can see from the list of possible field types that I’ve clicked on in the top field, there are lots to choose from. It’s important that you choose the right field type for each field (column) in your table. This generally means making two decisions. First, whether or not the content of that field will be purely numeric. Because if it will be, choosing one of the numeric field types will result in a database that can be searched and indexed more efficiently. The second decision is for when you decide that the field won’t be purely numeric, but will also hold alphabetical text. In which case you need to specify the maximum length of any one field. I’ll explain more about this as we create the customers table.

The field names are going to be:

id  
firstname  
surname  
title  
address  
phone