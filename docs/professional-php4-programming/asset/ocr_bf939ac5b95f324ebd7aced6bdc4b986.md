Display a message (with a link to view the details of the added item) indicating that the item has been added to the user's cart:

```
The item <a href="#details"> <?php echo($row[1]) ?></a> has been added
to your cart. <br />
```

Generate an anchor element to view the items in the cart:

```
<a href="DisplayCart.php><?php echo(getSessionIdString()) ?>">
Display Cart
</a>
</p>
</card>
```

Item details card:

```
<card id="details">
```

Define a <do> element of type options to go to the main page of the application (AppMain.php):

```
<do type="options" label="HOME">
<go href="AppMain.php><?php echo(getSessionIdString()) ?>"/>
</do>
```

Define a <do> element of type accept, which takes them back to the main card of the same page:

```
<do type="accept" label="BACK">
<go href="#main"/>
</do>
<p>
```

Print the details of the item:

```
<?php
```

Print the title of the item:

```
printf("%s <br/>\n", $item->getTitle());
```

Print the artist/ author of the item:

```
if (strncasecmp($item->getItemType(), 'BOOK', 4) == 0) {
	printf("%s<br/>\n", $item->getAuthor());
} else {
	printf("%s<br/>\n", $item->getArtist());
}
```

Print the type of the item – book/CD/cassette: