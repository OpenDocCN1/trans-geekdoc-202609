store some data at a memory address in the system.

You can also use a pointer to a struct with the help of the & operator, i.e., the address operator. It is allowed to access the fields of a structure using the pointers without any dereferencing explicitly in Golang.

In Go, any struct type that starts with a capital letter is exported and accessible from outside packages. Similarly, any struct field that starts with a capital letter is exported. Any struct type that starts with a small letter is visible only inside the same package.

Structs are value types in Golang, i.e., when a value-type instance is created, a single space in memory is allocated to store the value. When you assign one struct variable to another, a new copy of the struct is created and assigned. Similarly, when you pass a struct to another function, the function gets its copy of the

Two struct variables are equal if their corresponding fields are all equal.