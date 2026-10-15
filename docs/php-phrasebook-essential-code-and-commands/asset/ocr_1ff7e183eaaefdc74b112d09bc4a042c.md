TIP

This works well if only one server's status must be checked. If there are several servers, this approach has some disadvantages. The call to fsockopen() might take up to the timeout value until the next command is executed.
Therefore, all servers are checked sequentially and synchronously. This just takes too long for several servers.
However, with PHP 5 and stream sockets, this can be done asynchronously. The code is a bit complicated, but Wez Furlong explains this approach in great detail at http://netevil.org/node.php?nid=280.

# Understanding Web Services

Some people say Web Services are just old wine in new bottles because the idea behind them is far from new. The basic principle is: Two machines talk to each other. For instance, one machine contains some business logic or, more generally, some information, and the other machine requests this information (or wants to use the business logic).

This has been done for many years, but only a few years ago the major players sat together and started to work on protocols to put the whole communication on top of standards. Some of these standards are now under the aegis of the World Wide Web Consortium (W3C), whereas others are managed by the Organization for the Advancement of Structured Information Standards (OASIS) consortium.

A multitude of books are available on Web Services, with quite a lot of pages. However, in accordance with the concept of this phrasebook, this chapter puts it simple but still gives you all you need to know. There