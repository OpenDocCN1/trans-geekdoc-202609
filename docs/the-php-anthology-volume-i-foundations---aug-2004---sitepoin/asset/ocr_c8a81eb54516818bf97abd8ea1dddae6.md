```
/**
 * Fetch the header
 */
function getHeader()
{
    return $this->header;
}
}
```

Now, the subclass CategoryHeader brings extra functionality to its parent, adding the "bread crumb" links to the HTML that was generated. We don't need to re-create the setHeader and getHeader methods, as these are inherited from StandardHeader when CategoryHeader is instantiated.

File: 12.php (excerpt)

```
/**
 * Subclass for dealing with Categories, building a breadcrumb
 * menu
 */
class CategoryHeader extends StandardHeader {
    /**
     * Constructor, taking the category name and the pages base URL
     */
    function CategoryHeader($category, $baseUrl)
    {
        // Call the parent constructor
        parent::StandardHeader($category);

        // Build the breadcrumbs
        $html = <<<EOD
<p><a href="{$baseUrl}">Home</a> >
        <a href="{$baseUrl}?category=$category">{$category}</a></p>
EOD;
        // Call the parent setHeader() method
        $this->setHeader($html);
    }
}
```

Let's now put these two classes to use:

File: 12.php (excerpt)

```
// Set the base URL
$baseUrl = '12.php';

// An array of valid categories
```