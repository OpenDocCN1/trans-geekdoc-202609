# SELECTING A REPRESENTATION FORMAT

```
{
  "name" : "isbn",
  "value" : "978-0321834577",
  "label" : "ISBN",
  "rel" : ["https://schema.org/isbn"],
},
{
  "name" : "title",
  "value" : "Example Book",
  "label" : "Book Title",
  "rel" : ["https://schema.org/name"],
{
  "name" : "description",
  "value" : "With Implementing Domain-Driven Design, Vaughn has made an important contribution not only to the literature of the Domain-Driven Design community, but also to the literature of the broader enterprise application architecture field.\n  "label" : "Book Description",
  "rel" : ["https://schema.org/description"],
{
  "name" : "authors",
  "rel" : ["collection","http://example.org/rels/authors"],
  "data" : [
    {
      "id" : "author-765",
      "rel" : ["https://schema.org/Person"],\n      "url" : "http://example.org/authors/765",
      "data" : [
        {
          "name" : "authorId",
          "value" : "765",
          "label" : "Author ID"
        },
        {
          "name" : "fullName",
          "value" : "Vaughn Vernon",
          "label" : "Full Name",
          "rel" : "https://schema.org/name"
        }
      ]
    }
  ]
}
}]]]
```