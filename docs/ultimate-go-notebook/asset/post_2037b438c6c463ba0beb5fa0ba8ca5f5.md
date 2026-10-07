
# Listing 7.3

```go
package sample_test

import (
    "testing"
    "http"
)

func TestDownload(t *testing.T) {
    url := "https://www.ardanlabs.com/blog/index.xml"
    statusCode := 200

    resp, err := http.Get(url)
    if err != nil {
        t.Fatalf("unable to issue GET on: %s: %s", url, err)
    }
    defer resp.Body.Close()

    if resp.StatusCode != statusCode {
        t.Log("exp:", statusCode)
        t.Log("got:", resp.StatusCode)
        t.Fatal("status codes don't match")
    }
}
```

In this test, I plan to test the ability to download the RSS feed for Ardan Labs blog. First, I declare some variables with the URL to download and the expected status code. I then perform the httpGet call for the URL and check the error. It is critical that any function that returns an error has the error value checked. If there is an error, I call t.Fatal to report the problem and the test fails. If there is no error, I proceed to the next step which is checking the status code.

Before checking the status code, I prepare the close call for the response body. Always write tests like production code. If I don't get back the status code I expect, I provide verbose information about what I expected and what I got. This really helps with debugging failed tests. Then I call t.Fatal to report the test has failed. This is a test that only outputs information if the test fails.

# 7.2 Table Unit Test

Table tests can be powerful when I have code that can be run through a series of different inputs and expected outputs. They are perfect for negative path testing.

# Listing 7.4

```go
package sample_test

import (
    "testing"
    "http"
)

func TestDownload(t *testing.T) {
    tt := []struct {
        url        string
        statusCode int
    }{
        {"https://www.ardlanabs.com/blog/index.xml", http.StatusOK},
        {"http://rss.cnn.com/rss/cnn-topstory.rss", http.StatusNotFound},
    }

    for _, test := range tt {
        resp, err := http.Get(test.url)
        if err != nil {
            t.Fatal("unable to issue GET on URL: %s", test.url, err)
        }
        defer resp.Body.Close()

        if resp.StatusCode != test.statusCode {
            t.Log("exp:", test.statusCode)
            t.Fatal("status codes doesn't match")
        }
    }
}
```

In this test, I am checking URLs and potential status codes. The table is a slice of literal struct that has two fields: url to test and the expected status code. Two entries are added to the table, the first one is the positive path test, the second is a negative path test for a bad URL.

The test code is similar to the first test except the input is coming from iterating over the table. This allows me to add more entries over time without the need to write more code. The table can be anything from a slice to a map or any data structure I can iterate over and provide input and expected output.

# 7.3 Web Mocking

I am a fan of mocking when it can be avoided. The use of Docker provides lots of opportunities to hit real systems over mocked behavior. I need to remember, a mock is only as good as the behavior being simulated. If the behavior changes in an upgrade of a system, the mock is no longer representative of the correct behavior. Mocks can be useful for negative path testing when it's difficult to cause real systems to fail on demand.

When it comes to making web calls to external systems, the standard library already provides support for mocking web calls. This is great for testing API behavior without the cost of a real web call. Especially if the testing environment is on a private network with no access to the outside world.

# Listing 7.5

```go
package sample_test

import (
    "testing"
    "http"
    "httptest"
)

var feed = `<?xml version="1.0" encoding="UTF-8"?>
<rss>
<channel>
    <title>Ardan Labs</title>
    <item>
        <title>Go Programming</title>
        <description>This is mechanics</description>
        <link>http://www.ardanlanabs.com/mechanics</link>
        <pubDate>Sun, 15 Mar 2015 00:00:00 +0000</pubDate>
    </item>
</channel>
</rss>`

func mockServer() *httptest.Server {
    server := httptest.NewServer(func(w http.ResponseWriter, r *http.Request) {
        w.Header().Set("Content-Type", "application/xml")
        fmt.Fprint(w, feed)
    })
    return server
}
```

# Listing 7.6

```go
package sample_test

import (
    "encoding/xml"
    "fmt"
    "http"
    "net/http/httptest"
    "testing"
)

func TestDownload(t *testing.T) {
    statusCode := 200

    server := mockServer()
    defer server.Close()

    resp, err := http.Get(server.URL)
    if err != nil {
        t.Fatalf("unable to issue GET on URL: %s", server.URL, err)
    }
    defer resp.Body.Close()

    if resp.StatusCode != statusCode {
        t.Log("exp:", statusCode)
        t.Log("got:", resp.StatusCode)
        t.Fatal("status codes doesn't match")
    }

    var d Document
    if err := xml.NewDecoder(resp.Body).Decode(&d); err != nil {
        t.Fatal("unable to decode the response:", err)
    }
}
```

# Listing 7.7

```go
type Item struct {
	Title       string `xml:"title"`
	Description string `xml:"description"`
	Link        string `xml:"link"`
}
```

```go
// defines the fields associated with the channel.
type Channel struct {
	XMLName     xml.Name `xml:"channel"`
	Title       string   `xml:"title"`
	Description string   `xml:"description"`
	Link        string   `xml:"link"`
	PubDate     string   `xml:"pubDate"`
	Items       []Item   `xml:"item"`
}
```

```go
// defines the fields associated with the root.
type Document struct {
	XMLName xml.Name `xml:"rss"`
	Channel Channel  `xml:"channel"`
}
```

```go
func TestDownload(t *testing.T) {
	statusCode := 200

	server := mockServer()
	defer server.Close()

	resp, err := http.Get(server.URL)
	if err != nil {
		t.Fatalf("unable to issue GET on URL: %s", server.URL, err)
	}
	defer resp.Body.Close()

	if resp.StatusCode != statusCode {
		t.Log("exp:", statusCode)
		t.Log("got:", resp.StatusCode)
		t.Fatal("status codes don't match")
	}

	var d Document
	if err := xml.NewDecoder(resp.Body).Decode(&d); err != nil {
		t.Fatal("unable to decode the response:", err)
	}

	if len(d.Channel.Items) != 1 {
		t.Fatal("not seeing 1 item in the feed: %d", len(d.Channel.Items))
	}
}
```

# 7.4 Internal Web Endpoints

If I'm building a web service, I will want to test the endpoints without the need to build and run the service. The goal is to load the router with the endpoints and execute those endpoints without the need of all the networking stuff. The standard library provides support for this.
