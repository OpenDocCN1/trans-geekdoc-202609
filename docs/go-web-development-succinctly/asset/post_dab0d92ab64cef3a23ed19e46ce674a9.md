
# Code Listing 33: city.go

```go
package main

type City struct {
    Id         int    `json:"id"`
    Name       string `json:"name"`
    Country    string `json:"country"`
    District   string `json:"district"`
    Population int    `json:"pop"`
}
```

# Code Listing 34: The DBUpdate Struct in dbupdate.go

```go
package main

type DBUpdate struct {
    Id       int64 `json:"id"`
    Affected int64 `json:"affected"`
}
```

# Running the application

We can test the application from a browser, but that will involve a bit of fiddling around with the developer console and more clicks than necessary.

Instead

If you have a Mac or Linux machine, curl is probably already available to you. If you have Windows, the easiest way to access it is by downloading the Git Bash which contains curl and a wealth of other useful tools. There's even a Bash shell for Windows—see https://msdn.microsoft.com/en-us/commandline/wsl/about. It's handy to have around even if you don't use Git. Another alternative (although, in my opinion, a more bloated alternative) is Cygwin.

You can download Git Bash at https://git-for-windows.github.io.

# Displaying all cities

Open two shells.

Run the application in the first shell by executing `go run *.go` in the same folder as your application modules, as in Figure 24.

```bash
MINGW64 /C:/HOME/code/src/github.com/marklewin/go-web-succinctly/ch05
marklewLAPTOP-QVVF5MV9 MINGW64 ~/code/src/github.com/marklewin/go-web-succinctly/ch05 (master)
$ city.go database.go dbupdate handlers.go main.go router.go routes.go
marklewLAPTOP-QVVF5MV9 MINGW64 ~/code/src/github.com/marklewin/go-web-succinctly/ch05 (master)
$ go run *
2017/02/16 20:19:56 Connected.

marklewLAPTOP-QVVF5MV9 MINGW64 ~/code/src/github.com/marklewin/go-web-succinctly/ch05
$ |
```

Figure 23: Running the Application

Next, enter the following command in the second shell window:

```bash
curl -i localhost:8999/city
```

The -i flag instructs curl to include the HTTP header.

You should see a JSON representation of every city in the City table, as shown in Figure 25.

```bash
MINGW64:/c/HOME
marklewLAPTOP-QVVF5MV9 MINGW64 ~
$ curl -i localhost:8999/city
% Total % Received % Xfered Average Speed Time Time Current Speed
% 0 0 0 0 0 0 -- -- -- -- -- OHT
HTTP/1.1 200 OK
Content-Type: application/json
Date: Thu, 16 Feb 2017 20:22:29 GMT
Transfer-Encoding: chunked
[ {"id":1,"name":"Kabul","country":"AFG","district":"atric","name":"Kabul","pop":1782000},{"id":2,"name":"Aghzabad","country":"AFG","district":"Qandahar","pop":2375000},{"id":3,"name":"Herat","country":"AFG","district":"Herat","name":"Herat","pop":186800},{"id":4,"name":"Mazar-e-Sharif","country":"AFG","district":"Balkh","name":"Balkh","pop":1278000},{"id":5,"name":"Amsterdam","country":"NLD","district":"North-Holland","name":"North-Holland","pop":93368},{"id":6,"name":"Rotterdam","country":"NLD","district":"Zuid-Holland","name":"Zuid-Holland","pop":593321},{"id":7,"name":"Hague","country":"NLD","district":"Zuid-Holland","name":"Hague","pop":440900},{"id":8,"name":"Utrecht","country":"NLD","district":"Utrecht","name":"Utrecht","pop":316000},{"id":9,"name":"Eindhoven","country":"NLD","district":"North-Brabant","name":"North-Brabant","pop":201843},{"id":10,"name":"Tilburg","country":"NLD","district":"Nord-Brabant","pop":193283},{"id":11,"name":"Groningen","country":"NLD","district":"Groningen","pop":172701},{"id":12,"name":"Breda","country":"NLD","district":"Noord","pop":163000},{"id":13,"name":"Aapeldeorn","country":"NLD","district":"Gelderland","pop":153491},{"id":14 }]
```

