
*   **Path**: The sequence of nodes and edges from a source node to a target node is known as the path between two nodes. The length of the path is the number of nodes in the path. In our example, the path between `A` to `M` is `A-C-H-M`, and the length of the path is 4:

![](Image00043.jpg)

*   **Height of node**: The height of a node is defined by the number of edges between the node and the deepest level of the descendent node. For example, the height of node `B` is 2.

*   **Level**: The level represents the generation of nodes. If a parent node is in level `n`, its child node will be in the `n+1` level. So, the level is defined by 1+ number of edges between the node and the root. Here:

    *   Root `A` is in **Level 0**
    *   `B`, `C`, and `D` are in **Level 1**
    *   `E`, `F`, `G`, `H`, `I`, and `J` are in **Level 2**
    *   `K`, `L`, and `M` are in **Level 3**

*   **Height of tree**: The height of a tree is defined by the height of its root node. Here, the height of the tree is 3.

*   **Subtree**: In a tree structure, each child forms a subtree recursively. In other words, a tree consists of many subtrees. For example, `B` forms a subtree with `E`, `K`, and `L`, whereas `E` forms a subtree with `K` and `L`. In the preceding example, we have identified each in the left-hand side in different shades. We can do the same for `C` and `D` and their subtrees as well.

*   **Depth**: The depth of a node is determined by the number of edges between the node and the root node. For example, in our tree image, the depth of `H` is 2 and the depth of `L` is 3.

*   **Forest**: A forest is a set of zero or more disjoint trees.

*   **Traverse**: This indicates the process of visiting nodes in a specific order. We will use this term often in the upcoming sections.

*   **Keys**: A key is a value from the node that is used for searching purposes.

# Implementing a tree using PHP

So far, you have learned about different properties of a tree data structure. If we compare a tree data structure with a real-life example, we can consider our organization structure or family tree to represent the data structure. For an organization structure, there is one root node that can be the CEO of the company, followed by CXO-level employees, followed by other level employees. Here, we are not restricting any degree for a particular node. This means a node can have multiple children. So, let's think of a node structure where we can define the node property, its parent node, and its children nodes. It might look something like this:

```
class TreeNode { 



    public $data = NULL; 

    public $children = []; 



    public function __construct(string $data = NULL) { 

      $this->data = $data; 

    } 



    public function addChildren(TreeNode $node) { 

      $this->children[] = $node; 

    } 



} 
```

If we look at the preceding code, we can see that we have declared two public properties for data and children. We also have a method to add children to a particular node. Here, we are just appending the new child node at the end of the array. This will give us an option to add multiple nodes as children for a particular node. As a tree is a recursive structure, it will help us build a tree recursively and also traverse the tree in a recursive manner.

Now, we have the node; let's build a tree structure that will define the root node of the tree and also a method to traverse the whole tree. So, the basic tree structure will look like this:

```
class Tree { 



    public $root = NULL; 
    public function __construct(TreeNode $node) { 

      $this->root = $node; 

    } 



    public function traverse(TreeNode $node, int $level = 0) { 



      if ($node) { 

        echo str_repeat("-", $level); 

        echo $node->data . "\n"; 



        foreach ($node->children as $childNode) { 

          $this->traverse($childNode, $level + 1); 

        } 

      } 

    } 



} 
```

The preceding code shows a simple tree class where we can store the root node reference and also traverse the tree from any node. In the traverse part, we are visiting each child node and then immediately recursively calling the `traverse()` method to get the children of the current node. We are passing a level to print out a dash (`-`) at the beginning of the node name so that we can understand the child level data easily.

Let's now create the root node and assign it to the tree as a root. The code will look like this:

```
$ceo = new TreeNode("CEO"); 

$tree = new Tree($ceo); 
```

Here, we created the first node as CEO, and then created the tree and assigned the CEO node as the root node of the tree. Now, it is time to grow our tree from the root node. Since we choose the example of the CEO, we will now add CXOs and other employees under the CEO. Here is the code for this:

```
$cto     = new TreeNode("CTO"); 

$cfo     = new TreeNode("CFO"); 

$cmo     = new TreeNode("CMO"); 

$coo     = new TreeNode("COO"); 



$ceo->addChildren($cto); 

$ceo->addChildren($cfo); 

$ceo->addChildren($cmo); 

$ceo->addChildren($coo); 



$seniorArchitect = new TreeNode("Senior Architect"); 

$softwareEngineer = new TreeNode("Software Engineer"); 

$userInterfaceDesigner      = new TreeNode("User Interface Designer"); 

$qualityAssuranceEngineer = new TreeNode("Quality Assurance Engineer"); 



$cto->addChildren($seniorArchitect); 

$seniorArchitect->addChildren($softwareEngineer); 

$cto->addChildren($qualityAssuranceEngineer); 

$cto->addChildren($userInterfaceDesigner); 



$tree->traverse($tree->root); 
```

Here we are creating four new nodes (CTO, CFO, CMO, and COO) at the beginning and assigning them as child nodes of the CEO node. Then we are creating Senior Architect and here is the Software engineer node followed by the user interface designer and Quality assurance engineer. We have assigned the senior software engineer node to be a child node of the senior architect node and senior architect to be a child node of CTO, along with user interface engineer and quality assurance engineer. The last line is to display the tree from the root. This will output the following lines in our command line:

```
CEO



-CTO



--Senior Architect



---Software Engineer



--Quality Assurance Engineer



--User Interface Designer



-CFO



-CMO



-COO
```

If we consider the preceding output, we have `CEO` at level 0. `CTO`, `CFO`, `CMO`, and `COO` are at level 1. `Senior Architect`, `User Interface Designer`, and `Quality Assurance Engineer` are at level 2 and `Software Engineer` is at level 3.

We have constructed a basic tree data structure using PHP. Now, we will explore the different types of trees we have.

# Different types of tree structures

There are many types of tree data structures present in the programming world. We will explore some of the most used tree structures here.

## Binary tree

Binary is the most basic form of tree structure where each node has a maximum of two child nodes. The child nodes are known as left and right nodes. A binary tree will look like the one shown in the following diagram:

![](Image00044.jpg)

## Binary search tree

A binary search tree (BST) is a special type of binary tree where the nodes are stored in a sorted manner. It is sorted in such a way that at any given point, a node value must be greater than or equal to the left child node value and smaller than the right child node value. Each node has to satisfy this property to consider it as a binary search tree. Since the nodes are sorted in a particular order, the binary search algorithm can be applied to search items in a BST in logarithmic time. It is always better than linear searching, which takes **O(n)** time, and we will explore it in the next chapter. Here is an example of a binary search tree:

![](Image00045.jpg)

## Self-balanced binary search tree
