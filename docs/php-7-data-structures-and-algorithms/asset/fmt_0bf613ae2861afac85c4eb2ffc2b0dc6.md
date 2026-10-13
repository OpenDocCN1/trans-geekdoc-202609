
Now, let us examine the pseudocode we have written. We are supplying a list of books and a name that we are searching. We are running a `foreach` loop to iterate each of the books and matching with the book name we are searching. If it is found, we are returning the position of the book where we found it, `false` otherwise. So, we have written a pseudocode to find a book name from our book list. But what about the other remaining books? How do we continue our search till all books are found and placed on the right shelf?:

```
Algorithm placeAllBooks

  Input: list of Ordered Books OL, List of received books L

  Output: nothing.

  for each book_name in OL, do

     if FindABook(L,book_name), then

       remove the book from the list L

       place it to the bookshelf
```

Now we have the complete pseudocode for our algorithm of solving the book organization problem. Here, we are going through the list of ordered books and finding the book in the delivered section. If the book is found, we are removing it from the list and placing it to the right shelf.

This simple approach of writing pseudocode can help us solve more complex problems in a structured manner. Since pseudocodes are independent of programming languages and platforms, algorithms are expressed as pseudocode most of the time.

# Converting pseudocode to actual code

We are now going to convert our pseudocodes to actual PHP 7 codes as shown:

```
function findABook(Array $bookList, String $bookName) {

    $found = FALSE;

    foreach($bookList as $index => $book) {

        if($book === $bookName) {

             $found = $index;

             break;

        }

    }

    return $found;

}



function placeAllBooks(Array $orderedBooks, Array &$bookList) {

    foreach ($orderedBooks as $book) {

    $bookFound = findABook($bookList, $book);

    if($bookFound !== FALSE) {

        array_splice($bookList, $bookFound, 1);

    }

  }

}



$bookList = ['PHP','MySQL','PGSQL','Oracle','Java'];

$orderedBooks = ['MySQL','PGSQL','Java'];



placeAllBooks($orderedBooks, $bookList);

echo implode(",", $bookList);
```

Let us now understand what is happening in the preceding code. First we have defined a new function, `findABook` at the beginning of the code. The function is defined with two parameters. One is `Array $bookList` and the other is `String $bookName`. At the beginning of the function we are initializing the `$found` to `FALSE`, which means nothing has been found yet. The `foreach` loop iterates through the book list array `$bookList` and for each book, it matches with our provided book name `$bookName`. If the book name that we are looking for matches with the book in the `$bookList`, we are assigning the index (where we found the match) to our `$found` variable. Since we have found it, there is no point in continuing the loop. So, we have used the `break` command to get out of the loop. Just out of the loop we are returning our `$found` variable. If the book was found, usually `$found` will return any integer value greater than 0, else it will return `false`:

```
function placeAllBooks(Array $orderedBooks, Array &$bookList) {

    foreach ($orderedBooks as $book) {

    $bookFound = findABook($bookList, $book);

    if($bookFound !== FALSE) {

        array_splice($bookList, $bookFound, 1);

    }

  }

}
```

This particular function `placeAllBooks` actually iterates through our ordered books `$orderedBooks`. We are iterating our ordered book list and searching each book in our delivered list using the `findABook` function. If the book is found in the ordered list (`$bookFound !== FALSE`), we are removing that book from the delivered book list using the `array_splice()` function of PHP:

```
$bookList = ['PHP','MySQL','PGSQL','Oracle','Java'];

$orderedBooks = ['MySQL','PGSQL','Java'];
```

These two lines actually shows two PHP arrays which are used for the list of books we have received, `$bookList` and the list of books we have actually ordered `$orderedBooks`. We are just using some dummy data to test our implemented code as shown:

```
placeAllBooks($orderedBooks, $bookList);
```

The last part of our code actually calls the function `placeAllBooks` to perform the whole operation of checking each book searching for it in our received books and removing it, if it is in the list. So basically, we have implemented our pseudocode to an actual PHP code which we can use to solve our problem.

# Algorithm analysis

We have completed our algorithm in the previous section. But one thing we have not done yet is the analysis of our algorithm. A valid question in the current scenario can be, why do we really need to have an analysis of our algorithm? Though we have written the implementation, we are not sure about how many resources our written code will utilize. When we say resource, we mean both time and storage resource utilized by the running application. We write algorithms to work with any length of the input. In order to understand how our algorithm behaves when the input grows larger and how many resources have been utilized, we usually measure the efficiency of an algorithm by relating the input length to the number of steps (time complexity) or storage (space complexity). It is very important to do the analysis of algorithms in order to find the most efficient algorithm to solve the problem.

We can do algorithm analysis in two different stages. One is done before implementation and one after the implementation. The analysis we do before implementation is also known as *theoretical analysis* and we assume that other factors such as processing power and spaces are going to be constant. The after implementation analysis is known as *empirical analysis* of an algorithm which can vary from platform to platform or from language to language. In empirical analysis, we can get solid statistics from the system regarding time and space utilization.

For our algorithm to place the books and finding the books from purchased items, we can perform a similar analysis. At this time, we will be more concerned about the time complexity rather than the space complexity. We will explore space complexity in coming chapters.

# Calculating the complexity

There are two types of complexity we measure in algorithmic analysis:

*   **Time complexity**: Time complexity is measured by the number of key operations in the algorithm. In other words, time complexity quantifies the amount of time taken by an algorithm from start to finish.

*   **Space complexity**: Space complexity defines the amount of space (in memory) required by the algorithm in its life cycle. It depends on the choice of data structures and platforms.

Now let us focus on our implemented algorithm and find about the operations we are doing for the algorithm. In our `placeAllBooks` function, we are searching for each of our ordered books. So if we have 10 books, we are doing the search 10 times. If the number is 1000, we are doing the search 1000 times. So simply, we can say if there is *n* number of books, we are going to search it *n* number of times. In algorithm analysis, input number is mostly represented by *n*.

For each item in our ordered books, we are doing a search using the `findABook` function. Inside the function, we are again searching through each of the received books with a name we received from the `placeAllBooks` function. Now if we are lucky enough, we can find the name of the book at the beginning of the list of received books. In that case, we do not have to search the remaining items. But what if we are very unlucky and the book we are searching for is at the end of the list? We then have to search each of the books and, at the end, we find it. If the number of received books is also *n*, then we have to run the comparison *n* times.
