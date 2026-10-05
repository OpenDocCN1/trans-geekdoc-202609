# 9.4. A Brief Survey of the Go Standard Library

If a value is passed in that doesn't support the len() function and doesn't have a Len() method, the generic Len function panics. We could have handled this error in other ways—for example, by returning -1 to signify “no length available”, or by returning an index and an error.

Go's reflect package is incredibly flexible and allows us to do things at runtime that depend on the program's dynamic state. However, to quote Rob Pike, reflection is “a powerful tool that should be used with care and avoided unless strictly necessary”.

# 9.5. Exercises

This chapter has three inter-related exercises. The first exercise involves the creation of a custom package. The second exercise involves the creation of a test for the package. And the third exercise is to write a program that makes use of the package. The exercises increase in difficulty with the third one being challenging.

+   1. Create a package, called say, my_linkutil (in file my_linkutil/my_linkutil.go). The package should provide two functions. The first function is LinksFromURL(string) ([]string, error) which given a URL string (e.g., “http://www.trac.au/index.html”), returns a slice of all the web page's unique anchor links (i.e., <a> tags' attribute values), and nil (or and error). The second function is LinksFromReader(io.Reader) ([]string, error) which does the same thing it only reads from an io.Reader (e.g., an open file or an http.Response.Body). The LinksFromURL function should use the LinksFromReader() function internally.

+   2. Go's standard library provides support for HTTP testing (e.g., the net/http/httest package), but for this exercise we will be content testing the my_linkutil.LinksFromReader() function developed in the previous exercise. To do this, create a test file (e.g., my_linkutil/my_linkutil_test.go) containing a single test, TestLinksFromReader(*testing.T). The test should read in an HTML file from the file which lists the file's unique anchor links, and it should compare the links found in the HTML file by the my_linkutil.LinksFromReader() function with the links in the file.

> * Rob Pike has written an interesting and useful blog entry on reflection, blog.golang.org/2011/09/laws-of-reflection.html.