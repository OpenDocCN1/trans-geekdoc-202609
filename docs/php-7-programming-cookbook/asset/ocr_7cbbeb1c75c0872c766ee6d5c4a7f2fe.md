# **Implementing a stack**

A **stack** is a simple algorithm normally implemented as **Last In First Out (LIFO)**. Think of a stack of books sitting on a library table. When the librarian goes to restore the books to their place, the topmost book is processed first, and so on in order, until the book at the bottom of the stack has been replaced. The topmost book was the last one to be placed on the stack, thus last in first out.

In programming terms, a stack is used to temporarily store information. The retrieval order facilitates retrieving the most recent item first.

# How to do it…

+   1. First we define a class, `Application\Generic\Stack`. The core logic is encapsulated in an SPL class, `SplStack`:
   ```
   namespace Application\Generic;
   use SplStack;
   class Stack
   {
       // code
   }
   ```

+   2. Next we define a property to represent the stack, and set up an `SplStack` instance:
   ```
   protected $stack;
   public function __construct()
   {
       $this->stack = new SplStack();
   }
   ```

+   3. After that we define methods to add and remove from the stack, the classic `push()` and `pop()` methods:
   ```
   public function push($message)
   {
       $this->stack->push($message);
   }
   public function pop()
   {
       return $this->stack->pop();
   }
   ```