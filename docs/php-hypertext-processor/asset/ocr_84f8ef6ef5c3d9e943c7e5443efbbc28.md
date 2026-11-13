# Server variables: $_SERVER

$_SERVER is an array containing information such as headers, paths, and script locations. The entries in this array are created by the web server. There is no guarantee that every web server will provide any of these.

| Variable | Description |
|---|---|
| $_SERVER['PHP_SELF'] | The filename of the currently executing script, relative to the document root |
| $_SERVER['argv'] | Array of arguments passed to the script. When the script is run on the command line, this gives C-style access to the command line parameters. When called via the GET method, this will contain the query string. |
| $_SERVER['argc'] | Contains the number of command line parameters passed to the script if run on the command line. |
| $_SERVER['GATEWAY_INTERFACE'] | What revision of the CGI specification the server is using; i.e. 'CGI/1.1'. |
| $_SERVER['SERVER_ADDR'] | The IP address of the server under which the current script is executing. |
| $_SERVER['SERVER_NAME'] | The name of the server host under which the current script is executing. If the script is running on a virtual host, this will be the value defined for that virtual host. |
| $_SERVER['SERVER_SOFTWARE'] | Server identification string, given in the headers when responding to requests. |
| $_SERVER['SERVER_PROTOCOL'] | Name and revision of the information protocol via which the page was requested; i.e. 'HTTP/1.0'. |
| $_SERVER['REQUEST_METHOD'] | Which request method was used to access the page; i.e. 'GET', 'HEAD', 'POST', 'PUT'. |
| $_SERVER['REQUEST_TIME'] | The timestamp of the start of the request. Available since PHP 5.1.0. |
| $_SERVER['QUERY_STRING'] | The query string, if any, via which the page was accessed. |
| $_SERVER['DOCUMENT_ROOT'] | The document root directory under which the current script is executing, as defined in the server's configuration file. |