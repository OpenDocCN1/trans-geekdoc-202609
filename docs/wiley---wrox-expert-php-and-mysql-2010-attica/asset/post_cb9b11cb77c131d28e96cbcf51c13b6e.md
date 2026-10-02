
The validity function can be optimized now that the class has the ability to report its count. The method can assume that if the page being fetched is greater than the maximum number of pages, it must be empty. In that case, an empty array can be returned instead of executing a SELECT from the database. The bold lines of code were added in this revision of the method:

```
private function &touchPage( $pageNo=false ) {
    if ( $pageNo === false ) $pageNo = $this->currentPage;

    if ( !array_key_exists($pageNo,$this->pages) ) {
        if ( $pageNo > ceil($this->count()/$this->booksPerPage) ) {
            $this->pages[$pageNo] = array();
        } else {
            ..
        }
    }

    $tmp = &$this->pages[$pageNo];
    return $tmp;
}
```

In a more complex application with expensive queries, using count(*) on every page may be prohibitive. Caching yields better performance and avoids database hits. Caching is covered extensively in both Chapters 4 and 5.

> It is a good idea to stop and examine some of the implications of the code thus far. It is likely that in some cases, the count may become invalid while looping because it is calculated only once. If accuracy is necessary, it might be a good idea to do a write-lock on the table in the constructor and unlock it in the destructor. This will stall any scripts attempting to do a write to the table, so it is important that caution be taken when performing locks.

Another condition exists when the user moves to the next page. If a record has been added or deleted, the user may end up missing entries and possibly see the same entry on two consecutive pages. This can be avoided several ways:

- Passing the first entry on the next page via the query string along with the page number that is already being sent
- Caching the search results, either in a file, memory, or a temporary table in MySQL

However, in situations where the data is non-critical or updated infrequently (such as the book club application) it is acceptable to paginate using only the methods in this chapter.

## The SeekableIterator Interface and Pagination

The final feature that the class is missing is seeking a specific record. Without that ability, it is not possible to paginate and still stay within the parameters of the SPL. The SeekableIterator interface extends Iterator so a class does not need to indicate that it implements both of them. It also adds an additional method called seek(), which takes an integer as a parameter.

The seek() method will move the internal pointer for the object to the record that exists at a particular index. Seeking is unlike other methods that you have implemented thus far. Instead of waiting for a validity call it will immediately throw an OutOfBoundsException when trying to access a record that doesn't exist. Because you have implemented Countable it can easily check against those bounds. Seeking is also the only method that doesn't have an analog when dealing with arrays. Instead it must reset the array, then loop until the internal pointer hits the appropriate item:

```
public function seek( $index ) {
    if ( $index < 0 || $index > $this->totalBooks )
        throw new OutOfBoundsException();

    $this->currentPage = (int)floor($index/$this->booksPerPage)+1;
    $page = &$this->touchPage();
    reset($page);
    for ( $i= $index % $this->booksPerPage; $i>0; $i-- ) next($page);
}
```

Now that you have the ability to seek you can implement your Pagination class. The Pagination class is an extension of the IteratorIterator class that is also a part of the SPL. IteratorIterator implements OuterIterator, which, as the name implies, provides a wrapper around a second unseen iterator.

IteratorIterator provides you with one useful method: getInnerIterator(). Aside from that, every method needs to be rewritten. The new class is an iterator that loops through only the elements on a given page. Each method in the Iterator interface — which is also implemented by IteratorIterator — must know the bounds and act accordingly. In simple applications the inherited functionality of the other methods are acceptable and don't need to be re-implemented. Listing 2-2 shows this in action.

![](img/88e43d4c6a3d0e0d1f265975ce2f9f50_110_0.png)

### LISTING 2-2: Page.class.php

