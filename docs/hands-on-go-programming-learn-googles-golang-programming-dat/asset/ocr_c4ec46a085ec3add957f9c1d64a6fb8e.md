The following will be the output for the above program:

# Error 8.3:

```
```text
./main.go:16:15: cannot use s (type Student) as type Person in
argument to processPerson
```
```

In _Program_ we have defined Person with id and name fields and Student with Person as embedded and There is a function processPerson() which expects a Person as a parameter. We have created a value of Student type and have tried to pass it to the processPerson() function. It gives a compilation error saying that we cannot use Student type as Person type in the argument to

We can call the processPerson() function by passing Person value which is part of Student value:

```
```go
processPerson(s.Person)
```
```

Method overloading is also not allowed in Go. The compiler will complain if we try to do method overloading.