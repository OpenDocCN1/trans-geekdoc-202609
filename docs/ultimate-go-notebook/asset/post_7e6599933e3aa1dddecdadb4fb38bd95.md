
The Table type has three fields: hash function, the number of buckets, and the data which is represented as a slice of key/value pairs. The outer slice represents buckets and the inner slice represents key/value pairs that are stored inside a bucket.

Now I can apply generics syntax to declare the key and value generic types and apply them to the field declarations.

# Listing 9.42

```go
type Table[K comparable, V any] struct {   <-- CHANGED
    hashFunc hashFunc[K]                 <-- CHANGED
    buckets int
    data [][]KeyValuePair[K, V]
}
```

After the name, I add the square brackets with the generic types K and V. The hashFunc type declaration requires information about the concrete type to use for the key. The keyValuePair type declaration requires information about the concrete type for the key and value.

This is a factory function that can construct a Table for use.

# Listing 9.43

```go
func New(
    buckets int,
    hf hashFunc,
) *Table {
    return &Table{
        hashFunc: hf,
        buckets: buckets,
        data: make([][]KeyValuePair, buckets),
    }
}
```

The factory function accepts the number of buckets to manage and a hash function for selecting a bucket for data storage and lookup. When a Table value is constructed, the number of buckets is used to construct the slice, the length of the outer slice to the number of buckets that will be used.

Now I can apply the generics syntax to declare the key and value generic types and apply them to the types that need to be constructed.

# Listing 9.44

```go
func New[K comparable, V any](                  <-- CHANGED
    buckets int,
    hf hashFunc[K],                           <-- CHANGED
) *Table[K, V] {                             <-- CHANGED
    return &Table[K, V]{
        hashFunc: hf,
        buckets:  buckets,
        data:     make([][]KeyValuePair[K, V], buckets), <-- CHANGED
    }
}
```

After the type name, I add the square brackets and the generic types K and V. Then K is applied to the hf input parameter to complete the hashFunc declaration. The K and V types are applied to the Table type being constructed and returned. Finally, the initialization of the data field requires K and V to be applied to the construction syntax for the keyValuePair type.

This is a method that can insert values into the hash table based on a specified key.

# Listing 9.45

```go
type Table[K comparable, V any] struct {
    hashFunc hashFunc[K]
    buckets  int
    table    [][]keyValuePair[K, V]
}

func (t *Table) Insert(key K, value V) {
    bucket := t.hashFunc(key, t.buckets)

    for idx, kvp := range t.table[bucket] {
        if key == kvp.Key {
            t.table[bucket][idx].Value = value
            return
        }
    }

    kvp := keyValuePair{
        Key:   key,
        Value: value,
    }
    t.table[bucket] = append(t.table[bucket], kvp)
}
```

The Insert method is declared to accept a key and value of the same generic types that are declared with the Table type. The first step of inserting is to identify the bucket to use for storage. That is performed by calling the hash function with the specified key. The hash function returns an integer value that represents the bucket to use.

Then the function checks to see if the key has already been used to store a value in the selected bucket. This is performed by ranging over the existing set of key/value pairs in the bucket. If the key already exists, the value for that key is updated. If the key is not found, then a new key/value pair value is constructed,

initialized, and appended to the slice for the selected bucket.

Now I can apply the generic syntax to declare the key and value generic types and apply them to the types that need to be constructed.

# Listing 9.46

```go
func (t *Table[K, V]) Insert(key K, value V) {    // CHANGED
	bucket := t.hashFunc(key, t.buckets)
	for idx, kvp := range t.table[bucket] {
		if key == kvp.Key {
			t.table[bucket][idx].Value = value
			return
		}
	}
	kvp := keyValuePair[K, V]{                                     // CHANGED
	Key: key,
	Value: value,
	}
	t.table[bucket] = append(t.table[bucket], kvp)
}
```

After the type in the receiver, I add the square brackets and the generic types K and V. The only change is to apply K and V to the construction syntax of the keyValuePair type.

This is a method that can retrieve values from the hash table based on a specified key.

# Listing 9.47

```go
func (t *Table) Retrieve(key K) (V, bool) {
	bucket := t.hashFunc(key, t.buckets)

	for idx, kvp := range t.data[bucket] {
		if key == kvp.Key {
			return t.data[bucket][idx].Value, true
		}
	}

	var zero V
	return zero, false
}
```

The Retrieve method is declared to accept a key and return a value. The first step of retrieving is to identify the bucket to use for storage. That is performed by calling the hash function with the specified key. The hash function returns an integer value that represents the bucket to use.

Then the function checks to see if the key has already been used to store a value in the selected bucket. This is performed by ranging over the existing set of key/value pairs in the bucket. If the key already exists, the value for that key is returned. If the key is not found, then the zero value is returned.

Now I can apply the generic syntax to declare the key and value generic types and apply them to the types that need to be constructed.
