```
package main

import (
    "fmt"
    "io"
    "log"
)

type FakeReader struct {
    payload []byte
    position int
}

func (f *FakeReader) Read(p []byte) (n int, err error) {
    p = f.payload
    f.position += len(f.payload)
    if f.position > len(f.payload) {
        return 0, io.EOF
    }

    return len(f.payload), nil
}

func (f *FakeReader) SetFakeBytes(p []byte) {
    f.position = 0
    f.payload = p
}

func ReadAllTheBytes(reader io.Reader) []byte {
    data, err := io.ReadAll(reader)
    if err != nil {
        log.Fatal(err)
    }
    return data
}

func main() {
    fakeReader := &FakeReader{}
    want := []byte("when called, return this data")
    fakeReader.SetFakeBytes(want)
    got := ReadAllTheBytes(fakeReader)
    fmt.Printf("%d/%d bytes read.\n", len(got), len(want))
}
```

Before implementing your own abstractions (as above) it is a good idea to search the Golang docs to see if there is already something you can use. In the case above we could also use the standard library in the bytes package:

```
func NewReader(b []byte) *Reader
```

The testing/iotest package provides some Reader implementations which are slow or which cause errors to be thrown half way through reading. These are ideal for testing the resilience of your system. You should be prepared to ask questions like: “What would happen if there was a timeout?”