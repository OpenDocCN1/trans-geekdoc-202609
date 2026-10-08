# Chapter 7. I/O AND DISK ACCESS

HTTP Connections

Writing to the Browser

Output Buffering

Environment Variables

Getting Input from Forms

Cookies

File Uploads

PUT Method Requests

Reading and Writing to Files

Sessions

The `include` and `require` Functions

Ultimately, in order to be useful, a script must communicate with the outside world. We've seen PHP scripts that send text to the browser and get some information from functions like `date`. In this chapter we will examine all the ways a PHP script can exchange data without using special interfaces. This includes reading from local disk drives, connecting to remote machines on the Internet, and receiving input form.

PHP is similar to other programming environments—with one exception: User input comes from HTML forms. The fields in forms are turned into variables. You can't stop your script in the middle and ask the user a question. This situation provides unique challenges. Each time a script runs, it is devoid of context. It is not aware of what has gone on before you make it so.

# HTTP Connections

It will be helpful to review how data travels between a browser and a Web server. I will review it for purposes of illustration, but you may wish to refer to detailed descriptions, such as those found on the W3C Web site <http://www.w3.org/Protocols/>.

When you type a URL into the location box of your browser, the first task of the browser is to break it up into important parts, the first of which is the protocol, HTTP. Next is the