appName

+   - cmd
  - RootCommand.go
  - command1.go
  - command2.go
  - command3.go
- main.go

The main.go file is minimal and only executes the root command. Every command file must contain the logic required to execute this command. The logic of the program, library, framework, etc must not be coupled to these commands. Cobra commands must only be used to capture the required information to trigger actions and must not be part of the logic of your program.

As point of clarification, the examples in this Chapter have been condensed into single files that contain all the logic. Notice that these examples are focused on demonstrating CLI concepts, not any additional logic. For demonstration purposes and better clarity, the examples contain all the commands in a single file. However, the concepts shown here can be easily adapted to the Cobra conventions.

# # 17.2 ARGUMENTS AND FLAGS

Commands may require arguments to be executed. These arguments are passed to the Run field of every Command. In Example 17.2, the arguments received by the root command are printed.

> Example 17.2: Command receiving arguments

```
package main

import (
    "fmt"
    "github.com/spf13/cobra"
    "os"
    "strings"
)

var RootCmd = &cobra.Command{
    Use: "main",
    Long: "Long message",
    Run: func(cmd *cobra.Command, args []string) {
```