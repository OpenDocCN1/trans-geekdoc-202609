| Method | URL Pattern | Handler | Action |
|---|---|---|---|
| POST | /v1/users | registerUserHandler | Register a new user |
| PUT | /v1/users/activated | activateUserHandler | Activate a specific user |
| POST | /v1/tokens/authentication | createAuthenticationTokenHandler | Generate a new authentication token |

If you're following along, go ahead and create a new `cmd/api/tokens.go` file:

```
$ touch cmd/api/tokens.go
```

And in this new file we'll add the code for the `createAuthenticationTokenHandler`.

Essentially, we want this handler to *exchange the user's email address and password for an authentication token*, like so:

```
File: cmd/api/tokens.go

package main

import (
    "errors"
    "net/http"
    "time"

    "greenlight.alexedwards.net/internal/data"
    "greenlight.alexedwards.net/internal/validator"
)
```