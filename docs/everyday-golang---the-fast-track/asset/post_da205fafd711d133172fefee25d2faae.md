
![](img/0b5c3b498f62579835cf1d543b46de92_0_0.png)
![](img/0b5c3b498f62579835cf1d543b46de92_0_1.png)

YOUR FAST TRACK FOR GOLANG

## EVERYDAY GO

BY ALEX ELLIS

Learn tools, techniques and patterns from real tools used in production.

## Everyday Golang - The Fast Track

Alex Ellis

2024

- Compile the tests to a binary  .................................... 46
- Isolating dependencies  .................................... 47
- Example of isolating dependencies  .................................... 49
- Unit-testing a HTTP server  .................................... 51

## 7 Work concurrently with Goroutines 55

- A simple example with Goroutines  .................................... 55
- Avoid a common mistake with Goroutines  .................................... 57
- Error groups  .................................... 59
- Limiting requests to expensive resources  .................................... 60
- Sharing data between Goroutines  .................................... 64
- Using channels for synchronisation  .................................... 67
- Using a context to handle timeouts  .................................... 69
- Limiting concurrent work  .................................... 71

## 8 Store data with a database 76

## 9 Write your own config files in YAML 81

- A practical example of YAML in action  .................................... 81
- Read and write your own YAML schema  .................................... 81
- Merging objects  .................................... 83

## 10 Inject version information into your binaries 86

- Capture useful variable(s)  .................................... 86
- Prepare your code  .................................... 87
- Do it with Docker  .................................... 89
- Examples in production  .................................... 89

## 11 Embed data in your application 91

## 12 Create dynamic content with templates 93

- Advanced templates: ranges and custom functions  .................................... 94
- Real-world templates - arkade  .................................... 96

## 13 Write a HTTP server 99

- Reading the request  .................................... 100
- Advanced route handling  .................................... 101
- Writing HTTP middleware  .................................... 103

## 14 Add Prometheus metrics to your microservices 105

- Tracking HTTP metrics for our microservice  .................................... 110
- Adding custom metrics to your Prometheus data  .................................... 113
- The Prometheus Collector interface  .................................... 115

## 15 Building and releasing Go binaries 119

- The release-it example  .................................... 119
- Releasing your binaries with a GitHub Action  .................................... 120

## 16 Releasing a Docker container image 122

- Going multi-arch  .................................... 123
- Shipping a Docker container from GitHub Actions  .................................... 124

## 17 Your onward journey 126

- Giving feedback  .................................... 126
- Contributing to Open Source  .................................... 126
- My other content  .................................... 126

## 18 OpenFaaS and Go 127

- Topics covered  .................................... 127
- Serverless use-cases  .......................................................... 127
- Introduction to OpenFaaS  ....................................................... 128
  - The value vs cloud functions  .................................................. 128
  - Pros and Cons  ................................................................ 129
- Where can you run OpenFaaS functions?  .......................................... 129
- The Go template for OpenFaaS  .................................................... 129
- Your first function  .............................................................. 131
  - Building your function  ........................................................ 133
  - Adding unit tests to your function  ............................................ 134
  - Iterating locally  .............................................................. 135
  - Split code into multiple files  ................................................. 136
  - Introduce a sub-package  ......................................................... 138
- Working with secrets and databases  ............................................... 139
  - Create the todo-fn example  ...................................................... 139
  - Exploring the request  ........................................................... 142
  - The complete example  ............................................................ 148
  - Managing config between multiple environments  ................................. 153
  - Further tasks  .................................................................... 153
  - Custom domains and routes  ....................................................... 154
- Where to go next  .................................................................. 156

![](img/0b5c3b498f62579835cf1d543b46de92_7_0.png)

Figure 1.1: Go's new logo

- Go branding guidelines

Here are some projects that come to mind, which are written entirely (or have major portions) in Go:

