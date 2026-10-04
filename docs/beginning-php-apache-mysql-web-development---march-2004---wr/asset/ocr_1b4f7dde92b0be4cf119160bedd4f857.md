# Chapter 2

```
<BODY>
<?php include header.php"; ?>
<?php
$favamovies = array("Life of Brian","Stripes","Office Space","The Holy Grail",
"Matrix","Terminator 2","Star Wars","Close Encounters of the Third Kind",
"Sixteen Candles","Caddyshack");



// /delete these lines:
function listmovies_1()
{
    echo "1. Life of Brian<br>";
    echo "2. Stripes<br>";
    echo "3. Office Space<br>";
    echo "4. The Holy Grail<br>";
    echo "5. Matrix<br>";
}

function listmovies_2()
{
    echo "6. Terminator 2<br>";
    echo "7. Star Wars<br>";
    echo "8. Close Encounters of the Third Kind<br>";
    echo "9. Sixteen Candles<br>";
    echo "10. Caddyshack<br>";
}

// /end of deleted lines

if (ISSET($_REQUEST['favmovie'])) {
    echo "Welcome to our site, ";
    echo \$_SESSION['username'];";
    echo "<br>";
    echo "My favorite movie is: ";
    echo \$_REQUEST['favmovie'];";
    echo "<br>";
    \$movierate=5;
    echo "My movie rating for this movie is: ";
    echo \$movierate;
}
else {
    echo "My top 10 movies are:<br>";


    if (ISSET($_REQUEST['sorted'])) {
        sort(\$favamovies);
    }


    // /delete these lines
    echo \$_REQUEST['movienum'];
    echo " movies are: ";
    echo "<br>";";
}

listmovies_1();
If (\$_REQUEST['movienum'] == 10) listmovies_2();
```