```
message AddCartItemRequest {
  string cart_id = 1;
  string book_id = 2;
  int32 quantity = 3;
}
```

```
message RemoveCartItemRequest {
  string cart_id = 1;
  string cart_item_id = 2;
}
```

```
message Cart {
  string cart_item_id = 1;
  Book book = 2;
  int32 quantity = 3;
}
```

```
message Cart {
  string cart_id = 1;
  repeated CartItem cart_items = 2;
}
```

That's it! The RPC-based API now has a high-level design. Details can now be added to complete the API and code generators used to jumpstart the development and integration work. Generating human-readable documentation is also recommended using a tool such as prot-gen-doc.

Keep in mind that owing to RPC's tight coupling with code, any code changes will have a direct impact on the design of an RPC-based API. Put another way, RPC-based API designs are replaced, not modified, when code changes are applied.

Notice how most of the effort took place in the API modeling step. By using the API modeling technique as the foundation of the design effort, the work of bridging the desired outcomes of the customer is easily mapped into an RPC-based design. Should additional API styles be required, such as REST, the same API modeling work can be reapplied to the design effort for the API style of choice.

# What Is a Query-Based API?

Query-based APIs offer robust query capabilities and response shaping. Using support fetching a complete resource representation by identifier, paginated listing of resource collections, and resource collection filtering using simple and advanced

> https://github.com/pseudomuto/protoc-gen-doc