# CHAPTER 17
COMMAND LINE INTERFACE

A software developer is used to interact with command-line interfaces (CLI). Good systems not only solve problems but are also easy to use. Nowadays solutions may offer hundreds of commands with several parameters each. Defining a good command-line interface that enables users to execute any operation is challenging. Fortunately, the Go ecosystem offers powerful solutions that reduce the effort to define powerful and solid CLIs. This Chapter presents how the Cobra library can help developers to define solid CLIs in an efficient and consistent way.

# 17.1 THE BASICS

Cobra is a library that provides all the necessary items to develop CLIs in Go. This library is used by major projects such as Kubernetes, Github or Istio and has some interesting features such as intelligent suggestions, automatic help generation, documentation, shell autocompletion, it is POSIX compliant.

Before explaining basics make sure you have Cobra available in your environment. The examples from this Chapter require the library to be installed. As usual, you can Go Modules (see Chapter 12) or run the following command to download the code in your GOPATH.

```
go get github.com/spf13/cobra
```

Cobra CLIs are built around the command type which fields define the name of the actions to be executed, their arguments, and help information. Example 17.1 contains a minimal example of a Cobra CLI for a program. This naive program is intended to be executed like ./hello and print a message using the standard output.

# Example 17.1: Basic Cobra CLI

```
package main

import (
    "fmt"
    "github.com/spf13/cobra"
    "os"
)

var RootCmd = &cobra.Command{
    Use: "short message",
    Short: "short message",
    Long: "Long v0.1.0",
    Example: "this is an example",
    Run: func(cmd *cobra.Command, args []string) {
        fmt.Println("Save the world with Go!!!")
    }
```