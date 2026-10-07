
The raw memory profile breaks things down by stack, however at the very top there is some information that's interesting.

# Listing 11.12

```
heap profile: 7: 59424 [12335: 286125512] @ heap/1048576

[7]          Currently live objects,
[59424]      Amount of memory occupied by live objects
[12335]      Total number of allocations
[286125512] Amount of memory occupied by all allocations
```

Those first four numbers represent wide information for this snapshot of the memory profile. Then for each stack, there is similar information.

# Listing 11.13

```
1: 40960 [245: 1035200] @

[1]          Currently live objects,
[40960]      Amount of memory occupied by live objects
[245]      Total number of allocations
[1035200] Amount of memory occupied by all allocations
```

It's nice to have some understanding of the raw numbers, but this is not a productive way to read the profile data.

## 11.5 Viewing Memory Profile

I'm going to use the profile tooling as explained in chapter 10 to explore the memory profile. What's cool is I can give the pprof tool the URL to the memory profile and it can use that to read it in.

# Listing 11.14

```
$ go tool pprof -nonlines http://localhost:5000/debug/pprof/allocs

Fetching profile over HTTP from http://localhost:5000/debug/pprof/allocs
Type:alloc_space
Time: May 10, 2021 at 1:48pm (CDT)

Entering interactive mode (type "help" for commands, "o" for options)
pprof
```

The problem now is I don't know what I'm specifically looking for. I really want to find any low hanging fruit, therefore I will use the top command to get a list of the top 15 functions that are allocating the most memory.

# Listing 11.15

```
(pprof) top 15 -cum

Showing nodes accounting for 3300.39MB, 53.67% of 6148.89MB total
Dropped 90 nodes out of 47
Showing top 15 nodes cum cum%
flat flat% sum% cum cum%
0 0% 0% 3675.30MB 59.77% net/http.(*conn).serve
385.68MB 6.27% 3675.30MB 59.42% github.com/ardlan/gotraining/topics/go/profiling/project/service.handler
0 0% 3675.30MB 59.42% github.com/braintree/manners.
(*HandleFunc).ServeHTTP
0 0% 3675.30MB 59.42% net/http.(*ServeMux).ServeHTTP
0 0% 3675.30MB 59.42% net/http.HandlerFunc.ServeHTTP
617.76MB 10.05% 16.32% 3055.08MB 49.68% net/http.serverHandler.ServeHTTP
github.com/ardlan/gotraining/topics/go/profiling/project/service.render
48.01MB 0.78% 17.10% 2445.06MB 39.76% ngithub.com/ardlan/gotraining/topics/go/profiling/project/search.rssSearch
1.08MB 0.016% 17.12% 2437.26MB 39.64% github.com/ardlan/gotraining/topics/go/profiling/project/search.executeTemplate
(*Template).Execute
0 0% 17.12% 2436.26MB 39.62% html/template.
2.50MB 0.041% 17.16% 2436.28MB 39.62% text/template.
(*Template).execute
0 0% 17.16% 2437.66MB 39.58% text/template.(*state).walk
225.93MB 36.46% 53.52% 2393.58MB 38.93% strings.ToLower
9.51MB 0.15% 53.67% 2006.99MB 32.64% ngithub.com/ardlan/gotraining/topics/go/profiling/project/search.CNN.Search
0 0% 53.67% 1935.06MB 31.47% fmt.Fprint
```

(pprof)

I added the -switch to the top command to sort the list by the cumulative value. Using the socket connection and max at the top of the list makes sense since all traffic flows through that node. Having the template calls makes sense because rendering HTML will produce allocations.

What comes next to call the search.rssSearch function.

# Listing 11.16

```
flat flat% sum% cum cum%
48.01MB 0.78% 17.10% 2445.06MB 39.76%
github.com/ardlan/gotraining/topics/go/profiling/project/search.rssSearch
```

Top is telling me that this function 39.76% of the total allocations which is worth a total of 2.4 gig. This is a function that I should look at. Maybe I can find some non-productive allocations that could be removed to reduce the amount of GC that needs to take place to complete this work. If I reduce allocations, and therefore reduce the number of GC, I will get better performance.

I will use the list to review the search.rssSearch function.

# Listing 11.17

