# 16. ADDING DATA USING THE WEB APPLICATION

*PHP Code and HTML Markup for Form*

Listing 16.4 is what the PHP code and HTML markup look like for the entire form.

# Listing 16.4.

```
<?php
$genres = [
    'Action', 'Adventure', 'Comedy', 'Documentary', 'Drama',
    'Fantasy', 'Horror', 'Romance', 'Science Fiction'
];
?>
...
<form class=&quot;needs-validation&quot; novalidate method=&quot;POST&quot;
    action=&quot;<?=$_SERVER['PHP_SELF']?>"
<div class=&quot;form-group row&quot;>
    <label for=&quot;movie_title&quot;
        class=&quot;col-sm-3 col-form-label-lg&quot;>Title</label>
<div class=&quot;col-sm-8&quot;>
    <input type=&quot;text&quot; class=&quot;form-control&quot; id=&quot;movie_title&quot;
        name=&quot;movie_title&quot; placeholder=&quot;Title&quot; required>
    <div class=&quot;invalid-feedback&quot;>
        Please provide a valid movie title.
    </div>
</div>
</div>
<div class=&quot;form-group row&quot;>
    <label for=&quot;movie_rating&quot;
        class=&quot;col-sm-3 col-form-label-lg&quot;>Rating</label>
<div class=&quot;col-sm-8&quot;>
    <select class=&quot;custom-select&quot; id=&quot;movie_rating&quot;
        name=&quot;movie_rating&quot; required>
        <option value=&quot;&quot; disabled selected>Rating...</option>
        <option value=&quot;G&quot;>G</option>
        <option value=&quot;PG&quot;>PG</option>
        <option value=&quot;PG-13&quot;>PG-13</option>
        <option value=&quot;R&quot;>R</option>
    </select>
    <div class=&quot;invalid-feedback&quot;>
        Please select a movie rating.
    </div>
</div>
</div>
<div class=&quot;form-group row&quot;>
    <label for=&quot;movie_director&quot;
        class=&quot;col-sm-3 col-form-label-lg&quot;>Director</label>
<div class=&quot;col-sm-8&quot;>
    <input type=&quot;text&quot; class=&quot;form-control&quot; id=&quot;movie_director&quot;
        name=&quot;movie_director&quot; placeholder=&quot;Director&quot; required>
```