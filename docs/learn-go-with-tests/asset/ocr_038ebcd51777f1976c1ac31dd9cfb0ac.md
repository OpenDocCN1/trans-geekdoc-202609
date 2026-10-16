```
"reflect"
"testing"
)

func mockWebsiteChecker(url string) bool {
    if url == "waat://furhurterwe.geds" {
        return false
    }
    return true
}

func TestCheckWebsites(t *testing.T) {
    websites := []string{
        "http://google.com",
        "http://blog.gypsydave5.com",
        "waat://furhurterwe.geds",
    }

    want := map[string]bool{
        "http://google.com":      true,
        "http://blog.gypsydave5.com": true,
        "waat://furhurterwe.geds":  false,
    }

    got := CheckWebsites(mockWebsiteChecker, websites)

    if !reflect.DeepEqual(want, got) {
        t.Fatalf("Wanted %v, got %v", want, got)
    }
}
```

The function is in production and being used to check hundreds of websites. But your colleague has started to get complaints that it's slow, so they've asked you to help speed it up.

# Write a test

Let's use a benchmark to test the speed of `CheckWebsites` so that we can see the effect of our changes.