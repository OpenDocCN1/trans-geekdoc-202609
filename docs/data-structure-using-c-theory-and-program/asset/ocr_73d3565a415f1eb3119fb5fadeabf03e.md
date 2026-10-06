data element is greater than the key in the root, then the search is performed in the right sub-tree.

# Search 25

+   (i) Compare 25 with 48
(ii) 25 < 48, move to left child
(iii) Now, compare 25 with 30
(iv) 25 < 30, move to left child
(v) Now, compare 25 with 20
(vi) 25 > 20, move to right child
(vii) 25 found

# Search 50

+   (i) Compare 50 with 48
(ii) 50 > 48, move to right child
(iii) Now, compare 50 with 65
(iv) 50 < 65, move to left child
(v) Now, compare 50 with 56
(vi) 50 < 56, move to left child
(vii) NULL
(viii) 50 Not found

# 3. Finding nodes with Minimum and Maximum Values

To find minimum valued node in a binary search tree start at the root and move along the leftmost path until we get a node with no left child.

To find maximum value node start at the root and move along the rightmost path until we get a node with no right child.

# 4. Insertion in a Binary Tree

To insert an element in a binary tree start at the root node and compare the value to be inserted with the value at root node and take following actions.

+   (i) If the value to be inserted is equal to the value at the root node then there is nothing to be done as duplicate values are not allowed.
(ii) If the value to be inserted is less than the value of the node then we move to left child.
(iii) If the value to be inserted is greater than the value of the node then we move to right child.

# Insert 28

+   (i) Compare 28 with 48
(ii) 28 < 48, move to left child