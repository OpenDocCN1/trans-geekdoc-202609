
```go
    fmt.Println("----demo String To Numeric----")
    str_val1 := "5"
    str_val2 := "2.8769"

    var err error
    var int_val1 int64
    int_val1,err = strconv.ParseInt(str_val1,10,32) // base10, 64 size
    if err==nil {
        fmt.Println(int_val1)
    }else{
        fmt.Println(err)
    }

    var float_val2 float64
    float_val2,err = strconv.ParseFloat(str_val2,64)  // 64 size
    if err==nil {
        fmt.Println(float_val2)
    }else{
        fmt.Println(err)
    }
```

## 7.4 Numeric to String

It is easy to convert numeric to String type, you can use `fmt.Sprintf`. You can get string type automatically.

```go
    fmt.Println("----demo numeric to string----")
    num1 := 8
    num2 := 5.872

    var str_num1 string
    str_num1 = fmt.Sprintf("%d",num1)
    fmt.Println(str_num1)

    var str_num2 string
    str_num2 = fmt.Sprintf("%f",num2)
    fmt.Println(str_num2)
```

## 7.5 String Parser

The simple solution to parsing String uses `Split()` with delimiter parameter. For example, you have String data with `;` delimiter and want to parse it. Here is sample code

```go
    fmt.Println("----demo String Parser----")
    data := "Berlin;Amsterdam;London;Tokyo"
    fmt.Println(data)
    cities := strings.Split(data, ";")
    for _, city := range cities {
        fmt.Println(city)
    }
```

## 7.6 Check String Data Length

You can use `len()` to get the length of data.

```go
    fmt.Println("----demo String Length----")
    str_data := "welcome to go"
    len_data := len(str_data)
    fmt.Printf("len=%d \n",len_data)
```

## 7.7 Copy Data

You may copy some characters from String data. To do it, you can use `[start:end]` syntax. Here is syntax format:

```go
    fmt.Println("----demo copy data----")
    sample := "hello world, go!"
    fmt.Println(sample)
    fmt.Println(sample[0:len(sample)]) // copy all
    fmt.Println(sample[:5]) // copy 5 characters
    fmt.Println(sample[3:8]) // copy characters from index 3 until 8
    fmt.Println(sample[len(sample)-5:len(sample)]) // 5 copy characters from the end of string
```

## 7.8 Upper and Lower Case Characters

In some situation, you want to get all string data in upper or lower case characters. This feature is built in String object. `ToUpper()` function is used to make whole string in upper case and `ToLower()` is used to make whole string in lower case.

The following is a sample code to get upper and lower case characters.

```go
    fmt.Println("----demo upper/lower characters----")
    message := "Hello World, GO!"
    fmt.Println(message)
    fmt.Println(strings.ToUpper(message)) // upper chars
    fmt.Println(strings.ToLower(message)) // upper chars
```

## 7.9 Testing A Program

We can write our code in `main.go` completely as follows.

