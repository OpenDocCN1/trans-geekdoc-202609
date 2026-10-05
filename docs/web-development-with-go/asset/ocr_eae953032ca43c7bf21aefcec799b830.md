# CHAPTER 16. DEPLOYING TO PRODUCTION

```
$ atom models/services.go
import (
"github.com/jinzhu/gorm"
"github.com/jinzhu/gorm/dialects/postgres"
)
func NewServices(dialect, connectionInfo string) (*Services, error) {
db, err := gorm.Open(dialect, connectionInfo)
// .. nothing else changes
}
```

And then the main function...

```
$ atom main.go
func main() {
cfg := DefaultConfig()
dBCfg := DefaultPostgresConfig()
services, err := NewServices(dbCfg.Dialect,
dBCfg.ConnectionInfo())
// .. Unchanged code here

// .. our routes are unchanged
// Delete the IsProd var
nisprod = false
ber, err := rand.Bytes(32)
if err != nil {
panic(err)
}
// Use the config's IsProd method instead
csrfMW = csrf.Protect(b, csrf.Secure(cfg.IsProd))

// Our port is not provided via config, so we need to
// update the last bit of our main function.
fmt.Printf("Starting the server on %d...\n", cfg.Port)
http.ListenAndServe(fmt.Sprintf(":%d", cfg.Port),
csrfMW(userMW.Apply(r)))
}
```