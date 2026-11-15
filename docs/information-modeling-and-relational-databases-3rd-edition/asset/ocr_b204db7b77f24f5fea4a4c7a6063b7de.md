be constants, or the results produced by other functions (i.e., a parameter can be a call to another function). Now, we have another hierarchy: functions that provide results to functions that provide ... and so on. This *function* hierarchy may be established dynamically and may bear no direct relationship to the *data* hierarchy. The top level of the function hierarchy computes the result we are seeking; the lower-level functions provide results to their parents to (ultimately) enable the top-level computation. XQuery defines more than a hundred built-in functions, but commercial systems may not yet implement all of these.

XQuery allows information to be combined from multiple sources and restructured to produce a new result. The most common expressions of this kind in XQuery are called FLWOR expressions, from the first letter of the types of clauses that may appear in the expression: **for**, **let**, **where**, **order by**, and **return**. FLWOR expressions are the XQuery equivalent of *select* statements in SQL.

The clauses in a FLWOR expression are defined in terms of *tuples*. The tuples are created by binding variables to values in **for** and/or **let** clauses, so every FLWOR expression must have at least one **for** or **let** clause. The difference between the two is that **for** iterates over the items in an expression, producing a tuple for each, and **let** produces one tuple for the entire result of an expression. As a simple example, the following FLWOR expression produces the same result as the last path example in Table 16.2. The dollar sign “$” indicates a variable in XQuery.

```
for $m in movie
where $m/star = “Tom Hanks”
return $m/released
```

As a slightly more complex example, let’s assume that we want to invert the hierarchy of the source XML. For our Movies XML fragment, we could list the movies in which an actor starred under each actor, instead of listing the stars under each movie. An expression in XQuery to do this might look like the following:

```
for $s in distinct-values ( movie/star )
order by $s descending
return
<starring>
<actor>{ $s }</actor>
<movies>{ for $m in movie where $m/star = $s return $m/title }</movies>
</starring>
```

Here, we've used the distinct-values () function to make sure that each actor only appears once and sorted the result in descending order of actor name. The query contains *constructors*, indicated by braces around an inner expression, which are used to build element content. Evaluating the query produces the result: