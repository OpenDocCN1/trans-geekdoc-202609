```
userA := user.User(UserId: "John", Email: john@gmail.com", Info: []*anypb.Any{&info})
fmt.Println("To encode: %s", userA.String())
encoded, err := proto.Marshal(&userA)
if err != nil {
    panic(err)
}
recovered := user.User()
err = proto.Unmarshal(encoded, &recovered)
fmt.Println("Recovered: %s", recovered.String())
```

To encode: user_id:"John" email:john@gmail.com" info:(type_url:"urltype" value:"John rules")nRecovered: user_id:"John" email:john@gmail.com" info:(type_url:"urltype" value:"John rules")

# # 14.6 ONEOF

If a message with fields can have only one field when sent, there is no point in sending all the fields. The type oneof forces messages to include only one field from a collection.

Example 14.12 allows the User message with a field indicating which type of user we have. A user can only be a developer or an operator. Additionally, developers have information about the language they use, while operators have information about the platform they administrate.

> 14.12: Utilization of type Oneof.

```
syntax = "proto3"
package user;

option go_package="github.com/juanmanuel-tirado/savetheorldwithgo/12_protocolbuffers/pb/example_06/user";n
message Developer {
    string language = 1;
}

message Operator {
    string platform = 1;
}

message User {
    string user_id = 1;
    string email = 2;
    oneof typeof {
        Developer developer = 3;
        Operator operator = 4;
    }
}
```

When using oneof, PB defines nested types in the User message. In our case, types User_Developer