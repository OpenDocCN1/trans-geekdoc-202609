
## Chapter 7.6: Service (SRV)

The net.LookupSRV() function accepts a service, protocol, and domain name as a string. It returns a canonical name as a string along with a slice of SRV structs. An SRV struct supports a Target as a string and Port, Priority, and Weight as uint16's. The net.LookupSRV() function attempts to resolve an SRV query of the service, protocol, and domain name, sorted by priority and randomized by weight within a priority.

```go
package main

import (
	"fmt"
	"net"
)

func main() {
	cname, srvs, _ := net.LookupSRV(
		"xmpp-server", "tcp", "google.com")

	fmt.Printf("\ncname: %s \n\n", cname)

	for _, srv := range srvs {
		fmt.Printf("%v:%v:%v:%d:%d\n",
			srv.Target, srv.Port,
			srv.Priority, srv.Weight)
	}
}
```

The output below demonstrates the CNAME return, followed by the respective SRV record target, port, priority, and weight separated by a colon.

```
cname: _xmpp-server._tcp.google.com.

xmpp-server.l.google.com.:5269:5:0
alt2.xmpp-server.l.google.com:5269:20:0
alt1.xmpp-server.l.google.com:5269:20:0
alt3.xmpp-server.l.google.com:5269:20:0
alt4.xmpp-server.l.google.com:5269:20:0
```

## Chapter 7.7: Text (TXT)

The net.LookupTXT() function accepts a domain name as a string and returns a list of DNS TXT records as a slice of strings.

```go
package main

import (
	"fmt"
	"net"
)

func main() {
	txts, _ := net.LookupTXT("gmail.com")

	for _, txt := range txts {
		fmt.Println(txt)
	}
}
```

The single TXT record for gmail.com is shown below.

```
v=spf1 redirect=_spf.google.com
```

## Chapter 8: Regex Pattern Matching

Regular expression pattern matching is used to match a sequence of characters that are defined by a search pattern. The regexp package leverages the fast and thread-safe RE2 regular expression engine. While it does not support backtracking, it does guarantee linear time execution. This chapter covers simple matching, match groups, named matches, template expansion, and multi-line split.

This chapter will cover the following regex pattern topics:

- Simple matching
- Match groups
- Named capture groups
- Template expansion
- Multi-line delimited split

## Chapter 8.1: Simple Matching

Simple pattern matching covers the basic concept of returning a result from processing a regular expression pattern against a data set. In this example, the data set is first identified and then the regexp.MustCompile() function is used to define the pattern. The pattern leverages the \w+ syntax to match one or more word characters on either side of the dot. Then, using the dataset as input, the regexp.Regexp.FindString() method is called on the pattern to return the result. If multiple string matches were needed from the pattern, the regexp.Regexp.FindAllString() method would have been used and a slice returned.

```go
package main

import (
	"fmt"
	"regexp"
)

func main() {
	data := `# host.domain.tld #`
	pattern := regexp.MustCompile(`\w+\.\w+\.\w+`)
	result := pattern.FindString(data)

	fmt.Println(result)
}
```

The simple match using the \w+.\w+.\w+ pattern against the data set is shown below.

```
host.domain.tld
```

## Chapter 8.2: Match Groups

Using parentheses in the search pattern identifies individual match groups. Subpatterns are placed within parentheses to identify each individual matched group across the data set. In this example, match groups are demonstrated by matching each of the three sections of a domain name into their own group.

To start, the data set is identified and then the regexp.MustCompile() function is used to define the pattern. The pattern uses the \w+ syntax to match one or more word characters on either side of the dot. Then, using the dataset as input, the regexp.Regexp.FindAllStringSubmatch() method is called to return a two-dimensional slice, where the first slice value is the entire set of matches and each consecutive value is the respective matched group. A -1 is used as an input to the regexp.Regexp.FindAllStringSubmatch() method which signifies unlimited matches; otherwise, a positive number could have been set to limit the result.

```go
package main

import (
    "fmt"
    "regexp"
)

