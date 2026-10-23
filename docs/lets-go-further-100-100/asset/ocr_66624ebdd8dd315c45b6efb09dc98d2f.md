```
"github.com/felixge/httpsnoop"
"github.com/pascaldekloe/jwt" // New import
"github.com/tomasen/realip"
"golang.org/x/time/rate"
)

...

func (app *application) authenticate(next http.Handler) http.Handler {
    return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
        w.Header().Add("Vary", "Authorization")

        authorizationHeader := r.Header.Get("Authorization")

        if authorizationHeader == "" {
            r = app.contextSetUser(r, data.AnonymousUser)
            next.ServeHTTP(w, r)
            return
        }

        headerParts := strings.Split(authorizationHeader, " ")
        if len(headerParts) != 2 || headerParts[0] != "Bearer" {
            app.invalidAuthenticationTokenResponse(w, r)
            return
        }

        token := headerParts[1]

        // Parse the JWT and extract the claims. This will return an error if
        the JWT
        // contents doesn't match the signature (i.e. the token has been
        tampered with)
        // or the algorithm isn't valid.
        claims, err := jwt.HMACCheck([]byte(token),
        []byte(app.config.jwt.secret))
        if err != nil {
            app.invalidAuthenticationTokenResponse(w, r)
            return
        }
    }
```