
There are other "nil safe" types in Go. For example you can ask the length of a nil slice, receive a value from an empty channel (though you'll be blocked forever) and more.

### 2.1. Further Reading

- Go maps in action on the Go blog
- Maps section of "Effective Go"

## 3. WHEN IN KRAKÓW

Listing 4. city.go

```
package main

import (
	"fmt"
)

func main() {
	city := "Kraków"
	fmt.Println(len(city))
}
```

Try to guess what the output is before moving to the next page.

If you count the number of characters in Kraków, it’ll come out to 6. So why 7? The reason is... history.

In the beginning, computers were developed in English speaking countries - the UK and the US. When early developers wanted to encode text in computers that only understand bits, they came out with the following scheme. Use a byte (8 bits) [3] to represent a character. For example a is 97 (01100001), b is 98, etc. One byte is enough for the English alphabet that contains 26 lower case letters, 26 upper case letters, and 10 digits. There even some space left for other special characters (e.g. 9 for tab). This is known as ASCII encoding.

After a while, other countries started to use computers and they wanted to write using their native language. ASCII wasn’t good enough, a single byte isn’t big enough to hold all the numbers we need to represent letters in different languages. This lead to several different encoding schemes, the most common one is UTF-8. Rob Pike, one of the designers of Go, is also one of the designers of UTF-8.

Go strings are UTF-8 encoded, this means that a character (called rune) can be from one to four bytes long. When you ask the length of a string in Go, you’ll get the size in bytes. In this example the rune ó is taking 2 bytes, hence the total length of the string is 7.

If you want to know the number of runes in a string, you'll need to use the unicode/utf8 package.

Listing 5. cityu.go

```
package main

import (
	"fmt"
	"unicode/utf8"
)

func main() {
	city := "Kraków"
	fmt.Println(utf8.RuneCountInString(city))
}
```

### 3.1. Further Reading

- Strings, bytes, runes and characters in Go from the Go blog
- Unicode and You
- Unicode entry in Wikipedia

3 To be precise, ASCII uses only 7 bits, and LATIN-1 extends it to 8 bits.

## 4. I'VE GOT NOTHING

Listing 6. city.go

```
package main

import (
	"fmt"
)

func main() {
	n := nil
	fmt.Println(n)
}
```

Try to guess what the output is before moving to the next page.

This code will not compile.

nil is not a type but a reserved word. A variable initialized to nil must have a type. If, for example, you’ll change the assignment to var n *int = nil, the code will compile since now n has a type.

Here are some places where nil is used:

- The zero value for map, slice and chan is nil.
- You can't compare slices or maps using ==, you can only compare them to nil [4].
- Sending to or receiving from a nil channel will block forever. You can use this to avoid a busy wait.

### 4.1. Further Reading

- Understanding nil from Practical Go by Dave Cheney
- Why are there nil channels in Go? from justforfunc
- Channel Axioms by Dave Cheney

4 You can use reflect.DeepEqual to compare maps and slices.

## 5. A RAW DIET

Listing 7. raw.go

```
package main

import (
	"fmt"
)

func main() {
	s := `\a\tb`
	fmt.Println(s)
}
```

Try to guess what the output is before moving to the next page.

This code will print: a\tb

The Go spec says:

There are two forms: raw string literals and interpreted string literals.

Raw strings are enclosed in backticks (e.g. `hello`), interpreted strings are enclosed in quotes (e.g. "hello"). In raw strings, \ has no special meaning, so the `\t` is two characters - backslash and the letter t. If it was an interpreted string, then \t would be interpreted as the tab character.

Apart from the usual \t (tab), \n (newline) and friends, you can also use Unicode code points in interpreted strings. fmt.Println("\u2122") will print ™.

One of the most common uses for raw strings is to create multi-line strings.

```
// An HTTP request
request := `GET / HTTP/1.1
Host: www.353solutions.com
Connection: Close
`
```

### 5.1. Further Reading

- Strings, bytes, runes and characters in Go from the Go blog
- The string spec
- ASCII control characters on Wikipedia

## 6. ARE WE THERE YET?

Listing 8. time.go

```
package main

import (
	"fmt"
	"time"
)

func main() {
	timeout := 3
	fmt.Printf("before ")
	time.Sleep(timeout * time.Millisecond)
	fmt.Println("after")
}
```

Try to guess what the output is before moving to the next page.

This code will not compile.

When you write `timeout := 3` the Go compiler will do a type inference. 
In this case it will infer that `timeout` is an `int`. Then in line 11 you multiply `timeout` (int type) with `time.Millisecond` (`time.Duration` type) - which is not allowed.

You have several options to fix this.

Change the type of `timeout` to `time.Duration` (line 9):

```
var timeout time.Duration = 3
```

Make `timeout` a const, and then its type will be resolved in the context of usage (line 9):

```
const timeout = 3
```

Use a type conversion to convert `timeout` to `time.Duration` (line 11):

```
time.Sleep(time.Duration(timeout) * time.Millisecond)
```

### 6.1. Further Reading

- Type inference in the Go tour
- go/types: The Go Type Checker in golang/example
- time.Duration type
- Type conversions in the Go specification

## 7. CAN NUMBERS LIE?

Listing 9. float.go

```
package main
import (
"fmt"
)
func main() {
n := 1.1
fmt.Println(n * n)
}
```

Try to guess what the output is before moving to the next page.

This code will print: 1.2100000000000002

You might have expected 1.21 which is the right mathematical answer.

Some new developers, when seeing this or similar output, comes to the message boards and say "We found a bug in Go!". The usual answer is RTFM.[5].

> Floating point is sort of like quantum physics: the closer you look, the messier it gets.
> ~ Grant Edwards

The basic idea behind this issue, is that in floating points we sacrifice accuracy for speed (i.e. cheat). Don’t be shocked, it’s a trade-off we do a lot in computer science.

The result you see conforms with the floating point specification. If you’ll run the same code in Python, Java, C ... you will see the same output.

See the links below if you’re interested in understanding more about how floating points work. The main point you need to remember is that they are not accurate, and accuracy worsens as the number gets bigger.

One implication is that when testing with floating points, you need to check for "roughly equal" and decide what is an acceptable threshold. Testing libraries such as testify have ready-made functions (such as InDelta) to check that two floating numbers are approximately equal.

Floating points have several other oddities. For example there's a special NaN value (short for "not a number"). NaN does not equal any number, including itself. The following code will print false.

```
fmt.Println(math.NaN() == math.NaN())
```

To check that you got NaN, you need to use a special function such as math.IsNaN.

If you need better accuracy, look into math/big or external packages such as shopspring/decimal.

### 7.1. Further Reading

- floating point zine by Julia Evans
- What Every Computer Scientist Should Know About Floating-Point Arithmetic

5 Read the fine manual.

## 8. SLEEP SORT

Listing 10. sleep_sort.go

```
package main

import (
	"fmt"
	"sync"
	"time"
)

func main() {
	var wg sync.WaitGroup
	for _, n := range []int{3, 1, 2} {
		wg.Add(1)
		go func() {
			defer wg.Done()
			time.Sleep(time.Duration(n) * time.Millisecond)
			fmt.Printf("%d ", n)
		}()
	}
	wg.Wait()
	fmt.Println()
}
```

> Try to guess what the output is before moving to the next page.
