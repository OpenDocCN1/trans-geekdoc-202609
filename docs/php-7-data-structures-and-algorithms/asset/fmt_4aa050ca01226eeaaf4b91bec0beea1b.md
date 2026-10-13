
## Constructing a binary search tree

As we know, a node can have two children and itself can represent a tree in a recursive manner. We will define our node class to be more functional and have all the required functionalities to find the maximum value, minimum value, predecessors, and successors. Later on, we will add the delete functionality as well for a node. Let's check the following code for a node class for a BST:

```php
class Node { 



    public $data; 

    public $left; 

    public $right; 



    public function __construct(int $data = NULL) { 

       $this->data = $data; 

       $this->left = NULL; 

       $this->right = NULL; 

    } 



    public function min() { 

       $node = $this; 



       while($node->left) { 

         $node = $node->left; 

       } 

         return $node; 

    } 



    public function max() { 

         $node = $this; 



         while($node->right) { 

            $node = $node->right; 

         } 

         return $node; 

    } 



    public function successor() { 

         $node = $this; 

         if($node->right) 

               return $node->right->min(); 

         else 

               return NULL; 

    } 



    public function predecessor() { 

         $node = $this; 

         if($node->left) 

               return $node->left->max(); 

         else 

               return NULL;

    }



}
```

The node class looks straightforward and matches with our steps defined in the previous section. Each new node is a leaf and hence, does not have a left or right node at the moment of creation. As we know that we can find the smaller value at the left of the node to find the minimum, we are reaching to the left-most node and right-most node for the maximum value. For a `successor()`, we are finding the minimum value of a node from the right subtree of a given node and the maximum value of a node from the left subtree for the `predecessor()` part.

Now, we need a `BST` structure to add new nodes in the tree so that we can follow the insert principle:

```php
class BST { 



    public $root = NULL; 



    public function __construct(int $data) { 

         $this->root = new Node($data); 

    } 



    public function isEmpty(): bool { 

         return $this->root === NULL; 

    } 



    public function insert(int $data) { 



         if($this->isEmpty()) { 

               $node = new Node($data); 

               $this->root = $node; 

               return $node; 

         }  



    $node = $this->root; 



    while($node) { 

      if($data > $node->data) { 

          if($node->right) { 

            $node = $node->right; 

          } else { 

            $node->right = new Node($data); 

            $node = $node->right; 

            break; 

          } 



      } elseif($data < $node->data) { 

          if($node->left) { 

            $node = $node->left; 

          } else { 

            $node->left = new Node($data); 

            $node = $node->left; 

            break; 

          } 

      } else { 

            break; 

      } 

    } 

    return $node; 



    } 



    public function traverse(Node $node) { 

      if ($node) { 

          if ($node->left) 

            $this->traverse($node->left); 

          echo $node->data . "\n"; 

          if ($node->right)

            $this->traverse($node->right);

      }

    }



}
```

If we look at the preceding code, we have only one property for the `BST` class, which will mark the root node. During the construction of the `BST` object, we are passing a single value, which will be used as the root of the tree. The `isEmpty()` method checks whether the tree is empty or not. The `insert()` method allows us to add a new node in the tree. The logic checks whether the value is greater than or less than the root node and follows the principle of the BST to insert the new node in the right position. If the value is already inserted, we will ignore it and avoid adding to the tree.

We also have a `traverse()` method to go through the nodes and see the data in an ordered format (first left, then the node, and then the right node value). It has a designated name, and we will explore that in the next section. For now, let's prepare a sample code to use the `BST` class and add a few numbers and check whether the numbers are stored in a proper way. If the `BST` is working, then the `traverse()` will show a sorted list of numbers, no matter how we insert them:

```php
$tree = new BST(10); 



$tree->insert(12); 

$tree->insert(6); 

$tree->insert(3); 

$tree->insert(8); 

$tree->insert(15); 

$tree->insert(13); 

$tree->insert(36); 



$tree->traverse($tree->root);
```

If we look at the preceding code, `10` is our root node, and then, we added new nodes randomly. At the end, we invoked the `traverse()` method to show the nodes and how they are stored in the binary search tree. Here is the output of the preceding code:

```
3



6



8



10



12



13



15



36
```

The actual tree will look like this visually, which looks exactly like what is expected from the `BST` implementation:

![](Image00051.jpg)

Now, we will add the search part in our `BST` class. We want to find whether the value exists in the tree or not. If the value is not in our `BST`, it will return false and the node otherwise. Here is the simple search functionality:

```php
public function search(int $data) { 

  if ($this->isEmpty()) { 

      return FALSE; 

  } 



  $node = $this->root; 



  while ($node) { 

      if ($data > $node->data) { 

        $node = $node->right; 

      } elseif ($data < $node->data) { 

        $node = $node->left; 

      } else { 

        break; 

      } 

  } 



  return $node; 

}
```

In the preceding code, we can see that we are searching a value in the tree from the node and following either left or right of the tree iteratively. If no node is found with the value, the leaf of the node is returned, which is `NULL`. We can test the code like this:

```php
echo $tree->search(14) ? "Found" : "Not Found";

echo "\n";

echo $tree->search(36) ? "Found" : "Not Found";
```

This will produce the following output. Since `14` is not in our list, it will say `Not Found`, and for `36`, it will show `Found`:

```
Not Found



Found
```

Now, we will move to our most complex part of the coding, the deletion of a node. We need to implement each of the cases where a node can have zero, one, or two child nodes. The following image shows us the three conditions we need to satisfy for deleting a node and making sure the binary search tree remains a binary search tree after the operation. We have to be careful when we are dealing with a node that has two child nodes. Since we need to go back and forth between nodes, we need to know which node is the parent node for the current node. As a result, we need to add an additional property to track the parent node for any node:

![](Image00052.jpg)

Here is the change of code we are adding to our `Node` class:

```php
    public $data;

    public $left;

    public $right;

    public $parent;



    public function __construct(int $data = NULL, Node $parent = NULL)   

     {

      $this->data = $data; 

      $this->parent = $parent; 

      $this->left = NULL; 

      $this->right = NULL; 

     }
```

This code block now also creates a parent relationship with the newly created node to its immediate parent. We also want to attach our delete functionality with the individual node so that we can find a node and then just remove it using the `delete()` method. Here is the code for the delete functionality:
