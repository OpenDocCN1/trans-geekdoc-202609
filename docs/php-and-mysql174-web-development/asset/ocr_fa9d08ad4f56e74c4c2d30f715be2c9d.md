# Chapter 27 Building User Authentication and Personalization

Listing 27.26 recommend.php—This Script Suggests Some Bookmarks That a User Might Like

```
<?php
require_once('bookmark_fns.php');
session_start();
do_html_header('Recommended URLs');\ntry {
    check_valid_user();
    $urls = recommend_urls($_SESSION['valid_user']);
    display_recommended_urls($urls);
} catch(Exception $e) {
    echo $e->getMessage();
}
display_user_menu();
do_html_footer();
?
```

Listing 27.27 recommend_urls()Function from url_fns.php—This Works Out The Actual Recommendations

```
function recommend_urls($valid_user, $popularity = 1) {
// We will provide semi intelligent recommendations to people
// If they have an URL in common with other users, they may like
// other URLs that these people like
    $conn = db_connect();

// find other matching users
    // with an url the same as you
    // as a simple way of excluding people's private pages, and
    // increasing the chance of recommending appealing URLs, we
    // specify a minimum popularity level
    if ($popularity = 1, then more than one person must recommend it before we recommend it
$query = "select bm_URL
from bookmark
where username in
    (select distinct(b2.username)
    from bookmark b1, bookmark b2
    where b1.username='.'$valid_user.'
    and b1.username != b2.username
    and b1.bm_URL = b2.bm_URL)
    and bm_URL not in
    (select bm_URL
    from bookmark
    where username='.'$valid_user.')";
```