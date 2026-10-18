# Chapter 6

# Writing unit-tests in Golang

In a previous chapter we explored how to interact with a HTTP endpoint. We downloaded a response over the Internet, and then parsed the JSON response into a struct.

But how would we go about testing code that we write in Go? What can Go’s own test runner offer us? And what kind of opinions does it prescribe?

# Testing opinions

Just like Go has strong opinions and conventions for formatting, naming and package layout, it has the same for unit-testing.

Go actually has its own built-in testing command called `go test` and a package testing which combine to give a minimal but complete testing experience. The standard tool-chain also includes benchmarking `go test -bench` and statement-based code coverage `go test -cover` similar to [NCover](https://www.ndepend.com/) (.NET) or [Istanbul](https://istanbul.js.org/) (Node.js).

If you are coming to Go from a language like Ruby, Java or .NET, then you may be surprised to find that there is no assertions library, and certain books go as far as to discourage any use of them.

To a JavaScript developer, writing in a BDD style, testing a Sum method would look something like this:

```
```javascript
var expect = require('expect');

describe('Calculator', function() {
  describe('#multiply()', function() {
    it('should return -10 when 10 is multiplied by -1', function() {
      const calc = new Calculator()
      expect(calc.multiply(10, -1)).to.eql(-10)
    });
  });
});
```
```

An alternative to the above may be to use an `assert.AreEqual()` type of method from the Java / C# world. The Go developers do not take this approach, and if you want to see some examples of unit testing in Go, check out this test from the OpenFaaS CLI which parses a YAML file: [stack_test.go](#).

In Go, the same test would look more like this:

```
```go
func TestMultiply_ForANegativeNumber(t *testing.T) {
    c := Calculator{}
    want := -10
    got := c.Multiply(10, -1)

    if want != got {
```
```