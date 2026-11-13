```
def insert_at_end(self, data):
    new_node = ListNode(data) # Create new node
    if self.head is None: # Check if list is empty
        self.head = new_node # Insert new node as head of list
    else:
        current = self.head # Get a link to the first node in the list
        while current.next != None: # Keep moving down the list
            current = current.next
        # When the above loop ends, the next pointer must be None, indicating we
        # have reached the last node
        current.next = new_node # Set pointer on current last node to the new node
```

# Java

```
public void insertAtBeginning(int data) {
    ListNode newNode = new ListNode(data); // Create a new node with the data given
    newNode.next = head; // Set new node pointer to current head node
    head = newNode; // Set head pointer to new node
}

public void insertAfter(int targetValue, int data) {
    ListNode current = head;
    // Traverse the list to find the target value
    while (current != null && current.data != targetValue) {
        current = current.next;
    }

    // At this point current will either be null (not found) or our target node
    // If the target node is found, insert the new node after it
    if (current != null) {
        ListNode newNode = new ListNode(data); // Create new node with data
        // provided
        newNode.next = current.next; // Set new node pointer to the same pointer
        // as the found node
        current.next = newNode; // Set the found node pointer to the new node
    } else {
        // If the target value is not found in the list
        System.out.println("Node with value " + targetValue + " not found.");
    }
}

public void insertAtEnd(int data) {
    ListNode newNode = new ListNode(data); // Create a new node
    if (head == null) { // Check if list is empty
        head = newNode; // Insert new node as head of list
    } else {
        ListNode last = head; // Get link to the first node in the list
        while (last.next != null) { // Keep moving down the list
            last = last.next;
        }
    }
}
```