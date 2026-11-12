For Ukulele, we implemented a binary search tree (BST) to serve as the index structure. The BST employs a two-dimensional array in which the first dimension of each entry is used for storing the property value and the second dimension is used for storing a set of hashes to the elements that correspond to this specific value. We chose this implementation because of its simplicity for selecting an interval of indexes in any comparison operation, such as “greater than”, “lesser than”. We acknowledge that BST has a high storage requirement. However, we wanted a simple and fast solution to our first implementation of Ukulele. Moreover, Ukulele builds these internal indexes automatically, without the need for user interaction. On the other hand, Ukulele also supports users creating their own custom indexes to speed up queries. The syntax to create custom indexes is similar to SQL (Listing 13.5).

# Listing 13.5 Ukulele custom index grammar in EBNF format

```
1 <Index> ::= "create" ["unique"] "index" identifier "on"
    identifier "("identifier ")"
```

# Illustrative example

For this example, we will show some of the new features of Ukulele (i.e., contract querying). Let’s suppose a smart contract that handles the selling of a product. The following listing (Listing 13.6) shows the essential code parts for the product contract.

# Listing 13.6 Solidity product contract example

```
31 pragma solidity ^0.4.24;
32 /** @title Product Contract Example
33 * @author RMod-Blockchain Team
34 */
35 contract RModProduct {
36 /* Type Definition */
37 enum State {ON_SALE, WAITING_SEND, RECEIVED, FINISH}
38
39 /* Attributes */
40 State private state = State.ON_SALE;
41 address private owner;
42 address private buyer;
43 uint private price;
44 string private itemName;
45
46 /* Constructor */
47 constructor(string _name, uint _price) public {
48 owner = msg.sender; itemName = _name; price = _price;
49 }
```