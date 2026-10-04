```
if err == io.EOF {
    break
}
if err != nil {
    log.Fatal(err)
}
fmt.Println(record)
}
```

Example 8.2 writes CSV recs to standard output. Every CSV record is a string array that has to be passed to the Write method. Finally, the Flush method ensures that we send all the buffered data to the standard output.

The writing process follows a similar approach as shown in Example 8.2. Instead of converting strings to CSV records, the writer works operateously.

# Example 8.2: CSV writing.

```
package main
import (
    "encoding/csv"
    "os"
)

func main() {
    out := [][]string{
        {"user_id", "score", "password"},
        {"Gopher", "1000", "admin"},
        {"Bigj", "10", "1234"},
        {"GGoom", "", "11111"},
    }
    writer := csv.NewWriter(os.Stdout)
    for _, rec := range out {
        err := writer.Write(rec)
        if err != nil {
            panic(err)
        }
    }
    writer.Flush()
}
```

![](bbox=[0.748, 0.435, 0.882, 0.503])

# 8.2 JSON

The JavaScript Object Notation [4] (JSON) is a light-weight data interchange format defined by ECMA in 1999. It has turned extremely popular because it is human readable and easy to parse. JSON processing operators are available at encoding/json. This package provides Marshal and Unmarshal functions that convert types to a JSON representation in []byte, and vice versa.