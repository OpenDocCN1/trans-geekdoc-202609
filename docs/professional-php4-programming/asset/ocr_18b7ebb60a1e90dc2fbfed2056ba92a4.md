# WML Document Type Declaration:

```
<!DOCTYPE wml PUBLIC "-//WAPFORUM//DTD WML 1.1//EN"
"http://www.wapforum.org/DTD/wml_1.1.xml">
<wml>
```

# Main card of the application:

```
<card id="main">
<p>
```

# Print greeting message:

```
Welcome <?php echo($user->getUserId() ) ?>
<select ivalue="1">
```

Generate link for search. The action of the link points to the search card of the same WML page:

```
<option title="SRCH">
<onevent type="onpick">
<go href="#search"/>
</onevent>
Search
</option>
```

Generate link to view all the book titles. The action of the link points to ViewBookShop.php. Note that the session id string is added to the URL:

```
<option title="BOOK">
<onevent type="onpick">
<go
href="ViewBookShop.php?<?php echo(getSessionIdString()) ?>"/>
</onevent>
Book Shop
</option>
```

Generate link to view all the music albums. The action of the link points to ViewMusicShop.php:

```
<option title="MUSC">
<onevent type="onpick">
<go
href="ViewMusichShop.php?<?php echo(getSessionIdString()) ?>"/>
</onevent>
Music Shop
</option>
```

Generate link to display the contents of the user's cart. The action of the link points to DisplayCart.php:

```
<option title="DISP">
<onevent type="onpick">
<go
```