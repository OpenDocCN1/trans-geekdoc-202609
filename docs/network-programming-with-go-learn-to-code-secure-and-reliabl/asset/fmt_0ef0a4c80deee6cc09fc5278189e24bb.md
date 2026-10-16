
second one. Looks good. Notice also that the `housework.db` file contains readable JSON (to see this on Windows, use the type command instead of cat).

Let’s modify this application to use a binary encoding format native to Go.

***Gob***

`Gob`, as in “gobs of binary data,” is a binary serialization format native to Go.

Engineers on the Go team developed Gob to combine the efficiency of protocol buffers, arguably the most popular binary serialization format, with JSON’s ease of use. For example, protocol buffers don’t let us simply instantiate a new encoder and throw data structures at it, as you did in the JSON example in Listing 12-11. On the other hand, Gob functions much the same way as the JSON encoder, in that Gob can intelligently infer an object’s structure and serialize it.

If you’re interested in exploring the motivation and finer points of Gob, give Rob Pike’s “Gobs of Data” blog post a read (`https://blog.golang.org/gob`). In the meantime, let’s implement our storage backend in Gob (see Listing 12-13).

```go
package gob

import (
    "encoding/gob"
    "io"
)

func Load(r io.Reader) ([]*housework.Chore, error) {
    var chores []*housework.Chore
    return chores, gob.NewDecoder(r).Decode(&chores)
}

func Flush(w io.Writer, chores []*housework.Chore) error {
    return gob.NewEncoder(w).Encode(chores)
}
```

*Listing 12-13: Gob storage implementation (gob/housework.go)*

If you’re looking at this code and observing that it replaces all occurrences of json from Listing 12-11 with gob, you’re not wrong. In Go, Gob is as easy to use as JSON, since it infers what it needs to encode from the object itself. You’ll see how this differs from protocol buffers in the next section.

All that’s left to do is swap out the JSON storage implementation for the Gob one by modifying the imports from Listing 12-2 (Listing 12-14).

```go
// storage "github.com/awoodbeck/gnp/ch12/json"
storage "github.com/awoodbeck/gnp/ch12/gob"
// storage "github.com/awoodbeck/gnp/ch12/protobuf"
```

*Listing 12-14: Swapping the JSON storage package for the Gob storage package (cmd/housework.go)*

Comment out the JSON storage package import 1 in Listing 12-2 and uncomment the Gob storage package one 2.

Since your current `housework.db` file contains JSON, it isn’t compatible with Gob. Therefore, the housework application will throw an error when attempting to decode it using Gob. Remove the `housework.db` file and retest the application (see Listing 12-15).

```bash
$ **rm housework.db**
$ **go run cmd/housework.go**
```

You're all caught up!

```bash
$ **go run cmd/housework.go add Mop floors, Clean dishes, Mow the lawn**
# \[X\] Description
1 \[ \] Mop floors
2 \[ \] Clean dishes
3 \[ \] Mow the lawn
$ **go run cmd/housework.go complete 2**
# \[X\] Description
1 \[ \] Mop floors
2 \[X\] Clean dishes
3 \[ \] Mow the lawn
$ **hexdump -c housework.db**
0000000 \\r 377 203 002 001 002 377 204 \\0 001 377 202 \\0 \\0 ) 377
Data Serialization **279**
0000010 201 003 001 002 377 202 \\0 001 002 001 \\b C o m p l 0000020 e t e 001 002 \\0 001 \\v D e s c r i p t
0000030 i o n 001 \\f \\0 \\0 \\0 1 377 204 \\0 003 002 \\n M
0000040 o p f l o o r s \\0 001 001 001 \\f C l
0000050 e a n d i s h e s \\0 002 \\f M o w
0000060 t h e l a w n \\0
000006a
```

*Listing 12-15: Testing the housework application with Gob storage on the command line* Everything still works as expected. Using the hexdump tool, you can see that the `housework.db` file now includes binary data. It’s certainly not human-readable as JSON was in Listing 12-12, but Go happily deserializes the Gob-encoded data, even though it’s harder for us to make sense of it.

(My Windows friends can find a hexdump binary at `https://www.di-mgt.com.au/hexdump-for-windows.html`, though you’ll have to use the -C flag to get the same effect.)

If you are communicating with other Go services that support Gob, I recommend you use Gob over JSON. Go’s encoding/gob is more performant than encoding/json. Gob encoding is also more succinct, in that Gob uses less data to represent objects than JSON does. This can make a difference when storing or transmitting serialized data.

Now that you have a taste for serializing data using encoding/json and encoding/gob, let’s add protocol buffer support to your storage backend.

***Protocol Buffers***

Like Gob, `protocol buffers` use binary encoding to store or exchange information across various platforms. It’s faster and more succinct than Go’s JSON encoding. Unlike Gob and like JSON, protocol buffers are language neutral and enjoy wide support among popular programming languages. This makes them ideally suited for using in Go-based services that you hope to integrate with services written in other programming languages. This chapter assumes you’re using the *proto3* version of the format.

Protocol buffers use a definition file, conventionally suffixed with *.proto*, to define messages. *Messages* describe the structured data you want to serialize for storage or transmission. For example, a protocol buffer message representing the Chore type looks like the definition in Listing 12-16.

```proto
message Chore {
    bool complete = 1;
    string description = 2;
}
```

*Listing 12-16: Protocol buffer message definition representing a Chore type*

You define a new message by using the message keyword, followed by the unique name of the message. Convention dictates you use Pascal case. ( *Pascal casing* is a style of code formatting in which you concatenate capitalized words: *ThisIsPascalCasing*.) You then add fields to the Chore message. Each field definition includes a type, a snake-cased name, and a field number unique to the message. ( *Snake casing* is like 