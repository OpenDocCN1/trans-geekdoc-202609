```
')
AND (genres @> $2 OR $2 = '{}')
ORDER BY id
```

That looks pretty complicated at first glance, so let’s break it down and explain what’s going on.

The `to_tsvector('simple', title)` function takes a movie title and splits it into *lexemes*. We specify the `simple` configuration, which means that the lexemes are just lowercase versions of the words in the title†. For example, the movie title "The Breakfast Club" would be split into the lexemes `'breakfast' 'club' 'the'`.

> † Other ‘non-simple’ configurations may apply additional rules to the lexemes, such as the removal of common words or applying language-specific stemming.

The `plainto_tsquery('simple', $1)` function takes a search value and turns it into a formatted *query term* that PostgreSQL full-text search can understand. It normalizes the search value (again using the `simple` configuration), strips any special characters, and inserts the *and operator* & between the words. As an example, the search value "The Club" would result in the query term `'the' & 'club'`.

The `@@` operator is the matches operator. In our statement we are using it to check whether the generated *query term matches the lexemes*. To continue the example, the query term `'the' & 'club'` will match rows which contain *both* lexemes `'the'` and `'club'`.