# 5.2. Branching

```
case int, int8, int16, int32, int64:
    fmt.Printf("%d is an int\n", i)
case uint, uint8, uint16, uint32, uint64:
    fmt.Printf("%d is an unsigned int\n", i)
case nil:
    fmt.Printf("%d is nil\n", i)
case string:
    fmt.Printf("%d is a string\n", i)
default:
    fmt.Printf("%d's type is unknown\n", i)
}
}
```

The switch guard used here has the same format as a type assertion, that is variable.(Type), but using the keyword type instead of an actual type to stand for any type.

Sometimes we might want to access an interface{}s underlying value as well as its type (using the := operator), as we will see in a moment.

One use case for type testing is when we are dealing with data from external sources. For example, if we are parsing data using JSON (JavaScript Object Notation), we must somehow convert the data to the corresponding Go data types. This can be done using Go's json.Unmarshal() function. If we give the function a pointer to the struct's fields converting each item of JSON data into the data type of its corresponding struct. But if we do not know the JSON data's structure in advance we cannot give the json.Unmarshal() function a struct. In such cases we can give the function pointer to an interface{} which the json.Unmarshal() function will refer to a map[string]interface{} whose keys are JSON names and whose values are the corresponding values stored as interface{}.

Here is an example of how we can unmarshal a raw JSON object of unknown structure and how we can create and print a string representation of the JSON object.

```
MA := []byte("name": "Massachusetts", "area": 27336, "water": 25.7, "senators": ["John Kerry", "Scott Brown"]}")
```

```
var object interface{}
if err := json.Unmarshal(MA, &object); err != nil {
    fmt.Println(err)
} else {
    jsonObject := object.map(map[string]interface{})
```