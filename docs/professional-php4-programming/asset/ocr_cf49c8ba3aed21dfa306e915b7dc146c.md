```
?>
<card id="<?php echo($itemNo) ?>" >
<do type="accept" label="ADD">
<go href="AddToCart.php?selectedItem=<?php echo($itemNo . "&amp;" . getSessionIdString()) ?>"/>
</do>
<do type="options" label="BACK">
<go href="#main" />
</do>
</card>
</p>
<?php
printf("%s<br/>\n",
$musicShopContent[$generateDescCard[$i]]->getTitle());
printf("%s<br/>\n",
$musicShopContent[$generateDescCard[$i]]->getArtist());
printf("%s<br/>\n",
$musicShopContent[$generateDescCard[$i]]->getItemType());
printf("$$%2.2f\n",
$musicShopContent[$generateDescCard[$i]]->getPrice());
?>
</p>
</card>
<?php
} //end for
?>
</wml>
```

# # Search

The PHP script DoSearch.php does the search on the book titles and music albums. It displays the search results:

```
<?php
include_once("Common.php");
include_once("BookShop.php");
include_once("MusicShop.php");

header("Content-Type: text/vnd.wap.wml");
setSessionHandlers();
```

If the user session is not authenticated then send an error page:

```
checkSessionAuthenticated();
```

If the value of the session variable $searchContent is null, it means that this page is called for the first time:

```
if (!$searchContent) {
    $currentIndex=0;
    $bookShop = new Book_Shop();
    $musicShop = new Music_Shop();
```