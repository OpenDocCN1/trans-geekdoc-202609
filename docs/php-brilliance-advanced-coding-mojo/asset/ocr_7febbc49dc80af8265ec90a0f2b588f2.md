# Tell, Don't Ask

To a certain degree, the naysayers are right to call this out. If the Tell, Don’t Ask principle is only really saying to us that we should be doing encapsulation properly, then yes, the principle itself is an unnecessary addition to the catalogue of stuff that we as brilliant programmers are supposed to know.

If the Tell, Don’t Ask principle requires us to add a method to an object for every single operation we need to perform concerning the data that the object holds then there’s a very real possibility that our classes will become quite bloated over time. We should very certainly be striving to avoid bloated classes wherever possible.

Lastly, if we became fanatical about the Tell, Don’t Ask principle, then we might start to eliminate all of the getter methods that we’ve been writing into our classes previously. In some quarters, getter methods are criticised for breaking the principle of encapsulation by exposing the inner state of an object. Fanaticism is not normally a good thing though and in this case, eliminating getters entirely would also severely restrict our ability to create collaborators for the objects within our system.

Imagine trying to create a SalesReport object, that fed appropriate SalesOrder instances, wasn’t able to get any information about those orders for the reports that it is trying to build. Clearly the SalesOrder instances need to collaborate with the SalesReport instance and that the order objects have to be able to supply the details of the sales order that one represents.

So where does that leave us, the members of Team Brilliance?

The good news is that it leaves us in a very good place indeed. By adding this principle to our mental toolbox, we are backing up and reinforcing what we already understand about encapsulation. It’s not always easy to keep the principle of encapsulation at the forefront of our minds whilst we are banging out enterprise-grade application code. It is, however, much easier to catch ourselves when we inadvertently make a logic decision based on the values held within an object’s state. When we find ourselves performing a logic test on an object’s state to determine which block of code will be executed, we are almost certainly violating this principle and therefore by extension, we’re also violating the principle of encapsulation too.