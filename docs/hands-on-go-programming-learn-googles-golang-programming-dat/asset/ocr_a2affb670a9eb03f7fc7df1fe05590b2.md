an error is not nil, it means there is an error and we cannot proceed further:

```
file, err := os.Open("myfile.txt")
if err != nil {
log.Fatal(err)
}
```

Sometimes a function may not return any meaningful value but it may cause an error. In that case, the function will only return an error. One example is the Mkdir function of os package as shown below:

```
func Mkdir(name string, perm FileMode) error
```