```
(pprof) list rssSearch
Total: 6GB
ROUTINE ================= project/search/rss.go
48.01MB      2.39GB(flat, cum) 39.76% of Total
20.50MB      20.50MB       79: var d := xml.NewDecoder(resp.Body)
3.52MB       2.34GB      119:      if strings.Contains(strings.ToLower(item.Description), term)) {
27.51MB      27.51MB      120:      result = append(results, Result(

I've trimmed it down to list the lines that are causing allocations. Of the 2.39 GB coming from this function, line 119 2.34GB of that code I need to focus on.

# Listing 11.18

```
118  for _, item := range d.Channel.Items {
119      if strings.Contains(strings.ToLower(item.Description), term) {
120          result = append(results, Result{
121              Engine: engine,
122              Title: item.Title,
123              Link: item.Link,
124              Content: item.Description,
125      })
126  }
127}
```

When I look at the code on line 119 from search/rss.go file, I see there is a call to strings.Contains and strings.ToLower inside a loop. That loop is checking if the term matches each item for one specific feed. Since I have 12 feeds, for each request this loop is run 12 times. I know a large number of allocations are happening here on line 119, but can I tell it's because of the call to strings.Contains or strings.ToLower? Looking at a call that is isolated to the search.rssSearch function will help.

# Listing 11.19

```
(pprof) webSearch
```

For the call graph to be generated, it's important to make Graphviz is installed. This is the website for more information: https://www.graphviz.org/

# Figure 11.4

img/8be06d78925d0a5d2e9bad63_230.png

The call graph makes it clear that the call to strings.ToLower is causing all the allocations.

## 11.6 Removing Allocations

Knowing this, I need to find a way to remove the call to strings.ToLower.

# Listing 11.20

```
118  for i, item := range d.Channel.Items {
119     if strings.Contains(strings.ToLower(item.Description), term)) {
120         results = append(results, Result{
121             Engine: engine,
122             Title: item.Title,
123             Link: item.Link,
124             Content: item.Description,
125         }))
126     }
127 }
```

On closer inspection there are two things I can do.

# Listing 11.21

```
122  term = strings.ToLower(term)  <- ADDED
123  for item := range d.Channel.Items {
124    if strings.Contains(item.Description, term) {  <- CHANGED
125        results = append(results, Result{
126            Engine: engine,
127            Title: item.Title,
128            Link: item.Link,
129            Content: item.Description,
130        })
131  }
132 )
```

First, I move the call to the term outside of the loop. Having that call in the loop was really bad since it was performing the same operation over and over producing a lot of little values on the heap. Second, I removed the call to make the description lower That still needs to take place, so I moved it up with the code that caches the feeds.

# Listing 11.22

```
93  resp, err := http.Get(uri)
94  if err != nil {
95    return Result{}, err
96  }
97  defer resp.Body.Close()
98
99  if err := xml.NewDecoder(resp.Body).Decode(&d); err != nil {
100   return Result{}, err
101
102  for i := range d.Channel.Items {  <- ADDED
103    lower := strings.ToLower(d.Channel.Items[i].Description)
104    d.Channel.Items[i].Description = lower
105  }
106
107  cache.Set(uri, d, expiration)
```

The new code converts description to lowercase before storing the feed in the cache. This eliminates the need to do this inside the loop. Granted I should create a new field for the lowercase version of the description.

With these changes in place, I can build and run the program again. Then apply the same exact load and get the new results.

# Listing 11.23

```
Summary:
Total: 1.4367 secs
Slowest: 0.1706 secs
Fastest: 0.0005 secs
Average: 0.0131 secs
Requests/sec: 6960.6340

```
gc 484 87.9984s 4%: 0.038+0.76+0.025 ms clock, 0.62+52.5/1.5/1.8+0.40 ms cpu,
6->7-4 MB, 7 MB goal, 16 P
gc 485 87.991s 4%: 0.056+0.83+0.094 ms clock, 0.91+48.2/2.3/1.9+1.5 ms cpu,
7->8-4 MB, 9 MB goal, 16 P
gc 486 87.994s 4%: 0.089+0.65+0.023 ms clock, 1.4+55/1.8/1.2+0.38 ms cpu,
7->8-4 MB, 8 MB goal, 16 P
gc 487 87.996s 4%: 0.04+0.47+0.012 ms clock, 0.65+22.1/2.5/2.0+0.20 ms cpu,
7->8-4 MB, 8 MB goal, 16 P
```

With the code changes there are definite improvements. Now it seems that only 483 GC's needed to take place to complete the work. I'm subtracting the first 4 GC's again that took place before I ran the load. The program was able to process 6960 requests a second, with the slowest request taking 170ms. That's an improvement of 88% on the requests per second.

If I wanted to focus more on a specific function that the top command might present, I can go back to chapter 10 and use benchmarks.
