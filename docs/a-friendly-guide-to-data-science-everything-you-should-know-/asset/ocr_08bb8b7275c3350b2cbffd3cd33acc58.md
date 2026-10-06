# CHAPTER 15 NOT A CRYSTAL BALL: MACHINE LEARNING

# Table 15-6. After the third node split: Contains flagged words = True

| Email | Sender | Email Domain | Contains | Contains | Is |
| ID | Unknown | Unknown | Flagged Words | Misspellings | Spam |
| 2 | True | True | True | True | True |
| 4 | True | True | True | True | True |

# Table 15-7. After the third node split: Contains flagged words = False

| Email | Sender | Email Domain | Contains | Contains | Is |
| ID | Unknown | Unknown | Flagged Words | Misspellings | Spam |
| 3 | True | True | False | False | False |
| 5 | True | True | False | True | False |

Now, that split has yielded two sets that have only one label present, which means these can be nodes with the appropriate label. And now if we repeat this process on the right branch of the root node we have a decision tree trained that can be used to classify new emails that come in.

When using real data to build a decision tree, the splits are never perfect, and most leaves will have records with different labels. There are a lot of different ways to control the building of a tree, which is primarily why we can end up with misclassified records in training. In reality, we don't want the tree to get too deep, which is what would happen if we insisted on each leaf having only records with the same label. We'd also end up with leaves that have only one or very small number of records. Those situations are basically overfitting (we’ll talk about it below). So we impose some limitations, like max depth and minimum number of records required in a node to split it (once we get to a node that splitting would lead to too-small nodes, we'd call it a leaf with the most common label).

529