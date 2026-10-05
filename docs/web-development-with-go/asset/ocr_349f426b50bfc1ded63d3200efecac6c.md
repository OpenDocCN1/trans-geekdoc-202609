# 18.2. REFACTORING WITH GORENAME 717

```
$ get golang.org/x/tools/cmd/gorename
```

gorename needs two pieces of information to work - the variable, type, or function that you will be renaming, along with the new name you want to use. With that information it will parse all of your Go code attempting to update comments and references to that code with the changed name. This can be really handy when refactoring some code that is used by many different packages you have coded in the past.

To give a real example of this, we are going to rename the ErrInvalidID and ErrInvalidPassword variables that get refactored in Section 12.7.

The first variable we will look at is ErrInvalidID. We want to rename this to ErrInvalidID, but this isn't necessary in the section. It is also typically a good idea to wrap he package in double quotes, and to wrap the entire string in a single quote just to ensure there aren't any unexpected issues.

```
$ gorename -from "'lenslocked.com/models'.ErrInvalidID' -to 'ErrInvalidID'
```

When doing this you typically need to define the entire package in the from portion, but this isn't necessary in the section. It is also typically a good idea to wrap he package in double quotes, and to wrap the entire string in a single quote just to ensure there aren't any unexpected issues.

# Box 18.1. gorename errors

As we discussed earlier, gorename process all of the code in your GOPATH, so if there is an issue with any of this code it is possible you will see an error when using the rename tool. The error message might be long, but it will typically end with a message like:

```
gorename: couldn't load packages due to errors: some/package/name
```