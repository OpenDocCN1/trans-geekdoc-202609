# Connecting with HTTP Servers

sources because PHP’s stream support was vastly improved in that version (of course, using HTTP in the way this code shows was already possible in earlier PHP releases). The idea is that when you use a file operation, you access a stream of data. In practice, it doesn’t really matter whether it’s a file on the local system, on a network share, or on a remote server connected via either HTTP, File Transfer Protocol (FTP), or any other supported protocol. Just provide the appropriate filename, and PHP takes care of the rest. The preceding code shows this: It opens the PHP home page and prints its Hypertext Markup Language (HTML) code in the browser. With just one line of code, it cannot get much more simple. Figure 9.1 contains the output.

![](bbox=[0.16, 0.5, 0.95, 0.81])

Figure 9.1 A one-liner prints the HTML markup of the PHP home page.