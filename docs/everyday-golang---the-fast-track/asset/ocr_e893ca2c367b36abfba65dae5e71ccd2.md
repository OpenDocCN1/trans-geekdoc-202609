```
```bash
export GH_USERNAME="alexlellis"
mkdir -p $GOPATH/src/github.com/$GH_USERNAME/yaml-config/
cd $GOPATH/src/github.com/$GH_USERNAME/yaml-config/
```
```

To load a configuration file, you define a number of structs and annotate them, just like we did with the JSON examples.

```
```go
type Spec struct {

    // Name name of the function
    Name string `yaml:"name"`


    // Image docker image name of the function
    Image string `yaml:"image"`

    Environment map[string]string `yaml:"environment,omitempty"`


    // Limits for the function
    Limits *FunctionResources `yaml:"limits,omitempty"`
}

// FunctionResources Memory and CPU
type FunctionResources struct {
    Memory string `yaml:"memory"`
    CPU    string `yaml:"cpu"`
}
```
```

As you can see from above, where we would have put `json:"field"`, we just write yaml instead and then go on to use a very similar interface to unmarshal the text into an object.

Create main.go:

```
```go
package main

import (
    "fmt"
    "os"

    yaml "gopkg.in/yaml.v2"
)

// Add above structs here

func main() {
    bytesOut, err := os.ReadFile("config.yaml")
    if err != nil {
        panic(err)
    }

    spec := Spec{}
    if err := yaml.Unmarshal(bytesOut, &spec); err != nil {
        panic(err)
    }

    fmt.Printf("Function name: %s\tImage: %s\tEnvs: %d\n", spec.Name, spec.Image,
        len(spec.Environment))
}
```
```