func main() {
    data := `# host.domain.tld #`

    pattern := regexp.MustCompile(
        `\(\\w+).(\\w+).(\\w+)`)

    groups := pattern.FindAllStringSubmatch(
        data, -1)

    fmt.Printf("\n%q\n", groups)
    fmt.Printf("groups[0][0]: %s\n", groups[0][0])
    fmt.Printf("groups[0][1]: %s\n", groups[0][1])
    fmt.Printf("groups[0][2]: %s\n", groups[0][2])
    fmt.Printf("groups[0][3]: %s\n", groups[0][3])
}
```

The output below first demonstrates the entire match, followed by each individual group.

```
[["host.domain.tld" "host" "domain" "tld"]]
groups[0][0]: host.domain.tld
groups[0][1]: host
groups[0][2]: domain
groups[0][3]: tld
```

## Chapter 8.3: Named Capture Groups

When a regular expression becomes complicated, it is helpful to document and reference the purpose of each capture group by name. Since group names and positions are fixed, they can be referenced using the regexp.Regexp.SubexpNames() method. The group index within the slice matches the corresponding index in the slice that is returned by the regexp.Regexp.FindStringSubmatch() method, which is then used to build a map as demonstrated in the example below.

This example first identifies the data set and then uses the regexp.MustCompile() function to define the pattern. The pattern uses the \w+ syntax to match one or more word characters on either side of the dot. Since named capture groups are used, each pattern is defined with the (?P<name>re) syntax, where name is the capture group name. Then, using the dataset as input, the regexp.Regexp.FindStringSubmatch() method is called to return a slice, where the first slice value is the leftmost match. Next, a map is created to hold the result and then the slice that is returned from the regexp.Regexp.SubexpNames() method is looped over, which returns each name of the parenthesized subexpressions. As each name is iterated over, the subexpression name is checked to ensure it is not empty. If the name is valid, the map entry is created using the name as the key and the corresponding submatch index value as the value, before finally printing the new map.

```go
package main

import (
  "fmt"
  "regexp"
)

func main() {
  dat := `# host.domain.tld #`
  pat := regexp.MustCompile(
	`(?P<third>\w+).(?P<sec>\w+).(?P<first>\w+)`)

  mch := pat.FindStringSubmatch(dat)

  res := make(map[string]string)

  for i, name := range pat.SubexpNames() {
	if i != 0 && name != "" {
			res[name] = mch[i]
	}
  }

  ff := fmt.Printf
  ff("\n%\n", res)
  ff("res[\"first\"]: %s\n", res["first"])
  ff("res[\"sec\"]: %s\n", res["sec"])
  ff("res[\"third\"]: %s\n", res["third"])
}
```

The output below first demonstrates the entire match, followed by each value that is referenced by the named match key in the result map.

```
map["third":"host" "sec":"domain" "first":"tld"]
result["first"]: tld
result["sec"]: domain
result["third"]: host
```

## Chapter 8.4: Template Expansion

Template expansion captures regular expression pattern matches and expands them into a string template. This example demonstrates template expansion by using the regexp.Regexp.ExpandString() method to take a group of matches from the regular expression and expand them into the template.

To begin the example, the data set is identified as the source and then the regexp.MustCompile() function is used to define the pattern. The pattern uses the \w+ syntax to match one or more word characters on either side of the dot. Next, the string template is defined. It takes the named match as a variable by prefixing it with a dollar sign. Then, each matched line is looped over and returned from the regexp.Regexp.FindAllStringSubmatchIndex() method. Each match is then expanded into the template by using the regexp.Regexp.ExpandString() method to produce the output.

```go
package main

import (
    "fmt"
    "regexp"
)

func main() {
    src := `
host1.domain.tld some text
host2.domain.tld more text
`

    re := regexp.MustCompile(
        `(?m)(?P<thir>\w+).(?P<sec>\w+).(?P<fir>\w+)\s(?P<text>.*?)$`)

    tpl := "$thir.$sec.$fir.\tIN\tTXT\t\"$text\"\n"
```