- Docker - a container engine written by Docker Inc
- Kubernetes - a clustering system for containers built by Google and open source contributors
- Traefik - a load-balancer built by Traefik Labs
- Istio - a service mesh to encrypt traffic between Kubernetes Pods
- Consul, Terraform - tools for managing infrastructure built by Hashicorp
- Caddy - a high performance HTTP server written by Matt Holt
- OpenFaaS - serverless framework for hosting your own functions, built by myself and various other contributors

These are just a few of hundreds of thousands of projects which have appeared on GitHub's trending page for Go.

As you can see from the above, Go is very popular for server-side projects, but it is also very popular for writing Command Line Interfaces (CLIs) because the binaries can be statically linked. Statically-linked Go binaries are both fast and small, and do not require an additional runtime making them a very popular choice.

My personal highlights for Go are:

- portability - static compilation for easy distribution
- cross-compilation - being able to build binaries for Linux, Windows, macOS Operating Systems (OS) and Arm computers with a single command (go build)
- concurrency model - Go has built-in mechanisms for concurrency that make it well suited to tasks both small and large
- ecosystem - knowing Go means being able to contribute to almost any other open source Go project or product
- tooling - Go includes its own unit-testing runner and profiler, both of which are simple and easy to use
- opinions - Go has strong opinions on formatting, style and typing that make it easy to move between codebases

Above everything else, Go has an impressive set of packages available within its standard libraries or “stdlib”. There are many useful packages and utilities that would need to be installed separately in a programming language like JavaScript, Ruby or Java.

- crypto - libraries for X.509 certificates and cryptography
- compress - work with zip files and archives
- http - a very powerful and simple HTTP client and server package including things like reverse proxies
- net - work directly with sockets, URLs and DNS
- encoding/json - work directly with JSON files
- text/template - a powerful templating engine for replacing tokens in files, and generating text and HTML
- os - work with low level OS primitives

You can find a complete package list here.

Through the next few chapters we will explore some of the above highlights and also solve various practical problems. Even if you're a seasoned Go developer, I'd recommend going through each of the exercises, because even after 11 years, I myself am still learning new approaches and styles.

Go itself is a very stable language, which seldom sees deprecations or breaking changes, for that reason the latest version of Go has little bearing on the version mentioned in this material. The content is updated periodically in line with major changes.

## Getting started with Go

There are three ways to install Go.

- Install Go using a system package - such as an msi (Windows) or pkg (macOS)
- Install Go using a package manager - such as apt-get (Debian), pacman (Arch Linux), brew (macOS)
- Download a tar archive and unpack it to a set location (Linux only)

If you're a new user and running on Windows or macOS, then go ahead with the first option and download Go from the homepage. The version changes frequently, so download the latest stable version.

If you like to use package managers, you should be aware that the version they offer often lags behind. You may be installing a very old version of Go, and some features may not be available.

### A note for Windows users

Whilst the Go commands can be run in cmd.exe and PowerShell, some of the example commands expect a UNIX-style shell which is present on macOS and Linux hosts.

For ease of use, it's recommended that you try the content using Windows Subsystem for Linux (WSL), if it is available for your system. Or if not, make use of Git Bash.

Git Bash provides a terminal where you can run bash, have access to the git command and various other UNIX-style commands such as export, ls, mkdir and curl.

### Direct installation on Linux

As a Linux user, I often need to install Go on a server, within a Docker image, or on my Raspberry Pi. My arkade project provides a quick and efficient way to download the latest version without having to construct a curl statement or run tar.

Download and install arkade from: https://github.com/alexellis/arkade

Then run:

```
sudo arkade system install go

Installing Go to /usr/local/
Installing version: go1.23.4 for: amd64
Downloading from: https://go.dev/dl/go1.23.4.linux-amd64.tar.gz
142.05 MiB / 142.05 MiB [--------------------------------------------------] 100.00%
Downloaded to: /tmp/go1.23.4.linux-amd64.tar.gz
Unpacking Go to: /usr/local/go

export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin
export GOPATH=$HOME/go/
```
