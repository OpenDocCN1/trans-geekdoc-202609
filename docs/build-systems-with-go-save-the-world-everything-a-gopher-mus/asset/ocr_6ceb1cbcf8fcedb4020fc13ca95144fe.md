```
message UserRequest {
  string user_id = 1;
}

service UserService {
  rpc Get(UserRequest) returns (User) {
    option(google.api.http) = {
      get: "/v1/user/{user_id}"
    }
  }
  rpc Create (User) returns (User) {
    option(google.api.http) = {
      post: "/v1/user"
    }
  }
}
```

For every RPC method we want to expose through HTTP we must define the path and the required HTTP method. The method Get will be served at /v1/user/{user_id}, where `user_id` corresponds to the field with the same name from the corresponding input message. In this case, this will fill the unique field from the UserRequest message to be sent into the body of the HTTP request. By setting body="*", we indicate that a User message will be filled with all the available data from the body. If required, single fields can be specified, for example, body="email" will only expect the body to contain the email field.

> Remember that the URL of a remote procedure should not be changed unilaterally once this function is consumed by others. There are some good practices to be followed indicating the API version in the URL. In other cases, you can define additional bindings for the same procedure.

```
Get (UserRequest) returns (User) {
  option(google.api.http) = {
    get: "/v1/user/{user_id}"
    additional_bindings {
      get: "/v2/user/{user_id}"
    }
  }
}
```

Before running protoc, we must install the grpc-gateway plugin.

```
>> go install \ \
github.com/grpc-ecosystem/grpc-gateway/v2/protoc-gen-grpc-gateway \ \
github.com/grpc-ecosystem/grpc-gateway/v2/protoc-gen-openapi2 \ \
gogle.golang.org/protobuf/cmd/protoc-gen-go \ \
gogle.golang.org/grpc/cmd/protoc-gen-go-grpc
```