Figure 24: Requesting All Cities

# Displaying a specific city

With the application still running in the first shell window, enter the following in the second shell window:

```bash
curl -i localhost:8999/city/1028
```

You should see details for the city with the ID of 1028—namely, Hyderabad in India. Enter some random IDs and see which cities are referenced.

Figure 25: Requesting own City by ID

# Adding a city

In the second shell window, enter the following:

```bash
curl -H "Content-Type: application/json" -d '{"name":"Whoville","country":"ITA","district":"XXX","pop":1}' http://localhost:8999/cityadd
```

> Tip: Take care when entering the JSON object that represents the new city. JSON is simple, but it is not forgetting to close braces, or if you put quotes (that denote the string type) around a value that is expected to be an integer.

The record should be added to the database and you should receive the new ID in the response, as in Figure 27.

```bash
MINGW64 /C:/HOME/go/src/github.com/marklewin/go-web-succinctly/ch05
marklewLAPTOP-QVVF5MV9 MINGW64 ~/code/src/github.com/marklewin/go-web-succinctly/ch05 (master)
$ curl -X 'Content-Type: application/json' -d '{"name":"whoville","country":"ITA","district":"XXX","pop":1}' http://localhost:8999/cityadd
% Total % Received % Xfered Average Speed Time Time Current Speed
Download Upload Spent Speed
100 87 100 24 100 63 307 807 -- ------ --
```

Figure 26: Adding a New City

In the previous example, the ID of my recently added record is 4093. Yours is probably different. Rather than query the database manually or in order to see if the new record exists, you can use the following:

```bash
curl -i localhost:8999/city/4093
```

However, take to replace 4093 with whatever ID was assigned when you added the city.

```bash
MINGW64 /C:/HOME/go/src/github.com/marklewin/go-web-succinctly/ch05
marklewLAPTOP-QVVF5MV9 MINGW64 ~/code/src/github.com/marklewin/go-web-succinctly/ch05 (master)
$ curl -i localhost:8999/city/4093
% Total % Received % Xfered Average Speed Time Time Current Speed
Download Upload Spent Speed
100 70 100 0 0 437 0 -- ------ --
3HT
HTTP/1.1 200 OK
Content-Type: application/json
Date: 16 Feb 2017 20:31:28 GMT
Content-Length: 70

{"id":"4093","name":"Whoville","country":"ITA","district":"XXX","pop":1}
```

Figure 27: Verification—New City Added to the Database

# Deleting a city

In order to delete a city, you use a syntax similar to search for a city by ID. Try using the same city ID that you just added to the database. For example:

```bash
curl -i localhost:8999/city/4093
```

If everything proceeds to plan, you should get a DBUpdate object encoded as JSON, which shows a single row is affected, as in Figure 29.

```bash
MINGW64:/c/HOME/code/src/github.com/marklewin/go-web-succinctly/ch05
marklewLAPTOP-QVVF5MV9 MINGW64 ~/code/src/github.com/marklewin/go-web-succinctly/ch05 (master)
$ curl -X http://localhost:8999/city/4093
% Total % Received Xfered Average Speed Time Time Spent Current Speed
100 24 200 OK 24 0 0 1/1 0 --- --- 192
/3HT
HTTP/1.1 200 OK
Content-Type: application/json
Date: Thu, 16 Feb 2017 20:35:16 GMT
Content-Length: 24

{"id":"4093","affected":1}
```

Figure 28: Deleting a City

Congratulations! You have just written your first "real" service using Go.

Of course, this is far from perfect, and if you were planning to put it into production, you would probably want to do a fair bit of refactoring, implement better error handling, and so on.

However, the point of all this is to emphasize that Go is an excellent language for working on this type of application. I have done similar work in other languages, including Node.js and Ruby, and I am much happier working in Go. Everything seems much tidier and better thought out, in my humble opinion.
