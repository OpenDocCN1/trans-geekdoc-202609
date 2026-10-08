# Core PHP Programming

The date is in the format YYYY-MM-DD. Time is in the format HH:MM:uuuu. The last six digits of time are the seconds and microseconds. The host is the name of the server and pid is the process identifier. The type is a special code described in Table 22-1. The rest of the line is a message terminated with a linefeed.

Using the remote debugger is as simple as executing a PHP script and watching the debug information appear in the port listener output.

| Type | Description |
| --- | --- |
| end | The end of an error message. |\| frames | The number of frames in the call stack. |\| function | The name of the function where the error occurred. |\| location | The filename and line number that generated the error message. |\| message | A PHP error message. |\| start | This type signifies the beginning of a debugging message. The message for this line will be the type of the error. |

# Simulating HTTP Connections

When writing PHP scripts, it is not necessary to understand every detail of the HTTP protocol. I would be straining to include a treatise here, but you ought to have enough understanding so that you could simulate a connection by telnet. You may know that Web servers listen on port 80 by default. HTTP is a text-based protocol, so it's not hard to telnet directly to a Web server and type a simple request. HTTP has several commands that should be familiar; GET and POST are used most often. HEAD is a command that returns just the headers for a request. Browsers use this command to test whether they really want to get an entire document.

It is especially helpful to simulate an HTTP connection when your script sends custom headers. Figure 22-2 is an example showing a request I made to the PHP home page. The text in bold is what I typed. The remote server returned everything.

# Figure 22-2. Simulating an HTTP Connection