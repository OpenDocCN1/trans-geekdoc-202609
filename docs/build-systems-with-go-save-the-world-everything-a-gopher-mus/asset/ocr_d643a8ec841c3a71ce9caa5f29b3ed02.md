# CHAPTER 12
MODULES AND DOCUMENTATION

Nowadays is very difficult to find programming projects to be designed as isolated pieces of code. Projects use code developed by other developers. Other projects are designed to be incorporated into other projects. These dependencies between projects require tools to facilitate the definition of external code a project. And even more important, a systematic way to document our code so it can be shared with others. This Chapter explains how Go incorporates code into your projects using modules and how we can connect our programs.

# 12.1 MODULES

Dealing with dependencies is always key to ensure code compatibility and reproducibility. As it was explained in Chapter 2.1.1 we showed throughout this book, the most basic tool to make code accessible is go get. However, this is a very basic solution that does not solve issues such as code versioning. Nowadays projects require several third-party projects to run. For some years solutions were proposed to manage code dependencies in Go, until Go modules became the official solution.

> Go 1.16 was released while this was being written in version v0.1.0. One of the most important changes in this release is the use of go modules by default. For compatibility purposes, and to facilitate migrations the environment variable GO11MODULE can be set to false. However, this variable will be ignored in Go 1.17. This means, that every project will be expected to use Go modules.

Go modules facilitates the management of dependencies and makes it easier to share project requirements among developers. The idea is simple, to show the requirements of a project in a common format that can be used to acquire all the necessary code for a successful completion. Go modules are governed by the go.mod file that contains information about what projects in versions are required. We assume with the code from Example 12.1. This code uses a third-party logger to print a message. In the most basic approach, we would download the code using go get. However, with modules, we can simplify this process.

Example 12.1: Program using modules.

```
package main

import "github.com/rs/zerolog/log"

sfunc main() {
	log.Info().Msg("Save the world with Go!!!")
}
```

In the folder containing our code run go mod init. This creates a go.mod file which looks