# 4.6 Passing arrays to functions

When you pass an array to a function, they are passed by value like the int or string data type. The function receives only a copy of it. Hence, when you make changes to an array inside a function, it won’t be reflected in the original array. But this is not the case with a slice which you will study in the next chapter.

In Go language, you can pass an array as an argument in the function. For passing an array as an argument in the function, you should first create a formal parameter using the following syntax.

For sized array:

```
func function_name(variable_name [size]type){
// function body
}
```

Or, for unsized array:

```
func function_name(variable_name []type){
// function body
}
```