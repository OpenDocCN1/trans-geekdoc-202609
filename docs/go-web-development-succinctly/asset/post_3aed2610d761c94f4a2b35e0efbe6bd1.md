
Everything should look familiar except the {{.Name}} entry. To Go templates, that is a variable. It's contained within double braces, and its name (Name) is preceded by a dot.

The dot signifies the scope or context of the variable. In our case, the Name variable refers to the Name field of a Person struct, which will become apparent when you see the definition for it that we'll use in our program logic:

```go
type Person struct {
  Name string
}
```

We can pass a Person struct to populate the template variable, and it will pull out the Name field and replace the variable definition in the template with it.

Note that any fields you refer to in the template must be exported. That is, they must begin with a capital letter. Unexported fields cause issues, as we will see in a bit.

Code Listing 11 shows the full program code.

# Code Listing 11: Using the Template

```go
package main

import (
  "log"
  "net/http"
  "text/template"
)

type Person struct {
  Name string
}

func main() {
  http.HandleFunc("/", handler)
  err := http.ListenAndServe(":8999", nil)
  if err != nil {
    log.Fatal("ListenAndServe: ", err)
  }
}
```

The only code of note here is in the handler function that is invoked when a user visits the root of our web application at http://localhost:8999.

Handler creates a variable p of Person and assigns "John Smith" to its Name field. We then use template.ParseFiles, passing in the name of the template file and assigning the results to variable t.

Having parsed the template file, we next need to perform the merge, which we do by calling Execute, which passes the http.ResponseWriter and the data item we want to merge with the template as parameters.

When we launch the application in a browser, we get Figure 15.

![](img/cdabbe899d95a91197e7ec37cc1c8048_39_0.png)

Figure 15: The Output of Our Simple Template

# Reworking the data access application using a template

Let's put our newfound knowledge of Go templates to work. First, we need to understand one of the many capabilities of a template—the ability to iterate over a set of results, then apply the appropriate formatting to each of them.

In order to achieve this, we must use the {{range}} {{end}} construct. We'll use the following template to build out our table. Everything between {{range}} and {{end}} will be repeated for every member of the object we pass into it.

Code Listing 12: The Template for "Cities" Database Application

```html
<html>
<head>
<title>City Search</title>
</head>
<body>
<h1>Search Results</h1>
<table border='1'>
  <tr>
    <th>City</th>
```

```html
    <tr>
    <th>Country Code</th>
    <th>Population</th>
  </tr>
  {{range .}}
  <tr>
    <td>{{.Name}}</td>
    <td>{{.CountryCode}}</td>
    <td>{{.Population}}</td>
  </tr>
  {{end}}
</table>
</body>
</html>
```

See the dot notation that appears just after the range keyword? That means "any object."

Something important to note about using ranges in Go templates—they will only accept a single object. "What?" I hear you say. "Why would something supposed to iterate through a slice of values only accept one?"

And you'd be right. The range allows us to put in an array or slice of values, then it will get into that object to pull out its members.

So, in our database application, we simply need to do a bit of refactoring to ensure that each of our query results gets added to a slice—let's call it cities—and we pass that slice into our template.

Code Listing 13: Using the Template in Our "Cities" Application

```go
package main

import (
	"database/sql"
	"html/template"
	"log"
	"net/http"

	"github.com/go-sql-driver/mysql"
)

type City struct {
	Name        string
	CountryCode string
	Population  int
}

var database *sql.DB

func main() {
	db, err := sql.Open("mysql", "root:password@tcp(127.0.0.1:3306)/world")
	if err != nil {
		log.Println("Could not connect!")
	}
	database = db
	log.Println("Connected.")

	http.HandleFunc("/", showCity)
	http.ListenAndServe(":8999", nil)
}

func showCity(w http.ResponseWriter, r *http.Request) {
	var cities []City
	queryParam := r.URL.Path[1:]
	rows, err := database.Query("SELECT Name, CountryCode, Population FROM city WHERE Name LIKE ?", queryParam)
	if err != nil {
		log.Fatal(err)
	}
	defer rows.Close()

	for rows.Next() {
		var theCity City
		err := rows.Scan(&theCity.Name, &theCity.CountryCode, &theCity.Population)
		if err != nil {
			log.Fatal(err)
		}
		cities = append(cities, theCity)
	}

	t, _ := template.ParseFiles("results.html")
	t.Execute(w, cities)
}
```

# Using methods in templates

Let's say we want to format the Population column with a comma separator. Go doesn't provide this out of the box, so we'll have to write our own method.

```go
func (c City) FormatPopulation(n int, sep rune) string {
	s := strconv.Itoa(n)
	var buff bytes.Buffer
	startOffset := 0
	if n < 0 {
		startOffset = 1
		buff.WriteByte('-')
	}
	l := len(s)
	commaIndex := 3 - ((l - startOffset) % 3)
	if commaIndex == 3 {
		commaIndex = 0
	}
	for i := startOffset; i < l; i++ {
		if commaIndex == 3 {
			buff.WriteRune(sep)
			commaIndex = 0
		}
		commaIndex++
		buff.WriteByte(s[i])
	}
	return buff.String()
}
```

Note that the function accepts an integer value and a separator and returns a string. You can think of the Go keyword as an alias for a Unicode character, which is sometimes called a “code point” in Go terminology.

In order to call this function within our template, we simply specify its name followed by any parameters (not in parentheses), as shown in Code Listing 15.

# Code Listing 15: Calling the FormatPopulation Function from the Template

```html
<html>
<head>
<title>City Search</title>
</head>
<body>
<h1>Search Results</h1>
<table border='1'>
  <tr>
    <th>City</th>
    <th>Country Code</th>
    <th>Population</th>
  </tr>
  {{range }}
  <tr>
    <td>{{.Name}}</td>
    <td>{{.CountryCode}}</td>
    <td>{{.FormatPopulation .Population ','}}</td>
  </tr>
  {{/range}}
</table>
</body>
</html>
```

When we execute the application, we get nicely formatted population values, as in Figure 17.

![](img/cdabbe899d95a91197e7ec37cc1c8048_44_0.png)

Figure 16: The Population Values, Formatted by the Template
