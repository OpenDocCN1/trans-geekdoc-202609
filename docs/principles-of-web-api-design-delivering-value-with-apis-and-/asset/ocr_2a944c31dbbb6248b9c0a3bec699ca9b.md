# CHAPTER 6 API MODELING

| Property Name | Description |
| --- | --- |
| title | The book title |
| isbn | The unique ISBN of the book |
| authors | List of Book Author resources |

| Property Name | Description |
| --- | --- |
| books | The books currently in the cart for purchase |
| subtotal | The total cost of all books in the cart |
| salesTax | The sales tax to be applied |
| vatTax | Any value-added tax to be applied |
| cartTotal | The total cost of the cart |

> Is this an independent relationship?
Where does quantity go?

| Property Name | Description |
| --- | --- |
| fullName | The full name of the author |

**Figure 6.6** Reviewing the resource relationships introduces a challenge: where does the quantity of books belong?

6.6 shows the resources identified for the Shopping API, along with possible relationships. The relationship between a Book resource and Book Author resource is independent. There may be a reference between them, but each exists independently of the other.

Notice in Figure 6.6 that a question needs to be addressed regarding where the quantity is specified when a book is added to a cart. This issue needs to be explored further. When a book is added to a cart, additional details that may be important include the quantity and price of each book. This indicates an associative relationship that requires a new resource, in this case Cart Item. The result is shown in Figure 6.7.

The operation addBookToCart() is renamed removeItemToCart(), and removeBookFromCart() is renamed removeItemFromCart() to reflect the introduction of the Cart Item resource, as shown in Figure 6.8.

# Step 4: Add Operation Events

When the API taxonomy is expanded, each API operation with the significant events that it will emit. These events may be used for data analytics purposes or as events that other systems may react to when they occur of the operation.

The EventStorming canvas, created during the Align phase of the project, provides a starting point for important business events that were captured using the color-coded domain event sticky notes. If you didn't use EventStorming, capture the events as they are identified during the modeling process.