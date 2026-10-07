And favour Composition too.

```
<?php
class DespatchedOrder extends OrderAbstract
{
    public function isDespatched()
    {
        return true;
    }

    public function canBeCancelled()
    {
        return false;
    }
}
```

This seems to be a highly appropriate solution to the issue. The code involved is nice and clear and easy to read. When the business team comes rushing over to our desk next time with a new order status to implement, couldn't we just roll out another child class to represent that status?

We could, but there are two key issues with this approach. One highlights the need to consider the code that we write in the context of a living, breathing, functioning application. In other words, on the page this looks fine and dandy. In the real world, we will be faced with problems.

How so? For starters, if we're in the business of turning pending orders into despatched orders, we know that our orders are going to have to transition from one to the other. That means we're guaranteed to have points in our order lifecycle where the status changes because if it doesn't, we're going to go bust.

With an inheritance hierarchy to represent the order status, that would mean we either have to re-hydrate a new order object with an updated status or set an incorrect status into our existing order object. Which should we chose? The inefficient route or the invalid route.

The answer of course should be neither.

The other problem that will occur with an approach of this type arises from the fact that most of the details held within an order object should be cacheable. When we think in terms of cache-ability, we need to consider the anticipated lifetime of the data and our expectations of what will change when.