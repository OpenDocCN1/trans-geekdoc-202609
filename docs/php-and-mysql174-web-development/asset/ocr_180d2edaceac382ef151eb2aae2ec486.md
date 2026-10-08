![](bbox=[0.118, 0.111, 0.636, 0.403])

The script that generates this image is quite long. We split it into four parts, and we discuss each part separately. Most of the script is familiar, as you have seen many MySQL examples similar to this, and you have already looked at how to paint a background canvas in a solid color and how to print text labels on it.

The new parts of this script relate to drawing lines and rectangles. We will focus the bulk of our explanation on these sections. Part 1 (of this four-part script) is shown in Listing 21.5.1.

Listing 21.5.1 show_poll.php—Part 1 Updates the Vote Database and Retrieves the New Results

```
<php

// Check if we have the appropriate variable data
$vote = $_POST['vote'];

if (empty($vote))
{
    echo '<p>You have not voted for a politician.</p>';
    exit;
}

****************************************************
Database query to get poll info
****************************************************/
```