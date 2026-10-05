In Listing 1.1 the command you should type into your terminal is echo "testing" while the second line that reads "testing" represents the output from the terminal.

# 1.6.2 The subl or ‘atom’ command means “open with your text editor”

I will frequently use the command atom in my command line code listings to represent “opening a file with a text editor.”

On my computer, running atom hello.go will open a file named “hello.go” in Atom, the editor that I use to write My Code.

You are welcome to open files and create new ones however you wish, but I often depict them this way because it is the clearest way I know of representing it in a book.

# 1.6.3 Many code listings will be shortened for clarity

Throughout this book there will be many examples where we are working within a larger file but only need to make a change to a line or two. When this happens, showing a code listing of the entire file would be both confusing and a waste of space.

As a result, I will often show relevant portions of the code and will use comments to represent unchanged code. These comments will often begin with . . ., and might look like Listing 1.2

| Listing 1.2: A simple example of unchanged code |
| func main() { 
| // ... everything before this remains unchanged 
| var name string |