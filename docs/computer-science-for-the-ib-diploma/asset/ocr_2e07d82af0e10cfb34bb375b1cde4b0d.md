```
```java
public void deleteNode(int data) {
  ListNode current = head
  prev = null;
  // Case 1: If the head node is to be deleted
  if (current != null && current.data == data) {
    head = current.next; // Changed head
    return;
  }
  // Case 2: If the node to be deleted is somewhere other than at the head
  while (current != null && current.data != key) {
    prev = current;
    current = current.next;
  }
  // Case 3: If the key is not present in the list
  if (current == null) {
    System.out.println("Node with value " + key + " not found.");
    return;
  }
  // Unlink the node from the linked list
  prev.next = current.next;
}
```
```

# Search

The search method also resides in the LinkedList class. This is a relatively straightforward method that combines some of the techniques we have already used. The method needs a single parameter to look for and, in these examples, will return true or false, depending on whether the item was found. This could be modified to return the position in the list of the node itself, if needed.

```
```python
def search(self, key):
  current = self.head # Get the head node
  while current != None: # Keep looping until we have run out of nodes
    if current.data == key: # If we find the node we are looking for
      return True
    current = current.next # Move to the next node
  return False # Value not found in the list
```
```