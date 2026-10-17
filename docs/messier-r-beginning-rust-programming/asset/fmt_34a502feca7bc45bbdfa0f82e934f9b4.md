
By comparison, if you look at a language like C#, which does allow you to pass functions as parameters, as well as return functions, you could get something like the following as a function. This function takes two parameters. The first is an integer. The second is a function. This allows a level of abstraction because you could have an interface that was called `Dbl` where the implementation was handled by a number of functions underneath. The `Dbl` interface was just a consistent way of performing a task that was reasonably explicit from a readability perspective. The function being passed in is the one doing the actual work:

``` 
public int Dbl(double i, Func<int> f) { 
 
    return (f(i));
}
``` 
This brings us to closures, which allow us to have very narrowly scoped functions. In essence, it's a little like passing a function into a function. But instead of passing a function into a function, you just have a function inside of another function. This brings us back to the code we were looking at in the last section, repeated here so you don't have to flip back. You can look at this section a little differently now:

``` 
        let contents = match fs::read_to_string(filename.path()) {
            Ok(contents) => contents,
            Err(why) => panic!("{:?}", filename.path())
        };
``` 
What you will see is that what you have with the `match` keyword is really a function inside a function. We'll see this again later in this chapter, because this is a fairly limited implementation. What we get with this closure, or any closure, are very tightly scoped identifiers. Nothing that happens inside the `{};` is available outside of that scope, even in the rest of the function this happens in.

Closures are sometimes called *anonymous functions*, although there are some distinctions between the two. One reason a closure is called an anonymous function is that you get all of the scoping features (and some of the syntax) of a function without having to name it. Since it has no name (look at the code shown previously, and you will see no name associated with the brackets that denote the function/closure code—it is anonymous), we have the ability to write functions without defining them as functions and allow them to be very tightly controlled and scoped. This closure is only relevant to the `match` statement it goes with. There is no reason to create a larger function to send the `match` off to. We just create something that looks a little like a function and don't give it a name, and we're off to the races.

## THREADING IN THE MAIN

Now that you understand a little about closures, we can take a look at the `main` function, where we are going to make use of them when we create threads. In the following code, you will see the complete code from the `main` function before we start to dissect it. There is a lot of work being done in the `main` function, which is something of a design decision as well as a convenience factor. The convenience is not having to either create global variables, which is generally a bad programming choice, or pass variables around between functions, which can be problematic at times. As a result, we have the case where we are getting the location of the current directory and then setting up streams for our threads to communicate with before we finally create threads to do the hashing:

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
Before we go any further, let's tease apart the very first line of this function, because there is a lot going on in it. We will need the name of the directory we are currently in so we can pass that value into another function later on. As a result, we need an identifier to store that value, which we are calling `current_dir`. We need this to be a string, so we are going to use a `String` data structure constructor named `from()`. This trait takes the value we'll get back from the call we'll be making in a moment and returns a `String` structure to be stored in `current_dir`.

You may notice that inside the call to `String::from()` there is a lot going on. First, we need to get the current directory, which we can pull from the `env` crate because it would be stored in the environment that is given to the program when it is executed. This includes things like the `PATH` variable, storing all the directories where executables might be found, as well as the current directory. The problem with the trait that returns the current directory to us is that it comes back as a data structure called `PathBuf`. On top of that, the `PathBuf` structure we get will be wrapped inside a `Result`. As always with a `Result`, we have to `unwrap()` it to get the goodies out.

Once unwrapped, we have this `PathBuf`, which is not a `String` or anything our `String` type can take as an input to be stored as a `String`. However, the `PathBuf` structure has a `to_str()` trait that we can call. This returns a `str`, which is still not a `String`, although the contents of the two—at least, the contents we care about (and not any overhead that may be stored inside the data structure)—will be roughly the same: an ordered collection of Unicode characters. Since the `to_str()` trait returns a `Result`, as you'd expect, we need to unwrap that `Result` to get the underlying `str` data.

So, we have a `PathBuf` that needs to be unwrapped, which then has `to_str()` called on it to return a `str` value that also has to be unwrapped. Fortunately, the resulting `str` is an acceptable data type to create a `String` from, so that is what is passed into our `String` constructor.

### Creating Streams

Earlier, we talked about interprocess communication (IPC). We're going to take a different approach to IPC from the ones we looked at earlier. The following is the block of code that is being used to create the two ends of the conversation that the stream will be used for. We are using `UnixStream` for this, and setting it up is very simple. As we've done before, we are using a `match` statement because the return value from setting up the `UnixStream` is going to be a `Result`, and we need to know whether the setup was successful or if it generated an error. The method being used to create the stream is `UnixStream::pair()`, and it returns a `Result` with a tuple, which in this case is a pair of `UnixStream` structures:

``` 
    let (mut side1, mut side2) = match UnixStream::pair() {
        Ok((side1, side2)) => (side1, side2),
        Err(e) => {
            println!("Couldn't create a pair of sockets: {:?}", e);
            std::process::exit(-1);
        }
    };
``` 
We are going to need to make changes to these identifiers, so they have to be mutable. The reason for this is that they are data structures associated with a stream, which means they are being read from or written to, and the structure will have to keep track of where in the stream it is. There will be internal values to the structure that need to be altered, so the entire structure has to be mutable. Additionally, these structures will need to be passed into a function where they will be consumed.
