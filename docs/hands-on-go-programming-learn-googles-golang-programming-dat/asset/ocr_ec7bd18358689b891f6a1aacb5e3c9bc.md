# 12.1.1 The error interface

Go has a built-in interface called error which has only one method, i.e., The Error method returns string type is as shown below:

```
type error interface {
Error() string
}
```

Go has a package called The errors package has an un-exported errorString struct type. The errorString is an implementation of the error interface because it implements the Error() method. The code snippet given below is the full code of the error package:

```
package errors
```

```
func New(text string) error {
return &errorString{text}
}
```

```
type errorString struct {
s string
}
```

```
func (e *errorString) Error() string {
```