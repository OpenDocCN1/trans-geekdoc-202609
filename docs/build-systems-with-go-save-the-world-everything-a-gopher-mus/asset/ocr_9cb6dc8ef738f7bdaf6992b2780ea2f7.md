In order to replicate the logic from Example 14.3 now we have to import user group after running protoc. Check how this is done in Example 14.6 and compare it with the previous version using only one package.

# Example 14.7: Utilization of protos from Examples 14.5 and 14.6.

```
1 package main
2
3 import (
4	"github.com/juanmanuel-tirado/savetheworldldithgo/12_protocolbuffers/pb/example_03/group"
5	"github.com/juanmanuel-tirado/savetheworldldithgo/12_protocolbuffers/pb/example_03/user"
6	"google.golang.org/protobuf/proto"
7	"fmt"
8
)
9
10 func main() {
11	userA := user.User(UserId:"John", Email:"john@gmail.com")
12	userB := user.User(UserId:"Mary", Email:"mary@gmail.com")
13
14	g := group.Group(Id: 1,
15		Score: 42.0,
16		Category: group.Category_DEVELOPER,
17		Users: []user.User{userA,userB},
18	)
19	fmt.Printf("To encode: %s\n", g.String())
20
21	encoded, err := proto.Marshal(&g)
22	if err != nil {
23		panic(err)
24	}
25	recovered := group.Group{}
26	ererr = proto.Unmarshal(encoded, &recovered)
27
28	fmt.Printf("Recovered: %s\n", recovered.String())
29\}
```

# 14.4 NESTED TYPES

Certain messages may only make sense when found within other messages. PB permits the definition of nested types that are only accessible through other types. Our Group message can be rewritten using the User message as an embedded field shown in Example 14.8. Now the User type is defined in the context of Group. The winner message represents a user who won in a given category. Otherwise, that user field has to be referred to as Group.User.

**Example 14.8:** Group definition with nested User type.

```
1 syntax = "proto3"
2 package group;
3
4 option go_package="github.com/juanmanuel-tirado/savetheworldldithgo/12_protocolbuffers/pb/example_04/group";n5
```