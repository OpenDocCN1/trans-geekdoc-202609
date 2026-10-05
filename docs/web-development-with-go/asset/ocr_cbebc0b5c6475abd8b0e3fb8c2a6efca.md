# 638 CHAPTER 16. DEPLOYING TO PRODUCTION

```
Port: 3000,
Env: "dev",
Pepper: "secret-random-string",
HHMACKey: "secret-hmac-key",
Database: DefaultPostgresConfig(),
}
```

We are going to write the code used to load our JSON config file into the Config type and return it. If a JSON config file isn't present, we will have this function call back on the default. To do this, we are going to use the encoding/json package, which allows us to Convert Go structures into JSON, and vice versa.

In case we want to go from JSON to a Go type, so we need to decode JSON data into a Go struct. To do this, we will use the NewDecoder function⁴ accepts an io.Reader as its only argument and returns a pointer to a Decoder⁵ The reader argument to the NewDecoder function call can be any type of reader, but in case it is going to be the config JSON file we open up.

Note: You may sometimes hear this referred to as unmarshalling JSON data into a Go structure as well.

Once we have a Decoder we can use it to decode the file and place the results into a Config struct by calling the Decoder's Decode method⁶.

It sounds like a lot, but it is really only a few lines of code. Most of the code below is to explain what we are doing.

```
import (
// Add these imports as you need them
"encoding/json"
"fmt"
"os"
)
```

+   ⁴https://golang.org/pkg/encoding/json/#NewDecoder
⁵https://golang.org/pkg/encoding/json/#Decoder
⁶https://golang.org/pkg/encoding/json/#Decoder.Decode