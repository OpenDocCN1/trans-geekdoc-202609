# PHP Functions

| Function | Description |
|---|---|
| debugger_off() | Turns off the PHP debugger. |
| debugger_on(server) | Turns on the PHP debugger and connects it to the named server. |
| define_syslog_variables() | Initializes syslog constants. |
| dns_check_record(host[, type]) | Equal to checkdnrr, searches for DNS records based on named parameters. |
| dns_get_mxr(host, hosts[], weight]) | Equal to getmxr, returns MX records based on the named host. |
| fsockopen([hostname, port, errno, errstr, timeout]) | Opens a socket connection based on the named parameters. |
| gethostbyaddr(ip) | Returns the hostname based on the IP address. |
| gethostbyname(host) | Returns the IP address based on the named host. |
| gethostnames(host) | Returns multiple IP addresses based on the named host. |
| getmxr(host, mxhosts[], weight]) | Equal to get_mxr, returns MX records based on the named host. |
| getprotobname(name) | Returns protocol number based on named protocol. |
| getprotobynumber(number) | Returns protocol name based on named protocol number. |
| getservbyname(service, protocol) | Returns a port number based on named parameters. |
| getservbyport(port, protocol) | Returns the service based on named parameters. |
| ip2long(ip) | Converts a string with an IP address into a proper. |
| long2ip(proper_address) | Converts a proper address into an IP address with dotted format. |
| openlog(ident, option, facility) | Opens a connection to the system log, opposite of closelog |
| fsockopen([hostname, port, errno, errstr, timeout]) | Opens a persistent socket connection based on the named parameters. |
| socket_set_blocking(socket, mode) | Determines the blocking mode for the named socket. |
| socket_set_timeout(socket, seconds, microseconds) | Determines the socket timeout period. |
| syslog(priority, message) | Writes the named message to the system log. |