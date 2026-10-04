# Part IV: Not So Simple Applications

Methods:

+   - Address. Calls the Base() method, assigning each element of the $Satts array to Object properties.

+   - FetchAddress. Takes one argument, $address_id. Creates object properties for every row in the user table associated with the $address_id.

+   - LoadAddress. Takes one argument, $address_id. First runs FetchOrder and then creates an array, each element of which is an object containing information.

+   - SaveAddress. Takes no arguments, assumes a $this->order_id exists. Will both update styles and create new ones as needed.

+   - DeleteAddress. Takes no arguments. Removes a user from the database. It will force confirmation if there are related addresses. It will delete the user after confirmation is provided.

# CLASS ORDER

Finally, in this class we add something new and interesting.
Class Name: Order
Extends Address
Default Properties:

+   - Items

Methods:

+   - Order. Calls the Base() method, assigning each element of the $Satts array to Object properties.

+   - FetchOrder. Takes one argument, $order_id. Creates object properties for every row in the user table associated with the $order_id.

+   - LoadOrder. Takes one argument, $order_id. First runs FetchOrder and then creates an array, each element of which is an object containing information.

+   - SaveOrder. Takes no arguments, assumes a $this->order_id exists. Will both update styles and create new ones as needed.

+   - DeleteOrder. Takes no arguments. Removes a user from the database. It will force confirmation if there are related addresses. It will delete the user after confirmation is provided.

+   - CalculateTotals. Takes no arguments. This method calculates total prices for each item of the order and for the order as a whole. Items that are flagged for deletion are removed from the items array.