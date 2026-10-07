![](bbox=[0.298, 0.095, 0.701, 0.33])

Figure 6: Visting a Subroute

Entering localhost:8999/site displays the index.html page.

![](bbox=[0.298, 0.407, 0.701, 0.642])

Figure 7: Visiting/Site

Lets expand our ability to serve static files in this example. Suppose that the URL in the request starts with /static/ and we want to strip the /static part of the URL in order to look for the file referenced in the remaining path the /var/www directory. We can use the StripPrefix function to achieve this, as we see in Code Listing 3.

Code Listing 3: Using StripPrefix

```
package main
import (
    "fmt"
    "html"
    "log"
)
```