```
<?php
class Page extends IteratorIterator {
    private $page;
    private $currentItem;
    public $itemsPerPage;

    public function __construct( Iterator $iterator, $page, $itemsPerPage) {
        parent::__construct($iterator);
        $this->page = $page;
        $this->itemsPerPage = $itemsPerPage;
        $this->rewind();
    }

    public function valid() {
        return ( $this->currentItem != $this->itemsPerPage &&
            $this->getInnerIterator()->key() != null );
    }

    public function rewind() {
        $currentItem = 0;
        $this->getInnerIterator()->seek( ($this->page-1)*$this->itemsPerPage);
    }

    public function next() {
        if ( $this->currentItem < $this->itemsPerPage) {
            $this->currentItem++;
            $this->getInnerIterator()->next();
        }
    }

    public function current() {
        return ( $this->currentItem != $this->itemsPerPage
            ? $this->getInnerIterator()->current()
            : null );
    }
    public function key() {
        return ( $this->currentItem != $this->itemsPerPage
            ? $this->getInnerIterator()->key()
            : null );
    }
}?
```

Each method checks to make sure that the iterator is still within the bounds of the page. The current page and the number of records per page are passed to the constructor and then the rewind() method is called. The method is different than previous implementations because instead of going to the front of the inner iterator it goes to the first item on the selected page.

The new Page class can be extended to also implement the Countable and Seekable interfaces. For this application they are not needed so they are not covered in this chapter. If the new Page class is used in other applications, it is worth the time to implement the two additional interfaces. Each has only one method and can be written in under five lines of code.

You have now fully implemented everything you need to satisfy your use cases, but the application is far from being ready to deploy. It has a robust and easy-to-use reporting system but it still lacks the ability to insert, update, or delete records and the security that comes with those abilities. The next step is to create a Book class that has all the necessary operations. You can find full versions of the classes described in this chapter, as well as a Book class, on the Wiley web site. Chapter 12 covers adding authentication and user management. Before you go into that there is one more interface that you can add to the BookList class.

## The ArrayAccess Interface

The new application behaves almost exactly like an array. It implements every feature of an array that is needed for the use case. There is one piece of functionality missing that could conceivably be needed in future cases. That is the ability to access elements of the BookList using array notation. By implementing the ArrayAccess interface the BookList can be accessed randomly using a familiar $bookList[$i] notation and without changing the internal pointer to the current record.

If the keys returned by the key() method in the BookList class were not unique, this technique would not be able to function properly and you would only be able to access some of the books.

The ArrayAccess interface defines four methods that must be implemented. Three of the methods can be programmed easily. They are the methods to access, update, and check the validity of records based on a given key:

```
public function offsetExists( $offset ) {
    return ( $offset > 0 && $offset < count($this) );
}

public function offsetGet( $offset ) {
    $pageOfOffset = (int)floor($offset/$this->booksPerPage)+1;
    $page = &$this->touchPage( $pageOfOffset );
    return $page[ $offset % $this->booksPerPage ];
}

public function offsetSet( $offset, $newValue ) {
    $pageOfOffset = (int)floor($offset/$this->booksPerPage)+1;
    $page = &$this->touchPage( $pageOfOffset );
    $page[ $offset % $this->booksPerPage ] = $newValue;
}
```

The fourth method provides the ability to unset an element. This is problematic because there are a fixed number of elements on each page and you keep a hash table for all the book records. You can’t simply shift the entire result set downward. You also need to refill any partially filled pages and make sure that future calls to touchPage() are properly limited. You can accomplish this by using an array to track unlinks.

In this case, the new lower bound of the LIMIT in your query is now the total number of unlinks in all pages prior to the page currently being fetched subtracted from the original offset:

```
public function offsetUnset( $offset ) {
    $pageOfOffset = (int)floor($offset/$this->booksPerPage)+1;
    $page = &$this->touchPage( $pageOfOffset );

    $this->deletions[$pageOfOffset]++;
    ksort($this->deletions);
    unset( $page[ $offset % $this->booksPerPage ] );
    $page = array_values($page);
    while ( is_array($this->pages[$pageOfOffset+1]) ) {
        $this->pages[$pageOfOffset][] = array_shift($this->pages[++$pageOfOffset]);
    }
}
```
