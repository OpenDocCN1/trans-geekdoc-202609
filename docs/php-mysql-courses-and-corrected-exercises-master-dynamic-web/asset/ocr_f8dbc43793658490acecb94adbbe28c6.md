![](bbox=[0.04, 0.04, 0.96, 0.31])

When you consult the data in the "authors" table, you will see that the information for the author with ID 1 has been modified:

![](bbox=[0.04, 0.45, 0.96, 0.57])

You may have noticed in the previous code that the author ID and the new data were defined statically. In practice, however, it is essential to retrieve them dynamically.

This can be achieved in a number of ways: for example, by setting up a form where the user can enter the identifier of the author concerned, followed by its retrieval. Another option is to addition a link in front of each line of the table displaying all authors, enabling the corresponding author ID to be transmitted. It's this latter approach that we'll be developing in what follows.

New data can be managed via a form. This will first display the old data to be updated, then allow the user