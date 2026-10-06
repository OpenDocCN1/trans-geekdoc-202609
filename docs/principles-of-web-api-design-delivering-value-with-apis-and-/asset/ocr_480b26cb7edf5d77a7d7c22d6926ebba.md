| Resource Path | Operation Name | HTTP Method | Description | Request | Response |
| --- | --- | --- | --- | --- | --- |
| /books | listBooks() | GET | List books by category or release date | category/releaseDate | Book[] |
| /books/search | searchBooks() | POST | Search for books by author, title | searchQuery | Book[] |
| /books/(bookId) | viewBook() | GET | View book details | bookId | Book[] |
| /carts/(cartId) | viewCart() | GET | View the current cart and total | cartId | Cart |
| /carts/(cartId) | clearCart() | DELETE | Remove all books from the customer's cart | cartId | Cart |
| /carts/(cartId)/items | addItemToCart() | POST | Add a book to the customer's cart | cartId | Cart |
| /carts/(cartId)/items/(cartItemId) | removeItemFromCart() | DELETE | Remove a book from the customer's cart | cartItemId | Cart |
| /authors | getAuthorDetails() | GET | Retrieve the details of an author | author | BookAuthor |

Figure 7.6 Using the list of paths identified earlier, assign the appropriate path and HTTP method to each operation based on the intended usage.