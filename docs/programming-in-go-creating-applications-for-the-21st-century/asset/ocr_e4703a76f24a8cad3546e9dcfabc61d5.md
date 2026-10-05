# 7.2. Examples

channel since we never use it in a context where it is checked for being closed.
By blocking, this function ensures that the processing gets done before the main
goroutine terminates.

```
func showResults(pageMap safemap.SafeMap) {
	pages := pageMap.Close()
	for page, count := range pages {
		fmt.Printf("%d %s\n", count, page)
	}
}
```

Once all the lines have been read and all the matches added to the safe map,
this function begins by calling the safemap.
safemap.Close() method which closes the safe map's channel, terminates the
safemap.run() method executing in a goroutine, and returns the underlying
map[string]interface{} to the caller. The returned map can no longer be accessed
using the safe map's channel and can be safely used in a single goroutine (or
multiple goroutines if we serialize accesses using a mutex). From this point,
only the map in the main goroutine, so no serialization is necessary. We
impletely iterate over the map's key-value pairs and print them to the console.

Using a value type SafeMap interface provides thread safety and simple syntax
 no need to concern ourselves with locks. One disadvantage of this approach
is that the safe map's values are generic interface{} values rather than of a speci-
type, hence the need to use a type assertion in the incrementer() function.
(We will discuss another disadvantage later on; §7.2.4.3, ► 347.)

# 7.2.4.2. Synchronizing with a Mutex-Protected Map

We now compare and contrast the clean channel-based approach to the
ditional mutex-based approach. To do this we briefly discuss the apache-
port2 program (in apacheport2/apacheport.go). This is a variation of the
apacheport1 program which uses a custom data type that encapsulates a map
and mutex instead of using a SafeMap. The two programs do the same job but
are different in that the apacheport2 program stores its values in its map
rather than the interface{} is used by the generic SafeMap, and also provides
the minimal and specific functionality required to do the job—an Increment()
method—compared to the safe map's complete set of methods.

```
type pageMap struct {
	countPage map[string]int
	mutex     *sync.RWMutex
}
```

One advantage of using a specific custom type is that we can use the exact
types that we need rather than having to use the generic interface{} type.