
# 3. Getting Started

A PC with Windows/Linux or a MAC machine will be required to build Go applications. Go programs are plain text files (carrying the extension `.go`) and hence you will need a text editor to write Go programs. Any text editor will do the job including `Notepad`, `Wordpad`, `vi`, `emacs`, `Notepad++`, etc. Choose an editor that you are the most comfortable with. You can alternatively use IDEs such as `Eclipse`, `IntelliJ`, etc. I prefer keeping it simple for learning basics, sticking to a simple text editor instead of an IDE. You will need to install Go compiler toolchain on your machine in order to build Go applications.

## 3.1 Install Go on Windows

Visit [https://golang.org/dl/](https://golang.org/dl/) and download the latest installer file for Windows having the extension `.msi`. Once you have the file, execute it by double-clicking on it. You will need administrative rights to proceed. You will see a welcome screen as follows:

![](Image00002.jpg)

Click **Next** and you will be presented with the EULA.

![](Image00003.jpg)

Read the agreement, accept the terms and click **Next**.

![](Image00004.jpg)

Here, you will be given an option to change the installation directory. It is best to leave it as it is and click **Next**.

![](Image00005.jpg)

Click **Install** and the installation process will begin.

![](Image00006.jpg)

This may take a few minutes to complete. Once done, you will see something like this:

![](Image00007.jpg)

Click **Finish**. Verify the Go installation by going to the `bin` folder inside the Go installation directory (usually `C:\Go\` if you did not change it during installation) and make sure that an executable file called `go.exe` is present:

![](Image00008.jpg)

You can alternatively navigate to the Go installation directory using the command prompt with the help of `cd` command and list the contents of the directory using the `dir` command:

![](Image00009.jpg)

The Go installer automatically adds path of this `bin` directory to the `PATH` environment variable. This makes `go.exe` accessible from anywhere. To check, open Command Prompt or PowerShell and type the following command:

```
go
# OR
go.exe
```

If you see something like the following screenshot, it means that Go installation is successful and `PATH` variable is correctly set:

![](Image00010.jpg)

If you see something like this – `go` is not recognized as an internal or external command, operable program or batch file. It either means there is a problem with the installation or the `PATH` variable has not been set correctly. In such a case, check the `PATH` variable using the `echo %PATH%` command, if Go’s `bin` directory has not been added to it, add it manually through System Properties (`Windows Key + Pause Break`). If the `PATH` variable is correctly set and `go` command can still not be found, then go through the installation process once again.

## 3.2 Install Go on Unix-like Operating Systems

If you use a Unix-like operating system such as Linux, macOS, FreeBSD, DragonFly BSD, etc., download the appropriate installation file for your OS from [https://golang.org/dl/](https://golang.org/dl/). Installation process will vary from OS to OS. It is best to follow official Go documentation available at this link [https://golang.org/doc/install](https://golang.org/doc/install) in order to learn how to install Go on a particular OS.

> **Note:** Programs demonstrated in this book have been written, built and executed on a Windows machine. They should compile off the shelf on Unix-like operating systems unless specified otherwise.

## 3.3 Compile and Execute Go Programs

As mentioned earlier, Go programs are plaintext files carrying the extension `.go`. Go is a compiled language. That is, a special software called compiler converts a plaintext Go program into an executable file. Here is a conceptual block diagram of the compilation process:

![](Image00011.jpg)

In simple terms, a Go program is given to a Go compiler which then converts the plaintext file to an executable binary file. Of course, there is more to this; there are many technical concepts involved in the compilation process but it is transparent to the user and hence there is no need to learn about it unless you are into low-level system software design or compiler design domains. Let us now take a look at how to compile and execute Go programs.

### 3.3.1 On Windows

Open Command Prompt/PowerShell on Windows, navigate to the directory which has the program you want to compile and execute and enter the following command:

```
go build <program file>
```

**Example:** `go build test.go`

When you enter `go build <program file>`, the `go` command refers to the `go.exe` file which is the Go compiler. The program to be compiled is passed as a command line argument to this utility marked by `<program file>` in the above command. If the compilation process is completed successfully, an executable file will be generated having the same name as that of the program file but with `.exe` extension. For example, `go build test.go` command will generate `test.exe` file if compilation succeeds. If you want a custom output file name, you can use the `-o` flag as follows:

```
go build -o <output file> <program file>
```

**Example:** `go build -o xyz test.go`

Once you have the output file, it can be executed as follows inside Command Prompt/PowerShell:

```
<executable file name>
```

**Example:** `test.exe`

### 3.3.2 On Unix-like operating systems

Open Bash/Shell/Terminal on Linux, macOS or any other Unix-like OS, navigate to the directory where the program to be compiled is present and enter the following command:

```
go build <program file>
```

**Example:** `go build test.go`

When you say `go build <program file>`, the `go` command refers to the Go compiler’s executable file `go` usually present at `/usr/local/go/bin` directory. The program to be compiled is passed as a command line argument to this utility marked by `<program file>` in the above command. If the compilation process is completed successfully, an executable file with the same name as that of the program will be generated. This file will automatically acquire the execute permission. For example, `go build test.go` command will generate `test` file if compilation succeeds. If you want a custom output file name, you can use the `-o` flag as follows:

```
go build -o <output file> <program file>
```

**Example:** `go build -o test prog.go`

The output file can be executed as follows within the terminal:

```
./<executable file name>
```

**Example:** `./test`

### 3.3.3 Compile and Execute Demo

Let us get hands on experience to gain proper understanding of how to compile a Go program and then execute it. The process will be demonstrated on Windows. If you use a Unix-like OS, follow [Section 3.3.2](#332-on-unix-like-operating-systems). On Windows, open your favourite text editor and copy-paste the following code:

```
package main

import "fmt"

func main() {
    fmt.Printf("\nIf you see this, you did a great job so far!\n")
}
```

Save this file as `test.go` at a convenient location. This is your Go program to be compiled. A program can also be referred to as code, source, source code, source file or program file. Open Command Prompt or PowerShell, navigate to the directory where `test.go` is present using the `cd` command and enter the following command:

```
go build test.go
```

This command will generate a file called `test.exe`. Execute this file as follows:

```
test.exe
```

Here is the output:

![](Image00012.jpg)

> **Note:** You do not have to understand what the above code does or how it works, the only purpose of this section was to teach you how to compile and execute a Go program.

### 3.3.4 Compilation Errors

Compilation errors occur when there are mistakes in the source file. These are usually syntax related issues. If you try to compile a Go program which has problems, the compiler will throw an error and the compilation process will not complete successfully and hence, the executable file will not be generated. Sometimes, the error message returned by the compiler will tell you exactly what has gone wrong where and sometimes it will not. Hence it is a good idea to check every program manually before compiling. Here is what a sample compilation error looks like:

![](Image00013.jpg)

### 3.3.5 Go Playground

Go Playground is a web based tool used to compile and execute Go programs online. Of course, full functionality of Go will not be available through this tool but nonetheless, it is a very useful tool to try out small programs and learn concepts especially when you do not have access to a PC/Laptop with Go environment. Open your favourite web browser and visit [https://play.golang.org/](https://play.golang.org/). You will see something like this:

![](Image00014.jpg)

Clear the existing code, copy-paste the code from [Section 3.3.3](#333-compile-and-execute-demo) and click **Run**. You should see the output right below the code area:

![](Image00015.jpg)
