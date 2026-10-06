# API DESCRIPTION FORMATS

books:
type: array
items:
  $ref: '#components/schemas/BookSummary'
  description: "A list of book summaries as a result of a list or filter request..."

```
BookSummary:
  title: BookSummary
  type: object
  properties:
    bookId:
      type: string
      description: An internal identifier, separate from the ISBN, that identifies the book within the inventory
    isbn:
      type: string
      description: The ISBN of the book
    title:
      type: string
      description: "The book title, e.g., A Practical Approach to API Design"
```

```
authors:
  type: array
  items:
    $ref: '#components/schemas/BookAuthor'
    description: "Summarizes a book that is stocked by the book store..."
```

```
BookAuthor:
  title: BookAuthor
  type: object
  properties:
    authorId:
      type: string
      description: An internal identifier that references the author
    fullName:
      type: string
      description: "The full name of the author, e.g., D. Keith Casey"
    description: "Represents a single author for a book. Since a book may have more than one author, ..."
```