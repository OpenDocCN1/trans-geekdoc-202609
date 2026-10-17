
-   [相比之下，如果你查看像 C# 这样的语言，它允许你将函数作为参数传递，也允许返回函数，你可以得到下面这样的函数。这个函数接受两个参数。第一个是整数。第二个是函数。这使得一定程度的抽象化成为可能，因为你可以有一个名为 `Dbl` 的接口，其实现是由下面若干函数处理的。`Dbl` 接口仅仅是一种合理且明确的执行任务的方式，从可读性角度来看。传入的函数是实际执行工作的那一个：

``` 
public int Dbl(double i, Func<int> f) { 
 
    return (f(i));
}
``` 
这让我们回到闭包，闭包允许我们拥有非常局部作用域的函数。简单来说，它有点像将函数传递给另一个函数。但与其将函数传递给另一个函数不同，你只是在另一个函数内部有一个函数。这让我们回到上一节的代码，这里重复展示，方便你不必回头查看：

``` 
        let contents = match fs::read_to_string(filename.path()) {
            Ok(contents) => contents,
            Err(why) => panic!("{:?}", filename.path())
        };
``` 
你会发现，`match` 关键字所对应的其实是一个函数内的函数。我们在本章后面会再次看到它，因为这是一个相当有限的实现。通过这个闭包，或者任何闭包，我们获得非常紧凑的作用域标识符。在 `{};` 之内发生的任何事情都不会在函数的其余部分（即使是产生该闭包的函数）可见，更不用说其作用域之外。

闭包有时被称为 *匿名函数*，尽管两者之间存在一些区别。闭包被称为匿名函数的一个原因是，你可以在不命名它的情况下获得函数的所有作用域特性（以及部分语法），而无需为它命名。由于它没有名字（查看前面展示的代码，你会看到用来表示函数/闭包的括号内部没有关联任何名称），我们可以编写函数而无需将其定义为函数，并能够对其进行非常精细的控制和作用域限制。这个闭包只与它关联的 `match` 语句相关。没有理由创建一个更大的函数来将 `match` 传递出去。我们只是创建一个看起来像函数但不命名的东西，然后继续前进。

## THREADING IN THE MAIN

现在你对闭包有了一定了解，我们可以来看看 `main` 函数，这里我们将在创建线程时使用它们。在下面的代码中，你会看到 `main` 函数的完整内容，在我们开始拆解它之前。`main` 函数里做了大量工作，这既是一种设计决策，也是一种便利因素。便利之处在于不必创建全局变量（这通常是一个不好的编程选择），也不必在函数之间传递变量（有时这会带来问题）。因此，我们通过获取当前目录的路径，然后为线程间通信设置流，最后创建线程来执行哈希：

``` 
fn main() -> Result<(),()> { 
    let current_dir = String::from(env::current_dir().unwrap().to_str().unwrap());
    let (mut side1, mut side2) = match UnixStream::pair() {
        Ok((side1, side2)) => (side1, side2),
        Err(e) => {
            println!("Couldn't create a pair of sockets: {:?}", e);
            std::process::exit(-1);
        }
    };
    let serv_handle = thread::spawn( || { sock_server(side1) });
    for file in get_files(&current_dir) {
        let entry = file.unwrap();
        if let Ok(file) = read_file(&entry) {
            let msg = format!("{} : {:x}", entry.path().to_str().unwrap(), Sha256::digest(file.as_bytes()));
            side2.write_all(&msg.into_bytes());
        }
    } 
 
    Ok(())
}
``` 
在继续深入之前，让我们拆解函数的第一行，因为它包含了大量内容。我们需要当前目录的名称，以便稍后将其传递给另一个函数。因此，我们需要一个标识符来存储该值，命名为 `current_dir`。我们需要它是字符串类型，所以使用 `String` 数据结构构造函数 `from()`。这个特征会将稍后调用的值转换为 `String` 结构并存储在 `current_dir` 中。

你可能注意到在 `String::from()` 的调用中有很多内容。首先，我们需要获取当前目录，这可以从 `env` crate 获取，因为它包含在程序执行时的环境变量中，包括 `PATH` 变量以及程序可执行的目录，当然也包括当前目录。返回当前目录的特征返回的是 `PathBuf` 结构体，而 `PathBuf` 结构体被包装在 `Result` 之中。正如所有 `Result` 一样，我们需要 `unwrap()` 它以获取其中的值。

一旦 `unwrap()` 后，我们得到 `PathBuf`，它既不是 `String` 也不是 `String` 可以直接接受的类型。但是，`PathBuf` 结构体有 `to_str()` 特征，我们可以调用它。该特征返回一个 `str`，虽然它不是 `String`，但我们关心的内容（即字符序列）与 `String` 的内容大致相同，只是可能包含一些内部开销。因此，`to_str()` 也返回一个 `Result`，我们需要 `unwrap()` 它以获取底层的 `str` 数据。

于是，我们有一个 `PathBuf` 需要 `unwrap()`，然后调用 `to_str()` 返回一个 `str`，该 `str` 也需要 `unwrap()`。幸运的是，得到的 `str` 是 `String` 可以接受的类型，所以可以作为 `String` 构造函数的参数。

### 创建流

如前所述，我们讨论了进程间通信（IPC）。我们将采用不同于之前探讨的 IPC 方法。下面是用于创建流的代码块，该流将用于线程间通信。我们使用 `UnixStream`，设置它非常简单。和此前一样，我们使用 `match` 语句，因为 `UnixStream` 的设置返回一个 `Result`，我们需要判断设置是否成功或是否出错。创建流的方法是 `UnixStream::pair()`，它返回一个包含元组的 `Result`，这里的元组是一对 `UnixStream` 结构：

``` 
    let (mut side1, mut side2) = match UnixStream::pair() {
        Ok((side1, side2)) => (side1, side2),
        Err(e) => {
            println!("Couldn't create a pair of sockets: {:?}", e);
            std::process::exit(-1);
        }
    };
``` 
我们需要修改这些标识符，因此它们必须是可变的。原因是它们关联于流，意味着它们会被读取或写入，结构需要跟踪其在流中的位置。结构内部有需要修改的值，所以整个结构必须是可变的。此外，这些结构将被传递到函数中并被消耗。

