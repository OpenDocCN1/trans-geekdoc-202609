# CHAPTER 13. DISPLAYING ERRORS TO THE END USER

```
var buf bytes.Buffer
```

Buffer is a type that implements the Read and Write interface from the io package. There are many use cases for Buffer, but in this situation we are going to be using the buffer as a temporary location to execute our templates into. Once we have confirmed that there weren't any errors executing the template we will have the entire template stored inside of our Buffer, and we can copy it over to the ResponseWriter.

Remember: We are using a buffer because writing any data to Response will result in a 200 status code and we can't undo that write. By writing to a buffer first we can confirm that the entire template executes before we start writing any data to the ResponseWriter.

```
var buf bytes.Buffer
er := v.Template.Execute(&buf, v.Layout, data)
if err != nil {
    // We will handle this in a moment
}
// If we get that means our template executed correctly
// and we can copy the buffer to the ResponseWriter
io.Copy(w, &buf)
```

On the last line of our code we use the Copy¹³ function provided by the io package. This function takes in a Writer and a Reader, and then copies all the data in the Reader over to the Writer. In our code we are copying all of the data from the Buffer over to the ResponseWriter.

The last thing we need to implement is what to do when an error occurs executing our template. In this situation we are going to utilize the Error function provided by the net/http package, and we will set the message to be a generic “Something went wrong” message, along with a 500 HTTP status code signaling that we had an internal server error.

> ¹³https://golang.org/pkg/io/#Copy