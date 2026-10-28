# How to work with queues and stacks

Figure 11-8 shows four functions that you can use to work with two special types of arrays known as queues and stacks. A *stack* implements a *last-in, first-out (LIFO)* collection of values. You can think of a stack as a stack of dishes. The last dish you put on the stack is the first dish you must take off the stack.

The first example shows how to use a stack. Here, the first statement creates an array. Then, the second statement uses the array_push function to put a new value on the stack. Next, the third statement uses the array_pop function to take the value off the stack. Finally, the fourth statement displays the value that has just been taken off the stack.

A *queue*, on the other hand, implements a *first-in, first-out (FIFO)* collection of values. You can think of a queue as a single line of people waiting at a bank. The first person in the line is the first person to be served and get out of the line.

The second example shows how to use a queue. Here, the first statement creates an array. Then, the second statement uses the array_push function to push a new value onto the end of the queue. Next, the third statement uses the array_shift function to remove the value from the front of the queue and shift the rest of the queue over to take its spot. Finally, the fourth statement displays the value that has just been removed from the queue.

When you work with stacks, it doesn’t matter which side of the array you add and remove values from as long as you always work with the same side of the array. The example in this figure uses the array_push and array_pop functions to work with the end of an array. However, you can also implement a stack by using the array_unshift and array_shift functions to work with the front of an array.

Similarly, when working with a queue, you always add values to one side of the array and remove them from the other side. As a result, you can use the array_push and array_shift functions to create a queue. Or, you can use the array_unshift and array_pop functions to create a queue.

As you review the functions in this figure, note that they modify the array that’s passed to the function. In other words, they don’t return a new array.