```go
package main

import (
    "fmt"
    "strconv"
    "strings"
)

func main(){

    // simple string demo
    var str string
    str = "Hello world"
    fmt.Println(str)


    // Concatenating
    str1 := "hello"
    str2 := "world"
    str3 := str1 + str2
    fmt.Println(str3)

    str4 := fmt.Sprintf("%s %s",str1,str2)
    fmt.Println(str4)


    // String To Numeric
    fmt.Println("----demo String To Numeric----")
    str_val1 := "5"
    str_val2 := "2.8769"

    var err error
    var int_val1 int64
    int_val1,err = strconv.ParseInt(str_val1,10,32) // base10, 64 size
    if err==nil {
        fmt.Println(int_val1)
    }else{
        fmt.Println(err)
    }

    var float_val2 float64
    float_val2,err = strconv.ParseFloat(str_val2,64)  // 64 size
    if err==nil {
        fmt.Println(float_val2)
    }else{
        fmt.Println(err)
    }

    // numeric to string
    fmt.Println("----demo numeric to string----")
    num1 := 8
    num2 := 5.872

    var str_num1 string
    str_num1 = fmt.Sprintf("%d",num1)
    fmt.Println(str_num1)

    var str_num2 string
    str_num2 = fmt.Sprintf("%f",num2)
    fmt.Println(str_num2)

    // String Parser
    fmt.Println("----demo String Parser----")
    data := "Berlin;Amsterdam;London;Tokyo"
    fmt.Println(data)
    cities := strings.Split(data, ";")
    for _, city := range cities {
        fmt.Println(city)
    }

    // String Data Length
    fmt.Println("----demo String Length----")
    str_data := "welcome to go"
    len_data := len(str_data)
    fmt.Printf("len=%d \n",len_data)

    // copy data
    fmt.Println("----demo copy data----")
    sample := "hello world, go!"
    fmt.Println(sample)
    fmt.Println(sample[0:len(sample)]) // copy all
    fmt.Println(sample[:5]) // copy 5 characters
    fmt.Println(sample[3:8]) // copy characters from index 3 until 8
    fmt.Println(sample[len(sample)-5:len(sample)]) // 5 copy characters from the end of string


    // Upper and Lower Case Characters
    fmt.Println("----demo upper/lower characters----")
    message := "Hello World, GO!"
    fmt.Println(message)
    fmt.Println(strings.ToUpper(message)) // upper chars
    fmt.Println(strings.ToLower(message)) // upper chars
}
```

Save this code.

Build and run `main.go` on your Terminal.

```
$ go build
$ go run main.go
```

A sample of program output:

![ch7-1](Images/ch7-1.png)

# 8. File Operations

This chapter explains how to work with file operations.

## 8.1 Getting Started

We can work with I/O file using `io` package, `http://golang.org/pkg/io/` .

For illustration, we can try to write and read text file. Firstly, we create a folder, called `fileio`.

```
$ mkdir fileio
$ cd fileio
```

The next step is to build Go application to write and read a file.

## 8.2 Writing Data Into A File

To write and read a file, we can use `io` package. In this section, we try to write data into a file.

Create a file, called `main.go`, and put it on `<go_project_root>/fileio` folder. Firstly, we define our packages which we use.

```
import (
    "fmt"
    "io/ioutil"
)
```

Then, create a function, called `writeFile()`. Write this code.

```
func writeFile(message string) {
    bytes := []byte(message)
    ioutil.WriteFile("d:/temp/testgo.txt",bytes,0644)
    fmt.Println("created a file")
}
```

You can see that we can create a file using `ioutil.WriteFile()`. We pass data in byte array format. You can change file name and its path.

## 8.3 Reading Data From A File

To read data from a file, we create a function, called `readFile()`. Write this code.

```
func readFile(){
    data, _ := ioutil.ReadFile("d:/temp/testgo.txt")
    fmt.Println("file content:")
    fmt.Println(string(data))
}
```

To read a content of file, we can use `ioutil.ReadFile()`. It return array of string.

Note: a file and its patch is similar to file on previous section.

## 8.4 Writing All

To simply, we can write our code in `main.go` file as follows.

```
package main

import (
    "fmt"
    "io/ioutil"
)

func main() {

    // write data into a file
    fmt.Println("writing data into a file")
    writeFile("welcome to go")
    readFile()

    // read data from a file
    fmt.Println("reading data from a file")
    readFile()

}

func writeFile(message string) {
    bytes := []byte(message)
    ioutil.WriteFile("d:/temp/testgo.txt",bytes,0644)
    fmt.Println("created a file")
}
func readFile(){
    data, _ := ioutil.ReadFile("d:/temp/testgo.txt")
    fmt.Println("file content:")
    fmt.Println(string(data))
}
```

Save this file.

Now you can build and run it.

```
$ go build
$ go run main.go
```

A sample output of program is shown in Figure below.

![ch8-1](Images/ch8-1.png)

# 9. Error Handling and Logging

This chapter explains how to handle errors and exceptions that occur in Go application.

## 9.1 Error Handling

Basically when we write a program and occur error on running, Go will catch program error. It will generate a panic.

For illustration, we create a project by creating a folder, `errorhandle`.

```
$ mkdir errorhandle
$ cd errorhandle
```

Then, create a file, `main.go`, and write this code.
