![](bbox=[0.148, 0.073, 0.871, 0.423])

Figure 15.5: Summary of elements in a gRPC deployment.

This transformation is obtained adding the google.api.http notations to the .proto file. Observe in the figure that the output from proto includes two files like in a regular gRPC scenario, user_grpc.pb.go has been replaced by user.pb.gw.go. This file contains the definition of the necessary transcoding operations. Using transcoding is a powerful option to enable accessing remote methods to a vast number clients with minimal coding.

# 15.6.1 Generation of stubs and gRPC-gateway

Transcoding is defined in the .proto file using annotations. Example 15.14, defines a user service that creates and generates. There are two important elements we have added here. First, we have imported the annotations.proto file that defines the google.api.http option.

Example 15.14: gRPC services definition with transcoding notations.

```
syntax = "proto3";
package user;

option go_package="github.com/juanuel-tirado/savetheorldwithgo/13_grpc/transcoding/example_01/user";
import "google/api/annotations.proto";

message User {
  string user_id = 1;
  string email = 2;
}
```