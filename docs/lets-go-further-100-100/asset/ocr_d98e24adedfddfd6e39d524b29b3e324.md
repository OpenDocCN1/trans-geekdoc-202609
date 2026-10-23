```
Date: Tue, 06 Apr 2021 07:02:01 GMT
Content-Length: 19

404 page not found
```

# Creating a helper to read ID parameters

The code to extract an `id` parameter from a URL like `/v1/movies/:id` is something that we’ll need repeatedly in our application, so let’s abstract the logic for this into a small reuseable helper method.

Go ahead and create a new `cmd/api/helpers.go` file:

```
$ touch cmd/api/helpers.go
```

And add a new `readIDParam()` method to the `application` struct, like so:

```
File: cmd/api/helpers.go

package main

import (
    "errors"
    "net/http"
```