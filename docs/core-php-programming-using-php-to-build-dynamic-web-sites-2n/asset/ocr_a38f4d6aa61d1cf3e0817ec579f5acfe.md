# Core PHP Programming

content unique to the page, the stuff that comes before it, and the stuff that comes after it.
This could be hard to maintain, however. Some of the HTML is in one file, some
another. If nothing else you need to flip between two window editors.

Consider for a moment Web page as an object—that is, in an object-oriented way. On
the surface, a Web page is a part of HTML tags containing HEAD tags and BODY tags.
Regardless of the design or content of the page, these tags must exist, and inside
will be placed further tags. Inside the BODY tags table can be used for controlling the
layout of the page. Inside of the cells are either links to other pages on the site or
s content unique to the page.

FreeEnergy is a system that attempts to encapsulate major pieces of each page into files
to be included on. Before I proceed, I want to state my motivations Clearly.
First when developing a Web site is that it be clear and of the highest quality.
Second is that it may be developed and maintained in minimal time. After these needs are
addressed, I consider performance. Performance is considered last because of
relatively cheap cost of faster hardware. Moore's laws show that eighteen months from
now, CPU speed and memory capacity have doubled for the same price. This
double costs nothing but time. Also, experience has shown that a small minority of
code contributes to a majority of the time spent processing. These small sections can be
optimized later, leaving the rest of the code to be written as clearly as possible.

The FreeEnergy system uses more calls to include than you'd find where you are\simply making a few includes at the top of pages. Hits to the file system to take
longer than function calls, of course. You could place everything you need in one
large file and include it on every page, but you will face digging through that large file
when you need to change anything. A trade has been made between the performance of
t application and the time it takes to develop and maintain it.

I called this system FreeEnergy because it seems to draw power from the environment
at PHP provides. The include function in PHP is quite unique and central to
FreeEnergy, especially the allowance for naming a script with a variable. The content
unique to a page is called a screen. The screen name is passed to a single PHP script,
which references the screen name in a large array that matches the screen to
corresponding layout and navigation modules.

The FreeEnergy system breaks Web pages into five modules: action, layout, navigation,
screen, and utility. Action modules perform some sort of write function to a database, a,
or possibly to the network. Only one action module executes during a request, and
t are executed before the screen module. An action module may override the screen
module in the request. This is helpful in cases where an action module is
tempting to process a form and the submitted data are incomplete or otherwise
satisfactory. Action modules never send data directly to the screen. Instead, they
messages to a stack to be popped later by the layout module. It is possible that an action
module will send header information, so it's important that no output be produced.

IT-SC book

637