   

![Image 1](index-1_1.jpg)

V I S U A L Q U I C K S T A R T G U I D E

PHP for

the Web

Fourth Edition

LARRY ULLMAN

Peachpit Press

Visual QuickStart Guide

**PHP for the Web, Fourth Edition**

Larry Ullman

Peachpit Press

1249 Eighth Street

Berkeley, CA 94710

510/524-2178

510/524-2221 (fax)

Find us on the W[eb at: www.peachpit.com](http://www.peachpit.com)

To report errors, please send a note to: errata@peachpit.com

Peachpit Press is a division of Pearson Education.

Copyright © 2011 by Larry Ullman

Editor: Rebecca Gulick

Copyeditor: Liz Welch

Technical Reviewer: Jay Blanchard

Proofreader: Bob Campbell

Production Coordinator: Myrna Vladic

Compositor: Debbie Roberti

Indexer: Valerie Haynes-Perry

Cover Design: RHDG / Riezebos Holzbaur Design Group, Peachpit Press Interior Design: Peachpit Press

L[ogo Design: MINE™ www.minesf.com](http://www.minesf.com)

**Notice of Rights**

All rights reserved. No part of this book may be reproduced or transmitted in any form by any means, electronic, mechanical, photocopying, recording, or otherwise, without the prior written permission of the publisher. For information on getting permission for reprints and excerpts, contact permissions@peachpit.com.

**Notice of Liability**

The information in this book is distributed on an “As Is” basis, without warranty. While every precaution has been taken in the preparation of the book, neither the author nor Peachpit Press shall have any liability to any person or entity with respect to any loss or damage caused or alleged to be caused directly or indirectly by the instructions contained in this book or by the computer software and hardware products described in it.

**Trademarks**

Visual QuickStart Guide is a registered trademark of Peachpit Press, a division of Pearson Education. Macintosh and Mac OS X are registered trademarks of Apple Computer, Inc. Microsoft and Windows are registered trademarks of Microsoft Corp. Other product names used in this book may be trademarks of their own respective owners. Images of Web sites in this book are copyrighted by the original holders and are used with their kind permission. This book is not officially endorsed by nor affiliated with any of the above companies.

Many of the designations used by manufacturers and sellers to distinguish their products are claimed as trademarks. Where those designations appear in this book, and Peachpit was aware of a trademark claim, the designations appear as requested by the owner of the trademark. All other product names and services identified throughout this book are used in editorial fashion only and for the benefit of such companies with no intention of infringement of the trademark. No such use, or the use of any trade name, is intended to convey endorsement or other affiliation with this book.

ISBN-13: 978-0-321-73345-0

ISBN-10: 0-321-73345-2

9 8 7 6 5 4 3 2 1

Printed and bound in the United States of America

**Dedication**

For Jessica, Gina, and Rich, with gratitude for all of their love and support.

**Special Thanks to:**

Many, many thanks to everyone at Peachpit Press for their assistance and hard work, especially:

The best darn editor in the world, Rebecca Gulick. Thanks for, well, just about everything.

Liz Welch, for her attention to detail.

Jay Blanchard, for the technical review and for his uncanny ability to predict what I’m going to say next.

Bob Campbell, for the sharp proofreading eye.

Deb Roberti and Myrna Vladic, who take a bunch of disparate stuff and turn it into a book. Valerie Haynes-Perry for the excellent indexing.

Everyone at Peachpit for doing what’s required to create, publish, distribute, market, sell, and support these books.

My sincerest thanks to the readers of the other editions of this book and my other books. Thanks for your feedback and support and for keeping me in business.

Rasmus Lerdorf (who got the PHP ball rolling), the people at PHP.net and Zend.com, those who frequent the various newsgroups and mailing lists, and the greater PHP and open source communities for developing, improving upon, and supporting such wonderfully useful technology.

Karnesha, for entertaining the kids so that I can get some work done, even if I’d rather not.

Zoe and Sam, for continuing to be the kid epitome of awesomeness.

Jessica, for doing everything you do and everything you can. And for making all this mess work as well as it can, all things considered.

Table of Contents

[Introduction . . . . . . . . . . . . . . . . . . . . . . . . . . . ix](#index_split_000.html#p10)

[**Chapter 1**](#index_split_000.html#p22)

[Getting Started with PHP . . . . . . . . . . . . . . . . . . 1](#index_split_000.html#p22)

[Basic HTML Syntax. . . . . . . . . . . . . . . . . . . . . . . . . 2](#index_split_000.html#p23)

[Basic PHP Syntax . . . . . . . . . . . . . . . . . . . . . . 7](#index_split_000.html#p28)

[Using FTP . . . . . . . . . . . . . . . . . . . . . . . . . . 10](#index_split_000.html#p31)

[Testing Your Script . . . . . . . . . . . . . . . . . . . . . 12](#index_split_000.html#p33)

[Sending Text to the Browser . . . . . . . . . . . . . . . . 15](#index_split_000.html#p36)

[Using the PHP Manual . . . . . . . . . . . . . . . . . . . 18](#index_split_000.html#p39)

[Sending HTML to the Browser . . . . . . . . . . . . . . . 22](#index_split_000.html#p43)

[Adding Comments to Scripts. . . . . . . . . . . . . . . . 25](#index_split_001.html#p46)

[Basic Debugging Steps . . . . . . . . . . . . . . . . . . . 28](#index_split_001.html#p49)

[Review and Pursue . . . . . . . . . . . . . . . . . . . . . 30](#index_split_001.html#p51)

[**Chapter 2**](#index_split_001.html#p52)

[Variables . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 31](#index_split_001.html#p52)

[What Are Variables? . . . . . . . . . . . . . . . . . . . . . 32](#index_split_001.html#p53)

[Variable Syntax . . . . . . . . . . . . . . . . . . . . . . . 36](#index_split_001.html#p57)

[Types of Variables . . . . . . . . . . . . . . . . . . . . . . 38](#index_split_001.html#p59)

[Variable Values. . . . . . . . . . . . . . . . . . . . . . . . 41](#index_split_001.html#p62)

[Understanding Quotation Marks . . . . . . . . . . . . . 45](#index_split_001.html#p66)

[Review and Pursue . . . . . . . . . . . . . . . . . . . . . 48](#index_split_001.html#p69)

[**Chapter 3**](#index_split_001.html#p70)

[HTML Forms and PHP . . . . . . . . . . . . . . . . . . . . 49](#index_split_001.html#p70)

[Creating a Simple Form . . . . . . . . . . . . . . . . . . . 50](#index_split_001.html#p71)

[Choosing a Form Method . . . . . . . . . . . . . . . . . . 54](#index_split_001.html#p75)

[Receiving Form Data in PHP . . . . . . . . . . . . . . . . 57](#index_split_001.html#p78)

[Displaying Errors . . . . . . . . . . . . . . . . . . . . . . . 61](#index_split_002.html#p82)

[Error Reporting . . . . . . . . . . . . . . . . . . . . . . . . 64](#index_split_002.html#p85)

[Manually Sending Data to a Page . . . . . . . . . . . . . 67](#index_split_002.html#p88)

[Review and Pursue . . . . . . . . . . . . . . . . . . . . . 72](#index_split_002.html#p93)

Table of Contents v

[**Chapter 4**](#index_split_002.html#p94)

[Using Numbers . . . . . . . . . . . . . . . . . . . . . . . . . 73](#index_split_002.html#p94)

[Creating the Form . . . . . . . . . . . . . . . . . . . . . . 74](#index_split_002.html#p95)

[Performing Arithmetic. . . . . . . . . . . . . . . . . . . . 77](#index_split_002.html#p98)

[Formatting Numbers . . . . . . . . . . . . . . . . . . . . 81](#index_split_002.html#p102)

[Understanding Precedence . . . . . . . . . . . . . . . . 84](#index_split_002.html#p105)

[Incrementing and Decrementing a Number . . . . . . . 86](#index_split_002.html#p107)

[Creating Random Numbers . . . . . . . . . . . . . . . . 88](#index_split_002.html#p109)

[Review and Pursue . . . . . . . . . . . . . . . . . . . . . 90](#index_split_002.html#p111)

[**Chapter 5**](#index_split_002.html#p112)

[Using Strings . . . . . . . . . . . . . . . . . . . . . . . . . . . 91](#index_split_002.html#p112)

[Creating the HTML Form . . . . . . . . . . . . . . . . . . 92](#index_split_002.html#p113)

[Concatenating Strings . . . . . . . . . . . . . . . . . . . 95](#index_split_002.html#p116)

[Handling Newlines. . . . . . . . . . . . . . . . . . . . . . 98](#index_split_002.html#p119)

[HTML and PHP . . . . . . . . . . . . . . . . . . . . . . . . . 100](#index_split_002.html#p121)

[Encoding and Decoding Strings . . . . . . . . . . . . . . . 103](#index_split_002.html#p124)

[Finding Substrings. . . . . . . . . . . . . . . . . . . . . . . . 107](#index_split_002.html#p128)

[Replacing Parts of a String . . . . . . . . . . . . . . . . . 111](#index_split_002.html#p132)

[Review and Pursue . . . . . . . . . . . . . . . . . . . . . 114](#index_split_002.html#p135)

[**Chapter 6**](#index_split_002.html#p136)

[Control Structures. . . . . . . . . . . . . . . . . . . . . 115](#index_split_002.html#p136)

[Creating the HTML Form . . . . . . . . . . . . . . . . . . 116](#index_split_002.html#p137)

[The if Conditional . . . . . . . . . . . . . . . . . . . . . . 119](#index_split_003.html#p140)

[Validation Functions . . . . . . . . . . . . . . . . . . . . . . 122](#index_split_003.html#p143)

[Using else . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 126](#index_split_003.html#p147)

[More Operators . . . . . . . . . . . . . . . . . . . . . . . . . 129](#index_split_003.html#p150)

[Using elseif . . . . . . . . . . . . . . . . . . . . . . . . . . . . 138](#index_split_003.html#p159)

[The Switch Conditional . . . . . . . . . . . . . . . . . . . . 142](#index_split_003.html#p163)

[The for Loop . . . . . . . . . . . . . . . . . . . . . . . . . . . 146](#index_split_003.html#p167)

[Review and Pursue . . . . . . . . . . . . . . . . . . . . . 150](#index_split_003.html#p171)

[**Chapter 7**](#index_split_003.html#p172)

[Using Arrays . . . . . . . . . . . . . . . . . . . . . . . . 151](#index_split_003.html#p172)

[What Is an Array? . . . . . . . . . . . . . . . . . . . . . . . . 152](#index_split_003.html#p173)

[Creating an Array . . . . . . . . . . . . . . . . . . . . . . . . 154](#index_split_003.html#p175)

[Adding Items to an Array . . . . . . . . . . . . . . . . . . . 158](#index_split_003.html#p179)

[Accessing Array Elements . . . . . . . . . . . . . . . . . . 161](#index_split_003.html#p182)

[Creating Multidimensional Arrays . . . . . . . . . . . . . . . 164](#index_split_003.html#p185)

[Sorting Arrays . . . . . . . . . . . . . . . . . . . . . . . . . . 168](#index_split_004.html#p189)

[Transforming Between Strings and Arrays . . . . . . . . 172](#index_split_004.html#p193)

[Creating an Array from a Form . . . . . . . . . . . . . . . . 176](#index_split_004.html#p197)

[Review and Pursue . . . . . . . . . . . . . . . . . . . . . . . 182](#index_split_004.html#p203)

vi Table of Contents

[**Chapter 8**](#index_split_004.html#p204)

[Creating Web Applications . . . . . . . . . . . . . . . 183](#index_split_004.html#p204)

[Creating Templates . . . . . . . . . . . . . . . . . . . . . . . 184](#index_split_004.html#p205)

[Using External Files. . . . . . . . . . . . . . . . . . . . . . . 192](#index_split_004.html#p213)

[Using Constants . . . . . . . . . . . . . . . . . . . . . . . . . 197](#index_split_004.html#p218)

[Working with the Date and Time. . . . . . . . . . . . . . . 201](#index_split_004.html#p222)

[Handling HTML Forms with PHP, Revisited . . . . . . . . 204](#index_split_004.html#p225)

[Making Forms Sticky . . . . . . . . . . . . . . . . . . . . . . 210](#index_split_004.html#p231)

[Sending Email . . . . . . . . . . . . . . . . . . . . . . . . . . 217](#index_split_004.html#p238)

[Output Buffering. . . . . . . . . . . . . . . . . . . . . . 222](#index_split_005.html#p243)

[Manipulating HTTP Headers . . . . . . . . . . . . . . . 225](#index_split_005.html#p246)

[Review and Pursue . . . . . . . . . . . . . . . . . . . . 230](#index_split_005.html#p251)

[**Chapter 9**](#index_split_005.html#p252)

[Cookies and Sessions. . . . . . . . . . . . . . . . . . . . 231](#index_split_005.html#p252)

[What Are Cookies? . . . . . . . . . . . . . . . . . . . . 232](#index_split_005.html#p253)

[Creating Cookies . . . . . . . . . . . . . . . . . . . . . 234](#index_split_005.html#p255)

[Reading from Cookies . . . . . . . . . . . . . . . . . . 239](#index_split_005.html#p260)

[Adding Parameters to a Cookie . . . . . . . . . . . . . 242](#index_split_005.html#p263)

[Deleting a Cookie . . . . . . . . . . . . . . . . . . . . . 245](#index_split_005.html#p266)

[What Are Sessions? . . . . . . . . . . . . . . . . . . . . 248](#index_split_005.html#p269)

[Creating a Session . . . . . . . . . . . . . . . . . . . . 249](#index_split_005.html#p270)

[Accessing Session Variables . . . . . . . . . . . . . . . 252](#index_split_005.html#p273)

[Deleting a Session . . . . . . . . . . . . . . . . . . . . 254](#index_split_005.html#p275)

[Review and Pursue . . . . . . . . . . . . . . . . . . . . 256](#index_split_005.html#p277)

[**Chapter 10** Creating Functions . . . . . . . . . . . . . . . . . . . . 257](#index_split_005.html#p278)

[Creating and Using Simple Functions. . . . . . . . . . 258](#index_split_005.html#p279)

[Creating and Calling Functions That](#index_split_005.html#p286)

[Take Arguments. . . . . . . . . . . . . . . . . . . . . 265](#index_split_005.html#p286)

[Setting Default Argument Values . . . . . . . . . . . . . . 271](#index_split_005.html#p292)

[Creating and Using Functions That Return a Value. . . . 274](#index_split_005.html#p295)

[Understanding Variable Scope . . . . . . . . . . . . . 279](#index_split_006.html#p300)

[Review and Pursue . . . . . . . . . . . . . . . . . . . . 286](#index_split_006.html#p307)

[**Chapter 11** Files and Directories . . . . . . . . . . . . . . . . . . . 287](#index_split_006.html#p308)

[File Permissions . . . . . . . . . . . . . . . . . . . . . . 288](#index_split_006.html#p309)

[Writing to Files . . . . . . . . . . . . . . . . . . . . . . . 293](#index_split_006.html#p314)

[Locking Files . . . . . . . . . . . . . . . . . . . . . . . . . . . 301](#index_split_006.html#p322)

[Reading from Files. . . . . . . . . . . . . . . . . . . . . 304](#index_split_006.html#p325)

[Handling File Uploads . . . . . . . . . . . . . . . . . . 307](#index_split_006.html#p328)

[Navigating Directories . . . . . . . . . . . . . . . . . . . . . 315](#index_split_006.html#p336)

[Creating Directories . . . . . . . . . . . . . . . . . . . . 320](#index_split_006.html#p341)

[Reading Files Incrementally . . . . . . . . . . . . . . . 327](#index_split_006.html#p348)

[Review and Pursue . . . . . . . . . . . . . . . . . . . . 332](#index_split_006.html#p353)

Table of Contents vii

[**Chapter 12** Intro to Databases . . . . . . . . . . . . . . . . . . . . 333](#index_split_006.html#p354)

[Introduction to SQL . . . . . . . . . . . . . . . . . . . . 334](#index_split_006.html#p355)

[Connecting to MySQL. . . . . . . . . . . . . . . . . . . 336](#index_split_006.html#p357)

[MySQL Error Handling . . . . . . . . . . . . . . . . . . 340](#index_split_006.html#p361)

[Creating and Selecting a Database . . . . . . . . . . . 343](#index_split_006.html#p364)

[Creating a Table . . . . . . . . . . . . . . . . . . . . . . . . . 347](#index_split_007.html#p368)

[Inserting Data into a Database . . . . . . . . . . . . . . 352](#index_split_007.html#p373)

[Securing Query Data . . . . . . . . . . . . . . . . . . . 358](#index_split_007.html#p379)

[Retrieving Data from a Database . . . . . . . . . . . . . . 361](#index_split_007.html#p382)

[Deleting Data in a Database . . . . . . . . . . . . . . . 366](#index_split_007.html#p387)

[Updating Data in a Database. . . . . . . . . . . . . . . 372](#index_split_007.html#p393)

[Review and Pursue . . . . . . . . . . . . . . . . . . . . 378](#index_split_007.html#p399)

[**Chapter 13** Putting It All Together . . . . . . . . . . . . . . . . . . . 379](#index_split_007.html#p400)

[Getting Started . . . . . . . . . . . . . . . . . . . . . . 380](#index_split_007.html#p401)

[Connecting to the Database . . . . . . . . . . . . . . . 382](#index_split_007.html#p403)

[Writing the User-Defined Function . . . . . . . . . . . 383](#index_split_007.html#p404)

[Creating the Template . . . . . . . . . . . . . . . . . . 385](#index_split_007.html#p406)

[Logging In . . . . . . . . . . . . . . . . . . . . . . . . . 388](#index_split_007.html#p409)

[Logging Out . . . . . . . . . . . . . . . . . . . . . . . . 392](#index_split_007.html#p413)

[Adding Quotes. . . . . . . . . . . . . . . . . . . . . . . 393](#index_split_007.html#p414)

[Listing Quotes . . . . . . . . . . . . . . . . . . . . . . . 397](#index_split_007.html#p418)

[Editing Quotes . . . . . . . . . . . . . . . . . . . . . . . 400](#index_split_007.html#p421)

[Deleting Quotes . . . . . . . . . . . . . . . . . . . . . . 406](#index_split_008.html#p427)

[Creating the Home Page . . . . . . . . . . . . . . . . . . . 410](#index_split_008.html#p431)

[Review and Pursue . . . . . . . . . . . . . . . . . . . . . . . 414](#index_split_008.html#p435)

[**Appendix A** Installation and Configuration . . . . . . . . . . . . . 415](#index_split_008.html#p436)

[**Appendix B** Resources and Next Steps . . . . . . . . . . . . . . . . 437](#index_split_008.html#p458)

[Index . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 447](#index_split_008.html#p468)

viii Table of Contents

[Introduction](#index_split_000.html#p6)

When I began the first edition of this book

This book will teach you PHP, providing

in 2000, PHP was a little-known open

both a solid understanding of the

source project. It was adored by technical

fundamentals and a sense of where to look

people in the know but not yet recognized

for more advanced information. Although

as the popular choice for Web development

it isn’t a comprehensive programming

that it is today. When I taught myself PHP,

reference, through demonstrations and

very little documentation was available on

real-world examples, this book provides

the language—and that was my motivation

the knowledge you need to begin building

for writing this book in the first place.

dynamic Web sites and Web applications

using PHP.

Today things are different. The Internet

has gone through a boom and a bust and

has righted itself. Furthermore, PHP is now

the reigning king of dynamic Web design

**What Is PHP?**

tools and has expanded somewhat beyond

the realm of just Web development. But

PHP originally stood for Personal Home

despite PHP’s popularity and the increase

Page. It was created in 1994 by Rasmus

in available documentation, sample code,

Lerdorf to track the visitors to his online

and examples, a good book discussing the

résumé. As its usefulness and capabilities

language is still relevant. Although PHP

grew (and as it began to be utilized in

is in the midst of its fifth major release,

more professional situations), PHP came to

a book such as this—which teaches the

mean PHP: Hypertext Preprocessor. (The

language in simple but practical terms—

definition basically means that PHP handles

can still be your best guide in learning the

data before it becomes HTML—which

information you need to know.

stands for Hypertext Markup Language.)

Introduction ix

![Image 2](index-11_1.jpg)

According to the official PHP Web site,

[found at www.php.net](http://www.php.net) **A**, PHP is a

“widely-used general-purpose scripting

language that is especially suited for Web

development and can be embedded into

HTML.” I’ll explain the two key parts of this

definition in more detail.

To say that PHP can be embedded into

HTML means that PHP code can be written

within your HTML code—HTML being the

code with which all Web pages are built.

Therefore, programming with PHP starts

**A** As of this writing, this is the appearance of the

off as only slightly more complicated than

official PHP Web site[, located at www.php.net.](http://www.php.net)

hand-coding HTML.

Naturally, this should be the first place you look to

address most of your PHP questions and curiosities.

Also, PHP is a scripting language, as

opposed to a compiled language.

This means that PHP is designed to do

something only after an event occurs—for

example, when a user submits a form or

goes to a URL (Uniform Resource Locator—

the technical term for a Web address).

Another popular example of a scripting

language is JavaScript, which commonly

handles events that occur within the Web

browser. These two languages can also

be described as interpreted, because the

code must be run through an executable,

such as the PHP module or the browser’s

JavaScript component. Conversely,

compiled languages such as C and C+ + can

be used to write stand-alone applications

that can act independent of any event.

x Introduction

![Image 3](index-12_1.jpg)

You should also understand that PHP is a

server-side technology. This refers to the

fact that everything PHP does occurs on

the server (as opposed to on the client,

which is the computer being used by the

person viewing the Web site). A server

is just a computer set up to provide the

pages you see when you go to a Web

address with your browser (for example,

Firefox, Microsoft Internet Explorer, or

Safari). I’ll discuss this process in more

detail later (see “How PHP Works”).

**B** This is the home page of Zend, creators of the

programming at the heart of PHP. The site contains

Finally, PHP is cross-platform, meaning that

useful software as well as a code gallery and well-

it can be used on machines running Unix,

written tutorials.

Windows, Macintosh, and other operating

systems. Again, we’re talking about the

server’s operating system, not the client’s.

**What PHP Is Not**

Not only can PHP run on almost any

The thing about PHP that confuses most

operating system, but, unlike many other

new learners is what PHP can’t do.

programming languages, it enables you

Although you can use the language for an

to switch your work from one platform to

amazing array of tasks, its main limitation

another with few or no modifications.

is that PHP cannot be used for client-side

features found in some Web sites.

At the time this book was written, PHP

was simultaneously in versions 5.3.5 and

Using a client-side technology like

5.2.17. (There are slight differences between

JavaScript, you can create a new

versions 5.3 and 5.2, so 5.2 continues to be

browser window, add mouseovers,

make pop-up alerts, resize the browser

supported for a while.) Although this book

window, find out the screen size on

was written using a stable version of PHP 5.3,

the user’s machine, and dynamically

all of the code is backward compatible, at

generate and alter forms. None of these

least to PHP version 5.x, if not to 4.x. In a

tasks can be accomplished using PHP

couple of situations where a feature requires

(because PHP is server-side, whereas

a more current version of PHP, or where

those are client-side issues). But, you can

older versions might have slight variations,

use PHP to create JavaScript, just as you

a note in a sidebar or a tip will indicate how

can use PHP to create HTML.

you can adjust the code accordingly.

When it comes time to develop your own

More information can be found at PHP.net

PHP projects, remember that you can

[and www.zend.com, the minds behind the](http://www.zend.com)

only use PHP to send information (HTML

and such) to the Web browser. You can’t

core of PHP **B**.

do anything else within the Web browser

until another request from the server has

been made (a form has been submitted

or a link has been clicked).

Introduction xi

![Image 4](index-13_1.png)

**Why Use PHP?**

and lasting Web sites. Toward this end,

server-side technologies such as PHP have

Put simply, PHP is better, faster, and easier

become the norm. These technologies

to learn than the alternatives. All Web

allow Web page designers to create

sites must begin with just HTML, and you

Web applications that are dynamically

can create an entire site using a number

generated, taking into account whichever

of static HTML pages. But basic HTML is

elements the programmer desires. Often

a limited approach that does not allow

database-driven, these advanced sites can

for flexibility or responsiveness. Visitors

be updated and maintained more readily

accessing HTML-only sites see simple

than static HTML pages.

pages with no level of customization or

When it comes to choosing a server-side

dynamic behavior. With PHP, you can

technology, the primary alternatives to PHP

create exciting and original pages based

are CGI scripts (Common Gateway Interface,

on whatever factors you want to consider.

commonly, but not necessarily written

PHP can also interact with databases and

in Perl), ASP.NET (Active Server Pages),

files, handle email, and do many other

Adobe’s ColdFusion, JSP (JavaServer

things that HTML alone cannot.

Pages), and Ruby on Rails. And although

Webmasters learned a long time ago

there are some server-side JavaScript

that HTML alone won’t produce enticing

tools now available, JavaScript isn’t truly

an alternative to PHP (or vice versa).

**A** The Web Technology Surveys site says that PHP is running on 75% of all Web sites

[(http://w3techs.com/technologies/overview/programming\_language/all).](http://w3techs.com/technologies/overview/programming_language/all)

xii Introduction

![Image 5](index-14_1.png)

So the question is, why should a Web

was created to do), PHP isn’t a “better”

designer use PHP instead of CGI, ASP.NET,

programming language than Java or

JSP, or whatever to make a dynamic Web site?

Perl—they can do things PHP can’t.

■

**PHP is much easier to learn and use.**

■

**PHP is both free and cross-platform.**

People—perhaps like you—without any

Therefore, you can learn and use PHP

formal programming training can write

on nearly any computer and at no cost.

PHP scripts with ease after reading

Furthermore, its open source nature

this one book. In comparison, ASP.NET

means that PHP’s users are driving its

requires an understanding of VBScript,

development, not some corporate entity.

C#, or another language; and CGI

■

**PHP is the most popular tool available**

requires Perl (or C). These are more

**for developing dynamic Web sites.** As

complex languages and are much more

of this writing, PHP is in use on over

difficult to learn.

75% of all Web sites **A** and is the fourth

■

**PHP was written specifically for**

most popular programming language

**dynamic Web page creation.** Perl (and

overall **B**. Many of the biggest Web

VBScript and Java and Ruby) were not,

sites—Yahoo!, Wikipedia, and Facebook,

and this fact suggests that, by its very

just to name three—and content

intent, PHP can do certain tasks faster

management tools, such as WordPress,

and more easily than the alternatives.

Drupal, Moodle, and Joomla, use PHP.

I’d like to make it clear, however, that

By learning this one language, you’ll

although I’m suggesting PHP is better

provide yourself with either a usable

for certain things (specifically those it

hobby or a lucrative skill.

**B** [The Tiobe Index (http://www.tiobe.com/index.php/content/paperinfo/](http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html)

[tpci/index.html) uses a combination of factors to rank the popularity of](http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html)

programming languages.

Introduction xiii

![Image 6](index-15_1.png)

![Image 7](index-15_2.jpg)

![Image 8](index-15_3.png)

![Image 9](index-15_4.png)

![Image 10](index-15_5.png)

![Image 11](index-15_6.jpg)

![Image 12](index-15_7.png)

![Image 13](index-15_8.png)

![Image 14](index-15_9.png)

![Image 15](index-15_10.png)

![Image 16](index-15_11.png)

![Image 17](index-15_12.jpg)

![Image 18](index-15_13.jpg)

![Image 19](index-15_14.png)

![Image 20](index-15_15.png)

![Image 21](index-15_16.png)

![Image 22](index-15_17.png)

![Image 23](index-15_18.png)

![Image 24](index-15_19.png)

![Image 25](index-15_20.png)

![Image 26](index-15_21.png)

![Image 27](index-15_22.jpg)

![Image 28](index-15_23.jpg)

![Image 29](index-15_24.jpg)

![Image 30](index-15_25.png)

![Image 31](index-15_26.png)

![Image 32](index-15_27.png)

![Image 33](index-15_28.jpg)

![Image 34](index-15_29.jpg)

![Image 35](index-15_30.png)

![Image 36](index-15_31.jpg)

![Image 37](index-15_32.png)

![Image 38](index-15_33.png)

![Image 39](index-15_34.jpg)

![Image 40](index-15_35.png)

![Image 41](index-15_36.png)

![Image 42](index-15_37.png)

![Image 43](index-15_38.jpg)

![Image 44](index-15_39.png)

![Image 45](index-15_40.png)

![Image 46](index-15_41.png)

![Image 47](index-15_42.png)

![Image 48](index-15_43.png)

![Image 49](index-15_44.jpg)

![Image 50](index-15_45.jpg)

![Image 51](index-15_46.png)

![Image 52](index-15_47.png)

![Image 53](index-15_48.png)

![Image 54](index-15_49.png)

![Image 55](index-15_50.png)

![Image 56](index-15_51.png)

![Image 57](index-15_52.png)

![Image 58](index-15_53.png)

**How PHP Works**

occurs **B**. Hence, to the end user’s

browser, there may or may not be an

PHP is a server-side language, which

obvious difference between what **home.**

means the code you write in PHP resides

**html** and **home.php** look like, but how

on a host computer that serves Web pages

you arrive at that point is critically altered.

to Web browsers. When you go to a Web

The major difference is that by using PHP,

[site (www.LarryUllman.com, for example),](http://www.LarryUllman.com)

you can have the server dynamically

your Internet service provider (ISP) directs

generate the HTML code. For example,

your request to the server that holds the

different information could be presented

[www.LarryUllman.com information. That](http://www.LarryUllman.com)

if it’s Monday as opposed to Tuesday or

server reads the PHP code and processes

if the user has visited the page before.

it according to its scripted directions. In this

Dynamic Web page creation sets apart the

example, the PHP code tells the server to

less appealing, static sites from the more

send the appropriate Web page data to

interesting and, therefore, more visited,

your browser in the form of HTML **A**. In

interactive ones.

short, PHP creates an HTML page on the

The central difference between using PHP

fly based on parameters of your choosing.

and using straight HTML is that PHP does

This differs from an HTML-generated site

everything on the server and then sends

in that when a request is made, the server

the appropriate information to the browser.

merely sends the HTML data to the Web

This book covers how to use PHP to send

browser—no server-side interpretation

the right data to the browser.

**A** This graphic demonstrates (albeit in very simplistic terms) how the process works between a client, the server, and a PHP module (an application added to the server to increase its functionality) to send HTML back to the browser.

**B** Compare this direct relationship of how a server works handles basic HTML to **A**. This is also why HTML pages can be viewed in your browser from your own computer—they don’t need to be “served,” but dynamically generated pages need to be accessed through a server that handles the processing.

xiv Introduction

![Image 59](index-16_1.jpg)

**What You’ll Need**

The most important requirement for

working with PHP—because it’s a server-

side scripting language—is access to a

PHP-enabled server. Considering PHP’s

popularity, your ISP or Web host most likely

has this option available to you on their

servers. You’ll need to contact them to see

what technology they support.

Your other option is to install PHP and a

Web server application (like Apache) on

**A** The popular Dreamweaver application

supports PHP development, among other

your own computer. Users of Windows,

server-side technologies.

Mac OS X, or Linux can easily install

and use PHP for no cost. Directions for

installing PHP are available in Appendix A,

“Installation and Configuration.” If you’re up

to the task of using your own PHP-installed

server, you can take some consolation

in knowing that PHP is available for free

from the PHP W[eb site (www.php.net) and](http://www.php.net)

comes in easy-to-install packages. If you

take this approach, and I recommend that

you do, then your computer will act as both

the client and the server.

The second requirement is almost a

given: You must have a text editor on

your computer. Crimson Editor, SciTE,

TextWrangler, and similar freeware

applications are all sufficient for your

purposes; and BBEdit, TextPad, TextMate,

and other commercial applications offer

more features that you may appreciate. If

you’re accustomed to using a graphical

interface (also referred to as WYSIWYG—

What You See Is What You Get) like Adobe

Dreamweaver **A** or Aptana Studio, you

can consult that application’s manual to

see how to program within it**.**

continues on next page

Introduction xv

![Image 60](index-17_1.jpg)

![Image 61](index-17_2.jpg)

Third, you need a method of getting the

scripts you write to the server. If you’ve

installed PHP on your own computer, you

can save the scripts to the appropriate

directory. However, if you’re using a

remote server with your ISP or Web host,

you’ll need an FTP (File Transfer Protocol)

program to send the script to the server.

There are plenty of FTP applications

available; in Chapter 1, “Getting Started

with PHP,” [I use the free FileZilla (http://](http://filezilla-project.org)

[filezilla-project.org](http://filezilla-project.org) **B**) for an example.

**B** The FileZilla application can be used on many

Finally, if you want to follow the examples

different operating systems to move PHP scripts

in Chapter 12, “Intro to Databases,” you

and other files to a remote server.

[need access to MySQL (www.mysql.](http://www.mysql.com)

[com](http://www.mysql.com) **C**) or another database application.

MySQL is available in a free version that

you can install on your own computer.

This book assumes only a basic knowledge

of HTML, although the more comfortable

you are handling raw HTML code without

the aid of a WYSIWYG application such

as Dreamweaver, the easier the transition

to using PHP will be. Every programmer

will eventually turn to an HTML reference

at some time or other, regardless of how

much you know, so I encourage you to

**C** MySQL’s Web site (as of this writing).

keep a good HTML book by your side. One

such introduction to HTML is Elizabeth

Castro’s HTML, XHTML, and CSS: Visual

QuickStart Guide (Peachpit Press, 2007).

Previous programming experience is

certainly not required. However, it may

expedite your learning, because you’ll

quickly see numerous similarities between,

for example, Perl and PHP or JavaScript

and PHP.

xvi Introduction

**Script i.1** A sample PHP script, with line numbers and bold emphasis on a specific section of code.

**About This Book**

This book attempts to convey the

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

1.0 Transitional//EN"

fundamentals of programming with

2

"http://www.w3.org/TR/xhtml1/DTD/

PHP while hinting at some of the more

xhtml1-transitional.dtd">

advanced features you may want to

3

<html xmlns="http://www.w3.org/1999/

consider in the future, without going into

xhtml" xml:lang="en" lang="en">

overwhelming detail. It uses the following

4 <head>

5

<meta http-equiv="Content-Type"

conventions to do so.

content="text/html; charset=utf-8"/>

The step-by-step instructions indicate what

6 <title>Hello,

World!</title>

coding you’re to add to your scripts and

7 </head>

8 <body>

where. The specific text you should type is

**9**

**<?php print "Hello, World!"; ?>**

printed in a unique type style to separate it

10 </body>

from the main body text. For example:

11 </html>

**<?php print "Hello, World!"; ?>**

The PHP code is also written as its own

complete script and is numbered by line for

reference (**Script i.1**). You shouldn’t insert

these numbers yourself, because doing so

will render your work inoperable.

continues on next page

**What’s New in This Book?**

I would consider this fourth edition to be a modest revision of an already solid book. The biggest change in this edition is the removal of the previous version of Chapter 13, covering regular expressions. The type of regular expressions being discussed in earlier versions of the book have since been deprecated, meaning support for them is being dropped from the language. A more complex way of addressing regular expressions is beyond what’s appropriate for beginning readers, and is covered in detail in my PHP 6 and MySQL 5 for Dynamic Web Sites: Visual QuickPro Guide (Peachpit Press, 2008).

As a replacement for the excised material, the new Chapter 13, “Putting It All Together,” walks you through the creation of a fully functioning Web site, using almost everything discussed in the entire book (while still teaching a couple of tricks). I hope you’ll find this added chapter to be an illuminating demonstration of how to apply your new knowledge.

Second, each chapter in this edition of the book now concludes with a “Review and Pursue”

section. Over a page or two, you’ll be asked questions meant to reinforce some of the chapter’s key points. Prompts will direct you toward ways you can learn related, additional information, or try similar exercises. Help with the questions and prompts can be found in the book’s corresponding forum (a[t www.LarryUllman.com/forum/).](http://www.LarryUllman.com/forum/)

Finally, I tweaked some of the examples mostly to satisfy my own drive for perfection.

Introduction xvii

![Image 62](index-19_1.png)

![Image 63](index-19_2.png)

I recommend using a text editor that

Because the column in this book is narrower

automatically displays the line numbers for

than the common text editor screen,

you—the numbers will help when you’re

sometimes lines of PHP code printed in the

debugging your work. In the scripts you’ll

steps have to be broken where they would

sometimes see particular lines highlighted

not otherwise break in your editor. A small

in bold, in order to draw attention to new or

gray arrow indicates when this kind of break

relevant material.

occurs. For example:

Because of the nature of how PHP works,

**print "This is going to be a longer**

you need to understand that there are

➝ **line of code.";**

essentially three views of every script: the

You should continue to use one line in

PHP code (e.g., Script i.1), the code that’s

your scripts, or else you’ll encounter errors

sent to the browser (primarily HTML), and

when executing them. (The gray arrow isn’t

what the browser displays to the end user.

used in scripts that are numbered.)

Where appropriate, sections of or all of the

While demonstrating new features and

browser window are revealed, showing the

techniques, I’ll do my best to explain the

end result of the exercise **A**. Occasionally,

why’s and how’s of them as I go. Between

you’ll also see an image displaying the

reading about and using a function, you

HTML source that the browser received **B**.

should clearly comprehend it. Should

You can normally access this view by

something remain confusing, though, this

choosing View Source or View Page Source

book contains a number of references where

from the appropriate Web browser menu.

you can find answers to any questions (see

To summarize, **B** displays the HTML the

Appendix B, “Resources and Next Steps”). If

browser receives, and **A** demonstrates how

you’re confused by a particular function or

the browser interprets that HTML. Using

example, your best bet will be to check the

PHP, you’ll create the HTML that’s sent to

online PHP manual or the book’s supporting

the browser.

Web site (and its user support forum).

**A** This is a sample view you’ll see of the

browser window. For the purposes of this

book, it won’t make any difference which

Web browser or operating system you use.

**B** By viewing the

source code received

by the Web browser,

you can see the HTML

created by PHP and

sent by the server.

xviii Introduction

**Companion Web Site**

**Which Book Is Right for You?**

While you’re reading this book, you may also

This is the fourth edition of my first

find it helpful to visit the PHP for the Web:

book on PHP. Like the original,

Visual QuickStart Guide, 4th Edition Web

it’s written with the beginner or

site[, found within www.LarryUllman.com.](http://www.LarryUllman.com)

nonprogrammer in mind. If you have

little or no programming experience,

There you’ll find every script in this book

prefer a gentler pace, or like to learn

available in a downloadable form. (However,

things in bite-sized pieces, this is the

I strongly encourage you to type the scripts

book for you. Make no mistake: This

yourself in order to become more familiar

book covers what you need to know

with the structure and syntax of PHP.)

to begin develop dynamic Web sites

The site also includes a more detailed

(while using practical examples), but it

reference section with links to numerous

does so without any in-depth theory or

advanced applications.

useful Web pages where you can continue

learning PHP. In addition, the site provides

Conversely, if you pick up new

an errata page listing any mistakes made

technologies really quickly or already

in this text.

have some experience developing Web

sites, you may find this to be too basic.

What many users find most helpful, though,

In that case, you should consider my

is the book’s supporting forum, found

PHP 6 and MySQL 5 for Dynamic

through the Web site or more directly at

Web Sites: Visual QuickPro Guide

[www.LarryUllman.com/forum/. Using the](http://www.LarryUllman.com/forum/)

instead (Peachpit Press, 2008). It

forum, you can:

discusses SQL and MySQL in much

greater detail and goes through several

■

Find answers to problems you’re having

more complex examples, but it does so

■

Receive advice on how to approach an

at a quick jog.

idea you have

■

Get debugging help

■

See how changes in the technologies

have affected the examples in the book

■

Learn what other people are doing

with PHP

■

Confirm the answers to review questions

■

Receive a faster reply from me than if

you send me a direct email

Introduction xix

**Questions, comments,**

**or suggestions?**

**How to Ask Questions the**

**Smart Way**

If you have a PHP-specific question, there

are newsgroups, mailing lists, and question-

Whether you’re posting a message to

and-answer sections available on PHP-

the book’s supporting forum, sending

related Web sites for you to turn to. These

me an email, or asking a question in

a newsgroup, knowing how to most

are discussed in more detail in Appendix B.

effectively ask a question improves the

Browsing through these references or

quality of the response you’ll receive as

searching the Internet will almost always

well as the speed with which you’ll get

provide you with the fastest answer.

your answer. To receive the best answer

You can also direct your questions,

in the shortest amount of time, follow

comments, and suggestions to me. You’ll

these steps:

get the fastest reply using the book’s

**1.** Search the Internet, read the manu-

corresponding forum (I always answer those

als, and browse any applicable

questions first). If you’d rather email me, you

documentation.

can do so through the contact page on the

**2.** Ask your question in the most appro-

Web site. I do try to answer every email I

priate forum (newsgroup, mailing list,

receive, but it will probably take a week or

and so on).

two (whereas you’ll likely get a reply in the

**3.** Use a clear and concise subject.

forum within a couple of days).

**4.** Describe your problem in detail, show

For more tips and an enlightening read,

any relevant code, say what went

see the sidebar and Eric Steven Raymond’s

wrong, indicate what version of PHP

“How to Ask Questions the Smart Way” at

you’re using, and state what operat-

[www.catb.org/~esr/faqs/smart-questions.](http://www.catb.org/~esr/faqs/smart-questions.html)

ing system you’re running.

[html. The 10 minutes you spend on it will](http://www.catb.org/~esr/faqs/smart-questions.html)

save you hours in the future. Those people

who will answer your questions, like myself,

will be most appreciative!

xx Introduction

[**1**](#index_split_000.html#p6)

[Getting Started](#index_split_000.html#p6)

[with PHP](#index_split_000.html#p6)

When learning any new programming

language, you should always begin with

**In This Chapter**

an understanding of the basic syntax and

functionality, which is what you’ll learn

Basic HTML Syntax

2

in this chapter. The focus here is on the

Basic PHP Syntax

7

fundamentals of both HTML and PHP, and

Using FTP

10

how the two languages work together. The

chapter also covers some recommended

Testing Your Script

12

programming and debugging techniques,

Sending Text to the Browser

15

the mastery of which will improve your

Using the PHP Manual

18

work in the long run.

Sending HTML to the Browser

22

If you’ve never programmed before, a

focused reading of this chapter will start

Adding Comments to Scripts

25

you on the right track. If you have some

Basic Debugging Steps

28

programming experience, you’ll be able

Review and Pursue

30

to breeze through these pages, gaining

a perspective for the book’s remaining

material in the meantime. By the end of this

chapter you will have successfully written

and executed your first PHP scripts and be

on your way to developing dynamic Web

applications.

![Image 64](index-23_1.png)

[**Basic HTML Syntax**](#index_split_000.html#p6)

All Web pages are made using HTML

(Hypertext Markup Language). Every Web

browser, be it Microsoft’s Internet Explorer,

**A**

Apple’s Safari, Mozilla’s Firefox, or Google’s

How one Web browser

renders the HTML code.

Chrome, turns HTML code—

**<h1>Hello, World!</h1>**

**I just wanted to say <em>Hello</em>.**

—into the stylized Web page seen by

the user **A**.

As of this writing, the most current version

of HTML is 4.01. The next major release,

HTML 5, is being actively developed and

discussed, but is not production ready

(again, as of this writing). This book uses

a slight variant of HTML called XHTML

(eXtensible HTML). XHTML is almost exactly

like HTML, with the following differences:

■

All tags are written in lowercase.

■

Nested tags must be well formed.

This rule isn’t as complicated as it

sounds. It means that you can’t write

**<div><p>text</div></p>** ; instead you use **<div><p>text</p></div>.**

■

All tag attributes must be quoted.

In HTML, you might write **<table**

**border=2>** , but in XHTML, you must

use **<table border="2">** .

■

All tags must be closed.

This rule is the most confusing for

most people. Many HTML tags have

both an open and a close, like **<div**

**class="someclass">text</div>** .

However, a few don’t have implicit

closing tags. These include **<hr>** , **<br>** ,

**<img>** , and **<input>** . To make these

valid XHTML tags, you need to close

2 Chapter

1

them by adding a space and a slash at

the end, like this:

**<hr />**

**<br />**

**<img src="image.png" />**

**<input type="text" name="age" />**

**Basic CSS**

The HTML and XHTML elements define a page’s content, but formatting the look and behavior of such content is best left to CSS (Cascading Style Sheets). As with HTML and XHTML, this book does not teach CSS in any detail, but as some of the book’s code will use CSS, you should be familiar with its basic syntax, too.

You can add CSS to a Web page in a couple of ways. The first, and recommended, method is to use HTML **style** tags:

**<style type="text/css">**

***rules***

**</style>**

Between the opening and closing tags, the CSS rules are defined. You can also use the **link** HTML tag to incorporate CSS rules defined in an external file:

**<link href="styles.css" rel="stylesheet" type="text/css" />** CSS rules are applied to combinations of general page elements, CSS classes, and specific items: **img { border: 0px; }**

**.error { color: red; }**

**#about { background-color: #ccc; }**

The first rule applies to every image tag. The second applies to any element that has a class of error:

**<p class="error">Error!</p>**

The third rule applies to just the specific element that has an ID value of about:

**<p id="about">About...</p>**

(Not all elements need to have an **id** attribute, but no two elements can have the same **id** value.) For the most part, this book will just use CSS to do simple things, such as changing the color or background color of an element or some text.

Even though using a separate CSS section or file is best, in order to keep things simple, this book will occasionally apply CSS inline:

**<p style="color: red;">Error!</p>**

For more on CSS, search the Web or see a dedicated book on the subject.

Getting Started with PHP 3

![Image 65](index-25_1.png)

Before getting into the syntax of PHP,

let’s create one simple but valid XHTML

document that will act as a template for

almost all of this book’s examples.

**To create an XHTML page:**

**1.** Open your text editor or Integrated

Development Environment (IDE).

You can use pretty much any

application to create HTML, XHTML,

and PHP pages. Popular choices

include Adobe’s [Dreamweaver (www.](http://www.adobe.com)

[adobe.com),](http://www.adobe.com) which runs on Windows and Mac OS X; [EditPlus (www.editplus.](http://www.editplus.com)

[com) and Crimson Editor (www](http://www.editplus.com)[.](http://www.crimsoneditor.com)

[crimsoneditor.com) for Windows; and](http://www.crimsoneditor.com)

**B** BBEdit and most other Web development

applications will create the basics of an XHTML

Bare Bones[’ BBEdit (www.barebones.](http://www.barebones.com)

document for you.

[com) or MacroMates](http://www.barebones.com)’ T[extMate (www.](http://www.macromates.com)

[macromates.com) for the Mac.](http://www.macromates.com)

**Script 1.1** This sample document shows the basics

of XHTML code.

**2.** Choose File > New to create a new,

blank document.

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

1.0

Transitional//EN"

Some text editors allow you to start by

2 "http://www.w3.org/TR/xhtml1/DTD/

creating a new document of a certain

xhtml1-transitional.dtd">

type—for example, a new XHTML file **B**.

3 <html

xmlns="http://www.w3.org/1999/

If your application has this option, use it.

xhtml" xml:lang="en" lang="en">

4 <head>

**3.** Start with the XHTML header lines

5

<meta http-equiv="content-type"

(**Script 1.1**):

content="text/html; charset=utf-8" />

6

<title>Welcome to this Page!</title>

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

7 </head>

➝ **XHTML 1.0 Transitional//EN"**

8 <body>

**"http://www.w3.org/TR/xhtml1/DTD/**

9

<h1>This is a basic XHTML page!</h1>

 ➝ **xhtml1-transitional.dtd">**

10 <br

/>

**<html xmlns="http://www.w3.org/**

11 <p>Even with <span style="font-size:

150%;">some</span> decoration, it's still

➝ **1999/xhtml" xml:lang="en"**

not very exciting.</p>

➝ **lang="en">**

12 </body>

13 </html>

A valid XHTML document begins with

these lines. They tell the Web browser

what type of document to expect. For this

template, and in the entire book, XHTML

1.0 Transitional pages will be created.

4 Chapter

1

This means adherence to XHTML 1.0

**Understanding Encoding**

standards. The Transitional part means

the page can use deprecated (no longer

Encoding is a huge subject, but what

recommended) tags (as opposed to Strict

you most need to understand is this:

mode, which isn’t forgiving).

the encoding you use in a file dictates

what characters can be represented

**4.** Create the head section of the page:

(and therefore, what languages can

**<head>**

be used). To select an encoding, you

must first confirm that your text editor

**<meta**

**http-equiv="content-type"**

or IDE can save documents using that

 ➝ **content="text/html;**

encoding. Some applications let you

 ➝ **charset=utf-8"/>**

set the encoding in the preferences or

**<title>Welcome to this Page!**

options area; others set the encoding

 ➝ **</title>**

when you save the file.

**</head>**

To indicate to the Web browser the

The head of an XHTML page includes

encoding being used, there’s the

the **content-type** **meta** tag, required

corresponding **meta** tag:

for valid XHTML. The “Understanding

**<meta http-equiv="content-type"**

Encoding” sidebar discusses what the

➝ **content="text/html;**

**charset** part of the tag means.

➝ **charset=utf-8" />**

The head also contains the page’s

The **charset=utf-8** part says that UTF-8

title, which will appear at the top of

(short for 8-bit Unicode Transformation

the browser window, as well as in the

Format) encoding is being used. Unicode

browser’s bookmarks and history. You

is a way of reliably representing every

can also place JavaScript and CSS

symbol in every alphabet. Version 6

references in the head.

of Unicode—the current version as of

this writing—supports over 99,000

**5.** Create the body section:

characters! The most commonly used

**<body>**

Unicode encoding is UTF-8.

**<h1>This is a basic XHTML page!**

If you want to create a multilingual Web

➝ **</h1>**

page, UTF-8 is the way to go and I’ll be

**<br />**

using it in this book’s examples. You

**<p>Even with <span style=**

don’t have to, of course. But whatever

➝ **"font-size: 150%;">some</span>**

encoding you do use, make sure that the

➝ **decoration, it's still not very**

encoding indicated by the XHTML page

➝ **exciting.</p>**

matches the actual encoding used by the

text editor or IDE. If you don’t, you’ll likely

**</body>**

see odd characters when you view the

continues on next page

page in a Web browser.

Getting Started with PHP 5

![Image 66](index-27_1.png)

The page’s content—what is seen in the

**9.** Save the file as **welcome.html**.

Web browser—goes between opening

Even though you’re coding with

and closing **body** tags. Per XHTML rules,

XHTML, the page will still use the

the break tag (**<br />** ) includes a space

standard **.html** extension.

before the slash that closes it. All the

**10.** Test the page by viewing it in your

other tags are similar to their standard

Web browser **C**.

HTML counterparts except that they’re

in lowercase. CSS is used to increase

Unlike with PHP scripts (as you’ll soon

the font size for the word some.

discover), you can test XHTML and

HTML pages by opening them directly

**6.** Type **</html>** to complete the

in a Web browser.

HTML page.

**7.** Choose File > Save As. In the dialog

box that appears, choose Text Only

**Use the book’s support forum**

[**(www.LarryUllman.com/forum/) or search**](http://www.LarryUllman.com/forum/)

(or ASCII) for the format, if you’re given

**the Web to find a good HTML and PHP**

the option.

**editor or IDE.**

XHTML and PHP documents are just

**The book uses XHTML, but that doesn’t**

plain text files (unlike, for example, a

**mean you have to. If you’re more comfortable**

Microsoft Word document, which is

**with HTML, stick with what you know. It won’t**

stored in a proprietary format). You may

**affect the operability of your PHP scripts.**

also need to indicate the encoding

**For more information on XHTML and**

when you save the file (again, see

**HTML, check out Elizabeth Castro’s excellent**

the sidebar).

**book, HTML, XHTML, and CSS, Sixth Edition:**

**Visual QuickStart Guide**

**8.** Navigate to the location where you wish

**(Peachpit Press, 2006).**

to save the script.

**I’ll use the terms HTML and XHTML**

You can place this script anywhere you’d

**interchangeably throughout the book. In fact,**

**you’ll probably see just HTML the majority of**

like on your computer, although using

**the time, but understand that I mean XHTML**

one dedicated folder for every script in

**as well.**

this book, perhaps with subfolders for

each chapter, makes sense.

**C** The XHTML page, as interpreted by the

Web browser.

6 Chapter

1

[**Basic PHP Syntax**](#index_split_000.html#p6)

Now that you’ve seen how HTML will be

handled in this book, it’s time to begin PHP

scripting. To create your first PHP page,

you’ll start exactly as you would if you

were creating an HTML document from

scratch. Understanding the reason for this

is vitally important: Web browsers are client

applications that understand HTML; PHP

is a server-side technology, which cannot

be run in the client. To bridge this gap,

PHP will be used on the server to generate

HTML that’s run in a Web browser (refer

to the book’s Introduction for a visual

representation of this relationship).

There are three main differences between

a standard HTML document and a PHP

document. First, PHP scripts should be

saved with the **.php** file extension (for

example, **index.php**). Second, you place

PHP code within **<?php** and **?>** tags,

normally within the context of some HTML:

**…**

**<body><h1>This is HTML.</h1>**

**<?php *PHP code*! ?>**

**<p>More HTML</p>**

**…**

The PHP tags indicate the parts of the

page to be run through the PHP processor

on the server. This leads to the third major

difference: PHP scripts must be run on a

PHP-enabled Web server (whereas HTML

pages can be viewed on any computer,

directly in a browser). This means that PHP

scripts must always be run through a URL

(i.e[., http://something/page.php). If you’re](http://something/page.php)

viewing a PHP script in a Web browser and

the address does not begin with http, the

PHP script will not work.

continues on next page

Getting Started with PHP 7

To make this first PHP script do something

**Script 1.2** This first PHP script takes a typical HTML

without too much programming fuss, you’ll

page, adds the PHP tags, and invokes a PHP function.

use the **phpinfo()** function. This function,

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

when called, sends a table of information

1.0

Transitional//EN"

to the Web browser. That table lists the

2 "http://www.w3.org/TR/xhtml1/DTD/

xhtml1-transitional.dtd">

specifics of the PHP installation on that

3 <html

xmlns="http://www.w3.org/1999/

particular server. It’s a great way to test

xhtml" xml:lang="en" lang="en">

your PHP installation, and it has a high

4 <head>

“bang for your buck” quality.

5

<meta http-equiv="content-type"

content="text/html; charset=utf-8" />

6

<title>First PHP Script</title>

**To create a new PHP script**

7 </head>

**on your computer:**

8 <body>

**9 <?php**

**1.** Create a new HTML document in

**10 phpinfo();**

your text editor or IDE, to be named

**11 ?>**

**phpinfo.php** (**Script 1.2**):

12 </body>

13 </html>

**<!DOCTYPE html PUBLIC "-//W3C//**

➝ **DTD XHTML 1.0 Transitional//EN"**

➝ **"http://www.w3.org/TR/xhtml1/DTD/**

➝ **xhtml1-transitional.dtd">**

**<html xmlns="http://www.w3.org/**

➝ **1999/xhtml" xml:lang="en"**

➝ **lang="en">**

**<head>**

**<meta**

**http-equiv="content-type"**

 ➝ **content="text/html;**

 ➝ **charset=utf-8" />**

**<title>First PHP Script</title>**

**</head>**

**<body>**

**</body>**

**</html>**

This particular HTML is largely irrelevant

to the overall point of creating a PHP

page—but, for consistency’s sake, this

is the same template as in the basic

XHTML example (Script 1.1).

8 Chapter

1

**2.** Create some blank lines between the

**Just as a file’s extension on your**

opening and closing **body** tags by

**computer tells the operating system in what**

pressing Return (Mac) or Enter (PC).

**application to open the file, a Web page’s**

**extension tells the server how to process**

**3.** Type **<?php** on its own line, just after the

**the file: *file*.php goes through the PHP**

opening **body** tag.

**module, *file*.aspx is processed as ASP.NET,**

**and *file*.html is a static HTML document**

This initial PHP tag tells the server that

**(normally). The extension associations are**

the following code is PHP and should

**determined by the Web server’s settings.**

be handled as such.

**If you’re developing PHP scripts for a**

**4.** Add the following on the next line:

**hosted Web site, check with your hosting com-**

**phpinfo();**

**pany to learn which file extensions you can**

**use for PHP documents. In this book you’ll see**

The syntax will be explained in detail

**.php, the most common extension.**

later, but in short, this is just a call to an

**You’ll occasionally see PHP’s short tags—**

existing PHP function named phpinfo.

**simply <? and ?>—used in other people’s**

You must use the opening and closing

**scripts, although it’s best to stick with the**

parentheses, with nothing between

**formal tags. In fact, support for the short tags**

them, and the semicolon.

**is being dropped from the language.**

**5.** Type **?>** on its own line, just before the

**You’ll find it handy to have a copy of the**

closing body tag.

**phpinfo.php file around. As you’ll soon see,**

**this script will report upon PHP’s capabilities,**

The closing PHP tag tells the server

**settings, and other features of your server.**

that the PHP section of the script is

**In fact, this book will frequently suggest you**

over. Any text outside of the PHP tags

**return to this script for those purposes.**

is immediately sent to the Web browser

**PHP scripts can also be executed with-**

as HTML and isn’t treated as PHP code.

**out a Web browser, using a command-line**

**6.** Save the script as **phpinfo.php**.

**interface and a stand-alone PHP executable.**

**But that topic is well outside the scope of this**

Not to overstate the point, but

**book (and it’s a much less common use of PHP**

remember that PHP scripts must use

**regardless).**

a valid file extension. Most likely you’ll

have no problems if you save your files

as ***filename*****.php**.

You also need to be certain that the

application or operating system is not

adding a hidden extension to the file.

Notepad on Windows, for example, will

attempt to add **.txt** to uncommon file

extensions, which will render the PHP

script unusable.

Getting Started with PHP 9

![Image 67](index-31_1.jpg)

![Image 68](index-31_2.jpg)

[**Using FTP**](#index_split_000.html#p6)

PHP scripts to the PHP-enabled server

using FTP (File Transfer Protocol).

Unlike HTML, which can be tested directly

The Web hosting company or server’s

in a Web browser, PHP scripts need to be

administrator will provide you with FTP

run from a PHP-enabled server in order for

access information, which you’ll enter

you to see the results. Specifically, PHP

into an FTP client. There are many FTP

is run through a Web server application,

client applications available; in this next

[like Apache (http://httpd.apache.org),](http://httpd.apache.org)

sequence of steps, I’ll use the free FileZilla

[Abyss (www.aprelium.com), or Internet](http://www.aprelium.com)

[(http://filezilla-project.org/), which runs on](http://filezilla-project.org/)

[Information Server (IIS, www.iis.net).](http://www.iis.net)

many operating systems.

There are two ways you can obtain a PHP-

enabled server:

**To FTP your script to the server:**

**1.** Install the software on your computer.

**1.** Open your FTP application.

**2.** Acquire Web hosting.

**2.** In the application’s connection window,

enter the information provided by your

PHP is open source software (meaning, in

Web host **A**.

part, that it’s free) and is generally easy

to install (with no adverse effect on your

FTP access requires a hostname (e.g.,

computer as a whole). If you want to install

the domain name or an IP address),

PHP and a Web server on your computer,

username, and password.

follow the directions in Appendix A,

**3.** Click Quickconnect (or your FTP

“Installation and Configuration.” Once

client’s equivalent).

you’ve done so, you can skip ahead to the

If you’ve provided the correct

next section of the chapter, where you’ll

information, you should be able to

learn how to test your first PHP script.

connect. If not, you’ll see error messages

If you’re not running PHP on your own

at the top of the FileZilla window **B**.

computer, you’ll need to transfer your

**A** The connection section of FileZilla’s main window (as it appears on the Mac).

**B** The reported error says that the login information is incorrect.

10 Chapter

1

![Image 69](index-32_1.png)

**4.** Navigate to the proper directory for

your Web pages (for example, **www**,

**htdocs**, or **httpdocs**).

The FTP application won’t necessarily

drop you off in the appropriate directory.

You may need to do some navigation

to get to the Web document root. The

Web document root is the directory

on the server to which a URL directly

points ( for example, www.larryullman.

com). If you’re unsure of what the Web

document root is for your setup, see the

documentation provided by the hosting

company (or ask them for support).

In FileZilla, the right-hand column

represents the files and directories

on the server; the left-hand column

represents the files and directories on

your computer **C**. Just double-click on

folders to enter them.

**5.** Upload your script—**phpinfo.php**—to

the server.

To do this in FileZilla, you just need to

drag the file from the left column—your

computer—to the right column—the server.

**Some text editors and IDEs have**

**built-in FTP capability, allowing you to save**

**your scripts directly to the server. Some, like**

**Dreamweaver and TextMate, can run PHP**

**scripts without leaving the application at all.**

**C** I’ve successfully connected to the remote server and navigated into the **httpdocs** directory (aka the Web document root).

Getting Started with PHP 11

[**Testing Your Script**](#index_split_000.html#p6)

**To test your script in the browser:**

**1.** Open your favorite Web browser.

Testing a PHP script is a two-step process.

First you must put the PHP script in the

For the most part, PHP doesn’t behave

appropriate directory for the Web server.

differently on different browsers

Second, you run the PHP script in your

(because PHP runs on the server), so

Web browser by loading the correct URL.

use whichever browser you prefer. In

this book, you’ll see that I primarily use

If you’re using a separate Web server,

Firefox and Safari, regardless of the

like one provided by a hosting company,

operating system.

you just need to use an FTP application

to upload your PHP script to it (as in the

**2.** In the browser’s address bar, enter the

previous steps). If you have installed PHP

URL of the site where your script has

on your personal computer, then you can

been saved.

test your PHP scripts by saving them in, or

In my case[, I enter www.larryullman.com,](http://www.larryullman.com)

moving them to, the Web document root.

but your URL will certainly be different.

This is normally

If you’re running PHP on your own

■

**~/Sites** for Mac OS X users (where

computer, the URL is http://localhost

**~** stands for your home directory)

(Windows); or http: //localhost / ~username

■

***AbyssDir*****/htdocs** on any operating

(Mac OS X), where you should replace

username

system, where ***AbyssDir*** is the directory

with your username. Some

in which the Abyss Web Server was

all-in-one packages, such as MAMP and

installed

XAMPP, may also use a port as part of

the URL: http://localhost:8888.

■

**C:\\Inetpub\\wwwroot** for Windows users

running IIS

If you’re not sure what URL to use, see

the documentation for the Web server

■

**C:\\xampp\\htdocs** for Windows users

application you installed.

[running XAMPP (www.apachefriends.com)](http://www.apachefriends.com)

■

**/Applications/MAMP/htdocs** for Mac

[users running MAMP (www.mamp.info)](http://www.mamp.info)

If you’re not sure what the Web

document root for your setup is, see

the documentation for the Web server

application or operating system (if the

Web server application is built-in).

Once you’ve got the PHP script in the right

place, use your browser to execute it.

12 Chapter

1

![Image 70](index-34_1.png)

**3.** Add **/phpinfo.php** to the URL.

If you placed the script within a sub-

directory of the Web document root, you

would add that subdirectory name to the

URL as well (e.g., **/ch01/phpinfo.php**).

**4.** Press Return/Enter to load the URL.

The page should load in your browser

window **A**.

continues on next page

**A** If the script has been executed correctly, the browser result should look like this (woohoo!).

Getting Started with PHP 13

![Image 71](index-35_1.png)

![Image 72](index-35_2.png)

If you see the PHP code **B** or a blank

page, it could mean many things:

\> You are not loading the PHP script

through a URL (i.e., the address does

**B** If you see the raw PHP code,

not begin with http).

then the PHP code is not being

\> PHP has not been enabled on the

executed.

server.

\> You are not using the proper extension.

If you see a file not found or similar

error **C**, it could be because

\> You entered the incorrect URL.

\> The PHP script is not in the proper

directory.

\> The PHP script does not have the

correct name or extension.

**C** This server response indicates a mismatch

between the URL attempted and the files that

**It’s very important to remember that**

actually exist on the server.

**you can’t open a PHP file directly in a Web**

**browser as you would open HTML pages or**

**files in other applications. PHP scripts must**

**be processed by the Web server, which means**

**you must access them via a URL (an address**

**that starts with http: // ).**

**Even if you aren’t a seasoned computer**

**professional, you should consider installing**

**PHP on your computer. Doing so isn’t too dif-**

**ficult, and PHP is free. Again, see Appendix A**

**for instructions.**

**Technically speaking, you don’t need to**

**add any HTML to a phpinfo() script. If you**

**don’t, the phpinfo() function will still gener-**

**ate a complete HTML page.**

14 Chapter

1

[**Sending Text to**](#index_split_000.html#p6) 

[**the Browser**](#index_split_000.html#p6)

PHP wouldn’t be very useful if all you

could do was see that it works (although

that confirmation is critical). You’ll use PHP

most frequently to send information to the

browser in the form of plain text and HTML

tags. To do so, use **print**:

**print "something";**

Just type the word **print**, followed by what

you want to display: a simple message, the

value of a variable, the result of a calculation,

and so forth. In the previous example,

the message is a string of text, so it must

be surrounded with quotation marks (in

comparison, numbers are not quoted).

To be clear, **print** doesn’t actually print

anything; it just outputs data. When a PHP

script is run through a Web browser, that

PHP output is received by the browser itself.

Also notice that the line is terminated with

a semicolon (**;** ). Every statement in PHP

code must end with a semicolon, and

forgetting this requirement is a common

cause of errors. A statement in PHP is an

executable line of code, like

**print "something";**

or

**phpinfo();**

Conversely, comments, PHP tags, control

structures (conditionals, loops, and so on),

and certain other constructs discussed in

this book don’t require semicolons.

Finally, you should know about a minor

technicality: whereas **phpinfo()** is a function,

**print** is actually a language construct.

Although it’s still standard to refer to **print**

as a function, because **print** is a language

construct, no parentheses are required when

using it, as in the **phpinfo()** example.

Getting Started with PHP 15

**To print a simple message:**

**Script 1.3** By putting the **print** statement between

the PHP tags, the server will dynamically send the

**1.** Begin a new HTML document in

Hello, world! greeting to the browser.

your text editor or IDE, to be named

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

**hello.php** (**Script 1.3**):

1.0

Transitional//EN"

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

2 "http://www.w3.org/TR/xhtml1/DTD/

➝ **XHTML 1.0 Transitional//EN"**

xhtml1-transitional.dtd">

3 <html

xmlns="http://www.w3.org/1999/xhtml"

➝ **"http://www.w3.org/TR/xhtml1/DTD/**

xml:lang="en"

lang="en">

➝ **xhtml1-transitional.dtd">**

4 <head>

**<html xmlns="http://www.w3.org/**

5

<meta http-equiv="content-type"

➝ **1999/xhtml" xml:lang="en"**

content="text/html; charset=utf-8" />

➝ **lang="en">**

6 <title>Hello,

World!</title>

7 </head>

**<head>**

8 <body>

**<meta**

**http-equiv="content-type"**

9

<p>The following was created by PHP:

 ➝ **content="text/html;**

10 <?php

 ➝ **charset=utf-8" />**

**11 print "Hello, world!";**

**<title>Hello,**

**World!</title>**

12 ?>

13 </p>

**</head>**

14 </body>

**<body>**

15 </html>

**<p>The following was created**

➝ **by PHP:**

Most of this code is the standard HTML.

The last line will be used to distinguish

between the hard-coded HTML and the

PHP-generated HTML.

**2.** On the next line, type **<?php** to create

the initial PHP tag.

**3.** Add

**print "Hello, world!";**

Printing the phrase Hello, world! is the

first step most programming references

teach. Even though it’s a trivial reason to

use PHP, you’re not really a programmer

until you’ve made at least one Hello,

world! application.

16 Chapter

1

![Image 73](index-38_1.png)

**4.** Close the PHP section and complete

the HTML page:

**?>**

**</p>**

**A** A simple ***Hello,*** ***world!*** example: your first foray into PHP programming.

**</body>**

**</html>**

**5.** Save the file as **hello.php**, place it on

your PHP-enabled server, and test it in

your browser **A**.

If you’re running PHP on your own

computer, remember that you can save

the file to the proper directory and

access the script via http://localhost /.

If you see an error or a blank page

instead of the results shown in the

figure, see the debugging section at

the end of this chapter.

**PHP is case-insensitive when it comes to**

**calling functions like phpinfo() and print:**

**print, Print, and PRINT net the same**

**results. Later in the book you’ll see examples**

**where case makes a crucial difference.**

**You can use other functions to send text**

**to the browser, including echo and printf(),**

**but this book primarily uses print.**

**You can—and commonly will—use print**

**over multiple lines:**

**print "This is a longer**

**sentence of text.";**

**The closing quotation mark terminates the**

**message being printed and the semicolon is**

**placed only at the end of that line.**

Getting Started with PHP 17

![Image 74](index-39_1.png)

[**Using the PHP Manual**](#index_split_000.html#p6)

The PHP manual—accessible online at

[www.php.net /manual—lists every function](http://www.php.net/manual)

and feature of the language. The manual

is organized with general concepts

(installation, syntax, variables) discussed

first and ends with the functions by topic

(MySQL, string functions, and so on).

To quickly look up any function in the PHP

[manual, go to www.php.net /functionname](http://www.php.net/functionname)

in your Web browser (for example, www.

php.net /print).

To understand how functions are

described, look at the start of the **print**

function’s page **A**.

The first line is the name of the function

itself, followed by the versions of PHP in

which it’s available. As the language grows,

new functions are added and, occasionally,

older functions are removed. Then there’s

a textual description of the function along

with the function’s basic usage. The usage

is the most important and confusing part.

In this example, the first value, **int**, says

that **print** returns an integer value

(specifically, **print** returns 1, always).

**A** The PHP manual’s page for the **print** construct.

18 Chapter

1

![Image 75](index-40_1.png)

Within the parentheses, **string $arg**

states that the function takes one required

argument, which should be in the form of a

string. You’ve already seen this in action.

As a comparison, check out the manual’s

listing for the **nl2br()** function **B**. This

function converts newlines found within

text (the equivalent of pressing Return/

Enter) into HTML break tags. This function,

which returns a string, takes a string as its

first argument and an optional Boolean

(**true**/**false**) as its second. Whenever you

see the square brackets, that indicates

optional arguments, which are always

listed last. When a function takes multiple

arguments, they are separated by commas.

Hence, this function can be called like so:

**nl2br("Some text");**

**nl2br("Some text", false);**

As the definition also indicates, the second

argument has a default value of **true**,

meaning it’ll create XHTML **<br />** tags

unless the function is passed a second

argument value of **false**. In that case, the

function will create HTML **<br>** tags instead.

If you’re ever confused by a function or

how it is properly used, check the PHP

manual’s reference page for it.

**B** The PHP manual’s page for the **nl2br()** function.

Getting Started with PHP 19

![Image 76](index-41_1.png)

**To look up a function definition:**

**1.** [Head to www.php.net /functionname in](http://www.php.net/functionname)

your Web browser.

If the PHP manual doesn’t have a

matching record for the function you

tried, check the spelling or look at the

recommended alternatives that the

manual presents **C**.

**2.** Compare the versions of PHP that the

function exists in with the version of

PHP you’re using.

Use the **phpinfo()** function, already

demonstrated, to know for certain

what version of PHP you are running.

If a function was added in a later

version of PHP, you’ll either need to

upgrade the version you have or use

a different approach.

**3.** Examine what type of data the

function returns.

Sometimes you may be having a

problem with a function because it

returns a different type of value than

you expect it to.

**C** The manual will present alternative functions if the entered URL doesn’t directly match a reference.

20 Chapter

1

![Image 77](index-42_1.png)

**4.** Examine how many and what types

of arguments the function requires or

can take.

The most common mistake when using

functions is sending the wrong number

or type of arguments when the function

is called.

**5.** Read the user comments, when pres-

ent, to learn more.

Sometimes the user comments can be

quite helpful (other times not).

**If you see a message saying that a**

**function has been deprecated D, that means**

**the function will be dropped from future**

**versions of PHP and you should start using the**

**newer, better alternative (there almost always**

**is one, and it will be identified).**

**D** Deprecated functions should be avoided in your code.

Getting Started with PHP 21

![Image 78](index-43_1.png)

[**Sending HTML to**](#index_split_000.html#p6)

[**the Browser**](#index_split_000.html#p6)

**A** Attempting to print double quotation marks

As those who first learned HTML quickly

will create errors, as they conflict with the **print**

statement’s primary double quotation marks.

discovered, viewing plain text in a Web

browser leaves a lot to be desired. Indeed,

**Script 1.4** With the **print** function, you can send

HTML was created to make plain text more

HTML tags along with text to the browser, where

appealing and useful. Because HTML

the formatting will be applied.

works by adding tags to text, you can

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

use PHP to also send HTML tags to the

1.0

Transitional//EN"

browser, along with other data:

2 "http://www.w3.org/TR/xhtml1/DTD/

xhtml1-transitional.dtd">

**print "<b>Hello, world!</b>";**

3 <html

xmlns="http://www.w3.org/1999/xhtml"

There is one situation where you have

xml:lang="en"

lang="en">

to be careful, though. HTML tags that

4 <head>

5

<meta http-equiv="content-type"

require double quotation marks, like

content="text/html; charset=utf-8" />

**<a href="page.php">link</a>,** will cause 6 <title>Hello,

World!</title>

problems when printed by PHP, because

7 </head>

the **print** function uses quotation marks

8 <body>

as well **A**:

9

<p>The following was created by PHP:

10 <?php

**print "<a href="page.php">link</a>";** **11 print "<span style=\\"font-weight:**

**bold;\\">Hello,**

**world!</span>";**

One workaround is to escape the

12 ?>

quotation marks within the HTML by

13 </p>

preceding them with a backslash (**\\**):

14 </body>

15 </html>

**print "<a href=\\"page.php\\">link</a>";** By escaping each quotation mark within the

**print** statement, you tell PHP to print the

mark itself instead of treating the quotation

mark as either the beginning or end of the

string to be printed.

**To send HTML to the browser:**

**1.** Open the hello.php script (Script 1.3)

in your text editor or IDE, if it is not

already open.

**2.** Edit the Hello, world! text on line 11

by adding HTML tags, making it read

(**Script 1.4**) as follows:

**print "<span style=\\"font-weight:**

➝ **bold;\\">Hello, world!</span>";**

22 Chapter

1

![Image 79](index-44_1.png)

To make the PHP-generated part of

the message stand out, CSS styling

will embolden the greeting. For this to

work, you must escape the quotation

**B** The new version of the Hello, world! page, with

marks within the

a little more decoration and appeal.

**span** tag so that they

don’t conflict with the **print** statement’s

quotation mark.

**3.** Save the script as **hello2.php**, place it

on your PHP-enabled server, and run

the page in your browser **B**.

continues on next page

**Using White Space**

When you’re programming in PHP, you should understand that white space is generally (but not universally) ignored. Any blank line ( just one or several in a row) in PHP code is irrelevant to the end result. Likewise, tabs and spaces are normally inconsequential to PHP. And as PHP code is not visible in the Web browser (unless there’s a problem with the server), white space in your PHP files has no impact on what the end user sees.

The spacing of HTML code shows up in the HTML source of a Web page but has only a minimal effect on what’s viewed in the Web browser. For example, all of a Web page’s HTML source code could be placed on one line without changing what the end user sees. If you had to hunt for a problem in the HTML source, however, you would not like the long, single line of HTML. You can affect the spacing of dynamically generated HTML code by printing it in PHP over multiple lines, or by using the newline character (**\\n**) within double quotation marks: **print "Line 1\\nLine 2";**

Again, use of the newline character affects the HTML source code of the Web page, not what the end user will see rendered in the browser.

To adjust the spacing in the rendered Web page, you’ll use CSS, plus paragraph, div, and break tags, among others.

Getting Started with PHP 23

![Image 80](index-45_1.png)

**4.** View the HTML page source to see the

code that was sent to the browser **C**.

How you do this depends upon the

browser: select View > Page Source

in Firefox, View > Source in Internet

Explorer, or View > View Source in Safari.

This is a step you’ll want to be in the

habit of taking, particularly when

problems occur. Remember that PHP is

primarily used to generate HTML, sent

to and interpreted by the Web browser.

Often, confirming what was sent to the

Web browser (by viewing the source)

will help explain the problem you’re

seeing in the browser’s interpretation

(or visible result).

**Understanding the role of quotation**

**marks and how to escape problematic charac-**

**ters is crucial to programming with PHP. These**

**topics will be covered in more detail in the**

**next two chapters.**

**The HTML you send to the Web browser**

**from PHP doesn’t need to be this simple.**

**You can create tables, JavaScript, and much,**

**much more.**

**Remember that any HTML outside of the**

**PHP tags will automatically go to the browser.**

**Within the PHP tags, print statements are**

**used to send HTML to the Web browser.**

**C** The resulting HTML source code of **hello2.php** **B** on page 22.

24 Chapter

1

[**Adding Comments**](#index_split_000.html#p6) 

[**to Scripts**](#index_split_000.html#p6)

Comments are integral to programming,

not because they do anything but because

they help you remember why you did

something. The computer ignores these

comments when it processes the script.

Furthermore, PHP comments are never

sent to the Web browser and therefore

remain your secret.

PHP supports three ways of adding

comments. You can comment out one line

of code by putting either **//** or **#** at the

beginning of the line you want ignored:

**// This is a comment.**

You can also use **//** or **#** to begin a

comment at the end of a PHP line, like so:

**print "Hello"; // Just a greeting.**

Although it’s largely a stylistic issue, **//** is

much more commonly used in PHP than **#**.

You can comment out multiple lines by

using **/\*** to begin the comment and **\*/** to

conclude it:

**/\* This is a**

**multi-line comment. \*/**

Some programmers also prefer this

comment style as it contains both open

and closing “tags,” providing demarcation

for where the comment begins and ends.

Getting Started with PHP 25

![Image 81](index-47_1.png)

**To add comments to a script:**

**Script 1.5** PHP and HTML comments are added

to the script to document it and to render a line of

**1.** Open the hello2.php (Script 1.4) in your

PHP code inert.

text editor or IDE.

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

**2.** After the initial PHP tag, add some com-

1.0

Transitional//EN"

ments to your script (**Script 1.5**):

2 "http://www.w3.org/TR/xhtml1/DTD/

xhtml1-transitional.dtd">

**/\***

3 <html

xmlns="http://www.w3.org/1999/xhtml"

**\* Filename: hello3.php**

xml:lang="en"

lang="en">

**\* Book reference: Script 1.5**

4 <head>

**\* Created by: Larry Ullman**

5

<meta http-equiv="content-type"

content="text/html; charset=utf-8" />

**\*/**

6 <title>Hello,

World!</title>

This is just a sample of the kind of

7 </head>

comments you can write. You should

8 <body>

9

<p>The following was created by PHP: <br />

document what the script does, what

10 <?php

information it relies on, who created it,

**11 /\***

when, and so forth. Stylistically, such

**12 \* Filename: hello3.php**

comments are often placed at the top of

**13 \* Book reference: Script 1.5**

a script (as the first thing within the PHP

**14 \* Created by: Larry Ullman**

**15**

**\*/**

section, that is), using formatting like this.

16

The extra asterisks aren’t required; they

**17 //print "<span style=\\"font-weight:**

just draw attention to the comments.

**bold;\\">Hello,**

**world!</span>\\n";**

18

**3.** On line 17, in front of the **print**

19 ?>

statement, type **//**.

**20 <!-- This is an HTML comment. -->**

By preceding the **print** statement

21 </p>

22 </body>

with two slashes, the function call is

23 </html>

“commented out,” meaning it will never

be executed.

**4.** After the closing PHP tag (on line 19),

add an HTML comment:

**<!-- This is an HTML comment. -->**

This line of code will help you

**A** With the **print** statement commented out, the

distinguish among the different

page looks just as it would if the **print** function

weren’t there.

comment types and where they appear.

This comment will only appear within

the HTML source code.

**5.** Save the script as **hello3.php**, place it

on your PHP-enabled server, and run

the page in your Web browser **A**.

26 Chapter

1

![Image 82](index-48_1.png)

**6.** View the source of the page to see the

HTML comment **B**.

**You can comment out just one line of**

**code or several using the /\* and \*/ method.**

**With // or #, you can negate only one line at**

**a time.**

**Different programmers prefer to com-**

**ment code in different ways. The important**

**thing is to find a system that works for you**

**and stick to it.**

**Note that you cannot use HTML comment**

**characters (<!-- and -->) within PHP to com-**

**ment out code. You could have PHP print those**

**tags to the browser, but in that case you’d**

**create a comment that appeared in the HTML**

**source code on the client’s computer (but not**

**in the browser window). PHP comments never**

**make it as far as a user’s computer.**

**Despite my strong belief that you can’t**

**over-comment your scripts, the scripts in this**

**book aren’t as documented as they should**

**be, in order to save space. But the book will**

**document each script’s name and number, for**

**cross-reference purposes.**

**When you change a script’s code, be cer-**

**tain to update its comments as well. It’s quite**

**confusing to see a comment that suggests a**

**script or a line of code does something other**

**than what it actually does.**

**B** HTML comments don’t appear in the Web browser but are in the HTML source.

PHP comments remain in the PHP script on the server.

Getting Started with PHP 27

[**Basic Debugging Steps**](#index_split_000.html#p6)

Debugging is by no means a simple

concept to grasp, and unfortunately, it’s

one that is only truly mastered by doing.

The next 50 pages could be dedicated to

the subject and you’d still only be able to

pick up a fraction of the debugging skills

that you’ll eventually acquire and need.

The reason I introduce debugging in

this somewhat harrowing way is that it’s

important not to enter into programming with

delusions. Sometimes code won’t work as

expected, you’ll inevitably create careless

errors, and some days you’ll want to pull your

hair out, even when using a comparatively

user-friendly language such as PHP. In short,

prepare to be perplexed and frustrated

at times. I’ve been coding in PHP since

1999, and occasionally I still get stuck in

the programming muck. But debugging is

a very important skill to have, and one that

you will eventually pick up out of necessity

and experience. As you begin your PHP

programming adventure, I can offer the

following basic but concrete debugging tips.

**To debug a PHP script:**

■

**Make sure you’re always running PHP**

**scripts through a URL!**

This is perhaps the most common

beginner’s mistake. PHP code must be

run through the Web server application,

which means it must be requested

through **http:// *something***. When you

see actual PHP code instead of the result

of that code’s execution, most likely you’re

not running the PHP script through a URL.

■

**Know what version of PHP you’re**

**running.**

Some problems will arise from the

version of PHP in use. Before you ever

use any PHP-enabled server, run the

**phpinfo.php** file (Script 1.2) to confirm

the version of PHP in use.

28 Chapter

1

■

**Make sure display\_errors is on.**

■

**Take a break!**

This is a basic PHP configuration

So many of the programming problems

setting (discussed in Appendix A). You

I’ve encountered over the years, and the

can confirm this setting by executing

vast majority of the toughest ones, have

the **phpinfo()** function ( just use your

been solved by stepping away from my

browser to search for **display\_errors**

computer for a while. It’s easy to get

in the resulting page). For security

frustrated and confused, and in such

reasons, PHP may not be set to display

situations, any further steps you take are

the errors that occur. If that’s the case,

likely to only make matters worse.

you’ll end up seeing blank pages

when problems occur. To debug most

**These are just some general debug-**

problems, you’ll need to see the errors,

**ging techniques, specifically tailored to the**

so turn this setting on while you’re

**beginning PHP programmer. They should**

**suffice for now, though, as the examples in**

learning. You’ll find instructions for

**this book are relatively simple. More complex**

doing so in Appendix A and Chapter 3,

**coding requires more advanced debugging**

“HTML Forms and PHP.”

**techniques, so my PHP 6 and MySQL 5 for**

**Dynamic Web Sites: Visual QuickPro Guide**

■

**Check the HTML source code.**

**(Peachpit Press, 2007) dedicates a whole**

Sometimes the problem is hidden in

**chapter to this subject.**

the HTML source of the page. In fact,

sometimes the PHP error message can

be hidden there!

■

**Trust the error message.**

Another very common beginner’s

mistake is to not fully read or trust the

error that PHP reports. Although an error

message can often be cryptic and may

seem meaningless, it can’t be ignored.

At the very least, PHP is normally correct

as to the line on which the problem can

be found. And if you need to relay that

error message to someone else (like

when you’re asking me for help), do

include the entire error message!

Getting Started with PHP 29

[**Review and Pursue**](#index_split_000.html#p6)

**Pursue**

■

If you have access to more than one

New in this edition of the book, each

server, confirm what version of PHP is

chapter ends with a “Review and Pursue”

running on another server.

section. In these sections you’ll find

■

Create a static HTML page that displays

questions regarding the material just

some information. Then replace some

covered and prompts for ways to expand

of the static content with content

your knowledge and experience on your

created by PHP.

own. If you have any problems with these

sections, either in answering the questions

■

Create a template to use for your own

or pursuing your own endeavors, turn

work. The template should contain the

to the book’[s supporting forum (www.](http://www.LarryUllman.com/forum/)

HTML shell, the opening and closing

[LarryUllman.com/forum/).](http://www.LarryUllman.com/forum/)

PHP tags, and some basic comments.

■

Confirm, using the **phpinfo()** function,

**Review**

that **display\_errors** is enabled on

■

What is HTML? What is XHTML? Name

your server. If it’s not, change your

two differences between HTML and

server’s configuration to enable it (see

XHTML.

Chapter 3 and Appendix A).

■

What encoding is your text editor or

■

In subsequent chapters, occasionally

IDE set to use? Does that match the

check the PHP manual’s page when a

encoding specified in your generated

new function is mentioned in the book.

HTML pages?

■

What is CSS and what is it used for?

■

What file extension should PHP scripts

have for your particular server?

■

What is meant by “Web root directory”?

What is the Web root directory for your

server?

■

How do you test PHP scripts? What

happens when PHP scripts are not run

through a URL?

■

Name two ways comments can be

added to PHP code. Identify some ways

you would use comments.

30 Chapter

1

[**2**](#index_split_000.html#p6)

[Variables](#index_split_000.html#p6)

In the previous chapter, you learned how to

use PHP to send simple text and HTML to

**In This Chapter**

a Web browser—in other words, something

for which you don’t need PHP at all! Don’t

What Are Variables?

32

worry, though; this book will teach you how

Variable Syntax

36

to use **print** in conjunction with other PHP

Types of Variables

38

features to do great and useful things with

your Web site.

Variable Values

41

To make the leap from creating simple,

Understanding Quotation Marks

45

static pages to dynamic Web applications

Review and Pursue

48

and interactive Web sites, you need vari-

ables. Understanding what variables are,

the types that a language supports, and

how to use them is critical.

This chapter discusses the fundamentals

of variables used in PHP, and later chapters

cover the different types in greater detail.

If you’ve never dealt with variables before,

this chapter will be a good introduction. If

you’re familiar with the concept, then you

should be able to work through this chap-

ter with ease.

[**What Are Variables?**](#index_split_000.html#p6)

A variable is a container for data. Once

data has been stored in a variable (or,

stated more accurately, once a variable has

been assigned a value), that data can be

altered, printed to the Web browser, saved

to a database, emailed, and so forth.

Variables in PHP are, by their nature,

flexible: You can put data into a variable,

retrieve that data from it (without affecting

the value of the variable), put new data

in, and continue this cycle as long as

necessary. But variables in PHP are largely

temporary: Most only exist—that is, they

only have a value—for the duration of the

script’s execution on the server. Once

the execution passes the final closing

PHP tag, those variables cease to exist.

Furthermore, after users click a link or

submit a form, they are taken to a new

page that may have an entirely separate

set of variables.

Before getting too deep into the discussion

of variables, let’s write a quick script

that reveals some of PHP’s predefined

variables. These are variables that PHP

automatically creates when a script runs.

Over the course of the book you’ll be

introduced to many different predefined

variables. For this particular example, let’s

look at the predefined **$\_SERVER** variable.

It contains lots of information about the

computer on which PHP is running.

The **print\_r()** function offers an easy way

to display any variable’s value:

**print\_r($variable\_name);**

Just provide the name of the variable you’d

like to inspect as a single argument to the

**print\_r()** function (you’ll learn more about

a variable’s syntax throughout this chapter).

32 Chapter

2

**Script 2.1** The **print\_r()** function is called to show **To print PHP’s predefined variables:**

the values stored in the **$\_SERVER** predefined variable.

**1.** Create a new PHP script in your

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

text editor or IDE, to be named

1.0

Transitional//EN"

**predefined.php** (**Script 2.1**).

2 "http://www.w3.org/TR/xhtml1/DTD/

xhtml1-transitional.dtd">

**2.** Create the initial HTML tags:

3 <html

xmlns="http://www.w3.org/1999/xhtml"

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

xml:lang="en"

lang="en">

4 <head>

➝ **XHTML 1.0 Transitional//EN"**

5

<meta http-equiv="Content-Type"

**"http://www.w3.org/TR/xhtml1/DTD/**

content="text/html;

charset=utf-8"/>

 ➝ **xhtml1-transitional.dtd">**

6 <title>Predefined

Variables</title>

**<html xmlns="http://www.w3.org/**

7 </head>

➝ **1999/xhtml" xml:lang="en"**

8 <body>

9 <pre>

➝ **lang="en">**

10 <?php // Script 2.1 - predefined.php

**<head>**

11

**<meta**

**http-equiv="Content-Type"**

12 // Show the value of the $\_SERVER

 ➝ **content="text/html;**

variable:

 ➝ **charset=utf-8"/>**

**13 print\_r**

**($\_SERVER);**

14

**<title>Predefined**

**Variables**

15 ?>

 ➝ **</title>**

16 </pre>

**</head>**

17 </body>

**<body>**

18 </html>

**<pre>**

This code repeats the XHTML template

created in the preceding chapter. Within

the body of the page, the **<pre>** tags

are being used to make the generated

PHP information more legible. Without

using the **<pre>** tags, the **print\_r()**

function’s output would be quite messy.

**3.** Add the PHP code:

**<?php // Script 2.1 - predefined.php**

**print\_r($\_SERVER);**

**?>**

The PHP code contains just one

function call. The function should be

provided with the name of a variable.

continues on next page

Variables 33

![Image 83](index-55_1.png)

In this example, the variable is **$\_SERVER**,

which is special in PHP. **$\_SERVER** stores

all sorts of data about the server: its

name and operating system, the name

of the current user, information about

the Web server application (Apache,

Abyss, IIS, etc.), and more. It also

reflects the PHP script being executed:

its name, where it’s stored on the

server, and so forth.

Note that you must type **$\_SERVER** exactly

as it is here, in all uppercase letters.

**4.** Complete the HTML page:

**</pre>**

**</body>**

**</html>**

**5.** Save the file as **predefined.php**, upload

it to your server (or save it to the appro-

priate directory on your computer), and

test it in your Web browser **A**.

Once again, remember that you must

run all PHP scripts through a URL (i.e.,

http://something).

**A** The **$\_SERVER**

variable, as printed out

by this script, is a master

list of values pertaining

to the server and the

PHP script.

34 Chapter

2

![Image 84](index-56_1.png)

![Image 85](index-56_2.png)

**6.** If possible, transfer the file to another

computer or server running PHP and

execute the script in your Web browser

again **B**.

**Printing out the value of any variable**

**as you’ve done here is one of the greatest**

**debugging tools. Scripts often don’t work**

**as you expect them to because one or more**

**variables do not have the values you assume**

**they should, so confirming their actual values**

**is extremely helpful.**

**If you don’t use the HTML <pre></pre>**

**tags, the result will be like the mess in C.**

**B** With the **predefined.php** page, different servers will generate different results (compare with Figure **A**).

**C** With large, complex variables such as **$\_SERVER**, not using the HTML preformatting tags with **print\_r()** creates an incomprehensible mess (compare to Figures **A** and **B**).

Variables 35

![Image 86](index-57_1.png)

[**Variable Syntax**](#index_split_000.html#p6)

Now that you’ve had a quick dip in the

variable pool, it’s time to investigate the

subject further. In the preceding example,

the script reported upon PHP’s predefined

**$\_SERVER** variable. You can also create

your own variables, once you understand

the proper syntax. To create appropriate

variable names, you must follow these rules:

■

All variable names must be preceded

by a dollar sign (**$**).

■

Following the dollar sign, the variable

name must begin with either a letter

(A–Z, a–z) or an underscore ( **\_** ). It can’t

begin with a number.

■

The rest of the variable name can

contain any combination of letters,

underscores, and numbers.

■

You may not use spaces within the

name of a variable. (Instead, the

underscore is commonly used to

separate words.)

■

Each variable must have a unique name.

■

Variable names are case-sensitive!

Consequently, **$variable** and

**$Variable** are two different constructs,

and it would be a bad idea to use two

variables with such similar names.

This last point is perhaps the most

important: variable names in PHP are case-

sensitive. Using the wrong letter case is a

very common cause of bugs. (If you used,

for example, **$\_server** or **$\_Server** in the

previous script, you’d see either an error

message or nothing at all **A**.)

**A** Misspelling a variable’s name, including its case, will create undesired and unpredictable results.

36 Chapter

2

**Script 2.2** Properly documenting the purposes of To help minimize bugs, I recommend the

variables, along with using meaningful names, is

following policies:

a hallmark of a professional programmer.

■

Always use all lowercase variable

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

names.

1.0

Transitional//EN"

2 "http://www.w3.org/TR/xhtml1/DTD/

■

Make your variable names descriptive

xhtml1-transitional.dtd">

(e.g., **$first\_name** is better than **$fn**).

3 <html

xmlns="http://www.w3.org/1999/xhtml"

xml:lang="en"

lang="en">

■

Use comments to indicate the purpose

4 <head>

of variables (**Script 2.2**), redundant as

5

<meta http-equiv="Content-Type"

that may seem.

content="text/html;

charset=utf-8"/>

6

<title>Variables and Comments</title>

■

Above all, be consistent with whatever

7 </head>

naming convention you choose!

8 <body>

9

<?php // Script 2.2

**Table 2.1** lists some sample valid variables;

10

**Table 2.2** lists some invalid variables and

11 // Define my variables....

the rules they violate.

12

13 $year = 2011; // The current year.

14 $june\_avg = 88; // The average

**Unlike some other languages, PHP**

temperature for the month of June.

**generally doesn’t require you to declare or**

15 $page\_title = 'Weather Reports';

**initialize a variable prior to use. In other words,**

// A title for the page.

**you can refer to variables without first defining**

16

**them. But it’s best not to do that; I try to write**

17 // ... and so forth.

**my scripts so that every variable is defined or**

18

**validated before use.**

19 ?>

20 </body>

**There are two main variable naming**

21 </html>

**conventions, determined by how you delineate**

**words. These are the so-called camel-hump**

**or camel-case (named because of the way**

**capital letters break up the word—for example,**

**TABLE 2.1 Valid Variables in PHP**

**$FirstName) and underscore ($first\_name)**

**styles. This book uses the latter convention.**

**Name**

**$first\_name**

**$person**

**$address1**

**$\_SERVER**

**TABLE 2.2 Invalid Variables in PHP**

**Name**

**Reason**

**$first name**

Has a space

**$first.name**

Has a period

**first\_name**

Does not begin with **$**

**$1address**

A number cannot follow **$**

Variables 37

[**Types of Variables**](#index_split_000.html#p6)

**TABLE 2.3 Valid Numbers in PHP**

This book covers the three main PHP

**Number**

**Type**

variable types: numbers, strings, and arrays.

1

Integer

I’ll introduce them quickly here, and later

1.0

Floating-point

chapters will discuss them in more detail:

1972

Integer

■

Chapter 4, “Using Numbers”

19.72

Floating-point

■

Chapter 5, “Using Strings”

–1

Integer

■

Chapter 7, “Using Arrays”

–1.0

Floating-point

A fourth variable type, objects, is introduced

in Appendix B, “Resources and Next Steps,”

but isn’t covered in this book. That particular

**TABLE 2.4 Invalid Numbers in PHP**

subject is just too advanced for a beginner’s

guide—in fact, basic coverage of the subject

**Number**

**Reason**

in my PHP 5 Advanced: Visual QuickPro

1/3

Contains a slash

Guide (Peachpit Press, 2007) requires over

1996a

Contains a letter

150 pages!

08.02.06

Contains multiple

decimals

**Numbers**

Technically speaking, PHP breaks numbers

into two types: integers and floating-point

(also known as double-precision floating-

point or doubles). Due to the lax way

PHP handles variables, it won’t affect your

programming to group the two categories of

numbers into one all-inclusive membership.

Still, let’s briefly discuss the differences

between the two, for clarity’s sake.

The first type of numbers—integers—are

the same as whole numbers. They can be

positive or negative but include neither

fractions nor decimals. Numbers that use a

decimal point (even something like 1.0) are

floating-point numbers. You must also use

floating-point numbers to refer to fractions,

because the only way to express a fraction

in PHP is to convert it to its decimal

equivalent. Hence, 1 1⁄4 is written as 1.25.

**Table 2.3** lists some sample valid numbers

and their formal type; **Table 2.4** lists invalid

numbers and the rules they violate.

**As you’ll soon see, you can quote invalid**

**numbers to turn them into valid strings.**

38 Chapter

2

**Strings**

The backslash tells PHP to treat each

escaped quotation mark as part of the

A string is any number of characters

value of the string, rather than using it as

enclosed within a pair of either single (**'** )

the string’s opening or closing indicators.

or double (**"** ) quotation marks. Strings

can contain any combination of letters,

You can similarly circumvent this problem

numbers, symbols, and spaces. Strings

by using different quotation mark types:

can also contain variables.

**'I said, "How are you?"'**

Here are examples of valid string values:

**"I said, 'How are you?'"**

**"Hello, world!"**

**Notice that “1996” converts an integer**

**"Hello, $first\_name!"**

**into a string, simply by placing the number**

**"1/3"**

**within quotes. Essentially, the string contains**

**'Hello, world! How are you today?'**

**the characters 1996, whereas the number (a**

**"08.02.06"**

**nonquoted value) would be equal to 1996.**

**"1996"**

**It’s a fine distinction, and one that won’t**

**matter in your code, because you can perform**

**''**

**mathematical calculations with the string 1996**

That last one is an empty string—a string

**just as you can with the number.**

that contains no characters.

**Chapter 1 also demonstrated how to**

In short, to create a string, just wrap

**create a new line by printing the \\n charac-**

something within quotation marks. There

**ter within double quotation marks. Although**

are cases, however, where you may run

**escaping a quotation mark prints the quota-**

**tion mark, escaping an n prints a new line,**

into problems. For example:

**escaping an r creates a carriage return, and**

**"I said, "How are you?""**

**escaping a t creates a tab.**

This string will be tricky and I hinted at the

**Understanding strings, variables, and the**

same problem in Chapter 1, “Getting Started

**single and double quotation marks is critical**

with PHP,” with respect to printing HTML

**to programming with PHP. For this reason, a**

code. When PHP hits the second quotation

**section at the end of this chapter is dedicated**

**to the subject.**

mark in the above, it assumes the string

ends there; the continuing text (How…)

causes an error. To use a quotation mark

within a string you can escape the quotation

mark by putting a backslash ( **\\**) before it:

**"I said, \\"How are you?\\""**

Variables 39

**Arrays**

**TABLE 2.5 Indexed Array**

Arrays are covered more thoroughly in

**Key**

**Value**

Chapter 7, but let’s look at them briefly here.

Whereas a string or a number contains a

0

Don

single value (both are said to be scalar),

1

Betty

an array can have more than one value

2

Roger

assigned to it. You can think of an array as

3

Jane

a list or table of values: you can put multiple

strings and/or numbers into one array.

Arrays use keys to create and retrieve

**TABLE 2.6 Associative Array**

the values they store. The resulting

structure—a list of key-value pairs—looks

**Key**

**Value**

similar to a two-column spreadsheet.

VT

Vermont

Unlike arrays in other programming

NH

New Hampshire

languages, the array structure in PHP is

IA

Iowa

so flexible that it can use either numbers

PA

Pennsylvania

or strings for both the keys and the

values. The array doesn’t even need to be

consistent in this respect. (All of this will

make more sense in Chapter 7, when you

start working with specific examples.)

PHP has two different types of arrays,

based on the format of the keys. If the array

uses numbers for the keys (**Table 2.5**), it’s

called an indexed array. If it uses strings

for the keys (**Table 2.6**), it’s an associative

array. In either case, the values in the array

can be of any variable type (string, number,

and so on).

**The array’s key is also called its**

**index. You’ll see these two terms used**

**interchangeably.**

**An array can, and frequently will, contain**

**other arrays, creating what is called a multi-**

**dimensional array.**

**What PHP calls an associative array**

**is called a hash in Perl and Ruby, among**

**other languages.**

40 Chapter

2

![Image 87](index-62_1.png)

![Image 88](index-62_2.png)

[**Variable Values**](#index_split_000.html#p6)

To assign a value to a variable, regardless

of the variable type, you use the equals

**A** The result of printing the values of

two variables.

sign (**\=**). Therefore, the equals sign is

called the assignment operator, because

it assigns the value on the right to the

variable on the left. For example:

**$number = 1;**

**B** Using the **print**

statement on a complex

**$floating\_number = 1.2;**

variable type, such as an

**$string = "Hello, world!";**

array, will not have the

results you desire.

As each of these lines represents a complete

statement (i.e., an executable action), they

each conclude with a semicolon.

To print out the value of a variable, you can

use the **print** function:

**print $number;**

**print $string;**

If you want to print a variable’s value within

a context, you can place the variable’s

name in the printed string, as long as you

use double quotation marks **A**:

**print "Number is $number";**

**print "String is $string";**

Using **print** in this way works for the

scalar (single-valued) variable types—

numbers and strings. For complex variable

types—arrays and objects—you cannot just

use **print** **B**:

**print "**

**\_SERVER is $\_SERVER";**

As you’ve already seen, **print\_r()** can

handle these nonscalar types, and you’ll

learn other approaches later in the book.

continues on next page

Variables 41

Whether you’re dealing with scalar or

**Script 2.3** Some basic variables are defined and

nonscalar variables, don’t forget that

their values printed by this script.

printing out their values is an excellent

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

debugging technique when you’re having

1.0

Transitional//EN"

problems with a script!

2 "http://www.w3.org/TR/xhtml1/DTD/

xhtml1-transitional.dtd">

Because variable types aren’t locked in

3 <html

xmlns="http://www.w3.org/1999/xhtml"

(PHP is referred to as a weakly typed

xml:lang="en"

lang="en">

language), they can be changed on the fly:

4 <head>

5

<meta http-equiv="Content-Type"

**$variable = 1;**

content="text/html;

charset=utf-8"/>

**$variable = "Greetings";**

6 <title>Variables</title>

7 </head>

If you were to print the value of **$variable**

8 <body>

now, the result would be Greetings. The

9

<?php // Script 2.3 - variables.php

following script better demonstrates the

10

concept of assigning values to variables

11 // An address:

and then accessing those values.

**12 $street = "100 Main Street";**

**13 $city = "State College";**

**14 $state = "PA";**

**To assign values to and**

**15 $zip = 16801;**

**access variables:**

16

17 // Print the address:

**1.** Create a new PHP script in your

**18 print "<p>The address is:<br />$street**

text editor or IDE, to be named

**<br />$city $state $zip</p>";**

**variables.php** (**Script 2.3**).

19

20 ?>

**2.** Create the initial HTML tags:

21 </body>

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

22 </html>

➝ **XHTML 1.0 Transitional//EN"**

**"http://www.w3.org/TR/xhtml1/DTD/**

 ➝ **xhtml1-transitional.dtd">**

**<html xmlns="http://www.w3.org/**

➝ **1999/xhtml" xml:lang="en"**

➝ **lang="en">**

**<head>**

**<meta**

**http-equiv="Content-Type"**

 ➝ **content="text/html;**

 ➝ **charset=utf-8"/>**

**<title>Variables</title>**

**</head>**

**<body>**

42 Chapter

2

**3.** Begin the PHP code:

**<?php // Script 2.3 - variables.php**

**4.** Define some number and string variables:

**$street = "100 Main Street";**

**$city = "State College";**

**$state = "PA";**

**$zip = 16801;**

These lines create four different variables

of both string and number types. The

strings are defined using quotation

marks, and each variable name follows

the syntactical naming rules.

Remember that each statement must

conclude with a semicolon and that the

variable names are case-sensitive.

**5.** Print out the values of the variables

within some context:

**print "<p>The address is:<br />**

➝ **$street <br />$city $state**

➝ **$zip</p>";**

Here a single **print** statement can

access all the variables. The entire

string to be printed (consisting of text,

HTML tags, and variables) is enclosed

within double quotation marks. The

HTML **<br />** tags make the text flow

over multiple lines in the browser

window (remember, the extra space and

slash in the break tag are there for sake

of XHTML compliance).

continues on next page

Variables 43

![Image 89](index-65_1.png)

![Image 90](index-65_2.png)

![Image 91](index-65_3.png)

**6.** Complete the PHP section and the

HTML page:

**?>**

**</body>**

**</html>**

**7.** Save the file as **variables.php**, upload

**C** Some variables are assigned values,

and then printed within a context.

it to your server (or save it to the appro-

priate directory on your computer), and

test it in your Web browser **C**.

**If you see a parse error D when you**

**D** Parse errors are the most common type of

**run this script, you probably either omitted**

PHP error, as you’ll discover. They’re frequently

**a semicolon or have an imbalance in your**

caused by missing semicolons or an imbalance

of quotation marks or parentheses.

**quotation marks.**

**If one of the variable’s values isn’t**

**printed out or you see an Undefined variable**

**error E, you most likely failed to spell a vari-**

**able name the same way twice.**

**If you see a blank page, you most likely**

**have an error but PHP’s display\_errors**

**configuration is set to off. See Chapter 3,**

**“HTML Forms and PHP,” for details.**

**E** The Undefined variable error indicates that

you used a variable with no value (it hasn’t been

defined). This can happen with misspellings and

capitalization inconsistencies.

44 Chapter

2

**Script 2.4** This script simply demonstrates how the type of quotation mark you use with variables

[**Understanding**](#index_split_000.html#p6)

affects the end result.

[**Quotation Marks**](#index_split_000.html#p6)

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

1.0

Transitional//EN"

Now that you know the basics of variables

2 "http://www.w3.org/TR/xhtml1/DTD/

and how to create them, I want to make

xhtml1-transitional.dtd">

sure you completely understand how to

3 <html

xmlns="http://www.w3.org/1999/xhtml"

properly use quotation marks. PHP, like

xml:lang="en"

lang="en">

most programming languages, allows

4 <head>

5

<meta http-equiv="content-type"

you to use both double ( **"** ) and single

content="text/html; charset=utf-8" />

( **'** ) quotation marks—but they give vastly

6 <title>Quotes</title>

different results. It’s critical that you

7 </head>

comprehend the distinction, so the next

8 <body>

example will run tests using both types.

9

<?php // Script 2.4 - quotes.php

10

The rule to remember is: Items within

11 // Single or double quotation marks

single quotation marks are treated

won't matter here:

literally; items within double quotation

**12 $first\_name = 'Larry';**

**13 $last\_name = "Ullman";**

marks are extrapolated. This means

14

that within double quotation marks, a

15 // Single or double quotation marks DOES

variable’s name is replaced with its value,

matter

here:

as in Script 2.3, but the same is not true

**16 $name1 = '$first\_name $last\_name';**

for single quotation marks.

**17 $name2 = "$first\_name $last\_name";**

18

This rule applies anywhere in PHP you might

19 // Single or double quotation marks DOES

use quotation marks, including uses of the

matter

here:

**print** function and the assignment of values

**20 print "<h1>Double Quotes</h1><p>name1**

**is $name1 <br />**

to string variables. An example is the best

**21 name2 is $name2</p>";**

way to demonstrate this critical concept.

**22**

**23 print '<h1>Single Quotes</h1><p>name1**

**To use quotation marks:**

**is $name1 <br />**

**24 name2 is $name2</p>';**

**1.** Begin a new PHP script in your text

25

editor or IDE, to be named **quotes.php**

26 ?>

(**Script 2.4**).

27 </body>

28 </html>

**2.** Create the initial HTML tags:

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

➝ **XHTML 1.0 Transitional//EN"**

**"http://www.w3.org/TR/xhtml1/**

 ➝ **DTD/xhtml1-transitional.dtd">**

**<html xmlns="http://www.w3.org/**

➝ **1999/xhtml" xml:lang="en"**

➝ **lang="en">**

continues on next page

Variables 45

**<head>**

In these lines it makes a huge

**<meta**

**http-equiv="content-type"**

difference which quotation marks you

 ➝ **content="text/html;**

use. The **$name1** variable is now literally

 ➝ **charset=utf-8" />**

equal to $first\_name $last\_name,

**<title>Quotes</title>**

because no extrapolation occurs.

**</head>**

Conversely, **$name2** is equal to Larry

**<body>**

Ullman, presumably the intended result.

**3.** Begin the PHP code:

**6.** Print out the variables using both types

**<?php // Script 2.4 - quotes.php**

of quotation marks:

**print "<h1>Double Quotes**

**4.** Create two string variables:

➝ **</h1><p>name1 is $name1 <br />**

**$first\_name = 'Larry';**

**name2 is $name2</p>";**

**$last\_name = "Ullman";**

**print '<h1>Single Quotes**

It doesn’t matter whether you use single

➝ **</h1><p>name1 is $name1 <br />**

or double quotation marks for these two

**name2 is $name2</p>';**

variables, as each string can be treated

Again, the quotation marks make all

literally. However, if you’re using your

the difference here. The first **print**

own name here (and feel free to do so)

statement, using double quotation marks,

and it contains an apostrophe, you’ll

prints out the values of the **$name1** and

need to either use double quotation

**$name2** variables, whereas the second,

marks or escape the apostrophe within

using single quotation marks, prints out

single quotation marks:

$name1 and $name2 literally.

**$last\_name = "O'Toole";**

The HTML in the **print** statements

**$last\_name = 'O\\'Toole';**

makes them more legible in the

**5.** Create two different name variables,

browser, and each statement is

using the existing first- and last-name

executed over two lines, which is

variables:

perfectly acceptable.

**$name1 = '$first\_name $last\_name';**

**7.** Complete the PHP section and the

**$name2 = "$first\_name**

HTML page:

➝ **$last\_name";**

**?>**

**</body>**

**</html>**

46 Chapter

2

![Image 92](index-68_1.png)

**8.** Save the file as **quotes.php**, upload it to

your server (or save it to the appropri-

ate directory on your computer), and

test it in your Web browser **A**.

**If you’re still confused about the**

**distinction between the two types of quotation**

**marks, stick with double quotation marks and**

**you’ll be safer.**

**Arguably, using single quotation marks**

**when you can is marginally preferable, as PHP**

**won’t need to search the strings looking for**

**variables. But, at best, this is a minor point.**

**A** The different quotation marks

(single versus double) dictate whether

**The shortcuts for creating newlines (\\n),**

the variable’s name or value is printed.

**carriage returns (\\r), and tabs (\\t) must also**

**be used within double quotation marks to**

**have the desired effect.**

**Remember that you don’t always need to**

**use quotation marks at all. When assigning a**

**numeric value or when only printing a variable,**

**you can omit them:**

**$num = 2;**

**print $num;**

Variables 47

[**Review and Pursue**](#index_split_000.html#p6)

If you have any problems with the review

questions or the pursue prompts, turn

to the book’[s supporting forum (www.](http://www.LarryUllman.com/forum/)

[LarryUllman.com/forum/).](http://www.LarryUllman.com/forum/)

**Review**

■

What kind of variable is **$\_SERVER** an

example of?

■

What character must all variables

begin with?

■

What characters can be used first in a

variable’s name? What other characters

can be used in a variable’s name, after

the first character?

■

Are variable names case-sensitive or

case-insensitive?

■

What does it mean to say that a variable

is scalar? What are examples of scalar

variable types? What is an example of a

nonscalar variable type?

■

What is the assignment operator?

■

What great debugging technique—with

respect to variables—was introduced in

this chapter?

■

What is the difference between using

single or double quotation marks?

**Pursue**

■

Create another PHP script that defines

some variables and prints their values.

Try using variables of different scalar

types.

■

Create a PHP script that prints the value

of some variables within some HTML.

More sophisticated practice might

involve using PHP and variables to

create a link or image tag.

48 Chapter

2

[**3**](#index_split_000.html#p6)

[HTML Forms](#index_split_000.html#p6)

[and PHP](#index_split_000.html#p6)

The previous chapter provided a brief intro-

duction to the topic of variables. Although

**In This Chapter**

you’ll often create your own variables, you’ll

also commonly use variables in conjunction

Creating a Simple Form

50

with HTML forms. Forms are a fundamental

Choosing a Form Method

54

unit of today’s Web sites, enabling such

Receiving Form Data in PHP

57

features as registration and login systems,

search capability, and online shopping.

Displaying Errors

61

Even the simplest site will find logical rea-

Error Reporting

64

sons to incorporate HTML forms. And with

Manually Sending Data to a Page

67

PHP, it’s stunningly simple to receive and

handle data generated by them.

Review and Pursue

72

With that in mind, this chapter will cover

the basics of creating HTML forms and

explain how the submitted form data is

available to a PHP script. This chapter will

also introduce several key concepts of real

PHP programming, including how to man-

age errors in your scripts.

![Image 93](index-71_1.png)

[**Creating a**](#index_split_000.html#p6)

[**Simple Form**](#index_split_000.html#p6)

For the HTML form example in this chapter,

you’ll create a feedback page that takes

the user’s salutation, name, email address,

response, and comments **A**. The code that

generates a form goes between opening

and closing **form** tags:

**<form>**

***form elements***

**A** The HTML form that will be used in this

**</form>**

chapter’s examples.

The **form** tags dictate where a form begins

and ends. Every element of the form must

be entered between these two tags. The

opening **form** tag also contains an **action**

attribute. It indicates the page to which the

form data should be submitted. This value

is one of the most important considerations

when you’re creating a form. In this book,

the **action** attributes will always point to

PHP scripts:

**<form action="somepage.php">**

Before creating this next form, let’s briefly

revisit the topic of XHTML. As stated in

the first chapter, XHTML has some rules

that result in a significantly different syntax

than HTML. For starters, the code needs

to be in all lowercase letters, and every

tag attribute must be enclosed in quotes.

Further, every tag must be closed; those

that don’t have formal closing tags, like 

**input**, are closed by adding a blank space

and a slash at the end. Thus, in HTML you

might write

**<INPUT TYPE=TEXT NAME=address**

➝ **SIZE=40>**

but in XHTML you’d write

**<input type="text" name="address"**

➝ **size="40" />**

50 Chapter

3

**Script 3.1** This HTML page has a form with several Hopefully this quick explanation will help you

different input types.

understand the XHTML in the following script.

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

Finally, in both HTML and XHTML, each

1.0

Transitional//EN"

form element needs to have its own

2 "http://www.w3.org/TR/xhtml1/DTD/

unique name. Stick to a consistent naming

xhtml1-transitional.dtd">

3 <html

xmlns="http://www.w3.org/1999/

convention when naming elements, using

xhtml" xml:lang="en" lang="en">

only letters, numbers, and the underscore

4 <head>

( \_ ). The result should be names that are

5

<meta http-equiv="Content-Type"

also logical and descriptive.

content="text/html;

charset=utf-8"/>

6 <title>Feedback

Form</title>

7 </head>

**To create a basic HTML form:**

8 <body>

**1.** Begin a new document in your text edi-

9

<!-- Script 3.1 - feedback.html -->

10 <div><p>Please complete this form to

tor or IDE, to be named **feedback.html**

submit your feedback:</p>

(**Script 3.1**):

11

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

**12 <form**

**action="handle\_form.php">**

13

➝ **XHTML 1.0 Transitional//EN"**

**14**

**<p>Name: <select name="title">**

**"http://www.w3.org/TR/xhtml1/**

**15 <option**

**value="Mr.">Mr.</option>**

 ➝ **DTD/xhtml1-transitional.dtd">**

**16 <option**

**value="Mrs.">Mrs.</option>**

**<html xmlns="http://www.w3.org/**

**17 <option**

**value="Ms.">Ms.</option>**

**18**

**</select> <input type="text"**

➝ **1999/xhtml" xml:lang="en"**

**name="name" size="20" /></p>**

➝ **lang="en">**

19

**<head>**

**20**

**<p>Email Address: <input**

**<meta**

**http-equiv="Content-Type"**

**type="text" name="email"**

**size="20"**

**/></p>**

➝ **content="text/html;**

21

 ➝ **charset=utf-8"/>**

**22**

**<p>Response: This is...**

**<title>Feedback**

**Form</title>**

**23**

**<input type="radio"**

**</head>**

**name="response" value="excellent" />**

**<body>**

**excellent**

**24**

**<input type="radio"**

**<!-- Script 3.1 - feedback.html -->**

**name="response" value="okay" />**

**<div><p>Please complete this form**

**okay**

➝ **to submit your feedback:</p>**

**25 <input**

**type="radio"**

**name="response" value="boring" />**

**2.** Add the opening **form** tag:

**boring</p>**

**<form action="handle\_form.php">**

26

**27**

**<p>Comments: <textarea**

The **form** tag indicates that this form will

**name="comments" rows="3"**

be submitted to the page **handle\_form.**

**cols="30"></textarea></p>**

**php**, found within the same directory as

28

this HTML page. You can use a full URL

**29**

**<input type="submit" name="submit"**

**value="Send My Feedback" />**

to the PHP script, if you’d prefer to be

30

explicit (e.g., [**http://www.example.com/**](http://www.example.com/handle_form.php)

**31 </form>**

[**handle\_form.php**).](http://www.example.com/handle_form.php)

32 </div>

33 </body>

continues on next page

34 </html>

HTML Forms and PHP 51

![Image 94](index-73_1.png)

**3.** Add a select menu plus a text input for

the person’s name:

**<p>Name: <select name="title">**

**<option value="Mr.">Mr.</option>**

**<option value="Mrs.">Mrs.</option>**

**<option value="Ms.">Ms.</option>**

**B** The **select** element creates a drop-down

menu of options.

**</select> <input type="text"**

**name="name" size="20" /></p>**

The inputs for the person’s name will

consist of two elements **A**. The first is

a drop-down menu of common titles:

Mr., Mrs., and Ms. Each option listed

between the **select** tags is an answer

the user can choose **B**. The second

element is a basic text box for the

person’s full name.

**4.** Add a text input for the user’s email

address:

**<p>Email Address: <input**

➝ **type="text" name="email"**

➝ **size="20" /></p>**

**5.** Add radio buttons for a response:

**<p>Response: This is...**

**<input type="radio" name="response"**

➝ **value="excellent" /> excellent**

**<input type="radio" name="response"**

➝ **value="okay" /> okay**

**<input type="radio" name="response"**

➝ **value="boring" /> boring</p>**

This HTML code creates three radio

buttons (clickable circles, **A**). Because

they all have the same **name** value, only

one of the three can be selected at a

time. Per XHTML rules, the code is in

lowercase except for the values, and an

extra space and slash are added to the

end of each input to close the tag.

52 Chapter

3

**6.** Add a **textarea** to record the comments: **Note that feedback.html uses the**

**HTML extension because it’s a standard**

**<p>Comments: <textarea**

**HTML page (not a PHP script). You could**

➝ **name="comments" rows="3"**

**use the .php extension without a problem,**

➝ **cols="30"></textarea></p>**

**even though there’s no actual PHP code.**

**(Remember that in a PHP page, anything**

A **textarea** gives users more space to

**not within the PHP tags—<?php and ?>—is**

enter their comments than a text input

**assumed to be HTML.)**

would. However, the text input lets

**Be certain that your**

you limit how much information users

**action attribute**

**correctly points to an existing file on the**

can enter, which you can’t do with the

**server, or your form won’t be processed prop-**

**textarea** (not without using JavaScript,

**erly. In this case, the form will be submitted to**

that is). When you’re creating a form,

**handle\_form.php, to be located in the same**

choose input types appropriate to the

**directory as the feedback.html page.**

information you wish to retrieve from

**In this example, an HTML form is created**

the user.

**by hand-coding the HTML, but you can do**

Note that a **textarea** does have a

**this in a Web page application (such as Adobe**

**Dreamweaver) if you’re more comfortable with**

closing tag.

**that approach.**

**7.** Add the submit button:

**One welcome addition in the forthcom-**

**<input type="submit" name="submit"**

**ing HTML 5 specification are new form ele-**

➝ **value="Send My Feedback" />**

**ments, such as email, url, and number.**

The **value** attribute of a submit element

is what appears on the button in the

Web browser **A**. You could also use

Go! or Submit, for example.

**8.** Close the form:

**</form>**

**9.** Complete the page:

**</div>**

**</body>**

**</html>**

**10.** Save the page as **feedback.html** and

view it in your browser.

Because this is an HTML page, not a

PHP script, you could view it in your Web

browser directly from your computer.

HTML Forms and PHP 53

![Image 95](index-75_1.png)

[**Choosing a Form**](#index_split_000.html#p6)

[**Method**](#index_split_000.html#p6)

The experienced HTML developer will

notice that the feedback form just created

**A** If users refresh a PHP script that data has been

is missing one thing: The initial **form** tag

sent to via the POST method, they will be asked to

has no **method** attribute. The **method**

confirm the action (the specific message will differ

using other browsers).

attribute tells the server how to transmit

the data from the form to the handling

script.

You have two choices with **method**: GET

and POST. With respect to forms, the dif-

ference between using GET and POST is

squarely in how the information is passed

from the form to the processing script. The

GET method sends all the gathered infor-

mation along as part of the URL. The POST

method transmits the information invisibly

to the user. For example, upon submitting

a form, if you use the GET method, the

resulting URL will be something like

[**http://www.example.com/page.php?**](http://www.example.com/page.php?) 

➝ **some\_var=some\_value&age=20&...**

Following the name of the script, **page.php**, is a

question mark, followed by one name=value

pair for each piece of data submitted.

When using the POST method, the end

user will only see

[**http://www.example.com/page.php**](http://www.example.com/page.php)

When deciding which method to use, keep

in mind these four factors:

■

With the GET method, a limited amount

of information can be passed.

■

The GET method sends the data to the

handling script publicly (which means,

for example, that a password entered

in a form would be viewable by anyone

within eyesight of the Web browser,

creating a larger security risk).

54 Chapter

3

**Script 3.2** The **method** attribute with a value of

■

A page generated by a form that used

post is added to complete the form.

the GET method can be bookmarked,

but one based on POST can’t be.

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

1.0

Transitional//EN"

■

Users will be prompted if they attempt

2 "http://www.w3.org/TR/xhtml1/DTD/

to reload a page accessed via POST

xhtml1-transitional.dtd">

**A**,

but will not be prompted for pages

3 <html

xmlns="http://www.w3.org/1999/

xhtml" xml:lang="en" lang="en">

accessed via GET.

4 <head>

Generally speaking, GET requests are

5

<meta http-equiv="Content-Type"

used when asking for information from the

content="text/html;

charset=utf-8"/>

6 <title>Feedback

Form</title>

server. Search pages almost always use

7 </head>

GET (check out the URLs the next time

8 <body>

you use a search engine), as do sites that

9

<!-- Script 3.2 - feedback.html -->

paginate results (like the ability to browse

10 <div><p>Please complete this form to

categories of products). Conversely, POST

submit your feedback:</p>

11

is normally used to trigger a server-based

**12 <form action="handle\_form.php"**

action. This might be the submission of a

**method="post">**

contact form (result: an email gets sent)

13

or the submission of a blog’s comment

14

<p>Name: <select name="title">

form (result: a comment is added to the

15 <option

value="Mr.">Mr.</option>

16 <option

value="Mrs.">Mrs.</option>

database and therefore the page).

17 <option

value="Ms.">Ms.</option>

This book uses POST almost exclusively for

18

</select> <input type="text"

handling forms, although you’ll also see a

name="name" size="20" /></p>

19

useful technique involving the GET method

20

<p>Email Address: <input type="text"

(see “Manually Sending Data to a Page” at

name="email" size="20" /></p>

the end of this chapter).

21

22

<p>Response: This is...

23

<input type="radio" name="response"

**To add a method to a form:**

value="excellent" /> excellent

**1.** Open **feedback.html** (Script 3.1)

24

<input type="radio" name="response"

in your text editor or IDE, if it is not

value="okay" /> okay

25

<input type="radio" name="response"

already open.

value="boring" /> boring</p>

**2.** Within the initial **form** tag, add

26

**method="post"** (**Script 3.2**, line 12).

27

<p>Comments: <textarea name="comments"

rows="3"

cols="30"></textarea></p>

The form’s **method** attribute tells the

28

browser how to send the form data to

29

<input type="submit" name="submit"

the receiving script. Because there may

value="Send My Feedback" />

30

be a lot of data in the form’s submission

31 </form>

(including the comments), and because

32 </div>

it wouldn’t make sense for the user to

33 </body>

bookmark the resulting page, POST is

34 </html>

the logical method to use.

continues on next page

HTML Forms and PHP 55

![Image 96](index-77_1.png)

**3.** Save the script and reload it in your

Web browser.

It’s important that you get in the habit

of reloading pages in the Web browser

after you make changes. It’s quite easy

to forget the reloading step and find

yourself flummoxed when your changes

are not being reflected.

**4.** View the source of the page to make

sure all the required elements are pres-

ent and have the correct attributes **B**.

**In the discussion of the methods, GET**

**and POST are written in capital letters to make**

**them stand out. However, the form in the script**

**uses post for XHTML compliance. Don’t worry**

**about this inconsistency (if you caught it at**

**all)—the method will work regardless of case.**

**B** With forms, much of the important information, such as the **action** and **method** values or element names, can only be seen within the HTML source code.

56 Chapter

3

![Image 97](index-78_1.png)

[**Receiving Form**](#index_split_000.html#p6)

Instead, to access a specific value, you

must refer to the array’s index or key.

[**Data in PHP**](#index_split_000.html#p6)

Chapter 7, “Using Arrays,” goes into this

subject in detail, but the premise is simple.

Now that you’ve created a basic HTML

Start with a form element whose **name**

form capable of taking input from a user,

attribute has a value of something:

you need to write the PHP script that will

**<input type="text" name="something" />** receive and process the submitted form

data. For this example, the PHP script will

Then, assuming that the form uses the

simply repeat what the user entered into

POST method, the value entered into

the form. In later chapters, you’ll learn how

that form element would be available

to take this information and store it in a

in **$\_POST\['something'\]**:

database, send it in an email, write it to

**print $\_POST\['something'\];**

a file, and so forth.

Unfortunately, there is one little hitch here:

To access the submitted form data, you need

When used within double quotation marks,

to refer to a particular predefined variable.

the single quotation marks around the key

Chapter 2, “Variables,” already introduced

will cause parse errors **A**:

one predefined variable: **$\_SERVER**. When

**print "Thanks for saying:**

it comes to handling form data, the specific

➝ **$\_POST\['something'\]";**

variable the PHP script would refer to is

either **$\_GET** or **$\_POST**. If an HTML form uses

There are a couple of ways you can avoid

the GET method, the submitted form data

this problem. This chapter will use the

will be found in **$\_GET**. When an HTML form

solution that’s syntactically the simplest:

uses the POST method, the submitted form

just assign the particular **$\_POST** element to

data will be found in **$\_POST**.

another variable first:

**$\_GET** and **$\_POST**, besides being predefined

**$something = $\_POST\['something'\];**

variables (i.e., ones you don’t need to

**print "Thanks for saying: $something";**

create), are arrays, a special variable type

Two final notes before implementing this

(**$\_SERVER** is also an array). This means

information in a new PHP script: First, as with

that both **$\_GET** and **$\_POST** may contain

all variables in PHP, **$\_POST** is case-sensitive:

numerous values, making the printing of

it must be typed exactly as you see it here (a

those values more challenging. You cannot

dollar sign, one underscore, then all capital

treat arrays like so (also see Figure B under

letters). Second, the indexes in **$\_POST**—

“Variable Values” in Chapter 2):

something in the preceding example—must

**print $\_POST; // Will not work!**

exactly match the **name** attributes values in

the corresponding form element.

**A** This ugly parse error is created by attempting to use

**$\_POST\['something'\]** within double quotation marks.

HTML Forms and PHP 57

**To handle an HTML form:**

**Script 3.3** This script displays the form data

submitted to it by referencing the associated

**1.** Begin a new document in your

**$\_POST** variables.

text editor or IDE, to be named

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

**handle\_form.php** (**Script 3.3**):

1.0

Transitional//EN"

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

2 "http://www.w3.org/TR/xhtml1/DTD/

➝ **XHTML 1.0 Transitional//EN"**

xhtml1-transitional.dtd">

3 <html

xmlns="http://www.w3.org/1999/

**"http://www.w3.org/TR/xhtml1/DTD/**

xhtml" xml:lang="en" lang="en">

 ➝ **xhtml1-transitional.dtd">**

4 <head>

**<html xmlns="http://www.w3.org/**

5

<meta http-equiv="Content-Type"

➝ **1999/xhtml" xml:lang="en"**

content="text/html;

charset=utf-8"/>

➝ **lang="en">**

6 <title>Your

Feedback</title>

7 </head>

**<head>**

8 <body>

**<meta**

**http-equiv="Content-Type"**

9

<?php // Script 3.3 handle\_form.php

 ➝ **content="text/html;**

10

 ➝ **charset=utf-8"/>**

11 // This page receives the data from

**<title>Your**

**Feedback</title>**

feedback.html.

12 // It will receive: title, name, email,

**</head>**

response, comments, and submit in $\_POST.

**<body>**

13

**2.** Add the opening PHP tag and any

14 // Create shorthand versions of the

variables:

comments:

**15 $title = $\_POST\['title'\];**

**<?php // Script 3.3 handle\_form.php**

**16 $name = $\_POST\['name'\];**

**// This page receives the data**

**17 $response = $\_POST\['response'\];**

**18 $comments = $\_POST\['comments'\];**

➝ **from feedback.html.**

19

**// It will receive: title, name,**

20 // Print the received data:

➝ **email, response, comments, and**

**21 print "<p>Thank you, $title $name,**

➝ **submit in $\_POST.**

**for your comments.</p>**

**22 <p>You stated that you found this**

Comments are added to the script

**example to be '$response' and**

to make the script’s purpose clear.

**added:<br**

**/>$comments</p>";**

Even though the **feedback.html** page

23

indicates where the data is sent (via

24 ?>

25 </body>

the **action** attribute), a comment here

26 </html>

indicates the reverse (where this script

is getting its data). It also helps to spell

out the exact form element names, in a

case-sensitive manner.

**3.** Assign the received data to new

variables:

**$title = $\_POST\['title'\];**

**$name = $\_POST\['name'\];**

**$response = $\_POST\['response'\];**

**$comments = $\_POST\['comments'\];**

58 Chapter

3

Again, since the form uses the POST

**Magic Quotes**

method, the submitted data can be

found in the **$\_POST** array. The individual

Earlier versions of PHP had a feature

values are accessed using the syntax

called Magic Quotes, which has since

**$\_POST\[' *name\_attribute\_value*'\]**. This

been deprecated (meaning you shouldn’t

works regardless of the form element’s

use it and it will be removed from the

language in time). Magic Quotes—when

type (input, select, checkbox, etc.).

enabled—automatically escapes single

To make it easier to use these values

and double quotation marks found in

in a **print** statement in Step 4, each

submitted form data. So the string I’d

value is assigned to a new variable in

like more information would be turned

this step. Neither **$\_POST\['email'\]** nor

into I \\’d like more information.

**$\_POST\['submit'\]** is being addressed,

The escaping of potentially problematic

but you can create variables for those

characters can be useful and even

values if you’d like.

necessary in some situations. But if the

**4.** Print out the user information:

Magic Quotes feature is enabled on

your PHP installation, you’ll see these

**print "<p>Thank you, $title $name,**

backslashes when the PHP script prints

➝ **for your comments.</p>**

out the form data. You can undo its effect

**<p>You stated that you found this**

using the **stripslashes()** function. To

➝ **example to be '$response' and**

apply it to the **handle\_form.php** script,

➝ **added:<br />$comments</p>";**

you would do this, for example:

This one **print** statement uses the four

**$comments = stripslashes**

variables within a context to show the

➝ **($\_POST\['comments'\]);**

user what data the script received.

instead of just this:

**5.** Close the PHP section and complete

**$comments = $\_POST\['comments'\];**

the HTML page:

That will have the effect of converting

**?>**

an escaped submitted string back to its

**</body>**

original, non-escaped value.

**</html>**

If you’re not seeing extraneous slashes

**6.** Save the script as **handle\_form.php**.

added to submitted form data, you don’t

need to worry about Magic Quotes.

Note that the name of this file must

exactly match the value of the **action**

attribute in the form.

**7.** Upload the script to the server (or store

it in the proper directory on your com-

puter if you’ve installed PHP), making

sure it’s saved in the same directory as

**feedback.html**.

continues on next page

HTML Forms and PHP 59

![Image 98](index-81_1.png)

![Image 99](index-81_2.png)

![Image 100](index-81_3.png)

**8.** Load **feedback.html** in your Web browser

through a URL (http://something).

You must load the HTML form through

a URL so that when it’s submitted to

the PHP script, that PHP script is also

run through a URL. PHP scripts must

always be run through a URL!

Failure to load a form through a URL is

a common beginner’s mistake.

**9.** Fill out **B**, and then submit the form **C**.

If you see a blank page, read the next

**B** Whatever the user enters into the HTML form

should be printed out to the Web browser by the

section of the chapter for how to display

**handle\_form.php** script **C**.

the errors that presumably occurred.

If you see an error notice **D** or see that

a variable does not have a value when

printed, you likely misspelled either

the form element’s **name** value or the

**C** This is another application of the **print**

**$\_POST** array’s index (or you filled out

statement discussed in Chapter 1, but it constitutes

the form incompletely).

your first dynamically generated Web page.

**If you want to pass a preset value along**

**to a PHP script, use the hidden type of input**

**within your HTML form. For example, the line**

**<input type="hidden" name="form\_page"**

**D** Notices like these occur when a script refers

**value="feedback.html" />**

to a variable that doesn’t exist. In this particular

case, the cause is erroneously referring to

**inserted between the form tags will create a vari-**

**$\_POST\['Name'\]** when it should be **$\_POST\['name'\]**.

**able in the handling script called $\_POST\['form\_**

**page'\] with the value feedback.html.**

**Notice that the value of radio button and**

**certain menu variables is based on the value**

**attribute of the selected item (for example,**

**excellent from the radio button). This is also**

**true for checkboxes. For text boxes, the value**

**of the variable is what the user typed.**

**If the handle\_form.php script displays**

**extra slashes in submitted strings, see the**

**“Magic Quotes” sidebar for an explanation**

**and solution.**

**You can also access form data, regardless**

**of the form’s method, in the $\_REQUEST pre-**

**defined variable. $\_GET and $\_POST are more**

**precise, however, and therefore preferable.**

60 Chapter

3

![Image 101](index-82_1.png)

[**Displaying Errors**](#index_split_000.html#p6)

One of the very first issues that arise when

it comes to debugging PHP scripts is that

you may or may not even see the errors that

occur. After you install PHP on a Web server,

it will run under a default configuration

with respect to security, performance,

how it handles data, and so forth. One of

the default settings is to not display any

errors. In other words, the **display\_errors**

setting will be off **A**. When that’s the case,

what you might see when a script has an

error is a blank page. (This is the norm on

fresh installations of PHP; most hosting

companies will enable **display\_errors**.)

The reason that errors should not be

displayed on a live site is that it’s a security

risk. Simply put, PHP’s errors often give away

too much information for the public at large to

see (not to mention showing PHP errors looks

unprofessional). But you, the developer, do

need to see these errors in order to fix them!

To have PHP display errors, you can do

one of the following:

■

Turn **display\_errors** back on for PHP

as a whole. (See the “Configuring PHP”

section of Appendix A, “Installation and

Configuration,” for more information.)

■

Turn **display\_errors** back on for an

individual script.

continues on next page

**A** Run a **phpinfo()**

script (e.g., Script 1.2)

to view your server’s

**display\_errors**

setting.

HTML Forms and PHP 61

While developing a site, the first option is by

**Script 3.4** This addition to the PHP script turns on

far preferred. However, it’s only a possibility

the **display\_errors** directive so that errors will

be shown.

for those with administrative control over

the server. Anyone can use the second

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

option by including this line in a script:

1.0

Transitional//EN"

2 "http://www.w3.org/TR/xhtml1/DTD/

**ini\_set ('display\_errors', 1);**

xhtml1-transitional.dtd">

3 <html

xmlns="http://www.w3.org/1999/

The **ini\_set()** function allows a script

xhtml" xml:lang="en" lang="en">

to temporarily override a setting in PHP’s

4 <head>

configuration file (many, but not all, settings

5

<meta http-equiv="Content-Type"

can be altered this way). The previous

content="text/html;

charset=utf-8"/>

example changes the **display\_errors**

6 <title>Your

Feedback</title>

7 </head>

setting to on, which is represented by

8 <body>

the number 1.

9

<?php // Script 3.4 - handle\_form.php #2

Although this second method can be

10

**11 ini\_set ('display\_errors', 1);**

implemented by anyone, the downside is

**// Let me learn from my mistakes!**

that if your script contains certain kinds of

12

errors (discussed next), the script cannot

13 // This page receives the data from

be executed. In that situation, this line of

feedback.html.

code won’t be executed, and the particular

14 // It will receive: title, name, email,

response, comments, and submit in

error—or any that prevents a script from

$\_POST.

running at all—still results in a blank page.

15

16 // Create shorthand versions of the

**To display errors in a script:**

variables:

17 $title = $\_POST\['title'\];

**1.** Open **handle\_form.php** in your text

18 $name = $\_POST\['name'\];

editor or IDE, if it is not already open.

19 $response = $\_POST\['response'\];

20 $comments = $\_POST\['comments'\];

**2.** As the first line of PHP code, enter the

21

following (**Script 3.4**):

22 // Print the received data:

**ini\_set ('display\_errors', 1);**

23 print "<p>Thank you, $title $name, for

your

comments.</p>

Again, this line tells PHP you’d like to

24 <p>You stated that you found this

see any errors that occur. You should

example to be '$response' and added:

<br

/>$comments</p>";

call it first thing in your PHP section so

25

the rest of the PHP code will abide by

26 ?>

this new setting.

27 </body>

28 </html>

**3.** Save the file as **handle\_form.php**.

62 Chapter

3

![Image 102](index-84_1.png)

![Image 103](index-84_2.png)

**4.** Upload the file to your Web server and

test it in your Web browser ( **B** and **C**).

If the resulting page has no errors in it,

then the script will run as it did before.

If you saw a blank page when you ran

the form earlier, you should now see

messages like those in **C**. Again, if you

see such errors, you likely misspelled

the name of a form element, misspelled

the index in the **$\_POST** array, or didn’t

fill out the form completely.

**B** Incompletely filling out the form…

**Make sure display\_errors is enabled**

**any time you’re having difficulties debugging**

**a script. If you installed PHP on your computer,**

**I highly recommend enabling it in your PHP**

**configuration while you learn (again, see**

**Appendix A).**

**C** …results in error messages. These notices are

**If you see a blank page when running a**

generated by references to form elements for

**PHP script, also check the HTML source code**

which there are no values.

**for errors or other problems.**

**Remember that the display\_errors**

**directive only controls whether error mes-**

**sages are sent to the Web browser. It doesn’t**

**create errors or prevent them from occurring**

**in any way.**

**Failure to use an equals sign after name**

**in a form element will also cause problems:**

**<input name"something" />**

HTML Forms and PHP 63

[**Error Reporting**](#index_split_000.html#p6)

the **error\_reporting** level in PHP’s

configuration file (again, see Appendix A).

Another PHP configuration issue you should

If you are running your own PHP server,

be aware of, along with **display\_errors**,

you’ll probably want to adjust that global

is error reporting. There are eleven

setting while developing your scripts.

different types of errors in PHP, plus four

The second option is to use the **error\_**

user-defined types (which aren’t covered

**reporting()** function in a script. The

in this book). **Table 3.1** lists the four most

function takes either a number or one

important general error types, along with

or more constants (nonquoted strings

a description and example of each.

with predetermined meanings) to adjust

You can set what errors PHP reports

the levels. The most important of these

on in two ways. First, you can adjust

constants are listed in **Table 3.2**.

**TABLE 3.1 PHP Error Types**

**Type**

**Description**

**Example**

Notice

Nonfatal error that may or may not be

Referring to a variable that has no value

indicative of a problem

Warning

Nonfatal error that is most likely problematic

Misusing a function

Parse error

Fatal error caused by a syntactical mistake

Omission of a semicolon or an imbalance

of quotation marks, braces, or parentheses

Error

A general fatal error

Memory allocation problem

**TABLE 3.2 Error Reporting Constants**

**Name**

**E\_NOTICE**

**E\_WARNING**

**E\_PARSE**

**E\_ERROR**

**E\_ALL**

**E\_STRICT**

**E\_DEPRECATED**

64 Chapter

3

**Script 3.5** Adjust a script's level of error reporting Using this information, you could add any

to give you more or less feedback on potential

of the following to a script:

and existing problems. In my opinion, more is

always better.

**error\_reporting (0);**

**error\_reporting (E\_ALL);**

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

**error\_reporting (E\_ALL & ~E\_NOTICE);**

1.0

Transitional//EN"

2 "http://www.w3.org/TR/xhtml1/DTD/

The first line says that no errors should

xhtml1-transitional.dtd">

be reported. The second requests that all

3 <html

xmlns="http://www.w3.org/1999/

errors be reported. The last example states

xhtml" xml:lang="en" lang="en">

4 <head>

that you want to see all error messages

5

<meta http-equiv="Content-Type"

except notices (the **& ~** means and not).

content="text/html;

charset=utf-8"/>

Keep in mind that adjusting this setting

6 <title>Your

Feedback</title>

doesn’t prevent or create errors; it just

7 </head>

affects whether or not errors are reported.

8 <body>

9

<?php // Script 3.5 - handle\_form.php #3

It’s generally best to develop and test PHP

10

scripts using the highest level of error

11 ini\_set ('display\_errors', 1);

reporting possible. To accomplish that,

// Let me learn from my mistakes!

**12 error\_reporting (E\_ALL | E\_STRICT);**

declare that you want all errors plus strict

**// Show all possible problems!**

error reporting:

13

**error\_reporting (E\_ALL | E\_STRICT);**

14 // This page receives the data from

feedback.html.

The **E\_ALL** setting does not include

15 // It will receive: title, name, email,

**E\_STRICT**, which is why that line says that

response, comments, and submit in

all errors should be shown or (the vertical

$\_POST.

16

bar, called the pipe) strict errors should

17 // Create shorthand versions of the

be shown. This latter setting takes reporting

variables:

a step further, also raising notices for

18 $title = $\_POST\['title'\];

things that could be a problem in future

19 $name = $\_POST\['name'\];

versions of PHP. Let’s apply this setting to

20 $response = $\_POST\['response'\];

21 $comments = $\_POST\['comments'\];

the **handle\_form.php** page.

22

23 // Print the received data:

**To adjust error reporting in a script:**

24 print "<p>Thank you, $title $name, for

your

comments.</p>

**1.** Open **handle\_form.php** (Script 3.4)

25 <p>You stated that you found this

in your text editor or IDE, if it is not

example to be '$response' and added:

already.

<br

/>$comments</p>";

26

**2.** After the **ini\_set()** line, add the follow-

27 ?>

ing (**Script 3.5**):

28 </body>

29 </html>

**error\_reporting (E\_ALL | E\_STRICT);**

**3.** Save the file as **handle\_form.php**.

continues on next page

HTML Forms and PHP 65

![Image 104](index-87_1.png)

![Image 105](index-87_2.png)

**4.** Place the file in the proper directory for

your PHP-enabled server and test it in

your Web browser by submitting the

form ( **A** and **B** ).

At this point, if the form is filled out

completely and the **$\_POST** indexes

exactly match the names of the form

elements, you shouldn’t see any errors

(as in the figures). If any problems

exist, including any potential problems

(thanks to **E\_STRICT**), they should be

displayed and reported.

**A** Try the form one more time…

**The PHP manual lists all the error-**

**reporting levels, but those listed here are**

**the most important.**

**The code in this book was tested**

**B** …and here’s the result (if filled out completely

**using the highest level of error reporting:**

and without any programmer errors).

**E\_ALL | E\_STRICT.**

66 Chapter

3

[**Manually Sending**](#index_split_000.html#p6)

[**Data to a Page**](#index_split_000.html#p6)

The last example for this chapter is a slight

tangent to the other topics but plays off

the idea of handling form data with PHP. As

discussed in the section “Choosing a Form

Method,” if a form uses the GET method,

the resulting URL is something like

[**http://www.example.com/page.php?**](http://www.example.com/page.php?)

➝ **some\_var=some\_value&age=20&...**

The receiving page (here, **page.php**) is

sent a series of name=value pairs, each

of which is separated by an ampersand

(**&** ). The whole sequence is preceded by

a question mark (immediately after the

handling script’s name).

To access the values passed to the page

in this way, turn to the **$\_GET** variable. Just

as you would when using **$\_POST**, refer to

the specific name as an index in **$\_GET**.

In that example, **page.php** receives a

**$\_GET\['some\_var'\]** variable with a value of

some\_value, a **$\_GET\['age'\]** variable with

a value of 20, and so forth.

You can pass data to a PHP script in this

way by creating an HTML form that uses

the GET method. But you can also use this

same idea to send data to a PHP page

without the use of the form. Normally you’d

do so by creating links:

**<a href="page.php?id=22">Some Link</a>**

That link, which could be dynamically

generated by PHP, will pass the value 22

to **page.php**, accessible in **$\_GET\['id'\]**.

To try this for yourself, the next pair of

scripts will easily demonstrate this concept,

using a hard-coded HTML page.

HTML Forms and PHP 67

**To create the HTML page:**

**Script 3.6** This HTML page uses links to pass

values to a PHP script in the URL (thereby

**1.** Begin a new document in your text

emulating a form that uses the GET method).

editor or IDE, to be named **hello.html**

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

(**Script 3.6**):

1.0

Transitional//EN"

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

2 "http://www.w3.org/TR/xhtml1/DTD/

➝ **XHTML 1.0 Transitional//EN"**

xhtml1-transitional.dtd">

3 <html

xmlns="http://www.w3.org/1999/

**"http://www.w3.org/TR/xhtml1/**

xhtml" xml:lang="en" lang="en">

 ➝ **DTD/xhtml1-transitional.dtd">**

4 <head>

**<html xmlns="http://www.w3.org/**

5

<meta http-equiv="Content-Type"

➝ **1999/xhtml" xml:lang="en"**

content="text/html;

charset=utf-8"/>

➝ **lang="en">**

6 <title>Greetings!</title>

7 </head>

**<head>**

8 <body>

**<meta**

**http-equiv="Content-Type"**

9

<!-- Script 3.6 - hello.html -->

 ➝ **content="text/html;**

10 <div><p>Click a link to say hello:</p>

 ➝ **charset=utf-8"/>**

11

**<title>Greetings!</title>**

12 <ul>

**13 <li><a**

**href="hello.php?**

**</head>**

**name=Michael">Michael</a></li>**

**<body>**

**14 <li><a**

**href="hello.php?**

**<!-- Script 3.6 - hello.html -->**

**name=Celia">Celia</a></li>**

**<div><p>Click a link to say**

**15 <li><a**

**href="hello.php?**

➝ **hello:</p>**

**name=Jude">Jude</a></li>**

**16 <li><a**

**href="hello.php?**

**2.** Create links to a PHP script, passing

**name=Sophie">Sophie</a></li>**

values along in the URL:

17 </ul>

18

**<ul>**

19 </div>

**<li><a**

**href="hello.php?**

20 </body>

 ➝ **name=Michael">Michael</a></li>** 21 </html>

**<li><a**

**href="hello.php?**

 ➝ **name=Celia">Celia</a></li>**

**<li><a**

**href="hello.php?**

 ➝ **name=Jude">Jude</a></li>**

**<li><a**

**href="hello.php?**

 ➝ **name=Sophie">Sophie</a></li>**

**</ul>**

68 Chapter

3

![Image 106](index-90_1.png)

![Image 107](index-90_2.png)

The premise here is that the user will

see a list of links, each associated with

a specific name **A**. When the user

clicks a link, that name is passed to

**hello.php** in the URL **B**.

If you want to use different names,

that’s fine, but stick to one-word names

**A** The simple HTML page, with

without spaces or punctuation (or

four links to the PHP script.

else they won’t be passed to the PHP

script properly, for reasons that will be

explained in time).

**3.** Complete the HTML page:

**</div>**

**</body>**

**</html>**

**4.** Save the script as **hello.html** and

place it within the proper directory

on your PHP-enabled server.

**5.** Load the HTML page through a URL

in your Web browser.

Although you can view HTML pages

without going through a URL, you’ll click

links in this page to access the PHP

script, so you’ll need to start off using

a URL here. Don’t click any of the links

yet, as the PHP script doesn’t exist!

**B** The HTML source of the page shows how values are being passed along in the URL for the four links.

HTML Forms and PHP 69

**To create the PHP script:**

**Script 3.7** This PHP page refers to the **name** value

passed in the URL in order to print a greeting.

**1.** Begin a new document in your text

editor or IDE, to be named **hello.php**

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

1.0

Transitional//EN"

(**Script 3.7**):

2 "http://www.w3.org/TR/xhtml1/DTD/

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

xhtml1-transitional.dtd">

➝ **XHTML 1.0 Transitional//EN"**

3 <html

xmlns="http://www.w3.org/1999/

xhtml" xml:lang="en" lang="en">

**"http://www.w3.org/TR/xhtml1/**

4 <head>

 ➝ **DTD/xhtml1-transitional.dtd">**

5

<meta http-equiv="Content-Type"

**<html xmlns="http://www.w3.org/**

content="text/html;

charset=utf-8"/>

➝ **1999/xhtml" xml:lang="en"**

6 <title>Greetings!</title>

➝ **lang="en">**

7 </head>

8 <body>

**<head>**

9

<?php // Script 3.7 - hello.php

**<meta**

**http-equiv="Content-Type"**

10

 ➝ **content="text/html;**

11 ini\_set ('display\_errors', 1);

 ➝ **charset=utf-8"/>**

// Let me learn from my mistakes!

**<title>Greetings!</title>**

12 error\_reporting (E\_ALL | E\_STRICT);

// Show all possible problems!

**</head>**

13

**<body>**

14 // This page should receive a name value

**2.** Begin the PHP code:

in the URL.

15

**<?php // Script 3.7 - hello.php**

16 // Say "Hello":

**17 $name = $\_GET\['name'\];**

**3.** Address the error management, if desired:

**18 print "<p>Hello, <span**

**ini\_set ('display\_errors', 1);**

**style=\\"font-weight:**

**bold;\\">$name**

**error\_reporting (E\_ALL | E\_STRICT);**

**</span>!</p>";**

19

These two lines, which configure how

20 ?>

PHP responds to errors, are explained

21 </body>

in the pages leading up to this section.

22 </html>

They may or may not be necessary for

your situation but can be helpful.

**4.** Use the **name** value passed in the URL

to create a greeting:

**$name = $\_GET\['name'\];**

**print "<p>Hello, <span**

**style=\\"font-weight:**

**bold;\\">$name</span>!</p>";**

The **name** variable is sent to the page

through the URL (see Script 3.6). To

access that value, refer to **$\_GET\['name'\]**.

Again, you would use **$\_GET** (as opposed

to **$\_POST**) because the value is coming

from a GET request.

70 Chapter

3

![Image 108](index-92_1.png)

![Image 109](index-92_2.png)

![Image 110](index-92_3.png)

![Image 111](index-92_4.png)

As with earlier PHP scripts, the value in

the predefined variable (**$\_GET**) is first

assigned to another variable, to simplify

the syntax in the **print** statement.

**5.** Complete the PHP code and the

**C** By clicking the first link, Michael is passed

along in the URL and is greeted by name.

HTML page:

**?>**

**</body>**

**</html>**

**6.** Save the script as **hello.php** and place

it within the proper directory on your

**D** By clicking the second link, Celia is sent along

in the URL and is also greeted by name.

PHP-enabled server.

It should be saved in the same directory

as **hello.html** (Script 3.6).

**7.** Click the links in **hello.html** to view

the result **C** and **D**.

**If you run hello.php directly (i.e.,**

**without clicking any links), you’ll get an error**

**E** If the **$\_GET\['name'\]** variable isn’t assigned

**notice because no name value would be**

a value, the browser prints out this awkward

**passed along in the URL**

message, along with the error notice.

**E.**

**Because hello.php reads a value from**

**the URL, it actually works independently of**

**hello.html. For example, you can directly**

**edit the hello.php URL to greet anyone, even**

**if hello.html does not have a link for that**

**name F.**

**F** Any value assigned to **name** (lowercase) in the

URL is used by the PHP script.

**If you want to use a link to send multiple**

**values to a script, separate the name=value**

**pairs (for example, first\_name=Larry) with**

**the ampersand (&). So, another link may be**

**hello.php? first\_name=Larry&last\_**

**name=Ullman. You should continue to use**

**only single words, without punctuation or**

**spaces, however (until you later learn about**

**the urlencode() function).**

**Although the example here—setting the**

**value of a person’s name—may not be very**

**practical, this basic technique is useful on**

**many occasions. For example, a PHP script**

**might constitute a template, and the content**

**of the resulting Web page would differ based**

**on the values the page received in the URL.**

HTML Forms and PHP 71

[**Review and Pursue**](#index_split_000.html#p6)

■

If you have not already, and if you

can, make sure that **display\_errors**

If you have any problems with the review

is enabled on your development

questions or the pursue prompts, turn

environment.

to the book’[s supporting forum (www.](http://www.LarryUllman.com/forum/)

■

If you have not already, and if you

[LarryUllman.com/forum/ ).](http://www.LarryUllman.com/forum/)

can, make sure that **error\_reporting**

is set to **E\_ALL | E\_STRICT** on your

**Review**

development environment.

■

What is the significance of a form’s

■

Try introducing different errors in a PHP

**action** attribute?

script—by improperly balancing quotation

marks, failing to use semicolons, referring

■

What is the significance of a form’s

to variables improperly, and so on—to

**method** attribute? Is it more secure to

see the result.

use GET or POST? Which method type

can be bookmarked in the browser?

■

Experiment with the **hello.html** and

the **hello.php** pages to send different

■

What predefined variable will contain

values, including numbers, to the PHP

the data from a form submission? Note:

script through the URL.

There are multiple answers.

■

Create a variation on **hello.html** that

■

Why must an HTML page that contains

sends multiple name=value pairs to a

a form that’s being submitted to a PHP

PHP script. Have the PHP script then

script be loaded through a URL?

print all the received values.

■

Under what circumstances will attempts

■

If you’re the inquisitive type, and don’t

to enable **display\_errors** in a script

mind waiting for answers, try passing

not succeed? Why is it not secure to

more complicated values to a page

enable **display\_errors** on live sites?

through the URL. Try using spaces and

punctuation to see what happens.

**Pursue**

■

Create a new HTML form that performs

■

Load **feedback.html** in your Web

a task you envision yourself needing

browser without going through a URL

(or a lighter-weight version of that

(i.e., the address bar would likely start

functionality). Then create the PHP

with file:// ). Fill out and submit the form.

script that handles the form, printing

Observe the result so that you can

just the received data.

recognize this problem, and understand

its cause, in case you see similar results

in the future.

72 Chapter

3

[**4**](#index_split_000.html#p7)

[Using Numbers](#index_split_000.html#p7)

Chapter 2, “Variables,” briefly discussed

the various types of variables, how to

**In This Chapter**

assign values to them, and how they’re

generally used. In this chapter, you’ll work

Creating the Form

74

specifically with number variables—both

Performing Arithmetic

77

integers (whole numbers) and floating-

Formatting Numbers

81

point numbers (aka floats or decimals).

Understanding Precedence

84

The chapter begins by creating an HTML

form that will be used to generate number

Incrementing and Decrementing

variables. Then you’ll learn how to perform

a Number

86

basic arithmetic, how to format numbers, and

Creating Random Numbers

88

how to cope with operator precedence. The

Review and Pursue

90

last two sections of this chapter cover incre-

menting and decrementing numbers, plus

generating random numbers. Throughout the

chapter, you’ll also learn about other useful

number-related PHP functions.

![Image 112](index-95_1.png)

![Image 113](index-95_2.png)

[**Creating the Form**](#index_split_000.html#p7)

Most of the PHP examples in this chapter

will perform various calculations based on

an e-commerce premise. A form will take

price, quantity, discount amount, tax rate,

and shipping cost **A**, and the PHP script

that handles the form will return a total

cost. That cost will also be broken down

by the number of payments the user wants

to make in order to generate a monthly

cost value **B**.

**A** This form takes numbers from

To start, let’s create an HTML page that

the user and sends them to a

allows the user to enter the values.

PHP page.

**To create the HTML form:**

**1.** Begin a new HTML document in

your text editor or IDE, to be named

**calculator.html** (**Script 4.1**):

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

➝ **XHTML 1.0 Transitional//EN"**

**"http://www.w3.org/TR/xhtml1/DTD/**

**B** The PHP script performs a series of calculations

 ➝ **xhtml1-transitional.dtd">**

on the submitted data and outputs the results. The

results should look like this by the end of the chapter.

**<html xmlns="http://www.w3.org/**

 ➝ **1999/xhtml" xml:lang="en"**

 ➝ **lang="en">**

**<head>**

**<meta**

**http-equiv="Content-Type"**

 ➝ **content="text/html;**

 ➝ **charset=utf-8"/>**

**<title>Product Cost Calculator**

 ➝ **</title>**

**</head>**

**<body><!-- Script 4.1 -**

➝ **calculator.html -->**

**<div><p>Fill out this form to**

➝ **calculate the total cost:</p>**

74 Chapter

4

**Script 4.1** This basic HTML form will be the **2.** Create the initial **form** tag:

origination of the numbers on which mathematical

calculations will be performed in several PHP scripts.

**<form action="handle\_calc.php"**

➝ **method="post">**

1

<!DOCTYPE html PUBLIC "-//W3C//DTD

XHTML 1.0 Transitional//EN"

This **form** tag begins the HTML form. Its

2 "http://www.w3.org/TR/xhtml1/DTD/

**action** attribute indicates that the form

xhtml1-transitional.dtd">

data will be submitted to a page named

3 <html

xmlns="http://www.w3.org/1999/

xhtml" xml:lang="en" lang="en">

**handle\_calc.php**. The tag’s **method**

4 <head>

attribute tells the page to use POST to

5

<meta http-equiv="Content-Type"

send the data. See Chapter 3, “HTML

content="text/html;

charset=utf-8"/>

Forms and PHP,” for more details.

6

<title>Product Cost Calculator

</title>

**3.** Create the inputs for the price, quantity,

7 </head>

discount, and tax:

8

<body><!-- Script 4.1 -

calculator.html

\-->

**<p>Price: <input type="text"**

9

<div><p>Fill out this form to

➝ **name="price" size="5" /></p>**

calculate the total cost:</p>

**<p>Quantity: <input type="text"**

10

11 <form action="handle\_calc.php"

➝ **name="quantity" size="5" /></p>** method="post">

**<p>Discount: <input type="text"**

12

➝ **name="discount" size="5" /></p>** 13 <p>Price: <input type="text"

name="price" size="5" /></p>

**<p>Tax: <input type="text"**

14

➝ **name="tax" size="3" /> (%)</p>** 15 <p>Quantity: <input type="text"

name="quantity" size="5" /></p>

XHTML has no input type for numbers,

16

so you create text boxes for these

17 <p>Discount: <input type="text"

values. A parenthetical indicates that

name="discount" size="5" /></p>

18

the tax should be entered as a percent.

19 <p>Tax: <input type="text" name="tax"

size="3" /> (%)</p>

Also remember that the names used for

20

the inputs have to correspond to valid

21 <p>Shipping method: <select

PHP variable names (letters, numbers,

name="shipping">

22 <option value="5.00">Slow and steady

and the underscore only; doesn’t start

</option>

with a number, and so forth).

23 <option value="8.95">Put a move on

it.</option>

continues on next page

24 <option value="19.36">I need it

yesterday!</option>

25 </select></p>

26

27 <p>Number of payments to make:

<input type="text" name="payments"

size="3"

/></p>

28

29 <input type="submit" name="submit"

value="Calculate!"

/>

30

31 </form>

32

33 </div>

34 </body>

35 </html>

Using Numbers 75

**4.** Add a field in which the user can select a shipping method:

**<p>Shipping method: <select**

➝ **name="shipping">**

**<option value="5.00">Slow and**

➝ **steady</option>**

**<option value="8.95">Put a move**

➝ **on it.</option>**

**<option value="19.36">I need it**

➝ **yesterday!</option>**

**</select></p>**

The shipping selection is made using

a drop-down menu. The value of the

selected option is the cost for that option.

If the user selects, for example, the

Put a move on it. option, the value of

**$\_POST\['shipping'\]** in **handle\_calc.php**

will be 8.95.

**5.** Complete the HTML form:

**<p>Number of payments to make:**

➝ **<input type="text"**

➝ **name="payments" size="3" /></p>**

**<input type="submit" name="submit"**

➝ **value="Calculate!" />**

**</form>**

The final two input types take a number

for how many payments are required

and then create a submit button (labeled

Calculate!). The closing **form** tag marks

the end of the form section of the page.

**6.** Complete the HTML page:

**</div>**

**</body>**

**</html>**

**7.** Save the script as **calculator.html**

and view it in your Web browser.

Because this is an HTML page, you can

view it directly in a Web browser.

76 Chapter

4

**Script 4.2** This PHP script executes all the standard mathematical calculations using

[**Performing Arithmetic**](#index_split_000.html#p7)

the numbers submitted from the form.

Just as you learned in grade school, basic

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

mathematics involves the principles of

1.0

Transitional//EN"

addition, subtraction, multiplication, and

2 "http://www.w3.org/TR/xhtml1/DTD/

division. These are performed in PHP using

xhtml1-transitional.dtd">

the most obvious operators:

3 <html

xmlns="http://www.w3.org/1999/

xhtml" xml:lang="en" lang="en">

■

Addition (**+**)

4 <head>

■

5

<meta http-equiv="Content-Type"

Subtraction (**\-**)

content="text/html;

charset=utf-8"/>

■

Multiplication (**\***)

6

<title>Product Cost Calculator</title>

7

<style type="text/css" media="screen">

■

Division (**/**)

8

.number { font-weight: bold; }

To use these operators, you’ll create a PHP

9 </style>

10 </head>

script that calculates the total cost for the sale

11 <body>

of some widgets. This handling script could

12 <?php // Script 4.2 - handle\_calc.php

be the basis of a shopping cart application—

13 /\* This script takes values from

a very practical Web page feature (although

calculator.html and performs

in this case the relevant number values will

14 total cost and monthly payment

calculations.

\*/

come from **calculator.html**).

15

When you’re writing this script, be sure to

16 // Address error handling, if you want.

note the use of comments (**Script 4.2**) to

17

18 // Get the values from the $\_POST array:

illuminate the different lines of code and

**19 $price = $\_POST\['price'\];**

the reasoning behind them.

**20 $quantity = $\_POST\['quantity'\];**

**21 $discount = $\_POST\['discount'\];**

**To create your sales cost calculator:**

**22 $tax = $\_POST\['tax'\];**

**23 $shipping = $\_POST\['shipping'\];**

**1.** Create a new document in your text

**24 $payments = $\_POST\['payments'\];**

editor or IDE, to be named **handle\_**

25

**calc.php** (Script 4.2):

26 // Calculate the total:

**27 $total = $price \* $quantity;**

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

**28 $total = $total + $shipping;**

➝ **XHTML 1.0 Transitional//EN"**

**29 $total = $total - $discount;**

**"http://www.w3.org/TR/xhtml1/DTD/**

30

31 // Determine the tax rate:

➝ **xhtml1-transitional.dtd">**

**32 $taxrate = $tax/100;**

**<html xmlns="http://www.w3.org/**

**33 $taxrate = $taxrate + 1;**

➝ **1999/xhtml" xml:lang="en"**

34

➝ **lang="en">**

35 // Factor in the tax rate:

**<head>**

**36 $total = $total \* $taxrate;**

37

**<meta**

**http-equiv="Content-Type"**

38 // Calculate the monthly payments:

 ➝ **content="text/html;**

**39 $monthly = $total / $payments;**

 ➝ **charset=utf-8"/>**

40

**<title>Product Cost Calculator**

code continues on next page

➝ **</title>**

continues on next page

Using Numbers 77

 **<style type="text/css"**

**Script 4.2** continued

 ➝ **media="screen">**

41 // Print out the results:

**.number { font-weight: bold; }**

**42 print "<p>You have selected to**

**</style>**

**purchase:<br**

**/>**

**</head>**

**43 <span**

**class=\\"number\\">$quantity**

**<body>**

**</span> widget(s) at <br />**

**44 $<span**

**class=\\"number\\">$price</span>**

The head of the document defines one

**price each plus a <br />**

CSS class called ***number***. Any element

**45 $<span**

**class=\\"number\\">$shipping**

within the page that has that class

**</span> shipping cost and a <br />**

value will be given extra font weight. In

**46 <span class=\\"number\\">$tax</span>**

**percent tax rate.<br />**

other words, when the numbers from

**47 After your $<span class=\\"number\\">**

the form, and the results of the various

**$discount</span> discount, the total**

calculations, are printed in the script’s

**cost**

**is**

output, they’ll be made more obvious.

**48 $<span**

**class=\\"number\\">$total**

**</span>.<br**

**/>**

**2.** Insert the PHP tags and address error

**49 Divided over <span class=\\"number\\">**

handling, if desired:

**$payments</span> monthly payments,**

**that would be $<span class=\\"number\\">**

**<?php // Script 4.2 -**

**$monthly</span>**

**each.</p>";**

➝ **handle\_calc.php**

50

Depending on your PHP configuration,

51 ?>

52 </body>

you may or many not want to add a

53 </html>

couple of lines that turn on **display\_**

**errors** and adjust the level of error

reporting. See Chapter 3 for specifics.

**3.** Assign the **$\_POST** elements to local

variables:

**$price = $\_POST\['price'\];**

**$quantity = $\_POST\['quantity'\];**

**$discount = $\_POST\['discount'\];**

**$tax = $\_POST\['tax'\];**

**$shipping = $\_POST\['shipping'\];**

**$payments = $\_POST\['payments'\];**

The script will receive all the form data

in the predefined **$\_POST** variable. To

access individual form values, refer to

**$\_POST\[' *index*'\]**, replacing index with the corresponding form element’s **name** value.

These values are assigned to individual

local variables here, to make it easier to

use them throughout the rest of the script.

Note that each variable is given a

descriptive name and is written entirely

in lowercase letters.

78 Chapter

4

**4.** Begin calculating the total cost:

**7.** Print the results:

**$total = $price \* $quantity;**

**print "<p>You have selected to**

**$total = $total + $shipping;**

➝ **purchase:<br />**

**$total = $total - $discount;**

**<span class=\\"number\\">$quantity**

The asterisk (**\***) indicates multiplication

➝ **</span> widget(s) at <br />**

in PHP, so the total is first calculated

**$<span class=\\"number\\">$price**

as the number of items purchased

➝ **</span> price each plus a <br />**

(**$quantity**) multiplied by the price. Then

**$<span class=\\"number\\">$shipping**

the shipping cost is added to the total

➝ **</span> shipping cost and a <br />**

value (remember that the shipping cost

**<span class=\\"number\\">$tax</span>**

correlates to the **value** attribute of each

➝ **percent tax rate.<br />**

shipping drop-down menu’s **option**

**After your $<span class=\\"number\\">**

tags), and the discount is subtracted.

➝ **$discount</span> discount, the**

Note that it’s perfectly acceptable to

➝ **total cost is**

determine a variable’s value in part by

**$<span class=\\"number\\">$total**

using that variable’s existing value (as is

➝ **</span>.<br />**

done in the last two lines).

**Divided over <span class=\\"number\\">**

➝ **$payments</span> monthly**

**5.** Calculate the tax rate and the new total:

➝ **payments, that would be $<span**

**$taxrate = $tax/100;**

➝ **class=\\"number\\">$monthly</span>**

**$taxrate = $taxrate + 1;**

➝ **each.</p>";**

**$total = $total \* $taxrate;**

The **print** statement sends every value

The tax rate should be entered as a

to the Web browser along with some

percent—for example, 8 or 5.75. This

text. To make it easier to read, **<br />**

number is then divided by 100 to get the

tags are added to format the browser

decimal equivalent of the percent (.08 or

result; in addition, the **print** function

.0575). Finally, you calculate how much

operates over multiple lines to make the

something costs with tax by adding

PHP code cleaner. Each variable’s value

1 to the percent and then multiplying

will be highlighted in the browser by

that new rate by the total. This is the

wrapping it within **span** tags that have a

mathematical equivalent of multiplying

**class** attribute of ***number*** (see Step 1).

the decimal tax rate times the total and

**8.** Close the PHP section and complete

then adding this result to the total (for

the HTML page:

example, a 5 percent tax on $100 is $5,

making the total $105, which is the same

**?>**

as multiplying $100 times 1.05).

**</body>**

**</html>**

**6.** Calculate the monthly payment:

**$monthly = $total / $payments;**

**9.** Save the script as **handle\_calc.php**

and place it in the proper directory for

As an example of division, assume

your PHP-enabled server.

that the widgets can be paid for over

Make sure that **calculator.html** is in

the course of many months. Hence,

the same directory.

you divide the total by the number of

payments to find the monthly payment.

continues on next page

Using Numbers 79

![Image 114](index-101_1.png)

![Image 115](index-101_2.png)

![Image 116](index-101_3.png)

**10.** Test the script in your Web browser

by filling out **A** and submitting **B**

the form.

Not to belabor the point, but make sure

you start by loading the HTML form

through a URL (http://something) so

that when it’s submitted, the PHP script

is also run through a URL.

You can experiment with these values

to see how effectively your calculator

works. If you omit any values, the

**A** The HTML form…

resulting message will just be a little odd

but the calculations should still work **C**.

**As you’ll certainly notice, the calculator**

**comes up with numbers that don’t correspond**

**well to real dollar values (see B and C). In**

**the next section, “Formatting Numbers,” you’ll**

**learn how to address this issue.**

**B** …and the resulting calculations.

**If you want to print the value of the total**

**before tax or before the discount (or both),**

**you can do so in two ways. You can insert the**

**appropriate print statements immediately**

**after the proper value has been determined**

**but before the $total variable has been**

**changed again. Or, you can use new variables**

**to represent the values of the subsequent**

**calculations (for example, $total\_with\_tax**

**C** You can omit or change any value and rerun

**and $total\_less\_discount).**

the calculator. Here the tax and discount values

have been omitted.

**Attempting to print a dollar sign followed**

**by the value of a variable, such as $10 (where**

**10 comes from a variable), has to be handled**

**carefully. You can’t use the syntax $$variable,**

**because the combination of two dollar signs**

**creates a type of variable that’s too complex**

**This script performs differently, depend-**

**to discuss in this book. One solution is to put**

**ing on whether the various fields are sub-**

**something—a space or an HTML tag, as in this**

**mitted. The only truly problematic field is**

**example—between the dollar sign and the vari-**

**the number of monthly payments: If this is**

**able name. Another option is to escape the first**

**omitted, you’ll see a division-by-zero warning.**

**dollar sign:**

**Chapter 6, “Control Structures,” will cover**

**validating form data before it’s used.**

**print "The total is \\$$total";**

**HTML 5 is expected to have one or**

**A third option is to use concatenation, which is**

**more inputs that restrict the user to entering**

**introduced in the next chapter.**

**numeric values.**

80 Chapter

4

[**Formatting Numbers**](#index_split_000.html#p7)

Although the calculator is on its way to

being practical, it still has one legitimate

problem: You can’t ask someone to make

a monthly payment of $10.13183333! To

create more usable numbers, you need to

format them.

There are two appropriate functions for this

purpose. The first, **round()**, rounds a value

to a specified number of decimal places. The

function’s first argument is the number to

be rounded. This can be either a number

or a variable that has a numeric value. The

second argument is optional; it represents

the number of decimal places to which

to round. If omitted, the number will be

rounded to the nearest integer. For example:

**round (4.30); // 4**

**round (4.289, 2); // 4.29**

**$num = 236.26985;**

**round ($num); // 236**

The other function you can use in this

situation is **number\_format()**. It works

like **round()** in that it takes a number (or

a variable with a numeric value) and an

optional decimal specifier. This function has

the added benefit of formatting the number

with commas, the way it would commonly

be written:

**number\_format (428.4959, 2); // 428.50**

**number\_format (428, 2); // 428.00**

**number\_format (123456789);**

➝ **// 123,456,789**

Let’s rewrite the PHP script to format the

numbers appropriately.

Using Numbers 81

**To format numbers:**

**Script 4.3** The **number\_format()** function is

applied to the values of two number variables,

**1.** Open **handle\_calc.php** in your text

so they are more appropriate.

editor or IDE, if it is not already open

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

(Script 4.2).

1.0

Transitional//EN"

**2.** After all the calculations but before the

2 "http://www.w3.org/TR/xhtml1/DTD/

xhtml1-transitional.dtd">

**print** statement, add the following

3 <html

xmlns="http://www.w3.org/1999/

(**Script 4.3**):

xhtml" xml:lang="en" lang="en">

**$total = number\_format ($total, 2);**

4 <head>

5

<meta http-equiv="Content-Type"

**$monthly = number\_format**

content="text/html;

charset=utf-8"/>

➝ **($monthly, 2);**

6

<title>Product Cost Calculator</title>

7

<style type="text/css" media="screen"> To format these two numbers, apply

8

.number { font-weight: bold;}

this function after every calculation

9 </style>

has been made but before they’re

10 </head>

sent to the Web browser. The second

11 <body>

12 <?php // Script 4.3 - handle\_calc.php #2

argument (the 2) indicates that the

13 /\* This script takes values from

resulting number should have exactly

calculator.html and performs

two decimal places; this setting rounds

14 total cost and monthly payment

the numbers and adds zeros at the end,

calculations.

\*/

15

as necessary.

16 // Address error handling, if you want.

17

18 // Get the values from the $\_POST array:

19 $price = $\_POST\['price'\];

20 $quantity = $\_POST\['quantity'\];

21 $discount = $\_POST\['discount'\];

22 $tax = $\_POST\['tax'\];

23 $shipping = $\_POST\['shipping'\];

24 $payments = $\_POST\['payments'\];

25

26 // Calculate the total:

27 $total = $price \* $quantity;

28 $total = $total + $shipping;

29 $total = $total - $discount;

30

31 // Determine the tax rate:

32 $taxrate = $tax/100;

33 $taxrate = $taxrate + 1;

34

35 // Factor in the tax rate:

36 $total = $total \* $taxrate;

37

38 // Calculate the monthly payments:

39 $monthly = $total / $payments;

40

41 // Apply the proper formatting:

**42 $total = number\_format ($total, 2);**

**43 $monthly = number\_format ($monthly, 2);**

44

code continues on next page

82 Chapter

4

![Image 117](index-104_1.png)

![Image 118](index-104_2.png)

**Script 4.3** continued

**3.** Save the file, place it in the same direc-

tory as **calculator.html**, and test it in

45 // Print out the results:

your browser

46 print "<p>You have selected to

**A** and **B**.

purchase:<br

/>

47 <span class=\\"number\\">$quantity</span> **Another, much more complex way to**

widget(s) at <br />

**format numbers is to use the printf() and**

48 $<span class=\\"number\\">$price</span>

**sprintf() functions. Because of their tricky**

price each plus a <br />

**syntax, they’re not discussed in this book; see**

49 $<span

class=\\"number\\">$shipping</span>

**the PHP manual for more information.**

shipping cost and a <br />

50 <span

class=\\"number\\">$tax</span>

percent

**Non-Windows versions of PHP also have**

tax rate.<br />

**a money\_format() function, which can be**

51 After your $<span class=\\"number\\">

**used in lieu of**

$discount</span> discount, the total

**number\_format().**

cost

is

**For complicated reasons, the**

52 $<span class=\\"number\\">$total</span>.<br /> **round()**

**function rounds exact halves (.5, .05, .005,**

53 Divided over <span class=\\"number\\">

$payments</span> monthly payments, that

**and so on) down half the time and up half**

would be $<span class=\\"number\\">$monthly

**the time.**

</span>

each.</p>";

54

**In PHP, function calls can have spaces**

55 ?>

**between the function name and its parenthe-**

56 </body>

**ses or not. Both of these are fine:**

57 </html>

**round ($num);**

**round($num);**

**The number\_format() function takes**

**two other optional arguments that let you spec-**

**ify what characters to use to indicate a decimal**

**point and break up thousands. This is useful,**

**for example, for cultures that write 1,000.89 as**

**1.000,89. See the PHP manual for the correct**

**syntax, if you want to use this option.**

**A** Another

form entry.

**B** The updated version of the script returns more

appropriate number values thanks to the **number\_**

**format()** function.

Using Numbers 83

[**Understanding**](#index_split_000.html#p7)

**Script 4.4** By using parentheses, calculations

made over multiple lines (see Script 4.3) can

[**Precedence**](#index_split_000.html#p7)

be condensed without affecting the script’s

mathematical accuracy.

Inevitably, after a discussion of the various

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

sorts of mathematical operators comes the

1.0

Transitional//EN"

2 "http://www.w3.org/TR/xhtml1/DTD/

discussion of precedence. Precedence

xhtml1-transitional.dtd">

refers to the order in which a series of

3 <html

xmlns="http://www.w3.org/1999/

calculations are executed. For example,

xhtml" xml:lang="en" lang="en">

what is the value of the following variable?

4 <head>

5

<meta http-equiv="Content-Type"

**$number = 10 – 4 / 2;**

content="text/html;

charset=utf-8"/>

6

<title>Product Cost Calculator</title>

Is **$number** worth 3 (10 minus 4 equals 6,

7

<style type="text/css" media="screen"> divided by 2 equals 3) or 8 (4 divided by

8

.number { font-weight: bold;}

2 equals 2, subtracted from 10 equals 8)?

9 </style>

The answer here is 8, because division

10 </head>

takes precedence over subtraction.

11 <body>

12 <?php // Script 4.4 - handle\_calc.php #3

Appendix B, “Resources and Next Steps,”

13 /\* This script takes values from

shows the complete list of operator

calculator.html and performs

14 total cost and monthly payment

precedence for PHP (including operators

calculations.

\*/

that haven’t been covered yet). However,

15

instead of attempting to memorize a

16 // Address error handling, if you want.

large table of peculiar characters, you

17

can bypass the whole concept by using

18 // Get the values from the $\_POST array:

19 $price = $\_POST\['price'\];

parentheses. Parentheses always take

20 $quantity = $\_POST\['quantity'\];

precedence over any other operator.

21 $discount = $\_POST\['discount'\];

Thus:

22 $tax = $\_POST\['tax'\];

23 $shipping = $\_POST\['shipping'\];

**$number = (10 – 4) / 2; // 3**

24 $payments = $\_POST\['payments'\];

**$number = 10 – (4 / 2); // 8**

25

26 // Calculate the total:

Using parentheses in your calculations

**27 $total = (($price \* $quantity) +**

ensures that you never see peculiar results

**$shipping) - $discount;**

due to precedence issues. Parentheses

28

can also be used to rewrite complex

29 // Determine the tax rate:

**30 $taxrate = ($tax/100) + 1;**

calculations in fewer lines of code. Let’s

31

rewrite the **handle\_calc.php** script,

32 // Factor in the tax rate:

combining multiple lines into one by using

33 $total = $total \* $taxrate;

parentheses, while maintaining accuracy.

34

35 // Calculate the monthly payments:

36 $monthly = $total / $payments;

37

38 // Apply the proper formatting:

39 $total = number\_format ($total, 2);

40 $monthly = number\_format ($monthly, 2);

41

code continues on next page

84 Chapter

4

![Image 119](index-106_1.png)

![Image 120](index-106_2.png)

**Script 4.4** continued

**To manage precedence:**

42 // Print out the results:

**1.** Open **handle\_calc.php** in your text

43 print "<p>You have selected to

editor or IDE, if it is not already open

purchase:<br

/>

(Script 4.3).

44 <span class=\\"number\\">$quantity</span> widget(s) at <br />

**2.** Replace the three lines that initially cal-

45 $<span class=\\"number\\">$price</span>

culate the order total with the following

price each plus a <br />

(**Script 4.4**):

46 $<span

class=\\"number\\">$shipping</span>

shipping cost and a <br />

**$total = (($price \* $quantity) +**

47 <span

class=\\"number\\">$tax</span>

percent

➝ **$shipping) - $discount;**

tax rate.<br />

48 After your $<span class=\\"number\\">$discount There’s no reason not to make all the

</span> discount, the total cost is

calculations in one step, as long as

49 $<span class=\\"number\\">$total</span>.<br /> 50 Divided over <span class=\\"number\\">

you use parentheses to ensure that

$payments</span> monthly payments, that

the math works properly. The other

would be $<span class=\\"number\\">$monthly

option is to memorize PHP’s rules of

</span>

each.</p>";

precedence for multiple operators, but

51

52 ?>

using parentheses is a lot easier.

53 </body>

**3.** Change the two lines that calculate and

54 </html>

add in the tax to this:

**$taxrate = ($tax/100) + 1;**

Again, the tax calculations can be made

in one line instead of two separate ones.

**4.** Save the script, place it in the same

directory as **calculator.html**, and test

it in your browser **A** and **B**.

**Be sure that you match your parentheses**

**consistently as you create your formulas**

**(every opening parenthesis requires a closing**

**A** Testing

the form one

**parenthesis). Failure to do so will cause parse**

more time.

**errors.**

**Granted, using the methods applied**

**here, you could combine all the total cal-**

**culations into just one line of code (instead**

**of three)—but there is such a thing as**

**oversimplifying.**

**B** Even though the calculations have been

condensed, the math works out the same. If you

see different results or get an error message,

double-check your parentheses for balance (an

equal number of opening and closing parentheses).

Using Numbers 85

[**Incrementing and**](#index_split_000.html#p7) 

**Script 4.5** Incrementing or decrementing a number

is a common operation using **++** or **––**, respectively.

[**Decrementing**](#index_split_000.html#p7)

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

1.0

Transitional//EN"

[**a Number**](#index_split_000.html#p7)

2 "http://www.w3.org/TR/xhtml1/DTD/

xhtml1-transitional.dtd">

PHP, like Perl and most other programming

3 <html

xmlns="http://www.w3.org/1999/

languages, includes some shortcuts that let

xhtml" xml:lang="en" lang="en">

4 <head>

you avoid ugly constructs such as

5

<meta http-equiv="Content-Type"

**$tax = $tax + 1;**

content="text/html;

charset=utf-8"/>

6

<title>Product Cost Calculator

When you need to increase the value

</title>

of a variable by 1 (called an incremental

7

<style type="text/css" media="screen"> adjustment) or decrease the value of a

8

.number { font-weight: bold;}

9 </style>

variable by 1 (a decremental adjustment),

10 </head>

you can use **++** and **\--**, respectively:

11 <body>

**$var = 20; // 20**

12 <?php // Script 4.3 - handle\_calc.php #4

13 /\* This script takes values from

**$var++; // 21**

calculator.html and performs

**$var++; // 22**

14 total cost and monthly payment

**$var--; // 21**

calculations.

\*/

15

Solely for the sake of testing this concept,

16 // Address error handling, if you want.

you’ll rewrite the **handle\_calc.php** script

17

one last time.

18 // Get the values from the $\_POST array:

19 $price = $\_POST\['price'\];

20 $quantity = $\_POST\['quantity'\];

**To increment the value of a variable:**

21 $discount = $\_POST\['discount'\];

22 $tax = $\_POST\['tax'\];

**1.** Open **handle\_calc.php** in your text

23 $shipping = $\_POST\['shipping'\];

editor or IDE, if it is not already open

24 $payments = $\_POST\['payments'\];

(Script 4.4).

25

26 // Calculate the total:

**2.** Change the tax rate calculation from

27 $total = (($price \* $quantity) +

Script 4.3 to read as follows (**Script 4.5**):

$shipping) - $discount;

**$taxrate = $tax/100;**

28

29 // Determine the tax rate:

**$taxrate++;**

**30 $taxrate = $tax/100;**

The first line calculates the tax rate

**31 $taxrate++;**

32

as the **$tax** value divided by 100. The

33 // Factor in the tax rate:

second line increments this value by 1

34 $total = $total \* $taxrate;

so that it can be multiplied by the total

35

to determine the total with tax.

36 // Calculate the monthly payments:

37 $monthly = $total / $payments;

38

39 // Apply the proper formatting:

40 $total = number\_format ($total, 2);

41 $monthly = number\_format ($monthly, 2);

42

code continues on next page

86 Chapter

4

![Image 121](index-108_1.png)

![Image 122](index-108_2.png)

**Script 4.5** continued

**3.** Save the script, place it in the same

directory as **calculator.html**, and test

43 // Print out the results:

it in your browser

44 print "<p>You have selected to

**A** and **B**.

purchase:<br

/>

45 <span class=\\"number\\">$quantity</span> **Although functionally it doesn’t matter**

widget(s) at <br />

**whether you code $taxrate = $taxrate +**

46 $<span class=\\"number\\">$price</span>

**1; or the abbreviated $taxrate++, the latter**

price each plus a <br />

**method (using the increment operator) is more**

47 $<span

class=\\"number\\">$shipping</span>

**professional and common.**

shipping cost and a <br />

48 <span class=\\"number\\">$tax</span>

**In Chapter 6, “Control Structures,” you’ll**

percent tax rate.<br />

**see how the increment operator is commonly**

49 After your $<span class=\\"number\\">

**used in conjunction with loops.**

$discount</span> discount, the total

cost

is

50 $<span class=\\"number\\">$total</span>.<br /> 51 Divided over <span class=\\"number\\">

**Arithmetic Assignment**

$payments</span> monthly payments, that

**Operators**

would be $<span class=\\"number\\">

$monthly</span>

each.</p>";

PHP also supports a combination of

52

mathematical and assignment operators.

53 ?>

These are **+=**, **\-=**, **\*=**, and **/=**. Each will 54 </body>

assign a value to a variable by perform-

55 </html>

ing a calculation on it. For example, these

next two lines both add 5 to a variable:

**$num = $num + 5;**

**$num += 5;**

This means the **handle\_calc.php** script

could determine the tax rate using this:

**$tax = $\_POST\['tax'\]; // Say, 5**

**$tax /= 100; // Now $tax is .05**

**$tax += 1; // 1.05**

You’ll frequently see these shorthand

**A**

ways of performing arithmetic.

The last

execution of

the form.

**B** It won’t affect your calculations if you use the

long or short version of incrementing a variable

(compare Scripts 4.4 and 4.5).

Using Numbers 87

[**Creating Random**](#index_split_000.html#p7)

**Script 4.6** The **rand()** function generates a

random number.

[**Numbers**](#index_split_000.html#p7)

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

1.0

Transitional//EN"

The last function you’ll learn about in

2 "http://www.w3.org/TR/xhtml1/DTD/

this chapter is **rand()**, a random-number

xhtml1-transitional.dtd">

generator. All it does is output a random

3 <html

xmlns="http://www.w3.org/1999/

xhtml" xml:lang="en" lang="en">

number:

4 <head>

**$n = rand(); // 31**

5

<meta http-equiv="Content-Type"

**$n = rand(); // 87**

content="text/html;

charset=utf-8"/>

6 <title>Lucky

Numbers</title>

The **rand()** function can also take minimum

7 </head>

and maximum parameters, if you prefer to

8 <body>

limit the generated number to a specific range:

9

<?php // Script 4.6 - random.php

10 /\* This script generates 3 random

**$n = rand (0, 10);**

numbers.

\*/

11

These values are inclusive, so in this case

12 // Address error handling, if you want.

0 and 10 are feasible returned values.

13

As an example of generating random

14 // Create three random numbers:

**15 $n1 = rand (1, 99);**

numbers, let’s create a simple “Lucky

**16 $n2 = rand (1, 99);**

Numbers” script.

**17 $n3 = rand (1, 99);**

18

**To generate random numbers:**

19 // Print out the numbers:

20 print "<p>Your lucky numbers are:<br />

**1.** Begin a new document in your text

21 $n1<br

/>

editor or IDE, to be named **random.php**

22 $n2<br

/>

(**Script 4.6**):

23 $n3</p>";

24

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

25 ?>

➝ **XHTML 1.0 Transitional//EN"**

26 </body>

**"http://www.w3.org/TR/xhtml1/**

27 </html>

 ➝ **DTD/xhtml1-transitional.dtd">**

**<html xmlns="http://www.w3.org/**

➝ **1999/xhtml" xml:lang="en"**

➝ **lang="en">**

**<head>**

**<meta**

**http-equiv="Content-Type"**

 ➝ **content="text/html;**

 ➝ **charset=utf-8"/>**

**<title>Lucky**

**Numbers</title>**

**</head>**

**<body>**

**2.** Include the PHP tags and address error

management, if you need to:

**<?php // Script 4.6 - random.php**

88 Chapter

4

![Image 123](index-110_1.png)

![Image 124](index-110_2.png)

**3.** Create three random numbers:

**$n1 = rand (1, 99);**

**$n2 = rand (1, 99);**

**$n3 = rand (1, 99);**

This script prints out a person’s lucky

**A** The three random

numbers, like those found on the back

numbers created by invoking

of a fortune cookie. These numbers are

the **rand()** function.

generated by calling the **rand()** function

three separate times and assigning each

result to a different variable.

**4.** Print out the numbers:

**print "<p>Your lucky numbers**

**are:<br />**

**B** Running the script again

**$n1<br />**

produces different results.

**$n2<br />**

**$n3</p>";**

The **print** statement is fairly simple.

**Other Mathematical Functions**

The numbers are printed, each on its

PHP has a number of built-in functions

own line, by using the HTML break tag.

for manipulating mathematical data.

This chapter introduced **round()**,

**5.** Close the PHP code and the HTML page:

**number\_format()**, and **rand()**.

**?>**

PHP has broken **round()** into two other

**</body>**

functions. The first, **ceil()**, rounds every

**</html>**

number to the next highest integer. The

**6.** Save the file as **random.php**, place it

second, **floor()**, rounds every number

in the proper directory for your PHP-

to the next lowest integer.

enabled server, and test it in your Web

Another function the calculator page

browser

could make good use of is **abs()**, which

**A**. Refresh the page to see

different numbers

returns the absolute value of a number.

**B**.

In case you don’t remember your abso-

lute values, the function works like this:

**The getrandmax() function returns the**

**largest possible random number that can be**

**$number = abs(-23); // 23**

**created using rand(). This value differs by**

**$number = abs(23); // 23**

**operating system.**

In layman’s terms, the absolute value of

**PHP has another function that generates**

a number is always a positive number.

**random numbers: mt\_rand(). It works simi-**

Beyond these functions, PHP supports

**larly to (but, arguably, better than) rand() and**

all the trigonometry, exponent, base

**is the smarter choice for sensitive situations**

conversion, and logarithm functions

**like cryptography. Also see the PHP manual’s**

you’ll ever need. See the PHP manual

**page for the mt\_rand() function for more**

**discussion of generating random numbers as**

for more information.

**a whole.**

Using Numbers 89

[**Review and Pursue**](#index_split_000.html#p7)

If you have any problems with the review

questions or the pursue prompts, turn

to the book’[s supporting forum (www.](http://www.LarryUllman.com/forum/)

[LarryUllman.com/forum/).](http://www.LarryUllman.com/forum/)

**Review**

■

What are the four primary arithmetic

operators?

■

Why will the following code not work:

**print "The total is $$total";**

What must be done instead?

■

Why must an HTML page that contains

a form that’s being submitted to a PHP

script be loaded through a URL?

■

What functions can be used to format

numerical values? How do you format

numbers to a specific number of

decimals?

■

What is the importance of operator

precedence?

■

What are the incremental and

decremental operators?

■

What are the arithmetic assignment

operators?

**Pursue**

■

Look up the PHP manual page for one

of the new functions mentioned in this

chapter. Use the links on that page to

investigate a couple of other number-

related functions PHP has.

■

Create another HTML form for taking

numeric values. Then create the PHP

script that receives the form data,

performs some calculations, formats

the values, and prints the results.

90 Chapter

4

[**5**](#index_split_000.html#p7)

[Using Strings](#index_split_000.html#p7)

As introduced in Chapter 2, “Variables,”

a second category of variables used by

**In This Chapter**

PHP is strings—a collection of characters

enclosed within either single or double

Creating the HTML Form

92

quotation marks. A string variable may con-

Concatenating Strings

95

sist of a single letter, a word, a sentence, a

Handling Newlines

98

paragraph, HTML code, or even a jumble

of nonsensical letters, numbers, and sym-

HTML and PHP

100

bols (which might represent a password).

Encoding and Decoding Strings

103

Strings may be the most common variable

Finding Substrings

107

type used in PHP.

Replacing Parts of a String

111

This chapter covers PHP’s most basic

built-in functions and operators for manipu-

Review and Pursue

114

lating string data, regardless of whether

the string originates from a form or is first

declared within the script. Some common

techniques will be introduced—joining

strings together, trimming strings, and

encoding strings. Other uses for strings

are illustrated in subsequent chapters.

![Image 125](index-113_1.png)

[**Creating the**](#index_split_000.html#p7)

[**HTML Form**](#index_split_000.html#p7)

As in Chapter 3, let’s begin by creating an

HTML form that sends different values—in

the form of string variables—to a PHP

script. The theoretical example being used

is an online bulletin board or forum where

users can post a message, their email

address, and their first and last names **A**.

**To create the HTML form:**

**1.** Begin a new HTML document in

your text editor or IDE, to be named

**A** This HTML form is the basis for most of

**posting.html** (**Script 5.1**):

the examples in this chapter.

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

➝ **XHTML 1.0 Transitional//EN"**

**"http://www.w3.org/TR/xhtml1/**

➝ **DTD/xhtml1-transitional.dtd">**

**<html xmlns="http://www.w3.org/**

➝ **1999/xhtml" xml:lang="en"**

➝ **lang="en">**

**<head>**

**<meta**

**http-equiv="Content-Type"**

 ➝ **content="text/html;**

 ➝ **charset=utf-8"/>**

**<title>Forum**

**Posting</title>**

**</head>**

**<body>**

**<!-- Script 5.1 - posting.html -->**

**<div><p>Please complete this form**

➝ **to submit your posting:</p>**

**2.** Create the initial **form** tag:

**<form action="handle\_post.php"**

➝ **method="post">**

This form will send its data to the

**handle\_post.php** script and will use

the POST method.

92 Chapter

5

**Script 5.1** This form sends string data to a PHP script.

**3.** Add inputs for the first name, last name,

and email address:

1

<!DOCTYPE html PUBLIC "-//W3C//DTD

XHTML 1.0 Transitional//EN"

**<p>First Name: <input type="text"**

2 "http://www.w3.org/TR/xhtml1/DTD/

➝ **name="first\_name" size="20" /></p>** xhtml1-transitional.dtd">

**<p>Last Name: <input type="text"**

3 <html

xmlns="http://www.w3.org/1999/

➝ **name="last\_name" size="20" /></p>** xhtml" xml:lang="en" lang="en">

4 <head>

**<p>Email Address: <input type=**

5

<meta http-equiv="Content-Type"

➝ **"text" name="email"**

content="text/html;

charset=utf-8"/>

➝ **size="30" /></p>**

6 <title>Forum

Posting</title>

7 </head>

These are all basic text input types,

8 <body>

which were covered in Chapter 3.

9

<!-- Script 5.1 - posting.html -->

Remember that the various inputs’ name

10 <div><p>Please complete this form to

values should adhere to the rules of PHP

submit your posting:</p>

variable names (no spaces; must not

11

12 <form action="handle\_post.php"

begin with a number; must consist only

method="post">

of letters, numbers, and the underscore).

13

**4.** Add an input for the posting:

14

<p>First Name: <input type="text"

name="first\_name" size="20" /></p>

**<p>Posting: <textarea**

15

➝ **name="posting" rows="9"**

16

<p>Last Name: <input type="text"

➝ **cols="30"></textarea></p>**

name="last\_name" size="20" /></p>

17

The posting field is a **textarea**, which is

18

<p>Email Address: <input type="text"

a larger type of text input box.

name="email" size="30" /></p>

19

**5.** Create a submit button and close

20

<p>Posting: <textarea name="posting"

the form:

rows="9"

cols="30"></textarea></p>

21

**<input type="submit" name="submit"**

22

<input type="submit" name="submit"

➝ **value="Send My Posting" />**

value="Send My Posting" />

**</form>**

23

24 </form>

Every form must have a submit button

25 </div>

(or a submit image).

26 </body>

**6.** Complete the HTML page:

27 </html>

**</div>**

**</body>**

**</html>**

continues on next page

Using Strings 93

**7.** Save the file as **posting.html**, place it in the appropriate directory on your

PHP-enabled server, and view it in your

Web browser **A**.

This is an HTML page, so it doesn’t

have to be on a PHP-enabled server in

order for you to view it. But because

it will eventually send data to a PHP

script, it’s best to go ahead and place

the file on your server.

**Technically speaking, all form data,**

**aside from uploaded files, is sent to the**

**handling script as strings. This includes**

**numeric data entered into text boxes,**

**options selected from drop-down menus,**

**checkbox or radio button values, and so**

**forth. Even the form in Chapter 4, “Using**

**Numbers,” sent strings with numeric values**

**to the handling script.**

**Many forum systems written in PHP**

**are freely available for your use. This book**

**doesn’t discuss how to fully develop one, but**

**a multilingual forum is developed in my PHP**

**6 and MySQL 5 for Dynamic Web Sites: Visual**

**QuickPro Guide (Peachpit Press, 2007).**

**This book’s Web site has a forum**

**where readers can post questions and other**

**readers (and the author) answer questions.**

**Y[ou can find it at www.LarryUllman.com/](http://www.LarryUllman.com/forum/list.php?30)**

[**forum/list.php?30.**](http://www.LarryUllman.com/forum/list.php?30)

94 Chapter

5

[**Concatenating Strings**](#index_split_000.html#p7)

Concatenation is an unwieldy term but a

useful concept. It refers to the appending

of one item onto another. Specifically, in

programming, you concatenate strings. The

period (**.** ) is the operator for performing this

action, and it’s used like so:

**$s1 = 'Hello, ';**

**$s2 = 'world!';**

**$greeting = $s1 . $s2;**

The end result of this concatenation is

that the **$greeting** variable has a value

of Hello, world!.

Because of the way PHP deals with variables,

the same effect could be accomplished using

**$greeting = "$s1$s2";**

This code works because PHP replaces

variables within double quotation marks

with their value. However, the formal

method of using the period to concatenate

strings is more commonly used and is

recommended (it will be more obvious

what’s occurring in your code).

Another way of performing concatenation

involves the concatenation assignment

operator:

**$greeting = 'Hello, ';**

**$greeting .= 'world!';**

This second line roughly means “assign

to **$greeting** its current value plus the

concatenation of world!” The end result is

**$greeting** having the value Hello, world!

once again.

The **posting.html** script sends several

string variables to the **handle\_post.php**

page. Of those variables, the first and last

names could logically be concatenated. It’s

quite common, and even recommended, to

take a user’s first and last names as separate

inputs, as this form does. On the other hand,

it would be advantageous to be able to refer

to the two together as one name. You’ll write

the PHP script with this in mind.

Using Strings 95

**To use concatenation:**

**Script 5.2** This PHP script demonstrates

concatenation, one of the most common

**1.** Begin a new document in your text

manipulations of a string variable. Think of

editor or IDE, to be named **handle\_**

it as addition for strings.

**post.php** (**Script 5.2**):

1

<!DOCTYPE html PUBLIC "-//W3C//DTD

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

XHTML 1.0 Transitional//EN"

2 "http://www.w3.org/TR/xhtml1/DTD/

➝ **XHTML 1.0 Transitional//EN"**

xhtml1-transitional.dtd">

**"http://www.w3.org/TR/xhtml1/**

3 <html

xmlns="http://www.w3.org/1999/

 ➝ **DTD/xhtml1-transitional.dtd">**

xhtml" xml:lang="en" lang="en">

**<html xmlns="http://www.w3.org/**

4 <head>

➝ **1999/xhtml" xml:lang="en"**

5

<meta http-equiv="Content-Type"

content="text/html;

charset=utf-8"/>

➝ **lang="en">**

6 <title>Forum

Posting</title>

**<head>**

7 </head>

**<meta**

**http-equiv="Content-Type"**

8 <body>

 ➝ **content="text/html;**

9

<?php // Script 5.2 - handle\_post.php

**charset=utf-8"/>**

10 /\* This script receives five values

from

posting.html:

**<title>Forum**

**Posting</title>**

11 first\_name, last\_name, email, posting,

**</head>**

submit

\*/

**<body>**

12

13 // Address error management, if you

**2.** Create the initial PHP tag, and address

want.

error management, if necessary:

14

**<?php // Script 5.2 -**

15 // Get the values from the $\_POST

array:

➝ **handle\_post.php**

16 $first\_name = $\_POST\['first\_name'\];

If you don’t have **display\_errors**

17 $last\_name = $\_POST\['last\_name'\];

enabled, or if **error\_reporting** is

18 $posting = $\_POST\['posting'\];

19

set to the wrong level, see Chapter 3

20 // Create a full name variable:

for the lines to include here to alter

**21 $name = $first\_name . ' ' .**

those settings.

**$last\_name;**

22

**3.** Assign the form data to local variables:

23 // Print a message:

**$first\_name = $\_POST\['first\_name'\];**

24 print "<div>Thank you, $name, for

**$last\_name = $\_POST\['last\_name'\];**

your

posting:

25 <p>$posting</p></div>";

**$posting = $\_POST\['posting'\];**

26

The form uses the POST method, so all

27 ?>

the form data will be available in **$\_POST**.

28 </body>

29 </html>

This example doesn’t have a line for the

email address because you won’t be

using it yet, but you can replicate this

code to reference that value as well.

**4.** Create a new **$name** variable using

concatenation:

**$name = $first\_name . ' ' .**

➝ **$last\_name;**

96 Chapter

5

![Image 126](index-118_1.png)

![Image 127](index-118_2.png)

This act of concatenation takes two

variables plus a space and joins them

all together to create a new variable,

called **$name**. Assuming you entered

Elliott and Smith as the names, then

**$name** would be equal to Elliott Smith.

**5.** Print out the message to the user:

**print "<div>Thank you, $name, for**

➝ **your posting:**

**<p>$posting</p></div>";**

This message reports back to the user

what was entered in the form.

**6.** Close the PHP section and complete

the HTML page:

**A** The HTML form in use…

**?>**

**</body>**

**</html>**

**7.** Save your script as **handle\_post.php**,

place it in the same directory as

**B** …and the resulting PHP page.

**posting.html** (on your PHP-enabled

server), and test both the form and the

script in your Web browser **A** and **B**.

**You can link as many strings as you want**

As a reminder, you must load the form

**using concatenation. You can even join num-**

through a URL (http: //something) so

**bers to strings:**

that, when the form is submitted, the

handling PHP script is also run through

**$new\_string = $s1 . $s2 . $number;**

a URL.

**This works because PHP is weakly typed,**

**meaning that its variables aren’t locked in to**

**If you used quotation marks of any kind**

**one particular format. Here, the $number vari-**

**in your form and saw extraneous slashes in**

**able will be turned into a string and appended**

**the printed result, see the sidebar “Magic**

**to the value of the $new\_string variable.**

**Quotes” in Chapter 3 for an explanation of the**

**Concatenation can be used in many**

**cause and for the fix.**

**ways, even when you’re feeding arguments**

**As a reminder, it’s important to under-**

**to a function. An uncommon but functional**

**stand the difference between single and**

**example would be**

**double quotation marks in PHP. Characters**

**$text = nl2br($heading . $body);**

**within single quotation marks are treated liter-**

**ally; characters within double quotation marks**

**The nl2br() function, first mentioned in**

**are interpreted (for example, a variable’s name**

**Chapter 1, “Getting Started with PHP,” will**

**will be replaced by its value). See Chapter 3**

**be discussed in detail next.**

**for a refresher.**

Using Strings 97

![Image 128](index-119_1.png)

![Image 129](index-119_2.png)

![Image 130](index-119_3.png)

![Image 131](index-119_4.png)

[**Handling Newlines**](#index_split_000.html#p7)

A common question beginning PHP

developers have involves handling newlines

in strings. The **textarea** form element

allows a user to enter text over multiple

lines by pressing Return/Enter. Each use

of Return/Enter equates to a newline in

the resulting string. These newlines work

within a **textarea** but have no effect on a

rendered PHP page **A** and **B**.

To create the equivalent of newlines in a

rendered Web page, you use the break

tag: **<br />** . Fortunately, PHP has the

**nl2br()** function, which automatically

**A** Newlines in form data like text areas…

converts newlines into break tags:

**$var = nl2br($var);**

Let’s apply this function to **handle\_**

**post.php** so that the user’s posting

retains its formatting.

**B** …are not rendered by the Web browser.

**To convert newlines to breaks:**

**1.** Open **handle\_post.php** (Script 5.2)

in your text editor or IDE, if it is not

already open.

**2.** Apply the **nl2br()** function when

assigning a value to the **$posting**

**C** Now the same submitted data **A**

variable (**Script 5.3**):

is properly displayed over multiple

lines in the Web browser.

**$posting = nl2br($\_POST\['posting'\]);**

Now **$posting** will be assigned the

value of **$\_POST\['posting'\]**, with any

newlines converted to HTML break tags.

**D** The HTML source, corresponding to **B**, shows

the effect that newlines have in the Web browser

(i.e., they add spacing within the HTML source code).

98 Chapter

5

**Script 5.3** When you use the **nl2br()** function, **3.** Save the file, place it in the same direc-newlines entered into the posting **textarea** are

tory as **posting.html** (on your PHP-

honored when displayed in the Web browser.

enabled server), and test again in your

1

<!DOCTYPE html PUBLIC "-//W3C//DTD

Web browser **C**.

XHTML 1.0 Transitional//EN"

2 "http://www.w3.org/TR/xhtml1/DTD/

xhtml1-transitional.dtd">

**Newlines can also be inserted into**

3 <html

xmlns="http://www.w3.org/1999/

**strings by placing the newline character—**

xhtml" xml:lang="en" lang="en">

**\\n—between double quotation marks.**

4 <head>

**Other HTML tags, like paragraph tags,**

5

<meta http-equiv="Content-Type"

**also affect spacing in the rendered Web page.**

content="text/html;

charset=utf-8"/>

**You can turn newlines (or any character) into**

6 <title>Forum

Posting</title>

**paragraph tags using a replace function, but**

7 </head>

**the code for doing so is far more involved than**

8 <body>

**just invoking nl2br().**

9

<?php // Script 5.3 - handle\_post.php #2

10 /\* This script receives five values

**Newlines present in strings sent to the**

from

posting.html:

**browser will have an effect, but only in the**

11 first\_name, last\_name, email, posting,

**HTML source of the page**

submit

\*/

**D.**

12

13 // Address error management, if you

want.

14

15 // Get the values from the $\_POST

array:

16 $first\_name = $\_POST\['first\_name'\];

17 $last\_name = $\_POST\['last\_name'\];

**18 $posting = nl2br($\_POST\['posting'\]);**

19

20 // Create a full name variable:

21 $name = $first\_name . ' ' . $last\_name;

22

23 // Print a message:

24 print "<div>Thank you, $name, for your

posting:

25 <p>$posting</p></div>";

26

27 ?>

28 </body>

29 </html>

Using Strings 99

![Image 132](index-121_1.png)

![Image 133](index-121_2.png)

![Image 134](index-121_3.png)

[**HTML and PHP**](#index_split_000.html#p7)

As stated several times over by now, PHP

is a server-side technology that’s frequently

used to send data to the Web browser. This

data can be in the form of plain text, HTML

code, or, more commonly, both.

In this chapter’s primary example, data is

entered in an HTML form and then printed

back to the Web browser using PHP. A

potential problem is that the user can enter

HTML characters in the form, which can

affect the resulting page’s formatting **A**

and **B**—or, worse, cause security problems.

You can use a couple of PHP functions to

**A** If the user enters HTML code in

manipulate HTML tags within PHP string

the posting…

variables:

■

**htmlspecialchars()** converts certain

HTML tags into their entity versions.

■

**htmlentities()** turns all HTML tags

into their entity versions.

■

**strip\_tags()** removes all HTML and

PHP tags.

The first two functions turn an HTML tag

(for example, **<span>** ) into an entity version

**B** …it’s rendered by the Web

browser when reprinted.

like **&lt;span&gt;** . The entity version

appears in the output but isn’t rendered.

You might use either of these if you wanted

to display code without enacting it. The

third function, **strip\_tags()**, removes

HTML and PHP tags entirely.

You ought to watch for special tags in

user-provided data for two reasons. First,

**C** Displaying HTML submitted by a user in the

as already mentioned, submitted HTML

Web browser can have terrible consequences,

would likely affect the rendered page (e.g.,

such as the execution of JavaScript.

mess up a table, tweak the CSS, or just add

formatting where there shouldn’t be any). The

second concern is more important. Because

JavaScript is placed within HTML **script**

tags, a malicious user could submit JavaScript

that would be executed when it’s redisplayed

on the page **C**. This is how cross-site

scripting (XSS) attacks are performed.

100 Chapter

5

**Script 5.4** This version of the PHP script addresses To see the impact these functions have, this

HTML tags in two different ways.

next rewrite of **handle\_post.php** will use

them each and display the respective results.

1

<!DOCTYPE html PUBLIC "-//W3C//DTD

XHTML 1.0 Transitional//EN"

2 "http://www.w3.org/TR/xhtml1/DTD/

**To address HTML in PHP:**

xhtml1-transitional.dtd">

3 <html

xmlns="http://www.w3.org/1999/

**1.** Open **handle\_post.php** (Script 5.3)

xhtml" xml:lang="en" lang="en">

in your text editor or IDE, if it is not

4 <head>

already open.

5

<meta http-equiv="Content-Type"

content="text/html;

charset=utf-8"/>

**2.** Before the **print** line, add (**Script 5.4**): 6 <title>Forum

Posting</title>

**$html\_post = htmlentities**

7 </head>

➝ **($\_POST\['posting'\]);**

8 <body>

9

<?php // Script 5.4 - handle\_post.php #3

**$strip\_post = strip\_tags**

10 /\* This script receives five values

➝ **($\_POST\['posting'\]);**

from

posting.html:

To clarify the difference between how

11 first\_name, last\_name, email, posting,

submit

\*/

these two functions work, apply them

12

both to the posting text, creating two

13 // Address error management, if you

new variables in the process. Refer

want.

to **$\_POST\['posting'\]** here and not

14

**$posting** because **$posting** already

15 // Get the values from the $\_POST

array:

reflects the application of the **nl2br()**

16 $first\_name = $\_POST\['first\_name'\];

function, which means that break tags

17 $last\_name = $\_POST\['last\_name'\];

may have been introduced that were

18 $posting = nl2br($\_POST\['posting'\]);

not explicitly entered by the user.

19

20 // Create a full name variable:

**3.** Alter the **print** statement to read

21 $name = $first\_name . ' ' . $last\_name;

as follows:

22

23 // Adjust for HTML tags:

**print "<div>Thank you, $name, for**

**24 $html\_post = htmlentities($\_POST**

➝ **your posting:**

**\['posting'\]);**

**<p>Original: $posting</p>**

**25 $strip\_post = strip\_tags($\_POST**

**<p>Entity: $html\_post</p>**

**\['posting'\]);**

**<p>Stripped: $strip\_post</p></div>";**

26

27 // Print a message:

To highlight the different results, print out

**28 print "<div>Thank you, $name, for**

the three different versions of the posting

**your**

**posting:**

text. First is the original posting as it

**29 <p>Original:**

**$posting</p>**

**30 <p>Entity:**

**$html\_post</p>**

was entered, after being run through

**31 <p>Stripped:**

**$strip\_post</p></div>";**

**nl2br()**. Next is the **htmlentities()**

32

version of the posting, which will show

33 ?>

the HTML tags without rendering them.

34 </body>

Finally, the **strip\_tags()** version will be

35 </html>

printed; it doesn’t include any HTML (or

PHP) tags.

continues on next page

Using Strings 101

![Image 135](index-123_1.png)

![Image 136](index-123_2.png)

![Image 137](index-123_3.png)

**4.** Save the file, place it in the same direc-

tory as **posting.html** (on your PHP-

enabled server), and test it again in your

Web browser **D** and **E**.

If you view the HTML source code of

the resulting PHP page **F**, you’ll also

see the effect that applying these

functions has.

**For security purposes, it’s almost**

**always a good idea to use htmlentities(),**

**htmlspecialchars(), or strip\_tags() to**

**any user-provided data that’s being printed**

**to the Web browser. I don’t do so through the**

**course of this book only to minimize clutter.**

**D** The HTML characters entered as part of

**The html\_entity\_decode() function**

a posting will now be addressed by PHP.

**does just the opposite of htmlentities(),**

**turning HTML entities into their respective**

**HTML code.**

**Another useful function for outputting**

**strings in the Web browser is wordwrap().**

**This function wraps a string to a certain num-**

**ber of characters.**

**E**

**To turn newlines into breaks while**

The resulting PHP page shows the original post

as it would look if printed without modification,

**still removing any HTML or PHP tags, apply**

the effect of **htmlentities()**, and the effect of

**nl2br() after strip\_tags():**

**strip\_tags()**.

**$posting =**

**nl2br(strip\_tags($\_POST\['posting'\]));**

**In that line, the strip\_tags() function will**

**be called first, and its result will be sent to the**

**nl2br() function.**

**F** The HTML source for the content displayed in **E**.

102 Chapter

5

**Script 5.5** This script encodes two variables before adding them to a link. Then the values

[**Encoding and**](#index_split_000.html#p7)

can be successfully passed to another page.

[**Decoding Strings**](#index_split_000.html#p7)

1

<!DOCTYPE html PUBLIC "-//W3C//DTD

XHTML 1.0 Transitional//EN"

At the end of Chapter 3, the section

2 "http://www.w3.org/TR/xhtml1/DTD/

“Manually Sending Data to a Page”

xhtml1-transitional.dtd">

demonstrated how to use the thinking

3 <html

xmlns="http://www.w3.org/1999/

behind the GET form method to send data

xhtml" xml:lang="en" lang="en">

to a page. In that example, instead of using

4 <head>

5

<meta http-equiv="Content-Type"

an actual form, data was appended to the

content="text/html;

charset=utf-8"/>

URL, making it available to the receiving

6 <title>Forum

Posting</title>

script. I was careful to say that only single

7 </head>

words could be passed this way, without

8 <body>

spaces or punctuation. But what if you

9

<?php // Script 5.5 - handle\_post.php #4

10 /\* This script receives five values

want to pass several words as one variable

from

posting.html:

value or use special characters?

11 first\_name, last\_name, email, posting,

To safely pass any value to a PHP script

submit

\*/

12

through the URL, apply the **urlencode()**

13 // Address error management, if you

function. As its name implies, this function

want.

takes a string and encodes it (changes its

14

format) so that it can properly be passed

15 // Get the values from the $\_POST

as part of a URL. Among other things,

array:

16 $first\_name = $\_POST\['first\_name'\];

the function replaces spaces with plus

17 $last\_name = $\_POST\['last\_name'\];

signs (**+**) and translates special characters

18 $posting = nl2br($\_POST\['posting'\]);

(for example, the apostrophe) into less

19

problematic versions. To use this function,

20 // Create a full name variable:

you might code

21 $name = $first\_name . ' ' . $last\_name;

22

**$string = urlencode($string);**

23 // Print a message:

24 print "<div>Thank you, $name, for your

To demonstrate one application of

posting:

**urlencode()**, let’s update the **handle\_**

25 <p>$posting</p></div>";

**post.php** page so that it also creates

26

a link that passes the user’s name and

27 // Make a link to another page:

email address to a third page.

**28 $name = urlencode($name);**

**29 $email = urlencode($\_POST\['email'\]);**

**30 print "<p>Click <a href=\\" thanks.php?**

**To use urlencode( ):**

**name=$name&email=$email**

**\\">here**

**</a> to continue.</p>";**

**1.** Open **handle\_post.php** (Script 5.4)

31

in your text editor or IDE, if it is not

32 ?>

already open.

33 </body>

34 </html>

**2.** Delete the **htmlentities()** and

**strip\_tags()** lines added in the

previous set of steps (**Script 5.5**).

continues on next page

Using Strings 103

**3.** Revert to the older version of the

**print** invocation:

**print "<div>Thank you, $name, for**

➝ **your posting:**

**<p>$posting</p></div>";**

**4.** After the **print** statement, add

the following:

**$name = urlencode($name);**

**$email = urlencode($\_POST\['email'\]);**

This script will pass these two variables

to a second page. In order for it to do

so, they must both be encoded.

Because the script has not previously

referred to or used the **$email** variable,

the second line both retrieves the

email value from the **$\_POST** array and

encodes it in one step. This is the same

as having these two separate lines:

**$email = $\_POST\['email'\];**

**$email = urlencode($email);**

**5.** Add another **print** statement that

creates the link:

**print "<p>Click <a href=\\"thanks.**

➝ **php?name=$name&email=$email\\">**

➝ **here</a> to continue.</p>";**

The primary purpose of this **print**

statement is to create an HTML link

in the Web page, the source code of

which would be something like

**<a href="thanks.php?name=Larry+**

➝ **Ullman&email=larry%40example.**

➝ **com">here</a>**

To accomplish this, begin by hard-coding

most of the HTML and then include the

appropriate variable names. Because the

HTML code requires that the URL for the

link be in double quotation marks—and

the **print** statement already uses double

quotation marks—you must escape them

(by preceding them with backslashes) in

order for them to be printed.

104 Chapter

5

![Image 138](index-126_1.png)

![Image 139](index-126_2.png)

![Image 140](index-126_3.png)

**6.** Save the file, place it in the proper

directory of your PHP-enabled server,

and test it again in your Web browser

**A** and **B**.

Note that clicking the link will result in

a server error, as the **thanks.php** script

hasn’t yet been written.

**7.** View the HTML source code of the

handling page to see the resulting link

in the HTML code **C**.

**Values sent directly from a form are**

**automatically URL-encoded prior to being sent**

**and decoded upon arrival at the receiving script.**

**You only need the urlencode() function to**

**A** Another use of the form.

**manually encode data (as in the example).**

**The urldecode() function does just the**

**opposite of urlencode()—it takes an encoded**

**URL and turns it back into a standard form.**

**You’ll use it less frequently, though, as PHP will**

**automatically decode most values it receives.**

**B** The handling script now displays a link to

continues on next page

another page.

**C** The HTML source code of the page **B** shows the dynamically generated link.

Using Strings 105

![Image 141](index-127_1.png)

**Since you can use concatenation with**

**functions, the new print statement could be**

**written as follows:**

**D**

**print 'Click <a href="thanks.php?**

The third page in this process—to be created

by you at the end of the chapter—prints a message

➝ **name=' . $name . '&email=' .**

based on values it receives in the URL.

➝ **$email . '">here</a> to continue.';**

**This method has two added benefits over the**

**original approach. First, it uses single quota-**

**tion marks to start and stop the statement,**

**meaning you don’t need to escape the double**

**quotation marks. Second, the variables used**

**are more obvious—they aren’t buried in a lot**

**of other code.**

**You do not need to encode numeric PHP**

**values in order to use them in a URL, as they**

**do not contain problematic characters. That**

**being said, it won’t hurt to encode them either.**

**At the end of the chapter you’ll be**

**prompted to create thanks.php, which greets**

**the user by name and email address D.**

**Encrypting and Decrypting Strings**

Frequently, in order to protect data, programmers encrypt it—alter its state by transforming it to a form that’s more difficult, if not impossible, to discern. Passwords are an example of a value you might want to encrypt. Depending on the level of security you want to establish, usernames, email addresses, and phone numbers are likely candidates for encryption, too.

You can use the **crypt()** function to encrypt data, but be aware that no decryption option is available (it’s known as one-way encryption). So, a password may be encrypted using it and then stored, but the decrypted value of the password can never be determined. Using this function in a Web application, you might encrypt a user’s password upon registration; then, when the user logged in, the password they entered at that time would also be encrypted, and the two protected versions of the password would be compared. The syntax for using **crypt()** is **$data = crypt($data);**

A second encryption function is **mcrypt\_encrypt()**, which can be decrypted using the appropriately named **mcrypt\_decrypt()** function. Unfortunately, in order for you to be able to use these two functions, the Mcrypt extension must be installed with the PHP module. Its usage and syntax is also more complex (I discuss it in my PHP 5 Advanced: Visual QuickPro Guide

\[Peachpit Press, 2007\]).

If the data is being stored in a database, you can also use functions built into the database application (for example, MySQL, PostgreSQL, Oracle, or SQL Server) to perform encryption and decryption. Depending on the technology you’re using, it most likely provides both one- and two-way encryption tools.

106 Chapter

5

[**Finding Substrings**](#index_split_000.html#p7)

**Comparing Strings**

PHP has a few functions you can use to

To compare two strings, you can always

pull apart strings, search through them,

use the equality operator, which you’ll

learn about in the next chapter. Other-

and perform comparisons. Although

wise, you can use these functions:

these functions are normally used with

conditionals, discussed in Chapter 6,

. **strcmp()** indicates how two strings

“Control Structures,” they are important

compare by returning a whole

number.

enough that they’ll be introduced here;

later chapters will use them more formally.

. **strnatcmp()** is similar but linguisti-

cally more precise.

Earlier in this chapter you learned how to

join strings using concatenation. Along with

These also have case-insensitive

companions, **strcasecmp()** and

making larger strings out of smaller pieces,

**strnatcasecmp()**.

PHP easily lets you extract subsections

from a string. The trick to using any method

To see if a substring is contained within

to pull out a subsection of a string is that

another string (i.e., to find a needle in a

haystack), you’ll use these functions:

you must know something about the string

itself in order to know how to break it up.

. **strstr()** returns the haystack from

the first occurrence of a needle to

The **strtok()** function creates a substring,

the end.

referred to as a token, from a larger string

by using a predetermined separator (such

. **strpos()** searches through a

haystack and returns the numeric

as a comma or a space). For example, if

location of a particular needle.

you have users enter their full name in one

field (presumably with their first and last

Both of these functions also have a

case-insensitive alternative: **stristr()**

names separated by a space), you can pull

and **stripos()**, respectively. Each of

out their first name with this code:

these functions is normally used in a

**$first = strtok($\_POST\['name'\], ' ');**

conditional to test whether the substring

was found.

That line tells PHP to extract everything

from the beginning of **$\_POST\['name'\]** until

it finds a blank space.

If you have users enter their full name in

the format Surname, First, you can find

their surname by writing

**$last = strtok($\_POST\['name'\], ', ');**

Using Strings 107

A second way to pull out sections of

a string is by referring to the indexed

position of the characters within the string.

The indexed position of a string is the

numerical location of a character, counting

from the beginning. However, PHP—like

most programming languages—begins all

indexes with the number 0. For example, to

index the string Larry, you begin with the L

at position 0, followed by a at 1, r at 2, the

second r at 3, and y at 4. Even though the

string length of Larry is 5, its index goes

from 0 to 4 (i.e., indexes always go from 0

to the string’s length minus 1).

With this in mind, you can call on the

**substr()** function to create a substring

based on the index position of the

substring’s characters:

**$sub = substr($string, 0, 10);**

The first argument is the master string

from which the substring will be derived.

Second, indicate where the substring

begins, as its indexed position (0 means

that you want to start with the first

character). Third, from that starting point,

state how many characters the substring

should contain (10). If the master string

does not have that many characters in it,

the resulting substring will end with the

end of the master string. This argument is

optional; if omitted, the substring will also

go until the end of the master string.

You can also use negative numbers to

count backward from the end of the string:

**$string = 'ardvark';**

**$sub = substr($string, -3, 3); // ark**

The second line says that three characters

should be returned starting at the third

character from the end. With that particular

example, you can again omit the third

argument and have the same result:

**$sub = substr($string, -3); // ark**

108 Chapter

5

**Script 5.6** This version of **handle\_post.php** counts To see how many characters are in a string,

the number of words in the posting and trims the

use **strlen()**:

displayed posting down to just the first 50 characters.

**print strlen('Hello, world!'); // 13**

1

<!DOCTYPE html PUBLIC "-//W3C//DTD

The count will include spaces and punctuation.

XHTML 1.0 Transitional//EN"

2 "http://www.w3.org/TR/xhtml1/DTD/

To see how many words are in a string, use

xhtml1-transitional.dtd">

**str\_word\_count()**. This function, along

3 <html

xmlns="http://www.w3.org/1999/

with **substr()**, will be used in this next

xhtml" xml:lang="en" lang="en">

revision of the **handle\_post.php** script.

4 <head>

5

<meta http-equiv="Content-Type"

content="text/html;

charset=utf-8"/>

**To create substrings:**

6 <title>Forum

Posting</title>

**1.** Open **handle\_post.php** (Script 5.5)

7 </head>

in your text editor or IDE, if it is not

8 <body>

9

<?php // Script 5.6 - handle\_post.php #5

already open.

10 /\* This script receives five values

**2.** Before the **print** statement, add the

from

posting.html:

following (**Script 5.6**):

11 first\_name, last\_name, email, posting,

submit

\*/

**$words = str\_word\_count($posting);**

12

13 // Address error management, if you

This version of the script will do two

want.

new things with the user’s posting.

14

One will be to display the number of

15 // Get the values from the $\_POST

words it contains. That information is

array:

gathered here and assigned to the

16 $first\_name = $\_POST\['first\_name'\];

17 $last\_name = $\_POST\['last\_name'\];

**$words** variable.

18 $posting = nl2br($\_POST\['posting'\]);

**3.** On the next line (also before the **print**

19

statement), add

20 // Create a full name variable:

21 $name = $first\_name . ' ' . $last\_name;

**$posting = substr($posting, 0, 50);**

22

23 // Get a word count:

The second new thing this script will

**24 $words = str\_word\_count($posting);**

do is limit the displayed posting to

25

its first 50 characters. You might use

26 // Get a snippet of the posting:

this, for example, if one page shows

**27 $posting = substr($posting, 0, 50);**

the beginning of a post, then a link

28

29 // Print a message:

takes the user to the full posting. To

**30 print "<div>Thank you, $name, for**

implement this limit, the **substr()**

**your**

**posting:**

function is called.

**31 <p>$posting...</p>**

**32 <p>($words**

**words)</p></div>";**

continues on next page

33

34 ?>

35 </body>

36 </html>

Using Strings 109

![Image 142](index-131_1.png)

![Image 143](index-131_2.png)

**4.** Update the **print** statement to read

**print "<div>Thank you, $name, for**

➝ **your posting:**

**<p>$posting...</p>**

**<p>($words words)</p></div>";**

There are two changes here. First,

ellipses are added after the posting to

indicate that this is just part of the whole

posting. Then, within another paragraph,

the number of words is printed.

**5.** Delete the two **urlencode()** lines and

the corresponding **print** line.

I’m referring specifically to the code

added in the previous incarnation of

**A** Postings longer than 50 characters…

the script, linking to **thanks.php**.

**6.** Save the file, place it in the proper

directory of your PHP-enabled server,

and test it again in your Web browser

**A** and **B**.

**B** …will be cut short. The word count is

**If you want to check whether a string**

also displayed.

**matches a certain format—for example, to**

**see if it’s a valid email address—you need to**

**use regular expressions. Regular expressions**

**are an advanced concept in which you define**

**patterns and then see if a value fits the mold.**

**See the PHP manual or my book PHP 6 and**

**MySQL 5 for Dynamic Web Sites: Visual**

**QuickPro Guide (Peachpit Press, 2007).**

110 Chapter

5

[**Replacing Parts**](#index_split_000.html#p7)

**Adjusting String Case**

A handful of PHP functions are used to

[**of a String**](#index_split_000.html#p7)

change the case of a string’s letters:

Instead of just finding substrings within a

. **ucfirst()** capitalizes the first letter

string, as the previous section discusses,

of the string.

you might find that you need to replace

. **ucwords()** capitalizes the first letter

substrings with new values. You can do

of words in a string.

so using the **str\_ireplace()** function:

. **strtoupper()** makes an entire string

**$string = str\_ireplace($needle,**

uppercase.

➝ **$replacement, $haystack);**

. **strtolower()** makes an entire string

This function replaces every occurrence

lowercase.

of **$needle** found in **$haystack** with

Due to the variance in people’s names

**$replacement**. For example:

around the globe, there’s no flawless

**$me = 'Larry E. Ullman';**

way to automatically format names with

PHP (or any programming language). In

**$me = str\_ireplace('E.', 'Edward',**

fact, I would be hesitant to alter the case

➝ **$me);**

of user-supplied data unless you have

The **$me** variable now has a value of Larry

good cause to do so.

Edward Ullman.

That function performs a case-insensitive

search. To be more restrictive, you can

perform a case-sensitive search using

**str\_replace()**. In this next script, **str\_**

**ireplace()** will be used to eliminate “bad

words” in submitted text.

There’s one last string-related function

I want to discuss: **trim()**. This function

removes any white space—spaces,

newlines, and tabs—from the beginning and

end of a string. It’s quite common for extra

spaces to be added to a string variable,

either because a user enters information

carelessly or due to sloppy HTML code.

For purposes of clarity, data integrity, and

Web design, it’s worth your while to delete

those spaces from the strings before you

use them. Extra spaces sent to the Web

browser could make the page appear oddly,

and those sent to a database or cookie

could have unfortunate consequences at

a later date (for example, if a password has

a superfluous space, it might not match

when it’s entered without the space).

Using Strings 111

The **trim()** function automatically strips **Script 5.7** This final version of the handling script

away any extra spaces from both the

applies the **trim()** function and then replaces

uses of **badword** with a bunch of Xs.

beginning and the end of a string (but not

the middle). The format for using **trim()** is

1

<!DOCTYPE html PUBLIC "-//W3C//DTD

as follows:

XHTML 1.0 Transitional//EN"

2 "http://www.w3.org/TR/xhtml1/DTD/

**$string = ' extra space before and**

xhtml1-transitional.dtd">

➝ **after text ';**

3 <html

xmlns="http://www.w3.org/1999/

**$string = trim($string);**

xhtml" xml:lang="en" lang="en">

4 <head>

**// $string is now equal to 'extra**

5

<meta http-equiv="Content-Type"

➝ **space before and after text'.**

content="text/html;

charset=utf-8"/>

6 <title>Forum

Posting</title>

**To use str\_ireplace( ) and trim():**

7 </head>

8 <body>

**1.** Open **handle\_post.php** (Script 5.6)

9

<?php // Script 5.7 - handle\_post.php #6

in your text editor or IDE, if it is not

10 /\* This script receives five values

from

posting.html:

already open.

11 first\_name, last\_name, email, posting,

**2.** Apply **trim()** to the form data (**Script 5.7**): submit

\*/

12

**$first\_name =**

13 // Address error management, if you

➝ **trim($\_POST\['first\_name'\]);**

want.

**$last\_name =**

14

➝ **trim($\_POST\['last\_name'\]);**

15 // Get the values from the $\_POST

array.

**$posting = trim($\_POST\['posting'\]);**

16 // Strip away extra spaces using

Just in case the incoming data has

trim():

**17 $first\_name = trim($\_POST**

extraneous white space at its beginning

**\['first\_name'\]);**

or end, the **trim()** function is applied.

**18 $last\_name = trim($\_POST**

**3.** Remove the use of **substr()**:

**\['last\_name'\]);**

**19 $posting = trim($\_POST\['posting'\]);**

**$posting = substr($posting, 0, 50);**

20

21 // Create a full name variable:

You’ll want to see the entire posting for

22 $name = $first\_name . ' ' . $last\_name;

this example, so remove this invocation

23

of **substr()**.

24 // Get a word count:

25 $words = str\_word\_count($posting);

**4.** Before the **print** statement, add

26

**$posting = str\_ireplace('badword',**

27 // Take out the bad words:

**28 $posting = str\_ireplace('badword',**

➝ **'XXXXX', $posting);**

**'XXXXX',**

**$posting);**

This specific example flags the use of

29

a bad word in a posting by crossing it

30 // Print a message:

31 print "<div>Thank you, $name, for your

out. Rather than an actual curse word,

posting:

the code uses **badword**. (You can use

32 <p>$posting</p>

whatever you want, of course.)

33 <p>($words

words)</p></div>";

34

35 ?>

36 </body>

37 </html>

112 Chapter

5

![Image 144](index-134_1.png)

![Image 145](index-134_2.png)

If you’d like to catch many bad words,

you can use multiple lines, like so:

**$posting = str\_ireplace**

➝ **('badword1', 'XXXXX', $posting);**

**$posting = str\_ireplace**

➝ **('badword2', 'XXXXX', $posting);**

**$posting = str\_ireplace**

➝ **('badword3', 'XXXXX', $posting);**

**5.** Update the **print** statement so that it

no longer uses the ellipses:

**print "<div>Thank you, $name, for**

➝ **your posting:**

**<p>$posting</p>**

**<p>($words words)</p></div>";**

**A** If a user enters a word you’d prefer

they not use…

**6.** Save the file, place it in the proper

directory of your PHP-enabled server,

and test again in your Web browser **A**

and **B**.

**The str\_ireplace() function will even**

**catch bad words in context. For example, if**

**you entered I feel like using badwords, the**

**B** …you can have PHP replace it.

**result would be I feel like using XXXXXs.**

**The str\_ireplace() function can**

**also take an array of needle terms, an array**

**of replacement terms, and even an array as**

**the haystack. Because you may not know**

**what an array is yet, this technique isn’t**

**demonstrated here.**

**If you need to trim excess spaces from**

**the beginning or the end of a string but not**

**both, PHP breaks the trim() function into**

**two more specific functions: rtrim() removes**

**spaces found at the end of a string variable**

**(on its right side), and ltrim() handles those**

**at the beginning (its left). They’re both used**

**just like trim():**

**$string = rtrim($string);**

**$string = ltrim($string);**

Using Strings 113

[**Review and Pursue**](#index_split_000.html#p7)

**Pursue**

■

Look up the PHP manual page for one

If you have any problems with the review

of the new functions mentioned in this

questions or the pursue prompts, turn

chapter. Use the links on that page to

to the book’[s supporting forum (www.](http://www.LarryUllman.com/forum/)

examine a couple of other string-related

[LarryUllman.com/forum/ ).](http://www.LarryUllman.com/forum/)

functions PHP has.

**Review**

■

Check out the PHP manual page

specifically for the **substr()** function.

■

How do you create a string?

Read the other examples found on

■

What are the differences between using

that page to get a better sense of how

single and double quotation marks?

**substr()** can be used.

■

What is the concatenation operator?

■

Write the **thanks.php** script that goes

What is the concatenation assignment

along with Script 5.5. If you need

operator?

help, revisit the **hello.php** script from

Chapter 3 (Script 3.7).

■

What is the impact of having a newline

in a string printed to the browser? How

■

Rewrite the **print** statement in the final

do you convert a newline character to

version of **handle\_post.php** (Script 5.7),

a break tag?

so that it uses single quotation marks

and concatenation instead of double

■

What problems can occur when HTML

quotation marks.

is entered into form elements whose

values will later be printed back to the

■

Create another HTML form for taking

Web browser? What steps can be taken

string values. Then create the PHP

to sanctify submitted form data?

script that receives the form data,

addresses any HTML or PHP code,

■

What function makes data safe to pass

manipulates the data in some way,

in a URL?

and prints out the results.

■

How do you escape problematic

characters within a string? What

happens if you do not escape them?

■

The characters in a string are indexed

beginning at what number?

■

What does the **trim()** function do?

114 Chapter

5

[**6**](#index_split_000.html#p7)

[Control Structures](#index_split_000.html#p7)

Control structures—conditionals and loops—

are a staple of programming languages. PHP

**In This Chapter**

has two conditionals—**if** and **switch**—both

of which you’ll master in this chapter. Condi-

Creating the HTML Form

116

tionals allow you to establish a test and then

The if Conditional

119

perform actions based on the results. This

Validation Functions

122

functionality provides the ability to make Web

sites even more dynamic.

Using else

126

The discussion of **if** conditionals requires

More Operators

129

introduction of two last categories of

Using elseif

138

operators: comparison and logical (you’ve

The Switch Conditional

142

already seen the arithmetic and assign-

ment operators in the previous chapters).

The for Loop

146

You’ll commonly use these operators in

Review and Pursue

150

your conditionals, along with the Boolean

concepts of TRUE and FALSE.

Finally, this chapter introduces loops,

which allow you to repeat an action for a

specified number of iterations. Loops can

save you programming time and help you

get the most functionality out of arrays, as

you’ll see in the next chapter.

![Image 146](index-137_1.png)

[**Creating the**](#index_split_000.html#p7)

[**HTML Form**](#index_split_000.html#p7)

As with the previous chapters, the examples

in this chapter are based on an HTML form

that sends data to a PHP page. In this case,

the form is a simple registration page that

requests the following information **A**:

■

Email address

■

Password

■

Confirmation of the password

■

Year of birth (to verify age)

**A** The HTML form used in this chapter.

■

Favorite color (for customization purposes)

**Script**

■

Agreement to the site’s terms

**6.1** This pseudo-registration form is the

basis for the examples in this chapter.

(a common requirement)

1

<!DOCTYPE html PUBLIC "-//W3C//DTD

The following steps walk through the creation

XHTML 1.0 Transitional//EN"

of this form before getting into the PHP code.

2 "http://www.w3.org/TR/xhtml1/DTD/

xhtml1-transitional.dtd">

**To create the HTML form:**

3 <html

xmlns="http://www.w3.org/1999/

xhtml" xml:lang="en" lang="en">

**1.** Begin a new HTML document in

4 <head>

your text editor or IDE, to be named

5

<meta http-equiv="Content-Type"

**register.html** (**Script 6.1**):

content="text/html;

charset=utf-8"/>

6 <title>Registration

Form</title>

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

7 </head>

➝ **XHTML 1.0 Transitional//EN"**

8 <body>

**"http://www.w3.org/TR/xhtml1/**

9

<!-- Script 6.1 - register.html -->

10 <div><p>Please complete this form to

 ➝ **DTD/xhtml1-transitional.dtd">**

register:</p>

**<html xmlns="http://www.w3.org/**

11

➝ **1999/xhtml" xml:lang="en"**

12 <form action="handle\_reg.php"

➝ **lang="en">**

method="post">

**<head>**

13

14

<p>Email Address: <input type="text"

**<meta**

**http-equiv="Content-Type"**

name="email" size="30" /></p>

 ➝ **content="text/html;**

15

 ➝ **charset=utf-8"/>**

16

<p>Password: <input type="password"

**<title>Registration**

**Form</title>**

name="password" size="20" /></p>

**</head>**

17

18

<p>Confirm Password: <input

**<body>**

type="password" name="confirm"

**<!-- Script 6.1 - register.html -->**

size="20"

/></p>

**<div><p>Please complete this form**

19

➝ **to register:</p>**

code continues on next page

116 Chapter

6

![Image 147](index-138_1.png)

**Script 6.1** continued

**2.** Create the initial **form** tag:

20

<p>Year You Were Born: <input

**<form action="handle\_reg.php"**

type="text" name="year"

➝ **method="post">**

value="YYYY" size="4" /></p>

As with many of the previous examples,

21

22 <p>Favorite

Color:

this page uses the POST method. The

23 <select

name="color">

handling script, identified by the **action**

24

<option value="">Pick One</option>

attribute, will be **handle\_reg.php**, found

25 <option

value="red">Red</option>

in the same directory as the HTML form.

26 <option

value="yellow">Yellow

</option>

**3.** Create inputs for the email address

27 <option

value="green">Green</option>

and passwords:

28 <option

value="blue">Blue</option>

29 </select></p>

**<p>Email Address: <input**

30

➝ **type="text" name="email"**

31

<p><input type="checkbox"

➝ **size="30" /></p>**

name="terms" value="Yes" /> I agree

**<p>Password: <input**

to the terms (whatever they may

➝ **type="password" name="password"**

be).</p>

32

➝ **size="20" /></p>**

33

<input type="submit" name="submit"

**<p>Confirm Password: <input**

value="Register"

/>

➝ **type="password" name="confirm"**

34

➝ **size="20" /></p>**

35 </form>

36

These lines should be self-evident. Each

37 </div>

line is wrapped in HTML **<p></p>** tags to

38 </body>

improve the spacing in the Web browser.

39 </html>

Also, note that two password inputs are

created—the second is used to confirm

the text entered in the first. Password

input types don’t reveal what the user

enters **B**, so it’s a standard policy to

**B** A password input type, as it’s being filled out.

require the user to enter passwords

twice (thereby ensuring that users know

exactly what password they provided).

**4.** Create an input for the user’s birth year:

**<p>Year You Were Born: <input**

➝ **type="text" name="year"**

➝ **value="YYYY" size="4" /></p>**

Rather than use a drop-down menu that

displays 50 or 100 years, have users

enter their birth year in a text box. By

presetting the **value** attribute of the

input, you make the text box indicate

the proper format for the year **A**.

continues on next page

Control Structures 117

**5.** Create a drop-down menu for the user’s a hypothetical example anyway). In any

favorite color:

case, using this element, you’ll be able

**<p>Favorite Color:**

to see how checkboxes are treated by

**<select name="color">**

the handling PHP script.

**<option value="">Pick One</option>**

**7.** Add a submit button and close the form:

**<option value="red">Red</option>**

**<input type="submit" name=**

**<option value="yellow">Yellow**

 ➝ **"submit" value="Register" />**

➝ **</option>**

**</form>**

**<option value="green">Green</option>**

**<option value="blue">Blue</option>**

**8.** Complete the HTML page:

**</select></p>**

**</div>**

**</body>**

The truth is that I’m adding this input so

**</html>**

that it can be used for a specific example

later in the chapter, but it might be used

**9.** Save the file as **register.html**, place

to customize the look of the site after the

it in the proper directory for your PHP-

user logs in. Naturally, you can add as

enabled server, and load the page in

many colors as you want here.

your Web browser.

**6.** Create a check box for the user to

agree to the site’s terms:

**Registration pages should always have**

**users confirm their password and possibly**

**<p><input type="checkbox"**

**their username or email address (whatever**

➝ **name="terms" value="Yes" />**

**information will be used to log in).**

➝ **I agree to the terms (whatever**

➝ **they may be).</p>**

**Most registration pages use either a nick-**

**name or an email address for the username.**

Many sites have some sort of terms or

**If you use the email address as a username,**

licensing that the user must indicate

**it’s easier for your users to remember their**

acceptance of, normally by checking a

**registration information (a user may have**

box. This particular form doesn’t have

**only a couple of email addresses but a gazil-**

**lion usernames for different sites around the**

a link to where the user can read the

**Web). Furthermore, email addresses are, by**

terms, but it probably doesn’t matter

**their nature, unique to an individual, whereas**

as no one reads them (and this is just

**usernames are not.**

118 Chapter

6

![Image 148](index-140_1.png)

![Image 149](index-140_2.png)

![Image 150](index-140_3.png)

![Image 151](index-140_4.png)

that format isn’t syntactically required. You’ll

[**The if Conditional**](#index_split_000.html#p7)

also see people use this syntax:

The basic programming conditional is

**if ( *condition*)**

the standard **if** (what used to be called

**{**

an **if**\-**then** conditional—the **then** is

***statement(s)*****;**

now implied). The syntax for this kind of

**}**

conditional is simple:

How you arrange your curly brackets is a

**if ( *condition*) {**

matter of personal preference—and the

***statement(s)*****;**

source of minor online skirmishes. Just

**}**

pick a style you like and stick to it.

The condition must go within parentheses;

Failure to use a semicolon after each

then the statement(s) are placed within curly

statement, forgetting an opening or closing

brackets. The statements are commands to

parenthesis or curly bracket, or using a

be executed (for example, printing a string or

semicolon after either of the braces will

adding two numbers together). Each separate

cause errors to occur. Be mindful of your

statement (or command) must have its own

syntax as you code with conditionals!

semicolon indicating the end of the line, but

PHP uses the Boolean concepts of TRUE

there is no limit on the number of statements

and FALSE when determining whether to

that can be associated with a conditional.

execute the statements. If the condition is

Programmers commonly indent these

TRUE, the statements are executed; if it’s

statements from the initial **if** line to indicate

FALSE, they are not executed **A**.

that they’re the result of a conditional, but

continues on next page

**A** How an **IF** conditional affects the program flow

of a script.

Control Structures 119

Over the course of this chapter (most of it,

**Script 6.2** This shell of a PHP script will be

anyway), a PHP script will be developed

expanded to completely validate the form data.

until it fully validates the **register.html**

1

<!DOCTYPE html PUBLIC "-//W3C//DTD

form data. To start, this first version of the

XHTML 1.0 Transitional//EN"

script will just create the basic shell of the

2 "http://www.w3.org/TR/xhtml1/DTD/

xhtml1-transitional.dtd">

validation process, defining and using a

3 <html

xmlns="http://www.w3.org/1999/

variable with a Boolean value that will track

xhtml" xml:lang="en" lang="en">

the success of the validation process.

4 <head>

5

<meta http-equiv="Content-Type"

**To create an if conditional:**

content="text/html;

charset=utf-8"/>

**1.** Begin a new document in your

6 <title>Registration</title>

text editor or IDE, to be named

7 </head>

**handle\_reg.php** (**Script 6.2**):

8 <body>

9 <h1>Registration

Results</h1>

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

10 <?php // Script 6.2 - handle\_reg.php

➝ **XHTML 1.0 Transitional//EN"**

11 /\* This script receives seven values

**"http://www.w3.org/TR/xhtml1/**

from

register.html:

12 email, password, confirm, year, terms,

 ➝ **DTD/xhtml1-transitional.dtd">**

color, submit \*/

**<html xmlns="http://www.w3.org/**

13

➝ **1999/xhtml" xml:lang="en"**

14 // Address error management, if you

➝ **lang="en">**

want.

**<head>**

15

16 // Flag variable to track success:

**<meta**

**http-equiv="Content-Type"**

**17 $okay = TRUE;**

 ➝ **content="text/html;**

18

 ➝ **charset=utf-8"/>**

19 // If there were no errors, print a

**<title>Registration</title>**

success

message:

**</head>**

**20 if ($okay) {**

**21**

**print '<p>You have been**

**<body>**

**successfully registered (but**

**<h1>Registration Results</h1>**

**not**

**really).</p>';**

**2.** Begin the PHP section and address

**22 }**

23 ?>

error management, if necessary:

24 </body>

**<?php // Script 6.2 - handle\_reg.php**

25 </html>

If you don’t have **display\_errors**

enabled, or if **error\_reporting** is

set to the wrong level, see Chapter 3,

“HTML Forms and PHP,” for the lines to

include here to alter those settings.

**3.** Create a flag variable:

**$okay = TRUE;**

To validate the form data, a flag

variable will be used to represent

whether or not the form was properly

120 Chapter

6

![Image 152](index-142_1.png)

![Image 153](index-142_2.png)

completed. It’s called a “flag” variable

**5.** Complete the PHP section and the

because the variable stores a simple

HTML page:

value that indicates a status. For

**?>**

example: yes, the form was filled out

**</body>**

entirely or no, it was not.

**</html>**

The variable is initialized with a

**6.** Save the file as **handle\_reg.php**, place

Boolean value of TRUE, meaning that

it in the proper directory for your PHP-

the assumption is that the form was

enabled server (in the same directory as

completed properly. Understand that

**register.html**), and test both in your

Booleans are case-insensitive in PHP,

Web browser **B** and **C**.

so you could also write True or true.

Of course, the fact is that this particular

**4.** Print a message if everything is all right:

script will always print the success

**if ($okay) {**

message, as no code will set **$okay**

**print '<p>You have been**

to **FALSE**. You can even run the script

 ➝ **successfully registered**

directly and see the same result.

 ➝ **(but not really).</p>';**

**}**

**If the statement area of your conditional**

**is only one line long, you technically don’t need**

Over the course of this chapter,

**the curly brackets. In that case, you can write**

validation routines will be added to this

**the conditional using either of these formats:**

script, checking the submitted form

data. If any data fails a routine, then

**if ( *condition*) *statement*;**

**$okay** will be set to FALSE. In that case,

**or**

this conditional will also be FALSE, so

the message won’t be printed. However,

**if ( *condition*)**

if the data passes every validation

***statement*;**

routine, then **$okay** will still be TRUE, in

**You may run across code in these formats.**

which case this message will be printed.

**However, I think it’s best to always use the**

**multiline format, with the curly brackets (as**

**demonstrated in the syntax introduction) to**

**improve consistency and minimize errors.**

**C** …results in just this.

**B** Filling out the HTML form to any degree…

Control Structures 121

[**Validation Functions**](#index_split_000.html#p7)

PHP has dozens of functions commonly

used to validate form data. Of these

functions, the three most important ones

are used in this chapter’s examples.

First up is the **empty()** function, which

checks to see if a given variable has an

“empty” value. A variable is considered to

have an empty value if the variable has no

value, has a value of 0, or has a value of

FALSE. In any of these cases, the function

returns TRUE; otherwise, it returns FALSE:

**$var1 = 0;**

**$var2 = 'something';**

**$var3 = ' '; // An empty string**

**empty($var); // TRUE, no defined value**

**empty($var1); // TRUE, empty value**

**empty($var2); // FALSE, non-empty value**

**empty($var3); // TRUE, empty value**

This function is perfect for making sure

that text boxes in forms have been filled

out. For example, if you have a text input

named email and the user doesn’t enter

anything in it before submitting the form,

then the **$\_POST\['email'\]** variable will exist

but will have an empty value.

Next is the **isset()** function, which is

almost the opposite of **empty()**, albeit with

a slight difference. The **isset()** function

returns TRUE if a variable has any value

(including 0, FALSE, or an empty string).

If the variable does not have a value,

**isset()** returns FALSE:

**$var1 = 0;**

**$var2 = 'something';**

**$var3 = ' '; // An empty string**

**isset($var); // FALSE, no defined**

**value**

**isset($var1); // TRUE**

**isset($var2); // TRUE**

**isset($var3); // TRUE**

122 Chapter

6

**Script 6.3** Using **if** conditionals and the **empty()** The **isset()** function is commonly used

function, this PHP script checks if email address

to validate nontext form elements like

and password values were provided.

checkboxes, radio buttons, and select menus.

1

<!DOCTYPE html PUBLIC "-//W3C//DTD

Finally, the **is\_numeric()** function returns

XHTML 1.0 Transitional//EN"

2 "http://www.w3.org/TR/xhtml1/DTD/

TRUE if the submitted variable has a valid

xhtml1-transitional.dtd">

numerical value and FALSE otherwise.

3 <html

xmlns="http://www.w3.org/1999/

Integers, decimals, and even strings (if

xhtml" xml:lang="en" lang="en">

they’re a valid number) can all pass the

4 <head>

5

<meta http-equiv="Content-Type"

**is\_numeric()** test:

content="text/html;

**$var1 = 2309;**

charset=utf-8"/>

6 <title>Registration</title>

**$var2 = '80.23';**

**7**

**<style type="text/css"**

**$var3 = 'Bears';**

**media="screen">**

**is\_numeric($var1); // TRUE**

**8**

**.error { color: red; }**

**is\_numeric($var2); // TRUE**

**9 </style>**

10 </head>

**is\_numeric($var3); // FALSE**

11 <body>

Let’s start applying these functions to the

12 <h1>Registration

Results</h1>

13 <?php // Script 6.3 - handle\_reg.php #2

PHP script to perform data validation.

14 /\* This script receives seven values

from

register.html:

**To validate form data:**

15 email, password, confirm, year, terms,

color, submit \*/

**1.** Open **handle\_reg.php** (Script 6.2)

16

in your text editor or IDE, if it is not

17 // Address error management, if you want.

18

already open.

19 // Flag variable to track success:

**2.** Within the document’s head, define a

20 $okay = TRUE;

CSS class (**Script 6.3**):

21

22 // Validate the email address:

**<style type="text/css"**

**23 if (empty($\_POST\['email'\])) {**

**24**

**print '<p class="error">Please**

➝ **media="screen">**

**enter your email address.</p>';**

**.error { color: red; }**

**25**

**$okay = FALSE;**

**</style>**

**26 }**

27

This CSS class will be used to format

28 // Validate the password:

any printed registration errors.

**29 if (empty($\_POST\['password'\])) {**

**30**

**print '<p class="error">Please**

**3.** Validate the email address:

**enter your password.</p>';**

**if (empty($\_POST\['email'\])) {**

**31**

**$okay = FALSE;**

**32 }**

**print '<p class="error">Please**

33

 ➝ **enter your email address.</p>';**

34 // If there were no errors, print a

**$okay = FALSE;**

success

message:

**}**

35 if ($okay) {

36

print '<p>You have been successfully

continues on next page

registered (but not really).</p>';

37 }

38 ?>

39 </body>

40 </html>

Control Structures 123

![Image 154](index-145_1.png)

![Image 155](index-145_2.png)

This **if** conditional uses the code

**empty($\_POST\['email'\])** as its

condition. If that variable is empty,

meaning it has no value, a value of

0, or a value of an empty string, the

conditional is TRUE. In that case, the

**print** statement will be executed and

the **$okay** variable will be assigned

a value of FALSE (indicating that

everything is not okay).

If the variable isn’t empty, then the

conditional is FALSE, the **print** function

is never called, and **$okay** will retain its

original value.

**A** If you omit the email address or password

form input…

**4.** Repeat the validation for the password:

**if (empty($\_POST\['password'\])) {**

**print '<p class="error">Please**

 ➝ **enter your password.</p>';**

**$okay = FALSE;**

**}**

This is a repeat of the email validation,

but with the variable name and **print**

**B** …you’ll see messages like these.

statement changed accordingly. The

other form inputs will be validated in time.

All of the printed error messages are

placed within HTML paragraph tags that

have a **class** value of error. By doing so,

the CSS formatting will be applied (i.e.,

the errors will be printed in red, not that

it’ll be apparent in this book’s figures).

**5.** Save the file as **handle\_reg.php**, place

it in the same directory as **register.**

**html** (on your PHP-enabled server), and

test both the form and the script in your

Web browser **A** and **B**.

124 Chapter

6

**6.** Resubmit the form in different states of completeness to test the results

some more.

If you do provide both email address

and password values, the result will

be exactly like that in Figure C in the

section “The if Conditional,” because

the **$okay** variable will still have a value

of TRUE.

**When you use functions within**

**conditionals, as with empty() here, it’s easy**

**to forget a closing parenthesis and see a parse**

**error. Be extra careful with your syntax when**

**you’re coding any control structure.**

**One use of the isset() function is to**

**avoid referring to a variable unless it exists. If**

**PHP is set to report notices (see “Error Report-**

**ing” in Chapter 3), then, for example, using**

**$var if it has not been defined will cause an**

**error. You can avoid this by coding**

**if (isset($var)) {**

**// Do whatever with $var.**

**}**

**Even though almost all form data is sent**

**to a PHP script as strings, the is\_numeric()**

**function can still be used for values coming**

**from a form because it can handle strings that**

**contain only numbers.**

**The isset() function can take any**

**number of variables as arguments:**

**if (isset($var1, $var2)) {**

**print 'Both variables exist.';**

**}**

**If all the named variables are set, the function**

**returns TRUE; if any variable is not set, the**

**function returns FALSE.**

Control Structures 125

![Image 156](index-147_1.png)

![Image 157](index-147_2.png)

![Image 158](index-147_3.png)

![Image 159](index-147_4.png)

![Image 160](index-147_5.jpg)

[**Using else**](#index_split_000.html#p7)

The next control structure we’ll discuss

is the **if**\-**else** conditional. This control

structure allows you to execute one or

more statements when a condition is TRUE

and execute one or more other statements

when the condition is FALSE:

**if ( *condition*) {**

***statement(s)*****;**

**} else {**

***other\_statement(s)*****;**

**}**

The important thing to remember when

using this construct is that unless the

condition is explicitly met, the **else**

statement will be executed. In other words,

**A** How an **IF-ELSE** conditional affects the

the statements after the **else** constitute

program flow of a script.

the default action, whereas the statements

after the **if** condition are the exception to

**Script 6.4** By adding an **if-else** conditional, this

the rule **A**.

script validates the birth year and creates a new

variable in the process.

Let’s rewrite the **handle\_reg.php** page,

incorporating an **if**\-**else** conditional to

1

<!DOCTYPE html PUBLIC "-//W3C//DTD

XHTML 1.0 Transitional//EN"

validate the birth year. In the process, a

2 "http://www.w3.org/TR/xhtml1/DTD/

new variable will be created, representing

xhtml1-transitional.dtd">

the user’s age.

3 <html

xmlns="http://www.w3.org/1999/

xhtml" xml:lang="en" lang="en">

**To use else:**

4 <head>

5

<meta http-equiv="Content-Type"

**1.** Open **handle\_reg.php** (Script 6.3)

content="text/html;

in your text editor or IDE, if it is not

charset=utf-8"/>

6 <title>Registration</title>

already open.

7

<style type="text/css"

**2.** After the password validation but

media="screen">

before the **$okay** conditional, begin

8

.error { color: red; }

9 </style>

a new conditional (**Script 6.4**):

10 </head>

**if (is\_numeric($\_POST\['year'\])) {**

11 <body>

12 <h1>Registration

Results</h1>

Because the **year** variable should be a

13 <?php // Script 6.4 - handle\_reg.php #3

number, you can use the **is\_numeric()**

14 /\* This script receives seven values

function to check its value, rather than

from

register.html:

**empty()**. This is a basic start to this

15 email, password, confirm, year, terms,

color, submit \*/

particular form element’s validation;

16

later scripts will expand on this.

code continues on next page

126 Chapter

6

**Script 6.4** continued

**3.** Create a new variable:

17 // Address error management, if you

**$age = 2011 - $\_POST\['year'\];**

want.

If the **$\_POST\['year'\]** variable has

18

a numeric value (meaning that the

19 // Flag variable to track success:

20 $okay = TRUE;

conditional is TRUE), then the **$age**

21

variable is assigned the value of the

22 // Validate the email address:

current year minus the provided year.

23 if (empty($\_POST\['email'\])) {

For now, without knowledge of PHP’s

24

print '<p class="error">Please

date functions, just hard-code the

enter your email address.</p>';

25

$okay = FALSE;

current year into the equation.

26 }

**4.** Add an **else** clause:

27

28 // Validate the password:

**} else {**

29 if (empty($\_POST\['password'\])) {

**print '<p class="error">Please**

30

print '<p class="error">Please

 ➝ **enter the year you were born**

enter your password.</p>';

 ➝ **as four digits.</p>';**

31

$okay = FALSE;

32 }

**$okay = FALSE;**

33

**}**

34 // Validate the birth year:

If the year does not have a numeric

**35 if (is\_numeric($\_POST\['year'\])) {**

**36**

**$age = 2011 - $\_POST\['year'\];**

value, an error message is printed and

**// Calculate age this year.**

the **$okay** variable is set to FALSE (as is

**37 } else {**

the case if any validation routine fails).

**38**

**print '<p class="error">Please**

**enter the year you were born as**

**5.** After the final **print** statement but

**four**

**digits.</p>';**

within the same **$okay** conditional, also

**39**

**$okay = FALSE;**

print out the value of **$age**:

**40 }**

41

**print "<p>You will turn $age this**

42 // If there were no errors, print a

➝ **year.</p>";**

success

message:

If the **$okay** variable still has a value of

43 if ($okay) {

44

print '<p>You have been successfully

TRUE, then the submitted data passed

registered (but not really).</p>';

every validation routine. This means

**45**

**print "<p>You will turn $age**

that the user’s age has been calculated

**this**

**year.</p>";**

(in the sense of how old they’ll be at

46 }

some point this year), and it can be

47 ?>

48 </body>

printed, too.

49 </html>

continues on next page

Control Structures 127

![Image 161](index-149_1.png)

![Image 162](index-149_2.png)

![Image 163](index-149_3.png)

**6.** Save your script, place it in the same

directory as **register.html** (on your

PHP-enabled server), and test it in your

Web browser again **B**, **C**,  and **D**.

**Another good validation function is**

**checkdate(), which you can use to confirm**

**that a date exists (or existed in the past). You**

**would use it like so:**

**if (checkdate($month, $day, $year)) {…**

**B** Test the form again, without providing a year

value, and…

**C** …you’ll see this.

**D** If the user provides a numeric value for their

birth year, the user’s age will now be calculated

and printed (assuming that an email address and

password was also provided).

128 Chapter

6

**TABLE 6.1 PHP’s Operators**

[**More Operators**](#index_split_000.html#p7)

**Operator**

**Usage**

**Type**

Previous chapters discussed most of

PHP’s operators along with the variable

+

Addition

Arithmetic

types that use them. These operators

\-

Subtraction

Arithmetic

include arithmetic for numbers: addition

\*

Multiplication

Arithmetic

(**+**), subtraction (**\-**), multiplication (**\***), and

/

Division

Arithmetic

division (**/**), along with the incremental

%

Modulus (remainder Arithmetic

(**++**) and decremental (**\--**) shortcuts for

of a division)

increasing or decreasing the value of a

\+ +

Incrementation

Arithmetic

number by 1. Then there is the assignment

\- -

Decrementation

Arithmetic

operator (**\=**), which is used to set the value

of a variable, regardless of type. You’ve

\=

Assigns a value

Assignment

to a variable

also learned about concatenation (**.** ),

which appends one string to another.

\= =

Equality

Comparison

! =

Inequality

Comparison

When it comes to creating conditionals, the

comparison and logical operators are the

<

Less than

Comparison

most important. **Table 6.1** lists the operators

\>

Greater than

Comparison

to be discussed, along with those you’ve

< =

Less than or

Comparison

already seen.

equal to

\> =

Greater than

Comparison

**Comparison**

or equal to

!

Negation

Logical

When the assignment operator (the

equals sign) was introduced in Chapter 2,

AND

And

Logical

“Variables,” you learned that its meaning

&&

And

Logical

isn’t exactly what you’d conventionally think

OR

Or

Logical

it to be. The line

||

Or

Logical

**$var = 5;**

XOR

Or not

Logical

doesn’t state that **$var** is equal to 5 but

.

Concatenation

String

that it is assigned the value of 5. This is

an important distinction.

When you’re writing conditionals, you’ll

often want to see if a variable is equal to

a specific value (to match usernames or

passwords, perhaps), which you can’t do

with the equals sign alone (because that

operator is used for assigning a value, not

equating values). Instead, for comparisons,

use the equality operator (**\= =**):

**$var = 5;**

**if ($var == 5) { ...**

continues on next page

Control Structures 129

These two lines of code together first

**Script 6.5** This version of the form-handling

establish the value of **$var** as 5 and then

script uses comparison operators to validate

the password and year values.

make a TRUE conditional that checks

if **$var** is equal to 5. This example

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

demonstrates the significant difference

1.0

Transitional//EN"

2 "http://www.w3.org/TR/xhtml1/DTD/

one more equals sign makes in your

xhtml1-transitional.dtd">

PHP code and why you must distinguish

3 <html

xmlns="http://www.w3.org/1999/

carefully between the assignment and

xhtml" xml:lang="en" lang="en">

comparison operators.

4 <head>

5

<meta http-equiv="Content-Type"

The next comparison operator—not equal

content="text/html;

charset=utf-8"/>

to—is represented by an exclamation

6 <title>Registration</title>

mark coupled with an equals sign (**!=**).

7

<style type="text/css" media="screen"> The remaining comparison operators

8

.error { color: red; }

9 </style>

are identical to their mathematical

10 </head>

counterparts: less than (**<** ), greater than (**\>** ), 11 <body>

less than or equal to (**< =**), and greater than

12 <h1>Registration

Results</h1>

or equal to (**\> =**).

13 <?php // Script 6.5 - handle\_reg.php #4

14 /\* This script receives seven values

As a demonstration of comparison

from

register.html:

operators, you’ll check that the user’s birth

15 email, password, confirm, year, terms,

year is before 2011 and that the confirmed

color, submit \*/

password matches the original password.

16

17 // Address error management, if you want.

18

**To use comparison operators:**

19 // Flag variable to track success:

20 $okay = TRUE;

**1.** Open **handle\_reg.php** (Script 6.4) in

21

your text editor or IDE, if it is not already.

22 // Validate the email address:

**2.** After the password validation, check that

23 if (empty($\_POST\['email'\])) {

24

print '<p class="error">Please enter

the two passwords match (**Script 6.5**):

your email address.</p>';

**if ($\_POST\['password'\]**

25

$okay = FALSE;

➝ **!= $\_POST\['confirm'\]) {**

26 }

**print '<p class="error">Your**

27

28 // Validate the password:

 ➝ **confirmed password does**

29 if (empty($\_POST\['password'\])) {

 ➝ **not match the original**

30

print '<p class="error">Please enter

 ➝ **password.</p>';**

your

password.</p>';

**$okay = FALSE;**

31

$okay = FALSE;

**}**

32 }

33

To compare these two string values, use

34 // Check the two passwords for equality:

the inequality operator. Alternatively,

**35 if ($\_POST\['password'\] !=**

**$\_POST\['confirm'\])**

**{**

you could use one of the string

**36**

**print '<p class="error">Your**

comparison functions (see Chapter 5,

**confirmed password does not match**

“Using Strings”), but **!=** is just fine.

**the original password.</p>';**

code continues on next page

130 Chapter

6

**Script 6.5** continued

**3.** After the year validation, report an error

if the year is greater than or equal to 2011:

**37**

**$okay = FALSE;**

**38 }**

**if ($\_POST\['year'\] >= 2011) {**

39

**print '<p class="error">Either**

40 // Validate the birth year:

 ➝ **you entered your birth year**

41 if (is\_numeric($\_POST\['year'\])) {

 ➝ **wrong or you come from the**

42

$age = 2011 - $\_POST\['year'\];

// Calculate age this year.

 ➝ **future!</p>';**

43 } else {

**$okay = FALSE;**

44

print '<p class="error">Please enter

**}**

the year you were born as four

digits.</p>';

If the user entered their year of birth as

45

$okay = FALSE;

2011 or later, it’s presumably a mistake.

46 }

(If you’re reading this book after 2011,

47

change the year accordingly).

48 // Check that they were born before

this

year:

continues on next page

**49 if ($\_POST\['year'\] >= 2011) {**

**50**

**print '<p class="error">Either you**

**entered your birth year wrong or**

**you come from the future!</p>';**

**51**

**$okay = FALSE;**

**52 }**

53

54 // If there were no errors, print a

success

message:

55 if ($okay) {

56

print '<p>You have been successfully

registered (but not really).</p>';

57

print "<p>You will turn $age this

year.</p>";

58 }

59

60 ?>

61 </body>

62 </html>

Control Structures 131

![Image 164](index-153_1.png)

![Image 165](index-153_2.png)

**4.** Save your script, place it in the same

directory as **register.html** (on your

PHP-enabled server), and test it in your

Web browser again **A** and **B**.

**Before you compare two string values**

**that come from a form (like the password and**

**confirmed password), it’s a good idea to apply**

**the trim() function to both, to get rid of any**

**errant spaces. I didn’t do so here, so as not**

**to overcomplicate matters, but this habit is**

**recommended.**

**Another method of checking that a text**

**input type has been filled out (as opposed to**

**A**

**using the empty() function) is this:**

Run the form once again…

**if (strlen($var) > 0 ) {**

**// $var is okay.**

**}**

**In an if conditional, if you make the**

**mistake of writing $var = 5 in place of**

**$var == 5, you’ll see that the corresponding**

**B** …with two new validation checks in place.

**conditional statements are always executed.**

**This happens because although the condi-**

**tion $var == 5 may or may not be TRUE, the**

**condition $var = 5 is always TRUE.**

**Some programmers advocate reverse**

**conditionals—for example, writing**

**if (5 == $var) {**

**Although it looks awkward, if you inad-**

**vertently code 5 = $var, an error results**

**(allowing you to catch the mistake more eas-**

**ily) because the number 5 can’t be assigned**

**another value.**

132 Chapter

6

**Logical**

**Nesting Conditionals**

Writing conditions in PHP comes down

Besides using logical operators to cre-

to identifying TRUE or FALSE situations.

ate more complex conditionals, you

You can do this by using functions and

can use nesting for this purpose (the

comparative operators, as you’ve already

process of placing one control structure

seen. Logical operators—the final operator

inside another). The key to doing so is

type discussed in this chapter—help you

to place the interior conditional as the

create more elaborate or obvious constructs.

statement(s) section of the exterior

In PHP, one example of a TRUE condition

conditional. For example:

is simply a variable name that has a value

**if ( *condition1*) {**

that isn’t zero, an empty string, or FALSE,

**if**

**( *condition2*) {**

such as

***statement(s)2*****;**

**$var = 5;**

**} else { // condition2**

**if ($var) { ...**

**else**

You’ve already seen this with the **$okay**

***other\_statement(s)2*****;**

variable being used in the handling

**} // End of 2**

PHP script.

**} else { // condition1 else**

A condition is also TRUE if it makes

***other\_statement(s)1*****;**

logical sense:

**} // End of 1**

**if (5 >= 3) { ...**

As you can see from this example, you

A condition will be FALSE if it refers to a

can cut down on the complexity of these

structures by using extensive indenta-

variable and that variable has no value (or

tions and comments. As long as every

a value of 0 or an empty string), or if you’ve

conditional is syntactically correct, there

created an illogical construct. The following

are no rules as to how many levels of

condition is always FALSE:

nesting you can have, whether you use

**if (5 <= 3) { ...**

an **else** clause or even whether a sub-

conditional is part of the **if** or the **else**

In PHP, the exclamation mark (**!** ) is the not

section of the main conditional.

operator. You can use it to invert the TRUE/

FALSE status of a statement. For example:

**$var = 'value';**

**if ($var) {... // TRUE**

**if (!$var) {... // FALSE**

**if (isset($var)) {... // TRUE**

**if (!isset($var)) {... // FALSE**

**if (!empty($var)) {... // TRUE**

To go beyond simple one-part conditions,

PHP supports five more types of logical

operators: two versions of and (**AND** and **&&** ), two versions of or (**OR** and **||**—a character

called the pipe, put together twice), and

continues on next page

Control Structures 133

or not (**XOR**). When you have two options

**Script 6.6** Here the handling PHP script is

for one operator (as with and and or), they

changed so that the year validation routine uses

both multiple and nested conditions. Also, the

differ only in precedence. For almost every

terms of agreement check box is now validated.

situation, you can use either version of and

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

or either version of or interchangeably.

1.0

Transitional//EN"

Using parentheses and logical operators,

2 "http://www.w3.org/TR/xhtml1/DTD/

you can create even more complex **if**

xhtml1-transitional.dtd">

3 <html

xmlns="http://www.w3.org/1999/

conditionals. For an **AND** conditional, every

xhtml" xml:lang="en" lang="en">

conjoined part must be TRUE in order for

4 <head>

the whole conditional to be TRUE. With **OR**,

5

<meta http-equiv="Content-Type"

at least one subsection must be TRUE to

content="text/html;

charset=utf-8"/>

render the whole condition TRUE. These

6 <title>Registration</title>

7

<style type="text/css" media="screen"> conditionals are TRUE:

8

.error { color: red; }

**if ( (5 <= 3) OR (5 >= 3) ) { ...**

9 </style>

**if ( (5 > 3) AND (5 < 10) ) { ...**

10 </head>

11 <body>

These conditionals are FALSE:

12 <h1>Registration

Results</h1>

**if ( (5 != 5) AND (5 > 3) ) { ...**

13 <?php // Script 6.6 - handle\_reg.php #5

14 /\* This script receives seven values

**if ( (5 != 5) OR (5 < 3) ) { ...**

from

register.html:

As you construct your conditionals,

15 email, password, confirm, year, terms,

color, submit \*/

remember two important things: first, in

16

order for the statements that are the result

17 // Address error management, if you want.

of a conditional to be executed, the entire

18

conditional must have a TRUE value;

19 // Flag variable to track success:

second, by using parentheses, you can

20 $okay = TRUE;

21

ignore rules of precedence and ensure

22 // Validate the email address:

that your operators are addressed in the

23 if (empty($\_POST\['email'\])) {

order of your choosing.

24

print '<p class="error">Please enter

your email address.</p>';

To demonstrate logical operators, let’s add

25

$okay = FALSE;

more conditionals to the **handle\_reg.php**

26 }

page. You’ll also nest one of the year

27

conditionals inside another conditional (see

28 // Validate the password:

the sidebar “Nesting Conditionals” for more).

29 if (empty($\_POST\['password'\])) {

30

print '<p class="error">Please enter

your

password.</p>';

**To use logical operators:**

31

$okay = FALSE;

**1.** Open **handle\_reg.php** (Script 6.5) in your

32 }

33

text editor or IDE, if it is not already open.

34 // Check the two passwords for equality:

**2.** Delete the existing year validations

35 if ($\_POST\['password'\] !=

(**Script 6.6**).

$\_POST\['confirm'\])

{

36

print '<p class="error">Your confirmed

You’ll entirely rewrite these conditionals

password does not match the original

as one nested conditional, so it’s best to

password.</p>';

get rid of the old versions entirely.

code continues on next page

134 Chapter

6

**Script 6.6** continued

**3.** Check that the year variable is a four-

digit number:

37

$okay = FALSE;

38 }

**if ( is\_numeric($\_POST\['year'\]) AND**

39

➝ **(strlen($\_POST\['year'\]) == 4) ) {**

40 // Validate the year:

**41 if ( is\_numeric($\_POST\['year'\]) AND**

This conditional has two parts. The first

**(strlen($\_POST\['year'\]) == 4) ) {**

you’ve already seen—it tests for a valid

42

numeric value. The second part gets

**43**

**// Check that they were born**

the length of the year variable (using

**before**

**2011.**

the **strlen()** function) and checks if the

**44**

**if ($\_POST\['year'\] < 2011) {**

**45**

**$age = 2011 - $\_POST\['year'\];**

length value is equal to 4. Because of

**// Calculate age this year.**

the **AND**, this conditional is TRUE only if

**46**

**} else {**

both conditions are met.

**47**

**print '<p class="error">Either**

**you entered your birth year**

**4.** Create a subconditional to check if the

**wrong or you come from the**

year value is before 2011:

**future!</p>';**

**if ($\_POST\['year'\] < 2011) {**

**48 $okay**

**\=**

**FALSE;**

**49**

**} // End of 2nd conditional.**

**$age = 2011 - $\_POST\['year'\];**

50

**} else {**

**51 } else { // Else for 1st conditional.**

**print '<p class="error">Either**

52

 ➝ **you entered your birth year**

**53**

**print '<p class="error">Please**

 ➝ **wrong or you come from the**

**enter the year you were born as**

**four**

**digits.</p>';**

 ➝ **future!</p>';**

**54**

**$okay = FALSE;**

**$okay = FALSE;**

55

**} // End of 2nd conditional.**

**56 } // End of 1st conditional.**

57

This **if**\-**else** conditional acts as the

58 // Validate the terms:

statements part of the main conditional,

**59 if (!isset($\_POST\['terms'\])) {**

and is thus executed only if that

**60**

**print '<p class="error">You must**

condition is TRUE. This **if-else** checks

**accept the terms.</p>';**

whether the year variable is less than

**61**

**$okay = FALSE;**

**62 }**

2011 (i.e., the user must have been born

63

before the current year). If that condition

64 // If there were no errors, print a

is TRUE, the user’s age is calculated as

success

message:

before. Otherwise, an error message is

65 if ($okay) {

printed and the **$okay** variable is set to

66

print '<p>You have been successfully

registered (but not really).</p>';

FALSE (indicating a problem occurred).

67

print "<p>You will turn $age this

Note that this conditional is just the

year.</p>";

opposite of the previous version:

68 }

69 ?>

verifying that a value is less than some

70 </body>

number instead of greater than or equal

71 </html>

to that number.

continues on next page

Control Structures 135

![Image 166](index-157_1.png)

![Image 167](index-157_2.png)

**5.** Complete the main year conditional:

**} else { // Else for 1st**

➝ **conditional.**

**print '<p class="error">Please**

 ➝ **enter the year you were born**

 ➝ **as four digits.</p>';**

**$okay = FALSE;**

**} // End of 1st conditional.**

This **else** section completes the

conditional begun in Step 3. If at least

one of the conditions set forth there

is FALSE, this message is printed and

**$okay** is set to FALSE.

**C** The PHP script now catches if the year isn’t

**6.** Confirm that the terms checkbox wasn’t

a four-digit number, as will be the case with this

ignored:

form submission.

**if (!isset($\_POST\['terms'\])) {**

**print '<p class="error">You must**

 ➝ **accept the terms.</p>';**

**$okay = FALSE;**

**}**

If the **$\_POST\['terms'\]** variable is not

set, then the user failed to check that

**D** Error messages are printed if fields are incorrectly

box and an error should be reported. To

filled out or if the terms checkbox is not checked.

be more exact, this conditional could be

**if ( !isset($\_POST\['terms'\]) AND**

➝ **($\_POST\['terms'\] == 'Yes') ) {**

**7.** Those are the only changes to the

script, so you can now save it again,

place it in the same directory as

**register.html** (on your PHP-enabled

server), and test it in your Web browser

again **C** and **D**.

136 Chapter

6

![Image 168](index-158_1.png)

**8.** If desired, change your **year** value to be in

the future and submit the form again **E**.

**It’s another common programming**

**convention—which is maintained in this**

**book—to write the terms TRUE and FALSE in**

**all capitals. This isn’t a requirement of PHP,**

**though. For example, the following conditional**

**is TRUE:**

**if (true) {...**

**It’s very easy in long, complicated condi-**

**tionals to forget an opening or closing paren-**

**thesis or curly bracket, which will produce**

**either error messages or unexpected results.**

**Find a system (like spacing out your condition-**

**als and using comments) to help clarify your**

**code. Another good technique is to create the**

**entire conditional’s structure first, and then go**

**back to add the details.**

**If you have problems getting your**

**if-else statements to execute, print out**

**the values of your variables to help debug**

**the problem. A conditional may not be TRUE**

**or FALSE because a variable doesn’t have**

**the value you think it does.**

**E** The year validation still checks that the date is before 2011.

Control Structures 137

![Image 169](index-159_1.png)

![Image 170](index-159_2.png)

![Image 171](index-159_3.png)

![Image 172](index-159_4.png)

![Image 173](index-159_5.png)

![Image 174](index-159_6.png)

![Image 175](index-159_7.png)

![Image 176](index-159_8.png)

![Image 177](index-159_9.png)

![Image 178](index-159_10.png)

[**Using elseif**](#index_split_000.html#p7)

Similar to the **if**\-**else** conditional is

**if**\-**elseif** (or **if**\-**elseif**\-**else**). This conditional acts like a running **if**

statement and can be expanded to

whatever complexity you require:

**if ( *condition1*) {**

***statement(s)*****;**

**} elseif ( *condition2*) {**

***other\_statement(s)*****;**

**}**

Here’s another example **A**:

**if ( *condition1*) {**

***statement(s)*****;**

**} elseif ( *condition2*) {**

***other\_statement(s)*****;**

**} else {**

***other\_other\_statement(s)*****;**

**}**

If present, you must always make the **else**

the last part of a conditional because it’s

executed unless one of the conditions

to that point has been met (again, **else**

represents the default behavior). You

can, however, continue to use **elseif**s as

**A** How an **IF-ELSEIF-ELSE** conditional affects the

many times as you want as part of one **if**

program flow of a script.

conditional. You may also forego an **else**

clause, if you don’t need a default response.

As an example of this, let’s create a

conditional that prints a message based

on the selected color value.

138 Chapter

6

**Script 6.7** This multiline **if-elseif-else** conditional **To use elseif:**

validates that a submitted color has an allowed

value and is used to determine what type of color

**1.** Open **handle\_reg.php** (Script 6.6)

the selection is.

in your text editor or IDE, if it is not

already open.

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

1.0

Transitional//EN"

**2.** Before the **$okay** conditional, begin

2 "http://www.w3.org/TR/xhtml1/DTD/

a new conditional (**Script 6.7**):

xhtml1-transitional.dtd">

3 <html

xmlns="http://www.w3.org/1999/

**if ($\_POST\['color'\] == 'red') {**

xhtml" xml:lang="en" lang="en">

**$color\_type = 'primary';**

4 <head>

5

<meta http-equiv="Content-Type"

The color value comes from a select

content="text/html;

charset=utf-8"/>

menu with four possible options: red,

6 <title>Registration</title>

yellow, green, and blue. This conditional

7

<style type="text/css" media="screen"> will determine whether the user has

8

.error { color: red; }

selected a primary—red, yellow, or

9 </style>

10 </head>

blue—or secondary (all others) color. The

11 <body>

first condition checks if the value of **$\_**

12 <h1>Registration

Results</h1>

**POST\['color'\]** is equal to the string red.

13 <?php // Script 6.7 - handle\_reg.php #6

14 /\* This script receives seven values

Be certain to use the equality operator—

from

register.html:

two equals signs—and not the assignment

15 email, password, confirm, year, terms,

operator—one—in the conditional.

color, submit \*/

16

**3.** Add an **elseif** clause for the

17 // Address error management, if you want.

second color:

18

**} elseif ($\_POST\['color'\] ==**

19 // Flag variable to track success:

20 $okay = TRUE;

➝ **'yellow') {**

21

**$color\_type = 'primary';**

22 // Validate the email address:

The **elseif** continues the main

23 if (empty($\_POST\['email'\])) {

24

print '<p class="error">Please enter

conditional begun in Step 2. The condition

your email address.</p>';

itself is a replication of the condition in

25

$okay = FALSE;

Step 2, using a new color comparison.

26 }

continues on next page

27

28 // Validate the password:

29 if (empty($\_POST\['password'\])) {

30

print '<p class="error">Please enter

your

password.</p>';

31

$okay = FALSE;

32 }

33

34 // Check the two passwords for equality:

35 if ($\_POST\['password'\] !=

$\_POST\['confirm'\])

{

36

print '<p class="error">Your confirmed

password does not match the original

password.</p>';

code continues on next page

Control Structures 139

**4.** Add **elseif** clauses for the other **Script 6.7** continued

two colors:

37

$okay = FALSE;

**} elseif ($\_POST\['color'\] ==**

38 }

➝ **'green') {**

39

40 // Validate the year:

**$color\_type = 'secondary';**

41 if ( is\_numeric($\_POST\['year'\]) AND

**} elseif ($\_POST\['color'\] ==**

(strlen($\_POST\['year'\]) == 4) ) {

➝ **'blue') {**

42

**$color\_type = 'primary';**

43

// Check that they were born before

2011.

Once you understand the main concept,

44

if ($\_POST\['year'\] < 2011) {

it’s just a matter of repeating the

45

$age = 2011 - $\_POST\['year'\];

**elseif**s for every possible color value.

// Calculate age this year.

46

} else {

**5.** Add an **else** clause:

47

print '<p class="error">Either you

**} else {**

entered your birth year wrong or

you come from the future!</p>';

**print '<p class="error">Please**

48 $okay

\=

FALSE;

 ➝ **select your favorite**

49

} // End of 2nd conditional.

 ➝ **color.</p>';**

50

**$okay = FALSE;**

51 } else { // Else for 1st conditional.

**}**

52

53

print '<p class="error">Please enter

If the user didn’t select a color, or if

the year you were born as four

they manipulated the form to submit

digits.</p>';

54

$okay = FALSE;

a different color value (other than red,

55

yellow, green, or blue), none of the

56 } // End of 1st conditional.

conditions will be TRUE, meaning this

57

**else** clause will take effect. That clause

58 // Validate the terms:

prints an error and assigns a value of

59 if ( !isset($\_POST\['terms'\]) AND

($\_POST\['terms'\] == 'Yes') ) {

FALSE to **$okay**, indicating a problem.

60

print '<p class="error">You must

It doesn’t matter in what order the colors

accept the terms.</p>';

are checked, so long as the **else** clause

61

$okay = FALSE;

62 }

comes last.

63

64 // Validate the color:

**65 if ($\_POST\['color'\] == 'red') {**

**66**

**$color\_type = 'primary';**

**67 } elseif ($\_POST\['color'\] == 'yellow') {**

**68**

**$color\_type = 'primary';**

**69 } elseif ($\_POST\['color'\] == 'green') {**

**70**

**$color\_type = 'secondary';**

**71 } elseif ($\_POST\['color'\] == 'blue') {**

**72**

**$color\_type = 'primary';**

**73 } else { // Problem!**

**74**

**print '<p class="error">Please**

**select your favorite color.</p>';**

**75**

**$okay = FALSE;**

**76 }**

code continues on next page

140 Chapter

6

![Image 179](index-162_1.png)

![Image 180](index-162_2.png)

**Script 6.7** continued

**6.** Within the **$okay** conditional, print the

user’s favorite color type:

77

78 // If there were no errors, print a

**print "<p>Your favorite color is**

success

message:

➝ **a $color\_type color.</p>";**

79 if ($okay) {

80

print '<p>You have been successfully

**7.** Save the script, place it in the same

registered (but not really).</p>';

directory as **register.html** (on your

81

print "<p>You will turn $age this

PHP-enabled server), and test it in your

year.</p>";

Web browser again, using different

**82**

**print "<p>Your favorite color is a**

color options

**$color\_type**

**color.</p>";**

**B** and **C**.

83 }

84 ?>

**One thing most beginner developers**

85 </body>

**don’t realize is that it’s possible—in fact, quite**

86 </html>

**easy—for a hacker to submit data to your PHP**

**script without using your intended HTML form.**

**For this reason, it’s important that you validate**

**the existence of expected variables (i.e., that**

**they are set), their type, and their values.**

**PHP also allows you to write elseif as**

**two words, if you prefer:**

**if ( *condition1*) {**

***statement(s)*****;**

**} else if ( *condition2*) {**

**B** The script now prints a message acknowledging

***statement(s)2*****;**

the user’s color choice.

**}**

**C** Failure to select a color results in this

error message.

Control Structures 141

[**The Switch Conditional**](#index_split_000.html#p7)

**Script 6.8** Switch conditionals can simplify

complicated **if-elseif** conditionals.

Once you get to the point where you have

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

longer **if**\-**elseif**\-**else** conditionals, you

1.0

Transitional//EN"

may find that you can save programming

2 "http://www.w3.org/TR/xhtml1/DTD/

xhtml1-transitional.dtd">

time and clarify your code by using a

3 <html

xmlns="http://www.w3.org/1999/

**switch** conditional instead. The **switch**

xhtml" xml:lang="en" lang="en">

conditional takes only one possible

4 <head>

condition, normally just a variable:

5

<meta http-equiv="Content-Type"

content="text/html;

charset=utf-8"/>

**switch ($var) {**

6 <title>Registration</title>

**case**

***value1*****:**

7

<style type="text/css" media="screen">

***statement(s)1*****;**

8

.error { color: red; }

**break;**

9 </style>

10 </head>

**case**

***value2*****:**

11 <body>

***statement(s)2*****;**

12 <h1>Registration

Results</h1>

**break;**

13 <?php // Script 6.8 - handle\_reg.php #7

**default:**

14 /\* This script receives seven values

***statement(s)3*****;**

from

register.html:

15 email, password, confirm, year, terms,

**break;**

color, submit \*/

**}**

16

You must understand how a **switch**

17 // Address error management, if you want.

18

conditional works in order to use it

19 // Flag variable to track success:

properly. After the keyword **switch**, a

20 $okay = TRUE;

variable is identified within parentheses.

21

PHP will then look at each case in order,

22 // Validate the email address:

trying to identify a matching value. Note

23 if (empty($\_POST\['email'\])) {

24

print '<p class="error">Please enter

that, as with any other use of strings and

your email address.</p>';

numbers in PHP, numeric values would

25

$okay = FALSE;

not be quoted; string values should be.

26 }

After the **case** ***value*** section, a colon (not 27

a semicolon) prefaces the associated

28 // Validate the password:

29 if (empty($\_POST\['password'\])) {

statements, which are normally indented

30

print '<p class="error">Please enter

beginning on the following line.

your

password.</p>';

31

$okay = FALSE;

Once PHP finds a case that matches

32 }

the value of the conditional variable, it

33

executes the subsequent statements.

34 // Check the two passwords for equality:

Here’s the tricky part: once PHP has found

35 if ($\_POST\['password'\] !=

a matching case, it will continue going

$\_POST\['confirm'\])

{

36

print '<p class="error">Your confirmed

through the **switch** until it either comes

password does not match the original

to the end of the **switch** conditional (the

password.</p>';

closing curly bracket) or hits a **break**

37

$okay = FALSE;

statement, at which point it exits the **switch**

38 }

construct. Thus, it’s imperative that you

code continues on next page

142 Chapter

6

**Script 6.8** continued

close every case —even the **default** case,

for consistency’s sake—with a **break** (the

39

sidebar “Break, Exit, Die, and Continue”

40 // Validate the year:

discusses this keyword in more detail).

41 if ( is\_numeric($\_POST\['year'\]) AND

(strlen($\_POST\['year'\]) == 4) ) {

This previous **switch** conditional is like

42

a rewrite of:

43

// Check that they were born before

2011.

**if ($var == *value1*) {**

44

if ($\_POST\['year'\] < 2011) {

***statement(s)1*****;**

45

$age = 2011 - $\_POST\['year'\];

**} elseif ($variable == *value2*) {**

// Calculate age this year.

***statement(s)2*****;**

46

} else {

47

print '<p class="error">Either you

**} else {**

entered your birth year wrong or

***statement(s)3*****;**

you come from the future!</p>';

**}**

48 $okay

\=

FALSE;

Because the

49

} // End of 2nd conditional.

**switch** conditional uses

50

the value of **$var** as its condition, it first

51 } else { // Else for 1st conditional.

checks to see if **$var** is equal to value1

52

and, if so, executes statement(s)1. If not,

53

print '<p class="error">Please enter

it checks to see if **$var** is equal to value2

the year you were born as four

and, if so, executes statement(s)2. If

digits.</p>';

54

$okay = FALSE;

neither condition is met, the default action

55

of the **switch** conditional is to execute

56 } // End of 1st conditional.

statement(s)3.

57

58 // Validate the terms:

With this in mind, let’s rewrite the colors

59 if ( !isset($\_POST\['terms'\]) AND

conditional as a **switch**.

($\_POST\['terms'\] == 'Yes') ) {

60

print '<p class="error">You must

**To use a switch conditional:**

accept the terms.</p>';

61

$okay = FALSE;

**1.** Open **handle\_reg.php** (Script 6.7)

62 }

in your text editor or IDE, if it is not

63

already open.

64 // Validate the color:

**65 switch ($\_POST\['color'\]) {**

**2.** Delete the extended colors conditional

**66 case**

**'red':**

(**Script 6.8**).

**67 $color\_type**

**\=**

**'primary';**

**3.** Begin the

**68 break;**

**switch**:

**69 case**

**'yellow':**

**switch ($\_POST\['color'\]) {**

**70 $color\_type**

**\=**

**'primary';**

**71 break;**

As mentioned earlier, a **switch**

**72 case**

**'green':**

conditional takes only one condition:

**73**

**$color\_type = 'secondary';**

a variable’s name. In this example, it’s

**74 break;**

**$\_POST\['color'\]**.

**75 case**

**'blue':**

**76**

**$color\_type = 'primary';**

continues on next page

**77 break;**

**78 default:**

code continues on next page

Control Structures 143

**4.** Create the first case:

**Script 6.8** continued

**case 'red':**

**79**

**print '<p class="error">Please**

**$color\_type = 'primary';**

**select your favorite color.</p>';**

**break;**

**80**

**$okay = FALSE;**

**81 break;**

The first case checks to see if

**82 } // End of switch.**

**$\_POST\['color'\]** has a value of red.

83

If so, then, the same statement is

84 // If there were no errors, print a

success

message:

executed as before. Next you include

85 if ($okay) {

a **break** statement to exit the **switch**.

86

print '<p>You have been successfully

**5.** Add a case for the second color:

registered (but not really).</p>';

87

print "<p>You will turn $age this

**case 'yellow':**

year.</p>";

**$color\_type = 'primary';**

88

print "<p>Your favorite color is a

**break;**

$color\_type

color.</p>";

89 }

**6.** Add cases for the remaining colors:

90 ?>

91 </body>

**case 'green':**

92 </html>

**$color\_type = 'secondary';**

**break;**

**case 'blue':**

**$color\_type = 'primary';**

**break;**

**Break, Exit, Die, and Continue**

PHP includes many language constructs—tools that aren’t functions but still do something in your scripts. For example, **print** is a language construct. Another example is **break**, which is demonstrated in the **switch**. **break** exits the current structure, be it a **switch**, an **if**\-**else** conditional, or a loop.

Similar to this is **continue**, which terminates the current iteration of a loop. Any remaining statements within the loop aren’t executed, but the loop’s condition is checked again to see if the loop should be entered.

**exit** and **die** are more potent versions of **break** (and they’re synonymous). Instead of exiting the current structure, these two language constructs terminate the execution of the PHP script.

Therefore, all PHP code after a use of **exit** or **die** is never executed. For that matter, any HTML

after these constructs is never sent to the Web browser. You’ll see **die** used most frequently as a heavy-handed error handling tool. **exit** is often used in conjunction with the **header()** function.

144 Chapter

6

![Image 181](index-166_1.png)

![Image 182](index-166_2.png)

**7.** Add a **default** case and complete

the switch:

**default:**

**print '<p class="error">Please**

 ➝ **select your favorite**

 ➝ **color.</p>';**

**$okay = FALSE;**

**break;**

**A** The handling script still works the same,

whether the user selects a color…

**} // End of switch.**

This **default** case is the equivalent

of the **else** clause used in the original

conditional.

**8.** Save your script, place it in the same

directory as **register.html** (on your

**B** …or fails to.

PHP-enabled server), and test it in your

Web browser again **A** and **B**.

**A default case isn’t required in your**

**switch conditional (you could set it up so**

**that if the value isn’t explicitly met by one of**

**the cases, nothing happens), but if it’s used,**

**it should be the last case.**

**If you’re using a string in your switch**

**conditional as the case value, keep in mind**

**that it’s case sensitive, meaning that Value**

**won’t match value.**

Control Structures 145

![Image 183](index-167_1.png)

![Image 184](index-167_2.png)

![Image 185](index-167_3.png)

![Image 186](index-167_4.png)

![Image 187](index-167_5.png)

![Image 188](index-167_6.jpg)

![Image 189](index-167_7.png)

![Image 190](index-167_8.png)

[**The for Loop**](#index_split_000.html#p7)

Loops are the final type of control structure

discussed in this chapter. As suggested

earlier, loops are used to execute a section

of code repeatedly. You may want to print

something a certain number of times, or

you may want to do something with each

value in an array (i.e., a list of values). For

either of these cases, and many more,

you can use a loop. (The latter example is

demonstrated in the next chapter.)

PHP supports three kinds of loops: **for**,

**while**, and **foreach**. The **while** loop is similar to **for**, but it’s used most frequently when

retrieving values from a database or reading

from a text file (it’s introduced in the sidebar).

The **foreach** loop is related to using arrays

and is introduced in the next chapter.

The **for** loop is designed to perform

specific statements for a determined

number of iterations (unlike **while**, which

**A** This flowchart represents how a **for** loop is

runs until a condition is FALSE—similar,

executed in PHP.

but significantly different, concepts). You

normally use a dummy variable in the loop

for this purpose:

**for ( *initial expression*; *condition*;**

➝ ***closing expression*****) {**

***statement(s)*****;**

**}**

The initial expression is executed once:

the first time the loop is called. Then the

condition is used to determine whether

to execute the statements. The closing

expression is executed each time the

condition is found to be TRUE, but only

after the statements are executed **A**.

Here’s a simple loop that prints out the

numbers 1 through 10:

**for ($i = 1; $i <= 10; $i++) {**

**print**

**$i;**

**}**

146 Chapter

6

**Script 6.9** This script uses a PHP **for** loop to To practice with the **for** loop, let’s expand

dynamically generate the day of the month

the registration form so that it asks the user

drop-down menu.

for their complete birthday. A **for** loop can

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

be used to easily create a day drop-down

1.0

Transitional//EN"

menu in the HTML form.

2 "http://www.w3.org/TR/xhtml1/DTD/

xhtml1-transitional.dtd">

3 <html

xmlns="http://www.w3.org/1999/

**To write a for loop:**

xhtml" xml:lang="en" lang="en">

**1.** Open **register.html** (Script 6.1) in your

4 <head>

text editor or IDE, if it is not already open.

5

<meta http-equiv="Content-Type"

content="text/html;

charset=utf-8"/>

**2.** Remove the existing birth year prompt

6 <title>Registration

Form</title>

and input (**Script 6.9**).

7 </head>

8 <body>

You’ll replace this one prompt with three

9

<!-- Script 6.9 - register.php -->

separate elements to represent the

10 <div><p>Please complete this form to

entire birthday: month, day, and year.

register:</p>

11

**3.** Where the birth year prompt was, after

12 <form action="handle\_reg.php"

the password confirmation and before

method="post">

the color option, add a prompt and a list

13

of months:

14

<p>Email Address: <input type="text"

name="email" size="30" /></p>

**<p>Date Of Birth:**

15

**<select name="month">**

16

<p>Password: <input type="password"

**<option value="">Month</option>**

name="password" size="20" /></p>

17

**<option value="1">January</option>**

18

<p>Confirm Password: <input

**<option value="2">February</option>**

type="password" name="confirm"

**<option value="3">March</option>**

size="20"

/></p>

**<option value="4">April</option>**

19

**<option value="5">May</option>**

**20**

**<p>Date Of Birth:**

**21 <select**

**name="month">**

**<option value="6">June</option>**

**22 <option**

**value="">Month</option>**

**<option value="7">July</option>**

**23 <option**

**value="1">January</option>**

**<option value="8">August</option>**

**24 <option**

**value="2">February</option>**

**<option value="9">September</option>**

**25 <option**

**value="3">March</option>**

**<option value="10">October</option>**

**26 <option**

**value="4">April</option>**

**27 <option**

**value="5">May</option>**

**<option value="11">November</option>**

**28 <option**

**value="6">June</option>**

**<option value="12">December</option>**

**29 <option**

**value="7">July</option>**

**</select>**

**30 <option**

**value="8">August</option>**

**31 <option**

**value="9">September</option>**

First is a textual prompt, telling the user

**32 <option**

**value="10">October</option>**

to supply their entire date of birth. Next

**33 <option**

**value="11">November</option>**

comes a select menu in which the user

**34 <option**

**value="12">December</option>**

can pick their birth month. The value for

**35 </select>**

each option is numeric; the viewed text

**36 <select**

**name="day">**

**37 <option**

**value="">Day</option>**

is a string (the month’s name).

**38**

**<?php // Print out 31 days:**

continues on next page

code continues on next page

Control Structures 147

![Image 191](index-169_1.png)

**4.** Begin a select menu for the birth day:

**Script 6.9** continued

**<select name="day">**

**39**

**for ($i = 1; $i <= 31; $i++) {**

**<option value="">Day</option>**

**40**

**print "<option value=\\"$i\\">$i**

**</option>\\n";**

This code starts the **select** form

**41 }**

element for the user’s birth day of the

**42 ?>**

month. The list of possible values will

**43 </select>**

be generated using PHP.

**44**

**<input type="text" name="year"**

**value="YYYY" size="4" /></p>**

**5.** Create a new PHP section:

45

46 <p>Favorite

Color:

**<?php**

47 <select

name="color">

Because PHP can be embedded within

48

<option value="">Pick One</option>

HTML, you’ll use it to populate the drop-

49 <option

value="red">Red</option>

50 <option

value="yellow">Yellow</option>

down menu. Begin with the standard

51 <option

value="green">Green</option>

PHP tag.

52 <option

value="blue">Blue</option>

**6.** Create a **for** loop to print out 31 days as

53 </select></p>

54

select menu options:

55

<p><input type="checkbox"

**for ($i = 1; $i <= 31; $i++) {**

name="terms" value="Yes" /> I agree to

**print "<option value=\\"$i\\">$i**

the terms (whatever they may be).</p>

56

 ➝ **</option>\\n";**

57

<input type="submit" name="submit"

**}**

value="Register"

/>

The loop begins by creating a dummy

58

59 </form>

variable called **$i**. On the first use of

60

the loop, this variable is set to 1. Then,

61 </div>

as long as **$i** is less than or equal to 31,

62 </body>

the contents of the loop are executed.

63 </html>

These contents are the **print** line,

which creates code like

**<option value="1">1</option>**

followed by a return (created with **\\n**).

After this statement is executed, the **$i**

variable is incremented by 1. Then the

condition (**$i <= 31**) is checked again,

and the process is repeated.

**7.** Close the PHP section:

**?>**

**8.** Save the file as **register.php**.

You must save the file with the **.php**

extension now, in order for the PHP

**B** The new version of the HTML form, with some

code to be executed.

dynamically generated content.

148 Chapter

6

![Image 192](index-170_1.png)

**9.** Place the file in the proper directory for

your PHP-enabled server and test it in

your Web browser **B**.

As long as this script is in the same

directory as **handle\_reg.php**, you can

even fill out and submit the form as you

would with the plain HTML version.

**10.** If desired, view the HTML source code

**C** If you view the HTML source code for the form,

you’ll see the data generated by the **for** loop.

to see the PHP-generated options **C**.

**It’s conventional to use simple variables**

**The while Loop**

**as the counters within for loops: $i, $j, $k, etc.**

The second of the three types of loops

**Just as you can write the if conditional**

that exist in PHP—the **while** loop—is

**on one line if you have only one statement,**

designed to continue working as long as

**you can do the same with the while and for**

the condition you establish is TRUE. Like

**loops. Again, though, this isn’t recommended.**

the **for** loop, it checks the value of the

condition before each iteration. Once the

**Loops can be nested inside each other.**

condition becomes FALSE, the **while**

**You can also place conditionals within loops,**

loop is exited:

**loops within conditionals, and so forth.**

**while ( *condition*) {**

**Pay close attention to your loop’s condi-**

***statement(s)*****;**

**tion so that the loop ends at some point.**

**}**

**Otherwise, you’ll create an infinite loop, and**

**the script will run and run and run.**

The main difference between **for** and

**while** is that **while** doesn’t include a

system for setting initial conditions or for

executing closing expressions.

You also have the option of using the

**do...while** loop, which guarantees that

the statements are executed at least

once (this isn’t necessarily true of the

**while** loop):

**do {**

***statement(s)*****;**

**} while ( *condition*);**

Although there is a fair amount of overlap

regarding when you can use the two

major loop constructs (**while** and **for**),

you’ll discover as you program that some-

times one is more logical than the other.

The **while** loop is frequently used in the

retrieval of data from a database (see

Chapter 12, “Intro to Databases”).

Control Structures 149

[**Review and Pursue**](#index_split_000.html#p7)

**Pursue**

■

Check out the PHP manual’s pages for

If you have any problems with the review

the various operators.

questions or the pursue prompts, turn

to the book’[s supporting forum (www.](http://www.LarryUllman.com/forum/)

■

Rewrite **handle\_reg.php** so that it uses

[LarryUllman.com/forum/).](http://www.LarryUllman.com/forum/)

a variable for the current year, instead

of hard-coding that value.

**Review**

■

For debugging purposes, add code to

the beginning of the **handle\_reg.php**

■

Why is it important to have a user

script that prints out the values of the

confirm their password during the

received variables. Hint: There’s a short

registration process?

and a long way to do this.

■

What is the basic structure of an

■

**if**

Rewrite one of the versions of **handle\_**

conditional in PHP? An **if-else**

**reg.php** so that it prints the user’s

conditional? An **if-elseif**? An

**if-elseif-else**

favorite color selection in the user’s

?

favorite color. Hint: You’ll want to use

■

What are the differences between the

CSS and concatenation.

**empty()** and **isset()** functions?

■

Update **handle\_reg.php** so that it

■

What is the assignment operator? What

validates the user’s birthday by looking

is the equality operator?

at the three individual form elements:

■

Without knowing anything about **$var**,

month, day, and year. Create a variable

will the following conditional be TRUE

that represents the user’s birthday in

or FALSE? Why?

the format XX/DD/YYYY (again, you’ll

**if ($var = 'donut') {**

use concatenation for this).

■

What do these operators mean?

\> **&&**

\> **||**

\> **!**

■

What is the syntax of a **switch**

conditional? When is a **switch**

most commonly used?

■

What is the syntax of a **for** loop?

150 Chapter

6

[**7**](#index_split_000.html#p7)

[Using Arrays](#index_split_000.html#p7)

The next—and last—variable type you’ll

learn about in this book is the array. Arrays

**In This Chapter**

are significantly different from numbers or

strings, and you can’t make the most of

What Is an Array?

152

programming in PHP without understand-

Creating an Array

154

ing them.

Adding Items to an Array

158

Because of their unique nature, this

Accessing Array Elements

161

chapter will cover arrays more deliberately

and slowly than the other variable types.

Creating Multidimensional Arrays

164

The chapter begins with an introduction

Sorting Arrays

168

to the concept, along with the basics of

Transforming Between Strings

creating and using arrays. Then it covers

and Arrays

172

multidimensional arrays and some of the

array-related functions. The chapter con-

Creating an Array from a Form

176

cludes with array-string conversions and a

Review and Pursue

182

demonstration on how to create an array

from an HTML form.

[**What Is an Array?**](#index_split_000.html#p7)

**TABLE 7.1 Grocery List Array**

Arrays constitute a complicated but very

**Item Number**

**Item**

useful notion. Whereas numbers and

1

apples

strings are scalar variables (meaning they

2

bananas

always have only a single value), an array

3

oranges

is a collection of multiple values assembled

into one overriding variable. An array

can consist of numbers and/or strings

(and/or other arrays), which allows this

one variable to hold exponentially more

information than a simple string or number

can. For example, if you wanted to create a

grocery list using strings, your code would

look something like this:

**$item1 = 'apples';**

**$item2 = 'bananas';**

**$item3 = 'oranges';**

For each added item, you’d need to

create a new string. This approach is

cumbersome, and it makes it difficult to

refer back to the entire list or any specific

value later in your code. You can greatly

simplify matters by placing your entire list

into one array (say, **$items**), which contains

everything you need (**Table 7.1**).

As an array, your list can be added to, sorted,

searched, and so forth. With this context in

mind, let’s look into the syntax of arrays.

152 Chapter

7

**Syntactical rules for arrays**

**Superglobals and You**

The other variable types you’ve dealt

Throughout this book, you’ve already

with—numbers and strings—have a

dealt with some arrays: **$\_SERVER**,

variable name and a corresponding value

**$\_GET**, and **$\_POST**. These are all special

(for example, **$first\_name** could be

arrays called superglobals, along with

equal to ***Larry***). Arrays also have a name,

**$\_COOKIE**, **$\_SESSION**, and **$\_ENV**.

derived using the same conventions:

As you know, the **$\_POST** array receives

■

They begin with a dollar sign.

all the data sent to the page from a form

■

that uses the POST method. Its indexes

They continue with a letter or

are the names of the form elements, and

underscore.

its values are the values of those form

■

They finish with any combination of

elements. Therefore, **$\_POST\['name'\]**

letters, numbers, or the underscore.

refers to the value typed in a form input

created by the code

But arrays differ in that they contain

multiple elements (think of each row

**<input type="text" name="name" />**

in Table 7.1 as an element). An element

Similarly, **$\_GET** refers to data sent from a

consists of an index or key (the two words

form using the GET method or from data

can be used interchangeably) and a value.

otherwise passed in the URL. **$\_COOKIE**

In Table 7.1, the Item Number is the key,

refers to data stored in a cookie, and

and the Item is the value.

**$\_SESSION** refers to data stored in a

session (you’ll encounter these two in

An array’s index is used as a reference

Chapter 9, “Cookies and Sessions”).

point to the values. An array can use either

**$\_ENV** is like **$\_SERVER**, containing values

numbers or strings as its keys (or both),

pertaining to the computer on which PHP

depending on how you set it up.

is running.

Generally, when you use an array it looks

the same as any other variable, except that

you include a key in square brackets (**\[\]**)

to reference particular values. Whereas

**$items** refers to the array as a whole,

**$items\[1\]** points to a specific element in

the array (in this example, ***apples***).

Using Arrays 153

[**Creating an Array**](#index_split_000.html#p7)

The formal method of creating an array is

to use the **array()** function. Its syntax is:

**$list = array ('apples', 'bananas',**

➝ **'oranges');**

Arrays automatically begin their indexing

at 0, unless otherwise specified. In that

example—which doesn’t specify an index

for the elements—the first item, ***apples***,

is automatically indexed at 0, the second

item at 1, and the third at 2.

You can assign the index when using

**array()**:

**$list = array (1 => 'apples', 2 =>**

➝ **'bananas', 3 => 'oranges');**

Because PHP is very liberal when it comes

to blank space in your scripts, you can

make this structure easier to read by

writing it over multiple lines:

**$list = array (**

**1 => 'apples',**

**2 => 'bananas',**

**3 => 'oranges'**

**);**

Finally, the index value you specify doesn’t

have to be a number—you can use strings

as well. This indexing technique is practical

for making more meaningful lists. As an

example, you could create an array that

records the soup of the day for each day

of the week, as in the following script. This

example will also demonstrate how you

can, and cannot, print out an array (which

has already been demonstrated but is

worth rehashing).

154 Chapter

7

**Script 7.1** The **$soups** array contains three **To create an array:**

elements and uses strings for its keys.

**1.** Begin a new document in your text

1

<!DOCTYPE html PUBLIC "-//W3C//DTD

editor or IDE, to be named **soups1.php**

XHTML 1.0 Transitional//EN"

(**Script 7.1**):

2 "http://www.w3.org/TR/xhtml1/DTD/

xhtml1-transitional.dtd">

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

3 <html

xmlns="http://www.w3.org/1999/

➝ **XHTML 1.0 Transitional//EN"**

xhtml" xml:lang="en" lang="en">

**"http://www.w3.org/TR/xhtml1/**

4 <head>

 ➝ **DTD/xhtml1-transitional.dtd">**

5

<meta http-equiv="Content-Type"

content="text/html;

**<html xmlns="http://www.w3.org/**

charset=utf-8"/>

➝ **1999/xhtml" xml:lang="en"**

6

<title>No Soup for You!</title>

➝ **lang="en">**

7 </head>

**<head>**

8 <body>

**<meta**

**http-equiv="Content-Type"**

9 <h1>Mmm...soups</h1>

10 <?php // Script 7.1 - soups1.php

 ➝ **content="text/html;**

11 /\* This script creates and prints out

 ➝ **charset=utf-8"/>**

an array. \*/

**<title>No Soup for You!</title>**

12 // Address error management, if you

**</head>**

want.

**<body>**

13

14 // Create the array:

**<h1>Mmm...soups</h1>**

**15 $soups = array (**

**2.** Begin the PHP section of the script and

**16 'Monday' => 'Clam Chowder',**

address error handling, if necessary:

**17 'Tuesday' => 'White Chicken Chili',**

**18 'Wednesday' => 'Vegetarian'**

**<?php // Script 7.1 - soups1.php**

**19 );**

20

If you don’t have **display\_errors**

21 // Try to print the array:

enabled, or if **error\_reporting** is

**22 print**

**"<p>$soups</p>";**

set to the wrong level, see Chapter 3,

23

“HTML Forms and PHP,” for the lines to

24 // Print the contents of the array:

include here to alter those settings.

**25 print\_r**

**($soups);**

26

**3.** Use the **array()** function to create

27 ?>

an array:

28 </body>

29 </html>

**$soups = array (**

**'Monday' => 'Clam Chowder',**

**'Tuesday' => 'White Chicken Chili',**

**'Wednesday' => 'Vegetarian'**

**);**

continues on next page

Using Arrays 155

![Image 193](index-177_1.png)

This is the proper format for initializing

In Chapter 2, “Variables,” you learned

(creating and assigning a value to)

how to use **print\_r()** to show the

an array in PHP, using strings as the

contents and structure of any variable.

indices. Because both the keys and

Use it here so that you can see the

values are strings, you surround them

difference between the way this

with quotation marks. As with all strings,

function and **print** work with arrays.

you can use either single or double

**6.** Close the PHP and the HTML sections:

quotation marks, so long as you’re

**?>**

mindful of other quotation marks that

**</body>**

might be found within the string.

**</html>**

**4.** Attempt to print the array:

**7.** Save your document as **soups1.php**,

**print "<p>$soups</p>";**

place it in the proper directory for your

As you’ve already seen, arrays are also

PHP-enabled server, and test it in your

different in that they can’t be printed the

Web browser **A**.

way you’d print other (scalar) variables.

Remember to run the PHP script

**5.** Use the **print\_r()** function to print out

through a URL.

the array differently:

**print\_r ($soups);**

**A** Because an array is structured differently than other variable types, a request to print an array results in the word Array. On the other hand, the **print\_r()** function prints the array’s contents and structure.

156 Chapter

7

![Image 194](index-178_1.png)

**The practice of beginning any index at 0 is**

**The range() function can also be used**

**standard in PHP and most other programming**

**to create an array of items based on a range of**

**languages. As unnatural as this counting system**

**values. Here are two examples:**

**may seem, it’s here to stay, so you have two**

**possible coping techniques. First, manually start**

**$ten = range (1, 10);**

**all your arrays indexed at position 1. Second,**

**$alphabet = range ('a', 'z');**

**unlearn a lifetime of counting from 1. You can**

**decide which is easier, but most programmers**

**As of PHP version 5, the range() func-**

**just get used to this odd construct.**

**tion includes a *step*** **parameter that lets you**

**specify increments:**

**You must refer to an array’s elements**

**via the same index used to create the array. In**

**$evens = range (0, 100, 2);**

**the $soups example, $soups\[0\] has no value**

**even though the array obviously has a first ele-**

**If you use the var\_dump() function**

**ment (the first element normally being indexed**

**in your script in lieu of print\_r(), it shows**

**at 0 numerically).**

**not only the contents of the array but also its**

**structure in a more detailed format B.**

**If you use the array() function to define**

**an index, you can associate the first index, and**

**An array whose keys are numbers is**

**the others will follow sequentially. For example:**

**called an indexed array. If the keys are strings,**

**it’s referred to as an associative array. Other**

**$list = array (1 => 'apples',**

**languages refer to associative arrays as hashes.**

**'bananas', 'oranges');**

**Now *bananas*** **is indexed at 2 and oranges at 3.**

**B** The **var\_dump()** function (used with Script 7.1 instead of the **print\_r()** function) shows how many elements are in an array and how long each string value is.

Using Arrays 157

[**Adding Items**](#index_split_000.html#p7)

**Deleting Arrays and**

[**to an Array**](#index_split_000.html#p7)

**Array Elements**

In PHP, once an array exists, you can

You won’t frequently need to delete

an individual item from an array, but

add extra elements to the array with the

it’s possible to do using the **unset()**

assignment operator (the equals sign), in a

function. This function eliminates a

way similar to how you assign a value to a

variable and frees up the memory it

string or a number. When doing so, you can

used. When applied to an array element,

specify the key of the added element or not

that element is deleted:

specify it, but in either case, you must refer to

the array with the square brackets. To add two

**unset($array\[4\]);**

items to the existing **$list** array, you’d write

**unset($array\[' *name*'\]);**

**$list\[\] = 'pears';**

If you apply **unset()** to an entire array

**$list\[\] = 'tomatoes';**

or any other variable type, the whole

variable is deleted:

If you don’t specify the key, each element is

**unset($array);**

appended to the existing array, indexed with

**unset($string);**

the next sequential number. Assuming this is

the same array from the preceding section,

You can also reset an array (empty it

which was indexed at 1, 2, and 3, ***pears*** is

without deleting the variable altogether)

now located at 4 and ***tomatoes*** at 5.

using the **array()** function:

If you do specify the index, the value is assigned

**$array = array();**

at that location. Any existing value already

This has the effect of initializing the

indexed at that point is overwritten, like so:

variable: making it exist and defining

**$list\[3\] = 'pears';**

its type without assigning a value.

**$list\[4\] = 'tomatoes';**

Now, the value of the element in the fourth

position of the array is ***tomatoes***, and no

element of **$list** is equal to ***oranges*** (that value was overwritten by ***pears***). With this

in mind, unless you intend to overwrite any

existing data, you’ll be better off not naming

a specific key when adding values to your

arrays. However, if the array uses strings for

indices, you’ll probably want to specify keys

so that you don’t end up with an unusual

combination of string and numeric keys.

To test this process, in the following task

you’ll rewrite **soups1.php** to add more

elements to the array. To see the difference

adding more elements makes, you’ll print

out the number of elements in the array

before and after the new additions. Just

as you can find the length of a string—how

158 Chapter

7

**Script 7.2** You can directly add elements to an many characters it contains—by using

array one at a time by assigning each element a

**strlen()**, you can determine the number

value with the assignment operator. The **count()**

of elements in an array by using **count()**:

function will help you keep track of how many

elements the array contains.

**$how\_many = count($array);**

1

<!DOCTYPE html PUBLIC "-//W3C//DTD

XHTML 1.0 Transitional//EN"

**To add elements to an array:**

2 "http://www.w3.org/TR/xhtml1/DTD/

**1.** Open **soups1.php** in your text editor or

xhtml1-transitional.dtd">

3 <html

xmlns="http://www.w3.org/1999/

IDE, if it is not already.

xhtml" xml:lang="en" lang="en">

**2.** After the array is initialized using

4 <head>

**array()**, add the following (**Script 7.2**,

5

<meta http-equiv="Content-Type"

content="text/html;

charset=utf-8"/>

to be named **soups2.php**):

6

<title>No Soup for You!</title>

**$count1 = count ($soups);**

7 </head>

**print "<p>The soups array originally**

8 <body>

9 <h1>Mmm...soups</h1>

➝ **had $count1 elements.</p>";**

10 <?php // Script 7.2 - soups2.php

The **count()** function determines

11 /\* This script creates and prints out

how many elements are in **$soups**. By

an array. \*/

assigning that value to a variable, you

12 // Address error management, if you want.

13

can easily print out the number.

14 // Create the array:

**3.** Add three more elements to the array:

15 $soups = array (

16 'Monday' => 'Clam Chowder',

**$soups\['Thursday'\] = 'Chicken Noodle';**

17 'Tuesday' => 'White Chicken Chili',

**$soups\['Friday'\] = 'Tomato';**

18 'Wednesday' => 'Vegetarian'

**$soups\['Saturday'\] = 'Cream of**

19 );

➝ **Broccoli';**

20

21 // Count and print the current number

This code adds three more soups—

of

elements:

indexed at ***Thursday***, ***Friday***, and

**22 $count1 = count ($soups);**

***Saturday***—to the existing array.

**23 print "<p>The soups array originally**

**had $count1 elements.</p>";**

**4.** Recount how many elements are in the

24

array, and print this value:

25 // Add three items to the array:

**26 $soups\['Thursday'\] = 'Chicken**

**$count2 = count ($soups);**

**Noodle';**

**print "<p>After adding 3 more**

**27 $soups\['Friday'\] = 'Tomato';**

➝ **soups, the array now has**

**28 $soups\['Saturday'\] = 'Cream of Broccoli';**

29

➝ **$count2 elements.</p>";**

30 // Count and print the number of

This second **print** call is a repetition of

elements

again:

the first, showing how many elements

**31 $count2 = count ($soups);**

the array now contains.

**32 print "<p>After adding 3 more soups,**

**the array now has $count2 elements.</p>";**

**5.** Delete this line:

33

34 // Print the contents of the array:

**print "<p>$soups</p>";**

35 print\_r

($soups);

This line isn’t needed anymore, so you

36

37 ?>

can get rid of it (you now know that you

38 </body>

can’t print an array that easily).

39 </html>

continues on next page

Using Arrays 159

![Image 195](index-181_1.png)

**6.** Save your script as **soups2.php**,

**Be very careful when you directly add ele-**

place it in the proper directory for

**ments to an array. There’s a correct way to do it—**

your PHP-enabled server, and test

**$array\[\] = 'Add This';**

it in your Web browser **A**.

**or**

**$array\[1\] = 'Add This';**

**Merging Arrays**

**—and an incorrect way:**

PHP has a function that allows you

**$array = 'Add This';**

to append one array onto another.

Think of it as concatenation for arrays.

**If you forget to use the brackets, the new**

The function, **array\_merge()**, works

**value will replace the entire existing array,**

**leaving you with a simple string or number.**

like so:

**$new\_array = array\_merge**

**The code**

➝ **($array1, $array2);**

**$array\[\] = 'Value';**

You could also write the **soups2.php**

page using this function:

**creates the $array variable if it doesn’t yet exist.**

**$soups2 = array (**

**While working with these arrays, I’m**

**'Thursday' => 'Chicken Noodle',**

**using single quotation marks to enclose both**

**'Friday' => 'Tomato',**

**the keys and the values. Nothing needs to**

**'Saturday' => 'Cream of**

**be interpolated (like a variable), so double**

**quotation marks aren’t required. It’s perfectly**

➝ **Broccoli'**

**acceptable to use double quotation marks,**

**);**

**though, if you want to.**

**$soups = array\_merge($soups,**

➝ **$soups2);**

**You don’t (and, in fact, shouldn’t) quote**

**your keys if they’re numbers, variables, or con-**

You could even accomplish this result

**stants (you’ll learn about constants in Chapter 8,**

with the plus sign (thus adding two

**“Creating Web Applications”). For example:**

arrays together):

**$day = 'Sunday';**

**$soups = $soups + $soups2;**

**$soups\[$day\] = 'Mushroom';**

or

**The sizeof() function is an alias to**

**$soups += $soups2;**

**count(). It also returns the number of ele-**

**ments in an array.**

**A** A direct way to ensure

that the new elements were

successfully added to the

array is to count the number

of elements before and after

you make the additions.

160 Chapter

7

![Image 196](index-182_1.png)

![Image 197](index-182_2.png)

![Image 198](index-182_3.png)

[**Accessing Array**](#index_split_000.html#p7) 

the other variable types don’t have: You

must know the keys of the array in order

[**Elements**](#index_split_000.html#p7)

to access its elements. If the array was set

using strings, like the **$soups** array, then

Regardless of how you establish an array,

referring to **$soups\[1\]** points to nothing **C**.

there’s only one way to retrieve a specific

For that matter, because indexes are

element (or value) from it, and that is to

case-sensitive, **$soups\['monday'\]** is

refer to its index:

meaningless because ***Clam Chowder***

**print "The first item is $array\[0\]";**

was indexed at **$soups\['Monday'\]**.

If the array uses strings for indexes, which

The fastest and easiest way to access all

should be quoted, you must adjust for the

the values of an array is to use a **foreach**

quotation marks you’d use around the

loop. This construct loops through every

index, because they conflict with the **print**

element of an array:

syntax. This line will cause problems **A**:

**foreach ($array as $key => $value) {**

**print "<p>Monday's soup is**

**print "<p>Key is $key. Value**

➝ **$soups\['Monday'\].</p>";**

➝ **is $value</p>";**

**}**

To combat this issue, you can wrap the whole

array construct within curly brackets **B**:

With each iteration of the loop, the current

array element’s key will be assigned to

**print "<p>Monday's soup is**

the **$key** variable and the value to **$value**.

➝ **{$soups\['Monday'\]}.</p>";**

Note that you can use any variable here:

Ironically, the feature that makes arrays so

**$k** and **$v** are likely choices, too.

useful—being able to store multiple values

You can now write a new soups script to

in one variable—also gives it a limitation

use this knowledge.

**A** Referencing a specific element in an associative array will cause parse errors within double quotation marks.

**B** Wrapping an array element

reference in curly brackets is one

way to avoid parse errors.

**C** Referring to an array index that does not exist will create an Undefined offset or Undefined Index notice.

Using Arrays 161

**To print the values of any array:**

**Script 7.3** A **foreach** loop is the easiest way to

access every element in an array.

**1.** Begin a new document in your text

editor or IDE (**Script 7.3, to be named**

1

<!DOCTYPE html PUBLIC "-//W3C//DTD

XHTML 1.0 Transitional//EN"

**soups3.php**):

2 "http://www.w3.org/TR/xhtml1/DTD/

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

xhtml1-transitional.dtd">

➝ **XHTML 1.0 Transitional//EN"**

3 <html

xmlns="http://www.w3.org/1999/

xhtml" xml:lang="en" lang="en">

**"http://www.w3.org/TR/xhtml1/**

4 <head>

 ➝ **DTD/xhtml1-transitional.dtd">**

5

<meta http-equiv="Content-Type"

**<html xmlns="http://www.w3.org/**

content="text/html;

➝ **1999/xhtml" xml:lang="en" lang="en">** charset=utf-8"/>

**<head>**

6

<title>No Soup for You!</title>

7 </head>

**<meta**

**http-equiv="Content-Type"**

8 <body>

 ➝ **content="text/html;**

9 <h1>Mmm...soups</h1>

 ➝ **charset=utf-8"/>**

10 <?php // Script 7.3 - soups3.php

**<title>No Soup for You!</title>**

11 /\* This script creates and prints out

**</head>**

an array. \*/

12

**<body>**

13 // Address error management, if you

**<h1>Mmm...soups</h1>**

want.

**2.** Start the PHP section of the page and

14

15 // Create the array:

address error management, if you need:

16 $soups = array (

**<?php // Script 7.3 - soups3.php**

17 'Monday' => 'Clam Chowder',

18 'Tuesday' => 'White Chicken Chili',

**3.** Create the **$soups** array:

19 'Wednesday' => 'Vegetarian',

**$soups = array (**

20 'Thursday' => 'Chicken Noodle',

21 'Friday' => 'Tomato',

**'Monday' => 'Clam Chowder',**

22 'Saturday' => 'Cream of Broccoli'

**'Tuesday' => 'White Chicken Chili',**

23 );

**'Wednesday' => 'Vegetarian',**

24

**'Thursday' => 'Chicken Noodle',**

25 // Print each key and value:

**'Friday' => 'Tomato',**

**26 foreach ($soups as $day => $soup) {**

**'Saturday' => 'Cream of Broccoli'**

**27**

**print "<p>$day: $soup</p>\\n";**

**28 }**

**);**

29

Here the entire array is created at

30 ?>

31 </body>

once, although you could use the same

32 </html>

method (creating the array in steps) as

in the preceding script, if you’d rather.

162 Chapter

7

![Image 199](index-184_1.png)

**4.** Create a **foreach** loop to print out each

**One option for working with arrays is to**

day’s soup:

**assign a specific element’s value to a separate**

**variable using the assignment operator:**

**foreach ($soups as $day => $soup)**

**{**

**$total = $array\[1\];**

**print "<p>$day: $soup</p>\\n";**

**By doing this, you can preserve the original**

**}**

**value in the array and still manipulate the**

The **foreach** loop iterates through

**value separately as a variable.**

every element of the **$soups** array,

**If you only need to access an array’s**

assigning each index to **$day** and each

**values (and not its keys), you can use this**

value to **$soup**. These values are then

**foreach structure:**

printed out within HTML paragraph

**foreach ($array as $value) {**

tags. The **print** statement concludes

**// Do whatever.**

with a newline character (created by

**}**

**\\n**), which will make the HTML source

code of the page more legible.

**Another way to access all of an array’s**

**elements is to use a for loop:**

**5.** Close the PHP section and the HTML page:

**for ($n = 0; $n < count($array);**

**?>**

**$n++) {**

**</body>**

**print "The value is $array\[$n\]";**

**</html>**

**}**

**6.** Save the page as **soups3.php**, place it

**The curly brackets are used to avoid**

in the proper directory for your PHP-

**errors when printing array values that have**

enabled server, and test it in your Web

**strings for keys. Here are two examples where**

browser **D**.

**using quotation marks is not problematic, so**

**the curly brackets aren’t required:**

**$name = trim ($array\['name'\]);**

**$total = $\_POST\['qty'\] \***

**$\_POST\['price'\];**

**Curly brackets can also be used to sepa-**

**rate a variable reference from a dollar sign or**

**other characters:**

**print "The total is ${$total}.";**

**D** The execution of the loop for every element

in the array generates this page. The **foreach**

construct allows the script to access each key and

value without prior knowledge of what they are.

Using Arrays 163

[**Creating**](#index_split_000.html#p7)

**Script 7.4** The multidimensional **$books** array

stores a lot of information in one big variable.

[**Multidimensional Arrays**](#index_split_000.html#p7)

1

<!DOCTYPE html PUBLIC "-//W3C//DTD

XHTML 1.0 Transitional//EN"

Multidimensional arrays are both simple

2 "http://www.w3.org/TR/xhtml1/DTD/

and complicated at the same time. The

xhtml1-transitional.dtd">

structure and concept may be somewhat

3 <html

xmlns="http://www.w3.org/1999/

xhtml" xml:lang="en" lang="en">

difficult to grasp, but creating and

4 <head>

accessing multidimensional arrays in

5

<meta http-equiv="Content-Type"

PHP is surprisingly easy.

content="text/html;

charset=utf-8"/>

You use a multidimensional array to create

6

<title>Larry Ullman's Books and

an array containing more information than

Chapters</title>

a standard array. You accomplish this by

7 </head>

using other arrays for values instead of just

8 <body>

strings and numbers. For example:

9

<h1>Some of Larry Ullman's Books</h1>

10 <?php // Script 7.4 - books.php

**$fruits = array ('apples', 'bananas',**

11 /\* This script creates and prints out

➝ **'oranges');**

a multidimensional array. \*/

**$meats = array ('steaks',**

12 // Address error management, if you

➝ **'hamburgers', 'pork chops');**

want.

13

**$groceries = array (**

14 // Create the first array:

**'fruits' => $fruits,**

15 $phpvqs = array (1 => 'Getting Started

**'meats' => $meats,**

with PHP', 'Variables', 'HTML Forms

**'other' => 'peanuts',**

and PHP', 'Using Numbers');

**'cash' => 30.00**

16

17 // Create the second array:

**);**

18 $phpadv = array (1 => 'Advanced

This array, **$groceries**, now consists of

PHP Techniques', 'Developing Web

Applications', 'Advanced Database

one string (peanuts), one floating-point

Concepts', 'Security Techniques');

number (30.00), and two arrays (**$fruits**

19

and **$meats**).

20 // Create the third array:

21 $phpmysql = array (1 => 'Introduction

Pointing to an element in an array within an

to PHP', 'Programming with PHP',

array can seem tricky. The key (pardon the

'Creating Dynamic Web Sites',

pun) is to continue adding indices in square

'Introduction to MySQL');

brackets as necessary, working from the

22

outer array inward. With that example,

23 // Create the multidimensional array:

***bananas***

**24 $books = array (**

is at **$groceries\['fruits'\]\[1\].**

**25 'PHP VQS' => $phpvqs,**

First, you point to the element (in this case,

**26 'PHP Advanced VQP' => $phpadv,**

an array) in the **$groceries** array by using

**27 'PHP and MySQL VQP' => $phpmysql**

**\['fruits'\]**. Then, you point to the element

**28 );**

in that array based on its position—it’s the

29

second item, so you use the index **\[1\]**.

code continues on next page

In this next task, you’ll write a script

that creates another multidimensional

array example.

164 Chapter

7

**Script 7.4** continued

**To use multidimensional arrays:**

30 // Print out some values:

**1.** Begin a new document in your text

**31 print "<p>The third chapter of**

editor or IDE, to be named **books.php**

**my first book is <i>{$books\['PHP**

(**Script 7.4**):

**VQS'\]\[3\]}</i>.</p>";**

**32 print "<p>The first chapter of my**

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

**second book is <i>{$books\['PHP**

➝ **XHTML 1.0 Transitional//EN"**

**Advanced**

**VQP'\]\[1\]}</i>.</p>";**

**"http://www.w3.org/TR/xhtml1/**

**33 print "<p>The fourth chapter of**

 ➝ **DTD/xhtml1-transitional.dtd">**

**my fourth book is <i>{$books\['PHP**

**<html xmlns="http://www.w3.org/**

**and MySQL VQP'\]\[4\]}</i>.</p>";**

34

➝ **1999/xhtml" xml:lang="en" lang="en">** 35 // See what happens with foreach:

**<head>**

36 foreach ($books as $key => $value) {

**<meta**

**http-equiv="Content-Type"**

37

print "<p>$key: $value</p>\\n";

 ➝ **content="text/html;**

38 }

 ➝ **charset=utf-8"/>**

39

40 ?>

**<title>Larry Ullman's Books and**

41 </body>

 ➝ **Chapters</title>**

42 </html>

**</head>**

**<body>**

**<h1>Some of Larry Ullman's**

➝ **Books</h1>**

**2.** Create the initial PHP tags, and address

error management, if necessary:

**<?php // Script 7.4 - books.php**

**3.** Create the first array:

**$phpvqs = array (1 => 'Getting**

➝ **Started with PHP', 'Variables',**

➝ **'HTML Forms and PHP', 'Using**

➝ **Numbers');**

To build up the multidimensional array,

you’ll create three standard arrays

and then use them as the values for

the larger array. This array (called

**$phpvqs**, which is short for PHP for the

Web: Visual QuickStart Guide) uses

numbers for the keys and strings for the

values. The numbers begin with 1 and

correspond to the chapter numbers.

The values are the chapter titles.

continues on next page

Using Arrays 165

![Image 200](index-187_1.png)

**4.** Create the next two arrays:

**6.** Print out the name of the third chapter of

**$phpadv = array (1 => 'Advanced**

the PHP Visual QuickStart Guide book:

➝ **PHP Techniques', 'Developing Web**

**print "<p>The third chapter of**

➝ **Applications', 'Advanced**

➝ **my first book is <i>{$books\['PHP**

➝ **Database Concepts', 'Security**

➝ **VQS'\]\[3\]}</i>.</p>";**

➝ **Techniques');**

Following the rules stated earlier, all

**$phpmysql = array (1 =>**

you need to do to access any individual

➝ **'Introduction to PHP',**

chapter name is to begin with **$books**,

➝ **'Programming with PHP',**

follow that with the first index (**\['PHP VQS'\]**),

➝ **'Creating Dynamic Web Sites',**

and follow that with the next index (**\[3\]**).

➝ **'Introduction to MySQL');**

Because you’re placing this in a **print** call,

For each array, add only the book’s first

you enclose the whole construct in curly

four chapters for simplicity’s sake.

brackets to avoid parse errors.

**5.** Create the main, multidimensional array:

**7.** Print out two more examples:

**$books = array (**

**print "<p>The first chapter of**

**'PHP VQS' => $phpvqs,**

➝ **my second book is <i>{$books**

**'PHP Advanced VQP' => $phpadv,**

➝ **\['PHP Advanced VQP'\]\[1\]}</i>.</p>";**

**'PHP and MySQL VQP' => $phpmysql**

**print "<p>The fourth chapter of**

**);**

➝ **my fourth book is <i>{$books**

The **$books** array is the master array

➝ **\['PHP and MySQL VQP'\]\[4\]}</i>.</p>";**

for this script. It uses strings for keys

**8.** Run the **$books** array through a

(which are shortened versions of the

**foreach** loop to see the results:

book titles) and arrays for values. Use

**foreach ($books as $key => $value)**

the **array()** function to create it, as you

**{**

would any other array.

**print "<p>$key: $value</p>\\n";**

**}**

**A** The first three lines are generated

by **print** statements. The last three

show the results of the **foreach**

loop (and the notices come from

attempting to print an array).

166 Chapter

7

![Image 201](index-188_1.png)

![Image 202](index-188_2.png)

The **$key** variable will be assigned each

abbreviated book title, and the **$value**

variable ends up containing each

chapter array.

**9.** Close the PHP section and complete

the HTML page:

**?>**

**</body>**

**</html>**

**10.** Save the file as **books.php**, place it in the

proper directory for your PHP-enabled

server, and test it in your browser **A**.

**To access every element of every array,**

**you can nest two foreach loops like this B:**

**foreach ($books as $title =>**

➝ **$chapters) {**

**B** One **foreach** loop within another can access

every element of a two-dimensional array.

**print**

**"<p>$title";**

**foreach ($chapters as $number =>**

➝ **$chapter) {**

**print "<br />Chapter $number**

➝ **is $chapter";**

**}**

**print**

**'</p>';**

**}**

**Using the print\_r() or var\_dump()**

**function (preferably enclosed in HTML <pre>**

**tags for better formatting), you can view an**

**entire multidimensional array C.**

**You can create a multidimensional**

**array in one statement by using a series of**

**nested array() calls (instead of using several**

**steps as in this example). However, doing so**

**isn’t recommended, because it’s all too easy**

**to make syntactical errors as a statement**

**becomes more and more nested.**

**C** The **print\_r()** function shows the structure

**Although all the subarrays in this**

and contents of the **$books** array.

**example have the same structure (numbers for**

**indexes and four elements), that isn’t required**

**with multidimensional arrays.**

**To learn about the greater “Larry Ullman**

**Collection,” including the three books refer-**

[**enced here, head to www.LarryUllman.com.**](http://www.LarryUllman.com)

Using Arrays 167

[**Sorting Arrays**](#index_split_000.html#p7)

**TABLE 7.2 Array Sorting Functions**

PHP supports a variety of ways to sort an

**Maintains**

array (sort refers to an alphabetical sort if

**Function**

**Sorts By**

**Key-Values?**

the values being sorted are strings, or a

**sort()**

Values

No

numerical sort if the values being sorted

**rsort()**

Values

No

are numbers). When you’re sorting an

(inverse)

array, you must keep in mind that an array

**asort()**

Values

Yes

consists of pairs of keys and values. Thus,

**arsort()**

Values

Yes

an array can be sorted based on the keys

(inverse)

or the values. This is further complicated

**ksort()**

Keys

Yes

by the fact that you can sort the values and

**krsort()**

Keys (inverse)

Yes

keep the corresponding keys aligned, or

you can sort the values and have them be

assigned new keys.

To sort the values without regard to the

keys, you use **sort()**. To sort these values

(again, without regard to the keys) in

reverse order, you use **rsort()**. The syntax

for every sorting function is:

***function*****($ *array*);**

So, **sort()** and **rsort()** are used as follows:

**sort($array);**

**rsort($array);**

To sort the values while maintaining the

correlation between each value and its

key, you use **asort()**. To sort the values

in reverse while maintaining the key

correlation, you use **arsort()**.

To sort by the keys while maintaining the

correlation between the key and its value,

you use **ksort()**. Conversely, **krsort()**

sorts the keys in reverse. **Table 7.2** lists all

these functions.

Finally, **shuffle()** randomly reorganizes

the order of an array.

As an example of sorting arrays, you’ll

create a list of students and the grades

they received on a test, and then sort this

list first by grade and then by name.

168 Chapter

7

**Script 7.5** PHP provides a number of different **To sort an array:**

functions for sorting arrays, including **arsort()**

and **ksort()**.

**1.** Begin a new document in your text

editor or IDE, to be named **sort.php**

1

<!DOCTYPE html PUBLIC "-//W3C//DTD

(**Script 7.5**):

XHTML 1.0 Transitional//EN"

2 "http://www.w3.org/TR/xhtml1/DTD/

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

xhtml1-transitional.dtd">

➝ **XHTML 1.0 Transitional//EN"**

3 <html

xmlns="http://www.w3.org/1999/

**"http://www.w3.org/TR/xhtml1/**

xhtml" xml:lang="en" lang="en">

 ➝ **DTD/xhtml1-transitional.dtd">**

4 <head>

5

<meta http-equiv="Content-Type"

**<html xmlns="http://www.w3.org/**

content="text/html;

➝ **1999/xhtml" xml:lang="en"**

charset=utf-8"/>

➝ **lang="en">**

6

<title>My Little Gradebook</title>

**<head>**

7 </head>

**<meta**

**http-equiv="Content-Type"**

8 <body>

9

<?php // Script 7.5 - sort.php

 ➝ **content="text/html;**

10 /\* This script creates, sorts, and

**charset=utf-8"/>**

prints out an array. \*/

**<title>My Little Gradebook</**

11

**title>**

12 // Address error management, if you

**</head>**

want.

13

**<body>**

14 // Create the array:

**2.** Begin the PHP section, and address

15 $grades = array(

error handling, if desired:

16 'Richard' => 95,

17 'Sherwood' => 82,

**<?php // Script 7.5 - sort.php**

18 'Toni' => 98,

19 'Franz' => 87,

**3.** Create the array:

20 'Melissa' => 75,

**$grades = array(**

21 'Roddy' => 85

**'Richard' => 95,**

22 );

23

**'Sherwood' => 82,**

24 // Print the original array:

**'Toni' => 98,**

25 print '<p>Originally the array looks

**'Franz' => 87,**

like this: <br />';

**'Melissa' => 75,**

26 foreach ($grades as $student =>

**'Roddy' => 85**

$grade)

{

27

print "$student: $grade<br />\\n";

**);**

28 }

The **$grades** array consists of six

29 print

'</p>';

students’ names along with their

30

31 // Sort by value in reverse order,

corresponding grades. Because the

then print again:

grades are numbers, they don’t need

32 arsort

($grades);

to be quoted when assigning them.

33 print '<p>After sorting the array by

value using arsort(), the array looks

continues on next page

like this: <br />';

code continues on next page

Using Arrays 169

**4.** Print a caption, and then print each ele-Script 7.5 continued

ment of the array using a **foreach** loop:

34 foreach ($grades as $student =>

**print '<p>Originally the array**

$grade)

{

➝ **looks like this: <br />';**

35

print "$student: $grade<br />\\n";

**foreach ($grades as $student =>**

36 }

37 print

'</p>';

➝ **$grade) {**

38

**print "$student: $grade<br />\\n";**

39 // Sort by key, then print again:

**}**

40 ksort

($grades);

**print '</p>';**

41 print '<p>After sorting the array by

key using ksort(), the array looks

As the **$grades** array will be printed three

like this: <br />';

times, captions indicating each state of

42 foreach ($grades as $student =>

the array will be useful. At first, the script

$grade)

{

43

print "$student: $grade<br />\\n";

prints the array in the original order. To

44 }

do that, use a **foreach** loop, where each

45 print

'</p>';

index (the student’s name) is assigned to

46

**$student**, and each value (the student’s

47 ?>

grade) is assigned to **$grade**. The final

48 </body>

**print**

49 </html>

call closes the HTML paragraph.

**5.** Sort the array in reverse order by value

to determine who has the highest grade:

**arsort ($grades);**

To determine who has the highest

grade, you need to use **arsort()**

instead of **asort()**. The latter, which

sorts the array in numeric order, would

order the grades 75, 82, 85, and so on,

rather than the desired 98, 95, 87.

You also must use **arsort()** and not

**rsort()** in order to maintain the key-

value relationship (**rsort()** would

eliminate the student’s name associated

with each grade).

**6.** Print the array again (with a caption),

using another loop:

**print '<p>After sorting the array**

➝ **by value using arsort(), the**

➝ **array looks like this: <br />';**

**foreach ($grades as $student =>**

➝ **$grade) {**

**print "$student: $grade<br />\\n";**

**}**

**print '</p>';**

170 Chapter

7

![Image 203](index-192_1.png)

**7.** Sort the array by key to put the array in

alphabetical order by student name:

**ksort ($grades);**

The **ksort()** function organizes the

array by key (in this case, alphabetically)

while maintaining the key-value

correlation.

**8.** Print a caption and the array one last time:

**print '<p>After sorting the array**

➝ **by key using ksort(), the array**

➝ **looks like this: <br />';**

**foreach ($grades as $student =>**

➝ **$grade) {**

**print "$student: $grade<br />\\n";**

**A** You can sort an array in a number of ways with

**}**

varied results. Pay close attention to whether you

**print '</p>';**

want to maintain your key-value association when

choosing a sort function.

**9.** Complete the script with the standard

PHP and HTML tags:

**?>**

**</body>**

**</html>**

**10.** Save your script as **sort.php**, place

it in the proper directory for your

PHP-enabled server, and test it in

your Web browser **A**.

**Because each element in an array must**

**have its own unique key, the $grades array**

**will only work using unique student names.**

**The natsort() and natcasesort()**

**functions sort a string (while maintaining**

**key-value associations) using natural order.**

**The most obvious example of natural order**

**sorting is that it places name2 before name12,**

**whereas sort() orders them name12 and**

**then name2.**

**The usort(), uasort(), and ursort()**

**functions let you sort an array using a user-**

**defined comparison function. These functions**

**are most often used with multidimensional**

**arrays.**

Using Arrays 171

![Image 204](index-193_1.png)

![Image 205](index-193_2.png)

[**Transforming Between**](#index_split_000.html#p7)

The ***separator*** refers to whatever character(s)

define where one value ends and another

[**Strings and Arrays**](#index_split_000.html#p7)

begins. Commonly this is a comma, a tab,

or a blank space. Thus your code might be

Now that you have an understanding of

**$array = explode(',', $string);**

both strings and arrays, this next section

introduces two functions for switching

or

between the formats. The first, **implode()**,

**$array = explode(' ', $string);**

turns an array into a string. The second,

To go from an array to a string, you need

**explode()**, does just the opposite. Here

to define what the separator (aka the glue)

are some reasons to use these functions:

should be, and PHP does the rest:

■

To turn an array into a string in order to

**$string = implode( *glue*, $array);**

pass that value appended to a URL (which

**$string = implode(',', $array);**

you can’t do as easily with an array)

or

■

To turn an array into a string in order to

store that information in a database

**$string = implode(' ', $array);**

■

To turn a string into an array to convert

To demonstrate how to use **explode()** and

a comma-delimited text field (say a

**implode()**, you’ll create an HTML form that

keyword search area of a form) into its

takes a space-delimited string of names

separate parts

from the user **A**. The PHP script will then

turn the string into an array so that it can

The syntax for using **explode()** is as follows:

sort the list. Finally, the code will create and

**$array = explode( *separator*, $string);**

return the alphabetized string **B**.

**A** This HTML form takes a list of words, which is then alphabetized by the **list.php** script **B**.

**B** Here’s the same list, alphabetized

for the user. This process is quick and

easy to code, but doing so would be

impossible without arrays.

172 Chapter

7

**Script 7.6** This is a simple HTML form where a **To create the HTML form:**

user can submit a list of words. Including detailed

instructions for how the form should be used is a

**1.** Begin a new document in your text

prudent Web design policy.

editor or IDE, to be named **list.html**

(**Script 7.6**):

1

<!DOCTYPE html PUBLIC "-//W3C//DTD

XHTML 1.0 Transitional//EN"

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

2 "http://www.w3.org/TR/xhtml1/DTD/

➝ **XHTML 1.0 Transitional//EN"**

xhtml1-transitional.dtd">

**"http://www.w3.org/TR/xhtml1/**

3 <html

xmlns="http://www.w3.org/1999/

xhtml" xml:lang="en" lang="en">

 ➝ **DTD/xhtml1-transitional.dtd">**

4 <head>

**<html xmlns="http://www.w3.org/**

5

<meta http-equiv="Content-Type"

➝ **1999/xhtml" xml:lang="en"**

content="text/html;

➝ **lang="en">**

charset=utf-8"/>

**<head>**

6

<title>I Must Sort This Out!</title>

7 </head>

**<meta**

**http-equiv="Content-Type"**

8 <body>

 ➝ **content="text/html;**

9

<!-- Script 7.6 - list.html -->

 ➝ **charset=utf-8"/>**

10 <div><p>Enter the words you want

**<title>I Must Sort This Out!**

alphabetized with each individual word

 ➝ **</title>**

separated by a space:</p>

11

**</head>**

12 <form action="list.php" method="post">

**<body>**

13

**<!-- Script 7.6 - list.html -->**

14

<input type="text" name="words"

**2.** Create an HTML form with a text input:

size="60"

/>

15

<input type="submit" name="submit"

**<div><p>Enter the words you**

value="Alphabetize!"

/>

➝ **want alphabetized with each**

16

17 </form>

➝ **individual word separated by**

18 </div>

➝ **a space:</p>**

19 </body>

**<form action="list.php"**

20 </html>

➝ **method="post">**

**<input type="text" name="words"**

 ➝ **size="60" />**

It’s important in cases like this to

instruct the user. For example, if the

user enters a comma-delimited list, the

PHP script won’t be able to handle the

string properly (after completing both

scripts, try using commas in lieu of

spaces and see what happens).

continues on next page

Using Arrays 173

**3.** Create a submit button, and then close **Script 7.7** Because the **explode()** and **implode()**

the form and the HTML page:

functions are so simple and powerful, you can

quickly and easily sort a submitted list of words

**<input type="submit" name=**

(of practically any length) in just a couple of lines.

 ➝ **"submit" value="Alphabetize!" />** 1

<!DOCTYPE html PUBLIC "-//W3C//DTD

**</form>**

XHTML 1.0 Transitional//EN"

**</div>**

2 "http://www.w3.org/TR/xhtml1/DTD/

**</body>**

xhtml1-transitional.dtd">

**</html>**

3 <html

xmlns="http://www.w3.org/1999/

xhtml" xml:lang="en" lang="en">

**4.** Save your script as **list.html** and

4 <head>

place it in the proper directory for your

5

<meta http-equiv="Content-Type"

PHP-enabled server.

content="text/html;

charset=utf-8"/>

Now you’ll write the **list.php** page to

6

<title>I Have This Sorted Out</title>

process the data generated by **list.html**.

7 </head>

8 <body>

9

<?php // Script 7.7 - list.php

**To convert between**

10 /\* This script receives a string in

**strings and arrays:**

$\_POST\['words'\]. It then turns it into

an

array,

**1.** Begin a new document in your text

11 sorts the array alphabetically, and

editor or IDE, to be named **list.php**

reprints it. \*/

(**Script 7.7**):

12

13 // Address error management, if you

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

want.

➝ **XHTML 1.0 Transitional//EN"**

14

**"http://www.w3.org/TR/xhtml1/**

15 // Turn the incoming string into an

 ➝ **DTD/xhtml1-transitional.dtd">**

array:

**<html xmlns="http://www.w3.org/**

**16 $words\_array = explode(' ' ,**

**$\_POST\['words'\]);**

➝ **1999/xhtml" xml:lang="en"**

17

➝ **lang="en">**

18 // Sort the array:

**<head>**

**19 sort($words\_array);**

**<meta**

**http-equiv="Content-Type"**

20

 ➝ **content="text/html;**

21 // Turn the array back into a string:

**22 $string\_words = implode('<br />',**

 ➝ **charset=utf-8"/>**

**$words\_array);**

**<title>I Have This Sorted Out**

23

 ➝ **</title>**

24 // Print the results:

**</head>**

**25 print "<p>An alphabetized**

**<body>**

**version of your list is: <br />**

**$string\_words</p>";**

**<?php // Script 7.7 - list.php**

26

**2.** Turn the incoming string, **$\_**

27 ?>

**POST\['words'\]**

28 </body>

, into an array:

29 </html>

**$words\_array = explode(' ' ,**

➝ **$\_POST\['words'\]);**

This line of code creates a new array,

**$words\_array**, out of the string

174 Chapter

7

**$\_POST\['words'\]**. Each space between

the words in **$\_POST\['words'\]** indicates

that the next word should be a new array

element. Hence the first word becomes

**$words\_array\[0\]**, then there is a space

in **$\_POST\['words'\]**, then the second

word becomes **$words\_array\[1\]**, and so

forth, until the end of **$\_POST\['words'\]**.

**3.** Sort the array alphabetically:

**sort($words\_array);**

Because you don’t need to maintain key-

value associations in the **$words\_array**,

you can use **sort()** instead of **asort()**.

**4.** Create a new string out of the sorted array:

**$string\_words = implode('<br />',**

➝ **$words\_array);**

Arrays don’t print as easily as strings,

so turn **$words\_array** into a string

called **$string\_words**. The resulting

string starts with the value of **$words\_**

**array\[0\]**, followed by the HTML **<br />**

tag, the value of **$words\_array\[1\]**, and

so on. Using **<br />** instead of a space

or comma gives the list a more readable

format when it’s printed to the browser.

**5.** Print the new string to the browser:

**print "<p>An alphabetized**

➝ **version of your list is:**

➝ **<br />$string\_words</p>";**

**6.** Close the PHP section and the HTML page:

**?>**

**</body>**

**</html>**

**7.** Save your page as **list.php**, place it in

the same directory as **list.html**, and

test both scripts in your Web browser

**A** and **B**.

**You’ll also run across code written using**

**the join() function, which is synonymous**

**with implode().**

Using Arrays 175

![Image 206](index-197_1.png)

[**Creating an Array**](#index_split_000.html#p7) 

[**from a Form**](#index_split_000.html#p7)

Throughout this chapter, you’ve

established arrays entirely from within

a PHP page. You can, however, send an

array of data to a PHP script via an HTML

form. In fact, every time you use **$\_POST**,

this is the case. But you can take this one

step further by creating arrays using an

HTML form. Such arrays will then be a

part of the greater **$\_POST** array (thereby

making **$\_POST** a multidimensional array).

A logical use of this capability is in dealing

with checkboxes, where users might need

to select multiple options from a group **A**.

The HTML source code for a checkbox is

as follows:

**<input type="checkbox"**

**name="topping" value="Ham" />**

The problem in this particular case is that

each form element must have a unique

name. If you created several checkboxes,

each with a name of topping, only the

value of the last checked box would be

received in the PHP script. If you were to

create unique names for each checkbox—

ham, tomato, black\_olives, etc.—working

with the selected values would be tedious.

The workaround is to use array syntax, as

demonstrated in the next example.

**A** Checkboxes in an HTML form, presenting several possible options.

176 Chapter

7

**Script 7.8** This HTML form has an array for the **To create an array with**

checkbox input names.

**an HTML form:**

1

<!DOCTYPE html PUBLIC "-//W3C//DTD

**1.** Begin a new document in your text

XHTML 1.0 Transitional//EN"

editor or IDE, to be named **event.html**

2 "http://www.w3.org/TR/xhtml1/DTD/

(**Script 7.8**):

xhtml1-transitional.dtd">

3 <html

xmlns="http://www.w3.org/1999/

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

xhtml" xml:lang="en" lang="en">

➝ **XHTML 1.0 Transitional//EN"**

4 <head>

5

<meta http-equiv="Content-Type"

**"http://www.w3.org/TR/xhtml1/**

content="text/html;

 ➝ **DTD/xhtml1-transitional.dtd">**

charset=utf-8"/>

**<html xmlns="http://www.w3.org/**

6

<title>Add an Event</title>

➝ **1999/xhtml" xml:lang="en"**

7 </head>

➝ **lang="en">**

8 <body>

9

<!-- Script 7.8 - event.html -->

**<head>**

10 <div><p>Use this form to add an

**<meta**

**http-equiv="Content-Type"**

event:</p>

 ➝ **content="text/html;**

11

➝ **charset=utf-8"/>**

12 <form action="event.php" method="post">

**<title>Add an Event</title>**

13

14

<p>Event Name: <input type="text"

**</head>**

name="name" size="30" /></p>

**<body>**

15 <p>Event

Days:

**<!-- Script 7.8 - event.html -->**

**16**

**<input type="checkbox" name=**

**<div><p>Use this form to add an**

**"days\[\]" value="Sunday" /> Sun**

➝ **event:</p>**

**17**

**<input type="checkbox" name=**

**"days\[\]" value="Monday" /> Mon**

**2.** Begin the HTML form:

**18**

**<input type="checkbox" name=**

**"days\[\]" value="Tuesday" /> Tue**

**<form action="event.php"**

**19**

**<input type="checkbox" name=**

➝ **method="post">**

**"days\[\]" value="Wednesday" /> Wed**

**20**

**<input type="checkbox" name=**

This form will be submitted to **event.php**,

**"days\[\]" value="Thursday" /> Thu**

found in the same directory as this HTML

**21**

**<input type="checkbox" name=**

page.

**"days\[\]" value="Friday" /> Fri**

**22**

**<input type="checkbox" name=**

**3.** Create a text input for an event name:

**"days\[\]" value="Saturday" /> Sat**

**<p>Event Name: <input type="text"**

23 </p>

24

<input type="submit" name="submit"

➝ **name="name" size="30" /></p>**

value="Add the Event!" />

This example allows the user to enter

25

an event name and the days of the

26 </form>

week when it takes place.

27 </div>

28 </body>

continues on next page

29 </html>

Using Arrays 177

**4.** Create the days checkboxes:

**<p>Event Days:**

**<input type="checkbox" name=**

➝ **"days\[\]" value="Sunday" /> Sun**

**<input type="checkbox" name=**

➝ **"days\[\]" value="Monday" /> Mon**

**<input type="checkbox" name=**

➝ **"days\[\]" value="Tuesday" /> Tue**

**<input type="checkbox" name=**

➝ **"days\[\]" value="Wednesday" /> Wed**

**<input type="checkbox" name=**

➝ **"days\[\]" value="Thursday" /> Thu**

**<input type="checkbox" name=**

➝ **"days\[\]" value="Friday" /> Fri**

**<input type="checkbox" name=**

➝ **"days\[\]" value="Saturday" /> Sat**

**</p>**

All of these checkboxes use ***days\[ \]***

as the **name** value, which creates a

**$\_POST\['days'\]** array in the PHP script.

The **value** attributes differ for each

checkbox, corresponding to the day of

the week.

**5.** Complete the HTML form:

**<input type="submit" name=**

 ➝ **"submit" value="Add the**

 ➝ **Event!" />**

**</form>**

**6.** Complete the HTML page:

**</div>**

**</body>**

**</html>**

**7.** Save your page as **event.html** and

place it in the proper directory for your

PHP-enabled server.

You also need to write the **event.php** page

to handle this HTML form.

178 Chapter

7

**Script 7.9** This PHP script receives an array of **To handle the HTML form:**

values in **$\_POST\['days'\]**.

**1.** Begin a new document in your text

1

<!DOCTYPE html PUBLIC "-//W3C//DTD

editor or IDE, to be named **event.php**

XHTML 1.0 Transitional//EN"

(**Script 7.9**):

2 "http://www.w3.org/TR/xhtml1/DTD/

xhtml1-transitional.dtd">

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

3 <html

xmlns="http://www.w3.org/1999/

➝ **XHTML 1.0 Transitional//EN"**

xhtml" xml:lang="en" lang="en">

**"http://www.w3.org/TR/xhtml1/**

4 <head>

 ➝ **DTD/xhtml1-transitional.dtd">**

5

<meta http-equiv="Content-Type"

content="text/html;

**<html xmlns="http://www.w3.org**

charset=utf-8"/>

➝ **/1999/xhtml" xml:lang="en" lang="en">** 6

<title>Add an Event</title>

**<head>**

7 </head>

**<meta**

**http-equiv="Content-Type"**

8 <body>

 ➝ **content="text/html;**

9

<?php // Script 7.9 - event.php

10 /\* This script handle the event form. \*/

 ➝ **charset=utf-8"/>**

11

**<title>Add an Event</title>**

12 // Address error management, if you

**</head>**

want.

**<body>**

13

14 // Print the text:

**2.** Create the initial PHP tag, address error

15 print "<p>You want to add an event

management (if need be), and print an

called <b>{$\_POST\['name'\]}</b> which

introductory message:

takes place on: <br />";

16

**<?php // Script 7.9 - event.php**

17 // Print each weekday:

**print "<p>You want to add an event**

**18 if (isset($\_POST\['days'\]) AND**

➝ **called <b>{$\_POST\['name'\]}</b>**

**is\_array($\_POST\['days'\]))**

**{**

➝ **which takes place on: <br />";**

19

**20**

**foreach ($\_POST\['days'\] as $day) {**

The **print** line prints out the value

**21**

**print "$day<br />\\n";**

of the event’s name. In a real-world

**22 }**

version of this script, you would add

23

24 } else {

a conditional to check that a name

25

print 'Please select at least one

value was entered first (see Chapter 6,

weekday for this event!';

“Control Structures”).

26 }

27

**3.** Begin a conditional to check that at

28 // Complete the paragraph:

least one weekday was selected:

29 print

'</p>';

**if (isset($\_POST\['days'\]) AND**

30 ?>

31 </body>

➝ **is\_array($\_POST\['days'\])) {**

32 </html>

If no checkbox was clicked, then

**$\_POST\['days'\]** won’t be an existing

variable. To avoid an error caused by

referring to a variable that does not

exist, the first part of the conditional

checks that **$\_POST\['days'\]** is set.

continues on next page

Using Arrays 179

![Image 207](index-201_1.png)

The second part of the condition—

and both must be **TRUE** for the entire

**The List Function**

condition to be **TRUE**—confirms that

The **list()** function is used to assign

**$\_POST\['days'\]** is an array. This is a

array element values to individual

good step to take because a **foreach**

variables. To start with an example:

loop will create an error if it receives a

**$date = array('Thursday', 23,**

variable that isn’t an array **B**.

➝ **'October');**

**4.** Print each selected weekday:

**list($weekday, $day, $month) =**

**foreach ($\_POST\['days'\] as $day) {**

➝ **$date;**

**print "$day<br />\\n";**

Now there is a **$weekday** variable with a

**}**

value of ***Thursday***, a **$day** variable with

a value of **23**, and a **$month** variable

To print out each checked weekday,

with a value of ***October***.

run the **$\_POST\['days'\]** array through

a **foreach** loop. The array contains the

There are two caveats for using **list()**.

First, **list()** only works on arrays

values (from the HTML form inputs, for

numerically indexed starting at 0.

example, Monday, Tuesday, and so on)

Second, when you’re using the **list()**

for every box that was selected.

function, you must acknowledge each

**5.** Complete the **is\_array()** conditional:

array element. You could not do this:

**} else {**

**list($weekday, $month) = $date;**

**print 'Please select at least**

But you can use empty values to ignore

 ➝ **one weekday for this event!';**

elements:

**}**

**list ($weekday, , $month) = $date;**

If no weekday was selected, then the

or

**isset() AND is\_array()** condition is

**FALSE**, and this message is printed.

**list (, , $month) = $date;**

The **list()** function is often used when

retrieving values from a database.

**B** Attempting to use **foreach** on a variable that is not an array is a common cause of errors.

180 Chapter

7

![Image 208](index-202_1.png)

![Image 209](index-202_2.png)

![Image 210](index-202_3.png)

**6.** Complete the main paragraph, the PHP

section, and the HTML page:

**print '</p>';**

**?>**

**</body>**

**</html>**

**7.** Save the page as **event.php**, place it in

the same directory as **event.html**, and

test both pages in your Web browser

**C**, **D**, and **E**.

**The same technique demonstrated here**

**can be used to allow a user to select multiple**

**options in a drop-down menu. Just give the**

**menu a name with a syntax like *something*\[\],**

**then the PHP script will receive every selection**

**in $\_POST\[' *something*'\].**

**C** The HTML form with its checkboxes.

**D** The results of the HTML form.

**E** If users don’t check any of the day boxes, they’ll see this message.

Using Arrays 181

[**Review and Pursue**](#index_split_000.html#p7)

**Pursue**

■

Check out the PHP manual’s pages

If you have any problems with the review

for the array-related functions. Look

questions or the pursue prompts, turn

into some of the other available array

to the book’[s supporting forum (www.](http://www.LarryUllman.com/forum/)

functions. In particular I’d recommend

[LarryUllman.com/forum/ ).](http://www.LarryUllman.com/forum/)

familiarizing yourself with **array\_**

**key\_exists()**, **array\_search()**, and

**Review**

**in\_array()**.

■

What’s the difference between an

■

Rewrite **soups2.php** so that it displays

indexed array and an associative

the number of elements in the array

array?

without using a separate variable. Hint:

■

When should you use quotation marks

You’ll need to concatenate the **count()**

for an array’s key or value? When

function call into the **print** statement.

shouldn’t you?

■

Create another script that creates and

■

How do you print a specific array

displays a multidimensional array (or

element? How do you print every

some of it, anyway).

element in an array?

■

Rewrite **list.php** so that it uses

■

What happens if you don’t use the

**foreach** instead of **implode()**, but still

square brackets when adding an

prints each sorted word on its own

element to an array?

line in the browser. Also add some

form validation so that it only attempts

■

What function returns the number of

to parse and sort the string if it has a

elements in an array?

value.

■

When must you use curly brackets for

printing array elements?

■

What is the difference between

the **sort()** and **asort()** functions?

Between **sort()** and **rsort()**?

■

What is the syntax for **explode()**? For

**implode()**? If you don’t remember,

check out the PHP manual page for

either function.

182 Chapter

7

[**8**](#index_split_000.html#p8)

[Creating Web](#index_split_000.html#p8)

[Applications](#index_split_000.html#p8)

The book to this point has covered the

fundamentals of programming with PHP;

**In This Chapter**

now it’s time to begin tying it all together

into actual Web applications. In this chap-

Creating Templates

184

ter, you’ll learn a number of functions and

Using External Files

192

techniques for making your Web sites more

Using Constants

197

professional, more feature-rich, and easier

to maintain.

Working with the Date and Time

201

First, you’ll learn how to use external files

Handling HTML Forms with PHP,

to break Web pages into individual pieces,

Revisited 204

allowing you to separate the logic from the

Making Forms Sticky

210

presentation. Then you’ll tinker with con-

Sending Email

217

stants, a special data type in PHP. After that,

you’ll be introduced to some of the date-

Output Buffering

222

and time-related functions built into PHP.

Manipulating HTTP Headers

225

Two of the chapter’s topics discuss useful

Review and Pursue

230

techniques: having the same page both

display and handle an HTML form, and

having a form remember user-submitted

values. After that, you’ll see how easy

it can be to send email from PHP. The

chapter concludes with the slightly more

advanced topics of output buffering and

HTTP headers.

![Image 211](index-205_1.jpg)

![Image 212](index-205_2.jpg)

![Image 213](index-205_3.jpg)

[**Creating Templates**](#index_split_000.html#p8)

Every example thus far has been a one-

page script that handles an HTML form,

sorts arrays, performs calculations,

and so on. As you begin to develop

multiple-page Web sites (which is to say,

Web applications), it quickly becomes

impractical to repeat common elements

on multiple pages.

On more sophisticated Web sites, many

features, such as the HTML design, will

**A** The home page for the third edition of this

book has its page-specific content in the left

be used by every, or almost every, page

column and common elements in the right.

within the site. You can put these elements

into each individual page, but when you

need to make a change, you’ll be required

to make that change over and over again.

You can save time by creating templates

that separate out the repeating content

from the page-specific materials. For

example, a Web site may have navigation,

copyright, and other features that repeat

across multiple pages **A** and **B**.

When you first start doing dynamic Web

development, creating and using templates

can be daunting. The key is to start with

**B** The table of contents page uses some of the

same common elements as the home page **A**,

a basic prototype, as if you were creating

thanks to the templates.

a static Web page, and then divide that

prototype into reusable parts. Using the

PHP functions introduced in the next

section of this chapter, the repeating parts

can be easily included in each page while

the new content is generated on a page-

by-page basis. To create the template in

use by this chapter’s examples, let’s start

with the prototype. This example’s layout **C**

was created by James Koster of Six Shooter

[Media (www.sixshootermedia.com), and](http://www.sixshootermedia.com)

used with his kind permission.

**C** The design for this chapter’s examples, as a

single, static HTML page.

184 Chapter

8

**Script 8.1** This script represents the basic look **To create the layout model:**

each page in the site should have.

**1.** Begin a new HTML document in

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

your text editor or IDE, to be named

1.1//EN"

"http://www.w3.org/TR/xhtml11/

**template.html** (**Script 8.1**):

DTD/xhtml11.dtd">

2 <html

xmlns="http://www.w3.org/1999/

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

xhtml"

xml:lang="en">

➝ **XHTML 1.1//EN" "http://www.**

3 <head>

➝ **w3.org/TR/xhtml11/DTD/xhtml11.dtd">**

4

<title>Raise High the Roof Beam!

A J.D. Salinger Fan Club</title>

**<html xmlns="http://www.w3.org/**

5

<meta http-equiv="content-type"

➝ **1999/xhtml" xml:lang="en">**

content="text/html; charset=utf-8" />

**<head>**

6

<link rel="stylesheet"

**<title>Raise High the Roof**

href="css/1.css" type="text/css"

 ➝ **Beam! A J.D. Salinger Fan**

media="screen,projection"

/>

7 </head>

 ➝ **Club</title>**

8 <body>

**<meta**

**http-equiv="content-type"**

9 <div

id="wrapper">

 ➝ **content="text/html;**

10

 ➝ **charset=utf-8" />**

11 <div

id="header">

12

<p class="description">A J.D.

The first step in developing any

Salinger

Fan

Club</p>

template system is to create a model

13 <h1><a

href="index.php">Raise

High

document—an example of what a basic

the

Roof

Beam!</a></h1>

14 <ul

id="nav">

page should look like. Once you’ve

15

<li><a href="books.php">

created this, you can break it down

Books</a></li>

into its parts.

16 <li><a

href="#">Stories</a></li>

17 <li><a

href="#">Quotes</a></li>

**2.** Add the CSS code:

18 <li><a

href="login.php">

**<link rel="stylesheet"**

Login</a></li>

19

<li><a href="register.php">

➝ **href="css/1.css" type="text/css"**

Register</a></li>

➝ **media="screen,projection" />**

20 </ul>

This example uses CSS for most of the

21 </div><!-- header -->

22

formatting and layout controls. The CSS

23 <div

id="sidebar">

itself is stored in an external file that

24 <h2>Favorite

Quotes</h2>

becomes part of this page through the

25 <p

class="news">I

don't

exactly

**link** tag. The file itself is named simply

know what I mean by that, but

I mean it.<br />- <em>The

1.css, and is to be stored in a folder

Catcher

in

the

Rye</em></p>

named css.

26 <p

class="news">I

privately

say

to you, old friend... please

Note that you’ll need to download the

accept from me this unpretentious

CSS file from the book’s corresponding

bouquet

of

early-blooming

W[eb site (www.LarryUllman.com).](http://www.LarryUllman.com)

parentheses: (((()))).<br />- <em>

You’ll find it as part of the book’s

Raise High the Roof Beam,

downloadable code.

Carpenters and Seymour: An

Introduction</em></p>

continues on next page

27 </div><!-- sidebar -->

28

code continues on next page

Creating Web Applications 185

**3.** Close the HTML head, begin the body,

**Script 8.1** continued

and create a wrapper **div** tag:

29 <div

id="content">

**</head>**

30

<!-- BEGIN CHANGEABLE CONTENT. -->

**<body>**

31

<h2>Welcome to a J.D. Salinger Fan

**<div id="wrapper">**

Club</h2>

32

<p>Lorem ipsum dolor sit amet,

Many of today’s designs wrap the entire

consectetur adipisicing elit, sed

page content within a primary **div**, so

do eiusmod tempor incididunt ut

labore et dolore magna aliqua. Ut

that all of the content can easily be

enim ad minim veniam, quis nostrud

formatted within the browser window.

exercitation ullamco laboris

**4.** Create the page’s header:

nisi ut aliquip ex ea commodo

consequat. Duis aute irure dolor

**<div id="header">**

in reprehenderit in voluptate

**<p class="description">A J.D.**

velit esse cillum dolore eu fugiat

 ➝ **Salinger Fan Club</p>**

nulla pariatur. Excepteur sint

**<h1><a href="index.php">Raise**

occaecat cupidatat non proident,

sunt in culpa qui officia deserunt

 ➝ **High the Roof Beam!</a></h1>**

mollit anim id est laborum.</p>

**<ul**

**id="nav">**

33 <h2>Another

Header</h2>

**<li><a**

**href="books.php">**

34

<p>Lorem ipsum dolor sit amet,

 ➝ **Books</a></li>**

consectetur adipisicing elit, sed

**<li><a**

**href="#">Stories</a></li>**

do eiusmod tempor incididunt ut

labore et dolore magna aliqua. Ut

**<li><a**

**href="#">Quotes</a></li>**

enim ad minim veniam, quis nostrud

**<li><a**

**href="login.php">**

exercitation ullamco laboris

 ➝ **Login</a></li>**

nisi ut aliquip ex ea commodo

**<li><a**

**href="register.php">**

consequat. Duis aute irure dolor

in reprehenderit in voluptate

➝ **Register</a></li>**

velit esse cillum dolore eu fugiat

**</ul>**

nulla pariatur. Excepteur sint

**</div><!-- header -->**

occaecat cupidatat non proident,

sunt in culpa qui officia deserunt

The header area (also defined in the CSS

mollit anim id est laborum.</p>

code) creates the banner and the primary

35

<!-- END CHANGEABLE CONTENT. -->

navigation links to the other pages in

36 </div><!-- content -->

the Web application. The specific links

37

reference four PHP scripts, all of which

38 <div

id="footer">

39

<p>Template design by <a

will be developed in this chapter.

href="http://www.sixshootermedia.

com">

Six Shooter Media</a>.</p>

40 <p>&copy;

2011</p>

41 </div><!-- footer -->

42

43 </div><!-- wrapper -->

44 </body>

45 </html>

186 Chapter

8

**5.** Create the page’s sidebar:

**7.** Create the page’s content:

**<div id="sidebar">**

**<h2>Welcome to a J.D. Salinger**

**<h2>Favorite**

**Quotes</h2>**

➝ **Fan Club</h2>**

**<p class="news">I don't**

**<p>Lorem ipsum dolor sit**

 ➝ **exactly know what I mean**

➝ **amet...</p>**

 ➝ **by that, but I mean it.**

For the prototype, the content is just a

 ➝ **<br />- <em>The Catcher in**

couple of headers and a whole lot of

 ➝ **the Rye</em></p>**

text (there’s more in the actual script

**<p class="news">I privately**

than I’ve included in this step).

 ➝ **say to you, old friend...**

 ➝ **please accept from me this**

**8.** Mark the end of the changeable content:

 ➝ **unpretentious bouquet of**

**<!-- END CHANGEABLE CONTENT. -->**

 ➝ **early-blooming parentheses:**

**</div><!-- content -->**

 ➝ **(((()))).<br />- <em>Raise**

The code in Step 7 is the only text that

 ➝ **High the Roof Beam,**

will change on a page-by-page basis.

 ➝ **Carpenters and Seymour:**

Just as an HTML comment indicates

 ➝ **An Introduction</em></p>**

where that section starts, one here

**</div><!-- sidebar -->**

indicates where it ends.

In the original template, the sidebar

**9.** Add the footer:

can be used for latest news, secondary

links, a search box, and so forth. In

**<div id="footer">**

this site’s template, a couple of quotes

**<p>Template design by <a href=**

are highlighted.

➝ **"http://www.sixshootermedia.**

➝ **com">Six Shooter Media</a>.</p>**

**6.** Begin, and mark, the start of the page-

**<p>&copy;**

**2011</p>**

specific content:

**</div><!-- footer -->**

**<div id="content">**

The footer includes a credit and an

**<!-- BEGIN CHANGEABLE CONTENT. -->**

indication of copyright.

Everything up until this comment will

**10.** Finish the HTML page:

remain the same for every page in the

Web application. To indicate where the

**</div><!-- wrapper -->**

page-specific content begins (for your

**</body>**

own benefit), include an HTML comment.

**</html>**

In fact, looking back at the template so

To make the template easier to modify

far, you’ll see a number of HTML com-

and maintain, you’ll notice that HTML

ments, helping to indicate what each

comments indicate which **div**s are

piece of the page is for. You cannot  over-

being closed.

comment your HTML or PHP code!

**11.** Save the file as **template.html** and test

Just before that, the content area is begun.

it in your Web browser **C**.

This area is defined in the CSS code and

Once you’ve completed a prototype that

properly formats the main content part of

you like, you can break it into its various

the page. In other words, on every page,

parts to generate the template system.

that page’s content will go within the one

**div** that has an **id** of **content**.

Creating Web Applications 187

![Image 214](index-209_1.png)

**To create the header file:**

**1.** Open **template.html** (Script 8.1) in your

text editor or IDE, if it isn’t already open.

**2.** Select everything from the initial HTML

code to the **<!-- BEGIN CHANGEABLE**

**CONTENT -->** HTML comment **D**.

Part of the benefit of identifying the

start of the page-specific content with

an HTML comment is that it simplifies

breaking the model into its parts.

**D** Using the prototype file, select and copy the initial lines of code to create the header.

188 Chapter

8

**Script 8.2** This is a basic header file that creates **3.** Copy this code.

the HTML head information, includes the CSS file,

and begins the body.

Using your Edit menu or keyboard shortcut

(Ctrl+C on Windows, Command+C on the

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

Macintosh), copy all of the highlighted

1.1//EN" "http://www.w3.org/TR/xhtml11/

DTD/xhtml11.dtd">

code to your computer’s temporary

2

<html xmlns="http://www.w3.org/1999/

memory (the clipboard).

xhtml" xml:lang="en">

3 <head>

**4.** Create a new, blank document in

4

<title>Raise High the Roof Beam!

your text editor or IDE, to be named

A J.D. Salinger Fan Club</title>

**header.html**.

5

<meta http-equiv="content-type"

content="text/html; charset=utf-8" />

**5.** Paste the copied text into the document

6

<link rel="stylesheet"

(**Script 8.2**).

href="css/1.css" type="text/css"

media="screen,projection" />

Using your Edit menu or keyboard

7 </head>

shortcut (Ctrl+V on Windows,

8 <body>

Command+V on the Macintosh),

9 <div

id="wrapper">

10

paste all of the highlighted code

11 <div

id="header">

into this new document.

12

<p class="description">A J.D.

Salinger Fan Club</p>

**6.** Save the file as **header.html**.

13

<h1><a href="index.php">Raise High

Now that the header file has been created,

the Roof Beam!</a></h1>

14 <ul

id="nav">

you’ll make the footer file using the same

15

<li><a href="books.php">Books

process.

</a></li>

16 <li><a

href="#">Stories</a></li>

17 <li><a

href="#">Quotes</a></li>

18

<li><a href="login.php">Login

</a></li>

19

<li><a href="register.php">

Register</a></li>

20 </ul>

21 </div><!-- header -->

22

23 <div

id="sidebar">

24 <h2>Favorite

Quotes</h2>

25

<p class="news">I don't exactly

know what I mean by that,

but I mean it.<br />- <em>The

Catcher in the Rye</em></p>

26

<p class="news">I privately say to

you, old friend... please accept

from me this unpretentious

bouquet of early-blooming

parentheses: (((()))).<br />-

<em>Raise High the Roof Beam,

Carpenters and Seymour: An

Introduction</em></p>

27 </div><!-- sidebar -->

28

29 <div

id="content">

30

<!-- BEGIN CHANGEABLE CONTENT. -->

31

<!-- Script 8.2 - header.html -->

Creating Web Applications 189

![Image 215](index-211_1.png)

**To create the footer file:**

**Script 8.3** This is a basic footer file that concludes

the HTML page.

**1.** Open **layout.html** (Script 8.1) in your

text editor or IDE, if it isn’t already open.

1

<!-- Script 8.3 - footer.html -->

2

<!-- END CHANGEABLE CONTENT. -->

**2.** Select everything from the **<!-- END**

3

</div><!-- content -->

**CHANGEABLE CONTENT -->** HTML

4

comment to the end of the script **E**.

5 <div

id="footer">

6

<p>Template design by <a

**3.** Copy this code.

href="http://www.sixshootermedia.

com">Six Shooter Media</a>.</p>

**4.** Create a new, blank document in your

7 <p>&copy;

2011</p>

text editor, to be named **footer.html**.

8

</div><!-- footer -->

**5.** Paste the copied text into the document

9

10 </div><!-- wrapper -->

(**Script 8.3**).

11 </body>

**6.** Save the file as **footer.html**.

12 </html>

**E** Again using the prototype file, select and copy the concluding lines of code for the footer.

190 Chapter

8

![Image 216](index-212_1.png)

**There are many far more complex**

**template systems you can use in PHP to**

**separate the design from the logic. The**

**best known of these is probably Smarty**

[**(www.smarty.net).**](http://www.smarty.net)

**Although this example uses CSS for its**

**layout, you can certainly use tables instead F.**

**Your header file might begin the HTML page**

**and the table. Each content page would then**

**create its own specific content, and the footer**

**file would complete the table and the HTML**

**F** This mundane example shows how a table can

**page. To turn such a design into a template,**

be used with template files to create a design.

**copy all of the code up to Page-specific**

**content goes here. into a header file and**

**everything after that into a footer file.**

**CSS Templates**

Cascading Style Sheets (CSS) have been an increasingly important part of the World Wide Web for some time. Their initial usage was focused on cosmetics (font sizes, colors, and so on), but now CSS is frequently used in lieu of tables to control the layout of pages. The Web application in this chapter uses this approach.

This example defines four areas of the page—header, sidebar, content, and footer. The content area will change for each page. The other areas contain standard items, such as navigation links, that appear on each page of the site.

Just to be clear: The relationship between PHP and CSS is the same as that between PHP and HTML—PHP runs on the server and HTML and CSS are significant to the browser. As with HTML, you can use PHP to generate CSS, but in this example, the CSS is hard-coded into a separate file.

Creating Web Applications 191

![Image 217](index-213_1.png)

![Image 218](index-213_2.png)

[**Using External Files**](#index_split_000.html#p8)

As the preceding section stated, you

can save development time by creating

separate pages for particular elements and

then incorporating them into the main PHP

pages using specific functions. Two of these

functions are **include()** and **require()**:

**include ('file.php');**

**require ('file.html');**

Both functions work the same way, with

one relatively insignificant difference: If an

**A** When an **include()** fails, warnings are issued,

**include()** function fails, the PHP script

but the script continues to execute.

generates a warning **A** but continues

to run. Conversely, if **require()** fails, it

terminates the execution of the script **B**.

But what do these two functions do? Both

**include()** and **require()** incorporate

the referenced file into the main file

(for clarity’s sake, the file that has the

**include()** or **require()** line is the

**B** When a **require()** function call fails, warnings

including or parent file). The result is the

and errors are issued, and the script stops running.

same as if the included code were part of

the parent file in the first place.

Understanding that basic idea—including

a file makes it as if that file’s contents were

in the parent script to begin with—is key to

making the most out of this feature. This

means that any code within the included file

not within PHP tags is treated as HTML. And

this is true regardless of what extension the

included file has (because it’s the extension

of the including file that counts).

There are many reasons to use included files.

You could put your own defined functions

into a common file (see Chapter 10, “Creating

Functions,” for information on writing your

own functions). You might also want to place

your database access information into a

configuration file. First, however, let’s include

the template files created in the preceding

section of the chapter in order to make

pages abide by a consistent design.

192 Chapter

8

**Script 8.4** Once the two included files have been **To use external files:**

created, the **include()** function incorporates them

into the parent file to create the complete HTML

**1.** Create a new document in your text

page on the fly.

editor or IDE, to be named **index.php**.

1

<?php // Script 8.4 - index.php

**2.** Start with the initial PHP tags and add

2

/\* This is the home page for this site.

any comments (**Script 8.4**):

3

It uses templates to create the

layout.

\*/

**<?php // Script 8.4 - index.php**

4

**/\* This is the home page for**

5

// Include the header:

➝ **this site.**

**6 include('templates/header.html');**

**It uses templates to create the**

7

// Leave the PHP section to display lots

➝ **layout. \*/**

of HTML:

8 ?>

Notice that, with the template system,

9

the very first line of the script is the PHP

10

<h2>Welcome to a J.D. Salinger Fan Club</

tag. There’s no need to begin with the

h2>

initial HTML, because that is now stored

11

<p>Lorem ipsum dolor sit amet,

consectetur adipisicing elit, sed do

in the **header.html** file.

eiusmod tempor incididunt ut labore

**3.** Address error management, if necessary.

et dolore magna aliqua. Ut enim ad

minim veniam, quis nostrud exercitation

This topic is discussed in Chapter 3,

ullamco laboris nisi ut aliquip ex ea

“HTML Forms and PHP,” and may or

commodo consequat. Duis aute irure dolor

may not need to be addressed in your

in reprehenderit in voluptate velit esse

scripts. See that chapter for more;

cillum dolore eu fugiat nulla pariatur.

Excepteur sint occaecat cupidatat non

this will be the last time I specifically

proident, sunt in culpa qui officia

mention it in this chapter.

deserunt mollit anim id est laborum.</p>

**4.** Include the header file:

12 <h2>Another

Header</h2>

13

<p>Lorem ipsum dolor sit amet,

**include('templates/header.html');**

consectetur adipisicing elit, sed do

eiusmod tempor incididunt ut labore

To use the template system, you

et dolore magna aliqua. Ut enim ad

include the header file here by invoking

minim veniam, quis nostrud exercitation

the **include()** function. Because the

ullamco laboris nisi ut aliquip ex ea

header file contains only HTML, all of

commodo consequat. Duis aute irure dolor

its contents will be immediately sent to

in reprehenderit in voluptate velit esse

cillum dolore eu fugiat nulla pariatur.

the Web browser as if they were part of

Excepteur sint occaecat cupidatat non

this file. This line uses a relative path to

proident, sunt in culpa qui officia

refer to the included file (see the “File

deserunt mollit anim id est laborum.</p>

Navigation and Site Structure” sidebar)

14

and assumes that the file is stored in

15 <?php // Return to PHP.

**16 include('templates/footer.html');**

the **templates** directory.

**// Include the footer.**

continues on next page

17 ?>

Creating Web Applications 193

**5.** Close the PHP section and create the

page-specific content:

**File Navigation and Site Structure**

**?>**

To be able to use external files, you

**<h2>Welcome to a J.D. Salinger**

need to understand file navigation on

➝ **Fan Club</h2>**

your computer or server. Just as you

**<p>Lorem ipsum dolor sit**

must correctly refer to other pages in

HTML links or images in Web sites, you

➝ **amet...</p>**

must properly point a parent file to the

Because the bulk of this page is

included scripts. You can do this by

standard HTML, it’s easier to just exit

using absolute or relative paths. An

out of the PHP section and then add the

absolute path is a complete, specific

HTML (rather than using **print** to send

address, like the following:

it to the Web browser). Again, there’s

**include('C:\\inetpub\\wwwfiles\\**

more blather in the actual script than

➝ **file.php');**

I’ve included here.

**include('/Users/larry/Sites/**

➝ **file.php');**

**6.** Create another PHP section and require

the footer file:

As long as the included file isn’t moved,

an absolute path will always work.

**<?php**

**include('templates/footer.html');**

A relative path indicates where the

included file is in relation to the parent

**?>**

file. These examples assume both are

To finish the page, you need to include

within the same directory:

the footer file (which displays the footer

**include('file.php');**

and closes the HTML code). To do this,

**include('./file.php');**

you create a new section of PHP—you

The included file can also be in a

can have multiple sections of PHP code

directory below the parent one, as in this

within a script—and call the **include()**

chapter’s example (also see **C**):

function again.

**include('templates/header.html');**

**7.** Save the file as **index.php**.

Or, the included file could be in the

**8.** Create a folder called **templates** within

directory above the parent:

the main Web document directory on your

**include('../file.php');**

PHP-enabled computer or Web server.

Finally, a note on site structure: Once

To further separate the design elements

you divvy up your Web application

from the main content, the header and

into multiple pieces, you should begin

footer files go within their own directory.

thinking about arranging the files in

appropriate folders. Complex sites might

**9.** Place **header.html** and **footer.html**

have the main folder, another for images,

in the **templates** directory you just

one for administration files, and a special

created.

directory for templates and included

files. As long as you properly reference

the files in your **include()** or **require()**

statements, structuring your applications

will work fine and give the added benefit

of making them easier to maintain.

194 Chapter

8

![Image 219](index-216_1.png)

![Image 220](index-216_2.png)

![Image 221](index-216_3.png)

![Image 222](index-216_4.png)

![Image 223](index-216_5.png)

![Image 224](index-216_6.png)

![Image 225](index-216_7.png)

![Image 226](index-216_8.jpg)

**10.** Place **index.php** in the same directory

as the **templates** folder.

The relative locations on the computer

between the index page and the two

HTML pages must be correct in order

for the code to work.

**11.** Create a folder called **css** within the

main Web document directory on your

PHP-enabled computer or Web server.

The CSS script will need to go in this

directory.

**12.** Place the **1.css** script, available as part

**C** How the four files and two folders should be

organized on your PHP-enabled server.

of the book’s downloadable code, in

the **css** directory **C**.

Even though the header file includes

the CSS script, the reference to that

script must be relative to **index.php**.

It’s that page, after all, that will include

**header.html**.

**13.** Run **index.php** in your Web browser **D**.

The resulting page should look exactly

like the original layout (**C** in the

previous section of the chapter).

continues on next page

**D** This page has been dynamically generated using included files.

Creating Web Applications 195

**14.** View the page’s source code in your

**If a section of PHP only executes a single**

Web browser.

**command, it’s common to place both it and**

**the PHP tags on a single line:**

The source code should be exactly like

the source code of the **template.html**

**<?php include 'filename.html'; ?>**

script (Script 8.1), aside from the added

comments for the script names and

**If you see error messages like those**

**in A and B, the parent script can’t locate**

numbers.

**an included file. This problem is most likely**

**caused by a misspelled included filename or**

**All three files in this template system—**

**an error in the path (for example, using header.**

**header.html, footer.html, and index.**

**html instead of templates/header.html).**

**php—must use the same encoding in order**

**to avoid problems (see Chapter 1, “Getting**

**If the rendered Web page does not seem**

**Started with PHP,” for more on encoding).**

**to be reflecting the CSS styling, the HTML**

**Each file’s encoding must also match the**

**page can’t find the corresponding file. Make**

**encoding established in the HTML code.**

**sure you’ve stored the file in the proper folder,**

**with the correct name, and that the reference**

**The require() and include() func-**

**is correct relative to index.php.**

**tions can be used with or without parentheses:**

**A file’s extension is less important for**

**require 'filename.html';**

**included files because they aren’t intended**

**to be run directly. As a general rule of thumb,**

**You might sometimes use a variable that**

**you’ll be safe using .html for an included file**

**stores the name of the file to be included:**

**containing only or mostly HTML (in which case**

**the extension indicates it’s an HTML-related**

**require $filename;**

**file) and .php for included files containing only**

**or mostly PHP. Some programmers use an**

**.inc**

**Both include() and require() have**

**extension (for include), but security risks**

**variations: include\_once() and require\_**

**can arise with this practice. For that reason,**

**once(). Each is identical to its counterpart**

**use the .php extension for any file containing**

**except that it ensures that the same file can be**

**sensitive information (like database access**

**included only one time (in a parent script). You**

**parameters). And, of course, always use the**

**.php**

**should generally avoid using these, as they’ll**

**extension for any PHP script that will be**

**adversely affect the script’s performance.**

**executed directly.**

**Another good use of an external file is**

**to place your error settings code there so that**

**those changes are applied to every page in the**

**Web site.**

196 Chapter

8

![Image 227](index-218_1.png)

[**Using Constants**](#index_split_000.html#p8)

constants within single or double quotation

marks, like this **A**:

Many of PHP’s data types have already

**print "The cost is 468 CURRENCY";**

been discussed in this book: primarily

**print 'The cost is 468 CURRENCY';**

numbers, strings, and arrays. Constants

Instead, concatenation or multiple **print**

are another data type, but unlike variables,

statements are required:

their values cannot change.

**print 'The cost is 468 ' . CURRENCY;**

Whereas variables are assigned values

via the assignment operator (**\=**), constants

or

are assigned values using the **define()**

**print 'The cost is 468 ';**

function:

**print CURRENCY;**

**define(' *CONSTANT\_NAME*', *value*);** Along with the **define()** function for

Notice that—as a rule of thumb—constants

creating constants is the **defined()**

are named using all capital letters, although

function, which returns **TRUE** if the

doing so isn’t required. Most important,

submitted constant has been defined. It’s

constants don’t use the initial dollar sign

often used as the basis for a conditional:

as variables do (because constants are not

**if (defined('CONSTANT\_NAME')) { …**

variables). Here are two constants:

As an example of working with constants,

**define ('PI', 3.14);**

you’ll give the sample application the

**define ('CURRENCY', 'euros');**

ability to display a different title (which

As with any value, quote those that are

appears at the top of the browser window)

strings, not those that are numbers.

for each page. To accomplish this, you’ll

define a constant in the parent script that

Referring to constants is generally

will then be printed by the header file. This

straightforward:

technique works because any variables or

**print CURRENCY;**

constants that exist in the parent document

**number\_format(PI, 1);**

before the **include()** or **require()** call are

But using constants within quotation

available to the included file (it’s as if the

marks is more complicated. You can’t print

included file were part of the parent file).

**A** The value of a constant cannot be printed using

the constant’s name within quotation marks.

Creating Web Applications 197

**To use constants:**

**Script 8.5** This script uses the same template

system as **index.php** (Script 8.4) but also uses

**1.** Create a new PHP document in

a constant to identify the page's title.

your text editor or IDE, to be named

1

<?php // Script 8.5 - books.php

**books.php** (**Script 8.5**):

2

/\* This page lists J.D. Salinger's

**<?php // Script 8.5 - books.php**

bibliography. \*/

3

**2.** Define the page title as a constant:

4

// Set the page title and include the

**define ('TITLE', 'Books by J.D.**

header file:

**5**

**define ('TITLE', 'Books by J.D.**

➝ **Salinger');**

**Salinger');**

Here one constant is defined, named

6 include('templates/header.html');

**TITLE**, and given the value Books by

7

8

// Leave the PHP section to display lots

J.D. Salinger.

of HTML:

**3.** Include the header file:

9 ?>

10

**include('templates/header.html');**

11 <h2>J.D. Salinger's Books</h2>

This script uses the same header file

12 <ul>

13

<li>The Catcher in the Rye</li>

as all the others, although you’ll modify

14 <li>Nine

Stories</li>

that file shortly to take the constant

15

<li>Franny and Zooey</li>

into account.

16

<li>Raise High the Roof Beam,

Carpenters and Seymour: An

**4.** Close the PHP section and create

Introduction</li>

the HTML:

17 </ul>

**?>**

18

19 <?php

include('templates/footer.html');

**<h2>J.D. Salinger's Books</h2>**

?>

**<ul>**

**<li>The Catcher in the Rye</li>**

**<li>Nine**

**Stories</li>**

**<li>Franny and Zooey</li>**

**<li>Raise High the Roof Beam,**

 ➝ **Carpenters and Seymour: An**

 ➝ **Introduction</li>**

**</ul>**

The content here is simple but serves

the page’s purpose nicely.

**5.** Create a new PHP section that includes

the footer file:

**<?php include('templates/**

➝ **footer.html'); ?>**

As mentioned earlier in a tip, since the

remaining PHP code consists of just

198 Chapter

8

**Script 8.6** The **header.html** file is modified so one line it can all be written on a single

that it can set the page title value based on the

line, including the opening and closing

existence and value of a constant.

PHP tags. Just be certain to leave a

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

space between the executed code—the

1.1//EN" "http://www.w3.org/TR/xhtml11/

**include()**—and the tags.

DTD/xhtml11.dtd">

2

<html xmlns="http://www.w3.org/1999/

**6.** Save the file as **books.php**.

xhtml" xml:lang="en">

To take advantage of the constant, you

3 <head>

now need to modify the

4

<title> **<?php // Print the page**

**header.html** file.

**title.**

**5**

**if (defined('TITLE')) { // Is the**

**To print out a constant:**

**title**

**defined?**

**6 print**

**TITLE;**

**1.** Open **header.html** (Script 8.2) in your

**7**

**} else { // The title is not**

text editor or IDE.

**defined.**

**8**

**print 'Raise High the Roof**

**2.** Delete the Raise High the Roof Beam! A

**Beam! A J.D. Salinger Fan Club';**

J.D. Salinger Fan Club text that appears

**9 }**

between the **title** tags (line 4).

**10 ?>** </title>

11

<meta http-equiv="content-type"

Now that the page title will be determined

content="text/html; charset=utf-8" />

on a page-by-page basis, you don’t need

12

<link rel="stylesheet"

it to be hard-coded into the page.

href="css/1.css" type="text/css"

media="screen,projection" />

**3.** In the place of the deleted text

13 </head>

(between the **title** tags), add the

14 <body>

following (**Script 8.6**):

15 <div

id="wrapper">

16

**<?php**

17 <div

id="header">

**if (defined('TITLE')) {**

18

<p class="description">A J.D.

**print**

**TITLE;**

Salinger Fan Club</p>

19

<h1><a href="index.php">Raise High

**} else {**

the Roof Beam!</a></h1>

**print 'Raise High the Roof**

20 <ul

id="nav">

 ➝ **Beam! A J.D. Salinger Fan**

21

<li><a href="books.php">Books

 ➝ **Club';**

</a></li>

22 <li><a

href="#">Stories</a></li>

**}**

23 <li><a

href="#">Quotes</a></li>

**?>**

24

<li><a href="login.php">Login

To have PHP create the page title, you

</a></li>

25

<li><a href="register.php">

need to begin by starting a section of

Register</a></li>

PHP code between the **title** tags. Then

26 </ul>

you use a conditional to see if the **TITLE**

27 </div><!-- header -->

constant has been defined. If it has, print

28

its value as the page title. If **TITLE** hasn’t

29 <div

id="sidebar">

30 <h2>Favorite

Quotes</h2>

been defined, print a default title.

31

<p class="news">I don't exactly

**4.** Save the file as **header.html**.

know what I mean by that,

but I mean it.<br />- <em>The

continues on next page

Catcher in the Rye</em></p>

code continues on next page

Creating Web Applications 199

![Image 228](index-221_1.png)

![Image 229](index-221_2.png)

**5.** Upload **books.php** and **header.html**

**Script 8.6** continued

to your PHP-enabled server. The new

32

<p class="news">I privately say

PHP script, **books.php**, should go in

to you, old friend... please

the same directory as **index.php**;

accept from me this unpretentious

**header.html** should replace the previ-

bouquet of early-blooming

ous version, in the same directory—

parentheses: (((()))).<br />-

**templates**

<em>Raise High the Roof Beam,

—as **footer.html**.

Carpenters and Seymour: An

**6.** Run **books.php** in your Web browser **B**.

Introduction</em></p>

33 </div><!--

sidebar

\-->

**7.** View **index.php** (the home page) in

34

your Web browser **C**.

35 <div

id="content">

36

<!-- BEGIN CHANGEABLE CONTENT. -->

**8.** If you want, add the constant definition

37

<!-- Script 8.6 - header.html -->

line to **index.php** to change its title.

**The formal rules for naming constants**

**are exactly like those for variables except**

**for the omission of a dollar sign. Constant**

**names must begin with a letter; can contain**

**any combination of letters, numbers, and the**

**underscore; and are case-sensitive.**

**PHP runs with several predefined**

**constants. These include PHP\_VERSION**

**(the version of PHP running) and PHP\_OS**

**(the operating system of the server).**

**In Chapter 9, “Cookies and Sessions,”**

**you’ll learn about another constant, SID**

**(which stands for session ID).**

**An added benefit of using constants is**

**that they’re global in scope. This concept will**

**mean more to you after you read the section**

**B** The books page uses a PHP constant to create

**“Understanding Variable Scope” in Chapter 10.**

its title.

**Not only can the value of a constant**

**never be changed, a constant can’t be deleted**

**(unset, technically). Also, unlike arrays, a con-**

**stant can only ever contain a single value, like**

**a string or a number.**

**C** Because the index page didn’t have a **TITLE**

constant defined in it, the default page title is used

(thanks to the conditional in Script 8.6).

200 Chapter

8

[**Working with the**](#index_split_000.html#p8)

how useful that can be! The basic usage of

the **date()** function is just

[**Date and Time**](#index_split_000.html#p8)

**date(' *formatting*');**

PHP has a few functions for working with

A long list of possible options is available

the date and time, the most important

for formatting, as indicated in **Table 8.1**

of which is **date()**. The only thing the

(the PHP manual lists a few more). These

**date()** function does is return date and

parameters can also be combined—for

time information in a format based on the

example, **date('l F j, Y')** returns

arguments it’s fed, but you’d be surprised

Wednesday January 26, 2011.

**TABLE 8.1 Date( ) Function Formatting**

**Character**

**Meaning**

**Example**

Y

Year as 4 digits

2011

y

Year as 2 digits

11

L

Is it a leap year?

1 (for yes)

n

Month as 1 or 2 digits

2

m

Month as 2 digits

02

F

Month

February

M

Month as 3 letters

Feb

j

Day of the month as 1 or 2 digits

8

d

Day of the month as 2 digits

08

l (lowercase L)

Day of the week

Monday

D

Day of the week as 3 letters

Mon

w

Day of the week as a single digit

0 (Sunday)

z

Day of the year: 0 to 365

189

t

Number of days in the month

31

S

English ordinal suffix for a day, as 2 characters

rd

g

Hour; 12-hour format as 1 or 2 digits

6

G

Hour; 24-hour format as 1 or 2 digits

18

h

Hour; 12-hour format as 2 digits

06

H

Hour; 24-hour format as 2 digits

18

i

Minutes

45

s

Seconds

18

u

Microseconds

1234

a

am or pm

am

A

AM or PM

PM

U

Seconds since the epoch

1048623008

e

Timezone

UTC

I (capital i)

Is it daylight savings?

1 (for yes)

O

Difference from GMT

+0600

Creating Web Applications 201

![Image 230](index-223_1.png)

![Image 231](index-223_2.png)

The **date()** function can take a second

argument called a timestamp. A timestamp

is a number representing how many

seconds have passed since midnight on

January 1, 1970—a moment referred to as

the epoch. The **time()** function returns

the timestamp for the current moment. The

**mktime()** function can return a timestamp

for a particular time and date:

**mktime( *hour*, *minute*, *second*, *month*,** **A** As of PHP 5.1, notices will be generated when a

➝ ***day*****, *year*);**

date or time function is used without the time zone

being set.

So the code

**$ts = mktime(12, 30, 0, 11, 5, 2011);**

assigns to **$ts** the number of seconds

from the epoch to 12:30 on November 5,

2011\. That number can then be fed into the

**date()** function like so:

**date('D', $ts);**

This returns Sat, which is the three-letter

format for that day of the week.

As of PHP 5.1, you should establish the

**B** The Web site now displays

server’s time zone prior to calling any date-

the date and time in the sidebar,

or time-related function. To do so, use

thanks to the **date()** function.

**date\_default\_timezone\_set( *timezone*);**

**Script 8.7** The altered **header.html** file uses the

The timezone value is a string like

**date()** function to print the current date and time.

America/New\_York or Pacific/Auckland.

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

There are too many to list here (Africa

1.1//EN"

"http://www.w3.org/TR/xhtml11/

alone has over 50), but see the PHP

DTD/xhtml11.dtd">

manual for them all. If you don’t take this

2 <html

xmlns="http://www.w3.org/1999/

step, you might see errors **A**.

xhtml"

xml:lang="en">

3 <head>

To demonstrate the **date()** function, let’s

4

<title><?php // Print the page title.

update the header file so that it shows the

5

if (defined('TITLE')) { // Is the title

current date and time in the sidebar **B**.

defined?

6 print

TITLE;

7

} else { // The title is not defined.

**To use date():**

8

print 'Raise High the Roof Beam!

**1.** Open **header.html** (Script 8.6) in your

A J.D. Salinger Fan Club';

9 }

text editor or IDE.

10 ?></title>

**2.** Before the closing **sidebar** **</div>** tag, 11

<meta http-equiv="content-type"

add the following (**Script 8.7**):

content="text/html; charset=utf-8" />

**<p><?php**

code continues on next page

202 Chapter

8

**Script 8.7** continued

The initial HTML paragraph tag will

wrap the date and time. Then open a

12

<link rel="stylesheet"

PHP section so that you can call the

href="css/1.css" type="text/css"

media="screen,projection" />

**date()** function.

13 </head>

**3.** Establish the time zone:

14 <body>

15 <div

id="wrapper">

**date\_default\_timezone\_set**

16

➝ **('America/New\_York');**

17 <div

id="header">

18

<p class="description">A J.D.

Before calling **date()**, the time zone has

Salinger Fan Club</p>

to be set. To [find yours, see www.php.](http://www.php.net/timezones)

19

<h1><a href="index.php">Raise High

[net / timezones.](http://www.php.net/timezones)

the Roof Beam!</a></h1>

20 <ul

id="nav">

**4.** Use the **date()** function to print out the

21

<li><a href="books.php">

current date and time:

Books</a></li>

22 <li><a

href="#">Stories</a></li>

**print date('g:i a l F j');**

23 <li><a

href="#">Quotes</a></li>

Using the formatting parameters from

24 <li><a

href="login.php">

Table 8.1, the

Login</a></li>

**date()** function will return a

25

<li><a href="register.php">

value like 4:15 pm Tuesday February 22.

Register</a></li>

This value will immediately be printed.

26 </ul>

27 </div><!-- header -->

**5.** Close the PHP section and finish the

28

HTML code:

29 <div

id="sidebar">

**?></p>**

30 <h2>Favorite

Quotes</h2>

31

<p class="news">I don't exactly

**6.** Save the file as **header.html**, place it in

know what I mean by that,

the **templates** directory of your PHP-

but I mean it.<br />- <em>The

Catcher in the Rye</em></p>

enabled server, and test it in your Web

32

<p class="news">I privately say

browser **B**.

to you, old friend... please

accept from me this unpretentious

bouquet of early-blooming

**Because PHP is a server-side technology,**

parentheses: (((()))).<br />-

**these functions reflect the date and time on**

<em>Raise High the Roof Beam,

**the server. To get the time on the client (in**

Carpenters and Seymour: An

**other words, on the computer where the Web**

Introduction</em></p>

**browser viewing the page is located), you**

33

<p><?php // Print the current

**must use JavaScript.**

date and time...

34 //

Set

the

timezone:

**The server’s time zone can also be set**

**35 date\_default\_timezone\_set**

**in the PHP configuration file (see Appendix A,**

**('America/New\_York');**

**“Installation and Configuration”). Establishing**

36

**the time zone there is generally a better idea**

37

// Now print the date and time:

**than doing so on a script-by-script basis.**

**38**

**print date('g:i a l F j');**

39

?></p>

**Added to PHP 5.3 are new ways to**

40 </div><!-- sidebar -->

**create and manipulate dates and times using**

41

**the DateTime class. While useful, this new**

42 <div

id="content">

**tool requires familiarity with object-oriented**

43

<!-- BEGIN CHANGEABLE CONTENT. -->

**programming, therefore making it beyond the**

44

<!-- Script 8.7 - header.html -->

**scope of this beginner’s book.**

Creating Web Applications 203

![Image 232](index-225_1.png)

![Image 233](index-225_2.png)

![Image 234](index-225_3.png)

![Image 235](index-225_4.png)

![Image 236](index-225_5.png)

![Image 237](index-225_6.png)

![Image 238](index-225_7.png)

![Image 239](index-225_8.png)

![Image 240](index-225_9.png)

![Image 241](index-225_10.png)

![Image 242](index-225_11.png)

![Image 243](index-225_12.png)

![Image 244](index-225_13.png)

![Image 245](index-225_14.png)

![Image 246](index-225_15.png)

![Image 247](index-225_16.png)

![Image 248](index-225_17.png)

![Image 249](index-225_18.png)

![Image 250](index-225_19.png)

![Image 251](index-225_20.png)

![Image 252](index-225_21.png)

![Image 253](index-225_22.png)

![Image 254](index-225_23.png)

![Image 255](index-225_24.png)

![Image 256](index-225_25.png)

![Image 257](index-225_26.jpg)

![Image 258](index-225_27.png)

![Image 259](index-225_28.png)

![Image 260](index-225_29.png)

![Image 261](index-225_30.png)

![Image 262](index-225_31.png)

![Image 263](index-225_32.png)

![Image 264](index-225_33.png)

![Image 265](index-225_34.png)

![Image 266](index-225_35.png)

![Image 267](index-225_36.png)

![Image 268](index-225_37.png)

![Image 269](index-225_38.jpg)

[**Handling HTML Forms**](#index_split_000.html#p8)

[**with PHP, Revisited**](#index_split_000.html#p8)

All the examples in this book so far have

used two separate scripts for handling HTML

forms: one that displayed the form and

another that received and processed the

form’s data. There’s certainly nothing wrong

with this method, but there are advantages

to coding the entire process in one script. To

make a page both display and handle a form,

use a conditional **A**:

**if (/\* form has been submitted \*/) {**

**// Handle the form.**

**} else {**

**// Display the form.**

**A** This flowchart represents how the same PHP

**}**

script can both display and handle an HTML form.

There are many ways to determine if a

form has been submitted. One option is to

check whether any of the form’s variables

are set:

**if (isset($\_POST\[' *something*'\])) { …**

However, if the user submitted the form

without completing it, that variable may not

be set (depending on the corresponding

form element type). A more reliable

solution I’ve used in the past is to add a

hidden input to a form so that it can be

checked:

**<input type="hidden"**

➝ **name="submitted" value="true" />**

Again, the only purpose of this hidden

input is to reliably indicate that the form

has been submitted, even if the user did

nothing to complete the form. To check for

that, the handling PHP code would use this

conditional:

**if (isset($\_POST\['submitted'\])) { …**

204 Chapter

8

![Image 270](index-226_1.png)

![Image 271](index-226_2.png)

![Image 272](index-226_3.png)

![Image 273](index-226_4.png)

![Image 274](index-226_5.png)

![Image 275](index-226_6.png)

![Image 276](index-226_7.png)

![Image 277](index-226_8.png)

![Image 278](index-226_9.png)

![Image 279](index-226_10.png)

![Image 280](index-226_11.png)

![Image 281](index-226_12.png)

![Image 282](index-226_13.png)

![Image 283](index-226_14.png)

![Image 284](index-226_15.png)

![Image 285](index-226_16.png)

![Image 286](index-226_17.png)

![Image 287](index-226_18.png)

![Image 288](index-226_19.png)

![Image 289](index-226_20.png)

![Image 290](index-226_21.png)

![Image 291](index-226_22.png)

![Image 292](index-226_23.png)

![Image 293](index-226_24.png)

![Image 294](index-226_25.png)

![Image 295](index-226_26.jpg)

![Image 296](index-226_27.png)

![Image 297](index-226_28.png)

![Image 298](index-226_29.png)

![Image 299](index-226_30.png)

![Image 300](index-226_31.png)

![Image 301](index-226_32.png)

![Image 302](index-226_33.png)

![Image 303](index-226_34.png)

![Image 304](index-226_35.png)

![Image 305](index-226_36.png)

![Image 306](index-226_37.png)

![Image 307](index-226_38.jpg)

Another way of checking for a form’s

submission is to examine how the page

was accessed. When you have a form

that will be submitted back to the same

page, two different types of requests

will be made of that script **B**. The first

request, which loads the form, will be a

GET request. This is the standard request

made of most Web pages. When the form

is submitted, and its **action** attribute points

to the same page, a second request of

the script will be made, this time a POST

request (assuming the form uses the POST

method). With this in mind, you can test

for a form’s submission by checking the

request type, found in the **$\_SERVER** array:

**if ($\_SERVER\['REQUEST\_METHOD'\] ==**

➝ **'POST') { …**

As an example of this, you’ll create the

basics of a login form.

**B** When the same PHP script both displays and handles an HTML form, the script will be requested using two different methods.

Creating Web Applications 205

**To use one page to display**

**Script 8.8** The login page serves two purposes: It

displays the login form and handles its submission.

**and handle a form:**

1

<?php // Script 8.8 - login.php

**1.** Begin a new PHP document in your text

2

/\* This page lets people log into the

editor or IDE, to be named **login.php**

site (in theory). \*/

(**Script 8.8**):

3

**<?php // Script 8.8 - login.php**

4

// Set the page title and include the

header file:

**2.** Define the page title as a constant and

5 define('TITLE',

'Login');

include the header file:

6 include('templates/header.html');

7

**define('TITLE', 'Login');**

8

// Print some introductory text:

**include('templates/header.html');**

9

print '<h2>Login Form</h2>

10

<p>Users who are logged in can take

Using the constant system developed

advantage of certain features like

earlier in the chapter, give this page its

this, that, and the other thing.</p>';

own unique page title.

11

12 // Check if the form has been submitted:

**3.** Add some introductory text:

**13 if ($\_SERVER\['REQUEST\_METHOD'\] ==**

**print '<h2>Login Form</h2>**

**'POST')**

**{**

14

**<p>Users who are logged in can**

15

// Handle the form:

 ➝ **take advantage of certain**

**16**

**if ( (!empty($\_POST\['email'\])) &&**

 ➝ **features like this, that, and**

**(!empty($\_POST\['password'\])) ) {**

 ➝ **the other thing.</p>';**

17

**18 if**

**(**

**(strtolower($\_POST**

This text, which appears outside of the

**\['email'\]) == 'me@example.com')**

main conditional, will always show in

**&& ($\_POST\['password'\] ==**

the Web browser, whether the form is

**'testpass') ) { // Correct!**

being displayed or has been submitted.

19

**20**

**print '<p>You are logged**

Because the core of this script revolves

**in!<br />Now you can blah,**

around a PHP conditional, it’s arguably

**blah,**

**blah...</p>';**

clearer to print out HTML from PHP

21

rather than exit out of the PHP code as

**22**

**} else { // Incorrect!**

you did in the previous two examples

23

**24**

**print '<p>The submitted**

(**index.php** and **books.php**).

**email address and password**

**4.** Begin the conditional to check whether

**do not match those on**

the form has been submitted:

**file!<br />Go back and try**

**again.</p>';**

**if ($\_SERVER\['REQUEST\_METHOD'\] ==**

25

➝ **'POST') {**

**26 }**

27

To test whether the form has been

**28**

**} else { // Forgot a field.**

submitted, check whether **$\_SERVER**

29

**\['REQUEST\_METHOD'\]** equals ***POST***

**30**

**print '<p>Please make sure you**

(case-sensitive).

**enter both an email address**

**and a password!<br />Go back**

**and try again.</p>';**

31

code continues on next page

206 Chapter

8

**Script 8.8** continued

**5.** Create a nested pair of conditionals to

process the form data:

**32 }**

33

**if ( (!empty($\_POST\['email'\])) &&**

**34 } else { // Display the form.**

➝ **(!empty($\_POST\['password'\])) ) {**

35

**if ( (strtolower($\_POST\['email'\])**

**36**

**print '<form action="login.php"**

 ➝ **\== 'me@example.com') &&**

**method="post">**

**37**

**<p>Email Address: <input**

 ➝ **($\_POST\['password'\] ==**

**type="text"**

**name="email"**

 ➝ **'testpass') ) {**

**size="20"**

**/></p>**

**print '<p>You are logged**

**38**

**<p>Password: <input**

 ➝ **in!<br />Now you can blah,**

**type="password"**

**name="password"**

 ➝ **blah, blah...</p>';**

**size="20"**

**/></p>**

**39**

**<p><input type="submit" name=**

**} else { // Incorrect!**

**"submit" value="Log In!" /></p>**

**print '<p>The submitted email**

**40 </form>';**

 ➝ **address and password do not**

41

 ➝ **match those on file!<br />**

**42 }**

 ➝ **Go back and try again.</p>';**

43

44 include('templates/footer.html');

**}**

// Need the footer.

**} else {**

45 ?>

**print '<p>Please make sure you**

 ➝ **enter both an email address**

 ➝ **and a password!<br />Go back**

 ➝ **and try again.</p>';**

**}**

These conditionals handle the form data.

The first conditional checks that both the

email address and password variables

have values. If they don’t, a message is

displayed (Please make sure…). Within

that first conditional, another conditional

checks whether the email address

is equal to ***me@example.com*** and the

password is equal to ***testpass***. If so,

let’s say the user is logged in (it would

be too advanced at this juncture to

store and retrieve user information to

create a real login system). Otherwise,

a message indicates that the wrong

values were entered.

continues on next page

Creating Web Applications 207

![Image 308](index-229_1.png)

Be certain to use the equals operator (**\==**)

here and not the assignment operator

(**\=**) in this conditional, which is a common

mistake. Also, in case the user enters

their address as Me@example.com, or

any other capitalized permutation, the

**strtolower()** function is first applied

to the email address, prior to checking

for equality.

**6.** Complete the main conditional:

**C** This simple login page takes an email address

**} else { // Display the form.**

and a password.

**print '<form action="login.php"**

 ➝ **method="post">**

**<p>Email Address: <input**

 ➝ **type="text" name="email"**

 ➝ **size="20" /></p>**

**<p>Password: <input type=**

 ➝ **"password" name="password"**

 ➝ **size="20" /></p>**

**<p><input type="submit" name=**

 ➝ **"submit" value="Log In!" /></p>**

**</form>';**

**}**

This concludes the main conditional,

which checks whether the form has

been submitted. If it hasn’t been, then

the form is displayed. The form itself is

very simple **C**.

To clarify a point of possible confusion,

even though the form’s **method** attribute

has a value of post (all lowercase), to

check for the form’s submission, the

request method value is still POST

(all uppercase).

208 Chapter

8

![Image 309](index-230_1.png)

![Image 310](index-230_2.png)

![Image 311](index-230_3.png)

**7.** Require the footer file and complete the

PHP page:

**include('templates/footer.html');**

**?>**

**8.** Save the file as **login.php**, place it in

the same directory as **index.php**, and

test it in your Web browser **D**, **E**, and **F**.

**D** Upon successfully logging in, the user sees

this message.

**In the real world, you would add some**

**CSS formatting to the error messages so that**

**they stand out. The next section of the chapter**

**will include this feature.**

**This trick of checking for the presence**

**of a hidden input can be confusing. It works**

**because the same script—login.php—will be**

**accessed twice by the user. The first time the**

**form will not have been submitted, so a condi-**

**E** Failure to submit either an email address or

**tional checking if $\_POST\['submitted'\] is set**

a password results in this message.

**will be FALSE and the form will be displayed.**

**Then the page will be accessed again after the**

**user clicks submit, at which point the condi-**

**tional becomes TRUE.**

**If you want a page to handle a form**

**and then immediately display the form again,**

**use this:**

**if ($\_SERVER\['REQUEST\_METHOD'\] ==**

➝ **'POST') {**

**F** If either the email address or the password

**// Handle the form.**

doesn’t match that in the script, the user sees this

error message.

**}**

**// Display the form.**

Creating Web Applications 209

![Image 312](index-231_1.png)

![Image 313](index-231_2.png)

[**Making Forms Sticky**](#index_split_000.html#p8)

A sticky form remembers values entered into

it. A common example is a search engine,

which often displays your terms in the

search box, even when showing the results

of the search. You might also want to use

sticky forms on occasions where the user

failed to complete a form accurately and

therefore must resubmit it **A**.

From a technological standpoint, sticky forms

work by having their form element values

predetermined. You can make this happen

by setting the **value** attribute of text inputs:

**<input type="text" name="first\_name"**

**A** Creating sticky forms makes it easier for users to

➝ **value="Stephanie" />**

correct omissions in incomplete form submissions.

To have PHP preset that value, print

the appropriate variable between the

quotation marks:

**<input type="text" name="first\_name"**

➝ **value="<?php print $\_POST**

➝ **\['first\_name'\]; ?>" />**

The first time the form is run, the PHP code

prints nothing (because the variable has no

value). If the form is displayed again after

submission, values that the user originally

entered in the form input will be displayed

there automatically. That’s the basic idea,

but a more professional implementation

would address two things…

**B** The HTML source of the page shows the PHP error caused by referring to a variable that does not exist.

210 Chapter

8

![Image 314](index-232_1.png)

First, it’s best not to refer to variables that

don’t exist. Doing so creates PHP warnings,

and with the PHP code buried in a form

element’s attribute, the warning itself will

only be fully visible in the HTML source

code **B**. To avoid that, check that the

variable is set before printing it:

**<input type="text" name="first\_name"**

➝ **value="<?php if (isset($\_POST**

➝ **\['first\_name'\]) { print $\_POST**

➝ **\['first\_name'\]; } ?>" />**

Second, certain characters that could be

in a submitted value will cause problems

if printed as a form element’s value.

To prevent such problems, apply the

**C** The registration form as the user first sees it.

**htmlspecialchars()** function (discussed

in Chapter 5, “Using Strings”). With this in

mind, a longer but better version of this

code is as follows:

**<input type="text" name="first\_name"**

➝ **value="<?php if (isset($\_POST**

➝ **\['first\_name'\]) { print**

➝ **htmlspecialchars($\_POST\['first\_**

➝ **name'\]); } ?>" />**

To demonstrate, you’ll create the shell of a

registration form **C**.

Creating Web Applications 211

**To make a sticky form:**

**Script 8.9** The registration form uses a so-called

sticky feature so that it recalls the values previously

**1.** Create a new PHP script in your text

entered into it

editor or IDE, to be named **register.**

1

<?php // Script 8.9 - register.php

**php** (**Script 8.9**):

2

/\* This page lets people register for

**<?php // Script 8.9 - register.php**

the site (in theory). \*/

3

**2.** Set the page title and include the HTML

4

// Set the page title and include the

header:

header file:

**define('TITLE', 'Register');**

5 define('TITLE',

'Register');

6 include('templates/header.html');

**include('templates/header.html');**

7

**3.** Add some introductory text and define

8

// Print some introductory text:

a CSS class:

9

print '<h2>Registration Form</h2>

10

<p>Register so that you can take

**print '<h2>Registration Form</h2>**

advantage of certain features like

**<p>Register so that you can**

this, that, and the other thing.</p>';

 ➝ **take advantage of certain**

11

12 // Add the CSS:

 ➝ **features like this, that, and**

13

print '<style type="text/css"

 ➝ **the other thing.</p>';**

media="screen">

**print '<style type="text/css"**

14

.error { color: red; }

➝ **media="screen">**

15 </style>';

**.error { color: red; }**

16

**</style>';**

17 // Check if the form has been submitted:

18 if ($\_SERVER\['REQUEST\_METHOD'\] == 'POST') {

So that the error messages, generated

19

by improperly completing the registration

20

$problem = FALSE; // No problems

form, stand out, a CSS class is defined

so far.

21

that colors the applicable text in red.

22

// Check for each value...

Although CSS is normally defined in the

23

if (empty($\_POST\['first\_name'\])) {

page’s head, you can put it anywhere.

24 $problem

\=

TRUE;

**4.** Check whether the form has been

25

print '<p class="error">Please

enter your first name!</p>';

submitted:

26 }

**if ($\_SERVER\['REQUEST\_METHOD'\] ==**

27

➝ **'POST') {**

28

if (empty($\_POST\['last\_name'\])) {

29 $problem

\=

TRUE;

Like the login page, this one script both

30

print '<p class="error">Please

displays and handles the registration

enter your last name!</p>';

form. To check if the form has been

31 }

submitted, the same code previously

32

33

if (empty($\_POST\['email'\])) {

explained is used here.

34 $problem

\=

TRUE;

35

print '<p class="error">Please

enter your email address!</p>';

36 }

37

38

if (empty($\_POST\['password1'\])) {

code continues on next page

212 Chapter

8

**Script 8.9** continued

**5.** Create a flag variable:

39 $problem

\=

TRUE;

**$problem = FALSE;**

40

print '<p class="error">Please

The **$problem** variable will be used to

enter a password!</p>';

indicate whether a problem occurred.

41 }

42

Specifically, you want to make sure that

43

if ($\_POST\['password1'\] != $\_POST

every form input has been filled out

\['password2'\]) {

before you formally register the user.

44 $problem

\=

TRUE;

Initially, this variable is set to **FALSE**,

45

print '<p class="error">Your

password did not match your

because no problems have occurred.

confirmed password!</p>';

This is the same approach used in

46 }

Chapter 6, “Control Structures.”

47

48

if (!$problem) { // If there weren't

**6.** Check that a first name was entered:

any problems...

49

**if (empty($\_POST\['first\_name'\])) {**

50

// Print a message:

**$problem = TRUE;**

51

print '<p>You are now registered!

**print '<p class="error">Please**

<br />Okay, you are not really

 ➝ **enter your first name!</p>';**

registered but...</p>';

52

**}**

53

// Clear the posted values:

As a simple test to determine whether

54 $\_POST

\=

array();

55

the user has entered a first name value,

56

} else { // Forgot a field.

check that the variable isn’t empty. (This

57

technique was first discussed in Chapter

58

print '<p class="error">Please try

6.) If the variable is empty, then indicate

again!</p>';

a problem by setting that variable to

59

60 }

**TRUE** and print an error message. The

61

error message has a class type of ***error***,

62 } // End of handle form IF.

so that the CSS formatting is applied.

63

64 // Create the form:

**7.** Repeat the validation for the last name

65 ?>

and email address:

66

<form action="register.php"

method="post">

**if (empty($\_POST\['last\_name'\])) {**

67

**$problem = TRUE;**

**68**

**<p>First Name: <input type="text"**

**print '<p class="error">Please**

**name="first\_name" size="20"**

 ➝ **enter your last name!</p>';**

**value="<?php if (isset($\_POST**

**\['first\_name'\])) { print**

**}**

**htmlspecialchars($\_POST\['first\_**

**if (empty($\_POST\['email'\])) {**

**name'\]); } ?>" /></p>**

**$problem = TRUE;**

69

**print '<p class="error">Please**

**70**

**<p>Last Name: <input type="text"**

**name="last\_name" size="20"**

 ➝ **enter your email address!</p>';**

**value="<?php if (isset($\_POST**

**}**

**\['last\_name'\])) { print**

Both of these checks are variations on

**htmlspecialchars($\_POST\['last\_**

**name'\]); } ?>" /></p>**

the username validation routine.

continues on next page

code continues on next page

Creating Web Applications 213

**8.** Validate the passwords:

**Script 8.9** continued

**if (empty($\_POST\['password1'\])) {**

71

**$problem = TRUE;**

**72**

**<p>Email Address: <input**

**print '<p class="error">Please**

**type="text"**

**name="email"**

**size="20" value="<?php if**

➝ **enter a password!</p>';**

**(isset($\_POST\['email'\])) { print**

**}**

**htmlspecialchars($\_POST\['email'\]);**

**if ($\_POST\['password1'\] != $\_POST**

**} ?>" /></p>**

➝ **\['password2'\]) {**

73

**$problem = TRUE;**

**74**

**<p>Password: <input**

**print '<p class="error">Your**

**type="password"**

**name="password1"**

**size="20" value="<?php if**

 ➝ **password did not match your**

**(isset($\_POST\['password1'\]))**

 ➝ **confirmed password!</p>';**

**{ print htmlspecialchars($\_POST**

**}**

**\['password1'\]); } ?>" /></p>**

**75**

**<p>Confirm Password: <input**

The password validation requires two

**type="password"**

**name="password2"**

conditionals. The first checks whether

**size="20" value="<?php if**

the **$\_POST\['password1'\]** variable is

**(isset($\_POST\['password2'\]))**

empty. The second checks whether

**{ print htmlspecialchars($\_POST**

**\['password2'\]); } ?>" /></p>**

the **$\_POST\['password1'\]** variable isn’t

76

equal to the **$\_POST\['password2'\]**

77

<p><input type="submit" name="submit"

variable. You don’t need to see if

value="Register!" /></p>

**$\_POST\['password2'\]** is empty because

78

if it is and **$\_POST\['password1'\]** isn’t,

79 </form>

80

the second conditional will catch that

81 <?php include('templates/footer.html');

problem. If **$\_POST\['password1'\]** and

// Need the footer. ?>

**$\_POST\['password2'\]** are both empty, the

first conditional will catch the mistake.

**9.** Check whether a problem occurred:

**if (!$problem) {**

**print '<p>You are now**

 ➝ **registered!<br />Okay,**

 ➝ **you are not really registered**

 ➝ **but...</p>';**

**$\_POST = array();**

If there were no problems, the

**$problem** variable is still **FALSE**, and

the initial condition here is **TRUE** (the

condition is that **$problem** has a value

of **FALSE**). In that case, the registration

process would take place. The formal

registration process, where the data is

stored in a file or database, has not yet

been developed, so a simple message

appears in its stead here.

214 Chapter

8

Next, the **$\_POST** variable is assigned the Note that if the user filled out the form

value of **array()**. This line has the effect

properly, the entire **$\_POST** array will

of wiping out the contents of the **$\_POST**

have been reset, making this PHP

variable (i.e., resetting it as an empty

conditional false.

array). This step is taken only upon a

**13.** Repeat the process for the last name

successful (theoretical) registration so

and email address:

that the values are not redisplayed in

**<p>Last Name: <input type="text"**

the registration form (e.g., see Step 12).

➝ **name="last\_name" size="20"**

**10.** Complete the conditionals:

➝ **value="<?php if (isset($\_POST**

**} else { // Forgot a field.**

➝ **\['last\_name'\])) { print**

**print '<p class="error">**

➝ **htmlspecialchars($\_POST**

 ➝ **Please try again!</p>';**

➝ **\['last\_name'\]); } ?>" /></p>**

**}**

**<p>Email Address: <input**

**} // End of handle form IF.**

➝ **type="text" name="email"**

➝ **size="20" value="<?php if**

The **else** clause applies if a problem

➝ **(isset($\_POST\['email'\])) { print**

occurred, in which case the user is

➝ **htmlspecialchars($\_POST**

asked to complete the form again.

➝ **\['email'\]); } ?>" /></p>**

**11.** Begin the HTML form:

These are variations on Step 12, switching

**?>**

the variable names as appropriate.

**<form action="register.php"**

**14.** Add the rest of the form:

➝ **method="post">**

Unlike the login example, this page always

**<p>Password: <input type=**

displays the form. Therefore, the form

 ➝ **"password" name="password1"**

isn’t part of any conditional. Also, because

 ➝ **size="20" value="<?php if**

there’s a lot of HTML to be generated, it’ll

➝ **(isset($\_POST\['password1'\]))**

be easier to leave the PHP section of the

➝ **{ print htmlspecialchars**

page and just output the HTML directly.

➝ **($\_POST\['password1'\]); } ?>" /></p>**

**<p>Confirm Password: <input**

**12.** Create the sticky first name input:

 ➝ **type="password" name="password2"**

**<p>First Name: <input type="text"**

 ➝ **size="20" value="<?php if**

➝ **name="first\_name" size="20"**

 ➝ **(isset($\_POST\['password2'\]))**

➝ **value="<?php if (isset($\_POST**

 ➝ **{ print htmlspecialchars**

➝ **\['first\_name'\])) { print**

 ➝ **($\_POST\['password2'\]); }**

➝ **htmlspecialchars($\_POST**

 ➝ **?>" /></p>**

➝ **\['first\_name'\]); } ?>" /></p>**

**<p><input type="submit" name=**

To make the first name input sticky, preset

➝ **"submit" value="Register!" /></p>** its **value** attribute by printing out the

**</form>**

**$\_POST\['first\_name'\]** variable, but only

It used to be the case that you couldn’t

if it’s set. The conditional is therefore put

preset a value for a password input,

within PHP tags within the HTML’s **value**

but some browsers now support this

section of the form element. As already

feature. Then there is the submit button

mentioned, the **htmlspecialchars()**

and the closing **form** tag.

function is used to handle any potentially

continues on next page

problematic characters.

Creating Web Applications 215

![Image 315](index-237_1.png)

![Image 316](index-237_2.jpg)

**15.** Complete the PHP page:

**<?php include('templates/**

➝ **footer.html'); ?>**

The last step is to include the HTML footer.

**16.** Save the file as **register.php**, place it

in the proper directory on your PHP-

enabled server, and test it in your Web

browser **D** and **E**.

**According to (X)HTML rules, you must**

**quote all attributes in form inputs. Specifically,**

**you should use double quotation marks. If you**

**don’t quote your values, any spaces in them**

**mark the end of the value (for example, *Larry***

***Ullman*** **will display as just Larry in the form**

**input). Although quoting attributes will not be**

**a requirement of HTML5, I still recommend**

**doing so.**

**To preset the status of radio buttons**

**or check boxes as checked, add the code**

**checked="checked" to the input tag:**

**<input type="checkbox" name=**

**D** The registration form indicates any problems

and retains the form values.

➝ **"interests\[\]" value="Skiing"**

➝ **checked="checked" />**

**Of course, you’d need to use a PHP condi-**

**tional to see if that text should be added to**

**the element’s definition.**

**To preselect a pull-down menu, use**

**select-ed="selected":**

**<select name="year">**

**<option value="2011">2011</option>**

**<option value="2012" select-ed=**

➝ **"selected">2012</option>**

**</select>**

**Again, you’d need to use a PHP conditional**

**to see if that text should be added to the**

**element’s definition.**

**E** The registration form after the user successfully

fills it out.

**To preset the value of a text area, place**

**the value between the textarea tags:**

**<textarea name="comments" rows="10"**

➝ **cols="50">preset value</textarea>**

216 Chapter

8

![Image 317](index-238_1.png)

[**Sending Email**](#index_split_000.html#p8)

Sending email using PHP is theoretically

simple, merely requiring only PHP’s

**A** A user could easily attempt to send emails to

**mail()**

multiple recipients through a form like this.

function. This function uses the server’s

email application (such as **sendmail** on

Unix or Mac OS X) or an SMTP (Simple Mail

Transfer Protocol) server to send out the

messages. The basic usage of this function

is as follows:

**mail( *to*, *subject*, *body*);** The first argument is the email address

(or addresses, separated by commas)

to which the email should be sent.

The second argument establishes the

message’s subject line, and the third

argument creates the message’s content.

This function can take another argument

through which you can add more details

(additional headers) to the email, including

a From address, email priority, and carbon-

copy addresses:

**mail('someone@example.com', 'Test**

➝ **Email', 'This is a test email',**

➝ **'From: 'email@example.com');**

Although doing so is easy in theory, using

this function in real-world code can be far

more complex. For starters, setting up your

own computer to send out email can be

a challenge (see the sidebar “Configuring

Your Server to Send Email”).

Second, you should take steps to prevent

malicious people from using your forms

to send out spam. In our next example, an

email will be sent to the provided email

address. If a conniving user supplies

multiple addresses **A**, an email will be

sent to each one. There are many ways of

safeguarding against this. For the level of

this book, one simple option is to confirm

continues on next page

Creating Web Applications 217

that there’s only a single **@** present in the **Script 8.10** In PHP, you can send email by calling

provided address (i.e., it’s only one email

the **mail()** function.

address). You can count how many times

1

<?php // Script 8.10 - register.php #2

a substring is present in a string using the

2

/\* This page lets people register for

aptly named **substr\_count()** function:

the site (in theory). \*/

3

**if (substr\_count($\_POST\['email'\],**

4

// Set the page title and include the

➝ **'@') == 1) {…**

header file:

5 define('TITLE',

'Register');

With those caveats, let’s add a **mail()**

6 include('templates/header.html');

function call to the registration page so

7

that you get a sense of how the function

8

// Print some introductory text:

might be used.

9

print '<h2>Registration Form</h2>

10

<p>Register so that you can take

advantage of certain features like

**To send email with PHP:**

this, that, and the other thing.</p>';

11

**1.** Open **register.php** (Script 8.9) in your

12 // Add the CSS:

text editor or IDE.

13 print '<style type="text/css" media="screen"> **2.** Change the email validation so that it

14

.error { color: red; }

15 </style>';

also checks for a single “at” symbol

16

(**Script 8.10**):

17 // Check if the form has been submitted:

**if (empty($\_POST\['email'\]) ||**

18 if ($\_SERVER\['REQUEST\_METHOD'\] == 'POST')

➝ **(substr\_count($\_POST\['email'\],**

{

19

➝ **'@') != 1) ) {**

20

$problem = FALSE; // No problems so far.

Now the email address validation fails

21

22

// Check for each value...

if the value is empty or if it doesn’t

23

if (empty($\_POST\['first\_name'\])) {

contain exactly one **@**. This doesn’t

24 $problem

\=

TRUE;

constitute thorough validation—far from

25

print '<p class="error">Please

it—but the emails address becomes less

enter your first name!</p>';

of a security risk to use. See the tips for

26 }

27

ways to improve upon this.

28

if (empty($\_POST\['last\_name'\])) {

**3.** After the registration message (line 51),

29 $problem

\=

TRUE;

add the following:

30

print '<p class="error">Please

enter your last name!</p>';

**$body = "Thank you for registering**

31 }

➝ **with the J.D. Salinger fan**

32

➝ **club! Your password is**

**33**

**if (empty($\_POST\['email'\]) ||**

**(substr\_count($\_POST\['email'\],**

➝ **'{$\_POST\['password1'\]}'.";**

**'@') != 1) ) {**

**mail($\_POST\['email'\], 'Registration**

34 $problem

\=

TRUE;

➝ **Confirmation', $body, 'From:**

35

print '<p class="error">Please

➝ **admin@example.com');**

enter your email address!</p>';

36 }

continues on page 220

37

38

if (empty($\_POST\['password1'\])) {

39 $problem

\=

TRUE;

code continues on next page

218 Chapter

8

**Script 8.10** continued

40

print '<p class="error">Please enter a password!</p>'; 41 }

42

43

if ($\_POST\['password1'\] != $\_POST\['password2'\]) {

44 $problem

\=

TRUE;

45

print '<p class="error">Your password did not match your confirmed password!</p>'; 46 }

47

48

if (!$problem) { // If there weren't any problems...

49

50

// Print a message:

51

print '<p>You are now registered!<br />Okay, you are not really registered but...</p>'; 52

53 // Send the email:

**54**

**$body = "Thank you for registering with the J.D. Salinger fan club! Your password**

**is**

**'{$\_POST\['password1'\]}'.";**

**55**

**mail($\_POST\['email'\], 'Registration Confirmation', $body, 'From: admin@example.com');** 56

57

// Clear the posted values:

58 $\_POST

\=

array();

59

60

} else { // Forgot a field.

61

62

print '<p class="error">Please try again!</p>'; 63

64 }

65

66 } // End of handle form IF.

67

68 // Create the form:

69 ?>

70 <form action="register.php" method="post"> 71

72

<p>First Name: <input type="text" name="first\_name" size="20" value="<?php if (isset($\_POST

\['first\_name'\])) { print htmlspecialchars($\_POST\['first\_name'\]); } ?>" /></p> 73

74

<p>Last Name: <input type="text" name="last\_name" size="20" value="<?php if (isset($\_POST

\['last\_name'\])) { print htmlspecialchars($\_POST\['last\_name'\]); } ?>" /></p> 75

76

<p>Email Address: <input type="text" name="email" size="20" value="<?php if (isset($\_POST

\['email'\])) { print htmlspecialchars($\_POST\['email'\]); } ?>" /></p> 77

78

<p>Password: <input type="password" name="password1" size="20" value="<?php if (isset($\_POST

\['password1'\])) { print htmlspecialchars($\_POST\['password1'\]); } ?>" /></p> 79

<p>Confirm Password: <input type="password" name="password2" size="20" value="<?php if (isset($\_POST\['password2'\])) { print htmlspecialchars($\_POST\['password2'\]); } ?>" /></p> 80

81

<p><input type="submit" name="submit" value="Register!" /></p> 82

83 </form>

84

85 <?php include('templates/footer.html'); // Need the footer. ?> Creating Web Applications 219

![Image 318](index-241_1.png)

![Image 319](index-241_2.png)

Sometimes the easiest way to use

this function is to establish the body

as a variable and then feed it into

the **mail()** function (as opposed to

writing the email’s body within the

function call). The message itself is

sent to the address with which the

user registered, with the subject

Registration Confirmation, from the

address admin@example.com. If you’ll

be running this script on a live server,

you should use an actual email address

for that site as the from value.

**4.** Save the file, place it in the proper

**B** If the user provides multiple email addresses **A**, directory of your PHP- and email-they’ll see an error message.

enabled server, and test it in your

Web browser **B**.

**5.** Upon successfully completing the form,

check your email for the message **C**.

**The “Review and Pursue” section at the**

**end of this chapter points you in the direction**

**of an excellent tool for validating email**

**C** This email was sent by the PHP script upon

**addresses, provided you’re using version 5.2**

successful pseudo-registration.

**or later of PHP.**

**In my PHP 6 and MySQL 5 for Dynamic**

**Web Sites: Visual QuickPro Guide (Peachpit**

[**Press, 2007) and online in my forums (www.**](http://www.LarryUllman.com/forum/)

[**LarryUllman.com/forum/), I discuss other**](http://www.LarryUllman.com/forum/)

**ways to secure the emails that get sent by**

**a PHP script.**

**If you have problems receiving the PHP-**

**sent email, start by confirming that the mail**

**server works on its own without involving**

**PHP. Then make sure you’re using a valid from**

**address. Finally, try using different recipient**

**addresses and keep an eye on your spam**

**folder to see that the message isn’t getting**

**put there (if applicable).**

220 Chapter

8

 **It’s possible to send email with attachments** **Configuring Your Server**

**or HTML email, although doing so requires far**

**more sophisticated coding (normally involving**

**to Send Email**

**classes and objects). Fortunately, a number of**

Sending email with PHP is easy, as long

**programmers have already developed work-**

as your Web server (or computer) is

**able solutions that are available for use. See**

set up to send email. If you’re using a

**Appendix B, “Resources and Next Steps,” for**

**Web sites that may be of assistance.**

Web hosting service or your own Unix

computer (like Linux), this shouldn’t be a

**The mail() function returns a value (1 or**

problem at all. If you do have a problem,

**0) indicating its successful use. This value only**

contact the hosting company for support.

**indicates whether PHP was able to attempt**

If you’re running your own server (e.g., if

**to send the email (by using whatever email**

**system is in place). There’s no easy way to use**

you’re developing locally), the ability to

**PHP to see whether an email address is valid**

send email could be a sticking point. If

**or whether the end user received the message.**

you’re using an all-in-one installer, such

as MAMP or XAMPP (see Appendix A),

**To send an email to multiple addresses,**

it should also have an email server as

**either use the CC parameter or separate each**

part of the package. If you don’t receive

**TO address with a comma.**

the email after registering, check the

associated software’s documentation for

**To create new lines within the email**

**body, either create the message over multiple**

what you may need to do to enable email.

**lines or use the newline character (\\n) within**

If you’re using a Web server built into the

**double quotation marks.**

operating system, such as Apache on

Mac OS X, you may or may not already

**If you want to send multiple headers in**

be set up to send email. To start, go

**addition to the From address, separate them**

**with a combination of \\r\\n:**

ahead and try this example using a valid

email address. If you don’t receive the

**mail ('email@example.com', 'Testing',**

email, see Appendix A for information

➝ **$body, "From:email@example.org\\r\\**

about getting **mail()** to work.

➝ **nBcc:hidden@example.net,third@**

I’ll also add that I almost never worry

➝ **example.com");**

about getting PHP on my own computer

to send out emails because I’ll never be

running live Web sites from my computer.

In other words, why waste time getting

something to work that you’ll never end

up using (whereas getting PHP to send

out email on a live server does matter)?

Creating Web Applications 221

![Image 320](index-243_1.png)

[**Output Buffering**](#index_split_000.html#p8)

introduces output buffering now. Using this

feature will greatly reduce errors when you

There are a handful of functions that you’ll

begin using headers (in the next section of

use in this chapter and the next that can

this chapter), cookies (in the next chapter),

only be called if nothing has been sent to

and sessions (also in the next chapter).

the Web browser. These functions include

To begin output buffering, use the

**header()**, **setcookie()**, and **session\_**

**ob\_start()** function at the very top of

**start()**. If you use them after the Web

your page. Once you call it, every **print**

browser has already received some text,

and similar function will send data to a

HTML, or even a blank space, you’ll get

memory buffer rather than to the Web

a dreaded “headers already sent” error

browser. Conversely, HTTP calls, like

message **A**.

**header()** and **setcookie()**, won’t be

One solution that I recommend for

buffered and will operate as usual.

beginning PHP developers is to make use

At the conclusion of the script, call the

of output buffering (also called output

**ob\_end\_flush()** function to send the

control). In a normal PHP script, any HTML

accumulated buffer to the Web browser.

outside of the PHP tags is immediately sent

Or use the **ob\_end\_clean()** function to

to the Web browser. This is also true when

delete the buffered data without passing it

any **print** statement is executed. With

along. Both functions also turn off output

output buffering, the HTML and printed

buffering for that script.

data—the output—will instead be placed

From a programmer’s perspective, output

into a buffer (i.e., memory). At the end of

buffering allows you to structure a script

the script, the buffer will then be sent to the

in a more linear form, without concern for

Web browser, or if appropriate, the buffer

HTTP headers. Let’s remake **header.html**

can be cleared without being sent to the

and **footer.html** so that every page uses

Web browser. There are many reasons to

output buffering. You won’t appreciate

use output buffering, but for beginners, one

the benefits yet, but the number of errors

benefit is that you can use certain functions

you won’t see over the rest of this book

without worrying about headers already

sent

will go a long way toward preserving your

errors. Although you haven’t dealt with

programming sanity.

any of the named functions yet, this chapter

**A** If the browser receives any HTML prior to a **header()** call, you’ll see this error message.

222 Chapter

8

**Script 8.11** Add output buffering to the Web **To use output buffering:**

application by calling the **ob\_start()** function

at the top of the **header.html** script.

**1.** Open **header.html** (Script 8.7) in your

text editor or IDE.

1

<?php // Script 8.11 - header.html #4

2

**2.** At the very top of the page, before

3

// Turn on output buffering:

any HTML code, add the following

**4 ob\_start();**

(**Script 8.11**):

5

6

?><!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

**<?php**

1.1//EN" "http://www.w3.org/TR/xhtml11/

**ob\_start();**

DTD/xhtml11.dtd">

7

<html xmlns="http://www.w3.org/1999/

**?>**

xhtml" xml:lang="en">

The key to using output buffering is to

8 <head>

call the **ob\_start()** function as early

9

<title><?php // Print the page title.

10

if (defined('TITLE')) { // Is the title

as possible in a script. In this example,

defined?

you create a special section of PHP

11 print

TITLE;

prior to any HTML and call **ob\_start()**

12

} else { // The title is not defined.

13

print 'Raise High the Roof Beam! A

there. By turning on output buffering in

J.D. Salinger Fan Club';

your header file and turning it off in your

14 }

footer file, you buffer every page in the

15 ?></title>

Web application.

16

<meta http-equiv="content-type"

content="text/html; charset=utf-8" />

**3.** Open **footer.html** (Script 8.8) in your

17

<link rel="stylesheet"

text editor or IDE.

href="css/1.css" type="text/css"

media="screen,projection" />

continues on next page

18 </head>

19 <body>

20 <div

id="wrapper">

21

22 <div

id="header">

**Script 8.11** continued

23

<p class="description">A J.D.

Salinger Fan Club</p>

37

<p class="news">I privately say

24

<h1><a href="index.php">Raise High

to you, old friend... please

the Roof Beam!</a></h1>

accept from me this unpretentious

25 <ul

id="nav">

bouquet of early-blooming

26

<li><a href="books.php">

parentheses: (((()))).<br />-

Books</a></li>

<em>Raise High the Roof Beam,

27 <li><a

href="#">Stories</a></li>

Carpenters and Seymour: An

28 <li><a

href="#">Quotes</a></li>

Introduction</em></p>

29

<li><a href="login.php">

38

<p><?php // Print the current

Login</a></li>

date and time...

30

<li><a href="register.php">

39

// Set the timezone:

Register</a></li>

40

date\_default\_timezone\_set

31 </ul>

('America/New\_York');

32 </div><!-- header -->

41

33

42

// Now print the date and time:

34 <div

id="sidebar">

43

print date('g:i a l F j');

35 <h2>Favorite

Quotes</h2>

44

?></p>

36

<p class="news">I don't exactly

45 </div><!-- sidebar -->

know what I mean by that,

46

but I mean it.<br />- <em>The

47 <div

id="content">

Catcher in the Rye</em></p>

48

<!-- BEGIN CHANGEABLE CONTENT. -->

Creating Web Applications 223

![Image 321](index-245_1.jpg)

**4.** At the end of the script, after all of the

**Script 8.12** Output buffering is completed at the

HTML, add (**Script 8.12**):

end of the footer file using **ob\_end\_flush()**, which

sends the accumulated buffer to the Web browser.

**<?php**

1

<!-- END CHANGEABLE CONTENT. -->

**ob\_end\_flush();**

2

</div><!-- content -->

**?>**

3

This code turns off output buffering and

4 <div

id="footer">

5

<p>Template design by <a href=

sends the accumulated buffer to the

"http://www.sixshootermedia.com">

Web browser. In other words, all the

Six Shooter Media</a>.</p>

HTML is sent at this point.

6 <p>&copy;

2011</p>

7

</div><!-- footer -->

**5.** Save both files and place them in the

8

**templates** directory of your PHP-

9

</div><!-- wrapper -->

enabled server.

10 </body>

11 </html><?php // Script 8.12 - footer.html #2

**6.** Test any page in your Web browser **B**.

12

13

// Send the buffer to the browser and

**As a reminder, PHP code can be placed**

turn off buffering:

**in a file with an .html extension—as in**

**14 ob\_end\_flush();**

**these two examples here—if that file is being**

15 ?>

**included by a PHP script (like index.php).**

**For some time now, output buffering**

**has been automatically enabled in PHP’s**

**default configuration.**

**You can set the maximum buffer size in**

**php.ini (PHP’s configuration file). The default**

**is 4,096 bytes.**

**The ob\_get\_length() function returns**

**the length (in number of characters) of the**

**current buffer contents.**

**The ob\_get\_contents() function**

**returns the current buffer so that it can be**

**B** The site works the same as it did previously,

**assigned to a variable, should the need arise.**

but it will be easier to work with when you use

HTTP headers in the next section of this chapter.

**The ob\_flush() function sends the cur-**

**rent contents of the buffer to the Web browser**

**and then discards them, allowing a new buffer**

**to be started. This function lets your scripts**

**maintain more moderate buffer sizes.**

**The ob\_clean() function deletes the**

**current contents of the buffer without stop-**

**ping the buffer process.**

**PHP automatically runs ob\_end\_flush()**

**at the conclusion of a script if it isn’t otherwise**

**done. But it’s still a good idea to call it yourself.**

224 Chapter

8

[**Manipulating**](#index_split_000.html#p8)

[**HTTP Headers**](#index_split_000.html#p8)

Most interactions between a server and a

Web browser (the client) take place over

HTTP (Hypertext Transfer Protocol). This is

why the addresses for Web pages begin

with http://. But the Web server often

needs to communicate with a browser in

other ways, beyond just sending HTML,

images, and the like. These additional

communications can be accomplished

using HTTP headers. There are dozens of

uses for HTTP headers, all of which you

can do using PHP’s **header()** function.

Here, you’ll learn a very common use of

the **header()** function: redirecting the

user from one page to another. To redirect

the user’s browser with PHP, you send a

location header:

**header('Location: page.php');**

Normally, the **header()** function is followed

by **exit()**, to cancel the execution of the

script (because the browser has been

redirected to another page):

**header('Location: page.php');**

**exit();**

The most important thing to understand

about using **header()** is that the function

must be called before anything else is

sent to the Web browser—otherwise, you’ll

see the all-too-common “headers already

sent” error message (see **A** in the section

“Output Buffering”). If your Web page

receives any HTML or even blank space,

the **header()** function won’t work.

continues on next page

Creating Web Applications 225

Fortunately, you learned about output

**Script 8.13** The new version of the login page

buffering in the previous section. Because

redirects the user to another page using the

**header()** function.

output buffering is turned on in the Web

application, nothing is sent to the Web

1

<?php // Script 8.13 - login.php #2

browser until the very last line of the footer

2

/\* This page lets people log into the

script (when **ob\_end\_flush()** is called). By

site (in theory). \*/

3

using this method, you can avoid the dreaded

4

// Set the page title and include the

“headers already sent” error message.

header file:

To practice redirection, you’ll rewrite the

5 define('TITLE',

'Login');

6 include('templates/header.html');

login page to take the user to a welcome

7

page upon successful login.

8

// Print some introductory text:

9

print '<h2>Login Form</h2>

**To use the header() function:**

10

<p>Users who are logged in can take

advantage of certain features like

**1.** Open **login.php** in your text editor or

this, that, and the other thing.</p>';

IDE (Script 8.8).

11

12 // Check if the form has been submitted:

**2.** Delete the You are logged in… **print**

13 if ($\_SERVER\['REQUEST\_METHOD'\] == 'POST') {

statement (**Script 8.13**).

14

15

// Handle the form:

Because the user is redirected to

16

if ( (!empty($\_POST\['email'\])) &&

another page, there’s no need to

(!empty($\_POST\['password'\])) ) {

include this message.

17

18

if ( (strtolower($\_POST\['email'\])

\== 'me@example.com') && ($\_

POST\['password'\] == 'testpass') ) {

// Correct!

19

20

// Redirect the user to the

welcome page!

**21**

**ob\_end\_clean(); // Destroy**

**the buffer!**

**22 header**

**('Location:**

**welcome.php');**

**23 exit();**

24

25

} else { // Incorrect!

26

27

print '<p>The submitted email

address and password do not

match those on file!<br />Go

back and try again.</p>';

28

29 }

30

code continues on next page

226 Chapter

8

**Script 8.13** continued

**3.** Where the **print** statement was, add

the following:

31

} else { // Forgot a field.

32

**ob\_end\_clean();**

33

print '<p>Please make sure you

**header ('Location: welcome.php');**

enter both an email address and

**exit();**

a password!<br />Go back and try

again.</p>';

The first line destroys the page buffer

34

(because the accumulated buffer won’t

35 }

be used). This isn’t strictly required but

36

is a good idea. The next line redirects

37 } else { // Display the form.

38

the user to **welcome.php**. The third line

39

print '<form action="login.php"

terminates the execution of the rest of

method="post">

the script.

40

<p>Email Address: <input type="text"

name="email" size="20" /></p>

**4.** Save the file and place it in the proper

41

<p>Password: <input type="password"

directory for your PHP-enabled server

name="password" size="20" /></p>

(along with the other scripts from this

42

<p><input type="submit" name="submit"

chapter).

value="Log In!" /></p>

43 </form>';

Now you need to create the **welcome.php**

44

page to which the user will be redirected.

45 }

46

47

include('templates/footer.html');

// Need the footer.

48 ?>

Creating Web Applications 227

**To write welcome.php:**

**1.** Begin a new PHP document in your text

editor or IDE, to be named **welcome.php**

(**Script 8.14**):

**<?php // Script 8.14 - welcome.php**

**2.** Define the page title and include the

header:

**define('TITLE', 'Welcome to the**

➝ **J.D. Salinger Fan Club!');**

**include('templates/header.html');**

**3.** Create the page content:

**?>**

**<h2>Welcome to the J.D. Salinger**

➝ **Fan Club!</h2>**

**<p>You've successfully logged**

➝ **in and can now take advantage**

➝ **of everything the site has to**

➝ **offer.</p>**

**Script 8.14** The welcome page greets the user after they've logged in.

1

<?php // Script 8.14 - welcome.php

2

/\* This is the welcome page. The user is redirected here

3

after they successfully log in. \*/

4

5

// Set the page title and include the header file:

6

define('TITLE', 'Welcome to the J.D. Salinger Fan Club!');

7 include('templates/header.html');

8

9

// Leave the PHP section to display lots of HTML:

10 ?>

11

12 <h2>Welcome to the J.D. Salinger Fan Club!</h2>

13

<p>You've successfully logged in and can now take advantage of everything the site has to offer.</p>

14

<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p> 15

16 <?php include('templates/footer.html'); // Need the footer. ?> 228 Chapter

8

![Image 322](index-250_1.jpg)

![Image 323](index-250_2.png)

![Image 324](index-250_3.png)

**4.** Return to PHP and include the footer:

**<?php include('templates/**

➝ **footer.html'); ?>**

**5.** Save the script as **welcome.php**, place

it in the same directory as the new ver-

sion of **login.php**, and test it in your

Web browser **A**, **B**, and **C**.

**The headers\_sent() function returns**

**TRUE if the page has already received HTTP**

**A** The login form…

**headers and the header() function can’t**

**be used.**

**Using the GET method trick, you can**

**pass values from one page to another using**

**header():**

**$var = urlencode('Pass this text');**

**header ("Location: page.php?**

➝ **message=$var");**

**The header() function should techni-**

**cally use a full path to the target page when**

**redirecting. For example, it should be**

**B** …and the redirection if the user properly

logged in.

**header ('Location: http://www.**

➝ **example.com/welcome.php');**

**or**

**header ('Location: http://localhost/**

➝ **welcome.php');**

**In my book PHP 6 and MySQL 5 for**

**Dynamic Web Sites: Visual QuickPro Guide, I**

**show some code for dynamically generating**

**C** If the user didn’t properly log in, they remain on

the login page.

**an absolute URL based on the location of the**

**current script.**

Creating Web Applications 229

[**Review and Pursue**](#index_split_000.html#p8)

**Pursue**

■

Create a new prototype design for

If you have any problems with the review

this chapter’s examples, and then

questions or the pursue prompts, turn

create new header and footer files.

to the book’[s supporting forum (www.](http://www.LarryUllman.com/forum/)

View any of the site’s pages again

[LarryUllman.com/ forum/ ).](http://www.LarryUllman.com/forum/)

(you should not need to change

any of the PHP scripts).

**Review**

■

Change the parameters to the **date()**

■

What is the difference between

function in **header.html** to display the

**include()** and **required()**?

date and/or time in a different manner.

■

Why can you put PHP code into an

■

Rewrite the password conditionals

included file even when it uses an

found in **register.php** as a nested pair

**.html** extension?

of conditionals. Hint: See Chapter 6

■

What are the differences between

for examples.

relative and absolute references

■

If you’re using PHP 5.2 or later, check

to a file?

out the PHP manual pages for the

■

How do you define a constant? Are

Filter extension. Then incorporate the

constant names case-sensitive or

**filter\_var()** function to validate the

case-insensitive? How do you check

email address in **register.php**.

if a constant has been defined?

■

Change the subject and body of the

■

What is the epoch? What is a timestamp?

email sent upon (pseudo-) registration

to something more interesting and

■

What is the significance of

informative.

**$\_SERVER\['REQUEST\_METHOD'\]**?

■

How do you have a form element

“remember” previously submitted values?

■

How can you see a PHP error that

occurs within a form element (e.g., when

presetting a form’s element’s value)?

■

What does the “headers already sent”

error mean? How can it be prevented?

230 Chapter

8

[**9**](#index_split_000.html#p8)

[Cookies and](#index_split_000.html#p8)

[Sessions](#index_split_000.html#p8)

Chapter 8, “Creating Web Applications,” cov-

ered a number of techniques for developing

**In This Chapter**

more fully realized Web sites. One missing

piece—the focus of this chapter—is how

What Are Cookies?

232

to maintain “state” as the user traverses a

Creating Cookies

234

multipage Web site. The Hypertext Transfer

Reading from Cookies

239

Protocol (HTTP) is a stateless technology,

meaning that it has no built-in method for

Adding Parameters to a Cookie

242

tracking a user or remembering data from

Deleting a Cookie

245

one page of an application to the next. This

What Are Sessions?

248

is a serious problem, because e-commerce

applications, user registration and login sys-

Creating a Session

249

tems, and other common online services rely

Accessing Session Variables

252

on being able to follow the same user from

Deleting a Session

254

page to page. Fortunately, maintaining state

is quite simple with PHP.

Review and Pursue

256

This chapter discusses the two primary

methods for tracking data: cookies and

sessions. You’ll start by learning how to

create, read, modify, and delete cookies.

Then you’ll see how easy it is to master

sessions, a more potent option for main-

taining state.

![Image 325](index-253_1.png)

![Image 326](index-253_2.png)

![Image 327](index-253_3.png)

![Image 328](index-253_4.png)

![Image 329](index-253_5.png)

![Image 330](index-253_6.png)

![Image 331](index-253_7.png)

![Image 332](index-253_8.png)

![Image 333](index-253_9.png)

![Image 334](index-253_10.png)

![Image 335](index-253_11.png)

![Image 336](index-253_12.png)

![Image 337](index-253_13.png)

![Image 338](index-253_14.png)

![Image 339](index-253_15.png)

![Image 340](index-253_16.png)

![Image 341](index-253_17.png)

![Image 342](index-253_18.png)

[**What Are Cookies?**](#index_split_000.html#p8)

Prior to the existence of cookies, traversing

a Web site was a trip without a history.

Although the browser tracks the pages you

visit, allowing you to use the Back button

to return to previously visited pages and

indicating visited links in a different color,

the server does not follow what individual

users see and do. This is still true for sites

that don’t use cookies, as well as for users

who have disabled cookies in their Web

browsers **A**.

**A** Most Web browsers let users set the cookie-

Why is that a problem? If the server can’t

handling preferences. This is Internet Explorer 8’s

Advanced Privacy Settings tab.

track a user, there can be no shopping carts

for making purchases online. If cookies

didn’t exist (or if they’re disabled in the Web

browser), people wouldn’t be able to use

popular sites that require user registration.

In short, without cookies, there would be no

Amazon or Facebook or any of the other

most popular or useful sites (not in their

current incarnations, at least).

Cookies are simply a way for a server to

store information on the user’s computer. By

**B** How cookies are sent back and forth between

doing so, the server can remember the user

the server and the client.

over the course of a visit or through several

visits. Think of a cookie like a name tag: You

tell the server your name, and it gives you a

name tag. Then it can know who you are by

referring back to the name tag.

This brings up another point about the

security issues involved with cookies.

Cookies have gotten a bad rap because

users believe cookies allow a server to

know too much about them. However,

a cookie can only be used to store

information that you give it, so it’s as

secure as you want it to be. And, as

previously mentioned, it’s very easy

in modern browsers to customize the

cookie handling as desired.

232 Chapter

9

PHP has very good support for cookies.

browser, but only the site that originally

In this chapter, you’ll learn how to set a

sent a cookie can read it. Also, the cookies

cookie, retrieve information from a cookie,

are read by the site when the page on that

and then delete the cookie. You’ll also see

site is requested by the Web browser. In

some of the optional parameters you can

other words, when the user enters a URL in

use to apply limits to a cookie’s existence.

the address bar and clicks Go (or whatever),

the site reads any cookies it has access to

Before moving on, there are two more

and then serves up the requested page.

things you ought to know about cookies.

This order is important because it dictates

The first is how to debug cookie-related

when and how cookies can be accessed.

problems. You’ll inevitably need to know

how to do that, so the topic is discussed

in the sidebar “Debugging Cookies.” The

**The ability to send, read, and delete**

**cookies is one of the few overlaps between**

second is how a cookie is transmitted and

**server-side PHP and browser-side JavaScript.**

received **B**. Cookies are stored in the Web

**Debugging Cookies**

When you begin working with cookies in PHP, you’ll need to know how to debug your cookie-related scripts when difficulties arise. Three areas might cause you problems:

. Sending the cookie with PHP

. Receiving the cookie in your Web browser

. Accessing a cookie in a PHP script

The first and last issues can be debugged by printing out the variable values in your PHP scripts (as you’ll soon learn). The second issue requires that you know how to work with cookies in your Web browser. For debugging purposes, you’ll want your Web browser to notify you when a cookie is being sent.

With Internet Explorer on Windows, you can do this by choosing Internet Options under the Tools menu. Then click the Privacy tab, followed by the Advanced button under Settings. Click “Override automatic cookie handling,” **A** and then choose Prompt for both First-party and Third-party Cookies (you can actually block the third-party cookies, if you’d rather). Other versions of Internet Explorer may use different variations on this process. Internet Explorer also has a Developer Tools window (linked under the Tools menu) that can be useful.

The best way to debug cookies when using Firefox on any platform is to install one of the many cookie-related extensions, like Firecookie. The Firebug extension, which every developer must use, also shows cookie-related information. But at the very least, if you select “Use custom settings for history” on the Privacy panel (in the Options/Preferences window), you’ll be able to establish custom cookie behavior, such as being prompted.

Safari on Mac OS X and Windows doesn’t give you as many cookie choices; you can find the available options on the Security tab of the Preferences window.

Some browsers also let you browse through the existing cookies to see their names and values.

Doing so is a great asset in the debugging war.

Cookies and Sessions 233

![Image 343](index-255_1.png)

![Image 344](index-255_2.png)

[**Creating Cookies**](#index_split_000.html#p8)

An important thing to understand about

cookies is that they must be sent from

the server to the client prior to any other

information. This means a script should

send cookies before any **print** statement,

before including an external file that

contains HTML, and so forth.

Should the server attempt to send a

cookie after the Web browser has already

**A** A message like this is what you’ll see if the

**setcookie()** function is called after anything, even

received HTML—even an extraneous white

a blank line or space, has already been sent to the

space—an error message will result and

Web browser.

the cookie won’t be sent **A**. This is by far

the most common cookie-related error.

Cookies are sent using the **setcookie()**

function:

**setcookie( *name*, *value*);**

**setcookie('CookieName', 'This is the**

➝ **cookie value.');**

That line of code sends to the browser a

cookie with the name ***CookieName*** and the

value ***This is the cookie value.*** **B**.

You can continue to send more cookies

to the browser with subsequent uses of

the **setcookie()** function, although you’re

limited by the Web browser as to how many

cookies can be sent from the same site:

**setcookie('name2', 'some value');**

**setcookie('name3', 'another value');**

**B** If the browser is set to prompt the user for cookies,

Finally, when creating cookies, you can—as

a message like this will appear for each cookie sent.

(Note that the window, from Internet Explorer 8,

you’ll see in this example—use a variable for

shows the value in a URL-encoded format.)

the name or value attribute of your cookies:

**setcookie($cookie\_name, $cookie\_value);**

234 Chapter

9

![Image 345](index-256_1.png)

![Image 346](index-256_2.png)

For an example of setting cookies, you’ll

create a script that allows the user to

specify the default font size and color

for a page. The page displays a form for

**C** This form is used to select the

font size and color for use on another

choosing these values **C** and then handles

PHP page.

the form submission **D**. A separate page,

created in the next section of this chapter,

will use these settings.

**To send cookies:**

**1.** Create a new PHP document in

your text editor or IDE, to be named

**D** After submitting the form, the page shows a

message and a link to another page (where the

**customize.php** (**Script 9.1**):

user’s preferences will be used). That page will

be created next.

**<?php // Script 9.1 - customize.php**

The most critical issue with cookies is

**Script 9.1** Two cookies will be used to store the

that they’re created before anything is

user's choices for the font size and color. This

page both displays and handles the form.

sent to the Web browser. To accomplish

this, the script begins with a PHP section

1

<?php // Script 9.1 - customize.php

that handles the sending of cookies.

2

3

// Handle the form if it has been

Also be certain not to have any

submitted:

extraneous spaces or lines before

4

if (isset($\_POST\['font\_size'\],

the initial PHP tag.

$\_POST\['font\_color'\]))

{

5

**2.** Check whether the form has been

6

// Send the cookies:

submitted:

**7 setcookie('font\_size',**

**$\_POST\['font\_size'\]);**

**if (isset($\_POST\['font\_size'\],**

**8 setcookie('font\_color',**

➝ **$\_POST\['font\_color'\])) {**

**$\_POST\['font\_color'\]);**

This page will both display and handle

9

the form. It could use the same method

10

// Message to be printed later:

11

$msg = '<p>Your settings have

explained in the previous chapter—

been entered! Click <a href=

checking if the **$\_SERVER\['REQUEST\_**

"view\_settings.php">here</a>

**METHOD'\]** variable has a value of ***POST***,

to see them in action.</p>';

but as an alternative approach, the script

12

will perform basic, minimal validation

13 } // End of submitted IF.

14

?><!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

as the test for a form submission. The

1.0 Transitional//EN"

conditional checks for the existence of

15

"http://www.w3.org/TR/xhtml1/DTD/

two variables: **$\_POST\['font\_size'\]** and

xhtml1-transitional.dtd">

**$\_POST\['font\_color'\]**. If both are set,

16

<html xmlns="http://www.w3.org/1999/

the form submission will be addressed.

xhtml" xml:lang="en" lang="en">

continues on next page

code continues on next page

Cookies and Sessions 235

**3.** Create the cookies:

**Script 9.1** continued

**setcookie('font\_size',**

17 <head>

➝ **$\_POST\['font\_size'\]);**

18

<meta http-equiv="Content-Type"

**setcookie('font\_color',**

content="text/html; charset=utf-8"/>

19

<title>Customize Your Settings

➝ **$\_POST\['font\_color'\]);**

</title>

These two lines create two separate

20 </head>

cookies. One is named ***font\_size*** and

21 <body>

22

<?php // If the cookies were sent, print

the other ***font\_color***. Their values

a message.

will be based on the selected values

23 if (isset($msg)) {

from the HTML form, which are stored

24 print

$msg;

in the **$\_POST\['font\_size'\]** and

25 }

**$\_POST\['font\_color'\]** variables.

26 ?>

27

In a more fully developed application,

28

<p>Use this form to set your

you should first confirm that the

preferences:</p>

variables both have acceptable values.

29

30

<form action="customize.php"

**4.** Create a message and complete the

method="post">

conditional and the PHP section:

31 <select

name="font\_size">

32

<option value="">Font Size</option>

**$msg = '<p>Your settings**

33

<option value="xx-small">xx-small

 ➝ **have been entered! Click**

</option>

 ➝ **<a href="view\_settings.**

34 <option

value="x-small">x-small

 ➝ **php">here</a> to see them in**

</option>

35 <option

value="small">small

➝ **action.</p>';**

</option>

**} // End of submitted IF.**

36 <option

value="medium">medium

**?>**

</option>

37 <option

value="large">large

When the form has been submitted,

</option>

the cookies will be sent and the **$msg**

38 <option

value="x-large">x-large

variable will be assigned a string value.

</option>

This variable will be used later in the

39 <option

value="xx-large">xx-large

script to print a message. This approach

</option>

40 </select>

is necessary, as you can’t print the

41 <select

name="font\_color">

message at this juncture (because not

42

<option value="">Font Color

even the HTML head has been created).

</option>

43 <option

value="999">Gray</option>

**5.** Create the HTML head and opening

44 <option

value="0c0">Green</option>

body tag:

45 <option

value="00f">Blue</option>

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

46 <option

value="c00">Red</option>

47 <option

value="000">Black</option>

➝ **XHTML 1.0 Transitional//EN"**

48 </select>

**"http://www.w3.org/TR/xhtml1/**

49

<input type="submit" name="submit"

 ➝ **DTD/xhtml1-transitional.dtd">**

value="Set My Preferences" />

**<html xmlns="http://www.w3.org/**

50 </form>

➝ **1999/xhtml" xml:lang="en"**

51

52 </body>

➝ **lang="en">**

53 </html>

236 Chapter

9

**<head>**

**<option**

**value="medium">medium**

**<meta**

**http-equiv="Content-Type"**

 ➝ **</option>**

 ➝ **content="text/html;**

**<option**

**value="large">large**

 ➝ **charset=utf-8"/>**

 ➝ **</option>**

**<title>Customize Your Settings**

**<option**

**value="x-large">x-large**

 ➝ **</title>**

 ➝ **</option>**

**</head>**

**<option**

**value="xx-large">**

**<body>**

 ➝ **xx-large</option>**

**</select>**

All of this code must come after the

**setcookie()** lines. Not to overstate the

The HTML form itself is very simple **C**.

fact, but no text, HTML, or blank spaces

The user is given one drop-down menu

can be sent to the Web browser prior to

to select the font size. The value for

the **setcookie()** calls.

each corresponds to the CSS code

used to set the document’s font size:

**6.** Create another PHP section to report

from ***xx-small*** to ***xx-large***.

on the cookies being sent:

Because this script both displays and

**<?php**

handles the form, the form’s **action**

**if (isset($msg)) {**

attribute points to the same file.

**print**

**$msg;**

**}**

**8.** Complete the HTML form:

**?>**

**<select**

**name="font\_color">**

This code prints out a message if the

**<option value="">Font Color**

cookies have been sent. The first

 ➝ **</option>**

time the user comes to the page, the

**<option**

**value="999">Gray</option>**

cookies haven’t been sent, so **$msg** is

**<option**

**value="0c0">Green</option>**

not set, making this conditional **FALSE**,

**<option**

**value="00f">Blue</option>**

and this **print** invocation never runs.

**<option**

**value="c00">Red</option>**

Once the form has been submitted,

**<option**

**value="000">Black</option>**

**$msg** has been set by this point, so this

**</select>**

conditional is **TRUE** **D**.

**<input type="submit" name=**

**7.** Begin the HTML form:

 ➝ **"submit" value="Set My**

 ➝ **Preferences" />**

**<p>Use this form to set your**

**</form>**

➝ **preferences:</p>**

**<form action="customize.php"**

The second drop-down menu is used to

➝ **method="post">**

select the font color. The menu displays

**<select**

**name="font\_size">**

the colors in text form, but the values are

**<option value="">Font Size**

HTML color values. Normally such values

 ➝ **</option>**

are written using six characters plus

**<option**

**value="xx-small">**

a pound sign (e.g., ***#00cc00***), but CSS

 ➝ **xx-small</option>**

allows you to use just a three-character

**<option**

**value="x-small">**

version and the pound sign will be added

 ➝ **x-small</option>**

on the page that uses these values.

**<option**

**value="small">small**

continues on next page

 ➝ **</option>**

Cookies and Sessions 237

![Image 347](index-259_1.png)

![Image 348](index-259_2.png)

**9.** Complete the HTML page:

**</body>**

**</html>**

**10.** Save the file as **customize.php** and

place it in the proper directory for your

PHP-enabled server.

**11.** Make sure you’ve set your Web browser

to prompt for each cookie, if applicable.

To guarantee that the script is working,

you want the browser to prompt you

for each cookie, if you can. See the

“Debugging Cookies” sidebar.

**12.** Run the script in your Web browser **E**

and **F**.

**Cookies are one of the few areas in PHP**

**E** The user sees this message when the first

**that can behave differently from browser to**

**setcookie()** call is made, if they’ve opted to be

prompted before accepting a cookie. This cookie

**browser or operating system to operating**

is storing the value of ***x-large*** in a cookie named **system. You should test your cookie-based**

***font\_size***.

**applications on as many browsers and**

**operating systems as you can.**

**If you use the output buffering tech-**

**nique taught in Chapter 8, then you can place**

**your setcookie() calls anywhere within**

**the script (because the Web browser won’t**

**receive the data until the ob\_end\_flush()**

**function is called).**

**Cookies are limited to approximately**

**4 KB of total data. This is more than sufficient**

**for most applications.**

**To test whether it’s safe to send a cookie,**

**use the headers\_sent() function. It reports**

**on whether HTTP headers have already been**

**sent to the Web browser.**

**F** The Firebug extension

for Firefox shows the

cookies received by the

browser. The second cookie

that’s sent by the PHP

script is called ***font\_color***

and has a value of ***999***,

representing the color gray.

238 Chapter

9

**Script 9.2** This script sets the font size and color in CSS, using the values stored in the cookies.

[**Reading from Cookies**](#index_split_000.html#p8)

Just as form data is stored in the **$\_POST**

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

1.0 Transitional//EN"

array (assuming it used the POST method)

2

"http://www.w3.org/TR/xhtml1/DTD/

and values passed to a script in the

xhtml1-transitional.dtd">

URL are stored in the **$\_GET** array, the

3

<html xmlns="http://www.w3.org/1999/

**setcookie()** function places cookie data

xhtml" xml:lang="en" lang="en">

in the **$\_COOKIE** array. To retrieve a value

4 <head>

5

<meta http-equiv="content-type"

from a cookie, you only need to refer to

content="text/html; charset=utf-8" />

the cookie name as the index of this array.

6

<title>View Your Settings</title>

For example, to retrieve the value of the

7 <style

type="text/css">

cookie established with the line

8 body

{

9

<?php // Script 9.2 - view\_settings.php

**setcookie('user', 'trout');**

10

you would use the variable **$\_COOKIE\['user'\]**.

11 // Check for a font\_size value:

**12 if (isset($\_COOKIE\['font\_size'\])) {**

Unless you change the cookie’s parameters

**13**

**print "\\t\\tfont-size: " .**

(as you’ll see later in this chapter), the cookie

**htmlentities($\_COOKIE\['font\_**

will automatically be accessible to every

**size'\]) . ";\\n";**

**14 } else {**

other page in your Web application. You

**15**

**print "\\t\\tfont-size: medium;";**

should understand, however, that a cookie

**16 }**

is never accessible to a script immediately

17

after it’s been sent. You can’t do this:

18 // Check for a font\_color value:

**19 if (isset($\_COOKIE\['font\_color'\])) {**

**setcookie('user', 'trout');**

**20**

**print "\\t\\tcolor: #" .**

**print $\_COOKIE\['user'\]; // No value.**

**htmlentities($\_COOKIE\['font\_**

**color'\]) . ";\\n";**

The reason for this is the order in which

**21 } else {**

cookies are read and sent (see **B** in the

**22**

**print "\\t\\tcolor: #000;";**

first section of this chapter).

**23 }**

24

To see how simple it is to access cookie

25 ?>

values, let’s write a script that uses the

26 }

preferences set in **customize.php** to

27 </style>

specify the page’s text size and color. The

28 </head>

script relies on CSS to achieve this effect.

29 <body>

30

<p><a href="customize.php">Customize Your

Settings</a></p>

**To retrieve cookie data with PHP:**

31

<p><a href="reset.php">Reset Your

Settings</a></p>

**1.** Begin a new PHP document in your

32

text editor or IDE, to be named

33 <p>yadda yadda yadda yadda yadda

**view\_settings.php** (**Script 9.2**):

34 yadda yadda yadda yadda yadda

35 yadda yadda yadda yadda yadda

**<!DOCTYPE html PUBLIC "-//W3C//**

36 yadda yadda yadda yadda yadda

➝ **DTD XHTML 1.0 Transitional//EN"**

37 yadda yadda yadda yadda yadda</p>

**"http://www.w3.org/TR/xhtml1/**

38

 ➝ **DTD/xhtml1-transitional.dtd">**

39 </body>

40 </html>

continues on next page

Cookies and Sessions 239

**<html xmlns="http://www.w3.org/**

sufficient to see if the cookie exists. If

➝ **1999/xhtml" xml:lang="en"**

no such cookie exists, PHP will print out

➝ **lang="en">**

a default size, medium.

**<head>**

For security purposes, the cookie’s

**<meta**

**http-equiv="content-type"**

value is not directly printed. Instead,

 ➝ **content="text/html;**

it’s run through the **htmlentities()**

 ➝ **charset=utf-8" />**

function, discussed in Chapter 5, “Using

**<title>View Your Settings**

Strings.” This function will prevent bad

 ➝ **</title>**

things from happening should the user

**2.** Start the CSS section:

manipulate the value of the cookie

**<style type="text/css">**

(which is easy to do).

**body**

**{**

Also note that two tabs (**\\t**) and a

The page will use CSS to enact the

newline (**\\n**) are added to the **print**

user’s preferences. The aim is to create

statements so that the resulting CSS

code like

code is formatted properly. Not that this

affects the functionality of the page, but…

**body {**

**font-size:**

**x-large;**

**5.** Repeat this process for the font

**color:**

**#999;**

color cookie:

**}**

**if (isset($\_COOKIE\['font\_color'\])) {**

The two values will differ based on what

**print "\\t\\tcolor: #" .**

the user selected in the **customize.php**

 ➝ **htmlentities($\_COOKIE**

page. In this step, you create the initial

 ➝ **\['font\_color'\]) . ";\\n";**

CSS tag.

**} else {**

**print "\\t\\tcolor: #000;";**

**3.** Open a section of PHP code:

**}**

**<?php // Script 9.2 -**

Here the CSS’s **color** attribute is being

➝ **view\_settings.php**

assigned a value. The cookie itself is

The script will now use PHP to print out

used the same as in Step 4.

the remaining CSS, based on the cookies.

**6.** Close the PHP section, complete the

**4.** Use the font size cookie value, if it exists:

CSS code, and finish the HTML head:

**if (isset($\_COOKIE\['font\_size'\])) {**

**?>**

**print "\\t\\tfont-size: " .**

**}**

 ➝ **htmlentities($\_COOKIE**

**</style>**

 ➝ **\['font\_size'\]) . ";\\n";**

**</head>**

**} else {**

**7.** Start the HTML body and create links to

**print "\\t\\tfont-size: medium;";**

two other pages:

**}**

**<body>**

If the script can access a cookie with

**<p><a href="customize.php">**

a name of ***font\_size***, it will print out

➝ **Customize Your Settings</a></p>**

that cookie’s value as the CSS **font-**

**<p><a href="reset.php">Reset Your**

**size** value. The **isset()** function is

➝ **Settings</a></p>**

240 Chapter

9

![Image 349](index-262_1.png)

![Image 350](index-262_2.png)

These two links take the user to two

other PHP pages. The first, **customize.**

**php**, has already been written and

lets the user define their settings. The

second, **reset.php**, will be written later

in the chapter and lets the user delete

their customized settings.

**8.** Add some text:

**<p>yadda yadda yadda yadda yadda**

**yadda yadda yadda yadda yadda**

**yadda yadda yadda yadda yadda**

**yadda yadda yadda yadda yadda**

**A** This page reflects the customized font choices

**yadda yadda yadda yadda yadda</p>**

made using the other PHP script.

This text exists simply to show the

effects of the cookie changes.

**9.** Complete the HTML page:

**</body>**

**</html>**

**10.** Save the file as **view\_settings.php**,

place it in the same directory as

**customize.php**, and test it in your

Web browser **A** by clicking the link

on **customize.php**.

**11.** View the source of the page to see the

resulting CSS code **B**.

**12.** Use the customize page to change your

settings and return to this script.

Each submission of the form will create

two new cookies storing the form values,

thereby replacing the existing cookies.

**B** By viewing the source code of the page, you

**The value of a cookie is automatically**

can also track how the CSS values change.

**encoded when it’s sent and decoded on being**

**received by the PHP page. The same is true of**

**values sent by HTML forms.**

Cookies and Sessions 241

[**Adding Parameters**](#index_split_000.html#p8)

one hour (60 seconds times 60 minutes)

from the current moment:

[**to a Cookie**](#index_split_000.html#p8)

**setcookie( *name*, *value*, time()+3600);** Although passing just the **name** and **value**

Because the expiration time will be calculated

arguments to the **setcookie()** function will

as the value of **time()** plus 3600, that

suffice for most of your cookie uses, you

argument isn’t put in quotes (you don’t want to

ought to be aware of the other arguments

literally pass ***time() + 3600*** as the expiration

available. The function can take up to five

but rather the result of that calculation).

more parameters, each of which limits the

The **path** and **domain** arguments are used

operation of the cookie:

to limit a cookie to a specific folder in a

**setcookie( *name*, *value*, *expiration*,** Web site (the path) or to a specific domain.

➝ ***path*****, *domain*, *secure*, *httponly*);** Using the **path** option, you could limit a

cookie to exist only while a user is in a

The **expiration** argument is used to set a

specific subfolder of the domain:

specific length of time for a cookie to exist.

If it isn’t specified, the cookie will continue

**setcookie( *name*, *value*, time()+3600,** to be functional until the user closes the

➝ **'/ *subfolder*/');**

browser. Normally, you set the expiration

Cookies are already specific to a domain,

time by adding a particular number of

so the **domain** argument might be used

minutes or hours to the current time. You

to limit a cookie to a subdomain, such as

can find the current time in PHP by using

**forum.example.com**.

the **time()** function (it returns a timestamp;

**setcookie( *name*, *value*, time()+3600, '',** see Chapter 8). Therefore, this line of code

➝ **'forum.example.com');**

sets the expiration time of the cookie to be

**Script 9.3** When you add the ***expiration*** arguments to the two cookies, the cookies will persist even after the user has closed out of and later returned to their browser.

1

<?php // Script 9.3 - customize.php #2

2

3

// Handle the form if it has been submitted:

4

if (isset($\_POST\['font\_size'\], $\_POST\['font\_color'\])) {

5

6

// Send the cookies:

**7**

**setcookie('font\_size', $\_POST\['font\_size'\], time()+10000000, '/');** **8**

**setcookie('font\_color', $\_POST\['font\_color'\], time()+10000000, '/');** 9

10

// Message to be printed later:

11

$msg = '<p>Your settings have been entered! Click <a href="view\_settings.php">here</a> to see them in action.</p>';

12

13 } // End of submitted IF.

14

?><!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"

15

"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> 16

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en"> code continues on next page

242 Chapter

9

**Script 9.3** continued

The ***secure*** value dictates that a cookie

should only be sent over a secure HTTPS

17 <head>

connection. A value of 1 indicates that a

18

<meta http-equiv="Content-Type"

content="text/html; charset=utf-8"/>

secure connection must be used, whereas

19

<title>Customize Your Settings

0 indicates that a secure connection isn’t

</title>

necessary. You could ensure a secure

20 </head>

cookie transmission for e-commerce sites:

21 <body>

22

<?php // If the cookies were sent, print

**setcookie('cart', '82ABC3012',**

a message.

➝ **time()+3600, ', 'shop.example.com', 1);**

23 if (isset($msg)) {

24 print

$msg;

As with all functions that take arguments,

25 }

you must pass all the values in order. In the

26 ?>

preceding example, if there’s no need to

27

specify (or limit) the path, you use empty

28

<p>Use this form to set your

quotes. With the **path** argument, you can

preferences:</p>

29

also use a single slash (**/**) to indicate the

30

<form action="customize.php"

root folder (i.e., no path restriction). By

method="post">

doing so, you maintain the proper number

31 <select

name="font\_size">

of arguments and can still indicate that an

32

<option value="">Font Size</option>

HTTPS connection is necessary.

33

<option value="xx-small">xx-small

</option>

The final argument— ***httponly***—was added

34

<option value="x-small">x-small

in PHP 5.2. It can be used to restrict access

</option>

to the cookie (for example, preventing a

35

<option value="small">small

</option>

cookie from being read using JavaScript)

36

<option value="medium">medium

but isn’t supported by all browsers.

</option>

Let’s add an expiration date to the existing

37

<option value="large">large

</option>

**customize.php** page so that the user’s

38

<option value="x-large">x-large

preferences will remain even after they’ve

</option>

closed their browser and then returned to

39

<option value="xx-large">xx-large

the site later.

</option>

40 </select>

41 <select

name="font\_color">

**To set a cookie’s expiration date:**

42

<option value="">Font Color</option>

**1.** Open **customize.php** (Script 9.1) in your

43 <option

value="999">Gray</option>

text editor or IDE.

44 <option

value="0c0">Green</option>

45 <option

value="00f">Blue</option>

**2.** Change the two **setcookie()** lines to

46 <option

value="c00">Red</option>

read as follows (**Script 9.3**):

47 <option

value="000">Black</option>

48 </select>

**setcookie('font\_size', $\_POST**

49

<input type="submit" name="submit"

➝ **\['font\_size'\], time()+10000000,**

value="Set My Preferences" />

➝ **'/', '', 0);**

50 </form>

**setcookie('font\_color', $\_POST**

51

52 </body>

➝ **\['font\_color'\], time()+10000000,**

53 </html>

➝ **'/', '', 0);**

continues on next page

Cookies and Sessions 243

![Image 351](index-265_1.png)

![Image 352](index-265_2.png)

To make these cookies persist for a long

**Not all browsers acknowledge a cookie’s**

time (specifically, for a couple of months),

**adjusted expiration time when the cookie is**

set the expiration time to be 10,000,000

**being sent from your own computer (i.e., from**

**localhost).**

seconds from now. While you’re at it,

set the **path** argument to the root of

**Here are some general guidelines for**

the site (**/**). Doing so may improve the

**what kind of expiration date to use with your**

consistency of sending these cookies

**cookies: If the cookie should last as long**

across the various browsers.

**as the user browses through the site, don’t**

**set an expiration time. If the cookie should**

Because the expiration date of the

**continue to exist after the user has closed and**

cookies is set months into the future,

**reopened the browser, set an expiration time**

the user’s preferences, which are

**that’s weeks or months in the future. And if**

**the cookie can constitute a security risk, set**

stored in the cookies, will be valid even

**an expiration time of an hour or a fraction**

after the user has closed and reopened

**thereof so that the cookie doesn’t continue to**

the browser. Without this expiration

**exist too long after a user has left the browser.**

date, users would see the default font

size and color and have to reassign

**For security purposes, you can set a**

**5- or 10-minute expiration time on a cookie**

their preferences with every new

**and have the cookie re-sent with every new**

browser session.

**page the user visits. This way, the cookie will**

**3.** Save the file, place it in the proper

**continue to persist as long as the user is active**

**but will automatically die 5 or 10 minutes after**

directory for your PHP-enabled server,

**the user’s last action.**

and test it again in your Web browser

**A** and **B**.

**A** The browser’s cookie

reporting tools (here, Firebug

on Firefox) now reflects the

cookie expiration dates.

**B** The new cookie parameters

don’t adversely affect the

functionality of the application.

244 Chapter

9

![Image 353](index-266_1.png)

[**Deleting a Cookie**](#index_split_000.html#p8)

The final thing to know about cookies is

how to delete them. Although a cookie

automatically expires when the user’s

browser is closed or when the expiration

date/time is met, sometimes you’ll want

to manually delete the cookie as well. For

example, Web sites that have registered

**A** How Firefox displays the cookie information

users and login capabilities generally

when a deletion cookie is sent.

delete any cookies when the user logs out.

The **setcookie()** function can take up to

seven arguments, but only one is required—

the name. If you send a cookie that consists

of a name without a value, it will have the

same effect as deleting the existing cookie

of the same name. For example, to create

the cookie ***username***, you use this line:

**setcookie('username', 'Larry');**

To delete the ***username*** cookie, you code

**setcookie('username', '');**

or

**setcookie('username', FALSE);**

As an added precaution, you can also set

an expiration date that’s in the past **A**:

**setcookie('username', FALSE,**

➝ **time() - 600);**

The only caveat when it comes to deleting

a cookie is that you must use the same

argument values that were used to set

the cookie in the first place (aside from

the value and expiration). For example, if

you set a cookie while providing a **domain**

value, you must also provide that value

when deleting the cookie:

**setcookie('user', 'larry', time() +**

➝ **3600, '', 'forums.example.com');**

**setcookie('user', '', time() -**

➝ **600, '', 'forums.example.com');**

continues on next page

Cookies and Sessions 245

To demonstrate this feature, let’s add a

**Script 9.4** To delete the existing cookies, send

reset page to the Web application. This

new cookies with the same names, empty values,

and expirations in the past.

PHP script will destroy the sent cookies, so

that the user’s preferences are forgotten.

1

<?php // Script 9.4 - reset.php

2

3

// Delete the cookies:

**To delete a cookie:**

**4**

**setcookie('font\_size', '', time()**

**1.** Begin a new PHP script in your text

**\- 600, '/');**

**5**

**setcookie('font\_color', '', time()**

editor or IDE, to be named **reset.php**

**\- 600, '/');**

(**Script 9.4**):

6

**<?php // Script 9.4 - reset.php**

7

?><!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

1.0 Transitional//EN"

**2.** Delete the existing cookies by sending

8

"http://www.w3.org/TR/xhtml1/DTD/

blank cookies. Then complete the

xhtml1-transitional.dtd">

PHP code:

9

<html xmlns="http://www.w3.org/1999/

xhtml" xml:lang="en" lang="en">

**setcookie('font\_size', '',**

10 <head>

➝ **time() - 600, '/');**

11

<meta http-equiv="Content-Type"

**setcookie('font\_color', '',**

content="text/html; charset=utf-8"/>

12

<title>Reset Your Settings</title>

➝ **time() - 600, '/');**

13 </head>

**?>**

14 <body>

These two lines send cookies named

15

***font\_size***

16

<p>Your settings have been reset! Click

and ***font\_color***, each with

<a href="view\_settings.php">here</a> to

no value and an expiration time of 10

go back to the main page.</p>

minutes ago. As you did when creating

17

cookies, you must call the **setcookie()**

18 </body>

function before anything else is sent to

19 </html>

the Web browser.

**3.** Create the HTML head:

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

➝ **XHTML 1.0 Transitional//EN"**

**"http://www.w3.org/TR/xhtml1/**

 ➝ **DTD/xhtml1-transitional.dtd">**

**<html xmlns="http://www.w3.org/**

➝ **1999/xhtml" xml:lang="en"**

➝ **lang="en">**

**<head>**

**<meta**

**http-equiv="Content-Type"**

 ➝ **content="text/html;**

 ➝ **charset=utf-8"/>**

**<title>Reset Your Settings**

 ➝ **</title>**

**</head>**

246 Chapter

9

![Image 354](index-268_1.png)

![Image 355](index-268_2.png)

![Image 356](index-268_3.png)

**4.** Add the page’s body:

**<body>**

**<p>Your settings have been reset!**

➝ **Click <a href="view\_settings.php">**

➝ **here</a> to go back to the main**

➝ **page.</p>**

**</body>**

The body of this script merely tells

users that their settings have been

**B** When the **setcookie()** function is used with

a name but no value, the existing cookie of that

reset. A link is then provided to return

name is deleted. The expiration date in the past also

to the main page.

guarantees proper destruction of the existing cookie.

**5.** Complete the HTML:

**</html>**

**6.** Save the page as **reset.php**, place it

in the proper directory for your PHP-

enabled server, and test it in your Web

**C** The reset page sends two blank

browser

cookies and then displays this message.

**B**, **C**, and **D**.

To test this page, either click the

appropriate link in **view\_settings.php**

(Script 9.2) or just go to this page directly.

**Just as creating a cookie doesn’t take**

**effect until another page is loaded, deleting a**

**cookie doesn’t take effect until another page.**

**This is to say that you can delete a cookie on a**

**page but still access that cookie on it (because**

**the cookie was received by the page before**

**the delete cookie was sent).**

**D** After accessing the reset page,

PHP destroys the cookies **B**, which

**Just as creating cookies has mixed**

will have the effect of resetting the

**results using different browsers, the same**

**view\_settings.php** page to its

**applies to deleting them. Test your scripts**

default formatting.

**on many browsers and play with the**

**setcookie() settings to ensure the best**

**all-around compatibility.**

Cookies and Sessions 247

![Image 357](index-269_1.png)

[**What Are Sessions?**](#index_split_000.html#p8)

A session, like a cookie, provides a way

for you to track data for a user over a

series of pages. The difference between

the two—and this is significant—is that a

cookie stores the data on the client (in

the Web browser), whereas the session

data is stored on the server. Because of

this difference, sessions have numerous

**A** A session cookie being sent to the Web browser.

benefits over cookies:

■

Sessions are generally more secure,

**Script 9.5** How session data is stored in a file on

because the data isn’t transmitted

the server.

back and forth between the client

1

email|s:14:"me@example.com";

and server repeatedly.

loggedin|i:1292883103;

■

Sessions allow you to store more

information than you can in a cookie.

■

Sessions can be made to work even

**Choosing Between Sessions**

if the user doesn’t accept cookies in

**and Cookies**

their browser.

Sessions have many benefits over

When you start a session, PHP generates a

cookies, but there are still reasons why

random session ID. Each user’s session will

you would use the latter. Cookies have

these advantages over sessions:

have its own session ID, corresponding to

the name of the text file on the server that

. Marginally easier to create

stores the user’s session data (**Script 9.5**).

and retrieve

So that every PHP script on a site can

. Require slightly less work from

associate the same session data with a

the server

particular user, the session ID must be

. Normally persist over a longer

tracked as well. By default, this session ID

period of time

is sent to the Web browser as a cookie **A**.

As a rule of thumb, you should use

Subsequent PHP pages will use this cookie

cookies in situations where security is

to retrieve the session ID and access the

less of an issue and only a minimum

session information.

of data is being stored. If security’s a

Over the next few pages, you’ll see just

concern and there will be oodles of

information to remember, you’re best off

how easy sessions are to work with in PHP.

with sessions. Understand, though, that

using sessions may require a little more

effort in writing your scripts.

248 Chapter

9

[**Creating a Session**](#index_split_000.html#p8)

Creating, accessing, or deleting a session

begins with the **session\_start()** function.

This function will attempt to send a cookie

the first time a session is started, so it

absolutely must be called prior to any

HTML or white space being sent to the

Web browser. Therefore, on pages that

use sessions, you should call the **session\_**

**start()** function as one of the very first

lines in your script:

**<?php**

**session\_start();**

The first time a session is started, a random

session ID is generated and a cookie is

sent to the Web browser with a name of

***PHPSESSID*** (the session name) and a value

like ***4bcc48dc87cb4b54d63f99da23fb41e1***

(see **A** in the previous section).

Once the session has been started, you

can record data to it by assigning values

to the **$\_SESSION** array:

**$\_SESSION\['first\_name'\] = 'Sam';**

**$\_SESSION\['age'\] = 4;**

Unlike with other arrays you might use in

PHP, you should always treat this array as

an associative array. In other words, you

should explicitly use strings for the keys,

such as first\_name and age.

Each time a value is assigned to the

**$\_SESSION** array, PHP writes that data to

a temporary file stored on the server (see

Script 9.5).

To begin, you’ll rewrite the login script

from Chapter 8, this time storing the email

address in a session.

Cookies and Sessions 249

**To create a session:**

**Script 9.6** This script stores two values in the

session and then redirects the user to another

**1.** Open **login.php** (Script 8.13) in your

page, where the session values can be accessed.

text editor or IDE.

1

<?php // Script 9.6 - login.php #3

**2.** Before the **ob\_end\_clean()** line, add

2

/\* This page lets people log into the

the following (**Script 9.6**):

site (almost!). \*/

3

**session\_start();**

4

// Set the page title and include the

**$\_SESSION\['email'\] = $\_POST\['email'\];**

header file:

**$\_SESSION\['loggedin'\] = time();**

5 define('TITLE',

'Login');

6 include('templates/header.html');

To store values in a session, begin by

7

calling the **session\_start()** function.

8

// Print some introductory text:

9

print '<h2>Login Form</h2>

Although you normally have to call this

10

<p>Users who are logged in can

function first thing in a script (because

take advantage of certain features

it may attempt to send a cookie),

like this, that, and the other

that’s not required here because the

thing.</p>';

header file for this script begins output

11

12

// Check if the form has been

buffering (see Chapter 8).

submitted:

The session first stores the user’s

13

if ($\_SERVER\['REQUEST\_METHOD'\] == 'POST') {

14

submitted email address in **$\_SESSION**

15

// Handle the form:

**\['email'\]**. Then the timestamp of

16

if ( (!empty($\_POST\['email'\])) &&

when the user logged in is assigned

(!empty($\_POST\['password'\])) ) {

to **$\_SESSION\['loggedin'\]**. This value

17

18

if ( (strtolower($\_POST

is determined by calling the **time()**

\['email'\]) == 'me@example.com')

function, which returns the number of

&& ($\_POST\['password'\] ==

seconds that have elapsed since the

'testpass') ) { // Correct!

epoch (midnight on January 1, 1970).

19

20

// Do session stuff:

**3.** Save the file as **login.php** and place

**21**

**session\_start();**

it in the appropriate directory on your

**22 $\_SESSION\['email'\]**

**\=**

PHP-enabled computer.

**$\_POST\['email'\];**

**23 $\_SESSION\['loggedin'\]**

**\=**

This script should be placed in the

**time();**

same directory used in Chapter 8, as

24

it requires some of those other files.

25

// Redirect the user to the

welcome page!

26

ob\_end\_clean();

// Destroy the buffer!

27

header ('Location: welcome.php');

28

exit();

29

30

} else { // Incorrect!

31

32

print '<p>The submitted email

address and password do not

match those on file!<br />Go

back and try again.</p>';

code continues on next page

250 Chapter

9

![Image 358](index-272_1.jpg)

**Script 9.6** continued

**4.** Load the form in your Web browser to

ensure that it has no errors

33

**A**.

34 }

Don’t complete and submit the login

35

form yet, as the welcome page needs

36

} else { // Forgot a field.

to be updated prior to logging in.

37

38

print '<p>Please make sure you

enter both an email address and

**The php.ini configuration file includes**

a password!<br />Go back and try

**many session-related settings that you can**

again.</p>';

**tinker with if you have administrative-level**

39

**control over your server. Open the php.ini**

40 }

**file in a text editor and see the manual for**

41

**more information.**

42 } else { // Display the form.

43

**You can also alter some of the session**

44

print '<form action="login.php"

**settings using the ini\_set() function.**

method="post">

45

<p>Email Address: <input type="text"

**The session\_name() function lets you**

name="email" size="20" /></p>

**change the name of the session (instead of**

46

<p>Password: <input type="password"

**using the default *PHPSESSID*). It must be used**

name="password" size="20" /></p>

**before every session\_start() call, like so:**

47

<p><input type="submit" name=

"submit" value="Log In!" /></p>

**session\_name('YourVisit');**

48 </form>';

**session\_start();**

49

50 }

**The session\_set\_cookie\_params()**

51

**function alters the session cookie settings, like**

52

include('templates/footer.html');

**the expiration time, the path, and the domain.**

// Need the footer.

53 ?>

**The constant SID, short for Session ID,**

**stores a string in the format name=ID. An**

**example is PHPSESSID=4bcc48dc87cb4b54d**

**63f99da23fb41e1.**

**You can store any type of value—number,**

**string, array, or object—or any combination**

**thereof in your sessions.**

**A** The login form.

Cookies and Sessions 251

[**Accessing Session**](#index_split_000.html#p8)

**Script 9.7** You can access stored session values

using the **$\_SESSION** array, as long as your script

[**Variables**](#index_split_000.html#p8)

uses **session\_start()** first.

1

<?php // Script 9.7 - welcome.php #2

Now that you’ve stored values in a session,

2

/\* This is the welcome page. The user is

you need to know how to access them.

redirected here

The first step is to invoke the **session\_**

3

after they successfully log in. \*/

**start()**

4

function. This is necessary on

5

// Need the session:

every page that will make use of sessions,

**6 session\_start();**

whether it’s creating a new session or

7

accessing an existing one.

8

// Set the page title and include the

header file:

From there it’s simply a matter of

9

define('TITLE', 'Welcome to the J.D.

referencing the **$\_SESSION** variable as you

Salinger Fan Club!');

would any other array. With this in mind,

10 include('templates/header.html');

you’ll write another welcome page—similar

11

to the one from Chapter 8—that accesses

12 // Print a greeting:

the stored ***email*** and ***loggedin*** values.

13

print '<h2>Welcome to the J.D.

Salinger Fan Club!</h2>';

**14 print '<p>Hello, ' . $\_SESSION**

**To access session variables:**

**\['email'\] . '!</p>';**

**1.** Create a new PHP document in

15

16

// Print how long they've been

your text editor or IDE, to be named

logged in:

**welcome.php** (**Script 9.7**):

17

date\_default\_timezone\_set('America/

**<?php // Script 9.7 - welcome.php**

New\_York');

**18 print '<p>You have been logged**

**2.** Begin the session:

**in since: ' . date('g:i a',**

**session\_start();**

**$\_SESSION\['loggedin'\]) . '</p>';**

19

Even when you’re accessing session

20 // Make a logout link:

values, you should call the **session\_**

21

print '<p><a href="logout.php">Click here

**start()** function before any data is

to logout.</a></p>';

22

sent to the Web browser.

23

include('templates/footer.html');

**3.** Define a page title, and include the

// Need the footer.

HTML header:

24 ?>

**define('TITLE', 'Welcome to the**

➝ **J.D. Salinger Fan Club!');**

**include('templates/header.html');**

Because this page uses the same

template system developed in Chapter

8, it also uses the same header system.

252 Chapter

9

![Image 359](index-274_1.png)

**4.** Greet the user by email address:

**6.** Complete the content:

**print '<h2>Welcome to the J.D.**

**print '<p><a href="logout.php">**

➝ **Salinger Fan Club!</h2>';**

➝ **Click here to logout.</a></p>';**

**print '<p>Hello, ' . $\_SESSION**

The next script will provide logout

➝ **\['email'\] . '!</p>';**

functionality, so a link to it is added here.

To access the stored user’s address,

**7.** Include the HTML footer, and complete

refer to **$\_SESSION\['email'\]**. Here, that

the HTML page:

value is concatenated to the rest of the

**include('templates/footer.html');**

string that’s being printed out.

**?>**

**5.** Show how long the user has been

**8.** Save the file as **welcome.php**, place it

logged in:

in the proper directory for your PHP-

**date\_default\_timezone\_set**

enabled server, and test it (starting

➝ **('America/New\_York');**

with **login.php**, Script 9.6) in your

**print '<p>You have been logged**

Web browser **A**.

➝ **in since: ' . date('g:i a',**

➝ **$\_SESSION\['loggedin'\]) . '</p>';**

**To see whether a particular session**

To show how long the user has been

**variable exists, use isset($\_SESSION\[' *var*'\])**

logged in, refer to the **$\_SESSION**

**as you would to check if any other variable**

**\['loggedin'\]** variable. By using this as

**is set.**

the second argument sent to the **date()**

**Always remember that the data stored**

function, along with the appropriate

**in a session is being stored as plain text in an**

formatting parameters, you make the

**openly readable text file. Don’t be cavalier**

PHP script create text like 11:22 pm.

**about what gets stored in a session and never**

**store really sensitive information, such as**

Before using the **date()** function,

**credit card data, there.**

however, you need to set the default

time zone (this is also discussed in

**For added security, data can be**

**encrypted prior to storing it in a session and**

Chapter 8). If you want, after setting the

**decrypted upon retrieval. Doing so requires**

time zone here, you can remove the use

**the Mcrypt library and more advanced PHP**

of the same function from the footer file.

**knowledge, however.**

**A** After successfully logging in (using me@

example.com and testpass in the form), the user is

redirected to this page, which greets them using

the session values.

Cookies and Sessions 253

[**Deleting a Session**](#index_split_000.html#p8)

**Script 9.8** Deleting a session is a three-step

process: start the session, reset the array, and

destroy the session data.

It’s important to know how to delete a session,

just as it’s important to know how to delete

1

<?php // Script 9.8 - logout.php

a cookie: Eventually you’ll want to get rid of

2

/\* This is the logout page. It

destroys the session information. \*/

the data you’ve stored. Session data exists in

3

two places—in an array during the execution

4

// Need the session:

of the script and in a text file, so you’ll need to

**5 session\_start();**

delete both. But first you must begin with the

6

**session\_start()** function, as always:

7

// Delete the session variable:

**8 unset($\_SESSION);**

**session\_start();**

9

10 // Reset the session array:

Then, you clear the session variables by

**11 $\_SESSION = array();**

resetting the **$\_SESSION** array:

12

**$\_SESSION = array();**

13

// Define a page title and include the

header:

Finally, remove the session data from the

14 define('TITLE',

'Logout');

server (where it’s stored in temporary files).

15 include('templates/header.html');

To do this, use

16

17 ?>

**session\_destroy();**

18

19

<h2>Welcome to the J.D. Salinger Fan

With that in mind, let’s write **logout.php**,

Club!</h2>

which will delete the session, effectively

20 <p>You are now logged out.</p>

logging out the user.

21

<p>Thank you for using this site. We

hope that you liked it.<br />

**To delete a session:**

22 Blah, blah, blah...

23 Blah, blah, blah...</p>

**1.** Start a new PHP script in your text edi-

24

tor or IDE, to be named **logout.php**

25

<?php include('templates/

footer.html'); ?>

(**Script 9.8**).

**<?php // Script 9.8 - logout.php**

**2.** Begin the session:

**session\_start();**

Remember that you can’t delete a

session until you activate the session

using this function.

**3.** Reset the session array:

**$\_SESSION = array();**

As explained in Chapter 7, “Using

Arrays,” the **array()** function creates a

new, empty array. By assigning the result

of this function call to **$\_SESSION**, all the

existing key-value pairs in **$\_SESSION** will

be erased.

254 Chapter

9

![Image 360](index-276_1.png)

**4.** Destroy the session data on the server:

**session\_destroy();**

This step tells PHP to remove the actual

session file on the server.

**5.** Include the HTML header, and complete

this PHP section:

**define('TITLE', 'Logout');**

**A** The logout page destroys the session data.

**include('templates/header.html');**

**?>**

**6.** Make the page content:

**<h2>Welcome to the J.D. Salinger**

**Fan Club!</h2>**

**<p>You are now logged out.</p>**

**<p>Thank you for using this site.**

**We hope that you liked it.<br />**

**Blah, blah, blah...**

**Blah, blah, blah...</p>**

**7.** Include the HTML footer:

**<?php include('templates/footer.**

**html'); ?>**

**8.** Save the file as **logout.php**, place it in the

proper directory for your PHP-enabled

server, and test it in your Web browser

by clicking the link in **welcome.php** **A**.

**To delete an individual session value, use:**

**unset($\_SESSION\['var'\]);**

**The PHP module on the server will auto-**

**matically perform garbage collection based on**

**settings in its configuration. PHP uses garbage**

**collection to manually delete session files from**

**the server, with the assumption that they’re no**

**longer needed.**

**You can have PHP use sessions without**

**cookies, in which case the session ID must be**

**appended to every link in your site (so that**

**each page receives the session ID). If you**

**enable the use\_trans\_sid setting (in the**

**php.ini file), PHP will handle this for you.**

Cookies and Sessions 255

[**Review and Pursue**](#index_split_000.html#p8)

**Pursue**

■

Install the Firebug extension for Firefox,

If you have any problems with the review

if you have not already. Install Firefox

questions or the pursue prompts, turn

first, if you haven’t!

to the book’[s supporting forum (www.](http://www.LarryUllman.com/forum/)

■

[LarryUllman.com/forum/](http://www.LarryUllman.com/forum/) ).

Look up the PHP manual page for the

**setcookie()** function. Review the infor-

**Review**

mation and user comments there for

added instructions on cookies.

■

Where does a cookie store data? Where

■

Rewrite **customize.php** so that

does a session store data? Which is

the script also applies the user’s

generally more secure?

preferences. Hint: You need to take into

■

Name two debugging techniques when

account the fact that the cookies aren’t

trying to solve issues involving cookies.

available immediately after they’ve

■

How do the **path** and **domain**

been set. Instead, you would write

arguments to the **setcookie()** function

the CSS code using the **$\_GET** values

affect the accessibility of the cookie?

after the form has been submitted, the

**$\_COOKIE** values upon first arriving at

■

How do you delete a cookie?

the page (if the cookies exist), and the

■

What function must every page call if it

default values otherwise.

needs to assign or access session data?

■

Make the form in **customize.php** sticky,

■

Why do sessions also use cookies (by

so that it reflects the user’s current

default)?

choices.

■

Rewrite **welcome.php** so that the **print**

statement that greets the user by email

address uses double quotation marks.

■

For an added challenge, rewrite

**welcome.php** so that the **print**

statement that indicates how long the

user has been logged in also uses

double quotation marks. Hint: You’ll

need to use a variable.

■

Rewrite the last three scripts so that the

session uses a custom name.

256 Chapter

9

[**10**](#index_split_000.html#p8)

[Creating Functions](#index_split_000.html#p8)

Throughout this book, you’ve used dozens

of functions that provide much-needed

**In This Chapter**

functionality, such as **date()**, **setcookie()**,

and **number\_format()**. Whereas those

Creating and Using Simple Functions

258

functions have already been defined by

Creating and Calling Functions

PHP, here you’ll be creating your own.

That Take Arguments

265

However, once created, functions you’ve

Setting Default Argument Values

271

written and built-in PHP functions are used

in the same manner.

Creating and Using Functions

That Return a Value

274

Creating functions can save you oodles of

time as a programmer. In fact, they consti-

Understanding Variable Scope

279

tute a strong step in the process of creating

Review and Pursue

286

Web applications and building a solid library

of PHP code to use in future projects.

In this chapter, you’ll see how to write your

own functions that perform specific tasks.

After that, you’ll learn how to pass infor-

mation to a function, use default values

in a function, and have a function return a

value. You’ll also learn how functions and

variables work together.

[**Creating and Using**](#index_split_000.html#p8) 

[**Simple Functions**](#index_split_000.html#p8)

As you program, you’ll discover that you

use certain sections of code frequently,

either within a single script or over the

course of several scripts. Placing these

routines into a self-defined function can

save you time and make your programming

easier, especially as your Web sites

become more complex. Once you create

a function, the actions of that function take

place each time the function is called, just

as **print** sends text to the browser with

each use.

The syntax for creating a user-defined

function is

**function *function\_name*** **() {**

***statement(s)*****;**

**}**

For example:

**function whatever() {**

**print**

**'whatever';**

**}**

You can use roughly the same naming

conventions for functions as you do for

variables, just without the initial dollar

sign. Second to that is the suggestion that

you create meaningful function names,

just as you ought to write representative

variable names (**create\_header** would be

a better function name than **function1**).

Remember not to use spaces, though—

doing so constitutes two separate words

for the function name, which will result

in error messages (the underscore is a

logical replacement for the space). Unlike

variables, function names in PHP are not

case-sensitive, but you should still stick

with a consistent naming scheme.

258 Chapter

10

![Image 361](index-280_1.png)

Any valid PHP code can go within the

statement(s) area of the function, including

calls to other functions. There is also

no limit on the number of statements a

function contains, but make sure each

statement ends with a semicolon, just

as you would within the rest of the

PHP script. Functions can also contain

any combination of control structures:

conditionals and loops.

The exact formatting of a function isn’t

**A** These pull-down menus are created

important as long as the requisite elements

by a user-defined PHP function.

are there. These elements include the

word function, the function’s name, the

opening and closing parentheses, the

opening and closing brackets, and the

statement(s). It’s conventional to indent a

function’s statement(s) from the **function**

keyword line, for clarity’s sake, as you

would with a loop or conditional. In any

case, select a format style that you like

(which is both syntactically correct and

logically sound) and stick to it.

You call (or invoke) the function by referring

to it just as you do any built-in function. The

line of code

**whatever();**

will cause the statement part of the

previously defined function—the **print**

command—to be executed.

Let’s begin by creating a function that

generates month, day, and year pull-down

menus for a form **A**.

Creating Functions 259

**To create and call a basic function:**

**4.** Create the month pull-down menu:

**1.** Start a new PHP document in your text

**$months = array (1 => 'January',**

editor or IDE, to be named **menus.php**

➝ **'February', 'March', 'April',**

(**Script 10.1**):

➝ **'May', 'June', 'July', 'August',**

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

➝ **'September', 'October',**

➝ **'November', 'December');**

➝ **XHTML 1.0 Transitional//EN"**

**print '<select name="month">';**

**"http://www.w3.org/TR/xhtml1/**

**foreach ($months as $key =>**

 ➝ **DTD/xhtml1-transitional.dtd">**

**<html xmlns="http://www.w3.org/**

➝ **$value) {**

**print "\\n<option value=**

➝ **1999/xhtml" xml:lang="en"**

 ➝ **\\"$key\\">$value</option>";**

➝ **lang="en">**

**}**

**<head>**

**print '</select>';**

**<meta**

**http-equiv="content-type"**

 ➝ **content="text/html;**

To generate a list of months, first create

 ➝ **charset=utf-8" />**

an array of the month names, indexed

**<title>Date**

**Menus</title>**

numerically beginning at 1 for January.

**</head>**

When you specify the index for the first

**<body>**

array element, the others will follow

sequentially without the need to be

**2.** Begin the PHP section:

explicit in naming them.

**<?php // Script 10.1 - menus.php**

After the array has been created, the

**3.** Start defining a function:

initial **select** tag is printed out. Then, a

**function make\_date\_menus() {**

**foreach** loop runs through the **$months**

array. For each element in the array, the

The name of this function is ***make\_date\_***

HTML **option** tag is printed, using each

***menus***, which is both descriptive of what

element’s key (the numbers 1 through 12)

the function does and easy to remember.

as the **option** value and each element’s

value ( ***January*** through ***December***) as the displayed text. Each line is also

preceded by a newline character (**\\n**) so

that each option ends up on its own line

within the HTML source.

continues on page 262

260 Chapter

10

**Script 10.1** The function defined in this script creates three pull-down menus for a form.

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"

2 "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> 3

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en"> 4 <head>

5

<meta http-equiv="content-type" content="text/html; charset=utf-8" /> 6 <title>Date

Menus</title>

7 </head>

8 <body>

9

<?php // Script 10.1 - menus.php

10 /\* This script defines and calls a function. \*/

11

12 // This function makes three pull-down menus for the months, days, and years.

13 function make\_date\_menus() {

14

15

// Array to store the months:

16

$months = array (1 => 'January', 'February', 'March', 'April', 'May', 'June', 'July', 'August',

'September', 'October', 'November', 'December');

17

18

// Make the month pull-down menu:

19

print '<select name="month">';

20

foreach ($months as $key => $value) {

21 print

"\\n<option

value=\\"$key\\">$value</option>";

22 }

23 print

'</select>';

24

25

// Make the day pull-down menu:

26 print '<select name="day">';

27

for ($day = 1; $day <= 31; $day++) {

28

print "\\n<option value=\\"$day\\">$day</option>"; 29 }

30 print

'</select>';

31

32

// Make the year pull-down menu:

33

print '<select name="year">';

34

$start\_year = date('Y');

35

for ($y = $start\_year; $y <= ($start\_year + 10); $y++) {

36

print "\\n<option value=\\"$y\\">$y</option>"; 37 }

38 print

'</select>';

39

40 } // End of make\_date\_menus() function.

41

42 // Make the form:

43 print '<form action="" method="post">'; 44 make\_date\_menus();

45 print

'</form>';

46

47 ?>

48 </body>

49 </html>

Creating Functions 261

**5.** Create the day pull-down menu:

**print '<select name="day">';**

**for ($day = 1; $day <= 31; $day++) {**

**print "\\n<option value=**

 ➝ **\\"$day\\">$day</option>";**

**}**

**print '</select>';**

The day menu is a lot easier to create.

To do so, use a simple **for** loop, running

through the numbers 1 through 31.

**6.** Create the year pull-down menu:

**print '<select name="year">';**

**$start\_year = date('Y');**

**for ($y = $start\_year; $y**

➝ **<= ($start\_year + 10); $y++) {**

**print "\\n<option value=**

 ➝ **\\"$y\\">$y</option>";**

**}**

**print '</select>';**

To create the year pull-down menu,

start by using the **date()** function to get

the current year. Then create options

for this year plus the next 10, using a

**for** loop.

**7.** Close the function:

**} // End of make\_date\_menus()**

➝ **function.**

When you’re creating functions, it’s easy

to create parse errors by forgetting the

closing curly bracket. You may want to

add comments to help you remember

this final step.

**8.** Make the **form** tags, and call the function:

**print '<form action="" method=**

➝ **"post">';**

**make\_date\_menus();**

**print '</form>';**

262 Chapter

10

![Image 362](index-284_1.png)

The **print** statements are used to

create the HTML **form** tags. Without a

form, the date pull-down menus won’t

appear properly in the script.

Once you’ve created your function, you

simply have to call it by name (being

careful to use the exact spelling) to

make the function work. Be sure to

include the parentheses as well.

**9.** Complete the PHP and HTML:

**?>**

**</body>**

**</html>**

**10.** Save the file as **menus.php**, place it in the

proper directory for your PHP-enabled

server, and run it in your Web browser **A**.

**11.** If you want, check out the HTML source

of the page to see what was dynami-

cally generated **B**.

continues on next page

**B** The source of the page shows the HTML created by the **print** statements in the **make\_date\_menus()** function.

Creating Functions 263

![Image 363](index-285_1.png)

**If you see a “Call to undefined function:**

**some\_function…” error message, it means**

**you’re trying to call a function that doesn’t**

**exist C. If you’re trying to call a PHP func-**

**tion, either you misspelled the name or it’s**

**not supported on your version of PHP. Check**

**the PHP manual for more. If you’re calling a**

**user-defined function when you see this error,**

**either it hasn’t been defined or you’ve mis-**

**spelled it. Recheck your spelling in both the**

**definition of the function and its usage to see**

**if you made a mistake.**

**The function\_exists() function**

**returns TRUE or FALSE based on whether a**

**function exists in PHP. This applies to both**

**user-defined functions and those that can be**

**built into PHP:**

**if (function\_exists('some\_function'))**

➝ **{ …**

**Although you aren’t required to, I recom-**

**mend that you habitually define your functions**

**at the beginning of a script (or in an included**

**file), rather than at the end of the script.**

**Some people prefer this syntax for laying**

**out their functions:**

**function function\_name()**

**{**

**statement(s);**

**}**

**User-defined functions add extra**

**memory requirements to your PHP scripts, so**

**you should be judicious in using them. If you**

**find that your function merely calls another**

**PHP function or has but one line of code, it’s**

**probably not the best use of this capability.**

**C** This error means that the PHP script does not have

access to a function defined under the given name. In this

case, the problem is due to a missing “s” in the function call:

**make\_date\_menus()** vs. **make\_date\_menu()**.

264 Chapter

10

[**Creating and Calling**](#index_split_000.html#p8)

[**Functions That**](#index_split_000.html#p8)

[**Take Arguments**](#index_split_000.html#p8)

Although being able to create a simple

function is useful, writing one that takes

input and does something with that input

is even better. The input a function takes

is called an argument (or a parameter).

This is a concept you’ve seen before:

the **sort()** function takes an array as an

argument, which the function then sorts.

The syntax for writing functions that take

arguments is as follows:

**function *function\_name*($ *arg1*,**

➝ **$ *arg2*, …){**

***statement(s)*****;**

**}**

The function’s arguments are in the form

of variables that are assigned the values

sent to the function when you call it. The

variables are defined using the same

naming rules as any other variable in PHP:

**function make\_full\_name($first,**

➝ **$last) {**

**print $first . ' ' . $last;**

**}**

Functions that take input are called much

like those that don’t—you just need to

remember to pass along the necessary

values. You can do this either by passing

variables:

**make\_full\_name($fn, $ln);**

or by sending literal values, as in

**make\_full\_name('Larry', 'Ullman');**

or some combination thereof:

**make\_full\_name('Larry', $ln);**

continues on next page

Creating Functions 265

![Image 364](index-287_1.png)

![Image 365](index-287_2.png)

The important thing to note is that arguments

are passed quite literally: The first variable

in the function definition is assigned the first

value in the call line, the second function

variable is assigned the second call value,

and so forth **A**. Functions aren’t smart

enough to intuitively understand how you

meant the values to be associated. This is

also true if you fail to pass a value, in which

case the function will assume that value is

null (null isn’t the mathematical 0, which is

actually a value, but closer to the idea of the

word nothing). The same thing applies if a

function takes four arguments and you pass

three—the fourth will be null, which may

create an error **B**.

**A** How values in function calls are assigned to function arguments.

**B** As with any function (user-defined or built into PHP), passing an incorrect number of arguments when calling it yields warnings.

266 Chapter

10

![Image 366](index-288_1.png)

![Image 367](index-288_2.png)

To demonstrate functions that take

arguments, let’s create a more interesting

example. In Chapter 8, “Creating Web

Applications,” you learned how to make

forms “sticky”: having them remember their

values from previous submissions. The

code for a sticky text input might be

**First Name: <input type="text"**

➝ **name="first\_name" size="20"**

**C** These three form elements are created by a

user-defined function.

➝ **value="<?php if (isset($\_POST**

➝ **\['first\_name'\])) { print**

➝ **htmlspecialchars($\_POST**

➝ **\['first\_name'\]); } ?>" />**

Since many forms, such as **register.php**

from Chapter 8, repeatedly use similar

code, you have a good candidate for a

user-defined function.

This next script will define and call a function

that creates sticky text inputs. The function

will take one argument for the input’s

**D** The form elements reflect the values entered

by the user.

name, and another for the input’s label (its

textual prompt). The function will be called

multiple times by the script to generate

multiple inputs **C**. Upon form submission,

the previously entered values will be

remembered **D**.

Creating Functions 267

**To create and call a function**

**that takes an argument:**

**1.** Start a new PHP document in your text

editor or IDE, to be named **sticky1.php**

(**Script 10.2**):

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

➝ **XHTML 1.0 Transitional//EN"**

**"http://www.w3.org/TR/xhtml1/**

 ➝ **DTD/xhtml1-transitional.dtd">**

**<html xmlns="http://www.w3.org**

➝ **/1999/xhtml" xml:lang="en"**

➝ **lang="en">**

**<head>**

**<meta**

**http-equiv="content-type"**

 ➝ **content="text/html;**

 ➝ **charset=utf-8" />**

**<title>Sticky Text Inputs**

 ➝ **</title>**

**</head>**

**<body>**

**2.** Begin the PHP section:

**<?php // Script 10.2 – sticky1.php**

**3.** Start defining a function:

**function make\_text\_input($name,**

➝ **$label) {**

The **make\_text\_input()** function requires

two arguments, which will be assigned

to the **$name** and **$label** variables.

**4.** Print an opening paragraph and a

**label** tag:

**print '<p><label>' . $label . ': ';**

The code being generated by this

function will be essentially like that just

indicated (and in Chapter 8), but it will

be wrapped in a paragraph tag and

the input’s label will be formally placed

within **label** tags. The value of the label

(e.g., ***First Name***) will be passed to the

function when the function is called.

continues on page 270

268 Chapter

10

**Script 10.2** The **make\_text\_input()** function takes two arguments, for the input's name and label.

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"

2 "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> 3

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en"> 4 <head>

5

<meta http-equiv="content-type" content="text/html; charset=utf-8" /> 6

<title>Sticky Text Inputs</title>

7 </head>

8 <body>

9

<?php // Script 10.2 - sticky1.php

10 /\* This script defines and calls a function that creates a sticky text input. \*/

11

12 // This function makes a sticky text input.

13 // This function requires two arguments be passed to it.

**14 function make\_text\_input($name, $label) {**

15

16

// Begin a paragraph and a label:

17

print '<p><label>' . $label . ': ';

18

19

// Begin the input:

20

print '<input type="text" name="' . $name . '" size="20" '; 21

22

// Add the value:

23

if (isset($\_POST\[$name\])) {

24

print ' value="' . htmlspecialchars($\_POST\[$name\]) . '"'; 25 }

26

27

// Complete the input, the label and the paragraph:

28 print ' /></label></p>';

29

30 } // End of make\_text\_input() function.

31

32 // Make the form:

33 print '<form action="" method="post">'; 34

35 // Create some text inputs:

**36 make\_text\_input('first\_name', 'First Name');**

**37 make\_text\_input('last\_name', 'Last Name');**

**38 make\_text\_input('email', 'Email Address');**

39

40 print '<input type="submit" name="submit" value="Register!" /></form>'; 41

42 ?>

43 </body>

44 </html>

Creating Functions 269

**5.** Begin the text input:

case the form will automatically be

submitted back to the same page.

**print '<input type="text"**

➝ **name="' . $name . '" size="20" ';**

To create a “first name” input, call the

**make\_text\_input()** function, passing it

The PHP **print** statement just creates

the name the input should have and an

the HTML **input** tag, but the value of

appropriate label.

the tag’s **name** attribute will come from

the **$name** variable (assigned a value

**9.** Create two more inputs:

when the function is called, such as

**make\_text\_input('last\_name', 'Last**

***first\_name***).

➝ **Name');**

**6.** If applicable, add the input’s preset value:

**make\_text\_input('email', 'Email**

➝ **Address');**

**if (isset($\_POST\[$name\])) {**

**print ' value="' .**

Now the script has used the same

**vhtmlspecialchars($\_POST**

function three times, in three different

 ➝ **\[$name\]) . '"';**

ways. The result will be three distinct

**}**

text inputs.

The code in Step 5 didn’t actually

**10.** Complete the form:

complete the text input (the closing **/>**

**print '<input type="submit"**

wasn’t created), so another clause—

➝ **name="submit" value=**

specifically **value="whatever"** —can

➝ **"Register!" /></form>';**

still be added. But that clause should

The form needs a submit button in

only be added if **$\_POST\[' *input\_name*'\]**

order to test the sticky feature.

is set, so the conditional checks for

that. As with the code in Chapter 8, the

**11.** Complete the PHP and HTML:

value is printed only after being run

**?>**

through **htmlspecialchars()**.

**</body>**

**7.** Complete the input, the label, the para-

**</html>**

graph, and the function:

**12.** Save the file as **sticky1.php**, place it

**print ' /></label></p>';**

in the proper directory for your PHP-

**} // End of make\_text\_input()**

enabled server, and run it in your Web

➝ **function.**

browser **C** and **D**.

**8.** Make the **form** tags and call the

function:

**You can define as many functions as you**

**want, not just one per script as the examples**

**print '<form action=""**

**in this chapter portray.**

➝ **method="post">';**

**make\_text\_input('first\_name',**

**There are no limits on how many argu-**

➝ **'First Name');**

**ments a function can take.**

It’s important that the form uses the

**Once you’ve defined your own functions**

POST method, as the function checks

**like this, you can place them in an external**

**file and then require that file when you need**

for existing values in **$\_POST**. You can

**access to the functions.**

actually omit an **action** value, in which

270 Chapter

10

![Image 368](index-292_1.png)

![Image 369](index-292_2.png)

The default arguments must always be

[**Setting Default**](#index_split_000.html#p8)

written after the other standard arguments

(those without default values). This is because

[**Argument Values**](#index_split_000.html#p8)

PHP directly assigns values to arguments

PHP allows functions to have default

in the order they’re received from the call

argument values: just assign a value to

line. Thus, it isn’t possible to omit a value for

the argument in the function definition:

the first argument but include one for the

**function greeting($who = 'world') {**

second. For example, suppose you have

**print "<p>Hello, $who!</p>";**

**function calculate\_total($qty,**

**}**

➝ **$price = 20.00, $tax = 0.06) {...**

Such a function will use the preset values

If you call the function with the line

unless it receives a value that then

**calculate\_total(3, 0.07);**

overwrites the default. In other words, by

setting a default value for an argument,

with the intention of setting **$qty** to 3,

you render that particular argument

leaving **$price** at 20.00, and changing the

optional when calling the function. You’d

**$tax** to 0.07, there will be problems.

set an argument’s default value if you

The end result will be that **$qty** is set to 3,

wanted to assume a certain value but still

**$price** is set to 0.07, and **$tax** remains at

allow for other possibilities **A**:

0.06 **B**, which isn’t the desired outcome.

**greeting();**

The proper way to achieve that effect

**greeting('Zoe');**

would be to code

(Note: This isn’t really a good use of a user-

**calculate\_total(3, 20.00, 0.07);**

defined function, or a default argument value,

Let’s rework the **make\_text\_input()**

but it’s easily understood as an example.)

function to incorporate the notion of

setting default argument values.

**A** Calling the function without any arguments

uses the default value (the first greeting);

calling it with an argument provided means

that value will be used instead (the second).

**B** Because of the way function arguments work, you cannot “skip” an argument when calling a function.

Creating Functions 271

**To write a function that**

**uses default values:**

**1.** Open **sticky1.php** (Script 10.2) in your

text editor or IDE, if it isn’t open already.

**2.** Add a third argument with a default

value to the **make\_text\_input()**

function (**Script 10.3**):

**function make\_text\_input($name,**

➝ **$label, $size = 20) {**

Although I like the cleanliness of hav-

ing all text inputs be the same size, a

person’s last name and email address is

often longer than their first name, so an

adjustable size would be better. By tak-

ing the input’s size as an argument, this

will be possible. But the size will have

a default value, making it an optional

argument. If three arguments are sent

to the function, then **$size** will be set to

the third value instead of the default.

**Script 10.3** The function now takes three arguments, but only two of them are required. If no **$size** is passed to the function, its value will be 20.

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"

2 "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> 3

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en"> 4 <head>

5

<meta http-equiv="content-type" content="text/html; charset=utf-8" /> 6

<title>Sticky Text Inputs</title>

7 </head>

8 <body>

9

<?php // Script 10.3 - sticky2.php

10 /\* This script defines and calls a function that creates a sticky text input. \*/

11

12 // This function makes a sticky text input.

13 // This function requires two arguments be passed to it.

14 // A third argument is optional (it has a default value).

**15 function make\_text\_input($name, $label, $size = 20) {**

16

17

// Begin a paragraph and a label:

18

print '<p><label>' . $label . ': ';

19

code continues on next page

272 Chapter

10

![Image 370](index-294_1.png)

**Script 10.3** continued

**3.** Change the creation of the input so that

it uses the **$size** variable:

20

// Begin the input:

**21**

**print '<input type="text" name="' .**

**print '<input type="text"**

**$name . '" size="' . $size . '" ';**

➝ **name="' . $name . '"**

22

➝ **size="' . $size . '" ';**

23

// Add the value:

24

if (isset($\_POST\[$name\])) {

**4.** Change the function calls to vary

25

print ' value="' . htmlspecialchars

the sizes:

($\_POST\[$name\]) . '"';

26 }

**make\_text\_input('first\_name',**

27

➝ **'First Name');**

28

// Complete the input, the label and

**make\_text\_input('last\_name',**

the

paragraph:

➝ **'Last Name', 30);**

29

print ' /></label></p>';

**make\_text\_input('email', 'Email**

30

31 } // End of make\_text\_input() function.

➝ **Address', 50);**

32

Now the first input will use the default

33 // Make the form:

size, and the others will be longer.

34 print '<form action="" method="post">'; 35

**5.** Save the script as **sticky2.php**, place

36 // Create some text inputs:

it in the proper directory of your PHP-

**37 make\_text\_input('first\_name',**

**'First**

enabled server, and test it in your

**Name');**

**38 make\_text\_input('last\_name',**

**'Last**

Web browser **C**.

**Name',**

**30);**

**39 make\_text\_input('email', 'Email**

**To pass no value to a function for a**

**Address',**

**50);**

**particular argument, use an empty string (‘’)**

40

**or the word NULL (without quotes). Either of**

41 print '<input type="submit" name="submit"

**these values will override the default value, if**

value="Register!"

/></form>';

**one is established.**

42

43 ?>

**As mentioned way back in Chapter 1,**

44 </body>

**“Getting Started with PHP,” the PHP manual**

45 </html>

**marks optional function arguments using**

**square brackets. For example, when you use**

**the number\_format() function, the number**

**of decimals to round to is optional:**

**string number\_format(float number**

➝ **\[, int decimals\])**

**C** Now the function is capable

of changing the size of the

input, based on an argument.

If no value is provided for that

argument, the default size is

used instead (the first input).

Creating Functions 273

![Image 371](index-295_1.png)

![Image 372](index-295_2.png)

[**Creating and Using**](#index_split_000.html#p8) 

[**Functions That**](#index_split_000.html#p8)

[**Return a Value**](#index_split_000.html#p8)

**A** This simple form takes

two values on which

calculations will be made.

Functions do more than take arguments;

they can also return values. Doing so

requires just two more steps. First, you use

the **return** statement within the function.

Second, you use the output somehow

when you call the function. Commonly,

you’ll assign the returned value to a

variable, but you can also, for example,

directly print the output. Here is the

basic format for a function that takes two

**B** The result of the calculation,

arguments and returns a value:

which takes place within a user-

**function make\_full\_name($first,**

defined function.

➝ **$last) {**

**$name = $first . ' ' . $last;**

**return**

**$name;**

**}**

This function could be used like so:

**$full\_name = make\_full\_name($fn, $ln);**

There the returned value of the function

is assigned to a variable. Here it’s printed

immediately:

**print make\_full\_name($fn, $ln)**

To best demonstrate this concept, let’s

create a function that performs a simple

calculation and formats the result. This script

will display an HTML form where a user

enters a quantity and price **A**. When the

form is submitted (back to this same page),

a total value will be calculated and printed **B**.

274 Chapter

10

**To create and use a function**

**that returns a value:**

**1.** Create a new PHP document in

your text editor or IDE, to be named

**calculator.php** (**Script 10.4**):

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

➝ **XHTML 1.0 Transitional//EN"**

**"http://www.w3.org/TR/xhtml1/**

 ➝ **DTD/xhtml1-transitional.dtd">**

**<html xmlns="http://www.w3.org/**

➝ **1999/xhtml" xml:lang="en"**

➝ **lang="en">**

**<head>**

**<meta**

**http-equiv="Content-Type"**

 ➝ **content="text/html;**

 ➝ **charset=utf-8"/>**

**<title>Cost**

**Calculator</title>**

**</head>**

**<body>**

continues on next page

**Script 10.4** This script both displays and handles an HTML form in order to perform some basic calculations.

The script uses a function that takes two arguments and returns a single value.

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"

2 "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> 3

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en"> 4 <head>

5

<meta http-equiv="Content-Type" content="text/html; charset=utf-8"/> 6 <title>Cost

Calculator</title>

7 </head>

8 <body>

9

<?php // Script 10.4 - calculator.php

10 /\* This script displays and handles an HTML form.

11 It uses a function to calculate a total from a quantity and price. \*/

12

13 // This function performs the calculations.

14 function calculate\_total ($quantity, $price) {

15

16

$total = $quantity \* $price; // Calculation

17

$total = number\_format ($total, 2); // Formatting

18

**19**

**return $total; // Return the value.**

20

21 } // End of function.

22

code continues on next page

Creating Functions 275

**2.** Begin the PHP code:

**<?php // Script 10.4 -**

➝ **calculator.php**

**3.** Define the function:

**function calculate\_total**

➝ **($quantity, $price) {**

**$total = $quantity \* $price;**

**$total = number\_format**

 ➝ **($total, 2);**

**return**

**$total;**

**}**

This function takes two arguments—

a quantity and a price—and multiplies

them to create a total. The total value

is then formatted before it’s returned

by the function.

Although this may seem like a silly

use of a function, the benefits of

putting even a one-step calculation

into a function are twofold: First, the

**Script 10.4** continued

23 // Check for a form submission:

24 if ($\_SERVER\['REQUEST\_METHOD'\] == 'POST') {

25

26

// Check for values:

27

if ( is\_numeric($\_POST\['quantity'\]) AND is\_numeric($\_POST\['price'\]) ) {

28

29

// Call the function and print the results:

**30**

**$total = calculate\_total($\_POST\['quantity'\], $\_POST\['price'\]);** 31

print "<p>Your total comes to $<span style=\\"font-weight: bold;\\">$total</span>.</p>"; 32

33

} else { // Inappropriate values entered.

34

print '<p style="color: red;">Please enter a valid quantity and price!</p>'; 35 }

36

37 }

38 ?>

39 <form action="calculator.php" method="post"> 40 <p>Quantity: <input type="text" name="quantity" size="3" /></p> 41

<p>Price: <input type="text" name="price" size="5" /></p> 42

<input type="submit" name="submit" value="Calculate!" /> 43 </form>

44 </body>

45 </html>

276 Chapter

10

calculation will be easier to find and

**Returning Multiple Values**

modify at a later date with your function

located at the beginning of your script

User-defined functions frequently return

instead of hidden in the rest of the

just a single value but can return multiple

code; and second, should you want to

values by using arrays. Here’s how you

go about this:

repeat the action again in a script, you

can do so without duplicating code.

**function some\_function($a1, $a2) {**

**// Do whatever.**

**4.** Begin the conditional to see if the

**return array($v1, $v2);**

form was submitted:

**}**

**if ($\_SERVER\['REQUEST\_METHOD'\] ==**

Then, to call this function, use the **list()**

➝ **'POST') {**

function to assign the array elements to

Because this page both displays

individual variables:

and handles the HTML form, it has a

**list($var1, $var2) =**

conditional that checks how the page is

➝ **some\_function($p1,$p2);**

being requested. If it’s a POST request,

The end result is that **$v1** from the

that means the form has been submitted.

function is assigned to **$var1** in the

**5.** Validate the form data and use the

PHP script, and **$v2** from the function

function:

is assigned to **$var2**.

**if ( is\_numeric($\_POST\['quantity'\])**

➝ **AND is\_numeric($\_POST\['price'\]) ) {**

**$total = calculate\_total**

 ➝ **($\_POST\['quantity'\],**

 ➝ **$\_POST\['price'\]);**

**print "<p>Your total comes**

 ➝ **to $<span style=\\"font-weight:**

 ➝ **bold;\\">$total</span>.</p>";** This part of the PHP code—which

handles the form if it has been

submitted—first checks that a numeric

quantity and price were entered. If

so, the total is determined by calling

the **calculate\_total()** function and

assigning the result to the **$total**

variable. This result is then printed out.

continues on next page

Creating Functions 277

**6.** Complete the conditionals:

**8.** Complete the HTML page:

**} else {**

**</body>**

**print '<p style="color:**

**</html>**

 ➝ **red;">Please enter a valid**

**9.** Save the page as **calculator.php**,

 ➝ **quantity and price!</p>';**

place it in the proper directory for your

**}**

PHP-enabled server, and test it in your

**}**

Web browser **B**.

If either of the form variables was

not properly submitted, a message is

**You can have only one return statement**

printed indicating that. The final curly

**executed in a function, but the same function**

bracket closes the form submission

**can have multiple return statements. As an**

conditional.

**example, you may want to write a function**

**that checks for a condition and returns a value**

A little CSS is applied to both printed

**indicating whether the condition was satisfied.**

messages (here and in Step 5).

**In such a case, the function might contain:**

**7.** Display the HTML form:

**if ( *condition*) {**

**?>**

**return**

**TRUE;**

**} else {**

**<form action="calculator.php"**

**return**

**FALSE;**

➝ **method="post">**

**}**

**<p>Quantity: <input type="text"**

 ➝ **name="quantity" size="3" /></p>** **The result returned by the function is**

**<p>Price: <input type="text"**

**either TRUE or FALSE, indicating whether the**

**stated condition was met.**

 ➝ **name="price" size="5" /></p>**

**<input type="submit"**

 ➝ **name="submit"**

 ➝ **value="Calculate!" />**

**</form>**

The form itself is quite simple,

requesting two different values from

the user **A**. Because this form is

created outside of the main submission

conditional, the form will always be

displayed by the page **B**.

278 Chapter

10

![Image 373](index-300_1.png)

![Image 374](index-300_2.png)

![Image 375](index-300_3.png)

![Image 376](index-300_4.png)

![Image 377](index-300_5.png)

![Image 378](index-300_6.png)

Functions, though, create a new level of

[**Understanding**](#index_split_000.html#p8)

scope. Function variables—the arguments of

a function as well as any variables defined

[**Variable Scope**](#index_split_000.html#p8)

within the function—exist only within that

The concept of variable scope wasn’t

function and aren’t accessible outside of

introduced earlier because without an

it (that is, they’re local variables with local

understanding of functions, scope makes

scope). Likewise, a variable from outside a

little sense. Now that you are acquainted

function is not available within the function,

with functions, this section will revisit the

by default **A**. Even when a variable is

topic of variables and discuss in some

used as an argument to a function call,

detail just how variables and functions

that variable’s value is being passed to the

work together.

function, not the variable itself.

As you saw in the second section of this

You can, however, make a variable external

chapter, “Creating and Calling Functions

to a function available within the function

That Take Arguments,” you can send

by using the **global** statement. The

variables to a function by passing them

**global** statement roughly means, “I want

as arguments. However, you can also

this variable within the function to refer

reference an external variable from within

to the same named variable outside of

a function using the **global** statement. This

the function.” In other words, the **global**

is possible because of variable scope. The

statement turns a local variable with local

scope of a variable is the realm in which it

scope into a global variable with global

exists. By default, the variables you write

scope. Any changes made to the variable

in a script exist for the life of that script.

within the function are also reflected by the

Conversely, environment variables, such

variable outside of the function, without

as **$\_SERVER\['PHP\_SELF'\]**, exist throughout

using the **return** command (assuming the

every PHP script on the server.

function is called, that is).

**A** Adding function definitions to a script adds another area of variable scope.

Creating Functions 279

The syntax of the **global** statement is

as follows:

**function *function\_name*($args) {**

**global**

**$variable;**

***statement(s)*****;**

**}**

There is another issue regarding functions

and variables: Because of variable scope, a

local variable within a function is a different

entity (perhaps with a different value) than

a variable outside of the function, even

if the two variables use the exact same

name. Let’s look at this more explicitly…

Say you have:

**function test($arg) {**

**// Do whatever.**

**}**

**$var = 1;**

**test($var);**

When the function is called, the value of

**$var** will be assigned **$arg**, so their values

are the same but their names are different

and they are different variables. However,

if the name of the argument in the function

is also **$var**—

**function test($var) {**

**// Do whatever.**

**}**

**$var = 1;**

**test($var);**

—then the **$var** variable within the function

is assigned the same value as the original

**$var** outside of the function—but they’re

still two separate variables. The one has

a scope within the function, and the other

has a scope outside of it. This means that

you can use the same name for variables in

the function as exist outside of the function

without conflict. Just remember they

aren’t the same variable. What happens

280 Chapter

10

![Image 379](index-302_1.png)

![Image 380](index-302_2.png)

to a variable’s value within a function only

affects that variable within the function. As

**B** Changes to a local variable

inside a function have no effect on

an example **B**:

a similarly named global variable.

**function add\_one($n) {**

**$n++;**

**C** Changes made to a global

**print 'Added one!<br />';**

variable inside of a function will

**}**

impact the variable outside of

that function.

**$n = 1;**

**print "\\$n equals $n<br />";**

**add\_one($n);**

**print "\\$n equals $n<br />";**

This is all true unless you use the **global**

statement, which does make the two

variables the same **C**:

**function add\_one() {**

**global $n; // Same!**

**$n++;**

**print 'Added one!<br />';**

**}**

**$n = 1;**

**print "\\$n equals $n<br />";**

**add\_one();**

**print "\\$n equals $n<br />";**

Note that in this case, the variable’s value

no longer needs to be passed to the

function either.

To demonstrate variable scope, let’s

rework the **calculator.php** script using

the **global** statement.

Creating Functions 281

**To use the global statement:**

**1.** Open **calculator.php** (Script 10.4)

in your text editor or IDE, if it is not

already open.

**2.** Before the function definition, add the

following (**Script 10.5**):

**$tax = 8.75;**

This line creates a **$tax** variable with

a set value that will be used in the

cost calculations. It’s assigned a value

outside of the function because it will be

used later in the main body of the script.

**Script 10.5** The function in this script can use the **$tax** variable—even though it hasn't been passed to the function—thanks to the **global** statement.

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"

2 "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> 3

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en"> 4 <head>

5

<meta http-equiv="Content-Type" content="text/html; charset=utf-8"/> 6 <title>Cost

Calculator</title>

7 </head>

8 <body>

9

<?php // Script 10.5 - calculator.php #2

10 /\* This script displays and handles an HTML form.

11 It uses a function to calculate a total from a quantity, price, and tax rate. \*/

12

13 // Define a tax rate:

**14 $tax = 8.75;**

15

16 // This function performs the calculations.

17 function calculate\_total ($quantity, $price) {

18

**19 global**

**$tax;**

20

21

$total = $quantity \* $price; // Calculation

**22**

**$taxrate = ($tax / 100) + 1;**

**23**

**$total = $total \* $taxrate; // Add the tax.**

24

$total = number\_format ($total, 2); // Formatting

25

26

return $total; // Return the value.

27

28 } // End of function.

29

code continues on next page

282 Chapter

10

**3.** Within the function definition, add a **global** statement:

**global $tax;**

This statement tells the function to

incorporate the same **$tax** variable

as the one that exists outside of

the function.

**4.** Before the **$total** in the function is

formatted, recalculate the value using

the tax rate:

**$taxrate = ($tax / 100) + 1;**

**$total = $total \* $taxrate;**

To add the tax to the total value, you

start by dividing the tax by 100 to create

a percentage. Then you add 1 to this

value to get a multiplier. This result is

then multiplied by the total to come up

with the new, final total.

continues on next page

**Script 10.5** continued

30 // Check for a form submission:

31 if (isset($\_POST\['submitted'\])) {

32

33

// Check for values:

34

if ( is\_numeric($\_POST\['quantity'\]) AND is\_numeric($\_POST\['price'\]) ) {

35

36

// Call the function and print the results:

37

$total = calculate\_total($\_POST\['quantity'\], $\_POST\['price'\]);

**38**

**print "<p>Your total comes to $<span style=\\"font-weight: bold;\\">$total</span>,**

**including the $tax percent tax rate.</p>";**

39

40

} else { // Inappropriate values entered.

41

print '<p style="color: red;">Please enter a valid quantity and price!</p>'; 42 }

43

44 }

45 ?>

46 <form action="calculator.php" method="post"> 47 <p>Quantity: <input type="text" name="quantity" size="3" /></p> 48 <p>Price: <input type="text" name="price" size="5" /></p> 49

<input type="submit" name="submit" value="Calculate!" /> 50

<input type="hidden" name="submitted" value="true" /> 51 </form>

52 </body>

53 </html>

Creating Functions 283

![Image 381](index-305_1.png)

![Image 382](index-305_2.png)

Notice that you use a **$taxrate**

variable (based on **$tax**) to perform

these calculations. This is because

you’ll print out the value of **$tax** later,

and any changes made to it here will be

reflected (because it’s a global variable).

**D** Run the form again…

**5.** Alter the main **print** line (after the

function call) so that it prints the tax

rate as well:

**print "<p>Your total comes to**

➝ **$<span style=\\"font-weight:**

➝ **bold;\\">$total</span>, including**

➝ **the $tax percent tax rate.</p>";**

The **$tax** variable defined at the

beginning of the script is printed out

at the end. If you hadn’t used the

**$taxrate** variable within the function

and made the alterations to the global

**$tax** instead, those calculations would

be reflected in the value printed here.

**6.** Save the script, place it in the proper

directory for your PHP-enabled server,

and test it in your Web browser **D**

and **E**.

**E** …and the calculation now makes use of a global **$tax** variable.

284 Chapter

10

 **Constants and the superglobal arrays**

**Function Design Theory**

**($\_GET, $\_POST, $\_COOKIE, and $\_SESSION)**

**have the added benefit that they’re always**

Understanding the syntax for defining

**available inside functions without requiring**

your own functions is important, but you

**the global statement (which is why they are**

also need to understand good function

**called superglobals).**

design theory. A proper user-defined

function should be easily reusable, and

**Each function has its own, separate**

**local scope.**

be likely to be reused (i.e., if a Web site

only ever calls a function once, there’s

no need for it). There should also be a

“black box” mentality about the function:

A programmer shouldn’t need to know

about the internals of a function in order

to use it properly. As an example of this,

think of any PHP function: You probably

don’t know what the underlying function

code does specifically, but you can still

tap into its power.

In support of the “black box” approach,

proper function design suggests that

you should be extremely cautious

when using global variables. Arguably

(pun!), a function should be passed all

the information it needs, so that global

variables—including the superglobals

and constants—are not required.

Functions should also not make

assumptions either, like **make\_text\_**

**input()**, which assumes the form was

submitted using the POST method.

By writing functions that neither rely upon

global variables nor make assumptions as

to what outside of the function is true, you

make the function more independent and

portable—in short, better.

Creating Functions 285

[**Review and Pursue**](#index_split_000.html#p8)

**Pursue**

■  Make the function in **menus.php** take

If you have any problems with the review

arguments to indicate the starting year

questions or the pursue prompts, turn

and the number of years to generate.

to the book’[s supporting forum (www.](http://www.LarryUllman.com/forum/)

Make the later argument have a default

[LarryUllman.com/forum/ ).](http://www.LarryUllman.com/forum/)

value. Then rewrite the function body

so that it uses these values in the year

**Review**

**for** loop.

■

What is the basic syntax of a user-

■  Rewrite the **make\_text\_input()** func-

defined function?

tion so that it can be told whether to

■

What naming rules must your own

look for an existing value in either

functions abide by?

**$\_POST** or **$\_GET**.

■

What naming rules must function

■  Create a variation on the **make\_text\_**

arguments abide by?

**input()** function that can create a text

input or a password input, depending

■

How do you provide a default value for

upon how the function is called.

a function’s argument?

■  Come up with an idea for, create, and

■

In the example code in the

use your own custom function.

“Understanding Variable Scope”

section of the chapter, why does the

code use **\\$n**? What would happen if

that backslash wasn’t there?

■

What is variable scope? What scope

does a function argument variable have?

■

What scope does a variable in an

included file have? Note: This is a

tricky one!

286 Chapter

10

[**11**](#index_split_000.html#p8)

[Files and](#index_split_000.html#p8)

[Directories](#index_split_000.html#p8)

Taking your Web applications to the next

level requires a method of storing and

**In This Chapter**

retrieving data. You have two primary

options in PHP: using files (and directories)

File Permissions

288

or databases. This chapter will discuss

Writing to Files

293

the former, and the next chapter will

Locking Files

301

introduce the latter. It’s worth your time to

learn both methods: Although a database

Reading from Files

304

can be more powerful and secure than a

Handling File Uploads

307

file-based system, you may be surprised

Navigating Directories

315

at what’s possible by writing and reading

simple text documents on the server.

Creating Directories

320

In this chapter, you’ll learn about file per-

Reading Files Incrementally

327

missions, a topic that you must grasp first.

Review and Pursue

332

Then you’ll learn to write to, read from,

and lock files. After that, you’ll see how to

handle file uploads with PHP, how to create

directories, and an alternate method for

reading data from a file. These last two

examples will also demonstrate a simple

file-based registration and login system

that you can use in your Web applications.

[**File Permissions**](#index_split_000.html#p8)

**The Web Root Directory**

Before attempting to write to and read from

When discussing files, directories, and

a file, you must have an understanding of

security, an important concept is that of

file permissions. The topic is large enough

the Web root directory. To grasp this

that you may want to pursue it further,

concept, first consider that a file on a

but this quick introduction will get you

Web server is available in two ways. First,

started. Up front I will say that most of the

it exists in the file system. For example,

information in this chapter applies to only

this might be **C:\\inetpub\\wwwroot\\**

non-Windows users. In my experience,

**filename.php** on your own computer,

the preparatory steps to be taken aren’t

or **/var/web/sitename/htdocs/**

**filename.php** on a remote server

necessary when running PHP on a Windows

(that path would be applicable to

computer (although such things can change

\*nix systems).

from one version of an operating system

to the next). Still, having an understanding

Second, files placed within the proper

directories for a Web server are also

of permissions as a whole is a good idea,

available through HTTP, such as [**http://**](http://www.example.com/filename.php)

especially if you might later be running your

[**www.example.com/filename.php** or](http://www.example.com/filename.php)

PHP scripts on a non-Windows server.

**http://localhost/filename.php**.

Permissions identify who can do what with

With this in mind, the Web root

a file or directory. The options are read,

directory is the folder in the file system

write, and execute (actually, files can be

where the base URL—such as [**www.**](http://www.example.com%E2%80%94points)

designated executable, whereas directories

[**example.com**—points. W](http://www.example.com%E2%80%94points)ithout further are made searchable). Each of these

restrictions imposed, a Web browser

options can be set for three types of users:

can access all the files found within

the Web root directory and below (i.e.,

■

The owner of the file (the person who

in subfolders). A Web browser cannot,

created it or put it on the server)

however, access files found outside of

■

Members of a particular group, which

the Web root directory.

a server administrator determines and

When creating writable files and

which includes the owner

directories, it’s more secure to place

■

Others (those who don’t fall into the

them outside of the Web directory.

previous two categories)

In other words, if your Web pages go

in **C:\\inetpub\\wwwroot** or **/Users/**

There is also the implied everyone level,

***username*****/Sites**, then if you place items

which includes all three user types.

in **C:\\inetpub** or **/Users/ *username***,

As an example, if you use FTP to transfer a

they should be accessible to the locally

running PHP but not to others over the

file to a server, the account used to connect

Internet. The examples in this chapter

to the server will be the owner of the file.

follow this structure, and you should do

The default file permissions will likely be

so as well.

that everyone can read the file but that only

In general, the security concern here

the owner can modify it (i.e., write to it).

is more important for directories than

for files.

288 Chapter

11

![Image 383](index-310_1.png)

A catch is that in most cases, PHP will be

accounts aren’t associated with people

running through a Web server application,

who will log in, but rather with different

which counts as a different server user.

processes running on the server. For

Therefore, PHP and the Web server

example, there may be one user whose

would be able to read files you put onto

processes handle all Web requests and

the server (and consequently make them

another user through which the database

available for viewing in a Web browser),

application runs. Most importantly, know

but PHP would not, by default, be able to

that a “user” is not a person on another

modify those files.

computer and that “everyone” means

“everyone on the server.” Just because

For the examples in this chapter, PHP

you’ve made a file or directory writable

needs to be able to write to some files and

by any user doesn’t mean it’s writable by

directories. This means that you must know

anyone over the Internet. The user must

how, and be able, to adjust the permissions

be a recognized account on the server.

a file or directory has. That being said,

making a file or directory writable (i.e.,

**Creating the text file**

making the permissions less restrictive)

can be a security issue and should be

In the chapter’s first example, you’ll work

done only when absolutely necessary.

with a text file, **quotes.txt**, that’s located

on the server. If the file doesn’t have the

Finally, a common point of confusion has

correct permissions to do what your PHP

to do with what, exactly, a “user” is. A user

script is asking it to, you might see an error

is an account created on a computer. On

message like

your own computer, there may be just one

**A**. Before proceeding, you

should create **quotes.txt** on the server

user—you—or several. Servers normally

and establish its permissions.

have multiple users, although most user

**A** The …failed to open stream: Permission denied… message is the result of attempting to do something to a file that isn’t allowed by the server. Here the server is denying the **fopen()** function that is attempting to open **quotes.txt** for the purpose of writing to it.

Files and Directories 289

![Image 384](index-311_1.png)

![Image 385](index-311_2.png)

![Image 386](index-311_3.png)

![Image 387](index-311_4.png)

**To create quotes.txt:**

**1.** Open your text editor or IDE and create

a new, blank document.

**2.** Without typing anything into the file,

save it as **quotes.txt**.

**3.** Move the file just outside of the Web

root directory of your PHP-enabled

server **B**.

The sidebar “The Web Root Directory”

explains where you should put the file

with respect to your Web directory

and why.

**The file\_exists() function returns**

**TRUE if a provided file or directory exists on the**

**server. This can be used to test for the pres-**

**ence of a file before doing anything with it:**

**if (file\_exists('somefile.ext')) { …**

**Assuming that PHP has write permissions**

**on a directory, you can create a blank docu-**

**ment within that directory using PHP. This is**

**accomplished using the touch() function:**

**touch('somefile.ext');**

**B** The **quotes.txt** file should ideally be placed in the same directory as your Web documents folder (i.e., not in the directory with the actual Web documents).

290 Chapter

11

![Image 388](index-312_1.png)

![Image 389](index-312_2.jpg)

**Setting a file’s permissions**

The preceding sequence may seem like

an odd series of steps, but in order to set

the permissions on a file, the file must first

exist. You do want the file to be blank,

though, because you’ll use PHP to write

**C** This control panel, provided by a hosting

data to it later.

company, lets you adjust a file’s permissions.

The desired end result for this example

is to give either others or everyone

permission to read and write (but not

execute) **quotes.txt**. How you accomplish

this depends on:

■

Whether you’re running PHP on your

own computer or on a remote server

■

The operating system of the PHP-

enabled computer

Unfortunately, it would be impossible to

offer steps for how every user should set

the permissions under any circumstances,

but here are some rough guidelines and

steps to get you going.

**To set a file’s permissions**

**D** The Transmit FTP application uses

**on a remote server:**

this pop-up window to allow you to

set a file’s permissions.

■

Most ISPs offer users a Web-based

control panel where they can set file

permissions **C** as well as set other

hosting parameters.

■

You may be able to change a file’s

permissions using your FTP client **D**.

Files and Directories 291

![Image 390](index-313_1.png)

**To set a file’s permissions**

**Most operating systems have no PHP user.**

**on your computer:**

**Instead, the PHP user is essentially the user the**

**Web server application (for example, Apache or**

■

If you’re working on your own Windows

**IIS) is running as. In the Unix family, Apache often**

computer, you may not need to change the

**runs as nobody. On Windows, the Web server**

permissions. To test this theory, try each

**frequently runs as the same user who is logged**

example first. If a PHP script can’t write to

**in (and who probably created the file), meaning**

**there will be no need to alter a file’s permissions.**

the file or directory in question, use the

next suggestion to rework the permissions.

**If you’re already familiar with Telnet and**

**chmod, you probably also understand what the**

■

Windows users who need to change the

**0666 number means, but here’s an explana-**

permissions can do so by viewing the file's

**tion for those of you who aren’t familiar with it.**

or directory’s properties. The resulting

**The 0 is just a prefix indicating the number is**

panel will differ for each version of

**written in an octal format. Each 6 corresponds**

**to read (4) plus write (2) permission—first**

Windows, but basically you just need to

**assigning 6 to the owner, then to the group,**

tweak who can access the file and how.

**and then to others. Comparatively, 0777 allows**

■

Mac OS X users must select the file in

**read (4) plus write (2) plus execute (1 ) permis-**

the Finder and choose Get Info from

**sion to all three types of users. This numbering**

**is applicable for Unix variant operating systems**

the File menu. From there, use the

**(Linux, Solaris, and Mac OS X).**

Ownership & Permissions subpanel to

adjust the file’s permissions **E**.

**PHP has several functions for chang-**

**ing a file or directory’s permissions, including**

■

On Unix (including users of Linux

**chgrp(), chmod(), and chown(). However,**

and Mac OS X), you can also use the

**they will only work if PHP already has permis-**

command line **chmod** **0666** **quotes.txt**

**sion to modify the file or directory in question.**

in a terminal window, assuming that you

**A Web site running on a shared hosting**

have authority to do so.

**environment has greater security risks than**

**one running on a dedicated server as there are**

**literally more users. For example, if you make**

**a file or directory writable by every user, then**

**anyone with access to that server can manipu-**

**late that file (assuming they know it exists and**

**that other restrictions are not in place).**

**E** The Mac OS X Get Info panel lets you

adjust a file’s ownership and permissions,

among other things.

292 Chapter

11

[**Writing to Files**](#index_split_000.html#p8)

**File Paths**

Because you need to write something to

There are two ways of referring to any file

a file in order to read something from it,

or directory on the computer: using an

this chapter explores writing first. The

absolute or relative path. An absolute

path begins at the root of the computer:

easiest way to write to a file is to use the

**file\_put\_contents()** function:

. **C:\\somedir\\somefile.txt**

(Windows)

**file\_put\_contents($file, $data);**

. **/Users/ *username*/somefile.txt**

This function, added in PHP 5, will open

(Mac OS X)

the file and write the data there. The first

A relative path will not start with the

argument is the name of the file. This

root of the computer—**C:\\** or **/**. Instead

can be an absolute or relative path (see

it will be relative to the current working

the sidebar “File Paths”). The second

directory:

argument is the data, which can be a string,

. **fileA.txt** (in the same directory)

number, or array (one-dimensional, not

multidimensional). Neither the file nor the

. **./fileA.txt** (in the same directory)

data has to be represented by a variable,

. **dirB/fileB.txt** (inside **dirB**)

but it’s common to do so.

. **../fileC.txt** (inside the parent

If the file doesn’t exist, the function will

directory)

attempt to create it. If the file does exist,

. **../dirD/fileD.txt** (inside the

the file’s current contents will be replaced

parallel directory)

with the new data. If you’d prefer to have

Two periods together represent the

the new data appended to what’s already

current directory’s parent folder. A single

in the file, add the **FILE\_APPEND** constant as

period by itself represents the current

a third argument:

directory. If a file’s name begins with a

**file\_put\_contents($file, $data,**

single period, the file is hidden (on Unix,

Linux, and Mac OS X).

➝ **FILE\_APPEND);**

It technically doesn’t matter whether

When appending data to a file, you

you use a relative or an absolute path to

normally want each piece of data to be

refer to a file, as long as the reference is

written on its own line, so each submission

accurate. An absolute path is easier for

should conclude with the appropriate

beginners to understand but will only be

line break for the operating system of the

correct for that computer. A relative path

computer running PHP. This would be

can confound those new to the concept,

■

but can continue to be correct even after

**\\n** on Unix and Mac OS X

moving the site from one server to another.

■

**\\r\\n** on Windows

As with any meaningful escape sequence,

these must be placed within double

quotation marks in order to work.

continues on next page

Files and Directories 293

Alternatively, you can use the special PHP

constant **PHP\_EOL**, which represents the

**TABLE 11.1 fopen( ) Modes**

correct end-of-line character sequence (e.g.,

**Mode**

**Meaning**

**\\n** or **\\r\\n**) for the current operating system:

**r**

Reading only; begin reading at the

**file\_put\_contents($file,**

start of the file.

➝ **$data . PHP\_EOL, FILE\_APPEND);**

**r+**

Reading or writing; begin at the

start of the file.

If you’re not using PHP 5 or later, then

**w**

Writing only; create the file if it

the **file\_put\_contents()** function won’t

doesn’t exist, and overwrite any

be available for you and you must use

existing contents.

the legacy approach: first, open the file;

**w+**

Reading or writing; create the file if

second, write your data to it; and third,

it doesn’t exist, and overwrite any

close the file:

existing contents (when writing).

**a**

Writing only; create the file if it

**$fp = fopen($file, *mode*);**

doesn’t exist, and append the new

**fwrite($fp, $data . PHP\_EOL);**

data to the end of the file (retain

**fclose($fp);**

any existing data and add to it).

**a+**

To write to a file, you must create a file

Reading or writing; create the file

if it doesn’t exist, and append the

pointer when opening it. The file pointer

new data to the end of the file

returned by the **fopen()** function will be

(when writing).

used by PHP to refer to the open file.

**x**

Writing only; create the file if it

doesn’t exist, but do nothing (and

The most important consideration when

issue a warning) if the file does exist.

opening the file is what mode you use.

**x+**

Reading or writing; create the file if

Depending on what you intend to do with

it doesn’t exist, but do nothing (and

the file, the mode dictates how to open

issue a warning) if the file already

it. The most forgiving mode is **a+**, which

exists (when writing).

allows you to read or write to a file. It

creates the file if it doesn’t exist, and it

appends—hence ***a***—new data to the end

of the file automatically. Conversely, **r** only

allows you to read from a file. **Table 11.1**

lists all the possible modes. Each mode

can also be appended with a **b** flag, which

forces files to be opened in binary mode.

This is a safer option for files that might be

read on multiple operating systems.

294 Chapter

11

![Image 391](index-316_1.png)

The **fwrite()** function writes the new

data (sent as the second argument in the

function call) to the file in accordance with

the selected mode.

As the last step of the writing process,

you close the file by once again referring

to the file pointer while calling the

**A** This very simple form lets a user submit

a quotation that will be written to a text file.

**fclose()** function:

**fclose($fp);**

With this in mind, let’s create a form that

stores user-submitted quotations in a plain-

text file **A**. Later in this chapter, another

PHP script will retrieve and randomly display

these quotations. Before we get into the

code, however, there’s one more function to

be introduced: **is\_writable()**. This function

returns a Boolean value indicating the

writability of the named file:

**if (is\_writable($file)) {…**

Invoking this function prior to attempting to

write to a file (or directory) is a simple way to

avoid permissions errors.

Files and Directories 295

**To write to an external file:**

**1.** Create a new PHP document in

your text editor or IDE, to be named

**add\_quote.php** (**Script 11.1**):

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

➝ **XHTML 1.0 Transitional//EN"**

**"http://www.w3.org/TR/xhtml1/**

 ➝ **DTD/xhtml1-transitional.dtd">**

**<html xmlns="http://www.w3.org/**

➝ **1999/xhtml" xml:lang="en"**

➝ **lang="en">**

**<head>**

**<meta**

**http-equiv="content-type"**

 ➝ **content="text/html;**

 ➝ **charset=utf-8" />**

**<title>Add A Quotation</title>**

**</head>**

**<body>**

**Script 11.1** This script takes a user-submitted quotation and stores it in a text file.

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"

2 "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> 3

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en"> 4 <head>

5

<meta http-equiv="content-type" content="text/html; charset=utf-8" /> 6

<title>Add A Quotation</title>

7 </head>

8 <body>

9

<?php // Script 11.1 - add\_quote.php

10 /\* This script displays and handles an HTML form. This script takes text input and stores it in a text file. \*/

11

12 // Identify the file to use:

**13 $file = '../quotes.txt';**

14

15 // Check for a form submission:

16 if ($\_SERVER\['REQUEST\_METHOD'\] == 'POST') { // Handle the form.

17

18

if ( !empty($\_POST\['quote'\]) && ($\_POST\['quote'\] != 'Enter your quotation here.') ) { // Need some thing to write.

19

**20**

**if (is\_writable($file)) { // Confirm that the file is writable.**

21

**22**

**file\_put\_contents($file, $\_POST\['quote'\] . PHP\_EOL, FILE\_APPEND);**

**// Write the data.**

code continues on next page

296 Chapter

11

**2.** Create a section of PHP code and

identify the file to be used:

**<?php // Script 11.1 - add\_quote.php**

**$file = '../quotes.txt';**

As this script will reference the same

file twice, it’s a good idea to identify

the file as a variable. This way, should

you later need to change the name or

location of the file, only one line of code

will need to be edited.

The file identified is **quotes.txt**, which

should be located in the directory above

this script (which is presumably in the Web

directory root; see **B** in the previous

section of the chapter). See the sidebar

“File Paths” for more on this syntax.

continues on next page

**Script 11.1** continued

23

24 //

Print

a

message:

25

print '<p>Your quotation has been stored.</p>';

26

27

} else { // Could not open the file.

28

print '<p style="color: red;">Your quotation could not be stored due to a system error.</p>';

29 }

30

31

} else { // Failed to enter a quotation.

32

print '<p style="color: red;">Please enter a quotation!</p>'; 33 }

34

35 } // End of submitted IF.

36

37 // Leave PHP and display the form:

38 ?>

39

40 <form action="add\_quote.php" method="post"> 41

<textarea name="quote" rows="5" cols="30">Enter your quotation here.</textarea><br /> 42

<input type="submit" name="submit" value="Add This Quote!" /> 43 </form>

44

45 </body>

46 </html>

Files and Directories 297

**3.** Check if the form has been submitted: **6.** Write the data to the file and then print

**if ($\_SERVER\['REQUEST\_METHOD'\] ==**

a message:

➝ **'POST') {**

**file\_put\_contents($file,**

This page both displays and handles the

➝ **$\_POST\['quote'\] . PHP\_EOL,**

HTML form. The conditional tests if the

➝ **FILE\_APPEND);**

**print '<p>Your quotation has been**

form has been submitted, in which case

the quotation should be written to the

➝ **stored.</p>';**

text file.

The first line writes the user-submitted

data to the file. The **PHP\_EOL** constant

**4.** Check that a quotation was entered:

is concatenated to the written data, so

**if ( !empty($\_POST\['quote'\]) &&**

that each submission gets stored on its

➝ **($\_POST\['quote'\] != 'Enter your**

own line.

➝ **quotation here.') ) {**

If you’re not using PHP 5 or later, you’ll

This simple conditional validates

need to do this instead:

the user-supplied data. The first part

**$fp = fopen ($file, 'ab')**

confirms that the **$\_POST\['quote'\]**

**fwrite($fp, $\_POST\['quote'\] .**

variable isn’t empty. The second part

confirms that the variable doesn’t still

➝ **PHP\_EOL);**

**fclose($fp);**

have the default value (as shown in **A**).

**7.** Complete the conditionals:

**5.** Confirm that the file can be written to

**if (is\_writable($file)) {**

**} else { // Could not open**

 ➝ **the file.**

By placing this function call in a

**print '<p style="color:**

conditional, you make the PHP script

 ➝ **red;">Your quotation**

attempt to write to the file only if the

 ➝ **could not be stored due**

file is writable.

 ➝ **to a system error.</p>';**

**}**

**} else { // Failed to enter a**

 ➝ **quotation.**

**print '<p style="color:**

 ➝ **red;">Please enter a**

 ➝ **quotation!</p>';**

**}**

**} // End of submitted IF.**

298 Chapter

11

![Image 392](index-320_1.png)

![Image 393](index-320_2.png)

The first **else** completes the conditional

**9.** Create the HTML form:

that checks if PHP could open the file

**<form action="add\_quote.php"**

for writing **B**. If you see this message,

➝ **method="post">**

there’s likely a permissions issue or the file

**<textarea name="quote" rows="5"**

reference is incorrect. The second **else**

 ➝ **cols="30">Enter your quotation**

completes the conditional that checks

 ➝ **here.</textarea><br />**

whether no quotation was entered **C**. The

**<input type="submit" name=**

final closing curly bracket marks the end

 ➝ **"submit" value="Add This**

of the main submission conditional.

 ➝ **Quote!" />**

Because this page handles the form and

**<input type="hidden" name=**

then displays it again (so that the user may

 ➝ **"submitted" value="true" />** keep entering quotations), the form isn’t

**</form>**

displayed as part of an **else** statement as it

This HTML form presents a text box

has been in other examples in this book.

where the user can enter a quotation.

**8.** Complete the PHP section:

The text box has a preset value of Enter

your quotation here., created by putting

**?>**

that text between the **textarea** tags.

Because the rest of this script is

continues on next page

standard HTML, exit out of the PHP

code by closing the PHP tag.

**B** If the PHP script can’t find the **quotes.txt** file, or if it’s not writable, the user will see this message.

**C** The script includes basic

form validation.

Files and Directories 299

![Image 394](index-321_1.png)

![Image 395](index-321_2.png)

**10.** Complete the HTML page:

**</body>**

**</html>**

**11.** Save the file as **add\_quote.php** and

place it in the proper directory for your

PHP-enabled server.

**D** Filling out the form…

Again, refer back to **B** in the previous

section of the chapter for how the **add\_**

**quote.php** and **quotes.txt** should be

placed on your server relative to each

other. If this arrangement isn’t possible

for you, or if it’s just too confusing, then

place both documents within the same

directory (the one from which you can

execute PHP scripts) and change the

**$file** assignment line to

**E** …and the result if all went well.

**$file = 'quotes.txt';**

**12.** Run the script several times in your Web

browser **D** and **E**.

**13.** If you want, open the **quotes.txt** file in

a text editor to confirm that the data has

been written to it.

**Note that all of the file- and directory-**

**related functions are usable only on files and**

**directories on the same computer (i.e., server)**

**on which PHP is running. A PHP script on a**

**server has no access to a file on a client’s com-**

**puter (until the file is uploaded to the server).**

**If you receive a permissions error when**

**you run this script B, either the permissions**

**aren’t set properly or the PHP script couldn’t**

**access the data file. The latter can happen if**

**you misspell the filename or incorrectly refer-**

**ence the file’s path on the server.**

**If your version of PHP is running in safe**

**mode or has the open\_basedir directive set,**

**you may be limited in using PHP to access**

**files and directories. Check your phpinfo()**

**script to see these settings for your server.**

300 Chapter

11

**TABLE 11.2 flock( ) Lock Types**

[**Locking Files**](#index_split_000.html#p8)

Although the last example worked fine

**Lock**

**Meaning**

(hopefully), it could be improved on. If only

**LOCK\_SH**

Shared lock for reading purposes

a single user were submitting the form at

**LOCK\_EX**

Exclusive lock for writing

one time, there would be no problems.

purposes

But what if two or more users submitted

**LOCK\_UN**

Release of a lock

different quotations simultaneously? In

**LOCK\_NB**

Nonblocking lock

such a case, there could be problems

when multiple instances of the PHP script

attempt to write to the same text file at

once (the file could become corrupted).

The solution is to temporarily lock the

file while PHP is writing to it. If you are

running PHP 5.1 or greater, you can add the

**LOCK\_EX** constant as the third argument to

**file\_put\_contents()**:

**file\_put\_contents($file, $data,**

➝ **LOCK\_EX);**

To use both the **LOCK\_EX** and **FILE\_APPEND**

constants, separate them with the binary

OR operator (**|**):

**file\_put\_contents($file, $data,**

➝ **FILE\_APPEND | LOCK\_EX);**

It doesn’t matter in which order you list the

two constants. If you’re using an earlier

version of PHP and have to use **fopen()**,

**fwrite()**, and **fclose()**, you can invoke

the **flock()** function after opening the file:

**$fp = fopen($file, 'a+b');**

**flock($fp, *locktype*)**

The different lock types are represented by

the constants listed in **Table 11.2**. Note that

you should unlock the file once the script is

done with it.

As an example, to temporarily lock a file

during a write, use this code:

**$fp = fopen($file, 'a+b');**

**flock ($fp, LOCK\_EX);**

**fwrite ($fp, $data);**

**flock ($fp, LOCK\_UN);**

continues on next page

Files and Directories 301

To demonstrate, let’s update **add\_quote.php**

to lock the file during the writing process.

**To use file locks:**

**1.** Open **add\_quote.php** (Script 11.1) in your

text editor or IDE, if it isn’t already open.

**2.** Change the **file\_put\_contents()** line

to the following (**Script 11.2**):

**file\_put\_contents($file,**

➝ **$\_POST\['quote'\] . PHP\_EOL,**

➝ **FILE\_APPEND | LOCK\_EX);**

This command places an exclusive lock

on the file so that other scripts can’t

write to it at the same time.

Again, if you’re not able to use

**file\_put\_contents()** and **LOCK\_EX**,

you’ll need to apply **flock()**, as in

**flock($fp, LOCK\_EX);**

**fwrite($fp, $\_POST\['quote'\] .**

➝ **PHP\_EOL);**

**flock($fp, LOCK\_UN);**

**fclose($fp);**

**Script 11.2** The modified version of the **add\_quote.php** script locks the data file for better security and reliability.

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"

2 "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> 3

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en"> 4 <head>

5

<meta http-equiv="content-type" content="text/html; charset=utf-8" /> 6

<title>Add A Quotation</title>

7 </head>

8 <body>

9

<?php // Script 11.1 - add\_quote.php

10 /

\* This script displays and handles an HTML form. This script takes text input and stores it in a text file. \*/

11

12 // Identify the file to use:

13 $file = '../quotes.txt';

14

15 // Check for a form submission:

16 if ($\_SERVER\['REQUEST\_METHOD'\] == 'POST') { // Handle the form.

17

18

if ( !empty($\_POST\['quote'\]) && ($\_POST\['quote'\] != 'Enter your quotation here.') ) { // Need some thing to write.

code continues on next page

302 Chapter

11

![Image 396](index-324_1.png)

![Image 397](index-324_2.png)

**3.** Save the file, place it in the proper

directory for your PHP-enabled server,

and test it again in your Web browser

**A** and **B**.

**When you use flock(), the file will**

**automatically be unlocked once fclose() is**

**A** Using the form once again…

**called, but it’s good form to specifically unlock**

**it once the file writing is complete.**

**Technically, if a file is opened in an**

**appending mode, as in this example, not**

**locking it probably won’t be a problem even if**

**multiple scripts are writing to the file simultane-**

**ously. That said, better safe than sorry!**

**For file locking to be reliable, every script**

**that writes to a file needs to use locking.**

**B** …the quotation is still stored without

a problem.

**Script 11.2** continued

19

20

if (is\_writable($file)) { // Confirm that the file is writable.

21

**22**

**file\_put\_contents($file, $\_POST\['quote'\] . PHP\_EOL, FILE\_APPEND | LOCK\_EX); //**

**Write the data.**

23

24 //

Print

a

message:

25

print '<p>Your quotation has been stored.</p>';

26

27

} else { // Could not open the file.

28

print '<p style="color: red;">Your quotation could not be stored due to a system error.</p>';

29 }

30

31

} else { // Failed to enter a quotation.

32

print '<p style="color: red;">Please enter a quotation!</p>'; 33 }

34

35 } // End of submitted IF.

36

37 // Leave PHP and display the form:

38 ?>

39

40 <form action="add\_quote.php" method="post"> 41

<textarea name="quote" rows="5" cols="30">Enter your quotation here.</textarea><br /> 42

<input type="submit" name="submit" value="Add This Quote!" /> 43 </form>

44

45 </body>

46 </html>

Files and Directories 303

[**Reading from Files**](#index_split_000.html#p8)

Now that you’ve created a script that

writes data to a file, it’s time to create one

that can read the information. There are a

number of ways to read from a file; which

approach you take depends on what your

needs are. To read an entire file in as one

string, use **file\_get\_contents()**:

**$data = file\_get\_contents($file);**

If the file has some data on each line, as is

the case with **quotes.txt**, you’re better off

using the **file()** function:

**$data = file($file);**

The **file()** function is a valuable built-in tool

in PHP. It reads everything from a file and,

unlike **file\_get\_contents()**, returns that

information as an array. Each array element

contains one line from the file, where each

line is terminated by a newline (**\\n** or **\\r\\n**).

If the document represented by **$file**

contains two lines of information, each

of which ends with a newline, the

corresponding array will contain two

elements. The first element will be equal

to the first line of **$file**, and the second

element will be equal to the second line.

Once the data is stored into an array, you

can easily manipulate or print it, as you

learned in Chapter 7, “Using Arrays.”

Next, let’s use this knowledge to create

a script that randomly displays one of the

stored quotations.

304 Chapter

11

**Script 11.3** The **view\_quote.php** file retrieves all **To read from a file:**

the quotations from the text file and displays one

at random.

**1.** Create a new PHP document in

your text editor or IDE, to be named

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

**view\_quote.php** (**Script 11.3**):

1.0 Transitional//EN"

2

"http://www.w3.org/TR/xhtml1/DTD/

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

xhtml1-transitional.dtd">

➝ **XHTML 1.0 Transitional//EN"**

3

<html xmlns="http://www.w3.org/1999/

**"http://www.w3.org/TR/xhtml1/**

xhtml" xml:lang="en" lang="en">

 ➝ **DTD/xhtml1-transitional.dtd">**

4 <head>

5

<meta http-equiv="content-type"

**<html xmlns="http://www.w3.org/**

content="text/html; charset=utf-8" />

➝ **1999/xhtml" xml:lang="en"**

6

<title>View A Quotation</title>

➝ **lang="en">**

7 </head>

**<head>**

8 <body>

**<meta**

**http-equiv="content-type"**

9 <h1>Random

Quotation</h1>

10 <?php // Script 11.3 - view\_quote.php

 ➝ **content="text/html;**

11

/\* This script displays and handles an

 ➝ **charset=utf-8" />**

HTML form. This script reads in a file

**<title>View A Quotation</title>**

and prints a random line from it. \*/

**</head>**

12

**<body>**

13 // Read the file's contents into an array:

**14 $data = file('../quotes.txt');**

**<h1>Random Quotation</h1>**

15

**2.** Open a PHP code section:

16 // Count the number of items in the array:

**17 $n = count($data);**

**<?php // Script 11.3 -**

18

➝ **view\_quote.php**

19 // Pick a random item:

**20 $rand = rand(0, ($n - 1));**

**3.** Read the file contents and store them in

21

an array:

22 // Print the quotation:

**$data = file('../quotes.txt');**

**23 print '<p>' . trim($data\[$rand\]) . '</p>';**

24

The function reads the file data into

25 ?>

an array called **$data**. Each element

26 </body>

of **$data** is a string, which is the

27 </html>

submitted quotation.

If the quotes file is not in the parent

directory of this script, change the

reference here accordingly.

**4.** Pick a random number based on the

number of elements in **$data**:

**$n = count($data);**

**$rand = rand(0, ($n - 1));**

continues on next page

Files and Directories 305

![Image 398](index-327_1.png)

![Image 399](index-327_2.png)

The first line counts how many elements

**6.** Complete the PHP code and the

(which is to say, how many quotations)

HTML page:

are in the **$data** array. Then the **rand()**

**?>**

function selects a random number. In

**</body>**

order for **rand()** to pick an appropriate

**</html>**

number, a little logic is required.

**7.** Save the file as **view\_quote.php**, place

If **$data** has 10 elements, they’re indexed

it on your Web server (in the same

between 0 and 9, so that’s the range to

directory as **add\_quote.php**), and test it

use for **rand()**. Therefore, to calculate

in your Web browser **A**.

the range for a variable number of lines

**8.** Reload the page in your Web browser

in the text file, use 0 and 1 less than the

to view another random quote **B**.

number of elements in **$data**.

**5.** Print out the quotation:

**If you want to be extra careful, you**

**print '<p>' . trim($data\[$rand\]) .**

**can use the is\_readable() function to test**

➝ **'</p>';**

**that PHP can read a file before you call the**

**file() function (although it’s rare that a file**

A simple **print** statement involving

**isn’t readable).**

concatenation is used to print the

random quotation. To retrieve the

**The readfile() function reads through**

quotation, you refer to the **$data** array

**a file and immediately sends the contents to**

**the Web browser.**

and use the generated **$rand** number

as the index. The retrieved quotation

**Later in the chapter, you’ll learn a more**

is then trimmed to cut off the newline

**complex method of reading a file using**

characters from the end of the quotation.

**fgets() and fgetcsv().**

**A** A random quotation is displayed each time the page is viewed.

**B** Subsequent viewings of the **view\_quote.php** script display different quotations from the text file.

306 Chapter

11

![Image 400](index-328_1.png)

![Image 401](index-328_2.png)

[**Handling File Uploads**](#index_split_000.html#p8)

As this book has demonstrated, handling

**A** This is how Firefox interprets the file

HTML forms using PHP is a remarkably

input type.

easy achievement. Regardless of the data

being submitted, PHP can handle it easily

and directly. The same is true when the

user uploads a file via an HTML form.

**B** This is how the Safari Web

To give the user the option of uploading a

browser interprets the file input

type (prior to selecting a file).

file, you must make three changes to the

standard HTML form. First, the initial **form** tag

must include the code **enctype="multipart/**

**form-data"** , which lets the browser know to

expect different types of form data:

**<form action="script.php" enctype=**

➝ **"multipart/form-data" method="post">** The form must also always use the

POST method.

Second, a special hidden input type should

be added to the form:

**<input type="hidden" name=**

➝ **"MAX\_FILE\_SIZE" value="30000" />**

This tells the browser how large a file, in

bytes, can be uploaded.

Third, the **file** tag is used to create the

necessary form field **A** and **B**:

**<input type="file" name="picture" />** The file type of form input allows the user

to select a file on their computer, which,

upon submission, will be uploaded to the

server. Once this has occurred, you can

then use PHP to handle the file.

continues on next page

Files and Directories 307

In the PHP script, you refer to the **$\_FILES**

variable (think of it as the file equivalent of

**TABLE 11.3 $\_FILES Error Codes**

**$\_POST**) to reference the uploaded file. The

**Code**

**Meaning**

**$\_FILES** array contains five elements:

0

No error has occurred.

■

**name**, the name of the file as it was on

1

The file exceeds the **upload\_max\_**

the user’s computer

**filesize** setting in **php.ini**.

■

**type**, the MIME type of the file (for

2

The file exceeds the **MAX\_FILE\_SIZE**

setting in the HTML form.

example, image/jpg)

3

The file was only partially uploaded.

■

**size**, the size of the file in bytes

4

No file was uploaded.

■

**tmp\_name**, the temporary name of the

6

No temporary directory exists.

file as it’s stored on the server

7

Failed write to disk.

■

**error**, an error code if something goes

8

Upload prevented by an extension.

wrong (**Table 11.3**)

Note that, as strange as this may seem,

there is no error code 5.

When a file is uploaded, the server first places

it in a temporary directory. You can then use

the **move\_uploaded\_file()** function to move

the file to its final destination:

**move\_uploaded\_file($\_FILES\['picture'\]**

**\['tmp\_name'\], ' */path/to/dest/***

***filename*****');**

The first argument is the temporary name of

the file on the server. The second argument

is the full path and name of the destination.

For PHP to be able to take these steps,

you must set several configurations in the

**php.ini** file (see the “Configuring PHP for

File Uploads” sidebar), and the Web server

needs write access to both the temporary

and final destination directories. (PHP

should have write access to the temporary

directory by default.)

308 Chapter

11

![Image 402](index-330_1.png)

![Image 403](index-330_2.png)

![Image 404](index-330_3.png)

![Image 405](index-330_4.png)

![Image 406](index-330_5.png)

Next, you’ll write a basic script that uploads

a file and stores it on the server. Like

the **add\_quote.php** script, this example

also both creates the HTML form **C** and

processes it, all in one page. First, though,

you’ll create a writable directory as the

destination point.

**C** This HTML form lets the user

select a file on their computer to

upload to the server.

**To create a writable directory:**

**1.** Create a new folder called **uploads**,

located outside of the Web directory

root **D**.

**2.** Using the steps outlined in the first sec-

tion of this chapter, set the permissions

so that everyone can write to, read

from, and search (**0777** in Unix terms)

the directory.

**D** For this example, a writable **uploads** directory

must exist. Here, it’s placed in the same directory as

Again, if you’re running Windows you

the Web root folder. Thus **uploads** is in the directory

likely don’t need to do anything (try

above the one in which the **upload\_file.php** script

the next script to see for sure). If you’re

resides and is not accessible via HTTP.

running another operating system,

check the list of bullet points in the

first section of the chapter for the

suggestion that works for your situation.

**Configuring PHP for File Uploads**

In order for file uploading to work, a number of settings in your **php.ini** configuration file must be set. These may or may not be enabled in your configuration, so you should check them by viewing the **php.ini** file or running a **phpinfo()** script.

For starters, **file\_uploads** must be on. Second, the **upload\_tmp\_dir** value must be set to a directory on the server where PHP can place files (in other words, it must exist and be modifiable by the Web server). If this setting has no value, that’s probably fine (meaning that a hidden directory created expressly for purposes such as these will be used).

The **upload\_max\_filesize** and **post\_max\_size** settings dictate how large a file can be sent.

Whereas the **MAX\_FILE\_SIZE** hidden form input is a recommendation to the Web browser, these two settings control whether the file is uploaded.

Finally, if really large files will be uploaded (many megabytes or larger), you may need to increase the **memory\_limit** and **max\_execution\_time** settings to give PHP the time and the resources to do what it needs to do.

Files and Directories 309

**To use PHP for file uploads:**

**1.** Create a new PHP document in

your text editor or IDE, to be named

**upload\_file.php** (**Script 11.4**):

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

➝ **XHTML 1.0 Transitional//EN"**

**"http://www.w3.org/TR/xhtml1/**

 ➝ **DTD/xhtml1-transitional.dtd">**

**<html xmlns="http://www.w3.org/**

➝ **1999/xhtml" xml:lang="en"**

➝ **lang="en">**

**<head>**

**<meta**

**http-equiv="content-type"**

 ➝ **content="text/html;**

 ➝ **charset=utf-8" />**

**<title>Upload a File</title>**

**</head>**

**<body>**

**2.** Create a section of PHP code:

**<?php // Script 11.4 -**

➝ **upload\_file.php**

continues on page 312

**Script 11.4** This script handles a file upload by first defining the proper HTML form and, second, invoking **move\_uploaded\_file()** to move the file to the desired location.

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"

2 "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> 3

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en"> 4 <head>

5

<meta http-equiv="content-type" content="text/html; charset=utf-8" /> 6

<title>Upload a File</title>

7 </head>

8 <body>

9

<?php // Script 11.4 - upload\_file.php

10

/\* This script displays and handles an HTML form. This script takes a file upload and stores it on the server. \*/

11

12 if ($\_SERVER\['REQUEST\_METHOD'\] == 'POST') { // Handle the form.

13

code continues on next page

310 Chapter

11

**Script 11.4** continued

14

// Try to move the uploaded file:

**15**

**if (move\_uploaded\_file ($\_FILES\['the\_file'\]\['tmp\_name'\], "../uploads/{$\_FILES\['the\_file'\]**

**\['name'\]}"))**

**{**

16

17

print '<p>Your file has been uploaded.</p>';

18

19

} else { // Problem!

20

21

print '<p style="color: red;">Your file could not be uploaded because: '; 22

23

// Print a message based upon the error:

**24 switch ($\_FILES\['the\_file'\]\['error'\]) {**

**25**

**case 1:**

**26**

**print 'The file exceeds the upload\_max\_filesize setting in php.ini';** **27**

**break;**

**28 case**

**2:**

**29**

**print 'The file exceeds the MAX\_FILE\_SIZE setting in the HTML form';** **30**

**break;**

**31 case**

**3:**

**32**

**print 'The file was only partially uploaded';**

**33**

**break;**

**34 case**

**4:**

**35**

**print 'No file was uploaded';**

**36**

**break;**

**37**

**case 6:**

**38**

**print 'The temporary folder does not exist.';**

**39**

**break;**

**40 default:**

**41 print**

**'Something**

**unforeseen**

**happened.';**

**42**

**break;**

**43 }**

44

45

print '.</p>'; // Complete the paragraph.

46

47

} // End of move\_uploaded\_file() IF.

48

49 } // End of submission IF.

50

51 // Leave PHP and display the form:

52 ?>

53

**54 <form action="upload\_file.php" enctype="multipart/form-data" method="post">** 55

<p>Upload a file using this form:</p>

**56**

**<input type="hidden" name="MAX\_FILE\_SIZE" value="300000" />** **57**

**<p><input type="file" name="the\_file" /></p>** **58**

**<p><input type="submit" name="submit" value="Upload This File" /></p>** 59 </form>

60

61 </body>

62 </html>

Files and Directories 311

![Image 407](index-333_1.png)

**3.** Check whether the form has been

submitted:

**if ($\_SERVER\['REQUEST\_METHOD'\] ==**

➝ **'POST') {**

Once again, this script both displays

and handles the HTML form. If it has

been submitted, the uploaded file

should be addressed.

**E** If the file was uploaded and

moved successfully, a message

**4.** Attempt to move the uploaded file to its

is printed and the form is

final destination:

displayed again.

**if (move\_uploaded\_file**

➝ **($\_FILES\['the\_file'\]\['tmp\_name'\],**

➝ **"../uploads/{$\_FILES\['the\_file'\]**

➝ **\['name'\]}")) {**

The **move\_uploaded\_file()** function

attempts to move the uploaded file

(identified by **$\_FILES\['the\_file'\]**

**\['tmp\_name'\]**) to its new location

(**../uploads/{$\_FILES\['the\_file'\]**

**\['name'\]**). The location is the **uploads**

directory, which is located in the folder

above the one this script is in. The file’s

name will be the same as it was on the

user’s computer.

Placing this function as a condition in an

**if** statement makes it easy to respond

based on whether the move worked.

**5.** Print messages indicating the success

of the operation:

**print '<p>Your file has been**

 ➝ **uploaded.</p>';**

**} else { // Problem!**

**print '<p style="color: red;">**

 ➝ **Your file could not be**

 ➝ **uploaded because: ';**

The first **print** statement is executed if

the move worked **E**. The **else** applies

if it didn’t work, in which case an error

message is begun. This message will

be made more explicit in Step 6.

312 Chapter

11

![Image 408](index-334_1.png)

**6.** Print out the error message if the move

appropriate error message. When you

didn’t work:

use this in a **switch** conditional, the

PHP script can print out the appropriate

**switch ($\_FILES\['the\_file'\]**

error message

**\['error'\]) {**

**F**.

You wouldn’t normally place code like

**case**

**1:**

this in a public site (it’s a little too much

**print 'The file exceeds the**

information), but it’s exceptionally good

 ➝ **upload\_max\_filesize setting**

for helping you debug a problem.

 ➝ **in php.ini';**

**break;**

**7.** Complete the error message, and close

**case**

**2:**

both conditionals:

**print 'The file exceeds the**

**print '.</p>'; // Complete the**

 ➝ **MAX\_FILE\_SIZE setting in**

**paragraph.**

 ➝ **the HTML form';**

**} // End of move\_uploaded\_**

**break;**

**file() IF.**

**case**

**3:**

**} // End of submission IF.**

**print 'The file was only**

**8.** Exit out of PHP and create the

 ➝ **partially uploaded';**

HTML form:

**break;**

**case**

**4:**

**?>**

**print 'No file was uploaded';**

**<form action="upload\_file.php"**

**break;**

➝ **enctype="multipart/form-data"**

**case**

**6:**

➝ **method="post">**

**print 'The temporary folder**

**<p>Upload a file using this**

 ➝ **does not exist.';**

 ➝ **form:</p>**

**break;**

**<input type="hidden" name="MAX\_**

**default:**

 ➝ **FILE\_SIZE" value="300000" />**

**print 'Something unforeseen**

**<p><input**

**type="file"**

 ➝ **happened.';**

 ➝ **name="the\_file" /></p>**

**break;**

**<p><input**

**type="submit"**

**}**

 ➝ **name="submit" value="Upload**

 ➝ **This File" /></p>**

If a move doesn’t work, the **$\_**

**</form>**

**FILES\['the\_file'\]\['error'\]** variable

contains a number indicating the

continues on next page

**F** If a problem occurred, the script indicates the cause.

Files and Directories 313

![Image 409](index-335_1.png)

The HTML form is simple, containing

**If the file couldn’t be moved and a**

only two visible elements: a file input

**permissions denied error is shown, check the**

type and a submit button. It differs from

**permissions on the uploads directory. Then**

**check that the path to the directory used in**

other HTML forms in this book in that

**the script is correct and that there are no**

it uses the **enctype** attribute and a

**spelling errors.**

**MAX\_FILE\_SIZE** hidden input type.

**As you might discover, files uploaded**

Be careful when giving your **file**

**through the Web browser are owned (in terms**

input a name, because this value must

**of permissions) by the Web server application**

exactly match the index used in the

**(which put them there).**

**$\_FILES** variable. Here, you use a

**From a security standpoint, it’s better**

generic ***the\_file***.

**to rename an uploaded file. To do so, you’ll**

**9.** Complete the HTML page:

**need to devise a system that generates a new,**

**unique filename and stores both the original**

**</body>**

**and new filenames in a text file or a database.**

**</html>**

**A script can handle multiple file**

**10.** Save the page as **upload\_file.php**,

**uploads as long as they have different**

place it in the proper directory for your

**names. In such a case, you need only one**

PHP-enabled server relative to the

**MAX\_FILE\_SIZE hidden input. In the PHP**

**uploads** directory **D**, and test it in your

**script, you’d apply the move\_uploaded\_**

Web browser **G**.

**file() function to $\_FILES\['filename1'\],**

**$\_FILES\['filename2'\], and so on.**

Only files smaller than about 300 KB

should be allowed, thanks to the

**You can limit a file upload to a specific**

**MAX\_FILE\_SIZE**

**size or type by referencing the appropriate**

restriction.

**index (for example, $\_FILES\['the\_file'\]**

**11.** Check the **uploads** directory to ensure

**\['size'\]) in your PHP script (after the file**

that the file was placed there.

**has been uploaded).**

**Use unlink() to delete a file without**

**moving or copying it.**

**You can use the copy() function to make**

**a copy of a file on the server.**

**G** Select a file on your computer

to upload.

314 Chapter

11

![Image 410](index-336_1.png)

[**Navigating Directories**](#index_split_000.html#p8)

The previous PHP scripts work with files, but

you can also do many things with directories

using PHP. In this example, you’ll write a

script that lists a directory’s contents, but first

you’ll need to understand the usage and

syntax of many of the functions you’ll use.

To find all of the contents of a directory,

the easiest option is to use the **scandir()**

function:

**$stuff = scandir($dir);**

This function, added in PHP 5, returns an

array of every item—directory or file—found

within the given directory. As with the file-

related functions, the value of **$dir** can

be a relative or an absolute path to the

directory in question.

**A** The **list\_dir.php** script shows the contents of

If you’re using an earlier version of PHP,

a directory. The top part lists the subfolders, and

you’ll need to use **opendir()**, **readdir()**,

the bottom table lists the files.

and **closedir()** instead. See the PHP

manual page for **readdir()** for the full

syntax and usage.

This next example will make use of

**scandir()**, but let’s look at a couple more

functions first. You’ll use the **filesize()**

function in this example; it determines how

large a file is in bytes. This value can be

assigned to a variable or be printed:

**$size = filesize($file);**

Similarly, the **filemtime()** function

retrieves the modification time of a file.

It returns a timestamp, which can be

formatted using the **date()** function.

Finally, PHP includes several functions

that identify attributes. This chapter has

already mentioned **is\_writable()** and

**is\_readable()**, but there are also **is\_dir()**

and **is\_file()**. They return **TRUE** if the item

in question is a directory or a file, respectively.

You’ll put all of these capabilities together

into one page, which will constitute a

Web-based control panel for viewing a

directory’s contents **A**.

Files and Directories 315

**To create the directory**

**control panel:**

**1.** Create a new PHP document in

your text editor or IDE, to be named

**list\_dir.php** (**Script 11.5**):

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

➝ **XHTML 1.0 Transitional//EN"**

**"http://www.w3.org/TR/xhtml1/**

 ➝ **DTD/xhtml1-transitional.dtd">**

**<html xmlns="http://www.w3.org/**

➝ **1999/xhtml" xml:lang="en"**

➝ **lang="en">**

**<head>**

**<meta**

**http-equiv="content-type"**

 ➝ **content="text/html;**

 ➝ **charset=utf-8" />**

**<title>Directory**

**Contents**

 ➝ **</title>**

**</head>**

**<body>**

continues on page 318

**Script 11.5** This script displays the contents of a directory. First the subdirectories are listed, followed by the files (with their sizes and modification dates) in a table.

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"

2 "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> 3

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en"> 4 <head>

5

<meta http-equiv="content-type" content="text/html; charset=utf-8" /> 6 <title>Directory

Contents</title>

7 </head>

8 <body>

9

<?php // Script 11.5 - list\_dir.php

10 /\* This script lists the directories and files in a directory. \*/

11

12 // Set the time zone:

13 date\_default\_timezone\_set('America/New\_York');

14

15 // Set the directory name and scan it:

**16 $search\_dir = '.';**

**17 $contents = scandir($search\_dir);**

18

code continues on next page

316 Chapter

11

**Script 11.5** continued

19 // List the directories first...

20 // Print a caption and start a list:

**21 print**

**'<h2>Directories</h2>**

**22 <ul>';**

**23 foreach ($contents as $item) {**

**24**

**if ( (is\_dir($search\_dir . '/' . $item)) AND (substr($item, 0, 1) != '.') ) {**

**25 print**

**"<li>$item</li>\\n";**

**26 }**

**27 }**

28

29 print '</ul>'; // Close the list.

30

31 // Create a table header:

32 print '<hr /><h2>Files</h2>

33 <table cellpadding="2" cellspacing="2" align="left"> 34 <tr>

35 <td>Name</td>

36 <td>Size</td>

37 <td>Last

Modified</td>

38 </tr>';

39

40 // List the files:

**41 foreach ($contents as $item) {**

**42**

**if ( (is\_file($search\_dir . '/' . $item)) AND (substr($item, 0, 1) != '.') ) {**

43

44

// Get the file size:

**45**

**$fs = filesize($search\_dir . '/' . $item);**

46

47

// Get the file's modification date:

**48**

**$lm = date('F j, Y', filemtime($search\_dir . '/' . $item));**

49

50

// Print the information:

51 print

"<tr>

52 <td>$item</td>

53 <td>$fs

bytes</td>

54 <td>$lm</td>

55 </tr>\\n";

56

57

} // Close the IF.

58

59 } // Close the FOREACH.

60

61 print '</table>'; // Close the HTML table.

62

63 ?>

64 </body>

65 </html>

Files and Directories 317

**2.** Begin the PHP code and set the time zone: list every directory, so the **is\_dir()**

**<?php // Script 11.5 - list\_dir.php**

function is called to confirm the item’s

**date\_default\_timezone\_set**

type. That same conditional also checks

➝ **('America/New\_York');**

that the current item isn’t the current

directory (marked by a single period on

Because this script will make use of the

Unix systems) or the parent directory

**date()** function, it needs to establish

(marked by a double period on Unix

the time zone once. See Chapter 8,

systems). If this conditional is **TRUE**, then

“Creating Web Applications,” for more

the item’s name is printed out, within

and for the reference in the PHP manual

list item tags, followed by a newline (to

where you can find your time zone.

make for neater HTML source code).

**3.** Identify the directory to be opened, and

So that the **is\_dir()** function will work

scan in its contents:

when dealing with items found in other

**$search\_dir = '.';**

directories, the **$search\_dir** value, plus

**$contents = scandir($search\_dir);**

a slash, is appended to each item. If

By establishing this value as a variable

the code just referred to **$item** without

at the top of the PHP script, it will be

adding the directory path, the code

easy to find and change as needed.

would only work for the current directory.

Here you use a single period to refer

**5.** Create a new heading, and start a table

to the current directory. You could

for the files:

also use an absolute path to another

**print '<hr /><h2>Files</h2>**

directory (**/Users/larry/Documents** or

**<table cellpadding="2"**

**C:\\\\myfiles\\\\directory**) or a relative

➝ **cellspacing="2" align="left">**

path (**../myfiles**), as long as PHP has

**<tr>**

permission to read the named directory.

**<td>Name</td>**

The second line scans in the directory’s

**<td>Size</td>**

contents and assigns them as an array

**<td>Last Modified</td>**

to the variable **$contents**.

**</tr>';**

**4.** List the subdirectories of this directory:

The script also displays the files’ sizes and

**print '<h2>Directories</h2>**

modification dates. To make this look nicer,

**<ul>';**

the results are placed in an HTML table.

**foreach ($contents as $item) {**

**6.** Begin looping through the files in this

**if ( (is\_dir($search\_dir . '/' .**

directory:

 ➝ **$item)) AND (substr($item,**

**foreach ($contents as $item) {**

 ➝ **0, 1) != '.') ) {**

**if ( (is\_file($search\_dir . '/' .**

**print**

**"<li>$item</li>\\n";**

 ➝ **$item)) AND (substr($item,**

**}**

 ➝ **0, 1) != '.') ) {**

**}**

Another **foreach** loop is used to go

**print '</ul>';**

through the directory contents again.

This **foreach** loop accesses every item

This time, the conditional only wants

in the array, assigning each one to the

items that are files (but not hidden files

**$item** variable. The script should first

that begin with a single period).

318 Chapter

11

![Image 411](index-340_1.png)

Again, the **$search\_dir** value and a

slash is prepended to each item.

**7.** Calculate the file’s size and modification

date, and then print out the information:

**$fs = filesize($search\_dir . '/' .**

➝ **$item);**

**$lm = date('F j, Y', filemtime**

➝ **($search\_dir . '/' . $item));**

**print "<tr>**

**<td>$item</td>**

**<td>$fs bytes</td>**

**<td>$lm</td>**

**</tr>\\n";**

The first line calls the **filesize()**

function to retrieve the file’s size

in bytes. The second line calls the

**filemtime()** function, which returns

**B** The directory listing for another folder on

the server.

a timestamp of the file’s modification

time. The timestamp is then fed into

the **date()** function, along with the

proper formatting, to return a string like

November 24, 2011. Finally, these two

items and the file’s name are printed in

the appropriate columns of the table.

**8.** Complete the conditional and the loop:

**Notice that you need to use double**

**backslashes to create absolute path names on**

**}**

**a Windows server. This is necessary because**

**}**

**the single backslash, used in Windows path**

**names, is the escape character. So, it must be**

**9.** Close the table:

**escaped to be taken literally.**

**print '</table>';**

**The glob() function lets you search a**

**10.** Complete the PHP code and the

**directory for files whose name matches a pat-**

HTML page:

**tern (like *something*.jpg or *filename*.doc).**

**?>**

**Other file functions you might appreciate**

**</body>**

**include fileperms(), which returns the file’s**

**</html>**

**permissions; fileatime(), which returns the**

**last time a file was accessed; and fileowner(),**

**11.** Save the file as **list\_dir.php**, place

**which returns the user who owns the file.**

it in the proper directory for your PHP-

enabled server, and test it in your Web

**The basename() and dirname() func-**

**tions are useful for finding subparts of a full**

browser **A**.

**directory or file path.**

**12.** If you want, change the value of

**$search\_dir** and retest the script

**The finfo\_file() function is the best**

**way to find a file’s MIME type.**

in your Web browser **B**.

Files and Directories 319

[**Creating Directories**](#index_split_000.html#p8)

**To create the directory**

**and the data file:**

Understanding how to read from and write

**1.** Create a new folder called **users**, located

to files on the server is only part of the data

outside of the Web directory root.

storage process. It’s likely you’ll want to

use directories for this purpose as well.

It could be created in the same directory

as the **uploads** folder made earlier

The command for creating a directory in

(see **D** in “Handling File Uploads”).

PHP is **mkdir()**:

**2.** Using the steps outlined in the first sec-

**mkdir(' *directory \_name*', *permissions*);** tion of this chapter, set the permissions

The directory name is the name of the

so that everyone can write to, read

directory to be created. This value can be

from, and search (**0777** in Unix terms)

relative to the current directory (i.e., the

the directory.

one the script is in) or it can be a full path:

If you’re running Windows, this step will

**mkdir('C:\\\\inetpub\\\\users\\\\george');**

most likely not be necessary.

On Windows servers, the permissions are

**3.** In your text editor, create a new, blank

ignored and therefore not required (as in

document.

the preceding example). On non-Windows

**4.** Save this file in the **users** directory with

servers, the permissions are **0777** by

the name **users.txt**.

default (see the section “File Permissions”

earlier in this chapter to learn what those

**5.** Again using the steps outlined earlier

numbers mean).

in the chapter, set the permissions on

**users.txt** so that everyone can write to

With this in mind, let’s create a script that

and read from the file (**0666** in Unix terms).

makes a new directory for a user when the

user registers (the theory being that a user

Again, this will probably not be

could upload files to that directory). This script

necessary if you’re running Windows on

also records the username and password to

your PHP server.

a text file, so that the user can be validated

when logging in. You’ll begin by creating the

**Once you create a directory that PHP can**

parent directory (which must be writable so

**write to, PHP should be able to automatically**

that PHP can create subdirectories in it) and

**create a users.txt file in that directory to**

**which PHP can write. However, it’s best not to**

the **users.txt** data file.

**make assumptions about such things.**

320 Chapter

11

**To create the registration script:**

**1.** Begin a new PHP document in your

text editor or IDE, to be named

**register.php** (**Script 11.6**):

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

➝ **XHTML 1.0 Transitional//EN"**

**"http://www.w3.org/TR/xhtml1/**

 ➝ **DTD/xhtml1-transitional.dtd">**

**<html xmlns="http://www.w3.org/**

➝ **1999/xhtml" xml:lang="en"**

➝ **lang="en">**

**<head>**

**<meta**

**http-equiv="content-type"**

 ➝ **content="text/html;**

 ➝ **charset=utf-8" />**

**<title>Register</title>**

**<style type="text/css"**

 ➝ **media="screen">**

**.error { color: red; }**

**</style>**

**</head>**

**<body>**

**<h1>Register</h1>**

In the page’s head, a CSS class is

defined that will be used to format errors.

continues on page 323

**Script 11.6** The **register.php** script serves two purposes: it records the user's information in a text file and creates a new directory for that user's stuff.

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"

2 "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> 3

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en"> 4 <head>

5

<meta http-equiv="content-type" content="text/html; charset=utf-8" /> 6 <title>Register</title>

7

<style type="text/css" media="screen"> 8

.error { color: red; }

9 </style>

10 </head>

11 <body>

12 <h1>Register</h1>

13 <?php // Script 11.6 - register.php

code continues on next page

Files and Directories 321

**Script 11.6** continued

14

/\* This script registers a user by storing their information in a text file and creating a directory for them. \*/

15

16 // Identify the directory and file to use:

**17 $dir = '../users/';**

**18 $file = $dir . 'users.txt';**

19

20 if ($\_SERVER\['REQUEST\_METHOD'\] == 'POST') { // Handle the form.

21

22

$problem = FALSE; // No problems so far.

23

24

// Check for each value...

25 if (empty($\_POST\['username'\])) {

26 $problem

\=

TRUE;

27

print '<p class="error">Please enter a username!</p>'; 28 }

29

30

if (empty($\_POST\['password1'\])) {

31 $problem

\=

TRUE;

32

print '<p class="error">Please enter a password!</p>'; 33 }

34

35

if ($\_POST\['password1'\] != $\_POST\['password2'\]) {

36 $problem

\=

TRUE;

37

print '<p class="error">Your password did not match your confirmed password!</p>'; 38 }

39

40

if (!$problem) { // If there weren't any problems...

41

**42**

**if (is\_writable($file)) { // Open the file.**

43

44

// Create the data to be written:

**45**

**$subdir = time() . rand(0, 4596);**

**46**

**$data = $\_POST\['username'\] . "\\t" . md5(trim($\_POST\['password1'\])) . "\\t" .**

**$subdir**

**.**

**PHP\_EOL;**

47

48 //

Write

the

data:

**49**

**file\_put\_contents($file, $data, FILE\_APPEND | LOCK\_EX);**

50

51

// Create the directory:

**52**

**mkdir ($dir . $subdir);**

53

54 //

Print

a

message:

55

print '<p>You are now registered!</p>';

56

57

} else { // Couldn't write to the file.

58

print '<p class="error">You could not be registered due to a system error.</p>'; 59 }

60

code continues on next page

322 Chapter

11

**2.** Begin the PHP code and create two

variables:

**<?php // Script 11.6 - register.php**

**$dir = '../users/';**

**$file = $dir . 'users.txt';**

These two variables represent the

directory and file being used by the

example. The file will be in the directory,

so its value starts with the directory’s

value. Change the value of **$dir** so that

it’s appropriate for your situation.

**3.** Check whether the form has been

submitted:

**if ($\_SERVER\['REQUEST\_METHOD'\] ==**

➝ **'POST') {**

Once again, this page both displays

and handles the HTML form. This is

accomplished using a conditional

that checks how the script is being

requested.

continues on next page

**Script 11.6** continued

61

} else { // Forgot a field.

62

print '<p class="error">Please go back and try again!</p>'; 63 }

64

65 } else { // Display the form.

66

67 // Leave PHP and display the form:

68 ?>

69

70 <form action="register.php" method="post"> 71 <p>Username: <input type="text" name="username" size="20" /></p> 72

<p>Password: <input type="password" name="password1" size="20" /></p> 73

<p>Confirm Password: <input type="password" name="password2" size="20" /></p> 74

<input type="submit" name="submit" value="Register" /> 75 </form>

76

77 <?php } // End of submission IF. ?>

78 </body>

79 </html>

Files and Directories 323

**4.** Validate the registration information: an **fopen()** line as the condition instead

**$problem = FALSE;**

(see earlier in the chapter).

**if (empty($\_POST\['username'\])) {**

**7.** Create the data to be written to the file,

**$problem = TRUE;**

and then write it:

**print '<p class="error">Please**

**$subdir = time() . rand(0, 4596);**

 ➝ **enter a username!</p>';**

**$data = $\_POST\['username'\] . "\\t" .**

**}**

➝ **md5(trim($\_POST\['password1'\])) .**

**if (empty($\_POST\['password1'\])) {**

➝ **"\\t" . $subdir . PHP\_EOL;**

**$problem = TRUE;**

**file\_put\_contents($file, $data,**

**print '<p class="error">Please**

➝ **FILE\_APPEND | LOCK\_EX);**

 ➝ **enter a password!</p>';**

**}**

The name of the directory being

**if ($\_POST\['password1'\] != $\_POST**

created is a number based on the time

➝ **\['password2'\]) {**

the user registered and a random value.

**$problem = TRUE;**

This system helps to guarantee that the

**print '<p class="error">Your**

directory created is unique and has a

 ➝ **password did not match your**

valid name.

 ➝ **confirmed password!</p>';**

Instead of storing a single string as you

**}**

previously have, this script stores three

separate pieces of information: the

The registration form is a simpler

user’s name; an encrypted version of

version of earlier registration forms

the password (using the **md5()** function;

developed in this book. The same

see the first tip); and the directory name,

validation process you previously

created in the preceding line. The

developed is used to check the

password is trimmed first, to get rid of

submitted username and passwords.

any extraneous spaces.

The **$problem** variable is used as a flag

to indicate whether a problem occurred.

To distinguish between the pieces of

information, you insert a tab (created

**5.** Check for problems:

using the **\\t** code). A newline is used

**if (!$problem) {**

to mark the end of the line, again using

Again, the **$problem** variable lets you

the **PHP\_EOL** constant.

know if it’s okay to register the user. If no

**8.** Create the user’s directory, and print

problems occurred, it’s safe to continue.

a message:

**6.** Confirm that the **users.txt** file is

**mkdir ($dir . $subdir);**

writable:

**print '<p>You are now**

**if (is\_writable($file)) {**

➝ **registered!</p>';**

Like before, the data file is first

The **mkdir()** function creates the

confirmed as writable in a conditional, so

directory in the **users** directory. The

that the script can respond accordingly.

directory is named whatever random

If you’re not using PHP 5.1 or greater, use

number was generated earlier.

324 Chapter

11

![Image 412](index-346_1.png)

![Image 413](index-346_2.png)

**9.** Complete the conditionals:

**} else { // Couldn't write to**

 ➝ **the file.**

**print '<p class="error">You**

 ➝ **could not be registered due**

**A** The result if the **users.txt** file is not writable.

 ➝ **to a system error.</p>';**

**}**

**} else { // Forgot a field.**

**print '<p class="error">Please**

 ➝ **go back and try again!</p>';**

**}**

The first **else** completes the conditional

if the script couldn’t open the **users.txt**

file for writing **A**. The second **else**

completes the conditional if the user

**B** The script reports any form

failed to complete the form properly

validation errors.

**B**.

**10.** Add an **else** clause to the main condi-

tional, and exit out of PHP:

**} else {**

**?>**

Unlike the previous examples in this

chapter, this PHP script first displays the

form and then handles it. Whereas the

other scripts would then display the form

again, this one does not, as the form

creation is part of an **else** statement.

Because the rest of the page is just HTML,

you exit out of PHP to create the form.

**11.** Display the HTML form:

**<form action="register.php"**

➝ **method="post">**

**<p>Username: <input type="text"**

 ➝ **name="username" size="20" /></p>**

**<p>Password: <input type=**

 ➝ **"password" name="password1"**

 ➝ **size="20" /></p>**

**<p>Confirm Password: <input**

 ➝ **type="password" name=**

 ➝ **"password2" size="20" /></p>**

**<input type="submit" name=**

 ➝ **"submit" value="Register" />**

**</form>**

continues on next page

Files and Directories 325

![Image 414](index-347_1.png)

![Image 415](index-347_2.png)

**12.** Complete the main conditional:

**<?php } // End of submission IF. ?>**

This final closing curly bracket closes

the main submit conditional. For it to

work, a new PHP section must first

be created.

**13.** Complete the HTML page:

**</body>**

**</html>**

**14.** Save the file as **register.php**, place it

**C** The registration form is quite basic but

serves its purpose.

in the proper directory for your PHP-

enabled server, and test it in your Web

browser **C** and **D**.

**15.** If you want, open the **users.txt** file

in your text editor to see its contents

(**Script 11.7**).

**D** This is what the user

sees if the registration

**The md5() function creates a hash: a**

process worked.

**mathematically calculated representation of**

**a string. So this script doesn’t actually store**

**the password but a representation of that**

**password (in theory, no two strings would have**

**the same md5() value). You’ll soon see how the**

**hashed password is used by a login script.**

**You can also ensure that the page**

**worked as it should by looking in the users**

**directory for the new subdirectories.**

**The rmdir() function deletes an exist-**

**ing directory, assuming PHP has permission**

**to do so.**

**Script 11.7** The **users.txt** file lists three tab-delineated fields of information: the username, a scrambled version of the user's password, and their associated directory name.

1 larry

1a1dc91c907325c69271ddf0c944bc72

12936537501284

2 john

0cc175b9c0f1b6a831c399e269772661

1293653788455

3 paul

92eb5ffee6ae2fec3ad71c777531578f

12936537931717

4 george

4a8a08f09d37b73795649038408b5f33

1293653799360

5 ringo

8277e0910d750195b448797616e091ad

12936538042144

326 Chapter

11

[**Reading Files**](#index_split_000.html#p8)

In an example where the data is stored

in a delineated format (commonly

[**Incrementally**](#index_split_000.html#p8)

using a comma, hence a CSV—comma-

separated values—format), you can use

In the **view\_quote.php** script (Script 11.3),

the **fgetcsv()** function instead. It breaks

an entire file was read into an array using

the string into parts, using the marked

the **file()** function. But what if you want

separator, and returns an array:

to read in only a little of the file at a time?

**$array = fgetcsv($fp, *length*,**

Then you need to use the **fgets()** function.

➝ ***delimiter*****);**

The **fgets()** function reads a string of a

**$array = fgetcsv($fp, 1024);**

certain length. It’s most often placed in a

Again, the preceding function call returns

**while** loop that uses the **feof()** function to

1,023 bytes of data, but it breaks the string

make sure the end of the file hasn’t been

into an array using the default delimiter—a

reached. For example:

comma—as an indicator of where to make

**$fp = fopen($file, 'rb');**

elements. This function is the equivalent of

**while (!feof($fp)) {**

using the **fgets()** and **explode()** functions

**$string = fgets($fp, 1024);**

together. If you provide a delimiter

**}**

argument, you can change what character

**fclose ($fp);**

is used to delineate the data.

With that code, 1,023 bytes of data at a

Finally, because these functions rely on

time will be read in, as **fgets()** always

identifying the end of a line, it’s a smart

reads 1 byte less than the length you

extra precaution to enable PHP’s **auto\_**

specify. Or **fgets()** will stop reading once

**detect\_line\_endings** setting. You can do

it reaches the end of the line or the end of

so using the **ini\_set()** function:

the file. The second argument is optional,

**ini\_set('auto\_detect\_line\_endings', 1);**

but if present, it should be a number larger

than a single line of text in the file. If you

As an example, let’s create a login script

want to just read to the end of the line,

that uses the **users.txt** file created in the

omit the length argument:

preceding example. It will continue to read

a file until a matching username/password

**$string = fgets($fp);**

combination has been found.

Files and Directories 327

**To read a file incrementally:**

**2.** Create the PHP section and identify the

file to use:

**1.** Begin a new PHP document in your text

editor or IDE, to be named **login.php**

**<?php // Script 11.8 - login.php**

(**Script 11.8**):

**$file = '../users/users.txt';**

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

The value of **$file** should be the same

➝ **XHTML 1.0 Transitional//EN"**

as that in **register.php**.

**"http://www.w3.org/TR/xhtml1/**

**3.** Check whether the form has been

 ➝ **DTD/xhtml1-transitional.dtd">**

submitted:

**<html xmlns="http://www.w3.org/**

**if ($\_SERVER\['REQUEST\_METHOD'\] ==**

 ➝ **1999/xhtml" xml:lang="en"**

➝ **'POST') {**

➝ **lang="en">**

**<head>**

**4.** Create a dummy variable to use as a flag:

**<meta**

**http-equiv="content-type"**

**$loggedin = FALSE;**

 ➝ **content="text/html;**

The **$loggedin** variable is used to

 ➝ **charset=utf-8" />**

indicate whether the user entered

**<title>Login</title>**

the correct username/password

**</head>**

combination. When the script first

**<body>**

starts, it’s assumed that the user

**<h1>Login</h1>**

has not entered the correct values.

continues on page 380

**Script 11.8** The **login.php** script uses the information stored in **users.txt** (created by Script 11.6) to validate a user.

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"

2 "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> 3

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en"> 4 <head>

5

<meta http-equiv="content-type" content="text/html; charset=utf-8" /> 6 <title>Login</title>

7 </head>

8 <body>

9 <h1>Login</h1>

10 <?php // Script 11.8 - login.php

11 /\* This script logs a user in by check the stored values in text file. \*/

12

13 // Identify the file to use:

**14 $file = '../users/users.txt';**

15

16 if ($\_SERVER\['REQUEST\_METHOD'\] == 'POST') { // Handle the form.

17

18

$loggedin = FALSE; // Not currently logged in.

19

20

// Enable auto\_detect\_line\_settings:

**21 ini\_set('auto\_detect\_line\_endings',**

**1);**

22

code continues on next page

328 Chapter

11

**Script 11.8** continued

23

// Open the file:

**24**

**$fp = fopen($file, 'rb');**

25

26

// Loop through the file:

**27**

**while ( $line = fgetcsv($fp, 200, "\\t") ) {**

28

29

// Check the file data against the submitted data:

**30**

**if ( ($line\[0\] == $\_POST\['username'\]) AND ($line\[1\] == md5(trim($\_POST\['password'\])))**

**) {**

31

**32**

**$loggedin = TRUE; // Correct username/password combination.**

33

34

// Stop looping through the file:

**35**

**break;**

36

37

} // End of IF.

38

39

} // End of WHILE.

40

**41**

**fclose($fp); // Close the file.**

42

43

// Print a message:

44

if ($loggedin) {

45

print '<p>You are now logged in.</p>';

46

} else {

47

print '<p style="color: red;">The username and password you entered do not match those on file.</p>';

48 }

49

50 } else { // Display the form.

51

52 // Leave PHP and display the form:

53 ?>

54

55 <form action="login.php" method="post"> 56 <p>Username: <input type="text" name="username" size="20" /></p> 57

<p>Password: <input type="password" name="password" size="20" /></p> 58

<input type="submit" name="submit" value="Login" /> 59 </form>

60

61 <?php } // End of submission IF. ?>

62

63 </body>

64 </html>

Files and Directories 329

**5.** Open the file for reading:

the submitted password against the

**ini\_set('auto\_detect\_line\_**

stored password (**$line\[1\]**). However,

➝ **endings', 1);**

because the stored password was

**$fp = fopen($file, 'rb');**

scrambled using **md5()**, apply **md5()** to

the submitted value and then make the

Unlike the **file()** function, the

comparison.

**fgetcsv()** function requires a file

**8.** If a match was found, set **$loggedin** to

pointer. Therefore, the **users.txt** file

**TRUE** and exit the **while** loop:

must be opened with the **fopen()**

function, using the appropriate mode.

**$loggedin = TRUE;**

Here, that mode is **rb**, meaning the

**break;**

file should be opened for reading in

If the conditional is **TRUE**, the submitted

a binary safe mode.

username and password match those

First, though, just to be safe, PHP’s

on file. In this case, the **$loggedin** flag

**auto\_detect\_line\_endings** setting

is set to **TRUE**, and the **break** statement

is enabled.

is used to exit the **while** loop. The

benefit of this system is that only as

**6.** Loop through each line of the file:

much of the file is read as is required

**while ( $line = fgetcsv($fp,**

to find a match.

➝ **200, "\\t") ) {**

**9.** Close the conditional, the **while** loop,

This **while** loop reads another

and the file:

200 bytes or one line of the file—

**}**

whichever comes first—with each

**}**

iteration. The data being read is broken

**fclose ($fp);**

into an array, using the tab to indicate

the separate elements.

**10.** Print a message to the user:

Because the **users.txt** file stores

**if ($loggedin) {**

its data in the format username tab

**print '<p>You are now logged**

password tab directory newline, the

 ➝ **in.</p>';**

**$line** array contains three elements

**} else {**

indexed at 0 (username), 1 (password),

**print '<p style="color: red;">**

and 2 (directory).

 ➝ **The username and password you**

**7.** Check the submitted values against the

➝ **entered do not match those on**

retrieved values:

➝ **file.</p>';**

**}**

**if ( ($line\[0\] == $\_POST\['username'\])**

➝ **AND ($line\[1\] == md5(trim($\_POST**

Using the **$loggedin** flag, the script can

➝ **\['password'\]))) ) {**

now say whether the user is “logged in.”

You could add some functionality to this

This two-part conditional checks the

process by storing the user’s directory

submitted username against the stored

in a session and then sending them to a

username (**$line\[0\]**) and checks

file-upload page.

330 Chapter

11

![Image 416](index-352_1.png)

![Image 417](index-352_2.png)

![Image 418](index-352_3.png)

**11.** Continue the main submit conditional,

and exit PHP:

**} else {**

**?>**

**12.** Create the HTML form:

**<form action="login.php"**

➝ **method="post">**

**A** The login form takes a

**<p>Username: <input type="text"**

username and password.

 ➝ **name="username" size="20" /></p>**

**<p>Password: <input type=**

**B** If the submitted

 ➝ **"password" name="password"**

username and password

 ➝ **size="20" /></p>**

match those previously

recorded, the user sees

**<input type="submit" name=**

this message.

 ➝ **"submit" value="Login" />**

**</form>**

**13.** Return to PHP to complete the main

conditional:

**<?php } // End of submission IF. ?>**

**C** The result if the user submits a username and

**14.** Finish the HTML page:

password combination that doesn’t match the

values previously recorded.

**</body>**

**</html>**

**15.** Save the file as **login.php**, place it

in the proper directory for your PHP-

enabled server, and test it in your Web

browser **A**, **B**, and **C**.

**As of PHP 4.3, the fgetcsv() function**

**takes another optional argument: the string**

**being used to enclose the elements.**

**As of PHP 5.3, the fgetcsv() function**

**takes another optional argument: the char-**

**acter used to escape problematic characters.**

**Naturally, the default escape character is the**

**backslash.**

**If a line is blank, fgetcsv() returns an**

**array containing a single null value.**

Files and Directories 331

[**Review and Pursue**](#index_split_000.html#p8)

**Pursue**

Check out some of the other file system

If you have any problems with the review

related functions in the PHP manual

questions or the pursue prompts, turn

[(start at www.php.net/manual/en/ref.](http://www.php.net/manual/en/ref.filesystem.php)

to the book’[s supporting forum (www.](http://www.LarryUllman.com/forum/)

[filesystem.php).](http://www.php.net/manual/en/ref.filesystem.php)

[LarryUllman.com/forum/ ).](http://www.LarryUllman.com/forum/)

Modify **add\_quote.php** so that it con-

firms that the **quotes.txt** file exists,

**Review**

prior to checking if it’s writable.

■

What version of PHP are you running?

Make the text area in **add\_quote.php**

■

What steps did you need to take to

sticky.

make a file or directory writable for

Change **add\_quote.php** so that it

your server?

takes the quotation and the attribution

■

What is the Web root directory (as

as separate inputs and writes them

a concept)? What is the Web root

separately to the text file. Then modify

directory for your Web site (whether on

**view\_quote.php** so that it retrieves and

your own computer or on a live server)?

displays both pieces of data.

■

What are two ways you can write data

Modify **view\_quote.php** so that it dis-

to a file?

plays two random quotations.

■

How do you append new data to

Update **upload\_file.php**, making it

existing files (as opposed to replacing

confirm that the **uploads** directory is

any existing data)?

writable.

■

How do you ensure that new data is

View the PHP manual page for the

placed on its own line?

**glob()** function to see what it can do

■

In order for a form to accept file

and how to use it.

uploads, what attributes must the

Update **list\_dir.php** to display other

opening **form** tag have?

information about the files in a directory.

■

In what variable will a PHP script be

■

Create a system to guarantee unique

able to access an uploaded file? What

usernames in **register.php**. Hint:

function is used to move the file to its

Before you attempt to create the

final destination on the server?

directory, use PHP to check your list

■

How does the **fgetcsv()** function differ

of existing usernames for a match to

from **file()** or **file\_get\_contents()**?

the just-registered name. If no match

is found, the new name is acceptable.

If the username is already in use, then

PHP can create an error message

requesting a new username.

■

Use the combination of writing to and

reading from text files, plus either

sessions or cookies, to create a real

registration and login system.

332 Chapter

11

[**12**](#index_split_000.html#p9)

[Intro to](#index_split_000.html#p9)

[Databases](#index_split_000.html#p9)

The Internet wouldn’t be where it is today

if not for the existence of databases. In

**In This Chapter**

fact, PHP probably wouldn’t be as popular

or as useful if not for its built-in support

Introduction to SQL

334

for numerous types of databases. This

Connecting to MySQL

336

chapter will use MySQL as the example

MySQL Error Handling

340

database management system (DBMS).

Although MySQL—which is available for most

Creating and Selecting a Database

343

platforms—may not be as powerful as the

Creating a Table

347

highest-end commercial database servers,

Inserting Data into a Database

352

MySQL has enough speed and functionality

for most purposes. And its price—free for

Securing Query Data

358

most uses—makes it the common choice

Retrieving Data from a Database

361

for Web development.

Deleting Data in a Database

366

This chapter walks through the development

Updating Data in a Database

372

of a simple database for running a basic

blog. Although you’ll learn enough here to

Review and Pursue

378

get started working with database, you will

want to visit Appendix B, “Resources and

Next Steps,” once you’ve finished this chap-

ter to find some references where you can

learn more about the topic.

![Image 419](index-355_1.jpg)

![Image 420](index-355_2.jpg)

![Image 421](index-355_3.png)

![Image 422](index-355_4.png)

![Image 423](index-355_5.jpg)

![Image 424](index-355_6.png)

![Image 425](index-355_7.png)

![Image 426](index-355_8.png)

![Image 427](index-355_9.jpg)

![Image 428](index-355_10.png)

![Image 429](index-355_11.png)

![Image 430](index-355_12.png)

![Image 431](index-355_13.png)

![Image 432](index-355_14.jpg)

![Image 433](index-355_15.png)

![Image 434](index-355_16.png)

![Image 435](index-355_17.png)

![Image 436](index-355_18.jpg)

![Image 437](index-355_19.png)

![Image 438](index-355_20.png)

![Image 439](index-355_21.png)

[**Introduction to SQL**](#index_split_000.html#p9)

**TABLE 12.1 Common SQL Commands**

A database is a collection of tables (made

**Command**

**Purpose**

up of columns and rows) that stores

**ALTER**

Modifies an existing table

information. Most databases are created,

**CREATE**

Creates a database or table

updated, and read using SQL (Structured

**DELETE**

Deletes records from a table

Query Language). There are surprisingly

few commands in SQL (**Table 12.1** lists the

**DROP**

Deletes a database or table

seven most important), which is both a

**INSERT**

Adds records to a table

blessing and a curse.

**SELECT**

Retrieves records from a table

SQL was designed to be written a lot like

**UPDATE**

Updates records in a table

the English language, which makes it very

user friendly. But SQL is still extremely

capable, even if it takes some thought to

create more elaborate SQL statements

with only the handful of available terms. In

this chapter you’ll learn how to execute all

the fundamental SQL commands.

For people new to PHP, confusion can

**A** PHP will be used to send an SQL statement

to MySQL. MySQL will execute the statement and

stem from PHP’s relationship to HTML

return the result to the PHP script.

(i.e., PHP can be used to generate HTML

but PHP code is never executed in the

Web browser). When you incorporate a

**MySQL Support in PHP**

database, the relationships can become

Support for the MySQL database

even fuzzier. The process is quite simple:

server has to be built into PHP in order

PHP is used to send SQL statements to

for you to use PHP’s MySQL-specific

the database application, where they are

functions. For most PHP installations,

executed. The result of the execution—

this should already be the case. You can

the creation of a table, the insertion of a

confirm support for MySQL by calling

record, the retrieval of some records, or

the **phpinfo()** function, which reveals

even an error—is then returned by the

details of your installation.

database to the PHP script **A**.

When working through this chapter,

With that in mind, PHP’s **mysql\_query()**

if you see an error message saying …

undefined function mysql\_…, this

function will be the most-used tool in this

means the version of PHP you’re using

chapter. It sends an SQL command to MySQL:

doesn’t have support for MySQL (or you

**$result = mysql\_query( *SQL command*,**

misspelled the function name, which you

➝ ***database connection*****);**

should also check).

Enabling support for MySQL takes a

little effort, but it can be done if you

have administrative-level control over

your server. For more information,

see the PHP manual.

334 Chapter

12

![Image 440](index-356_1.png)

![Image 441](index-356_2.png)

I start this chapter with this prologue

Next, you would take the printed query and

because the addition of SQL and MySQL

execute it using another application. The

to the Web development process will

two most common options are:

complicate things. When problems occur—

■

The MySQL client **B**, a command-line

and undoubtedly they will—you’ll need to

tool for interacting with MySQL

know how solve them.

■

phpMyAdmin **C**, a PHP-based MySQL

When a PHP script that interacts with a

interface

MySQL database does not perform as

One or both of these should be provided to

expected, the first step is to determine

you by your hosting company or the software

if the problem is in the query itself—

you installed on your own computer. For a

number 1 in **A**—or in the results of the

demonstration of using each, see Appendix A,

query—number 2 in **A**. To take this step,

“Installation and Configuration.”

you can start by printing out the query

being executed, using code such as

the following:

**Technically, a DBMS, or database**

**application, is the software that interfaces with**

**print $query;**

**the database proper. However, most people use**

**the terms database and DBMS synonymously.**

Assuming that **$query** represents the

complete SQL command, often containing

**Lots of other applications are available**

the values of PHP variables, this one,

**for interacting with MySQL aside from the**

simple line will reveal to you the actual

**MySQL client and phpMyAdmin. Some are free,**

SQL statement being run.

**and others cost. A quick search using Google**

**for MySQL, admin, and your operating system**

**should turn up some interesting results.**

**B** The MySQL client

comes with the MySQL

database software and

can be used to execute

queries without the

need for a PHP script.

**C** phpMyAdmin is perhaps the most popular software written in PHP. It provides a Web-based interface for a MySQL database.

Intro to Databases 335

[**Connecting to MySQL**](#index_split_000.html#p9)

When you worked with text files in Chapter

11, “Files and Directories,” you saw that

some functions, such as **fwrite()** and

**fgets()**, require that you first create a file

pointer using **fopen()**. This pointer then

acts as a reference to that open file. You

use a similar process when working with

databases. First, you have to establish a

connection to the database server (in this

case, MySQL). This connection is then

used as the access point for any future

commands. The syntax for connecting to

a database is

**$dbc = mysql\_connect( *hostname*,**

***username*****, *password*);**

The database connection (assigned to

**$dbc** in the above) is established using at

least three arguments: the host, which is

almost always localhost; the username; and

the password for that username.

If you’re using a database through a

hosting company, the company will most

likely provide you with the host name,

username, and password to use. If you’re

running MySQL on your own computer, see

Appendix A to learn how you create a user.

Once you’re done working with a

database, you can close the connection,

just as you’d close an open file:

**mysql\_close($dbc);**

The PHP script will automatically close

the database connection when the script

terminates, but it’s considered good form

to formally close the connection once it’s

no longer needed.

For the first example of this chapter, you’ll

write a simple script that attempts to

connect to MySQL. Once you have this

connection working, you can proceed

through the rest of the chapter.

336 Chapter

12

**Script 12.1** Being able to connect to the MySQL

**To connect to MySQL:**

server is the most important step. This script tests

that process.

**1.** Begin a new PHP document in

your text editor or IDE, to be named

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

**mysql\_connect.php** (**Script 12.1**):

1.0 Transitional//EN"

2

"http://www.w3.org/TR/xhtml1/DTD/

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

xhtml1-transitional.dtd">

➝ **XHTML 1.0 Transitional//EN"**

3

<html xmlns="http://www.w3.org/1999/

**"http://www.w3.org/TR/xhtml1/**

xhtml" xml:lang="en" lang="en">

 ➝ **DTD/xhtml1-transitional.dtd">**

4 <head>

5

<meta http-equiv="content-type"

**<html xmlns="http://www.w3.org/**

content="text/html; charset=utf-8" />

➝ **1999/xhtml" xml:lang="en"**

6

<title>Connect to MySQL</title>

➝ **lang="en">**

7 </head>

**<head>**

8 <body>

**<meta**

**http-equiv="content-type"**

9

<?php // Script 12.1 - mysql\_connect.php

10

/\* This script connects to the MySQL

 ➝ **content="text/html;**

server. \*/

 ➝ **charset=utf-8" />**

11

**<title>Connect to MySQL</title>**

12

// Attempt to connect to MySQL and print

**</head>**

out messages:

**<body>**

**13 if ($dbc = mysql\_connect('localhost',**

**'username', 'password')) {**

**2.** Start the section of PHP code:

14

15

print '<p>Successfully connected to

**<?php // Script 12.1 -**

MySQL!</p>';

➝ **mysql\_connect.php**

16

**3.** Connect to MySQL, and report on

**17**

**mysql\_close($dbc); // Close the**

**connection.**

the results:

18

**if ($dbc = mysql\_connect**

19 } else {

➝ **('localhost', 'username',**

20

21

print '<p style="color: red;">Could

➝ **'password')) {**

not connect to MySQL.</p>';

**print '<p>Successfully connected**

22

 ➝ **to MySQL!</p>';**

23 }

**mysql\_close($dbc);**

24

**} else {**

25 ?>

26 </body>

**print '<p style="color:**

27 </html>

 ➝ **red;">Could not connect to**

 ➝ **MySQL.</p>';**

**}**

By placing the connection attempt as

the condition in an **if-else** statement,

you make it easy to report on whether

the connection worked.

This chapter will continue to use

username and password as values.

continues on next page

Intro to Databases 337

![Image 442](index-359_1.png)

![Image 443](index-359_2.png)

For your scripts, you’ll need to replace

these with the values provided by

your Web host or set them when you

add a user using the steps outlined in

Appendix A.

If a connection was established, a

**A** If PHP has support for MySQL and the

positive message is printed and then

username/password/host combination you used

the connection is closed. Otherwise, a

was correct, you should see this simple message.

message stating the opposite is printed,

and there is no need to close the database

connection (because it wasn’t opened).

**4.** Complete the PHP code and the

HTML page:

**?>**

**</body>**

**</html>**

**5.** Save the file as **mysql\_connect.php**,

place it in the proper directory of your

PHP-enabled computer, and test it in

your Web browser **A**.

If you see results like those in **B**, double-

check the username and password

values. They should match up with

those provided to you by your Web host

or those you used to create the user.

You can always test your connection

username and password by using them in

the MySQL client (again, see Appendix A).

If you see call to undefined function

mysql\_connect…, your version of

PHP doesn’t support MySQL (see the

“MySQL Support in PHP” sidebar).

**B** If PHP couldn’t connect

to MySQL, you’ll probably

see something like this. The

warning message may or may

not appear, depending on your

error management settings.

338 Chapter

12

 **The database connection ($dbc in this**

**MySQL Extensions**

**case) in most mysql\_ *something*() functions**

**is optional. Regardless of that, in this book**

PHP can communicate with MySQL using

**you’ll see it always used, as it’s not optional in**

different extensions. The first, used in

**the mysqli\_ *something*() functions and you**

this chapter, is the “standard” MySQL

**should be prepared to provide the database**

extension. It has been around for years

**connection when you move to those functions**

and works with all versions of PHP and

**later (see the “MySQL Extensions” sidebar).**

MySQL. All of the standard MySQL

**The localhost value is used as the**

extension functions begin with mysql\_.

**hostname when both the PHP script and the**

The second extension is called MySQLi

**MySQL database reside on the same com-**

(Improved MySQL Extension). This

**puter. You can use PHP to connect to a MySQL**

**database running on a remote server by**

extension was added in PHP 5 and

**changing the hostname in the PHP script and**

can be used with MySQL 4.1 or greater.

**creating the proper permissions in MySQL.**

These functions all begin with mysqli\_

and take advantage of some of the

**PHP has built-in support for most**

added features in MySQL. If possible,

**databases, including dBase, FilePro, SQLite,**

it’s preferable to use the MySQLi

**MySQL, Oracle, PostgreSQL, and Sybase. If**

functions, but as the older extension

**you’re using a type of database that doesn’t**

is more universally enabled, this book

**have direct support—for example, Access or**

**SQL Server—you’ll need to use PHP’s ODBC**

uses it exclusively. See the PHP manual

**(Open Database Connectivity) functions along**

or my book PHP 6 and MySQL 5 for

**with that database’s ODBC drivers to interface**

Dynamic Web Sites: Visual QuickPro

**with the database.**

Guide (Peachpit Press, 2007) for details

on the MySQLi extension.

**The combination of using PHP and**

**MySQL is so common that you may run across**

**terms that identify servers configured with**

**both PHP and MySQL: LAMP, MAMP, and**

**WAMP. These stand for the operating system—**

**Linux, Mac OS X, or Windows—plus the Apache**

**Web server, the MySQL DBMS, and PHP.**

**You’ll be working with MySQL, so all**

**the functions you use in this chapter are**

**MySQL specific. For example, to connect to**

**a database in MySQL the proper function is**

**mysql\_connect(), but if you’re using Post-**

**greSQL, you’d instead write pg\_connect(). If**

**you aren’t using a MySQL DBMS, use the PHP**

[**manual (available through www.PHP.net) to**](http://www.PHP.net)

**find the appropriate function names.**

Intro to Databases 339

[**MySQL Error Handling**](#index_split_000.html#p9)

Before this chapter gets too deep into

working with MySQL, it would be best to

discuss some error-handling techniques up

front. Common errors you’ll encounter are

■

Failure to connect to MySQL

■

Failure to select a database

■

Inability to run a query

■

No results returned by a query

■

Data not inserted into a table

Experience will teach you why these errors

normally occur, but immediately seeing

what the problem is when running your

scripts can save you much debugging

time. To have your scripts give informative

reports about errors that occur, use the

**mysql\_error()** function. This function

returns a textual version of the error that

the MySQL server returned.

Along with this function, you may want to

use some PHP tools for handling errors.

Specifically, the error suppression operator

(**@**), when used preceding a function

name, suppresses any error messages

or warnings the function might invoke:

**@ *function\_name*();**

Note that this operator doesn’t stop the

error from happening; it just prevents

the message from being immediately

displayed. You’d use it in situations where

you intend to handle the error yourself,

should one occur.

340 Chapter

12

**To use error handling:**

**1.** Open **mysql\_connect.php** (Script 12.1) in

your text editor or IDE.

**2.** Suppress any PHP errors created by the

**mysql\_connect()** function by changing

the **if** conditional as follows (**Script 12.2**):

**if ($dbc = @mysql\_connect**

➝ **('localhost', 'username',**

➝ **'password')) {**

Rather than have PHP print out an error

message when the **mysql\_connect()**

function backfires (**B** in the previous

section), the message will be suppressed

here using the **@** symbol. The errors still

occur, but they’re handled by the change

made in the next step.

continues on next page

**Script 12.2** By adding error control to the script (the **@** symbol and the **mysql\_error()** function), you can more purposefully address problems that occur.

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"

2 "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> 3

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en"> 4 <head>

5

<meta http-equiv="content-type" content="text/html; charset=utf-8" /> 6

<title>Connect to MySQL</title>

7 </head>

8 <body>

9

<?php // Script 12.2 - mysql\_connect.php #2

10 /\* This script connects to the MySQL server. \*/

11

12 // Attempt to connect to MySQL and print out messages:

**13 if ($dbc = @mysql\_connect('localhost', 'username', 'password')) {**

14

15

print '<p>Successfully connected to MySQL!</p>';

16

17

mysql\_close($dbc); // Close the connection.

18

19 } else {

20

**21**

**print '<p style="color: red;">Could not connect to MySQL:<br />' . mysql\_error() . '.</p>';** 22

23 }

24

25 ?>

26 </body>

27 </html>

Intro to Databases 341

![Image 444](index-363_1.png)

**3.** Add the **mysql\_error()** function to the

**In this chapter, error messages are**

**print** statement in the **else** section:

**revealed to assist in the debugging process.**

**Live Web sites should not have this level of**

**print '<p style="color: red;">Could**

**explicit error messages shown to the user.**

➝ **not connect to MySQL:<br />' .**

➝ **mysql\_error() . '.</p>';**

**You can use the @ symbol to suppress**

**errors, notices, or warnings stemming from**

Instead of printing a message or relying

**any function, not just a MySQL-related one.**

on whatever error PHP kicks out (see **B**

**For example:**

in the previous section), the script

**@include('./filename.php');**

now prints the MySQL error within this

context. You accomplish this by printing

**You may also see code where die(),**

some HTML concatenated with the

**which is an alias for exit(), is called when a**

**mysql\_error()** function.

**connection error occurs. The thinking is that**

**since a database connection cannot be made,**

You should note that the **mysql\_error()**

**there’s no point in continuing. In my opinion,**

function, in this case, is not provided

**that’s too heavy-handed of an approach.**

with the database connection—**$dbc**—

as an argument, since no database

connection was made.

**4.** Save the file and test it again in your

Web browser **A**.

If there was a problem, this result now

looks better than what would have been

shown previously. If the script connected,

the result is like that shown in **A** in the

previous section, because neither of the

error-management tools is involved.

**A** Using PHP’s error-control functions, you can adjust how errors are handled.

342 Chapter

12

the DBMS itself—and establish the initial

[**Creating and Selecting**](#index_split_000.html#p9)

database for you. If you’re working on your

own server or have administrative access,

[**a Database**](#index_split_000.html#p9)

you should have the capability to create

Before a PHP script can interact with

new users and databases.

a database, the database must first be

To create a database with PHP, you use the

selected. Of course, in order for you to

**mysql\_query()** function to execute a **CREATE**

select a database, it must exist. You can

**DATABASE** ***databasename*** SQL command:

create a database using PHP, the MySQL

client, phpMyAdmin, or any number of

**mysql\_query('CREATE DATABASE somedb',**

tools, as long as the MySQL hostname/

➝ **$dbc);**

username/password combination you are

Once you’ve done this, you can select the

using has permission to do so.

database using **mysql\_select\_db()**:

Database permissions are a bit more

**mysql\_select\_db('somedb', $dbc);**

complicated than file permissions, but you

Note that you have to create a database

need to understand this: Different types of

only once, but it must always be selected

users can be assigned different database

before any other queries are run on it. In

capabilities. For example, one DBMS user

other words, some readers will need to

may be able to create new databases

perform the first step, but every reader must

and delete existing ones (you may have

take the second step with every PHP script.

dozens of databases in your DBMS), but a

lower-level user may only be able to create

In this example, you’ll create a new

and modify tables within a single database.

database and then select it. To repeat,

The most basic user may just be able to

creating a database requires that you have

read from, but not modify, tables.

administrator access. If your Web host

restricts your access, the hosting company

If you’re using PHP and MySQL for a live,

should create the initial database for you

hosted site, the hosting company will most

upon request; you can just write the second

likely give you the second type of access—

part of this script, which selects the database.

control over a single database but not

Intro to Databases 343

**To create and select a database:**

**1.** Open **mysql\_connect.php** (Script 12.2)

in your text editor or IDE.

**2.** After the first **print** statement,

create the new database, if necessary

(**Script 12.3**):

**if (@mysql\_query('CREATE DATABASE**

➝ **myblog', $dbc)) {**

**print '<p>The database has been**

 ➝ **created!</p>';**

**} else {**

**print '<p style="color: red;">**

 ➝ **Could not create the database**

 ➝ **because:<br />' .**

 ➝ **mysql\_error($dbc) . '.</p>');**

**}**

If you need to create the database,

use this construct to handle the task

**Script 12.3** Creating a new database consists of three steps: connecting to the database, running a **CREATE**

**DATABASE** query using the **mysql\_query()** function, and then closing the connection.

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"

2 "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> 3

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en"> 4 <head>

5

<meta http-equiv="content-type" content="text/html; charset=utf-8" /> 6

<title>Create the Database</title>

7 </head>

8 <body>

9

<?php // Script 12.3 - create\_db.php

10 /\* This script connects to the MySQL server. It also creates and selects the database. \*/

11

12 // Attempt to connect to MySQL and print out messages:

13 if ($dbc = @mysql\_connect('localhost', 'username', 'password')) {

14

15

print '<p>Successfully connected to MySQL!</p>';

16

17

// Try to create the database:

**18**

**if (@mysql\_query('CREATE DATABASE myblog', $dbc)) {**

**19**

**print '<p>The database has been created!</p>';**

**20**

**} else { // Could not create it.**

**21**

**print '<p style="color: red;">Could not create the database because:<br />' .**

**mysql\_error($dbc) . '.</p>';**

**22 }**

23

code continues on next page

344 Chapter

12

cleanly and effectively. The query—

**CREATE** **DATABASE** **myblog**—is run using

the **mysql\_query()** function. The **@**

symbol is used to suppress any error

messages, which are instead handled

by **print** in conjunction with the **mysql\_**

**error()** function in the **else** clause.

Note that this invocation of **mysql\_**

**error()** can be provided with the

specific database connection: **$dbc**.

If the database has already been

created for you, skip this step.

**3.** Attempt to select the database:

**if (@mysql\_select\_db('myblog',**

➝ **$dbc)) {**

**print '<p>The database has been**

 ➝ **selected!</p>';**

**} else {**

**print '<p style="color: red;">**

 ➝ **Could not select the database**

 ➝ **because:<br />' .**

 ➝ **mysql\_error($dbc) . '.</p>';**

**}**

continues on next page

**Script 12.3** continued

24

// Try to select the database:

**25**

**if (@mysql\_select\_db('myblog', $dbc)) {**

**26**

**print '<p>The database has been selected!</p>';**

**27**

**} else {**

**28**

**print '<p style="color: red;">Could not select the database because:<br />' .**

**mysql\_error($dbc) . '.</p>';**

**29 }**

30

31

mysql\_close($dbc); // Close the connection.

32

33 } else {

34

35

print '<p style="color: red;">Could not connect to MySQL:<br />' . mysql\_error() . '.</p>'; 36

37 }

38

39 ?>

40 </body>

41 </html>

Intro to Databases 345

![Image 445](index-367_1.png)

![Image 446](index-367_2.png)

This conditional has the same structure

as that in Step 2. If PHP can select the

database, a message is printed. If it

can’t select the database, the specific

MySQL error will be displayed instead.

Every PHP script that runs queries on a

**A** If the database could be created

and selected, you’ll see this result in

database must connect to MySQL and

the Web browser.

select the database in order to work.

**4.** If you want, change the page title to

reflect this script’s new purpose:

**<title>Create the Database</title>**

**5.** Save your script as **create\_db.php**,

place it in the proper directory for your

PHP-enabled server, and test it in your

Web browser **A** and **B**.

**You probably won’t create databases**

**with any frequency and may not normally**

**do so using a PHP script. Still, this example**

**demonstrates both how you execute simple**

**queries using PHP as well as the SQL**

**command needed to create a database.**

**You haven’t done so in these examples,**

**but in general it’s a good idea to set your**

**database information—hostname, username,**

**password, and database name—as variables**

**or constants. Then you can plug them into the**

**appropriate functions. By doing so, you can**

**separate the database specifics from the func-**

**tionality of the script, allowing you to easily**

**port that code to other applications.**

**B** If the MySQL user doesn’t have the authority to create a database, you’ll see a message like this. A similar result will occur if the user doesn’t have permission to select the database.

346 Chapter

12

A table’s primary key is a special column

[**Creating a Table**](#index_split_000.html#p9)

of unique values that is used to refer to the

Once you’ve created and selected the initial

table’s rows. The database makes an index

database, you can begin creating individual

of this column in order to more quickly

tables in it. A database can consist of multiple

navigate through the table. A table can have

tables, but in this simple example you’ll create

only one primary key, which you normally

one table in which all the chapter’s data will

set up as an automatically incremented

be stored.

column of integers. The first row has a key

of 1, the second has a key of 2, and so forth.

To create a table in the database, you’ll

Referring back to the key always retrieves

use SQL—the language that databases

the values for that row.

understand. Because SQL is a lot like

spoken English, the proper query to

You can visit the MySQL Web site for more

create a new table reads like this:

information on SQL and column definitions.

By following the directions in this section,

**CREATE TABLE tablename (column1**

though, you should be able to accomplish

➝ ***definition*****, column2 *definition*,** some basic database tasks. The table that

➝ **etc.)**

you’ll create in this example is represented

For each column, separated by commas,

by **Table 12.2**.

you first indicate the column name and

In this example, you’ll create the database

then the column type. Common types

table that will be used to store information

are **TEXT,** **VARCHAR** (a variable number of

submitted via an HTML form. In the next

characters), **DATETIME**, and **INT** (integer).

section of the chapter, you’ll write the script

Because it’s highly recommended that you

that inserts the submitted data into the

create a column that acts as the primary

table created here.

key (a column used to refer to each row),

a simple **CREATE** statement could be

**CREATE TABLE my\_table (**

**id INT PRIMARY KEY,**

**information TEXT**

**)**

**TABLE 12.2 The entries Table**

**Column Name**

**Column Type**

**entry\_id**

Positive, non-null, automatically incrementing integer

**title**

Text up to 100 characters in length

**entry**

Text of any length

**date\_entered**

A timestamp including both the date and the time the

row was added

Intro to Databases 347

**To create a new table:**

**1.** Begin a new PHP document in your

text editor or IDE, to be named

**create\_table.php** (**Script 12.4**):

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

➝ **XHTML 1.0 Transitional//EN"**

**"http://www.w3.org/TR/xhtml1/**

 ➝ **DTD/xhtml1-transitional.dtd">**

**<html xmlns="http://www.w3.org/**

➝ **1999/xhtml" xml:lang="en"**

➝ **lang="en">**

**<head>**

**<meta**

**http-equiv="content-type"**

 ➝ **content="text/html;**

 ➝ **charset=utf-8" />**

**<title>Create a Table</title>**

**</head>**

**<body>**

**Script 12.4** To create a database table, define the appropriate SQL statement and then invoke the **mysql\_query()** function.

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"

2 "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> 3

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en"> 4 <head>

5

<meta http-equiv="content-type" content="text/html; charset=utf-8" /> 6

<title>Create a Table</title>

7 </head>

8 <body>

9

<?php // Script 12.4 - create\_table.php

10 /\* This script connects to the MySQL server, selects the database, and creates a table. \*/

11

12 // Connect and select:

13 if ($dbc = @mysql\_connect('localhost', 'username', 'password')) {

14

15

// Handle the error if the database couldn't be selected:

16

if (!@mysql\_select\_db('myblog', $dbc)) {

17

print '<p style="color: red;">Could not select the database because:<br />' .

mysql\_error($dbc) . '.</p>';

18 mysql\_close($dbc);

19 $dbc

\=

FALSE;

20 }

21

22 } else { // Connection failure.

23

print '<p style="color: red;">Could not connect to MySQL:<br />' . mysql\_error() . '.</p>'; 24 }

code continues on next page

348 Chapter

12

![Image 447](index-370_1.png)

**Script 12.4** continued

**2.** Begin a section of PHP code:

25

**<?php // Script 12.4 -**

26 if ($dbc) {

➝ **create\_table.php**

27

**3.** Connect to the MySQL server, and

28

// Define the query:

**29**

**$query = 'CREATE TABLE entries (**

select the database:

**30 entry\_id INT UNSIGNED NOT NULL**

**if ($dbc = @mysql\_connect**

**AUTO\_INCREMENT PRIMARY KEY,**

➝ **('localhost', 'username',**

**31 title VARCHAR(100) NOT NULL,**

**32 entry TEXT NOT NULL,**

➝ **'password')) {**

**33 date\_entered DATETIME NOT NULL**

**if**

**(!@mysql\_select\_db('myblog',**

**34 )';**

 ➝ **$dbc)) {**

35

**print '<p style="color:**

36

// Execute the query:

 ➝ **red;">Could not select the**

**37**

**if (@mysql\_query($query, $dbc)) {**

**38**

**print '<p>The table has been**

 ➝ **database because:<br />' .**

**created!</p>';**

 ➝ **mysql\_error($dbc) . '.</p>';**

**39**

**} else {**

**mysql\_close($dbc);**

**40**

**print '<p style="color: red;">**

**$dbc = FALSE;**

**Could not create the table**

**}**

**because:<br />' .**

**mysql\_error($dbc) . '.</p>**

**} else {**

**<p>The query being run was: ' .**

**print '<p style="color:**

**$query . '</p>';**

 ➝ **red;">Could not connect to**

**41 }**

 ➝ **MySQL:<br />' . mysql\_error()**

42

 ➝ **. '.</p>';**

**43**

**mysql\_close($dbc); // Close the**

**connection.**

**}**

44

This is an alternative version of the

45 }

code used in the preceding script. The

46 ?>

47 </body>

main difference is that no messages

48 </html>

are printed if each step was successful

(hopefully you have connection and

database selection working by this point).

If for some reason a connection could

not be made to the database, or the

database could not be selected, then

error messages will be displayed **A**.

If a connection could be made but

the database could not be selected,

**A** Between the MySQL error message and

the connection is then closed, as the

printing out the query being executed, you should

be able to figure out what the problem is if the

connection won’t be useful. To indicate

script does not work properly.

that scenario, the **$dbc** variable, which

had represented the connection, is set

to **FALSE**, which will prevent the **CREATE**

query from being executed (see Step 4).

continues on next page

Intro to Databases 349

![Image 448](index-371_1.png)

**4.** Define the query for creating the table:

row added (**AUTO** **INCREMENT**) and stand

**if ($dbc) {**

as the primary key.

**$query = 'CREATE TABLE entries (**

The next two columns consist of text.

**entry\_id INT UNSIGNED NOT NULL**

One, called **title**, is limited to 100

➝ **AUTO\_INCREMENT PRIMARY KEY,**

characters. The second, **entry**, can

**title VARCHAR(100) NOT NULL,**

be vast in size. Each of these fields is

**entry TEXT NOT NULL,**

also marked as **NOT** **NULL**, making them

**date\_entered DATETIME NOT NULL**

required fields.

**)';**

Finally, the **date\_entered** column is

First, if **$dbc** still has a value, the table

a timestamp that marks when each

can be created. If not—meaning that

record was added to the table.

no connection could be made or the

**5.** Execute the query:

database couldn’t be selected—then none

**if (@mysql\_query($query, $dbc)) {**

of the following code will be executed.

**print '<p>The table has been**

As for the query itself, let’s break that

 ➝ **created.</p>';**

into more recognizable parts. First, to

**} else {**

create a new table, you write **CREATE**

**print '<p style="color:**

**TABLE** ***tablename*** (where tablename is

 ➝ **red;">Could not create the**

replaced by the desired table name).

 ➝ **table because:<br />' .**

Then, within parentheses, you list every

 ➝ **mysql\_error($dbc) .**

column you want with each column

 ➝ **'.</p><p>The query being run**

separated by a comma. Your table and

 ➝ **was: ' . $query . '</p>';**

column names should be alphanumeric,

**}**

with no spaces.

To create the table, call the **mysql\_**

The first column in the table is called

**query()** function using the **$query**

**entry\_id**; it’s an unsigned integer

variable as the first argument and the

(**INT** **UNSIGNED**—which means that it

database connection as the second. If

can only be a positive whole number).

a problem occurred, the MySQL error is

By including the words **NOT** **NULL**, you

printed, along with the value of the **$query**

indicate that this column must have

variable. This last step—printing the actual

a value for each row. The values

query being executed—is a particularly

automatically increase by 1 for each

useful debugging technique **B**.

**B** If the query caused an error, the MySQL error will be reported and the query itself displayed (for debugging purposes).

350 Chapter

12

![Image 449](index-372_1.png)

**6.** Close the database connection and

complete the **$dbc** conditional:

**mysql\_close($dbc);**

**}**

**7.** Complete the PHP code and the HTML

page:

**C** If all went well, all you’ll see is this message.

**?>**

**</body>**

**</html>**

**8.** Save the script as **create\_table.php**,

place it in the proper directory for your

PHP-enabled server, and test it in your

Web browser **C**.

**It’s not necessary to write your SQL**

**keywords in all capital letters as I do here, but**

**doing so helps to distinguish the SQL terms**

**from the table and column names.**

**On larger Web applications, I highly**

**recommended that you place the database**

**connection and selection code (lines 13**

**through 24 here) in a separate file, located**

**outside of the Web directory. Then, each page**

**that requires the database can include this**

**external file. You’ll see an example of this in**

**Chapter 13, “Putting It All Together.”**

**The mysql\_query() function returns**

**TRUE if a query was successfully run on a data-**

**base. That result doesn’t necessarily mean the**

**desired result occurred.**

**This chapter presents the basics of**

**MySQL- and SQL-related knowledge (including**

**column types). You’ll want to check out other**

**resources—listed in Appendix B—once you’re**

**comfortable with the fundamentals.**

**You wouldn’t normally use a PHP script**

**to create a table, just as you wouldn’t normally**

**create a database using a PHP script, but**

**when you’re just starting with MySQL, this is**

**an easy way to achieve the desired results.**

Intro to Databases 351

[**Inserting Data**](#index_split_000.html#p9)

if you’re populating a slew of columns.

In either case, you must be certain to list

[**into a Database**](#index_split_000.html#p9)

the right number and type of values for

each column.

As mentioned, this database will be used

The values are placed within parentheses,

as a simple blog, an online journal. Blog

with each value separated by a comma.

entries—consisting of a title and text—will

Non-numeric values—strings and dates—

be added to the database using one page

need to be quoted, whereas numbers

and then displayed on another page.

do not:

With the last script, you created the table,

**INSERT INTO example (name, age)**

which consists of four columns: **entry\_id**,

➝ **VALUES ('Jonah', 1)**

**title**, **entry**, and **date\_entered**. The

process of adding information to a table is

The query is executed using the **mysql\_**

similar to creating the table itself in terms

**query()** function. Because **INSERT** queries

of which PHP functions you use, but the

can be complex, it makes sense to assign

SQL query is different. To insert records,

each query to a variable and send that

use the **INSERT** SQL command with either

variable to the **mysql\_query()** function

of the following syntaxes:

(as previously demonstrated).

**INSERT INTO *tablename*** **VALUES ( *value1*,**

To demonstrate, let’s create a page that

➝ ***value2*****, *value3*, etc.)**

adds blog entries to the database. Like

**INSERT INTO *tablename*** **( *column1\_name*,** many of the examples in the preceding

➝ ***column2\_name*****) VALUES ( *value1*, *value2*)** chapter, this one will both display and

handle the HTML form. Before getting into

The query begins with **INSERT** **INTO**

the example, though, I’ll say that this script

***tablename***. Then you can either specify

knowingly has a security hole in it; it’ll be

which columns you’re inserting values for

explained and fixed in the next section of

or not. The latter is more specific and is

the chapter.

therefore preferred, but it can be tedious

**Building on This Example**

The focus in this chapter is on explaining and demonstrating the basics of using PHP with MySQL. This also includes the core components of SQL. However, this chapter’s examples do a few things that you wouldn’t want to do in a real site, such as allow anyone to insert, edit, and delete database records.

In the next chapter, a different example will be developed that is also database driven. That example will use cookies to restrict what users can do with the site.

352 Chapter

12

**To enter data into a database**

**from an HTML form:**

**1.** Begin a new PHP document in your text

editor or IDE, to be named **add\_entry.**

**php** (**Script 12.5**):

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

➝ **XHTML 1.0 Transitional//EN"**

**"http://www.w3.org/TR/xhtml1/**

 ➝ **DTD/xhtml1-transitional.dtd">**

**<html xmlns="http://www.w3.org/**

➝ **1999/xhtml" xml:lang="en"**

➝ **lang="en">**

**<head>**

**<meta**

**http-equiv="content-type"**

 ➝ **content="text/html;**

 ➝ **charset=utf-8" />**

**<title>Add a Blog Entry</title>**

**</head>**

**<body>**

**<h1>Add a Blog Entry</h1>**

continues on next page

**Script 12.5** The query statement for adding information to a database is straightforward enough, but be sure to match the number of values in parentheses to the number of columns in the database table.

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"

2 "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> 3

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en"> 4 <head>

5

<meta http-equiv="content-type" content="text/html; charset=utf-8" /> 6

<title>Add a Blog Entry</title>

7 </head>

8 <body>

9

<h1>Add a Blog Entry</h1>

10 <?php // Script 12.5 - add\_entry.php

11 /\* This script adds a blog entry to the database. \*/

12

13 if ($\_SERVER\['REQUEST\_METHOD'\] == 'POST') { // Handle the form.

14

15

// Connect and select:

16

$dbc = mysql\_connect('localhost', 'username', 'password');

17 mysql\_select\_db('myblog',

$dbc);

18

19

// Validate the form data:

20

$problem = FALSE;

21

if (!empty($\_POST\['title'\]) && !empty($\_POST\['entry'\])) {

code continues on next page

Intro to Databases 353

**2.** Create the initial PHP section and check At this point, if you’re running these

for the form submission:

examples in order, I’ll assume you have

**<?php // Script 12.5 -**

a working connection and selection

➝ **add\_entry.php**

process down, so I’ll dispense with all

**if ($\_SERVER\['REQUEST\_METHOD'\] ==**

the conditionals and error reporting

➝ **'POST') {**

(mostly to shorten the script). If you have

problems connecting to and selecting

**3.** Connect to and select the database:

the database, apply the code already

**$dbc = mysql\_connect('localhost',**

outlined in the chapter.

➝ **'username', 'password');**

**mysql\_select\_db('myblog', $dbc);**

**Script 12.5** continued

22 $title

\=

trim(strip\_tags($\_POST\['title'\]));

23 $entry

\=

trim(strip\_tags($\_POST\['entry'\]));

24

} else {

25

print '<p style="color: red;">Please submit both a title and an entry.</p>'; 26 $problem

\=

TRUE;

27 }

28

29

if (!$problem) {

30

31

// Define the query:

**32**

**$query = "INSERT INTO entries (entry\_id, title, entry, date\_entered) VALUES**

**(0, '$title', '$entry', NOW())";**

33

34

// Execute the query:

**35**

**if (@mysql\_query($query, $dbc)) {**

**36**

**print '<p>The blog entry has been added!</p>';**

**37 }**

**else**

**{**

**38**

**print '<p style="color: red;">Could not add the entry because:<br />' .**

**mysql\_error($dbc) . '.</p><p>The query being run was: ' . $query . '</p>';** **39 }**

40

41

} // No problem!

42

43

mysql\_close($dbc); // Close the connection.

44

45 } // End of form submission IF.

46

47 // Display the form:

48 ?>

49 <form action="add\_entry.php" method="post"> 50

<p>Entry Title: <input type="text" name="title" size="40" maxsize="100" /></p> 51

<p>Entry Text: <textarea name="entry" cols="40" rows="5"></textarea></p> 52

<input type="submit" name="submit" value="Post This Entry!" /> 53 </form>

54 </body>

55 </html>

354 Chapter

12

![Image 450](index-376_1.png)

**4.** Validate the form data:

**$problem = FALSE;**

**if (!empty($\_POST\['title'\]) &&**

➝ **!empty($\_POST\['entry'\])) {**

**$title = trim(strip\_tags**

 ➝ **($\_POST\['title'\]));**

**$entry = trim(strip\_tags**

 ➝ **($\_POST\['entry'\]));**

**} else {**

**print '<p style="color:**

 ➝ **red;">Please submit both a**

**A** The PHP script performs some basic form

validation so that empty records are not inserted

 ➝ **title and an entry.</p>';**

into the database.

**$problem = TRUE;**

**}**

Before you use the form data in an

**INSERT** query, it ought to be validated.

Just a minimum of validation is used

here, guaranteeing that some values

are provided. If so, new variables are

assigned those values, after trimming

away extraneous spaces and applying

**strip\_tags()** (to prevent cross-site

scripting attacks and other potential

problems). If either of the values was

empty, an error message is printed **A**

and the **$problem** flag variable is set to

**TRUE** (because there is a problem).

**5.** Define the **INSERT** query:

**if (!$problem) {**

**$query = "INSERT INTO entries**

 ➝ **(entry\_id, title, entry,**

 ➝ **date\_entered) VALUES**

 ➝ **(0, '$title', '$entry', NOW())";**

The query begins with the necessary

**INSERT** **INTO** ***tablename*** code. Then it lists the columns for which values will be

submitted. After that is **VALUES**, followed

by four values (one for each column,

in order) separated by commas. When

assigning this query to the **$query**

variable, use double quotation marks so

that the values of the variables will

continues on next page

Intro to Databases 355

![Image 451](index-377_1.png)

be automatically inserted by PHP. The

As an essential debugging tool, if the

**$title** and **$entry** variables are strings,

query didn’t run properly, the MySQL

so they must be placed within single

error and the query being run are both

quotation marks in the query itself.

printed to the Web browser **B**.

Because the **entry\_id** column has been

**7.** Close the **$problem** conditional, the

set to **AUTO\_INCREMENT**, you can use 0 as

database connection, and complete the

the value and MySQL will automatically

main conditional and the PHP section:

use the next logical value for that column.

**} // No problem!**

To set the value of the **date\_entered**

**mysql\_close($dbc);**

column, use the MySQL **NOW()** function. It

**} // End of form submission IF.**

inserts the current time as that value.

**?>**

**6.** Run the query on the database:

From here on out, the form will

**if (@mysql\_query($query, $dbc)) {**

be displayed.

**print '<p>The blog entry has**

**8.** Create the form:

 ➝ **been added!</p>';**

**} else {**

**<form action="add\_entry.php"**

**print '<p style="color: red;">**

➝ **method="post">**

 ➝ **Could not add the entry**

**<p>Entry Title: <input type=**

 ➝ **because:<br />' . mysql\_**

 ➝ **"text" name="title" size="40"**

 ➝ **error($dbc) . '.</p><p>The**

 ➝ **maxsize="100" /></p>**

 ➝ **query being run was: ' .**

**<p>Entry Text: <textarea**

 ➝ **$query . '</p>';**

 ➝ **name="entry" cols="40"**

**}**

 ➝ **rows="5"></textarea></p>**

**<input type="submit" name=**

The query, once defined, is run using the

 ➝ **"submit" value="Post This**

**mysql\_query()** function. By calling this

 ➝ **Entry!" />**

function as the condition of an **if-else**

**</form>**

statement, you can print simple messages

indicating the result of the query execution.

**B** If the **INSERT** query didn’t work, the MySQL error is printed along with the query that was run.

356 Chapter

12

![Image 452](index-378_1.png)

![Image 453](index-378_2.png)

The HTML form is very simple, requiring

only a title for the blog entry and the

entry itself. As a good rule of thumb,

use the same name for your form inputs

as the corresponding column names in

the database. Doing so makes errors

less likely.

**9.** Finish the HTML page:

**</body>**

**</html>**

**10.** Save the script as **add\_entry.php**,

place it in the proper directory for your

**C** This is the form for adding an entry to the database.

PHP-enabled server, and test it in your

Web browser **C** and **D**.

You should probably avoid using

apostrophes in your form values or

you might see results like those in **B**.

Turn the page for the explanation

and solution.

**D** If the **INSERT** query ran properly, a message

is printed and the form is displayed again.

**MySQL allows you to insert several**

**records at once, using this format:**

**INSERT INTO *tablename*** **( *column1\_name*,**

➝ ***column2\_name*****) VALUES ( *value1*,**

➝ ***value2*****), ( *value3*, *value4*);** **Most other database applications don’t support this construct, though.**

**To retrieve the automatically incremented**

**number created for an AUTO\_INCREMENT col-**

**umn, call the mysql\_insert\_id() function.**

**Because of the way auto-incrementing**

**primary keys work, this query is also fine:**

**INSERT INTO entries (title, entry,**

➝ **date\_entered) VALUES ('$title',**

➝ **'$entry', NOW())";**

Intro to Databases 357

![Image 454](index-379_1.png)

[**Securing Query Data**](#index_split_000.html#p9)

The initial apostrophe in the provided entry

title has the effect of completing the blog

As I mentioned in the introduction to the

title value part of the query. The semicolon

preceding sequence of steps, the code as

then terminates the **INSERT** query

written has a pretty bad security hole in it.

itself. This will make the original query

As it stands, if someone submits text that

syntactically invalid. Then the database will

contains an apostrophe, that data will break

be provided with a second query—**DROP**

the SQL query **A** (security concerns aside,

**TABLE entries**, with the hope that it will be

it’s also a pretty bad bug). The result is

executed when the original **INSERT** query

obviously undesirable, but why is it insecure?

fails. This is called an SQL injection attack,

but fortunately it’s easy to prevent.

If a malicious user knows they can break

a query by typing an apostrophe, they

To do so, send potentially insecure

may try to run their own queries using this

data to be used in a query through the

hole. If someone submitted ‘;DROP TABLE

**mysql\_real\_escape\_string()** function.

entries; as the blog post title, the resulting

This function will escape—preface with

query would be

a backslash—any potentially harmful

**INSERT INTO entries (entry\_id,**

characters, making the data safe to use

in a query:

➝ **title, entry, date\_entered) VALUES**

➝ **(0, '';DROP TABLE entries;', '<entry**

**$var = mysql\_real\_escape\_string**

➝ **text>', NOW())**

➝ **($var, $dbc);**

Let’s apply this function to the preceding script.

**A** The apostrophe

in the conjunction

It’s breaks the

query because

apostrophes (or

single quotation

marks) are used to

delimit strings used

in queries.

**Showing MySQL Errors**

Even if MySQL doesn’t execute an injected SQL command (normally MySQL will only run a single SQL query sent through the **mysql\_query()** function), hackers will provide bad characters in form data in the hopes that the syntactically broken query generates a database error. By seeing the database error, the hacker seeks to gain knowledge about the database that can be used for malicious purposes. For this reason, it’s imperative that a live site never reveal the actual MySQL errors or queries being executed. The scripts in this chapter do so only for your own debugging purposes.

358 Chapter

12

**To secure query data:**

These two lines will greatly improve the

security and functionality of the script. For

**1.** Open **add\_entry.php** (Script 12.5)

both posted variables, their values are first

in your text editor or IDE, if it is not

trimmed and stripped of tags, then sent

already open.

through **mysql\_real\_escape\_string()**.

**2.** Update the assignment of the **$title**

The result will be safe to use in the query.

and **$entry** variables to read (**Script 12.6**)

If the application of three functions to one

as follows:

variable is too confusing for you, you can

**$title = mysql\_real\_escape\_string**

separate the code into discrete steps:

➝ **(trim(strip\_tags($\_POST**

**$title = $\_POST\['title'\];**

➝ **\['title'\])), $dbc);**

**$title = trim(strip\_tags($title));**

**$entry = mysql\_real\_escape\_string**

**$title = mysql\_real\_escape\_**

➝ **(trim(strip\_tags($\_POST**

**string($title, $dbc);**

➝ **\['entry'\])), $dbc);**

continues on next page

**Script 12.6** To better secure the Web application and the database, the **mysql\_real\_escape\_string()** function is applied to the form data used in the query.

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"

2 "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> 3

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en"> 4 <head>

5

<meta http-equiv="content-type" content="text/html; charset=utf-8" /> 6

<title>Add a Blog Entry</title>

7 </head>

8 <body>

9

<h1>Add a Blog Entry</h1>

10 <?php // Script 12.6 - add\_entry.php #2

11 /\* This script adds a blog entry to the database. It now does so securely! \*/

12

13 if (isset($\_POST\['submitted'\])) { // Handle the form.

14

15

// Connect and select:

16

$dbc = mysql\_connect('localhost', 'username', 'password');

17 mysql\_select\_db('myblog',

$dbc);

18

19

// Validate and secure the form data:

20

$problem = FALSE;

21

if (!empty($\_POST\['title'\]) && !empty($\_POST\['entry'\])) {

**22**

**$title = mysql\_real\_escape\_string(trim(strip\_tags($\_POST\['title'\])), $dbc);** **23**

**$entry = mysql\_real\_escape\_string(trim(strip\_tags($\_POST\['entry'\])), $dbc);** 24

} else {

25

print '<p style="color: red;">Please submit both a title and an entry.</p>'; 26 $problem

\=

TRUE;

27 }

28

code continues on next page

Intro to Databases 359

![Image 455](index-381_1.png)

![Image 456](index-381_2.png)

**3.** Save the script, place it on your PHP-

enabled server, and test it in your Web

browser **B** and **C**.

**If you see (later in the chapter) that the**

**displayed blog posts have extra backslashes**

**before apostrophes, this is likely because**

**you’re using a version of PHP with Magic**

**Quotes enabled. (Magic Quotes automatically**

**escapes problematic characters in form**

**B** Now apostrophes in form data…

**data, although not as well as mysql\_real\_**

**escape\_string()). If that’s the case, you’ll**

**need to apply the stripslashes() function**

**to remove the extraneous slashes from the**

**submitted values:**

**$title = mysql\_real\_escape\_string**

➝ **(stripslashes(trim(strip\_tags**

**C** …will not cause problems.

➝ **($\_POST\['title'\]))), $dbc);**

**Script 12.6** continued

29

if (!$problem) {

30

31

// Define the query:

32

$query = "INSERT INTO entries (entry\_id, title, entry, date\_entered) VALUES (0, '$title',

'$entry', NOW())";

33

34

// Execute the query:

35

if (@mysql\_query($query, $dbc)) {

36

print '<p>The blog entry has been added!</p>';

37 }

else

{

38

print '<p style="color: red;">Could not add the entry because:<br />' .

mysql\_error($dbc) . '.</p><p>The query being run was: ' . $query . '</p>'; 39 }

40

41

} // No problem!

42

43

mysql\_close($dbc); // Close the connection.

44

45 } // End of form submission IF.

46

47 // Display the form:

48 ?>

49 <form action="add\_entry.php" method="post"> 50

<p>Entry Title: <input type="text" name="title" size="40" maxsize="100" /></p> 51

<p>Entry Text: <textarea name="entry" cols="40" rows="5"></textarea></p> 52

<input type="submit" name="submit" value="Post This Entry!" /> 53

<input type="hidden" name="submitted" value="true" /> 54 </form>

55 </body>

56 </html>

360 Chapter

12

This is a good example of how SQL uses

[**Retrieving Data**](#index_split_000.html#p9)

only a few terms effectively and flexibly.

[**from a Database**](#index_split_000.html#p9)

The main difference in retrieving data from

a database as opposed to inserting data

The next process this chapter demonstrates

into a database is that you need to handle

for working with databases is retrieving

the query differently. You should first assign

data from a populated table. You still use

the results of the query to a variable:

the **mysql\_query()** function to run the

query, but retrieving data is slightly different

**$result = mysql\_query($query, $dbc);**

than inserting data—you have to assign

Just as **$dbc** is a reference to an open

the query result to a variable and then use

database connection, **$result** is a reference

another function in order to fetch the data.

to a query result set. This variable is then

The basic syntax for retrieving data is the

provided to the **mysql\_fetch\_array()**

**SELECT** query:

function, which retrieves the query results:

**SELECT *what columns*** **FROM *what table***

**$row = mysql\_fetch\_array($result);**

The easiest query for reading data from a

The function fetches one row from the

table is

result set at a time, creating an array

in the process. The array will use the

**SELECT \* FROM *tablename***

selected column names as its indexes:

The asterisk is the equivalent of saying

**$row\['name'\]**, **$row\['email'\]**, and so on.

every column. If you only require certain

As with any array, you must refer to the

columns to be returned, you can limit your

columns exactly as they’re defined in the

query, like so:

database (the keys are case-sensitive).

**SELECT name, email FROM users**

So, in this example, you must use

**$row\['email'\]** instead of **$row\['Email'\]**.

This query requests that only the

information from two columns (**name** and

If the query will return multiple rows,

**email**) be gathered. Keep in mind that

execute the **mysql\_fetch\_array()** function

this structure doesn’t limit what rows (or

within a loop to access them all:

records) are returned, just what columns

**while ($row = mysql\_fetch\_array**

for those rows.

➝ **($result)) {**

Another way to alter your query is to add

**// Do something with $row.**

a conditional restricting which rows are

**}**

returned, accomplished using a **WHERE** clause:

With each iteration of the loop, the

**SELECT \* FROM users WHERE**

next row of information from the query

➝ **name='Larry'**

(referenced by **$result**) is assigned to an

array called **$row**. This process continues

Here you want the information from every

until no more rows of information are

column in the table, but only from the rows

found. Within the loop, you would do

where the **name** column is equal to Larry.

whatever you want with **$row**.

continues on next page

Intro to Databases 361

![Image 457](index-383_1.png)

The best way to understand this new code

is to try it. You’ll write a script that retrieves

the posts stored in the **entries** table and

displays them **A**. You may want to run

through **add\_entry.php** a couple more

times to build up the table first.

**To retrieve data from a table:**

**1.** Begin a new PHP document in your

text editor or IDE, to be named

**view\_entries.php** (**Script 12.7**):

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

**A** This dynamic Web page uses PHP to pull data

➝ **XHTML 1.0 Transitional//EN"**

from a database.

**"http://www.w3.org/TR/xhtml1/**

 ➝ **DTD/xhtml1-transitional.dtd">**

**<html xmlns="http://www.w3.org/**

➝ **1999/xhtml" xml:lang="en"**

➝ **lang="en">**

**<head>**

**<meta**

**http-equiv="content-type"**

 ➝ **content="text/html;**

 ➝ **charset=utf-8" />**

**<title>View My Blog</title>**

**</head>**

**<body>**

**<h1>My**

**Blog</h1>**

**Script 12.7** The SQL query for retrieving all data from a table is quite simple; but in order for PHP to access every returned record, you must loop through the results one row at a time.

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"

2 "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> 3

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en"> 4 <head>

5

<meta http-equiv="content-type" content="text/html; charset=utf-8" /> 6

<title>View My Blog</title>

7 </head>

8 <body>

9 <h1>My

Blog</h1>

10 <?php // Script 12.7 - view\_entries.php

11 /\* This script retrieves blog entries from the database. \*/

12

code continues on next page

362 Chapter

12

**2.** Begin a PHP section and connect to

the order in which they were entered

the database:

(recorded in the **date\_entered** column),

starting with the most recent first. This

**<?php // Script 12.7 -**

last option is set by **DESC**, which is short

➝ **view\_entries.php**

for descending. If the query was **ORDER**

**$dbc = mysql\_connect('localhost',**

**BY** **date\_entered** **ASC**, the most recently

➝ **'username', 'password');**

added record would be retrieved last.

**mysql\_select\_db('myblog', $dbc);**

**4.** Run the query:

**3.** Define the **SELECT** query:

**if ($r = mysql\_query($query,**

**$query = 'SELECT \* FROM entries**

➝ **$dbc)) {**

➝ **ORDER BY date\_entered DESC';**

The **SELECT** query is run like any

This basic query tells the database

other. However, the result of the

that you’d like to fetch every column

query is assigned to a **$result**

of every row in the **entries** table. The

(or, more tersely, **$r**) variable, which

returned records should be sorted, as

will be referenced later.

indicated by the **ORDER** **BY** clause, by

continues on next page

**Script 12.7** continued

13 // Connect and select:

14 $dbc = mysql\_connect('localhost', 'username', 'password');

15 mysql\_select\_db('myblog',

$dbc);

16

17 // Define the query:

**18 $query = 'SELECT \* FROM entries ORDER BY date\_entered DESC';** 19

20 if ($r = mysql\_query($query, $dbc)) { // Run the query.

21

22

// Retrieve and print every record:

**23**

**while ($row = mysql\_fetch\_array($r)) {**

**24 print**

**"<p><h3>{$row\['title'\]}</h3>**

**25 {$row\['entry'\]}<br**

**/>**

**26 <a**

**href=\\"edit\_entry.php?id={$row\['entry\_id'\]}\\">Edit</a>** **27 <a**

**href=\\"delete\_entry.php?id={$row\['entry\_id'\]}\\">Delete</a>** **28 </p><hr**

**/>\\n";**

**29 }**

30

31 } else { // Query didn't run.

32

print '<p style="color: red;">Could not retrieve the data because:<br />' . mysql\_error($dbc)

. '.</p><p>The query being run was: ' . $query . '</p>'; 33 } // End of query IF.

34

35 mysql\_close($dbc); // Close the connection.

36

37 ?>

38 </body>

39 </html>

Intro to Databases 363

**5.** Print out the returned results:

**while ($row = mysql\_fetch\_array**

➝ **($r)) {**

**print**

**"<p><h3>{$row\['title'\]}</h3>**

**{$row\['entry'\]}<br**

**/>**

**<a**

**href=\\"edit\_entry.php?id=**

 ➝ **{$row\['entry\_id'\]}\\">Edit</a>**

**<a**

**href=\\"delete\_entry.php?**

 ➝ **id={$row\['entry\_id'\]}\\">**

 ➝ **Delete</a>**

**</p><hr**

**/>\\n";**

**}**

This loop sets the variable **$row** to an

array containing the first record returned

in **$r**. The loop then executes the

following command (the **print** statement).

Once the loop gets back to the beginning,

it assigns the next row, if it exists. It

continues to do this until there are no

more rows of information to be obtained.

Within the loop, the array’s keys are

the names of the columns from the

table—hence, **entry\_id**, **title**, and

**entry** (there’s no need to print out the

**date\_entered**).

At the bottom of each post, two links

are created: to **edit\_entry.php** and

**delete\_entry.php**. These scripts will

be written in the rest of the chapter.

Each link passes the posting’s database

ID value along in the URL. That

information will be necessary for those

other two pages to edit and delete the

blog posting accordingly.

**6.** Handle the errors if the query didn’t run:

**} else { // Query didn't run.**

**print '<p style="color: red;">**

 ➝ **Could not retrieve the**

 ➝ **data because:<br />' .**

 ➝ **mysql\_error($dbc) . '.</p>**

 ➝ **<p>The query being run**

 ➝ **was: ' . $query . '</p>';**

**} // End of query IF.**

364 Chapter

12

![Image 458](index-386_1.png)

![Image 459](index-386_2.png)

If the query couldn’t run on the database,

it should be printed out, along with the

MySQL error (for debugging purposes).

**7.** Close the database connection:

**mysql\_close($dbc);**

**8.** Complete the PHP section and the

HTML page:

**?>**

**</body>**

**</html>**

**B** Thanks to the **SELECT** query, which orders the

**9.** Save the script as **view\_entries.php**,

returned records by the date they were entered,

place it in the proper directory for your

the most recently added entry is always listed first.

PHP-enabled server, and test it in your

Web browser **A**.

**10.** If you want, add another record to the

blog using the **add\_entry.php** page

(Script 12.6), and run this page again **B**.

**11.** Check the source code of the page to

see the dynamically generated links **C**.

**The mysql\_fetch\_array() function**

**takes another argument, which is a constant**

**indicating what kind of array should be**

**C** Part of the HTML source of the page. Note that

the two links have ?id=X appended to each URL.

**returned. MYSQL\_ASSOC returns an associative**

**array, whereas MYSQL\_NUM returns a**

**numerically indexed array.**

**The mysql\_num\_rows() function**

**returns the number of records returned**

**by a SELECT query.**

**It’s possible to paginate returned records**

**so that 10 or 20 appear on each page (like the**

**way Google works). Doing so requires more**

**advanced coding than can be taught in this book,**

**though. See my book PHP 6 and MySQL 5**

**for Dynamic Web Sites: Visual QuickPro**

**Guide (Peachpit Press, 2007), or look online**

**for code examples and tutorials.**

Intro to Databases 365

![Image 460](index-387_1.png)

![Image 461](index-387_2.png)

[**Deleting Data in**](#index_split_000.html#p9)

[**a Database**](#index_split_000.html#p9)

Sometimes you might also want to run a

**DELETE** query on a database. Such a query

removes records from the database. The

syntax for a delete query is

**DELETE FROM *tablename*** **WHERE**

**A** When the user arrives at this page, the blog

➝ ***column*****\= *value***

entry is shown and the user must confirm that they

want to delete it.

The **WHERE** clause isn’t required, but if it’s

omitted, you’ll remove every record from

the table. You should also understand that

once you delete a record, there’s no way

to recover it (unless you have a backup of

the database).

As a safeguard, if you want to delete only

a single record from a table, add the **LIMIT**

**B** If the delete query worked

properly, the user sees this result.

clause to the query:

**DELETE FROM *tablename*** **WHERE**

➝ ***column*****\= *value*** **LIMIT 1**

This clause ensures that only one record

is deleted at most. Once you’ve defined

your query, it’s again executed using the

**mysql\_query()** function, like any other query.

To see if a **DELETE** query worked, you can use

the **mysql\_affected\_rows()** function. This

function returns the number of rows affected

by an **INSERT**, **DELETE**, or **UPDATE** query.

As an example, let’s write the **delete\_**

**entry.php** script, which is linked from the

**view\_blog.php** page. This page receives

the database record ID in the URL. It then

displays the entry to confirm that the user

wants to delete it **A**. If the user clicks the

button, the record will be deleted **B**.

366 Chapter

12

**To delete data from a database:**

**1.** Begin a new PHP document in your

text editor or IDE, to be named

**delete\_entry.php** (**Script 12.8**):

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

➝ **XHTML 1.0 Transitional//EN"**

**"http://www.w3.org/TR/xhtml1/**

 ➝ **DTD/xhtml1-transitional.dtd">**

**<html xmlns="http://www.w3.org/**

➝ **1999/xhtml" xml:lang="en"**

➝ **lang="en">**

**<head>**

**<meta**

**http-equiv="content-type"**

 ➝ **content="text/html;**

 ➝ **charset=utf-8" />**

**<title>Delete a Blog Entry**

 ➝ **</title>**

**</head>**

**<body>**

**<h1>Delete an Entry</h1>**

**2.** Start the PHP code and connect to

the database:

**<?php // Script 12.8 -**

➝ **delete\_entry.php**

**$dbc = mysql\_connect('localhost',**

➝ **'username', 'password');**

**mysql\_select\_db('myblog', $dbc);**

continues on page 369

**Script 12.8** The **DELETE** SQL command permanently removes a record (or records) from a table.

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"

2 "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> 3

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en"> 4 <head>

5

<meta http-equiv="content-type" content="text/html; charset=utf-8" /> 6

<title>Delete a Blog Entry</title>

7 </head>

8 <body>

9

<h1>Delete an Entry</h1>

10 <?php // Script 12.8 - delete\_entry.php

11 /\* This script deletes a blog entry. \*/

12

code continues on next page

Intro to Databases 367

**Script 12.8** continued

13 // Connect and select:

14 $dbc = mysql\_connect('localhost', 'username', 'password');

15 mysql\_select\_db('myblog',

$dbc);

16

17 if (isset($\_GET\['id'\]) && is\_numeric($\_GET\['id'\]) ) { // Display the entry in a form: 18

19

// Define the query:

20

$query = "SELECT title, entry FROM entries WHERE entry\_id={$\_GET\['id'\]}"; 21

if ($r = mysql\_query($query, $dbc)) { // Run the query.

22

23

$row = mysql\_fetch\_array($r); // Retrieve the information.

24

25

// Make the form:

26

print '<form action="delete\_entry.php" method="post"> 27

<p>Are you sure you want to delete this entry?</p>

28

<p><h3>' . $row\['title'\] . '</h3>' .

29

$row\['entry'\] . '<br />

30

<input type="hidden" name="id" value="' . $\_GET\['id'\] . '" /> 31

<input type="submit" name="submit" value="Delete this Entry!" /></p> 32 </form>';

33

34

} else { // Couldn't get the information.

35

print '<p style="color: red;">Could not retrieve the blog entry because:<br />' .

mysql\_error($dbc) . '.</p><p>The query being run was: ' . $query . '</p>'; 36 }

37

38 } elseif (isset($\_POST\['id'\]) && is\_numeric($\_POST\['id'\])) { // Handle the form.

39

40

// Define the query:

**41**

**$query = "DELETE FROM entries WHERE entry\_id={$\_POST\['id'\]} LIMIT 1";** **42**

**$r = mysql\_query($query, $dbc); // Execute the query.**

43

44

// Report on the result:

**45**

**if (mysql\_affected\_rows($dbc) == 1) {**

**46**

**print '<p>The blog entry has been deleted.</p>';**

**47**

**} else {**

**48**

**print '<p style="color: red;">Could not delete the blog entry because:<br />' .**

**mysql\_error($dbc) . '.</p><p>The query being run was: ' . $query . '</p>';** **49 }**

50

51 } else { // No ID received.

52

print '<p style="color: red;">This page has been accessed in error.</p>'; 53 } // End of main IF.

54

55 mysql\_close($dbc); // Close the connection.

56

57 ?>

58 </body>

59 </html>

368 Chapter

12

![Image 462](index-390_1.png)

**3.** If the page received a valid entry

ID in the URL, define and execute

a **SELECT** query:

**if (isset($\_GET\['id'\]) && is\_numeric**

➝ **($\_GET\['id'\]) ) {**

**$query = "SELECT title, entry**

 ➝ **FROM entries WHERE**

 ➝ **entry\_id={$\_GET\['id'\]}";**

**if ($r = mysql\_query($query,**

**C** If the script does not receive an ***id*** value in the URL, an error is reported.

 ➝ **$dbc)) {**

To display the blog entry, the page must

confirm that a numeric ID is received

by the page. Because that value should

first come in the URL (when the user

clicks the link in **view\_blog.php**, see **C**

in the previous section), you reference

**$\_GET\['id'\]**.

The query is like the **SELECT** query

used in the preceding example, except

that the **WHERE** clause has been added

to retrieve a specific record. Also,

because only the two stored values

are necessary—the title and the entry

itself—only those are being selected.

This query is then executed using the

**mysql\_query()** function.

**4.** Retrieve the record, and display the

entry in a form:

**$row = mysql\_fetch\_array($r);**

**print '<form action="delete\_entry.**

➝ **php" method="post">**

**<p>Are you sure you want to**

➝ **delete this entry?</p>**

**<p><h3>' . $row\['title'\] . '</h3>' .**

**$row\['entry'\] . '<br />**

**<input type="hidden" name="id"**

➝ **value="' . $\_GET\['id'\] . '" />**

**<input type="submit" name="submit"**

➝ **value="Delete this Entry!" /></p>**

**</form>';**

continues on next page

Intro to Databases 369

Instead of retrieving all the records

**6.** Check for the submission of the form:

using a **while** loop, as you did in the

**} elseif (isset($\_POST\['id'\]) &&**

previous example, use one call to the

➝ **is\_numeric($\_POST\['id'\]))**

**mysql\_fetch\_array()** function to

➝ **{ // Handle the form.**

assign the returned record to the **$row**

variable. Using this array, the record to

This **elseif** clause is part of the

be deleted can be displayed.

conditional begun in Step 3. It

corresponds to the second usage

The form first shows the blog entry

of this same script (the form being

details, much as it did in the **view\_blog.**

submitted). If this conditional is **TRUE**,

**php** script. When the user clicks the

the record should be deleted.

button, the form will be submitted back

to this page, at which point the record

**7.** Define and execute the query:

should be deleted. In order to do so,

**$query = "DELETE FROM entries**

the blog identification number, which

➝ **WHERE entry\_id={$\_POST\['id'\]}**

is passed to the script as **$\_GET\['id'\]**,

➝ **LIMIT 1";**

must be stored in a hidden input so

**$r = mysql\_query($query, $dbc);**

that it exists in the **$\_POST** array upon

This query deletes the record whose

submission (because **$\_GET\['id'\]** won’t

**entry\_id** has a value of **$\_POST\['id'\]**.

have a value at that point).

The ID value comes from the form,

**5.** Report an error if the query failed:

where it’s stored as a hidden input. By

**} else { // Couldn't get the**

adding the **LIMIT** **1** clause to the query,

➝ **information.**

you can guarantee that only one record,

**print '<p style="color: red;">**

at most, is removed.

 ➝ **Could not retrieve the blog**

**8.** Check the result of the query:

 ➝ **entry because:<br />' .**

**if (mysql\_affected\_rows($dbc) ==**

 ➝ **mysql\_error($dbc) . '.</p>**

➝ **1) {**

 ➝ **<p>The query being run was:**

**print '<p>The blog entry has**

 ➝ **' . $query . '</p>';**

 ➝ **been deleted.</p>';**

**}**

**} else {**

If the **SELECT** query failed to run, the

**print '<p style="color: red;">**

MySQL error and the query itself are

 ➝ **Could not delete the blog**

printed out.

 ➝ **entry because:<br />' .**

 ➝ **mysql\_error($dbc) . '.</p>**

 ➝ **<p>The query being run**

 ➝ **was: ' . $query . '</p>';**

**}**

370 Chapter

12

The **mysql\_affected\_rows()** function

returns the number of rows altered by

the most recent query. If the query ran

properly, one row was deleted, so this

function should return 1. If so, a message

is printed. Otherwise, the MySQL error and

query are printed for debugging purposes.

**9.** Complete the main conditional:

**} else { // No ID received.**

**print '<p style="color: red;">**

 ➝ **This page has been accessed**

 ➝ **in error.</p>';**

**} // End of main IF.**

If no numeric ID value was passed to

this page using either the GET method

or the POST method, then this **else**

clause takes effect **C**.

**10.** Close the database connection, and

complete the page:

**mysql\_close($dbc);**

**?>**

**</body>**

**</html>**

**11.** Save the script as **delete\_entry.php**,

place it in the proper directory for your

PHP-enabled server, and test it in your

Web browser **A** and **B**.

To test this script, you must first run

**view\_blog.php**. Then, click one of the

Delete links to access **delete\_entry.php**.

**You can empty a table of all of its records**

**by running the query TRUNCATE TABLE**

***tablename*****. This approach is preferred over**

**using DELETE FROM *tablename*. TRUNCATE will**

**completely drop and rebuild the table, which is**

**better for the database.**

**It’s a fairly common error to try to run**

**the query DELETE \* FROM *tablename*, like a**

**SELECT query. Remember that DELETE doesn’t**

**use the same syntax as SELECT, because you**

**aren’t deleting specific columns.**

Intro to Databases 371

![Image 463](index-393_1.png)

![Image 464](index-393_2.png)

[**Updating Data**](#index_split_000.html#p9)

[**in a Database**](#index_split_000.html#p9)

The final type of query this chapter will

cover is **UPDATE**. It’s used to alter the values

of a record’s columns. The syntax is

**UPDATE *tablename*** **SET *column1\_name*\=**

➝ ***value*****, *column2\_name*\= *value2*** **WHERE**

➝ ***some\_column*****\= *value***

As with any other query, if the values are

strings, they should be placed within single

**A**

quotation marks:

When the user arrives at the edit page, the

form is shown with the existing values.

**UPDATE users SET first\_name=**

➝ **'Eleanor', age=7 WHERE user\_id=142**

As with a **DELETE** query, you should use

a **WHERE** clause to limit the rows that are

affected. If you don’t do this, every record

in the database will be updated.

To test that an update worked, you can

again use the **mysql\_affected\_rows()**

**B** Upon submitting the form, the user

function to return the number of records

sees a message like this.

altered.

To demonstrate, let’s write a page for

editing a blog entry. It will let the user

alter an entry’s title and text, but not the

date entered or the blog ID number (as a

primary key, the ID number should never

be changed). This script will use a structure

like that in **delete\_entry.php** (Script 12.8),

first showing the entry **A**, and then

handling the submission of that form **B**.

372 Chapter

12

**To update data in a database:**

**1.** Begin a new PHP document in your

text editor or IDE, to be named

**edit\_entry.php** (**Script 12.9**).

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

➝ **XHTML 1.0 Transitional//EN"**

**"http://www.w3.org/TR/xhtml1/**

 ➝ **DTD/xhtml1-transitional.dtd">**

**<html xmlns="http://www.w3.org/**

➝ **1999/xhtml" xml:lang="en"**

➝ **lang="en">**

**<head>**

**<meta**

**http-equiv="content-type"**

 ➝ **content="text/html;**

 ➝ **charset=utf-8" />**

**<title>Edit a Blog Entry</title>**

**</head>**

**<body>**

**<h1>Edit an Entry</h1>**

continues on page 375

**Script 12.9** You can edit records in a database table by using an **UPDATE** SQL command.

1

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"

2 "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> 3

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en"> 4 <head>

5

<meta http-equiv="content-type" content="text/html; charset=utf-8" /> 6

<title>Edit a Blog Entry</title>

7 </head>

8 <body>

9

<h1>Edit an Entry</h1>

10 <?php // Script 12.9 - edit\_entry.php

11 /\* This script edits a blog entry using an UPDATE query. \*/

12

13 // Connect and select:

14 $dbc = mysql\_connect('localhost', 'username', 'password');

15 mysql\_select\_db('myblog',

$dbc);

16

17 if (isset($\_GET\['id'\]) && is\_numeric($\_GET\['id'\]) ) { // Display the entry in a form: 18

19

// Define the query.

20

$query = "SELECT title, entry FROM entries WHERE entry\_id={$\_GET\['id'\]}"; 21

if ($r = mysql\_query($query, $dbc)) { // Run the query.

22

23

$row = mysql\_fetch\_array($r); // Retrieve the information.

24

code continues on next page

Intro to Databases 373

**Script 12.9** continued

25

// Make the form:

26

print '<form action="edit\_entry.php" method="post"> 27

<p>Entry Title: <input type="text" name="title" size="40" maxsize="100" value="' .

htmlentities($row\['title'\]) . '" /></p>

28

<p>Entry Text: <textarea name="entry" cols="40" rows="5">' . htmlentities($row\['entry'\]) . '</

textarea></p>

29

<input type="hidden" name="id" value="' . $\_GET\['id'\] . '" /> 30

<input type="submit" name="submit" value="Update this Entry!" /> 31 </form>';

32

33

} else { // Couldn't get the information.

34

print '<p style="color: red;">Could not retrieve the blog entry because:<br />' . mysql\_

error($dbc) . '.</p><p>The query being run was: ' . $query . '</p>'; 35 }

36

37 } elseif (isset($\_POST\['id'\]) && is\_numeric($\_POST\['id'\])) { // Handle the form.

38

39

// Validate and secure the form data:

40

$problem = FALSE;

41

if (!empty($\_POST\['title'\]) && !empty($\_POST\['entry'\])) {

42

$title = mysql\_real\_escape\_string(trim(strip\_tags($\_POST\['title'\])), $dbc); 43

$entry = mysql\_real\_escape\_string(trim(strip\_tags($\_POST\['entry'\])), $dbc); 44

} else {

45

print '<p style="color: red;">Please submit both a title and an entry.</p>'; 46 $problem

\=

TRUE;

47 }

48

49

if (!$problem) {

50

51

// Define the query.

**52**

**$query = "UPDATE entries SET title='$title', entry='$entry' WHERE entry\_id=**

**{$\_POST\['id'\]}";**

**53**

**$r = mysql\_query($query, $dbc); // Execute the query.**

54

55

// Report on the result:

**56**

**if (mysql\_affected\_rows($dbc) == 1) {**

**57**

**print '<p>The blog entry has been updated.</p>';**

**58 }**

**else**

**{**

**59**

**print '<p style="color: red;">Could not update the entry because:<br />' .**

**mysql\_error($dbc) . '.</p><p>The query being run was: ' . $query . '</p>';** **60 }**

61

62

} // No problem!

63

64 } else { // No ID set.

65

print '<p style="color: red;">This page has been accessed in error.</p>'; 66 } // End of main IF.

67

68 mysql\_close($dbc); // Close the connection.

69

70 ?>

71 </body>

72 </html>

374 Chapter

12

**2.** Start your PHP code and connect to

Again, this is almost exactly the same

the database:

as in the preceding script, including

**<?php // Script 12.9 -**

the most important step of storing the

➝ **edit\_entry.php**

ID value in a hidden form input. Here,

**$dbc = mysql\_connect('localhost',**

though, the stored data isn’t just printed

➝ **'username', 'password');**

but is actually used as the values for

**mysql\_select\_db('myblog', $dbc);**

form elements. For security and to

avoid potential conflicts, each value is

**3.** If the page received a valid entry

run through **htmlentities()** first.

ID in the URL, define and execute

**5.** Report an error if the query failed:

a **SELECT** query:

**if (isset($\_GET\['id'\]) &&**

**} else { // Couldn't get the**

➝ **is\_numeric($\_GET\['id'\]) ) {**

➝ **information.**

**$query = "SELECT title,**

**print '<p style="color:**

 ➝ **entry FROM entries WHERE**

 ➝ **red;">Could not retrieve**

 ➝ **entry\_id={$\_GET\['id'\]}";**

 ➝ **the blog entry because:**

**if ($r = mysql\_query($query,**

 ➝ **<br />' . mysql\_error($dbc) .**

 ➝ **$dbc)) {**

 ➝ **'.</p><p>The query being run**

 ➝ **was: ' . $query . '</p>';**

This code is exactly the same as that

**}**

in the delete page; it selects the two

**6.** Check for the submission of the form:

column values from the database for

the provided ID value.

**} elseif (isset($\_POST\['id'\]) &&**

**4.** Retrieve the record, and display the

➝ **is\_numeric($\_POST\['id'\])) {**

entry in a form:

This conditional will be **TRUE** when the

**$row = mysql\_fetch\_array($r);**

form is submitted.

**print '<form action="edit\_entry.**

**7.** Validate and secure the form data:

 ➝ **php" method="post">**

**$problem = FALSE;**

**<p>Entry Title: <input type=**

**if (!empty($\_POST\['title'\]) &&**

➝ **"text" name="title" size="40"**

➝ **!empty($\_POST\['entry'\])) {**

➝ **maxsize="100" value="' .**

**$title = mysql\_real\_escape\_**

➝ **htmlentities($row\['title'\]) .**

 ➝ **string(trim(strip\_tags($\_POST**

➝ **'" /></p>**

 ➝ **\['title'\])), $dbc);**

**<p>Entry Text: <textarea name=**

**$entry = mysql\_real\_escape\_**

➝ **"entry" cols="40" rows="5">' .**

 ➝ **string(trim(strip\_tags($\_POST**

➝ **htmlentities($row\['entry'\]) .**

 ➝ **\['entry'\])), $dbc);**

➝ **'</textarea></p>**

**} else {**

**<input type="hidden" name="id"**

**print '<p style="color: red;">**

➝ **value="' . $\_GET\['id'\] . '" />**

 ➝ **Please submit both a title**

**<input type="submit" name="submit"**

 ➝ **and an entry.</p>';**

➝ **value="Update this Entry!" />**

**$problem = TRUE;**

**</form>';**

**}**

continues on next page

Intro to Databases 375

This code comes from the page used to

If one row was affected, then a success

add blog postings. It performs minimal

message is returned. Otherwise, the

validation on the submitted data and

MySQL error and the query are sent to

then runs it through the **mysql\_real\_**

the Web browser.

**escape\_string()** function to be safe.

**10.** Complete the conditionals:

Because the form data can be edited,

**} // No problem!**

the form should be validated as if it

**} else { // No ID set.**

were a new record being created.

**print '<p style="color: red;">**

**8.** Define and execute the query:

 ➝ **This page has been accessed**

**if (!$problem) {**

 ➝ **in error.</p>';**

**$query = "UPDATE entries SET**

**} // End of main IF.**

 ➝ **title='$title', entry='$entry'**

If no numeric ID value was passed to

 ➝ **WHERE entry\_id={$\_POST\['id'\]}";**

this page using either the GET method

**$r = mysql\_query($query, $dbc);**

or the POST method, then this **else**

The **UPDATE** query sets the **title**

clause takes effect.

column equal to the value entered in

**11.** Close the database connection, and

the form’s title input and the **entry**

complete the page:

column equal to the value entered in

**mysql\_close($dbc);**

the form’s entry text area. Only the

**?>**

record whose **entry\_id** is equal to

**$\_POST\['id'\]**

**</body>**

, which comes from a

**</html>**

hidden form input, is updated.

**12.** Save the file as **edit\_entry.php**, place

**9.** Report on the success of the query:

it in the proper directory for your PHP-

**if (mysql\_affected\_rows($dbc) == 1) {**

enabled server, and test it in your Web

**print '<p>The blog entry has**

browser **A** and **B**.

 ➝ **been updated.</p>';**

**} else {**

As in the preceding example, to edit an

**print '<p style="color: red;">**

entry, you must click its Edit link in the

 ➝ **Could not update the entry**

**view\_blog.php** page.

 ➝ **because:<br />' . mysql\_**

 ➝ **error($dbc) . '.</p><p>The**

 ➝ **query being run was: ' .**

 ➝ **$query . '</p>';**

**}**

376 Chapter

12

![Image 465](index-398_1.png)

**13.** Revisit **view\_blog.php** to confirm that

the changes were made **C**.

**The id is a primary key, meaning that its**

**value should never change. By using a primary**

**key in your table, you can change every other**

**value in the record but still refer to the row**

**using that column.**

**The mysql\_real\_escape\_string()**

**function does not need to be applied to the**

**ID values used in the queries, as the is\_**

**numeric() test confirms they don’t contain**

**apostrophes or other problematic characters.**

**More thorough edit and delete pages**

**would use the mysql\_num\_rows() function in**

**a conditional to confirm that the SELECT query**

**returned a row prior to fetching it:**

**if (mysql\_num\_rows($r) == 1) {…**

**If you run an update on a table but don’t**

**change a record’s values, mysql\_affected\_**

**rows() will return 0.**

**It can’t hurt to add a LIMIT 1 clause to**

**an UPDATE query, to ensure that only one row,**

**at most, is affected.**

**C** Reloading the **view\_blog.php** script reflects the changes made to the entries.

Intro to Databases 377

[**Review and Pursue**](#index_split_000.html#p9)

**Pursue**

■

Find the version of the MySQL manual

If you have any problems with the review

that corresponds to your version of

questions or the pursue prompts, turn

MySQL. Start reading!

to the book’[s supporting forum (www.](http://www.LarryUllman.com/forum/)

■

Move the code for connecting to and

[LarryUllman.com/ forum/ ).](http://www.LarryUllman.com/forum/)

selecting the database to a separate

**Review**

script, then include that script in the PHP

pages that interact with the database.

■

What version of MySQL are you using?

■

Make the **add\_entry.php** form sticky.

What values do you personally use to

connect to MySQL?

■

Change the code in **view\_entry.php**

so that it converts newline characters in

■

How does a PHP script connect

each entry into HTML break tags.

to a MySQL server? How does it

disconnect?

■

What is the error suppression operator?

What does it do?

■

What function returns MySQL-reported

errors?

■

What debugging techniques should you

use when having problems with a PHP

script that interacts with MySQL?

■

How do you select which database

to use?

■

What SQL command is used to create a

table? To add new records? To retrieve

records? To modify records? To remove

records?

■

What function should string values be

run through to prevent SQL injection

attacks?

378 Chapter

12

[**13**](#index_split_000.html#p9)

[Putting It All](#index_split_000.html#p9)

[Together](#index_split_000.html#p9)

The 12 chapters to this point have covered

all the fundamentals of using PHP for Web

**In This Chapter**

development. In this chapter, you’ll use

your accumulated knowledge to create

Getting Started

380

a complete and functional Web site. And

Connecting to the Database

382

even though the focus of this chapter is on

Writing the User-Defined Function

383

applying your newfound knowledge, you’ll

still learn a few new tricks. In particular,

Creating the Template

385

you’ll see how to develop a full-scale Web

Logging In

388

application from scratch.

Logging Out

392

Adding Quotes

393

Listing Quotes

397

Editing Quotes

400

Deleting Quotes

406

Creating the Home Page

410

Review and Pursue

414

![Image 466](index-401_1.png)

![Image 467](index-401_2.png)

[**Getting Started**](#index_split_000.html#p9)

The first step when starting any project is

identifying the site’s goals. The primary

goal of this chapter is to apply everything

taught in the book thus far (a lofty aim, to

be sure). The example I came up with for

doing so combines the models from the

previous two chapters, creating a site that

will store and display quotations. Instead of

using a file to do so, as in Chapter 11, “Files

and Directories,” this site will use a MySQL

database as the storage repository. But as

**A** The site’s simple home page.

with the blog example from Chapter 12,

“Intro to Databases,” the ability to create,

edit, and delete quotations will be

implemented. Further, the public user will

be able to view the most recent quotation

by default **A**, or a random one, or a random

quotation previously marked as a favorite.

For improved security, the site will have an

administrator who can log in and log out.

And only the logged-in administrator will be

allowed to create, edit, or delete quotations **B**.

**B** Nonadministrators are denied access to

certain pages.

The site will use a simple template to give

every page a consistent look, with CSS

handling all the formatting and layout. The

site will also make use of one user-defined

function, stored in an included file.

As in Chapter 12, you must first create the

database and its one table. The database

could be named myquotes (or something

else if you’d rather). You create its one

table with this SQL command:

**CREATE TABLE quotes (**

**quote\_id INT UNSIGNED NOT NULL**

 ➝ **AUTO\_INCREMENT,**

**quote TEXT NOT NULL,**

**source VARCHAR(100) NOT NULL,**

**favorite TINYINT(1) UNSIGNED NOT**

 ➝ **NULL,**

**date\_entered TIMESTAMP NOT NULL**

 ➝ **DEFAULT CURRENT\_TIMESTAMP,**

**PRIMARY KEY (quote\_id)**

**)**

380 Chapter

13

![Image 468](index-402_1.jpg)

![Image 469](index-402_2.png)

![Image 470](index-402_3.png)

![Image 471](index-402_4.png)

![Image 472](index-402_5.png)

![Image 473](index-402_6.png)

![Image 474](index-402_7.png)

![Image 475](index-402_8.png)

![Image 476](index-402_9.png)

![Image 477](index-402_10.png)

![Image 478](index-402_11.png)

![Image 479](index-402_12.png)

![Image 480](index-402_13.png)

![Image 481](index-402_14.png)

![Image 482](index-402_15.png)

![Image 483](index-402_16.png)

The **quote\_id** is the primary key, and it will

application (like the MySQL client

automatically be incremented to the next

or phpMyAdmin).

logical value with each new submission.

Finally, a word about how the site should

The **quote** field stores the quote itself,

be organized on the server **C**. Ideally

with the **source** field storing the attribution

the **mysql\_connect.php** script, which

(unlike in Chapter 11, where the quote and

establishes a database connection, would

the source were stored together). The

be stored outside the Web root directory.

**favorite** field stores a 1 or a 0, marking

If that is not possible in your case, you can

the quote as a favorite or not. Finally, the

place it in the **includes** folder, then change

**date\_entered** column is a timestamp,

the code in the other scripts accordingly.

automatically set to the current timestamp

Once you’ve created the database, the

when a new record is created.

database table, and the necessary folders,

You can create this table using a PHP

you can begin coding.

script, such as Script 12.4, or a third-party

**C** The structure and

organization of the files

on the server.

Putting It All Together 381

[**Connecting to**](#index_split_000.html#p9)

**Script 13.1** This script connects to the database

server and selects the database to be used.

[**the Database**](#index_split_000.html#p9)

1

<?php // Script 13.1 - mysql\_connect.php

2

/\* This script connects to and selects

Unlike the scripts in Chapter 12, which

the database. \*/

connected to the database using code

3

repeated in each script, this site will use

4 //

Connect:

5

$dbc = mysql\_connect('localhost',

the more common practice of placing the

'username', 'password');

repeated code in a stand-alone file. Every

6

script that interacts with the database—

7 //

Select:

which will be most but not all of them—will

8 mysql\_select\_db('myquotes',

$dbc);

then include this file. As you can see in

9

10 ?>

Figure **C** in the previous section, this file

should be stored outside of the Web root

directory or, if that’s not possible, within the

**includes** folder.

**To create mysql\_connect.php:**

**1.** Begin a new PHP script in your

text editor or IDE, to be named

**mysql\_connect.php** (**Script 13.1**):

**<?php**

**2.** Connect to the database server:

**$dbc = mysql\_connect('localhost',**

**'username', 'password');**

Naturally, you’ll need to change the

values used here to be appropriate for

your server.

**3.** Select the database:

**mysql\_select\_db('myquotes', $dbc);**

If you named your database something

else, change this value accordingly.

**4.** Complete the script:

**?>**

**5.** Save the file as **mysql\_connect.php**.

382 Chapter

13

![Image 484](index-404_1.png)

[**Writing the User-**](#index_split_000.html#p9)

[**Defined Function**](#index_split_000.html#p9)

The site will have a single user-defined

function. As discussed in Chapter 10,

“Creating Functions,” the best time to

create your own functions is when a script

or a site might have repeating code. In this

site there are a couple such instances, but

**A** This cookie will be used to identify the

the most obvious one is this: Many scripts

administrator.

will need to check whether or not the

current user is an administrator. In this next

script, you’ll create your own function that

returns a Boolean value indicating if the

user is an administrator. But what will be

the test of administrative status?

Upon successfully logging in, a cookie

will be sent to the administrator’s browser,

with a name of Samuel and a value of

Clemens **A**. This may seem odd or

random, and it is. When using something

simple, like a cookie, for authentication, it’s

best to be obscure about what constitutes

verification. If you went with something

more obvious, such as a name of admin

and a value of true, that’d be quite easy

for anyone to guess and falsify. With this

cookie in mind, this next function simply

checks if a cookie exists with a name of

Samuel and a value of Clemens.

Putting It All Together 383

**To create functions.php:**

site’s functionality expand (e.g., if you

had multiple types of authentication to

**1.** Begin a new PHP script in your

perform). Still, by using default values

text editor or IDE, to be named

for those arguments, function calls don’t

**functions.php** (**Script 13.2**):

need to provide argument values when

**<?php // Script 13.2 - functions.php**

the assumed cookie name and value

Even though, as written, the script only

are being checked.

defines a single function, I’m naming

**3.** Return a Boolean value based on the

the file using the plural—functions—

cookie’s existence and value:

with the understanding that more user-

**if (isset($\_COOKIE\[$name\]) &&**

defined functions might be added to

➝ **($\_COOKIE\[$name\] == $value)) {**

the script in time.

**return**

**true;**

**2.** Begin defining a new function:

**} else {**

**function is\_administrator($name =**

**return**

**false;**

➝ **'Samuel', $value = 'Clemens') {**

**}**

The function takes two arguments: the

If the cookie exists and has the appropri-

cookie’s name and its value. Both have

ate value, the Boolean true is returned.

default values.

Otherwise the function returns false.

Since the function checks only a single

**4.** Complete the function and the script:

cookie with a single expected value, it

**} // End of is\_administrator()**

doesn’t need to take arguments at all,

➝ **function.**

let alone default ones. But by having

**?>**

the function take arguments, it can

**5.** Save the file as **functions.php**, stored

be used in different ways should the

in the **includes** directory.

**Script 13.2** The **is\_administrator()** function, defined in an includable script, will be called on any page that needs to verify administrator status.

1

<?php // Script 13.2 - functions.php

2

/\* This page defines custom functions. \*/

3

4

// This function checks if the user is an administrator.

5

// This function takes two optional values.

6

// This function returns a Boolean value.

7

function is\_administrator($name = 'Samuel', $value = 'Clemens') {

8

9

// Check for the cookie and check its value:

10

if (isset($\_COOKIE\[$name\]) && ($\_COOKIE\[$name\] == $value)) {

11 return

true;

12

} else {

13 return

false;

14 }

15

16 } // End of is\_administrator() function.

17

18 ?>

384 Chapter

13

![Image 485](index-406_1.png)

[**Creating the Template**](#index_split_000.html#p9)

Now that the two helper files have been

created, it’s time to move on to the

template. As illustrated in Chapter 8,

“Creating Web Applications,” the site’s

layout will be controlled by two includable

**A** If the person viewing any page

files: a header and a footer. Both will be

is an administrator, they’ll see some

additional links.

stored in the **templates** directory. The

header also references a style sheet, to

**Script 13.3** The header file includes the

be stored in the **css** folder. You can find

**functions.php** script and begins the HTML page.

the style sheet by downloading the book’s

1

<?php // Script 13.3 - header.html

[code from www.LarryUllman.com (the file](http://www.LarryUllman.com)

2

will be in the **ch13** folder of the download).

3

// Include the functions script:

Besides generating the primary HTML for

4 include('includes/functions.php');

?>

5

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML

the site, the header file must include the

1.0 Transitional//EN"

functions script. The footer file should also

6

"http://www.w3.org/TR/xhtml1/DTD/

display some administration links **A**, should

xhtml1-transitional.dtd">

the current user be an administrator.

7

<html xmlns="http://www.w3.org/1999/

xhtml" xml:lang="en" lang="en">

8 <head>

**To create header.html:**

9

<meta http-equiv="content-type"

**1.** Begin a new HTML document in

content="text/html; charset=utf-8" />

10

<link rel="stylesheet" media="all"

your text editor or IDE, to be named

href="css/style.css" />

**header.html** (**Script 13.3**).

11

<title><?php // Print the page title.

**<?php // Script 13.3 - header.html**

12

if (defined('TITLE')) { // Is the title

defined?

**include('includes/functions.php'); ?>**

13 print

TITLE;

The header will start with a PHP section

14

} else { // The title is not defined.

in order to include the **functions.php**

15

print 'My Site of Quotes';

16 }

script, which will be required by multiple

17 ?></title>

pages on the site. The reference to the

18 </head>

script is relative to the pages that will

19 <body>

be including the header: files in the

20 <div

id="container">

main directory.

21

<h1>My Site of Quotes</h1>

22 <br

/>

continues on next page

23

<!-- BEGIN CHANGEABLE CONTENT. -->

Putting It All Together 385

**2.** Begin the HTML document:

**To create footer.html:**

**<!DOCTYPE html PUBLIC "-//W3C//DTD**

**1.** Begin a new HTML document in

➝ **XHTML 1.0 Transitional//EN"**

your text editor or IDE, to be named

**"http://www.w3.org/TR/xhtml1/**

**footer.html** (**Script 13.4**):

 ➝ **DTD/xhtml1-transitional.dtd">**

**<!-- END CHANGEABLE CONTENT. -->**

**<html xmlns="http://www.w3.org/**

➝ **1999/xhtml" xml:lang="en"**

**2.** Check if it’s appropriate to display gen-

➝ **lang="en">**

eral administration links:

**<head>**

**<?php**

**<meta**

**http-equiv="content-type"**

**if ( (is\_administrator() &&**

 ➝ **content="text/html;**

➝ **(basename($\_SERVER\['PHP\_SELF'\])**

 ➝ **charset=utf-8" />**

➝ **!= 'logout.php'))**

**<link rel="stylesheet" media=**

**OR (isset($loggedin) &&**

 ➝ **"all" href="css/style.css" />**

➝ **$loggedin) ) {**

Again, the style sheet needs to

This conditional is a bit complicated.

be downloaded from the book’s

To start, most pages can confirm that

corresponding Web site. And the

the current user is an administrator by

reference to that style sheet is relative

just invoking the **is\_administrator()**

to the scripts that include the header,

function. But because of how

all found within the main directory.

cookies work, that function will return

**3.** Print the page’s title:

inappropriate results on two pages:

**login.php** and **logout.php**. On the

**<title><?php**

**logout.php**, the script will have received

**if (defined('TITLE')) {**

the administrative cookie prior to deleting

**print**

**TITLE;**

it. So on that page, it will seem like the

**} else {**

user is an administrator (because they

**print 'My Site of Quotes';**

just were), but links to the administrative

**}**

pages should not be shown as the user

**?></title>**

will be blocked from using them (because

This code also comes from Chapter 8,

when they get to those pages, the

printing either the default title or a

cookie will no longer exist). Hence, the

custom one, if set as a constant.

first part of the conditional requires that

**4.** Complete the head:

**is\_administrator()** return true and that

**</head>**

the current page not be **logout.php**. The

code **basename($\_SERVER\['PHP\_SELF'\])**

**5.** Begin the page’s body:

is a reliable way to get the current script

**<body>**

(and because the footer file is included by

**<div**

**id="container">**

another script, **$\_SERVER\['PHP\_SELF'\]** will

**<h1>My Site of Quotes</h1>**

have the value of the including script.

**<br**

**/>**

The second part of the conditional, after

**<!-- BEGIN CHANGEABLE**

the **OR**, checks if the **$loggedin** variable

 ➝ **CONTENT. -->**

is set and has a true value. This will be

**6.** Save the file as **header.html**, stored in

the case on the **login.php** page, after

the **templates** directory.

the user successfully logged in. The

386 Chapter

13

**is\_administrator()** function won’t

**4.** Complete the conditional and the

return a true value at that juncture,

PHP section:

because the cookie will have been just

**}**

sent by the script, and therefore won’t

**?>**

be available to be read.

**5.** Complete the HTML page:

**3.** Create the links:

**</div><!-- container -->**

**print '<hr /><h3>Site Admin</h3>**

**<div id="footer">Content &copy;**

➝ **<p><a href="add\_quote.php">Add**

 ➝ **2011</div>**

➝ **Quote</a> <->**

**</body>**

**<a href="view\_quotes.php">View All**

**</html>**

➝ **Quotes</a> <->**

**6.** Save the file as **footer.html**, stored in

**<a href="logout.php">Logout</a></p>';** the **templates** directory.

Three links are created: to a page for

adding new quotes, to a page for viewing

every quote, and to the logout page.

**Script 13.4** The footer file displays general administrative links, when appropriate, and completes the HTML page.

1

<!-- END CHANGEABLE CONTENT. -->

2

<?php // Script 13.4 - footer.html

3

4

// Display general admin links...

5

// - if the user is an administrator and it's not the logout.php page 6

// - or if the $loggedin variable is true (i.e., the user just logged in) 7

if ( (is\_administrator() && (basename($\_SERVER\['PHP\_SELF'\]) != 'logout.php')) 8

OR (isset($loggedin) && $loggedin) ) {

9

10

// Create the links:

11

print '<hr /><h3>Site Admin</h3><p><a href="add\_quote.php">Add Quote</a> <-> 12

<a href="view\_quotes.php">View All Quotes</a> <-> 13 <a

href="logout.php">Logout</a></p>';

14

15 }

16

17 ?>

18 </div><!-- container -->

19

<div id="footer">Content &copy; 2011</div> 20 </body>

21 </html>

Putting It All Together 387

[**Logging In**](#index_split_000.html#p9)

**Script 13.5** The login script both displays and

handles a form, sending a cookie upon a successful

login attempt.

Next, it’s time to create the script through

which the administrator can log in. The end

1

<?php // Script 13.5 - login.php

result will be very similar to the scripts in

2

/\* This page lets people log into the

site. \*/

Chapter 9, “Cookies and Sessions,” with

3

one structural difference: that chapter

4

// Set two variables with default values:

used output buffering, allowing you to lay

5

$loggedin = false;

out your script however you want. This

6

$error = false;

site does not use output buffering, so the

7

8

// Check if the form has been submitted:

handling of the form must be written in

9

if ($\_SERVER\['REQUEST\_METHOD'\] == 'POST')

such a way that the cookie can be sent

{

without generating headers already sent

10

errors (see Chapter 9 if this isn’t ringing

11

// Handle the form:

a bell for you). In other words, the script

12

if (!empty($\_POST\['email'\]) &&

!empty($\_POST\['password'\])) {

must check for a form submission prior

13

to including the header. To still be able

14

if ( (strtolower($\_POST\['email'\])

to reflect errors and other messages

\== 'me@example.com') && ($\_

within the context of the page, you must

POST\['password'\] == 'testpass') ) {

therefore use variables.

// Correct!

15

16

// Create the cookie:

**To create login.php:**

17

setcookie('Samuel', 'Clemens',

time()+3600);

**1.** Begin a new PHP document in your text

18

editor or IDE, to be named **login.php**

19

// Indicate they are logged in:

(**Script 13.5**):

20 $loggedin

\=

true;

21

**<?php // Script 13.5 - login.php**

22

} else { // Incorrect!

**2.** Define two variables with default values:

23

24

$error = 'The submitted email

**$loggedin = false;**

address and password do not

**$error = false;**

match those on file!';

25

These two variables will be used later in

26 }

the script. Here they are given default

27

values, indicating that the person is

28

} else { // Forgot a field.

not logged in and no errors have yet

29

occurred.

30

$error = 'Please make sure you

enter both an email address and a

**3.** Check if the form has been submitted:

password!';

31

**if ($\_SERVER\['REQUEST\_METHOD'\] ==**

32 }

➝ **'POST') {**

33

34 }

35

code continues on next page

388 Chapter

13

**Script 13.5** continued

**4.** Handle the form:

36

// Set the page title and include the

**if (!empty($\_POST\['email'\]) &&**

header file:

➝ **!empty($\_POST\['password'\])) {**

37 define('TITLE',

'Login');

**if ( (strtolower($\_POST\['email'\])**

38 include('templates/header.html');

➝ **\== 'me@example.com') && ($\_POST**

39

➝ **\['password'\] == 'testpass') ) {**

40 // Print an error if one exists:

41 if ($error) {

Similar to examples in Chapter 9,

42

print '<p class="error">' . $error .

this script first confirms that both **$\_**

'</p>';

**POST\['email'\]** and **$\_POST\['password'\]**

43 }

44

are not empty. The second conditional

45

// Indicate the user is logged in, or

compares the submitted values against

show the form:

what they need to be.

46 if ($loggedin) {

47

**5.** Create the cookie:

48

print '<p>You are now logged in!</p>';

**setcookie('Samuel', 'Clemens',**

49

➝ **time()+3600);**

50 } else {

51

The cookie has a name of Samuel and

52

print '<h2>Login Form</h2>

a value of Clemens. It’s set to expire in

53

<form action="login.php"

an hour.

method="post">

54

<p><label>Email Address <input type=

**6.** Indicate that the user is logged in:

"text" name="email" /></label></p> 55

<p><label>Password <input

**$loggedin = true;**

type="password" name="password" />

This variable will be used later in this

</label></p>

same script, and in the footer file (see

56

<p><input type="submit" name="submit"

value="Log In!" /></p>

Script 13.4).

57 </form>';

**7.** Create error messages for the two

58

other conditions:

59 }

60

**} else { // Incorrect!**

61 include('templates/footer.html');

**$error = 'The submitted**

// Need the footer.

 ➝ **email address and**

62 ?>

 ➝ **password do not match**

 ➝ **those on file!';**

**}**

**} else { // Forgot a field.**

**$error = 'Please make sure**

 ➝ **you enter both an email**

 ➝ **address and a password!';**

**}**

**}**

continues on next page

Putting It All Together 389

![Image 486](index-411_1.png)

The first **else** clause applies if an email

address and password were provided

but were wrong. The second **else**

clause applies if no email address or

password was submitted. In both cases,

the message is assigned to a variable

so that it may be used later in the script.

**8.** Set the page title and include the

header file:

**A** Error messages are displayed after the header

**define('TITLE', 'Login');**

is included but before the HTML form.

**include('templates/header.html');**

**9.** Print an error if one exists:

**if ($error) {**

**print '<p class="error">' .**

 ➝ **$error . '</p>';**

**}**

The error itself will be determined in

Step 7, but it can’t be printed at that

point because the HTML header will

not have been included. The solution is

to have this code check for a non-false

**$error** value and then print **$error**

within some HTML and CSS **A**.

390 Chapter

13

![Image 487](index-412_1.png)

![Image 488](index-412_2.png)

**10.** Indicate that the user is logged in, or

display the form:

**if ($loggedin) {**

**print '<p>You are now logged**

 ➝ **in!</p>';**

**} else {**

**print '<h2>Login Form</h2>**

**<form action="login.php"**

 ➝ **method="post">**

**<p><label>Email Address <input**

 ➝ **type="text" name="email" />** **B** The result upon successfully

 ➝ **</label></p>**

logging in.

**<p><label>Password <input**

 ➝ **type="password" name=**

 ➝ **"password" /></label></p>**

**<p><input type="submit" name=**

 ➝ **"submit" value="Log In!" /></p>**

**</form>';**

**}**

If the **$loggedin** variable has a true

value—its value is false by default—then

the user just successfully logged into

the site and a message saying so is

displayed **B**. If the **$loggedin** variable

still has its default value, then the form

**C** The basic login form.

should be shown **C**.

**11.** Include the footer and complete the page:

**include('templates/footer.html');**

**?>**

**12.** Save the file as **login.php**.

**13.** Test the file in your Web browser

(Figures **A**, **B**, and **C**).

I purposefully omitted creating a link

to the login section (as a security

measure), so you’ll need to enter the

correct URL in your Web browser’s

address bar.

**Note that, as written, the script requires**

**administrators to log back in after an hour,**

**whether or not they continue to be active in**

**the site.**

Putting It All Together 391

![Image 489](index-413_1.png)

![Image 490](index-413_2.png)

[**Logging Out**](#index_split_000.html#p9)

**Script 13.6** The logout script deletes the

administrator-identifying cookie.

If you write a login process, there must

1

<?php // Script 13.6 - logout.php

be a logout process, too. In this case, just

2

/\* This is the logout page. It destroys

using cookies, it’s a very simple script.

the cookie. \*/

3

**To create logout.php:**

4

// Destroy the cookie, but only if it

already exists:

**1.** Begin a new PHP document in your text

**5**

**if (isset($\_COOKIE\['Samuel'\])) {**

editor or IDE, to be named **logout.php**

**6**

**setcookie('Samuel', FALSE,**

**time()-300);**

(**Script 13.6**):

**7 }**

**<?php // Script 13.6 - logout.php**

8

9

// Define a page title and include the

**2.** Destroy the cookie, but only if it

header:

already exists:

10 define('TITLE',

'Logout');

11 include('templates/header.html');

**if (isset($\_COOKIE\['Samuel'\])) {**

12

**setcookie('Samuel', FALSE,**

13 // Print a message:

 ➝ **time()-300);**

14 print '<p>You are now logged out.</p>';

**}**

15

16 // Include the footer:

As an extra security measure, the script

17 include('templates/footer.html');

only attempts to delete the cookie if it

18 ?>

exists. By making this check, the script

prevents hackers from discovering the

name of the cookie used by the site

by accessing the logout script without

having first logged in.

To delete the existing login cookie,

another cookie is sent with the same

name, a value of FALSE, and an

expiration time in the past.

**3.** Define a page title and include the header:

**A** This cookie deletes the existing cookie.

**define('TITLE', 'Logout');**

**include('templates/header.html');**

**4.** Print a message:

**print '<p>You are now logged**

➝ **out.</p>';**

**5.** Include the footer:

**include('templates/footer.html');**

**?>**

**B** The resulting logout page.

**6.** Save the file as **logout.php**.

**7.** Test the file in your Web browser **A**

and **B**.

392 Chapter

13

![Image 491](index-414_1.png)

[**Adding Quotes**](#index_split_000.html#p9)

Now that the administrator has the ability

to log in, she or he should be able to start

adding quotations. The script for doing

so is a lot like the one for adding blog

postings (from Chapter 12), but the form will

have an additional checkbox for marking

the quotation as a favorite **A**.

Because this script creates records in

the database, security must be a primary

concern. As an initial precaution, the script

will make sure that only the administrator

can use the page. Second, values to

be used in the SQL command will be

**A** The form for adding quotations to

sanctified to prevent invalid queries.

the database.

**Script**

**To create add\_quote.php:**

**13.7** The **add\_quote.php** script allows

only administrators to add new quotations to

**1.** Begin a new PHP document in your text

the database.

editor or IDE, to be named **add\_quote.**

1

<?php // Script 13.7 - add\_quote.php

**php** (**Script 13.7**):

2

/\* This script adds a quote. \*/

3

**<?php // Script 13.7 -**

4

// Define a page title and include the

➝ **add\_quote.php**

header:

**define('TITLE', 'Add a Quote');**

5

define('TITLE', 'Add a Quote');

**include('templates/header.html');**

6 include('templates/header.html');

**print '<h2>Add a Quotation</h2>';**

7

8

print '<h2>Add a Quotation</h2>';

**2.** Deny access to the page if the user is

9

not an administrator:

10 // Restrict access to administrators only:

11 if (!is\_administrator()) {

**if (!is\_administrator()) {**

12

print '<h2>Access Denied!</h2><p

**print '<h2>Access Denied!</h2>**

class="error">You do not have

 ➝ **<p class="error">You do not**

permission to access this page.</p>';

 ➝ **have permission to access**

13 include('templates/footer.html');

14 exit();

 ➝ **this page.</p>';**

15 }

**include('templates/footer.html');**

16

**exit();**

17 // Check for a form submission:

**}**

18

if ($\_SERVER\['REQUEST\_METHOD'\] == 'POST')

{ // Handle the form.

continues on next page

19

20

if ( !empty($\_POST\['quote'\]) &&

!empty($\_POST\['source'\]) ) {

21

code continues on next page

Putting It All Together 393

![Image 492](index-415_1.png)

By invoking the **is\_administrator()**

function, the script can quickly test

for that condition. If the user is not an

administrator, an Access Denied error

is displayed, the footer is included, and

the script is terminated **B**.

**3.** Check for a form submission:

**if ($\_SERVER\['REQUEST\_METHOD'\] ==**

➝ **'POST') {**

**B** Any user not logged in as an

**4.** Check for values:

administrator is denied access to

**if ( !empty($\_POST\['quote'\]) &&**

the form.

➝ **!empty($\_POST\['source'\]) ) {**

**Script 13.7** continued

This script performs a minimum of

validation, checking that the two

22

// Need the database connection:

23 include('../mysql\_connect.php');

variables aren’t empty. With large

24

blocks of text, such as a quotation,

25

// Prepare the values for storing:

there’s not much more that can be done

26

$quote = mysql\_real\_escape\_

in terms of validation.

string(trim(strip\_tags($\_

POST\['quote'\])), $dbc);

**5.** Prepare the values for use in the query:

27

$source = mysql\_real\_escape\_

**$quote = mysql\_real\_escape\_**

string(trim(strip\_tags($\_

➝ **string(trim(strip\_tags($\_POST**

POST\['source'\])), $dbc);

28

➝ **\['quote'\])), $dbc);**

29

// Create the "favorite" value:

**$source = mysql\_real\_escape\_**

30 if

(isset($\_POST\['favorite'\]))

{

➝ **string(trim(strip\_tags($\_POST**

31 $favorite

\=

1;

➝ **\['source'\])), $dbc);**

32 }

else

{

33

$favorite = 0;

To make the two textual values safe to

34 }

use in the query, they’re run through the

35

**mysql\_real\_escape\_string()** function

36

$query = "INSERT INTO quotes

(quote, source, favorite) VALUES

(see Chapter 12). To make the values

('$quote', '$source', $favorite)";

safe to later display in the Web page,

37

$r = mysql\_query($query, $dbc);

the **strip\_tags()** function is applied,

38

too (see Chapter 5, “Using Strings”).

39

if (mysql\_affected\_rows($dbc) ==

1) {

**6.** Create the favorite value:

40 //

Print

a

message:

**if (isset($\_POST\['favorite'\])) {**

41

print '<p>Your quotation has

**$favorite = 1;**

been stored.</p>';

42 }

else

{

**} else {**

43

print '<p class="error">Could

**$favorite = 0;**

not store the quote because:<br

**}**

/>' . mysql\_error($dbc) . '.</

p><p>The query being run was: '

. $query . '</p>';

code continues on next page

394 Chapter

13

**Script 13.7** continued

In the database, a quotation’s status

as a favorite is indicated by a 1.

44 }

Nonfavorites are represented by a 0.

45

46

// Close the connection:

To determine which number to use, all

47 mysql\_close($dbc);

the PHP script has to do is check for

48

a **$\_POST \['favorite'\]** value. If that

49

} else { // Failed to enter a quotation.

variable is set, regardless of what its

50

print '<p class="error">Please

value is, it means the user checked the

enter a quotation and a source!</p>';

51 }

favorite checkbox. If the user didn’t do

52

that, then the variable won’t be set, and

53 } // End of submitted IF.

the **$favorite** variable will be assigned

54

the value 0.

55 // Leave PHP and display the form:

56 ?>

**7.** Define and execute the query:

57

**$query = "INSERT INTO quotes**

58

<form action="add\_quote.php"

method="post">

➝ **(quote, source, favorite) VALUES**

59

<p><label>Quote <textarea

➝ **('$quote', '$source', $favorite)";**

name="quote" rows="5" cols="30"> **$r = mysql\_query($query, $dbc);**

</textarea></label></p>

60

<p><label>Source <input type="text"

The query specifies values for three

name="source" /></label></p>

fields and uses the variables already

61

<p><label>Is this a favorite? <input

defined. The remaining two table

type="checkbox" name="favorite"

columns—**quote\_id** and **date\_**

value="yes" /></label></p>

**entered**—will automatically be assigned

62

<p><input type="submit" name="submit"

value="Add This Quote!" /></p>

values, thanks to the table’s definition.

63 </form>

**8.** Print a message based on the results:

64

65 <?php

include('templates/header.html');

**if (mysql\_affected\_rows($dbc) ==**

?>

➝ **1) {**

**print '<p>Your quotation has**

 ➝ **been stored.</p>';**

**} else {**

**print '<p class="error">Could**

 ➝ **not store the quote because:**

 ➝ **<br />' . mysql\_error($dbc) .**

 ➝ **'.</p><p>The query being run**

 ➝ **was: ' . $query . '</p>';**

**}**

If the **INSERT** query created one new row

in the database, a message indicating

such is displayed. Otherwise, debugging

information is shown so that you can try

to figure out what went wrong.

continues on next page

Putting It All Together 395

![Image 493](index-417_1.png)

**9.** Complete the validation conditional:

**} else { // Failed to enter a**

➝ **quotation.**

**print '<p class="error">Please**

 ➝ **enter a quotation and a**

 ➝ **source!</p>';**

**}**

**10.** Complete the submission conditional

and the PHP block:

**} // End of submitted IF.**

**?>**

**C** The result after adding a quotation.

**11.** Create the form:

**<form action="add\_quote.php"**

➝ **method="post">**

**<p><label>Quote <textarea**

 ➝ **name="quote" rows="5"**

 ➝ **cols="30"></textarea>**

 ➝ **</label></p>**

**<p><label>Source <input**

 ➝ **type="text" name="source" />**

 ➝ **</label></p>**

**<p><label>Is this a favorite?**

 ➝ **<input type="checkbox"**

 ➝ **name="favorite" /></label></p>**

**<p><input**

**type="submit"**

 ➝ **name="submit" value="Add This**

 ➝ **Quote!" /></p>**

**</form>**

The form has one text area, one text

input, and a checkbox (plus the submit

button, of course). It is not designed to

be sticky: that’s a feature you could add

later, if you wanted.

**12.** Include the footer:

**<?php include('templates/**

➝ **footer.html'); ?>**

**13.** Save the file as **add\_quote.php** and test

in your Web browser **C**.

**The ability to create (i.e., INSERT),**

**retrieve (SELECT), update, and delete database**

**records is collectively referred to as CRUD.**

396 Chapter

13

![Image 494](index-418_1.png)

[**Listing Quotes**](#index_split_000.html#p9)

The administrative side of the site will have

a page that lists every quote stored in the

database **A**. Although the same script could

easily be adapted for the public side, its

primary purpose is to provide quick links for

the administrator to edit or delete any quote

(as opposed to searching randomly through

the public side for the right quote to manage).

Like the **add\_quote.php** script, this page

will restrict access to just administrators.

**To create view\_quotes.php:**

**1.** Begin a new PHP document in

your text editor or IDE, to be named

**view\_quotes.php** (**Script 13.8**):

**A** The full list of stored quotations, with

**<?php // Script 13.8-**

links to edit or delete each.

➝ **view\_quotes.php**

**Script**

**define('TITLE', 'View All Quotes');**

**13.8** This script lists every quotation

currently stored, providing links for the

**include('templates/header.html');**

administrator to edit or delete them.

**print '<h2>All Quotes</h2>';**

1

<?php // Script 13.8- view\_quotes.php

**2.** Terminate the script if the user isn’t an

2

/\* This script lists every quote. \*/

administrator:

3

4

// Include the header:

**if (!is\_administrator()) {**

5

define('TITLE', 'View All Quotes');

**print '<h2>Access Denied!</h2>**

6 include('templates/header.html');

 ➝ **<p class="error">You do not**

7

 ➝ **have permission to access**

8

print '<h2>All Quotes</h2>';

9

 ➝ **this page.</p>';**

10 // Restrict access to administrators only:

**include('templates/footer.html');**

11 if (!is\_administrator()) {

**exit();**

12

print '<h2>Access Denied!</h2><p

**}**

class="error">You do not have

permission to access this page.</p>';

continues on next page

13 include('templates/footer.html');

14 exit();

15 }

16

17 // Need the database connection:

18 include('../mysql\_connect.php');

19

code continues on next page

Putting It All Together 397

![Image 495](index-419_1.png)

This is the exact same code as that in

**add\_quote.php**. Except for the browser’s

title, the result for nonadministrators will

be the same as in **B** in the previous

section of the chapter.

**3.** Include the database connection and

define the query:

**B** The HTML source code for the page shows

**include('../mysql\_connect.php');**

how the **quote\_id** value is passed in the URL to

**$query = 'SELECT quote\_id, quote,**

the linked pages.

➝ **source, favorite FROM quotes**

➝ **ORDER BY date\_entered DESC';**

**Script 13.8** continued

20 // Define the query:

21 $query = 'SELECT quote\_id, quote, source, favorite FROM quotes ORDER BY date\_entered DESC'; 22

23 // Run the query:

24 if ($r = mysql\_query($query, $dbc)) {

25

26

// Retrieve the returned records:

27

while ($row = mysql\_fetch\_array($r)) {

28

29

// Print the record:

30 print

"<div><blockquote>{$row\['quote'\]}</blockquote>-

{$row\['source'\]}\\n";

31

32

// Is this a favorite?

33

if ($row\['favorite'\] == 1) {

34 print

'

<strong>Favorite!</strong>';

35 }

36

37

// Add administrative links:

38

print "<p><b>Quote Admin:</b> <a href=\\"edit\_quote.php?id={$row\['quote\_id'\]}\\">Edit</a> <-> 39 <a

href=\\"delete\_quote.php?id={$row\['quote\_id'\]}\\">Delete</a></p></div>\\n"; 40

41

} // End of while loop.

42

43 } else { // Query didn't run.

44

print '<p class="error">Could not retrieve the data because:<br />' . mysql\_error($dbc) . '.</

p><p>The query being run was: ' . $query . '</p>'; 45 } // End of query IF.

46

47 mysql\_close($dbc); // Close the connection.

48

49 include('templates/footer.html'); // Include the footer.

50 ?>

398 Chapter

13

The query returns four columns—all but

For each quote, two links must be

the date entered—from the database for

created. The first is to **edit\_quote.php**

every record. The results will be returned

and the second to **delete\_quote.php**.

in order by the date they were entered.

Each link must also pass the **quote\_id**

value along in the URL, as the code in

**4.** Execute the query and begin retrieving

Chapter 12 does

the results:

**B**.

The end of the **print** statement closes

**if ($r = mysql\_query($query,**

the DIV for the specific quotation

➝ **$dbc)) {**

(begun in Step 5).

**while ($row = mysql\_fetch\_**

 ➝ **array($r)) {**

**8.** Complete the **while** loop and the

**mysql\_query()** conditional:

The **while** loop code was explained

in Chapter 12, even though it wasn’t

**} // End of while loop.**

used in that chapter. This construct is

**} else { // Query didn't run.**

how you fetch every record returned

**print '<p class="error">Could**

by a query.

 ➝ **not retrieve the data**

➝ **because:<br />' . mysql\_**

**5.** Begin printing the record:

 ➝ **error($dbc) . '.</p><p>The**

**print "<div><blockquote>**

 ➝ **query being run was: ' .**

➝ **{$row\['quote'\]}</blockquote>-**

 ➝ **$query . '</p>';**

➝ **{$row\['source'\]}\\n";**

**} // End of query IF.**

This code starts a DIV, places the

**9.** Close the database connection:

quotation itself within **blockquote** tags,

**mysql\_close($dbc);**

and then shows the quote’s attribution.

**10.** Complete the page:

**6.** Indicate that the quotation is a favorite,

if applicable:

**include('templates/footer.html');**

**?>**

**if ($row\['favorite'\] == 1) {**

**print ' <strong>Favorite!**

**11.** Save the view as **view\_quotes.php** and

 ➝ **</strong>';**

test in your Web browser.

**}**

The value of **$row\['favorite'\]** will be

**As some of the queries in this chapter**

**demonstrate, you can use a column or value in**

either 1 or 0. If it’s 1, the word Favorite!,

**an ORDER BY clause even if it’s not selected by**

emphasized, is displayed along with

**the query.**

the record.

**7.** Add administrative links for editing and

deleting the quote:

**print "<p><b>Quote Admin:</b>**

➝ **<a href=\\"edit\_quote.php?id=**

➝ **{$row\['quote\_id'\]}\\">Edit</a> <->**

**<a href=\\"delete\_quote.php?id=**

➝ **{$row\['quote\_id'\]}\\">Delete</a>**

➝ **</p></div>\\n";**

Putting It All Together 399

![Image 496](index-421_1.png)

[**Editing Quotes**](#index_split_000.html#p9)

The **view\_quotes.php** page (and later,

**index.php**) has links to **edit\_quote.php**,

where the administrator can update a

quote. Functionally, this script will be very

similar to **edit\_entry.php** from Chapter 12:

**1.** The script needs to receive an ID value

in the URL.

**2.** Using the ID, the record is retrieved and

used to populate a form **A**.

**3.** Upon form submission, the form data

will be validated (even if only slightly).

**4.** If the form data passes validation, the

record will be updated in the database.

**A** The form’s elements are prepopulated,

and pre-checked, using the record’s

For the most part, this script is just another

existing values.

application of what you’ve already seen.

But one new thing you’ll learn here is how

**Script 13.9** The **edit\_quote.php** script gives the

to check or not check a form’s checkbox

administrator a way to update an existing record.

element based on a preexisting value.

1

<?php // Script 13.9 - edit\_quote.php

2

/\* This script edits a quote. \*/

**To create edit\_quote.php:**

3

4

// Define a page title and include the

**1.** Begin a new PHP document in

header:

your text editor or IDE, to be named

5

define('TITLE', 'Edit a Quote');

**edit\_quote.php** (**Script 13.9**):

6 include('templates/header.html');

7

**<?php // Script 13.9 -**

8

print '<h2>Edit a Quotation</h2>';

➝ **edit\_quote.php**

9

**define('TITLE', 'Edit a Quote');**

10 // Restrict access to administrators only:

11 if (!is\_administrator()) {

**include('templates/header.html');**

12

print '<h2>Access Denied!</h2>

**print '<h2>Edit a Quotation</h2>';**

<p class="error">You do not have

permission to access this page.</p>';

**2.** Terminate the script if the user isn’t

13 include('templates/footer.html');

an administrator:

14 exit();

15 }

**if (!is\_administrator()) {**

16

**print '<h2>Access Denied!</h2>**

17 // Need the database connection:

 ➝ **<p class="error">You do not**

18 include('../mysql\_connect.php');

 ➝ **have permission to access**

19

 ➝ **this page.</p>';**

20

if (isset($\_GET\['id'\]) && is\_numeric

($\_GET\['id'\]) && ($\_GET\['id'\] > 0) ) { //

**include('templates/footer.html');**

Display the entry in a form:

**exit();**

21

**}**

22

// Define the query.

code continues on next page

400 Chapter

13

**3.** Include the database connection:

anything for the security of the script—

**include('../mysql\_connect.php');**

the **is\_numeric()** test confirms that

the value is safe to use in a query, but

Both phases of the script—displaying

prevents the query from being executed

the form and handling the form—require

if the ID has an unusable value.

a database connection, so the included

**5.** Define and execute the query:

file is incorporated at this point.

**$query = "SELECT quote, source,**

**4.** Validate that a numeric ID value was

received in the URL:

➝ **favorite FROM quotes WHERE**

➝ **quote\_id={$\_GET\['id'\]}";**

**if (isset($\_GET\['id'\]) &&**

**if ($r = mysql\_query($query,**

➝ **is\_numeric($\_GET\['id'\]) &&**

➝ **$dbc)) {**

➝ **($\_GET\['id'\] > 0) ) {**

**$row = mysql\_fetch\_array($r);**

This conditional is like one from

The query returns three columns for a

Chapter 12, with the addition of

specific record.

checking that the ID value is greater

continues on next page

than 0. Adding that clause doesn’t do

**Script 13.9** continued

23

$query = "SELECT quote, source, favorite FROM quotes WHERE quote\_id={$\_GET\['id'\]}"; 24

if ($r = mysql\_query($query, $dbc)) { // Run the query.

25

26

$row = mysql\_fetch\_array($r); // Retrieve the information.

27

28

// Make the form:

29

print '<form action="edit\_quote.php" method="post"> 30

<p><label>Quote <textarea name="quote" rows="5" cols="30">' . htmlentities($row\['quote'\])

. '</textarea></label></p>

31

<p><label>Source <input type="text" name="source"value="' . htmlentities($row\['source'\])

. '" /></label></p>

32

<p><label>Is this a favorite? <input type="checkbox" name="favorite" value="yes"'; 33

34

// Check the box if it is a favorite:

35

if ($row\['favorite'\] == 1) {

36 print

'

checked="checked"';

37 }

38

39

// Complete the form:

40 print

'

/></label></p>

41

<input type="hidden" name="id" value="' . $\_GET\['id'\] . '" /> 42

<p><input type="submit" name="submit" value="Update This Quote!" /></p> 43 </form>';

44

45

} else { // Couldn't get the information.

46

print '<p class="error">Could not retrieve the quotation because:<br />' . mysql\_

error($dbc) . '.</p><p>The query being run was: ' . $query . '</p>'; 47 }

48

code continues on next page

Putting It All Together 401

**6.** Begin creating the form:

**<p><label>Source <input type=**

➝ **"text" name="source"value="' .**

**print '<form action="edit\_quote.php"**

➝ **htmlentities($row\['source'\]) .**

➝ **method="post">**

➝ **'" /></label></p>**

**<p><label>Quote <textarea name=**

**<p><label>Is this a favorite?**

➝ **"quote" rows="5" cols="30">' .**

➝ **<input type="checkbox"**

➝ **htmlentities($row\['quote'\]) .**

➝ **name="favorite" value="yes"';**

➝ **'</textarea></label></p>**

**Script 13.9** continued

49 } elseif (isset($\_POST\['id'\]) && is\_numeric($\_POST\['id'\]) && ($\_POST\['id'\] > 0)) { // Handle the form.

50

51

// Validate and secure the form data:

52

$problem = FALSE;

53

if ( !empty($\_POST\['quote'\]) && !empty($\_POST\['source'\]) ) {

54

55

// Prepare the values for storing:

56

$quote = mysql\_real\_escape\_string(trim(strip\_tags($\_POST\['quote'\])), $dbc); 57

$source = mysql\_real\_escape\_string(trim(strip\_tags($\_POST\['source'\])), $dbc); 58

59

// Create the "favorite" value:

60 if

(isset($\_POST\['favorite'\]))

{

61

$favorite = 1;

62 }

else

{

63

$favorite = 0;

64 }

65

66

} else {

67

print '<p class="error">Please submit both a quotation and a source.</p>'; 68 $problem

\=

TRUE;

69 }

70

71

if (!$problem) {

72

73

// Define the query.

74

$query = "UPDATE quotes SET quote='$quote', source='$source', favorite=$favorite WHERE

quote\_id={$\_POST\['id'\]}";

75

if ($r = mysql\_query($query, $dbc)) {

76

print '<p>The quotation has been updated.</p>';

77 }

else

{

78

print '<p class="error">Could not update the quotation because:<br />' . mysql\_

error($dbc) . '.</p><p>The query being run was: ' . $query . '</p>'; 79 }

80

81

} // No problem!

82

83 } else { // No ID set.

84

print '<p class="error">This page has been accessed in error.</p>'; 85 } // End of main IF.

86

87 mysql\_close($dbc); // Close the connection.

88

89 include('templates/footer.html'); // Include the footer.

90 ?>

402 Chapter

13

![Image 497](index-424_1.png)

The form is posted back to this same

page. It starts with a text area, whose

value will be prepopulated with

the quote value retrieved from the

database. That value is run through

**htmlentities()** as a safety precaution.

Next, a text input is created,

prepopulated with the quotation’s

source. Finally, the checkbox for the

indication of the favorite is begun.

Note that this checkbox element is not

completed, as the script needs to next

determine whether or not to check the

box (in Step 7).

**7.** Check the box if it is a favorite:

**if ($row\['favorite'\] == 1) {**

**print ' checked="checked"';**

**}**

If the record’s **favorite** value equals

1, then the administrator previously

marked this quotation as a favorite. In

that case, additional HTML needs to

be added to the checkbox input to pre-

check it. After this point in the code, the

favorite checkbox’s underlying HTML

will be either

**<input type="checkbox"**

➝ **name="favorite" value="yes"**

or **B**

**<input type="checkbox"**

➝ **name="favorite" value="yes"**

➝ **checked="checked"**

continues on next page

**B** The HTML source code for the page, upon first arriving, shows how the favorite checkbox can be pre-checked.

Putting It All Together 403

**8.** Complete the form:

The form validation for the edit page

**print ' /></label></p>**

mirrors that in the **add\_quote.php** script

**<input type="hidden" name="id"**

(Script 13.7).

➝ **value="' . $\_GET\['id'\] . '" />**

**12.** Prepare the values for use in the query:

**<p><input type="submit" name=**

**$quote = mysql\_real\_escape\_string**

➝ **"submit" value="Update This**

➝ **(trim(strip\_tags($\_POST**

➝ **Quote!" /></p>**

➝ **\['quote'\])), $dbc);**

**</form>';**

**$source = mysql\_real\_escape\_**

The **print** statement starts by closing

➝ **string(trim(strip\_tags($\_POST**

the checkbox. Then the form must also

➝ **\['source'\])), $dbc);**

store the ID value in a hidden input, so

**if (isset($\_POST\['favorite'\])) {**

that it’s available to the script upon the

**$favorite = 1;**

form submission.

**} else {**

**9.** Create an error if the record could not

**$favorite = 0;**

be retrieved:

**}**

**} else { // Couldn't get the**

This code is also taken straight from

➝ **information.**

**add\_quote.php**.

**print '<p class="error">Could**

**13.** Indicate a problem if the form wasn’t

 ➝ **not retrieve the quotation**

completed:

 ➝ **because:<br />' . mysql\_**

**} else {**

 ➝ **error($dbc) . '.</p><p>The**

**print '<p class="error">Please**

 ➝ **query being run was: ' .**

 ➝ **submit both a quotation and**

 ➝ **$query . '</p>';**

 ➝ **a source.</p>';**

**}**

**$problem = TRUE;**

**10.** Check for a form submission:

**}**

**} elseif (isset($\_POST\['id'\]) &&**

**14.** If no problem occurred, update the

➝ **is\_numeric($\_POST\['id'\]) &&**

database:

➝ **($\_POST\['id'\] > 0)) {**

**if (!$problem) {**

This conditional begins the second phase

**$query = "UPDATE quotes SET**

of the script: handling the submission

 ➝ **quote='$quote', source=**

of the form. The validation is the same

 ➝ **'$source', favorite=$favorite**

as in Step 4, but now **$\_POST\['id'\]** is

 ➝ **WHERE quote\_id={$\_POST\['id'\]}";**

referenced instead of **$\_GET\['id'\]**.

**if ($r = mysql\_query($query,**

**11.** Validate the form data:

 ➝ **$dbc)) {**

**print '<p>The quotation has**

**$problem = FALSE;**

 ➝ **been updated.</p>';**

**if ( !empty($\_POST\['quote'\]) &&**

➝ **!empty($\_POST\['source'\]) ) {**

404 Chapter

13

![Image 498](index-426_1.png)

The **UPDATE** query updates the values

of three of the record’s columns. The

two string values are enclosed in single

quotation marks (within the query); the

numeric **$favorite** value is not.

The **WHERE** clause, which dictates the

**C** The result upon successfully

record to be updated, is the critical piece.

editing a record.

Finally, a simple message indicates the

success of the operation **C**.

**15.** Indicate a problem if the query failed:

**} else {**

**print '<p class="error">Could**

 ➝ **not update the quotation**

 ➝ **because:<br />' . mysql\_**

 ➝ **error($dbc) . '.</p><p>The**

 ➝ **query being run was: ' .**

 ➝ **$query . '</p>';**

**}**

**16.** Complete the conditionals:

**} // No problem!**

**} else { // No ID set.**

**print '<p class="error">This**

 ➝ **page has been accessed in**

 ➝ **error.</p>';**

**} // End of main IF.**

The **else** clause applies if no valid ID

value is received by the page via either

GET or POST.

**17.** Close the database connection and

complete the page:

**mysql\_close($dbc);**

**include('templates/footer.html');**

**?>**

**18.** Save the file and test in your Web browser

(by clicking a link on **view\_quotes.php**).

Putting It All Together 405

![Image 499](index-427_1.png)

![Image 500](index-427_2.png)

[**Deleting Quotes**](#index_split_000.html#p9)

The script for deleting existing quotations

mimics **delete\_entry.php** from Chapter 12.

Upon first arriving, assuming that a valid

record ID was passed along in the URL, the

quote to be deleted is displayed **A**. If the

administrator clicks the submit button, the

form will be submitted back to this same

page, at which point the record will be

removed from the database **B**.

**To create delete\_quote.php:**

**A** The first step for deleting a record is

confirming the record to be removed.

**1.** Begin a new PHP document in

your text editor or IDE, to be named

**delete\_quote.php** (**Script 13.10**):

**<?php // Script 13.10 -**

➝ **delete\_quote.php**

**define('TITLE', 'Delete a Quote');**

**B** Upon submission of the

**include('templates/header.html');**

form, the quotation is deleted

and a message is printed.

**print '<h2>Delete a Quotation</h2>';**

**Script 13.10** The **delete\_quote.php** script provides the administrator with a way to delete an existing record.

1

<?php // Script 13.10 - delete\_quote.php

2

/\* This script deletes a quote. \*/

3

4

// Define a page title and include the header:

5

define('TITLE', 'Delete a Quote');

6 include('templates/header.html');

7

8

print '<h2>Delete a Quotation</h2>';

9

10

// Restrict access to administrators only:

11 if (!is\_administrator()) {

12

print '<h2>Access Denied!</h2>

<p class="error">You do not have permission to access this page.</p>'; 13 include('templates/footer.html');

14 exit();

15 }

16

17 // Need the database connection:

18 include('../mysql\_connect.php');

19

20

if (isset($\_GET\['id'\]) && is\_numeric($\_GET\['id'\]) && ($\_GET\['id'\] > 0) ) { // Display the quote in a form:

code continues on next page

406 Chapter

13

**2.** Terminate the script if the user isn’t an administrator:

**if (!is\_administrator()) {**

**print '<h2>Access Denied!</h2>**

 ➝ **<p class="error">You do not**

 ➝ **have permission to access**

 ➝ **this page.</p>';**

**include('templates/footer.html');**

**exit();**

**}**

**3.** Include the database connection:

**include('../mysql\_connect.php');**

continues on next page

**Script 13.10** continued

21

22

// Define the query:

23

$query = "SELECT quote, source, favorite FROM quotes WHERE quote\_id={$\_GET\['id'\]}"; 24

if ($r = mysql\_query($query, $dbc)) { // Run the query.

25

26

$row = mysql\_fetch\_array($r); // Retrieve the information.

27

28

// Make the form:

29

print '<form action="delete\_quote.php" method="post"> 30

<p>Are you sure you want to delete this quote?</p>

31

<div><blockquote>' . $row\['quote'\] . '</blockquote>- ' . $row\['source'\]; 32

33

// Is this a favorite?

34

if ($row\['favorite'\] == 1) {

35 print

'

<strong>Favorite!</strong>';

36 }

37

38

print '</div><br /><input type="hidden" name="id" value="' . $\_GET\['id'\] . '" /> 39

<p><input type="submit" name="submit" value="Delete this Quote!" /></p> 40 </form>';

41

42

} else { // Couldn't get the information.

43

print '<p class="error">Could not retrieve the quote because:<br />' . mysql\_error($dbc) .

'.</p><p>The query being run was: ' . $query . '</p>'; 44 }

45

46

} elseif (isset($\_POST\['id'\]) && is\_numeric($\_POST\['id'\]) && ($\_POST\['id'\] > 0) ) { // Handle the form.

47

48

// Define the query:

49

$query = "DELETE FROM quotes WHERE quote\_id={$\_POST\['id'\]} LIMIT 1"; code continues on next page

Putting It All Together 407

**4.** Validate that a numeric ID value was

**6.** Begin creating the form:

received in the URL:

**print '<form action="delete\_quote.**

**if (isset($\_GET\['id'\]) &&**

➝ **php" method="post">**

➝ **is\_numeric($\_GET\['id'\]) &&**

**<p>Are you sure you want to**

➝ **($\_GET\['id'\] > 0) ) {**

➝ **delete this quote?</p>**

**<div><blockquote>' . $row\['quote'\] .**

This is the same conditional used in

**edit\_quote.php**.

➝ **'</blockquote>- ' .**

**$row\['source'\];**

**5.** Retrieve the record to be deleted:

The form, for the most part, just displays

**$query = "SELECT quote, source,**

the quotation.

➝ **favorite FROM quotes WHERE**

➝ **quote\_id={$\_GET\['id'\]}";**

**7.** Indicate if the quotation is a favorite:

**if ($r = mysql\_query($query, $dbc))**

**if ($row\['favorite'\] == 1) {**

➝ **{ $row = mysql\_fetch\_array($r);**

**print ' <strong>Favorite!**

The standard three fields are retrieved

➝ **</strong>';**

**}**

from the database for the record.

Because only one record is being

This code is the same as that on the

addressed in this script, the **mysql\_**

**view\_quotes.php** page, indicating that

**fetch\_array()** function is called once,

the quote is, in fact, a favorite.

outside of any loop.

**Script 13.10** continued

50

$r = mysql\_query($query, $dbc); // Execute the query.

51

52

// Report on the result:

53

if (mysql\_affected\_rows($dbc) == 1) {

54

print '<p>The quote entry has been deleted.</p>';

55

} else {

56

print '<p class="error">Could not delete the blog entry because:<br />' . mysql\_

error($dbc) . '.</p><p>The query being run was: ' . $query . '</p>'; 57 }

58

59 } else { // No ID received.

60

print '<p class="error">This page has been accessed in error.</p>'; 61 } // End of main IF.

62

63 mysql\_close($dbc); // Close the connection.

64

65 include('templates/footer.html');

66 ?>

408 Chapter

13

**8.** Complete the form:

The **DELETE** query will remove the

record. The **WHERE** conditional indicates

**print '</div><br />**

which specific record is to be removed,

**<input type="hidden" name="id"**

and the **LIMIT 1** clause is applied as an

➝ **value="' . $\_GET\['id'\] . '" />**

extra precaution.

**<p><input type="submit" name=**

➝ **"submit" value="Delete this**

**12.** Report on the result:

➝ **Quote!" /></p>**

**if (mysql\_affected\_rows($dbc)**

**</form>';**

➝ **\== 1) {**

The form must contain a hidden input

**print '<p>The quote entry has**

that will pass the quote ID back to the

 ➝ **been deleted.</p>';**

page upon form submission.

**} else {**

**print '<p class="error">Could**

**9.** Complete the **mysql\_query()** conditional:

 ➝ **not delete the blog entry**

**} else { // Couldn't get the**

 ➝ **because:<br />' . mysql\_**

➝ **information.**

 ➝ **error($dbc) . '.</p><p>The**

**print '<p class="error">Could**

 ➝ **query being run was: ' .**

 ➝ **not retrieve the quote**

 ➝ **$query . '</p>';**

 ➝ **because:<br />' . mysql\_**

**}**

 ➝ **error($dbc) . '.</p><p>The**

If the query succeeded, then one

 ➝ **query being run was: ' .**

record will have been affected, and a

 ➝ **$query . '</p>';**

message is displayed to the user

**}**

**B**.

**13.** Complete the conditionals:

If the query failed, the MySQL error,

and the query itself, are displayed for

**} else { // No ID received.**

debugging purposes.

**print '<p class="error">This**

 ➝ **page has been accessed in**

**10.** Check for a form submission:

 ➝ **error.</p>';**

**} elseif (isset($\_POST\['id'\]) &&**

**} // End of main IF.**

 ➝ **is\_numeric($\_POST\['id'\]) &&**

The **else** clause applies if no valid ID

 ➝ **($\_POST\['id'\] > 0) )) {**

value is received by the page via either

This conditional begins the second phase

GET or POST.

of the script: handling the submission

**14.** Close the database connection and

of the form. The validation is the same

complete the page:

as in Step 4, but now **$\_POST\['id'\]** is

referenced instead of **$\_GET\['id'\]**.

**mysql\_close($dbc);**

**include('templates/footer.html');**

**11.** Delete the record:

**?>**

**$query = "DELETE FROM quotes**

**15.** Save the file and test in your Web browser

➝ **WHERE quote\_id={$\_POST\['id'\]}**

(by clicking a link on **view\_quotes.php**).

➝ **LIMIT 1";**

**$r = mysql\_query($query, $dbc);**

Putting It All Together 409

![Image 501](index-431_1.png)

![Image 502](index-431_2.png)

[**Creating the**](#index_split_000.html#p9)

[**Home Page**](#index_split_000.html#p9)

Last, but certainly not least, there’s the

home page. For this site, the home page

will be the only page used by the public at

large. The home page will show a single

quotation, but the specific quotation can

be one of the following:

■

The most recent (the default)

**A** Values passed in the URL trigger the execution

■

A random quotation

of different queries.

■

A random favorite quotation

To achieve this effect, links will pass

different values in the URL back to this

same page **A**.

The script should also display

administrative links—edit and delete—

for the currently displayed quote, if the

user is an administrator **B**.

**To create index.php:**

**1.** Begin a new PHP document in your text

editor or IDE, to be named **index.php**

**B** When an administrator views the home page,

(Script 13.11):

extra links are displayed.

**<?php // Script 13.11 - index.php**

**Script**

**2.** Include the header:

**13.11** The home page of the site shows a

single quotation at a time, plus administrative links

**include('templates/header.html');**

(when appropriate).

The home page does not need a

1

<?php // Script 13.11 - index.php

custom title, so no constant is defined

2

/\* This is the home page for this site.

It displays:

before including the header.

3

\- The most recent quote (default)

**3.** Include the database connection:

4

\- OR, a random quote

5

\- OR, a random favorite quote \*/

**include('../mysql\_connect.php');**

6

**4.** Begin defining the query to be run:

7

// Include the header:

8 include('templates/header.html');

**if (isset($\_GET\['random'\])) {**

9

**$query = 'SELECT quote\_id,**

10 // Need the database connection:

 ➝ **quote, source, favorite FROM**

11 include('../mysql\_connect.php');

12

 ➝ **quotes ORDER BY RAND() DESC**

13 // Define the query...

 ➝ **LIMIT 1';**

code continues on next page

410 Chapter

13

If a **$\_GET\['random'\]** variable is set, the This query is similar to that in Step 4,

user clicked a link requesting a random

but it uses a **WHERE** clause to restrict the

quotation. It doesn’t matter what value

pool of possible quotations to just those

this variable has, so long as it is set.

whose **favorite** value equals 1.

For all of the queries, four columns—

**6.** Define the default query:

**quote\_id**, the **quote**, the **source**,

**} else {**

and **favorite**—from one row will be

**$query = 'SELECT quote\_id,**

returned. To only retrieve one row, a

 ➝ **quote, source, favorite FROM**

**LIMIT 1** clause is used.

 ➝ **quotes ORDER BY date\_entered**

To select a random row in MySQL, use

 ➝ **DESC LIMIT 1';**

the **ORDER BY RAND()** clause. This code

**}**

uses MySQL’s **RAND()** function, short

If no value was passed in the URL,

for random, to return the records in a

then the home page should display the

random order. So this query first selects

most recently added quotation. To do

every record in random order, and then

that, the query orders all of the quotes

returns only the first in that set.

in descending order of date entered,

**5.** Define the query that selects a random

and then limits the results to just a

favorite record:

single record.

**} elseif (isset($\_GET\['favorite'\])) {**

**7.** Execute the query and fetch the

**$query = 'SELECT quote\_id,**

returned record:

 ➝ **quote, source, favorite FROM**

**if ($r = mysql\_query($query, $dbc)) {**

 ➝ **quotes WHERE favorite=1 ORDER**

**$row = mysql\_fetch\_array($r);**

 ➝ **BY RAND() DESC LIMIT 1';**

continues on next page

**Script 13.11** continued

14 // Change the particulars depending upon values passed in the URL: 15 if (isset($\_GET\['random'\])) {

16

$query = 'SELECT quote\_id, quote, source, favorite FROM quotes ORDER BY RAND() DESC LIMIT 1'; 17 } elseif (isset($\_GET\['favorite'\])) {

18

$query = 'SELECT quote\_id, quote, source, favorite FROM quotes WHERE favorite=1 ORDER BY

RAND() DESC LIMIT 1';

19 } else {

20

$query = 'SELECT quote\_id, quote, source, favorite FROM quotes ORDER BY date\_entered DESC

LIMIT 1';

21 }

22

23 // Run the query:

24 if ($r = mysql\_query($query, $dbc)) {

25

26

// Retrieve the returned record:

27

$row = mysql\_fetch\_array($r);

28

29

// Print the record:

30

print "<div><blockquote>{$row\['quote'\]}</blockquote>- {$row\['source'\]}"; code continues on next page

Putting It All Together 411

**8.** Print the quotation:

**10.** If the user is an administrator, create

**print "<div><blockquote>{$row**

links to edit or delete this record:

➝ **\['quote'\]}</blockquote>-**

**if (is\_administrator()) {**

➝ **{$row\['source'\]} ";**

**print "<p><b>Quote Admin:</b>**

This code is similar to that in

➝ **<a href=\\"edit\_quote.php?**

**view\_quotes.php**

, but only needs

➝ **id={$row\['quote\_id'\]}\\">Edit**

to be used once.

➝ **</a> - + | + -**

**<a**

**href=\\"delete\_quote.php?**

**9.** Indicate if the quotation is a favorite

 ➝ **id={$row\['quote\_id'\]}\\">**

and complete the DIV:

 ➝ **Delete</a>**

**if ($row\['favorite'\] == 1) {**

**</p>\\n";**

**print ' <strong>Favorite!**

**}**

 ➝ **</strong>';**

If the user is an administrator, links

**}**

to the edit and delete scripts will

**print '</div>';**

be added to the page. The links

The conditional is the same as

themselves have values just like

in **delete\_quote.php** and **view\_**

those in **view\_quotes.php**.

**quotes.php**.

**Script 13.11** continued

31

32

// Is this a favorite?

33

if ($row\['favorite'\] == 1) {

34 print

'

<strong>Favorite!</strong>';

35 }

36

37 // Complete the DIV:

38 print

'</div>';

39

40

// If the admin is logged in, display admin links for this record: 41

if (is\_administrator()) {

42

print "<p><b>Quote Admin:</b> <a href=\\"edit\_quote.php?id={$row\['quote\_id'\]}\\">Edit</a> <-> 43 <a

href=\\"delete\_quote.php?id={$row\['quote\_id'\]}\\">Delete</a> 44 </p>\\n";

45 }

46

47 } else { // Query didn't run.

48

print '<p class="error">Could not retrieve the data because:<br />' . mysql\_error($dbc) .

'.</p><p>The query being run was: ' . $query . '</p>'; 49 } // End of query IF.

50

51 mysql\_close($dbc); // Close the connection.

52

53

print '<p><a href="index.php">Latest</a> <-> <a href="index.php?random=true">Random</a> <->

<a href="index.php?favorite=true">Favorite</a><p>'; 54

55 include('templates/footer.html'); // Include the footer.

56 ?>

412 Chapter

13

![Image 503](index-434_1.png)

**11.** If the query didn’t run, print an error

Three public links are added to the

message:

page, each back to this same script. The

first link, which passes no values in the

**} else { // Query didn't run.**

URL, will always show the most recent

**print '<p class="error">Could**

quotation. The second, which passes

 ➝ **not retrieve the data**

a random value in the URL, will trigger

 ➝ **because:<br />' . mysql\_error**

the query in Step 4, thereby retrieving

 ➝ **($dbc) . '.</p><p>The query**

a random record. The third link, which

 ➝ **being run was: ' . $query .**

passes a favorite value in the URL, will

 ➝ **'</p>';**

trigger the query in Step 5, thereby

**} // End of query IF.**

retrieving a random favorite record.

This code is for your own debugging

**14.** Include the footer and complete the page:

purposes. You would not display a

MySQL error, or the query that caused

**include('templates/footer.html');**

it, to the general public.

**?>**

**12.** Close the database connection:

**15.** Save the file and test in your Web

browser

**mysql\_close($dbc);**

**C**.

The database connection will no longer be

**Normally the home page is one of the first**

needed, so it can be closed at this point.

**scripts written, not the last. But in this case I**

**13.** Create links to other pages:

**wanted to build up to this point in the example.**

**print '<p><a href="index.php">**

 ➝ **Latest</a> <-> <a href=**

 ➝ **"index.php?random=true">**

 ➝ **Random</a> <-> <a href=**

 ➝ **"index.php?favorite=true">**

 ➝ **Favorite</a><p>';**

**C** The latest quotation (note the URL).

Putting It All Together 413

[**Review and Pursue**](#index_split_000.html#p9)

**Pursue**

■

Make the login form sticky.

If you have any problems with the review

questions or the pursue prompts, turn

■

Define the login credentials—the

to the book’[s supporting forum (www.](http://www.LarryUllman.com/forum/)

cookie name and value—as constants

[LarryUllman.com/ forum/ ).](http://www.LarryUllman.com/forum/)

in a configuration file. Then include

that configuration file on every page

**Review**

and use those constants for creating,

deleting, and confirming the value of

■

How would the **is\_administrator()**

the cookie.

function be called to check for the

■

Limit the cookie’s expiration to only 15

same cookie—named Samuel—with a

minutes, and then re-send the cookie

different value? A different cookie—not

on each page, if appropriate (i.e., if the

named Samuel—with a different value?

cookie exists).

■

Why is the reference to the style sheet

■

Use sessions instead of a cookie.

in the header file **css/style.css** instead

of **../css/style.css**? How else could

■

Make the **add\_quote.php** and **edit\_**

the style sheet be referenced?

**quote.php** forms sticky.

■

Why is the **login.php** script structured

■

Change **view\_quotes.php** so that the

the way it is? How could that script be

administrator can list the quotes in

organized more linearly?

different order. Hint: Create links back

to the page like those on **index.php**

■

What would be some other good ideas

and change the query accordingly.

for user-defined functions with this site?

Hint: look for repeated code.

■

Before putting this site on a live server

(should you do that), update all the

code so that no MySQL error is ever

shown to a nonadministrative user.

414 Chapter

13

[**A**](#index_split_000.html#p9)

[Installation and](#index_split_000.html#p9)

[Configuration](#index_split_000.html#p9)

There are three technical requirements

**Installation on Windows**

for executing all of this book’s examples:

MySQL (the database application), PHP

Although you can certainly install a Web

(the scripting language), and the Web

server (like Apache, Abyss, or IIS), PHP,

server application (that PHP runs through).

and MySQL individually on a Windows

This appendix describes the installation

computer, I strongly recommend you use

of these tools on two different platforms—

an all-in-one installer instead. It’s simply

Windows XP and Mac OS X. If you are

easier and more reliable to do so.

using a hosted Web site, all of this will

There are several all-in-one installers out

already be provided for you, but these

there for Windows. The two that I see

products are all free and easy enough

mentioned most frequently are XAMPP

to install, so putting them on your own

[(www.apachefriends.org) and W](http://www.apachefriends.org)AMP

computer still makes sense.

[(www.wampserver.com). For this appendix,](http://www.wampserver.com)

After the installation section, this appendix

I’ll use XAMPP, which runs on Windows

demonstrates some basics for working

2000, 2003, XP, and Vista. (The XAMPP

with MySQL and configuring PHP. The PHP

site makes no mention of Windows 7, but

and MySQL manuals cover installation and

you should be able to use XAMPP on that

configuration in a reasonable amount of

version of Windows.)

detail. You may want to also peruse them,

particularly if you encounter problems.

Along with Apache, PHP, and MySQL,

XAMPP also installs:

**On Firewalls**

■

PEAR (PHP Extension and Application

A firewall prevents communication over

Repository), a library of PHP code

ports (a port is an access point to a

computer). Versions of Windows starting

■

phpMyAdmin, the Web-based interface

with Service Pack 2 of XP include a

to a MySQL server

built-in firewall. You can also download

■

A mail server (for sending email)

and install third-party firewalls. Firewalls

improve the security of your computer,

■

Several useful extensions

but they may also interfere with your

As of this writing, XAMPP (Version 1.7.3)

ability to run Apache, MySQL, and

installs PHP 5.31, MySQL 5.1.41, Apache

some of the other tools used by XAMPP

2.2.14, and phpMyAdmin 3.2.4.

because they all use ports.

I’ll run through the installation process in

When running XAMPP for the first time, if

these next steps. Note that if you have

you see a security prompt indicating that

the firewall is blocking Apache, MySQL,

any problems, you can use the book’s

or the like, choose Unblock. Otherwise,

[supporting forum (www.LarryUllman.com/](http://www.LarryUllman.com/forum/)

you can configure your firewall manually

[forum/), but you’ll probably have more](http://www.LarryUllman.com/forum/)

(for example, on Windows XP, it’s done

luck turning to the XAMPP site (it is their

through Control Panel > Security Center).

product, after all). Also, the installer works

The ports that need to be open are

really well and isn’t that hard to use, so

as follows: 80 (for Apache), 3306 (for

rather than detail every single step in the

MySQL), and 25 (for the Mercury mail

process, I’ll highlight the most important

server). If you have any problems starting

considerations.

or accessing one of these, disable your

firewall and see if it works then. If so,

you’ll know the firewall is the problem

and that it needs to be reconfigured.

Just to be clear, firewalls aren’t found

just on Windows, but in terms of the

instructions in this appendix, the

presence of a firewall will more likely trip

up a Windows user than any other.

416 Appendix

A

![Image 504](index-438_1.jpg)

![Image 505](index-438_2.png)

![Image 506](index-438_3.png)

**To install XAMPP on Windows:**

**1.** Download the latest release of XAMPP for

[Windows from www.apachefriends.org.](http://www.apachefriends.org)

You’ll need to click around a bit to find

the download section, but eventually

you’ll come to an area where you can

find the download **A**. Then click EXE,

which is the specific item you want.

**A** From the Apache Friends Web site, grab the

latest installer for Windows.

**2.** On your computer, double-click the

downloaded file in order to begin the

installation process.

**3.** When prompted **B**, install XAMPP

somewhere other than in the Program

Files directory.

You shouldn’t install it in the Program Files

directory because of a permissions issue

in Windows Vista. I recommend installing

XAMPP in your root directory (e.g., **C:\\**).

Wherever you decide to install the

program, make note of that location, as

you’ll need to know it several other times

**B** Select where XAMPP should be installed.

as you work through this appendix.

**4.** If you want, create Desktop and Start

Menu shortcuts **C**.

During the installation process, XAMPP

will open a console window, where you’ll

be prompted for additional options.

**C** The XAMPP console window.

**5.** When prompted, have XAMPP locate

the paths correctly.

**6.** When prompted, do not make a por-

table XAMPP without drive letters.

**7.** Continue through the remaining

prompts, reading them and pressing

Enter/Return to continue.

You’ll be notified that the installation

is successful, what time zone was set

in the PHP configuration, and so forth.

Nothing that significant here.

continues on next page

Installation and Configuration 417

![Image 507](index-439_1.png)

![Image 508](index-439_2.png)

![Image 509](index-439_3.jpg)

**8.** After the installation process has done its

thing **D**, enter 1 to start the control panel.

Upon completion of the installation,

you’ll be given a few options, still within

the console window. One option is to

start the control panel, which can also

be done using the Desktop or Start

Menu shortcuts, assuming you chose

to create those in Step 4.

**D** The installation of XAMPP is complete!

**9.** To start, stop, and configure XAMPP,

use the XAMPP control panel **E**.

**10.** Using the control panel, start Apache,

MySQL, and Mercury.

Apache has to be running for every

chapter in this book. MySQL must

be running for Chapter 12, “Intro to

Databases.” Mercury is the mail server

that XAMPP installs. It needs to be running

in order to send email using PHP (see

Chapter 8, “Creating Web Applications”).

**11.** Immediately set a password for the

root MySQL user.

**E** The XAMPP control panel, used to manage

How you do this is explained later in

the software.

the chapter.

**The XAMPP control panel’s various**

**admin links will take you to different Web**

**pages (on your server) and other resources F.**

**See the “PHP Configuration” section**

**to learn how to configure PHP by editing the**

**php.ini file.**

**Your Web root directory—where your**

**PHP scripts should be placed in order to test**

**them—is the htdocs folder in the directory**

**where XAMPP was installed. Following my**

**installation instructions, this would be**

**C:\\xampp\\htdocs.**

**F** The Web-based splash page for XAMPP, linked

from the control panel.

418 Appendix

A

**Installation on Mac OS X**

Thanks to some ready-made packages,

installing MySQL and PHP on Mac OS X

used to be surprisingly easy (and may still

be for you). Mac OS X already uses Apache

as its Web server and comes with a version

of PHP installed but not enabled. Thanks to

[Marc Liyanage (www.entropy.ch), who does](http://www.entropy.ch)

a ton of work supporting the Mac operating

system, more current and feature-rich

versions of PHP can be easily installed.

I say that installation “used to be” and

“may still be” easy because it depends

on the hardware and operating system

you’re using. Starting with Mac OS X 10.5

(Leopard), the version of Apache included

is 64-bit (assuming your computer supports

it), meaning that PHP must also be 64-bit, as

must every library that PHP uses. This is not

easily done.

Because of the complications that have

arisen from Mac OS X 10.5 using the 64-bit

version of Apache (if possible), I’ve decided

to take a more universally foolproof route

and recommend that you use the all-in-

[one MAMP installer (www.mamp.info).](http://www.mamp.info)

It’s available in both free and commercial

versions, is very easy to use, and won’t

affect the Apache server built into the

operating system.

Along with Apache, PHP, and MySQL,

MAMP also installs phpMyAdmin, the Web-

based interface to a MySQL server, along

with lots of useful PHP extensions. As of

this writing, MAMP (Version 1.9.4) installs

both PHP 5.2.13 and 5.3.2, in addition

to MySQL 5.1.44, Apache 2.0.63, and

phpMyAdmin 3.2.5.

continues on next page

Installation and Configuration 419

![Image 510](index-441_1.png)

![Image 511](index-441_2.jpg)

![Image 512](index-441_3.jpg)

I’ll run through the installation process in

these next steps. If you have any problems,

you can use the book’s supporting forum

[(www.LarryUllman.com/forum/), but you’ll](http://www.LarryUllman.com/forum/)

probably have more luck turning to the

MAMP site (it is their product, after all).

Also, the installer works really well and isn’t

that hard to use, so rather than detail every

single step in the process, I’ll highlight the

most important considerations.

**A** Download MAMP from this page at

[www.mamp.info.](http://www.mamp.info)

**To install MAMP on Mac OS X:**

**1.** Download the latest release of MAMP

[from www.mamp.info.](http://www.mamp.info)

On the front page, click Download, and

then click MAMP & MAMP PRO 1.9.4 **A**.

(As new releases of MAMP come out,

the link and filename will obviously

change accordingly.)

The same downloaded file is used for

both products. In fact, MAMP Pro is

just a nicer interface for controlling and

customizing the same MAMP software.

**B** The contents of the downloaded MAMP

**2.** On your computer, double-click the

disk image.

downloaded file in order to mount the

disk image **B**.

**3.** Copy the MAMP folder from the disk

image to your **Applications** folder.

If you think you might prefer the

commercial MAMP PRO, copy that folder

as well (again, it’s an interface to MAMP,

so both folders are required). MAMP PRO

comes with a free 14-day trial period.

Whichever folder you choose, note that

you must place it within the **Applications**

folder. It cannot go in a subfolder or

another directory on your computer.

**C** The simple MAMP application, used to control

and configure Apache, PHP, and MySQL.

420 Appendix

A

![Image 513](index-442_1.jpg)

![Image 514](index-442_2.jpg)

**4.** Open the **Applications/MAMP** (or

**Applications/MAMP PRO**) folder.

**5.** Double-click the MAMP (or MAMP PRO)

application to start the program **C**.

It may take just a brief moment to

start the servers, but then you’ll see

a result like that in **C** for MAMP

or **D** for MAMP PRO.

When starting MAMP, a start page

should also open in your default Web

browser **E**. Through this page you can

view the version of PHP that’s running,

as well as how it’s configured, and

interface with the MySQL database

**D** The MAMP PRO application, used to control

and configure Apache, PHP, MySQL, and more.

using phpMyAdmin.

With MAMP PRO, you can access that

same page by clicking the WebStart

button **D**.

continues on next page

**E** The MAMP Web start page.

Installation and Configuration 421

![Image 515](index-443_1.jpg)

![Image 516](index-443_2.jpg)

**6.** To start, stop, and configure MAMP, use

the MAMP or MAMP PRO application **C**

or **D**.

There’s not much to the MAMP

application itself (which is a good thing),

but if you click Preferences, you can

tweak the application’s behavior **F**, set

the version of PHP to run, and more.

MAMP PRO also makes it easy to create

different virtual hosts (i.e., different

sites), adjust how Apache is configured

and runs, use dynamic DNS, change

how email is sent, and more.

**F** These options dictate what happens when you

start and stop the MAMP application.

**7.** Immediately change the password for

the root MySQL user.

How you do this is explained later in

the chapter.

**Personally, I appreciate how great MAMP**

**alone is, and that it’s free. I also don’t like**

**spending money. But I’ve found the purchase**

**of MAMP PRO to be well worth the relatively**

**little money it costs.**

**See the “PHP Configuration” section**

**to learn how to configure PHP by editing the**

**php.ini file.**

**You may want to change the Apache**

**G** MAMP allows you to change where the Web

**Document Root G to the Sites directory in**

documents are placed.

**your home folder. By doing so, you assure that**

**your Web documents will backed up along**

**with your other files (and you are performing**

**regular backups, right?).**

**MAMP also comes with a Dashboard**

**widget you can use to control the Apache**

**and MySQL servers.**

**Your Web root directory—where your**

**PHP scripts should be placed in order to test**

**them—is the htdocs folder in the directory**

**where MAMP was installed. For a standard**

**MAMP installation without alteration, this**

**would be Applications/MAMP/htdocs.**

422 Appendix

A

![Image 517](index-444_1.png)

**To alter PHP’s configuration:**

**PHP Configuration**

**1.** In your Web browser, execute a script

One of the benefits of installing PHP on

that invokes the phpinfo() function **A**.

your own computer is that you can configure

The **phpinfo()** function, discussed in

it however you prefer. How PHP runs is

Chapter 1, “Getting Started with PHP,”

determined by the **php.ini** file, which is

reveals oodles of information about the

normally created when PHP is installed.

PHP installation.

Two of the most important settings

**2.** In the browser’s output, search for

you may want to consider adjusting are

Loaded Configuration File.

**display\_errors** and **error\_reporting**

(both are discussed in Chapter 3, “HTML

The value next to this text is the loca-

Forms and PHP”). To change any setting,

tion of the active configuration file.

open the PHP configuration file, edit it

This will be something like **C:\\xampp\\**

as needed, then save it and restart the

**php\\php.ini** or **/Library/Application**

Web server.

**Support/appsolute/MAMP PRO/conf/**

**php.ini**.

If there is no value for the Loaded Con-

figuration File, your server has no active

**php.ini** file. In that case, you’ll need to

download the PHP source code, from

[www.php.net, to find a sample configu-](http://www.php.net)

ration file.

continues on next page

**A** Some of the output from calling the **phpinfo()** function.

Installation and Configuration 423

**3.** Open the **php.ini** file in any text editor.

**Enabling Mail**

**4.** Change the settings as you wish.

The **mail()** function works only if the

Depending on your operating system,

computer running PHP has access to

you may need to be an administrator or

sendmail or another mail server. One

enter a password to make changes to

way to enable the **mail()** function is

this file.

to set the **smtp** value in the **php.ini**

Many instructions are included in the

file (for Windows only). This approach

file. Lines are commented out (made

works, for example, if your Internet

inactive) by preceding them with a

provider has an SMTP address you can

use. Unfortunately, you can’t use this

semicolon.

value if your ISP’s SMTP server requires

**5.** Save the **php.ini** file.

authentication.

**6.** Restart your Web server.

For Windows, there are also a number

of free SMTP servers, like Mercury. It’s

You don’t need to restart the entire com-

installed along with XAMPP, or you can

puter, just the Web server (e.g., Apache).

install it yourself if you’re not using XAMPP.

Mac OS X comes with a mail server

**You can also use the phpinfo() function**

installed—postfix and/or sendmail—that

**to confirm that your configuration changes**

needs to be enabled. Search Google for

**have taken effect.**

instructions on manually enabling your

**If you edit the php.ini file and restart**

mail server on Mac OS X.

**the Web server but your changes don’t take**

Alternatively, you can search some of the

**effect, make sure you’re editing the proper**

PHP code libraries to learn how to use an

**php.ini file (you may have more than one**

SMTP server that requires authentication.

**on your computer).**

**MAMP PRO on Mac OS X uses a tem-**

**plate for the php.ini file that must be edited**

**within MAMP PRO itself. To change the PHP**

**settings when using MAMP PRO, select File >**

**Edit Template > PHP X.X.X php.ini.**

424 Appendix

A

**MySQL Interfaces**

In Chapter 12 and Chapter 13, “Putting It

All Together,” a PHP script will be used

to interact with a MySQL database. As I

explain in Chapter 12, being able to interact

with MySQL independent of your PHP

scripts is the most valuable debugging tool

there is. Knowing how to use a separate

MySQL interface is therefore critical

information. I’ll quickly introduce the two

most common options.

**Using the MySQL Client**

The MySQL software comes with an

important tool called the MySQL client.

This application provides a simple interface

for communicating with the MySQL server.

It’s a command-line tool that must be

accessed using the Terminal application

on Linux and Mac OS X or through the

command (DOS) prompt on Windows.

**To use the MySQL client:**

**1.** Make sure the MySQL server is running.

**2.** Find the MySQL **bin** directory.

To connect to the client, you’ll need to

know where it’s located. The MySQL

client is found within the **bin** directory

for your installation. I’ll run through the

common possibilities.

If you installed MySQL yourself, the

client’s location depends on where you

installed the software, but it’s most likely

**C:\\mysql\\bin\\mysql** (Windows)

or

**/usr/local/mysql/bin/mysql**

(Mac OS X and Unix)

continues on next page

Installation and Configuration 425

![Image 518](index-447_1.png)

If you used XAMPP on Windows, it’s **C:\\**

**xampp\\mysql\\bin\\mysql** (assuming you

installed XAMPP in **C:\\**). If you installed

MAMP on Mac OS X, the MySQL

directory is **/Applications/MAMP/**

**Library/bin/mysql**.

**3.** Access a command prompt.

**A** Use the Run prompt to access a

On Mac OS X and Unix, you can

console window on Windows.

accomplish this by running the Terminal

application. On Mac OS X, it’s found within

the **Applications/Utilities** folder.

On Windows, click the Start menu,

select Run, and then type **cmd** and press

Enter or click OK at the prompt **A**.

**4.** Attempt to connect to the MySQL server.

To connect, enter the pathname

identified in Step 2 plus **\-u *username*** 

**\-p**. So, the command might be

**c:\\mysql\\bin\\mysql -u *username*** **\-p**

(Windows)

or

**/usr/local/mysql/bin/mysql -u**

***username*** **\-p** (Unix and Mac OS X)

or

**C:\\xampp\\mysql\\bin\\mysql -u**

***username*** **\-p** (Windows)

or

**/Applications/MAMP/Library/bin/**

**mysql -u *username*** **\-p** (Mac OS X)

Replace username with the username

you want to use. If you haven’t yet

created any other users, this will be

root (root is the supreme MySQL user).

If you haven’t yet established a root

user password (the default behavior for

XAMPP), you can omit the **\-p** flag.

426 Appendix

A

![Image 519](index-448_1.png)

![Image 520](index-448_2.png)

**5.** Enter the password at the prompt

**7.** Exit the MySQL client.

**B**.

The password requested is the MySQL

To do so, type **exit** or **quit**.

password for the user named during the

connection. You’ll see this prompt only

**If you see a Can’t connect to local**

if you used the **\-p** option in Step 4.

**MySQL server through socket… error message,**

**it normally means MySQL isn’t running.**

If you installed MAMP on Mac OS X, the

password for the root user will be root.

**The MySQL client is one of the best**

If you installed XAMPP on Windows,

**tools for debugging PHP scripts that work**

there is no password initially set.

**with MySQL. You can use the MySQL client**

**to check user permissions and to run queries**

**6.** List the available databases **C**:

**outside of the PHP script.**

**SHOW DATABASES;**

The **SHOW** **DATABASES** command is an

SQL query that lists every database

hosted on that MySQL installation that

the connected user can see.

**B** Successfully accessing the MySQL client on Windows.

**C** After a fresh MySQL

installation, there will

be only a couple of

default databases.

Installation and Configuration 427

![Image 521](index-449_1.jpg)

**Using phpMyAdmin**

phpMy[Admin (www.phpmyadmin.net)](http://www.phpmyadmin.net)

is a Web-based interface for interacting

with a MySQL server, allowing you to

create tables, import and export records,

and much more, without having to use a

command-line interface. It is arguably the

most popular Web software written in PHP,

as every PHP hosting company provides

it. In fact, the all-in-one XAMPP and MAMP

installers include it, too. phpMyAdmin is

well documented and easy to use, but I’ll

highlight a couple of quick points.

**To use phpMyAdmin:**

**1.** Access phpMyAdmin in your Web

browser **D**.

When using XAMPP, phpMyAdmin

is available at http://localhost /

phpmyadmin/, also found by clicking

the MySQL admin link in the control

panel. On MAMP, phpMyAdmin is

available by first going to http://

localhost:8888/MAMP/.

**2.** Click a database name in the left

column to select that database.

**D** The phpMyAdmin

front page.

428 Appendix

A

![Image 522](index-450_1.jpg)

**3.** Click a table name in the left column

to select that table **E**.

You don’t always have to select

a table, but by doing so you can

simplify some tasks.

**4.** Use the tabs and links (on the right side

of the page) to perform common tasks.

For the most part, the tabs and links are

shortcuts to common SQL commands.

For example, the Browse tab performs a

**SELECT** query and the Insert tab creates

a form for adding new records.

**5.** Use the SQL tab to execute any

SQL command.

You can alternatively use the SQL Query

Window, linked just above the list of

database or table names. Using either

interface, you can test queries that

your PHP scripts are using, without the

added complication of the script itself.

**There are many other clients for**

**interacting with a MySQL database, but the**

**MySQL command-line client and phpMyAdmin**

**are the two most common.**

**E** Selecting a database or a table, from the left column, changes the options on the right side of the page.

Installation and Configuration 429

**Managing MySQL Users**

Once you’ve successfully installed MySQL,

you can begin creating MySQL users. A

MySQL user is a fundamental security

concept, limiting access to, and influence

over, stored data. Just to clarify, your

databases can have several different users,

just as your operating system might. But

MySQL users are different from operating

system users. While learning PHP and

MySQL on your own computer, you don’t

necessarily need to create new users, but

live production sites need to have dedicated

MySQL users with appropriate permissions.

The initial MySQL installation comes with

one user (named root) with no password

set (except when using MAMP, which sets a

default password of root). At the very least,

you should create a new, secure password

for the root user after installing MySQL.

After that, you can create other users with

more limited permissions. As a rule, you

shouldn’t use the root user for normal, day-

to-day operations.

**Setting the root user password**

When you install MySQL, no value—or no

secure password—is established for the

root user. This is certainly a security risk

that should be remedied before you begin

to use the server (as the root user has

unlimited powers).

You can set any user’s password using

either phpMyAdmin or the MySQL client,

so long as the MySQL server is running.

If MySQL isn’t currently running, start it

now using the steps outlined earlier in

the appendix.

Second, you must be connected to MySQL

as the root user in order to be able to

change the root user’s password.

430 Appendix

A

![Image 523](index-452_1.png)

**To assign a password to the root**

**user via the MySQL client:**

**1.** Connect to the MySQL client.

See the preceding set of steps for

detailed instructions.

**2.** Enter the following command, replacing

thepassword with the password you

want to use **A**:

**SET PASSWORD FOR**

➝ **'root'@'localhost' =**

➝ **PASSWORD('thepassword');**

Keep in mind that passwords in

MySQL are case-sensitive, so Kazan

and kazan aren’t interchangeable.

The term **PASSWORD** that precedes the

actual quoted password tells MySQL to

encrypt that string. And there cannot be

a space between PASSWORD and the

opening parenthesis.

**3.** Exit the MySQL client:

**exit**

**4.** Test the new password by logging

into the MySQL client again.

Now that a password has been

established, you need to add the

**\-p** flag to the connection command.

You’ll see an Enter password:

prompt, where you enter the just-

created password.

**A** Updating the root user’s password using SQL within the

MySQL client.

Installation and Configuration 431

![Image 524](index-453_1.png)

![Image 525](index-453_2.png)

**To assign a password to the**

The result of changing the root user’s

**root user via phpMyAdmin:**

password will likely be that phpMyAdmin

is denied access to the MySQL server.

**1.** Open phpMyAdmin in your Web browser.

This is because phpMyAdmin, on a local

See the preceding set of steps for

server, normally connects to MySQL

detailed instructions.

as the root user, with the root user’s

**2.** On the home page, click the

password hard-coded into a configuration

Privileges tab.

file. After following Steps 1–4, find the

**config.inc.php** file in the phpMyAdmin

You can always click the home icon,

directory—likely **/Applications/MAMP/**

in the upper-left corner, to get to the

**bin/phpMyAdmin** (Mac OS X with MAMP)

home page.

or **C:\\xampp\\phpMyAdmin** (Windows with

**3.** In the list of users, click the Edit Privi-

XAMPP). Open that file in any text editor

leges icon on the root user’s row **B**.

or IDE and change this next line to use

**4.** Use the Change Password form **C**,

the new password:

found further down the resulting page,

**$cfg\['Servers'\]\[$i\]\['password'\]**

to change the password.

➝ **\= 'the\_new\_password';**

**5.** Change the root user’s password

Then save the file and reload

in phpMyAdmin’s configuration file,

phpMyAdmin in your Web browser.

if necessary.

**B** The list of MySQL users, as shown in phpMyAdmin.

**C** The form for updating a MySQL user’s password within phpMyAdmin.

432 Appendix

A

**Creating users and privileges**

**TABLE A.1 MySQL Privileges**

After you have MySQL successfully up

**PRIVILEGE**

**ALLOWS**

and running, and after you’ve established

**SELECT**

Read rows from tables.

a password for the root user, you can add

**INSERT**

Add new rows of data

other users. To improve the security of your

to tables.

databases, you should always create new

**UPDATE**

Alter existing data in tables.

users to access your databases rather than

using the root user at all times.

**DELETE**

Remove existing data from

tables.

The MySQL privileges system was

**INDEX**

Create and drop indexes

designed to ensure proper authority for

in tables.

certain commands on specific databases.

**ALTER**

Modify the structure of

This technology is how a Web host, for

a table.

example, can let several users access

**CREATE**

Create new tables or

several databases without concern. Each

databases.

user in the MySQL system can have

**DROP**

Delete existing tables

specific capabilities on specific databases

or databases.

from specific hosts (computers). The

**RELOAD**

Reload the grant tables

root user—the MySQL root user, not the

(and therefore enact user

changes).

system’s—has the most power and is used

to create subusers, although subusers can

**SHUTDOWN**

Stop the MySQL server.

be given rootlike powers (inadvisably so).

**PROCESS**

View and stop existing

MySQL processes.

When a user attempts to do something

**FILE**

Import data into tables from

with the MySQL server, MySQL first

text files.

checks to see if the user has permission

**GRANT**

Create new users.

to connect to the server at all (based on

the username, the user’s host, the user’s

**REVOKE**

Remove users’ permissions.

password, and the information in the **mysql**

database’s **user** table). Second, MySQL

checks to see if the user has permission

to run the specific SQL statement on the

specific databases—for example, to select

data, insert data, or create a new table.

**Table A.1** lists most of the various privileges

you can set on a user-by-user basis.

continues on next page

Installation and Configuration 433

There are a handful of ways to set users

com, or an IP address. Normally, localhost is

and privileges in MySQL, but I’ll start by

specified as the hostname, meaning that the

discussing the **GRANT** command. The

MySQL user must be connecting from the

syntax goes like this:

same computer that the MySQL database

**GRANT *privileges*** **ON *database*.\* TO**

is running on. To allow for any host, use the

➝ **' *username*'@' *hostname*' IDENTIFIED**

hostname wildcard character (**%**):

➝ **BY ' *password*';**

**GRANT *privileges*** **ON *database*.\***

For the privileges aspect of this statement,

➝ **TO ' *username*'@' *%*' IDENTIFIED**

you can list specific privileges from

➝ **BY ' *password*';**

Table A.1, or you can allow for all of them

But that is also not recommended. When

by using **ALL** (which isn’t prudent). The

it comes to creating users, it’s best to be

***database*****.\*** part of the statement specifies explicit and confining.

which database and tables the user can

The password has no length limit but

work on. You can name specific tables

is also case-sensitive. The passwords

using the ***database*****. *tablename*** syntax or are encrypted in the MySQL database,

allow for every database with **\*.\*** (again,

meaning they can’t be recovered in a plain

not prudent). Finally, you can specify the

text format. Omitting the **IDENTIFIED BY**

username, hostname, and a password.

**' *password*'** clause results in that user not The username has a maximum length of

being required to enter a password (which,

16 characters. When you’re creating a

once again, should be avoided).

username, be sure to avoid spaces (use

As an example of this process, you’ll create

the underscore instead), and note that

two new users with specific privileges on a

usernames are case-sensitive.

new database named temp. Keep in mind

The hostname is the computer from which

that you can only grant permissions to users

the user is allowed to connect. This could

on existing databases. This next sequence

be a domain name, such as www.example.

will also show how to create a database.

**Creating Users in phpMyAdmin**

To create users in phpMyAdmin, start by clicking the Privileges tab on the phpMyAdmin home page. On the Privileges page, click Add A New User. Complete the Add A New User form to define the user’s name, host, password, and privileges. Then click Go. This creates the user with general privileges but no database-specific privileges.

On the resulting page, select the database to apply the user’s privileges to and then click Go.

On the next page, select the privileges this user should have on that database, and then click Go again. This completes the process of creating rights for that user on that database. Note that this process allows you to easily assign a user different rights on different databases.

Finally, click your way back to the Privileges tab on the home page and then click the reload the privileges link.

434 Appendix

A

![Image 526](index-456_1.png)

![Image 527](index-456_2.png)

**To create new users using GRANT:**

**3.** Create a user with administrative-level

privileges on the **temp** database

**1.** Log in to the MySQL client as a root user.

**E**:

**GRANT SELECT, INSERT, UPDATE,**

Use the steps already explained to do

➝ **DELETE, CREATE, DROP,**

this. You must be logged in as a user

➝ **ALTER, INDEX ON temp.\* TO**

capable of creating databases and

➝ **'llama'@'localhost' IDENTIFIED**

other users.

➝ **BY 'camel';**

**2.** Create a new database **D**:

This user, llama, can create tables, alter

**CREATE DATABASE temp;**

tables, insert data, update data, and

If your MySQL server doesn’t yet have a

so forth, on the **temp** database. This

**temp** database, create one using **CREATE**

essentially includes every administrative-

**DATABASE** **temp** (followed by a semicolon,

level capability aside from creating new

as is required by the MySQL client).

users. Be certain to use a password—

perhaps one more clever than used

here—and, preferably, specify a

particular host.

continues on next page

**D** Creating a new database.

**E** Creating an administrative-level user for a single database.

Installation and Configuration 435

![Image 528](index-457_1.png)

![Image 529](index-457_2.png)

**4.** Create a user with basic access to

**5.** Apply the changes **G**:

the databases **F**:

**FLUSH PRIVILEGES;**

**GRANT SELECT, INSERT,**

The changes just made won’t take effect

➝ **UPDATE, DELETE ON temp.\* TO**

until you’ve told MySQL to reset the list of

➝ **'webuser'@'localhost' IDENTIFIED**

acceptable users and privileges, which is

➝ **BY 'BroWs1ng';**

what this command does. Forgetting this

Now the generic webuser can browse

step and then being unable to access the

through records (**SELECT** from tables)

database using the newly created users

as well as add, edit, and delete them,

is a common mistake.

but this user can’t alter the structure of

the database. When you’re establishing

**Any database whose name begins with**

users and privileges, work your way

**test\_ can be modified by any user who has**

from the bottom up, allowing the bare

**permission to connect to MySQL. Therefore,**

minimum of access at all times.

**be careful not to create a database named this**

**way unless it truly is experimental.**

**The REVOKE command removes users**

**and permissions.**

**F** This user has more restricted rights to the same database.

**G** Don’t forget this step before you try to

access MySQL using the newly created users.

436 Appendix

A

[**B**](#index_split_000.html#p9)

[Resources and](#index_split_000.html#p9)

[Next Steps](#index_split_000.html#p9)

This book was written to give beginning

**Online PHP Resources**

PHP programmers a good foundation on

which to base their learning. A few topics

If you have questions specifically about

have been either omitted or glossed over,

PHP, you should be able to find the answer

as the book focuses on covering the

with ease. This section of the appendix

absolute fundamentals. This appendix lists

highlights the best Internet-specific tools

a number of useful PHP-related Internet

for you to use.

resources; briefly discusses where to obtain

more information for databases and some

**The PHP manual**

uncovered topics; and includes a few tables,

All PHP programmers should familiarize

both old and new.

themselves with, and possibly acquire,

Along with those sites included here, you

some version of the PHP manual before

should check out the book’s companion

beginning to work with the language. The

Web site[, found at www.LarryUllman.com.](http://www.LarryUllman.com)

manual is available from the official PHP

There you’ll find all of the book’s code, a

[site—www.php.net /docs.php—as well as](http://www.php.net/docs.php)

support forum, an errata page, and more.

from a number of other locations.

Before getting to it, consider that when the

You can download the manual in nearly a

first edition of this book was written, few

dozen languages in different formats. The

good PHP sites were available. Now there

official Web site also has an annotated

are literally dozens (and hundreds of not-so-

[version of the manual available at www.php.](http://www.php.net/manual/en/)

good ones). The best, most obvious ones are

[net /manual/en/ (in English), where users](http://www.php.net/manual/en/)

included here, but a quick Internet search will

have added helpful notes and comments.

always be a great resource for you.

If you’re having problems with a particular

function, reading the manual’s page for that

function will likely provide an answer.

A trick pointed out in Chapter 1, “Getting

[W3Schools (www.w3schools.com) is a](http://www.w3schools.com)

Started with PHP,” is that you can quickly

good general Web development site, but it

access the documentation page for any

also focuses a good portion of its energies

[specific function by going to www.php.net /](http://www.php.net/functionname)

on PHP. For a cohesive look at developing

[functionname. For example](http://www.php.net/functionname), the page for dynamic Web sites using PHP, HTML, CSS,

the **number\_format()** [function is www.php.](http://www.php.net/number_format)

and JavaScript, this is an excellent place

[net/number\_format.](http://www.php.net/number_format)

to turn.

When a good resource, PHP or otherwise,

**General PHP Web sites**

comes across my desk, I’ll normally

This section mentions a few of the many

reference it on my site. You can find any

useful Web sites you can turn to when

post related to PHP under the “PHP”

you’re programming, but I’ll leave it up to

[category here: www.larryullman.com/](http://www.larryullman.com/category/php/)

you to discover the ones you like best. Most

[category/php/.](http://www.larryullman.com/category/php/)

of these also contain links to other PHP-

related sites. The first, and most obvious,

**Code repositories**

site to bookmark is PHP.net [(www.php.net),](http://www.php.net)

There’s no shortage of code libraries

the official site for PHP.

online these days. Due to the generous

You should familiarize yourself with Zend

(and often showy) nature of PHP

[(www.zend.com), the home page for the](http://www.zend.com)

programmers, many sites have scores

creators of PHP’s core. The site contains

of PHP scripts, organized and available

numerous downloads plus a wealth

for download. The best online code

of other resources—straight from the

repositories are as follows:

masters, so to speak.

■

[HotScripts (www.hotscripts.com/PHP/)](http://www.hotscripts.com/PHP/)

For information on specific topics,

■

PHP R[esource Index (http://php.](http://php.resourceindex.com)

[PHPBuilder (www.phpbuilder.com) is one](http://www.phpbuilder.com)

[resourceindex.com)](http://php.resourceindex.com)

of many good places to turn. The site has

■

PHP Classes R[epository (www.](http://www.phpclasses.org)

dozens of articles explaining how to do

[phpclasses.org)](http://www.phpclasses.org)

particular tasks using PHP. On top of that,

PHPBuilder provides support forums and

■

PX: The PHP Code Ex[change (http://](http://px.sklar.com)

a code library where programmers have

[px.sklar.com)](http://px.sklar.com)

uploaded sample scripts.

You can also find code examples at Zend

You can also find useful articles at

and PHPBuilder or by searching the Web.

[PHP Zone (http://php.dzone.com) and](http://php.dzone.com)

There’s even a search engine dedicated to

[php|architect (www.phparch.com), which](http://www.phparch.com)

[finding code: www.koders.com.](http://www.koders.com)

also puts out a monthly PHP magazine.

438 Appendix

B

**Newsgroups and mailing lists**

**Database Resources**

If you have access to newsgroups, you can

Which database resources will be most

use them as a great sounding board for

useful to you depends, obviously, on which

ideas as well as a place to get your most

database management system (DBMS)

difficult questions answered. Of course,

you’re using. The most common database

you can always give back to the group by

used with PHP is probably MySQL, but

offering your own expertise to those in need.

PHP supports all the standard database

The largest English-language PHP

applications.

newsgroup is comp.lang.php. You may

To learn more about using MySQL, begin

be able to access it through your ISP or

with the official MySQL W[eb site (www.](http://www.mysql.com)

via a pay-for-use Usenet organization.

[mysql.com). Y](http://www.mysql.com)ou can download the MySQL

Newsgroups are also available in

manual to use as a reference while you

languages other than English.

work. A handful of books are also available

The PHP Web site lists the available

specifically on MySQL, including my own

[mailing lists you can sign up for at www.](http://www.php.net/mailing-lists.php)

MySQL: Visual QuickStart Guide, 2nd

[php.net/mailing-lists.php.](http://www.php.net/mailing-lists.php)

Edition (Peachpit Press, 2006).

Before you post to any newsgroup or

If you’re using MySQL, don’t forget to

mailing list, it will behoove you to read Eric

download and install phpMy[Admin (www.](http://www.phpmyadmin.net)

Steven Raymond’s “How to Ask Questions

[phpmyadmin.net). W](http://www.phpmyadmin.net)ritten in PHP, this is an the Smart W[ay” at www.catb.org/~esr/faqs/](http://www.catb.org/~esr/faqs/smart-questions.html)

invaluable tool for working with a database.

[smart-questions.html. The 10 minutes spent](http://www.catb.org/~esr/faqs/smart-questions.html)

If you’re using PostgreSQL or even Oracle,

reading that document will save you hours

you can find similar tools available for

when you go asking for assistance.

interfacing with them. Every database

application also has its own mailing lists

and newsgroups.

Another area of database resources

you should delve into is SQL. Web sites

discussing SQL, the language used by every

database application, include the following:

■

[SQL Course (www.sqlcourse.com)](http://www.sqlcourse.com)

■

A Gentle Introduction to SQL

[(www.sqlzoo.net)](http://www.sqlzoo.net)

■

W3Schools’ SQL Tutorial

[(www.w3schools.com/sql/)](http://www.w3schools.com/sql/)

■

SQL. [org (www.sql.org)](http://www.sql.org)

My PHP 6 and MySQL 5 for Dynamic Web

Sites: Visual QuickPro Guide (Peachpit

Press, 2008) also discusses SQL and MySQL

in much greater detail than this book.

Resources and Next Steps 439

**Top 10 Frequently Asked**

because they don’t pay attention to the

error message they see. Although some

**Questions (or Problems)**

of PHP’s error messages are cryptic and

even a few can be misleading, if PHP

Debugging is a valuable skill that takes

says there’s a problem on line 22, the

time and experience to fully develop.

problem is probably on line 22.

But rather than send you off on that

journey ill-equipped, I’ve included the

**4.** Avoid “trying” things to fix a problem!

10 most frequently seen problems in

If you’re not sure what’s causing the

PHP scripts, along with the most likely

problem and what the proper fix

causes. First, though, here are 5 of my

is, avoid trying random things as a

best pieces of advice when it comes to

solution. You’ll likely create new issues

debugging a problem:

this way and only further confuse the

**1.** Know what version of PHP you’re

original problem.

running.

**5.** Take a break!

Some problems are specific to a version

The best piece of advice I can offer is

of PHP. Use the **phpinfo()** function to

to step away from the computer and

test the version in use whenever you

take a break. I’ve solved many, many

go to use a server for the first time. Also

problems this way. Sometimes a clear

make sure you know what version of

head is what you need.

MySQL you’re using, if applicable; the

Moving on, here are the top 10 likely

operating system; and the Web server

problems you’ll encounter in PHP:

(e.g., Apache 2.2).

**1.** Blank Web pages

**2.** Run all PHP scripts through a URL.

If you see a blank screen in your

If you don’t run a PHP script through a

Web browser after submitting a form

URL—and this includes the submission

or loading a PHP script, it’s most

of a form to a PHP script—the Web

likely because an error occurred that

server will not handle the request,

terminated the execution of the page.

meaning that PHP will never execute

First check the HTML source code to

the code.

see if it’s an HTML problem. Then turn

**3.** Trust the error message!

on **display\_errors** in your **php.ini**

Many beginners have more difficulty

configuration file or PHP script to see

than they should in solving a problem

what PHP problem could be occurring.

440 Appendix

B

![Image 530](index-462_1.png)

![Image 531](index-462_2.png)

**2.** Undefined variable or undefined

to define your own function before calling

index error

it, or using a function that’s not available in

**A**

your version of PHP. Check your spelling

These errors occur when error

and the PHP manual for a non-user-

reporting is set on its highest level, and

defined function to find the problem.

they may or may not indicate a problem.

Check the spelling of each variable or

**5.** Headers already sent error **B**

array index to make sure it’s correct.

This error message indicates that

Then, either change the error reporting

you’ve used an HTTP header-related

settings or initialize variables prior to

function—**header()**, **setcookie()**,

referring to them. Also make sure, of

or **session\_start()**—after the Web

course, that variables that should have

browser has already received HTML or

a value actually do!

even a blank space. Double-check what

**3.** Variables that don’t have a value

occurs in a script before you call any

of these functions. You can also make

Perhaps you referred to a variable by

use of output buffering to prevent these

the wrong name. Double-check your

errors from occurring.

capitalization and spelling of variable

names, and then be certain to use

**6.** Access denied error **C**

**$\_GET**, **$\_POST**, **$\_COOKIE**, and **$\_SESSION**

If you see this message while

as appropriate. If need be, use the

attempting to work with a database,

**print\_r()** function to see the value of

then the username, password, and host

any variable.

combination you’re using doesn’t have

**4.** Call to undefined function… error

permission to access the database. This

isn’t normally a PHP issue. Confirm the

Such an error message means you’re

values that are being used, and attempt to

attempting to use a function that PHP

connect to the database using a different

doesn’t have. This problem can be caused

interface (such as the MySQL client).

by a misspelling of a function name, failure

continues on next page

**A** Errors complaining about undefined variables or indexes often come from spelling or capitalization mistakes.

**B** Some functions create headers already sent errors if

called at the wrong time.

Resources and Next Steps 441

![Image 532](index-463_1.png)

![Image 533](index-463_2.png)

**7.** Supplied argument is not a valid

**9.** Conditionals or loops behave

MySQL result resource error

unpredictably

This is another database-related error

These logical errors are quite common.

message. The message means that a

Check that you haven’t used the wrong

query result is being used inappropriately.

operator (such as **\=** instead of **\==**) and

Most frequently, this is because you’re

that you refer to the proper variables.

trying to fetch rows from a query that

Then use **print** statements to let you

didn’t return any records. To solve this

know what the script is doing.

problem, print out the query being run

**10.** Parse errors **D**

and test it using another tool (such as

Parse errors are the most ubiquitous

the MySQL client or phpMyAdmin). Also

problems you’ll deal with. Even the

check that you’ve been consistent with

most seasoned PHP programmer

your variable names.

sees them occasionally. Check that

**8.** Preset HTML form values are cut off

every statement concludes with a

You must put the value attribute of

semicolon and that all quotation marks,

an HTML form input within double

parentheses, square braces, and curly

quotation marks. If you fail to do so,

brackets are evenly paired. If you still

only the part of the value up to the first

can’t find the parse error, comment out

space will be set as that input’s value.

large sections of the script using the **/\***

and **\*/** characters. Uncomment a section

at a time until you see the parse error

again. Then you’ll know where in the

script the problem is (or most likely is).

**C** If the MySQL access information is incorrect, you’ll see a message saying that database access has been denied.

**D** Parse errors are all too common and prevent scripts from executing.

442 Appendix

B

PHP 5 Advanced: Visual QuickPro Guide

**Next Steps**

(Peachpit Press, 2007). I dedicate around 150

This book will get you started using PHP,

pages of that book just to OOP (and there

but there are a few topics that you may

are still aspects of OOP that I didn’t get to)!

want to investigate further.

**Frameworks**

**Security**

A framework is an established library

Web servers, operating systems,

of code that you can use to develop

databases, and PHP security are all topics

sophisticated Web applications. By reusing

that merit their own books. Although this

someone else’s proven code, you can

book demonstrates writing secure Web

quickly build parts or all of a Web site.

applications, there’s always room for you to

There are many PHP frameworks available,

learn more in this area. Start by checking

starting with PEAR. The PEAR library is an

out these sites:

immense repository of PHP code, written

■

A S[tudy in Scarlet (www.securereality.](http://www.securereality.com.au/studyinscarlet.txt)

using objects (classes, technically). Even

[com.au/studyinscarlet.txt)](http://www.securereality.com.au/studyinscarlet.txt)

if you don’t use objects yourself or you

barely understand the concept, you can

■

W3C Security R[esources (www.w3.org/](http://www.w3.org/Security/)

still get a lot of value out of the PEAR

[Security/)](http://www.w3.org/Security/)

W[eb site (http://pear.php.net). PEAR and](http://pear.php.net)

The first is an article about writing secure

its Web site provide free, wonderful code

PHP code. The second is the World Wide

and demonstrate good PHP coding style.

Web Consortium’s resources page for

[PECL (http://pecl.php.net) is PEAR’](http://pecl.php.net)s more Web-related security issues.

powerful sibling.

You should also read the relevant sections

Another framework to consider is the Zend

of the PHP manual and the manual for

[Framework (http://framework.zend.com).](http://framework.zend.com)

the database you’re using. Searching the

This framework was created by some of

Internet for PHP and security will turn up

the key people behind PHP and is well

many interesting articles as well.

documented.

My personal favorite PHP framework, as of

**Object-oriented programming**

[this writing, is Yii (www.yiiframework.com).](http://www.yiiframework.com)

I write about Yii extensively on my site.

The subject of objects and object-oriented

programming (OOP) is not covered in this

Many people love frameworks and

book for two reasons:

what they offer. On the other hand, it

does take some time to learn how to

**1.** It’s well beyond the scope of a begin-

use a framework, and customizing the

ner’s guide.

framework’s behavior can be daunting.

**2.** You won’t be restricted as to what you can

do in PHP by not understanding objects.

**JavaScript and Ajax**

When you decide you want to learn the

JavaScript is a client-side technology that

subject, you can search the PHP sites for

runs in the Web browser. It can be used to

tutorials, check out a framework (see the

add various dynamic features to a Web site,

next section of the appendix), or read my

from simple eye candy like image rollovers

Resources and Next Steps 443

to interactive menus and forms. Because

some overlap in content, particularly in

it runs within the Web browser, JavaScript

the early chapters, but the examples are

provides some functionality that PHP cannot.

different and it goes at a faster pace.

And, like PHP, JavaScript is relatively easy to

MySQL and SQL in particular get a lot more

learn and use. For more, see:

coverage, and there are three different

example chapters: a multilingual forum, a

■

JavaScript. [com (www.javascript.com)](http://www.javascript.com)

user registration and login system, and an

■

W3School’s JavaScript pages

e-commerce setup.

[(www.w3schools.com/js/)](http://www.w3schools.com/js/)

My PHP 5 Advanced: Visual QuickPro

Ajax (which either means Asynchronous

Guide (Peachpit Press, 2007) is kind of

JavaScript and XML or doesn’t, depending

a sequel to the PHP and MySQL book

on whom you ask) has been all the rage

just mentioned. This book is much more

in the Web development community

advanced, spending a lot of time on topics

since around 2005. This technology uses

such as OOP and PEAR. It’s not intended

JavaScript to communicate with the server

to be read as linearly as this one, but rather

without the user knowing it. The net effect

each chapter focuses on a specific topic.

is a Web site that behaves more like a

MySQL: Visual QuickStart Guide, Second

desktop application. For more, see Ajaxian

Edition (Peachpit Press, 2006) looks

[(www.ajaxian.com) or search online](http://www.ajaxian.com).

almost exclusively at just MySQL and SQL.

I highly recommend you consider learning

Although there are four chapters covering

[jQuery (www.jquery.com) to help you](http://www.jquery.com)

languages used to interact with MySQL—

with your JavaScript, Ajax, and other

PHP, Perl, and Java, plus a techniques

dynamic Web needs. jQuery is a JavaScript

chapter—this book largely addresses

framework that’s easy to use, powerful,

things like installation, administration, and

and pretty well documented.

maximizing your MySQL knowledge.

My newest book (written just before the

**Other books**

one you’re reading now) is Effortless

It is my hope that after reading this book

E-Commerce with PHP and MySQL

you’ll be interested in learning more about

(New Riders, 2011). The book covers

PHP and Web development in general.

everything you need to know to create

While I could recommend books by other

fully functioning e-commerce sites. The

writers, there’s an inherent conflict there and

book uses two specific examples for doing

my opinion as a rival writer would not be the

so, and incorporates two different payment

same as yours as a reader. So, instead, I’ll

systems. Complete comfort with PHP and

just quickly highlight a couple of my other

MySQL is assumed, however.

books and how they compare to this one.

Finally, my Building a Web Site with Ajax:

The PHP 6 and MySQL 5 for Dynamic

Visual QuickProject Guide (Peachpit

Web Sites: Visual QuickPro Guide

Press, 2008) walks through the process

(Peachpit Press, 2008) is kind of a sequel

of coding an Ajax-enabled Web site. It

to this one (a new edition, tentatively titled

also uses PHP and MySQL, but those

PHP and MySQL for Dynamic Web Sites:

technologies aren’t taught in the same way

Visual QuickPro Guide, Fourth Edition,

that JavaScript and Ajax are.

should be published in 2011). There is

444 Appendix

B

**Tables**

**TABLE B.2 PHP’s Operators**

This book has a handful of tables scattered

**Operator**

**Usage**

**Type**

about, the three most important of which

**+**

Addition

Arithmetic

are reprinted here as a convenient

**\-**

Subtraction

Arithmetic

reference. You’ll also find one new table

**\***

that lists operator precedence **(Table B.1**).

Multiplication

Arithmetic

This partial list goes from highest to

**/**

Division

Arithmetic

lowest (for example, multiplication takes

**%**

Modulus

Arithmetic

precedence over addition).

(remainder

of a division)

**Table B.2** lists PHP’s main operators and

\+ +

Incrementation

Arithmetic

their types. It’s most important to remember

\--

Decrementation

Arithmetic

that a single equals sign (**\=**) assigns a value

to a variable, whereas two equals signs (**\==**)

**\=**

Assigns a value

Assignment

to a variable

are used together to check for equality.

**\==**

Equality

Comparison

**Table B.3** indicates the modes you can use

**!=**

Inequality

Comparison

when opening a file. Which you choose

determines what PHP can do with that

**<**

Less than

Comparison

file—write to it, read from it, and so forth.

**\>**

Greater than

Comparison

The various formats for the **date()** function

**<=**

Less than or

Comparison

equal to

may be one of the hardest things to

remember. Keep **Table B.4** nearby when

**\>=**

Greater than or

Comparison

equal to

you’re using the **date()** function.

**!**

Negation

Logical

**AND**

And

Logical

**&&**

And

Logical

**TABLE B.1 Operator Precedence**

**OR**

Or

Logical

**! ++ --**

**||**

Or

Logical

**\* / %**

**.**

Concatenation

String

**\+ - .**

XOR

Or not

Logical

**< <= > >=**

**.=**

**\== != ===**

Concatenates

Combined

to the value

concatenation

**&&**

of a variable

and assignment

**||**

**+=**

Adds to the

Combined

**\= + = -= \*= /= .= %=**

value of a

arithmetic and

variable

assignment

**and**

**\-=**

Subtracts from

Combined

**xor**

the value of a

arithmetic and

**or**

variable

assignment

Resources and Next Steps 445

**TABLE B.3 fopen( ) Modes**

**Mode**

**Meaning**

**r**

Read only; begin reading at the start of the file.

**r+**

Read or write; begin at the start of the file.

**w**

Write only; create the file if it doesn’t exist, and overwrite any existing contents.

**w+**

Read or write; create the file if it doesn’t exist, and overwrite any existing contents (when writing).

**a**

Write only; create the file if it doesn’t exist, and append the new data to the end of the file (retain any existing data and add to it).

**a+**

Read or write; create the file if it doesn’t exist, and append the new data to the end of the file (when writing).

**x**

Write only; create the file if it doesn’t exist, but do nothing (and issue a warning) if the file does exist.

**x+**

Read or write; create the file if it doesn’t exist, but do nothing (and issue a warning) if the file already exists (when writing).

**TABLE B.4 Date( ) Function Formatting**

**TABLE B.4** continued

**Character**

**Meaning**

**Example**

**Character**

**Meaning**

**Example**

Y

Year as 4 digits

2011

S

English ordinal

rd

suffix for a day,

y

Year as 2 digits

11

as 2 characters

L

Is it a leap year?

1 (for yes)

g

Hour; 12-hour

6

n

Month as

2

format as

1 or 2 digits

1 or 2 digits

m

Month as

02

G

Hour; 24-hour

18

2 digits

format as

1 or 2 digits

F

Month

February

h

Hour; 12-hour

06

M

Month as

Feb

format as 2 digits

3 letters

H

Hour; 24-hour

18

j

Day of the

8

format as 2 digits

month as

1 or 2 digits

i

Minutes

45

d

Day of the month

08

s

Seconds

18

as 2 digits

u

Microseconds

1234

l (lowercase L)

Day of the week

Monday

a

am or pm

am

D

Day of the week

Mon

A

AM or PM

PM

as 3 letters

U

Seconds since

1048623008

w

Day of the week

0 (Sunday)

the epoch

as a single digit

e

Timezone

UTC

z

Day of the year:

189

0 to 365

I (capital i )

Is it daylight

1 (for yes)

savings?

t

Number of days

31

in the month

O

Difference from GMT

+0600

446 Appendix

B

[Index](#index_split_000.html#p9)

**Symbols**

**<=** operator[, 129](#index_split_003.html#p150)

**\==**

**..**

operator[, 129](#index_split_003.html#p150)

[, using with directories, 293](#index_split_006.html#p314)

**\=**

**\\\\**

operator[, 129](#index_split_003.html#p150)

[, using with absolute paths, 320](#index_split_006.html#p341)

**\-=**

**'**

operator[, 87](#index_split_002.html#p108)

[(apostrophe), in MySQL, 358, 360](#index_split_007.html#p379)

**\>**

**@**

operator[, 129](#index_split_003.html#p150)

[(at symbol), using in MySQL, 342](#index_split_006.html#p363)

**\>=**

**\\**

operator[, 129](#index_split_003.html#p150)

[(backslash), using with strings, 39](#index_split_001.html#p60)

**<!-- -->** [comment characters, 27](#index_split_001.html#p48)

**#** [(comments), using with scripts, 25, 27](#index_split_001.html#p46)

**A**

**//** (comments), using with scripts [, 25, 27](#index_split_001.html#p46)

**abs()**[math function, 89](#index_split_002.html#p110)

**/\* \*/** [(comments), using with scripts, 25, 27](#index_split_001.html#p46)

absolute paths

**{}** [(curly brackets), using with array values, 163](#index_split_003.html#p184)

[creating on Windows servers, 319](#index_split_006.html#p340)

**$** [(dollar sign), preceding variables with, 36](#index_split_001.html#p57)

start of[, 293](#index_split_006.html#p314)

[$ (dollar sign), printing, 79](#index_split_002.html#p100)

[using with external files, 194](#index_split_004.html#p215)

**()** (parentheses)

**action** attribute, including in **form** [tag, 50, 53](#index_split_001.html#p71)

[using in calculations, 84–85](#index_split_002.html#p105)

**add\_entry.php** script

[using in conditionals, 125](#index_split_003.html#p146)

[creating, 353](#index_split_007.html#p374)

**"** (double quotation marks)

[saving, 357](#index_split_007.html#p378)

error caused by[, 22](#index_split_000.html#p43)

[securing query data, 359–360](#index_split_007.html#p380)

[using with strings, 39](#index_split_001.html#p60)

**add\_quote.php** script

[using with variables, 45–47](#index_split_001.html#p66)

[creating, 296](#index_split_006.html#p317)

**\\n** [(newline character), using with HTML, 23](#index_split_000.html#p44)

[file locks, 302](#index_split_006.html#p323)

**;** [(semicolon), using in MySQL, 358](#index_split_007.html#p379)

for sample site[, 393–396](#index_split_007.html#p414)

**'** (single quotation marks)

[saving, 300](#index_split_006.html#p321)

[using with arrays, 160](#index_split_003.html#p181)

addition (**+**) operator[, using, 77–80](#index_split_002.html#p98)[, 129](#index_split_002.html#p101)

[using with strings, 39](#index_split_001.html#p60)

[Ajax resources, 443–444](#index_split_008.html#p464)

[using with variables, 45–47](#index_split_001.html#p66)

**ALTER** [command in SQL, 334](#index_split_006.html#p355)

**\_** [(underscore), using with variables, 36](#index_split_001.html#p57)

**AND** operator[, 129, 133–134](#index_split_003.html#p150)

**−** operator[, using, 77–80](#index_split_002.html#p98)[, 129](#index_split_002.html#p101)

Apache Web site[, 10](#index_split_000.html#p31)

**\--** operator[, 129](#index_split_003.html#p150)

apostrophe (**'** [), in MySQL, 358, 360](#index_split_007.html#p379)

**!** operator[, 129, 133](#index_split_003.html#p150)

arguments. See also PHP functions

**!= =** operator[, 129](#index_split_003.html#p150)

error[, 266](#index_split_005.html#p287)

**!=** operator[, 130](#index_split_003.html#p151)

[using with functions, 265–270](#index_split_005.html#p286)

**%** operator[, 129](#index_split_003.html#p150)

arithmetic

**&&** operator[, 129, 133](#index_split_003.html#p150)

[assignment operators, 87, 129](#index_split_002.html#p108)

**\*** operator[, 77–80](#index_split_002.html#p98)[, 129](#index_split_002.html#p101)

[performing, 77–80](#index_split_002.html#p98)

**\*=** operator[, 87](#index_split_002.html#p108)

**array()** [calls, nesting, 167](#index_split_003.html#p188)

**.** operator[, 129](#index_split_003.html#p150)

array elements

**/** operator[, 77–80](#index_split_002.html#p98)[, 129](#index_split_002.html#p101)

[accessing, 161–163, 167](#index_split_003.html#p182)

**/=** operator[, 87](#index_split_002.html#p108)

[deleting, 158](#index_split_003.html#p179)

**|** operator[, 129](#index_split_003.html#p150)

pointing to[, 164](#index_split_003.html#p185)

**||** operator[, 133](#index_split_003.html#p154)

referring to[, 157](#index_split_003.html#p178)

**+** operator[, 77–80](#index_split_002.html#p98)[, 129](#index_split_002.html#p101)

**array()** [function, 154–155, 157](#index_split_003.html#p175)

**++** operator[, 86–87](#index_split_002.html#p107)[, 129](#index_split_002.html#p108)

array indexes, using strings for[, 161](#index_split_003.html#p182)

**+=** operator[, 87](#index_split_002.html#p108)

[array syntax, using, 176–178](#index_split_004.html#p197)

**<** operator[, 129](#index_split_003.html#p150)

[array values, accessing, 163](#index_split_003.html#p184)

Index 447

[arrays, 40.](#index_split_001.html#p61) See also superglobals **C**

adding items to[, 158–160](#index_split_003.html#p179)

[calculations, using parentheses in, 84–85](#index_split_002.html#p105)

associative[, 40](#index_split_001.html#p61)

**calculator.html** script

for checkbo[x input names, 177](#index_split_004.html#p198)

[creating, 74–76](#index_split_002.html#p95)

[versus constants, 200](#index_split_004.html#p221)

[saving, 76](#index_split_002.html#p97)

contents of[, 152](#index_split_003.html#p173)

**calculator.php** script

[creating, 154–157](#index_split_003.html#p175)

function returning value[, 275–278](#index_split_005.html#p296)

[creating from forms, 176–181](#index_split_004.html#p197)

[saving, 278](#index_split_005.html#p299)

[deleting, 158](#index_split_003.html#p179)

variable scope[, 281–285](#index_split_006.html#p302)

examples of[, 153](#index_split_003.html#p174)

Cascading Style Sheets (CSS), adding to Web

grocery list example[, 152](#index_split_003.html#p173)

[pages, 3](#index_split_000.html#p24)

index[ed, 40, 157](#index_split_001.html#p61)

[case of strings, adjusting, 111](#index_split_002.html#p132)

[indexing, 154, 157](#index_split_003.html#p175)

**cell()**[math function, 89](#index_split_002.html#p110)

[merging, 160](#index_split_003.html#p181)

characters

[multidimensional, 164–167](#index_split_003.html#p185)

[counting in strings, 109](#index_split_002.html#p130)

overview[, 152](#index_split_003.html#p173)

[escaping, 59](#index_split_002.html#p80)

printing values of[, 162–163](#index_split_003.html#p183)

indexed positions of[, 108](#index_split_002.html#p129)

[sorting, 168–171](#index_split_004.html#p189)

check boxes

**$soups**[, 155](#index_split_003.html#p176)

[creating for form, 118](#index_split_003.html#p139)

[superglobals, 153](#index_split_003.html#p174)

presetting status of[, 216](#index_split_004.html#p237)

[syntactical rules, 153](#index_split_003.html#p174)

**checkdate()** [validation function, 128](#index_split_003.html#p149)

[using single quotation marks with, 160](#index_split_003.html#p181)

[code repositories, 438](#index_split_008.html#p459)

[arrays and strings, transforming between, 172–175](#index_split_004.html#p193)

comments

**arsort()**[function, 168, 170](#index_split_004.html#p189)

\# type of[, 25, 27](#index_split_001.html#p46)

**asort()**[function, 168–170](#index_split_004.html#p189)

// type of[, 25, 27](#index_split_001.html#p46)

[assignment versus comparison operators, 130](#index_split_003.html#p151)

/\* \*/ type of[, 25, 27](#index_split_001.html#p46)

at symbol (**@**[), using in MySQL, 342](#index_split_006.html#p363)

**<!-- -->** type of[, 27](#index_split_001.html#p48)

[attributes, identifying, 315](#index_split_006.html#p336)

[adding to scripts, 25–27](#index_split_001.html#p46)

comparison operators

**B**

[versus assignment operators, 130](#index_split_003.html#p151)

backslash (**\\**[), using with strings, 39](#index_split_001.html#p60)

[using, 129–132](#index_split_003.html#p150)

banners, creating for W[eb pages, 186](#index_split_004.html#p207)

[concatenating strings, 95–97](#index_split_002.html#p116)

BBEdit Web site[, 4](#index_split_000.html#p25)

concatenation

birth year, creating input for[, 117](#index_split_003.html#p138)

operator[, 129](#index_split_003.html#p150)

blank W[eb pages, debugging, 440–441](#index_split_008.html#p461)

[using with functions, 106](#index_split_002.html#p127)

blog entry

conditionals. See also **if** conditional

[adding, 355–358](#index_split_007.html#p376)

[debugging, 442](#index_split_008.html#p463)

[editing, 372–377](#index_split_007.html#p393)

**if-else**[, 126–127](#index_split_003.html#p147)

[retrieving data from, 362](#index_split_007.html#p383)

[nesting, 133](#index_split_003.html#p154)

[securing query data, 360](#index_split_007.html#p381)

[nesting for login form, 207](#index_split_004.html#p228)

**$books** array[, 164–165](#index_split_003.html#p185)

reverse[, 132](#index_split_003.html#p153)

**books.php** script

[using in functions, 125](#index_split_003.html#p146)

[creating, 165, 198](#index_split_003.html#p186)

[using parentheses in, 125](#index_split_003.html#p146)

[saving, 199](#index_split_004.html#p220)

conditions, TRUE versus F[ALSE, 133](#index_split_003.html#p154)

**<br />** tag

[configuration changes, confirming, 424](#index_split_008.html#p445)

[using for newlines, 98–99](#index_split_002.html#p119)

constants

[using in XHTML pages, 6](#index_split_000.html#p27)

[versus arrays, 200](#index_split_004.html#p221)

**break**[, language construct, 144](#index_split_003.html#p165)

benefits of[, 285](#index_split_006.html#p306)

breaks, converting newlines to[, 98–99](#index_split_002.html#p119)[, 102](#index_split_002.html#p120)

global scope of[, 200](#index_split_004.html#p221)

browser

[naming, 200](#index_split_004.html#p221)

sending **Hello,** **world!** greeting to[, 16–17](#index_split_000.html#p37)

[predefined, 200](#index_split_004.html#p221)

sending HTML to[, 22–24](#index_split_000.html#p43)

[printing, 199–200](#index_split_004.html#p220)

sending text to[, 15–17](#index_split_000.html#p36)

using in W[eb applications, 197–200](#index_split_004.html#p218)

[testing scripts in, 12–14](#index_split_000.html#p33)

control structures. See also loops

buffer size, setting maximum for[, 224](#index_split_005.html#p245)

**else**[, 126–128](#index_split_003.html#p147)

buttons. See radio buttons; submit button

**elseif**[, 138–141](#index_split_003.html#p159)

**foreach** loop[, 146, 162–163](#index_split_003.html#p167)

HTML form for[, 116–118](#index_split_002.html#p137)

448 Index

**if** [conditional, 119–121, 124](#index_split_003.html#p140)

databases. See also sample site

**for** loop[, 146–149](#index_split_003.html#p167)[, 163](#index_split_003.html#p170)

connecting to[, 382](#index_split_007.html#p403)

**switch** [conditional, 142–145](#index_split_003.html#p163)

[creating, 343–346](#index_split_006.html#p364)

**while** loop[, 146, 149](#index_split_003.html#p167)

[defined, 334](#index_split_006.html#p355)

cookies

[deleting data in, 366–371](#index_split_007.html#p387)

adding **expiration** arguments to[, 242–244](#index_split_005.html#p263)

[editing records in, 373–374](#index_split_007.html#p394)

adding parameters to[, 242–243](#index_split_005.html#p263)

**id** primary key, [377](#index_split_007.html#p398)

[creating, 234–238](#index_split_005.html#p255)

**INSERT INTO** [command, 352](#index_split_007.html#p373)

[debugging, 233](#index_split_005.html#p254)

inserting data into[, 352–357](#index_split_007.html#p373)

[deleting, 245–247](#index_split_005.html#p266)

permissions for[, 343](#index_split_006.html#p364)

features of[, 234](#index_split_005.html#p255)

[queries, 352](#index_split_007.html#p373)

[output buffering, 238](#index_split_005.html#p259)

[retrieving data from, 361–365](#index_split_007.html#p382)

overview[, 232–233](#index_split_005.html#p253)

[securing query data, 358–360](#index_split_007.html#p379)

[reading from, 239–241](#index_split_005.html#p260)

[selecting, 343–346](#index_split_006.html#p364)

in sample site[, 383](#index_split_007.html#p404)

[updating data in, 372–377](#index_split_007.html#p393)

***secure*** value[, 243](#index_split_005.html#p264)

**date()** [function, 201–203, 295, 446](#index_split_004.html#p222)

[sending, 235–238](#index_split_005.html#p256)

day of month, drop-down menu for[, 147–148](#index_split_003.html#p168)

[versus sessions, 248](#index_split_005.html#p269)

[day pull-down menu, creating, 262](#index_split_005.html#p283)

testing compatibility[, 247](#index_split_005.html#p268)

**$dbc** reference

[cost, calculating, 79](#index_split_002.html#p100)

[explained, 361](#index_split_007.html#p382)

**count()** [function, 160](#index_split_003.html#p181)

[setting, 364](#index_split_007.html#p385)

**CREATE** [command in SQL, 334](#index_split_006.html#p355)

[DBMS (database management system), 335](#index_split_006.html#p356)

**create\_table.php** script

debugging

[beginning, 348](#index_split_007.html#p369)

[cookies, 233](#index_split_005.html#p254)

[saving, 351](#index_split_007.html#p372)

FA[Qs (frequently asked questions), 440–442](#index_split_008.html#p461)

Crimson Editor Web site[, 4](#index_split_000.html#p25)

[PHP scripts, 28–29](#index_split_001.html#p49)[, 63](#index_split_001.html#p50)

[cross-site scripting (XSS) attacks, 100](#index_split_002.html#p121)

[variables without values, 441](#index_split_008.html#p462)

CRUD[, explained, 396](#index_split_007.html#p417)

decrementation operator[, 129](#index_split_003.html#p150)

**crypt()** [function, using with strings, 106](#index_split_002.html#p127)

**default** case, adding to **switch** [conditional, 145](#index_split_003.html#p166)

CSS (Cascading Style Sheets), adding to

**DELETE** [queries, 334](#index_split_006.html#p355)

W[eb pages, 3](#index_split_000.html#p24)

error related to[, 371](#index_split_007.html#p392)

CSS code[, adding to layout model, 185](#index_split_004.html#p206)

[using in MySQL, 366–371](#index_split_007.html#p387)

[CSS templates, 191.](#index_split_004.html#p212) See also templates

**delete\_entry.php** script

curly brackets ( **{}**) , [using with array values, 163](#index_split_003.html#p184)

[creating, 367](#index_split_007.html#p388)

**customize.php** script

[saving, 371](#index_split_007.html#p392)

[creating for cookies, 235](#index_split_005.html#p256)

**delete\_quote.php** script

expiration date[, 243–244](#index_split_005.html#p264)

[creating, 406](#index_split_008.html#p427)

[saving, 238](#index_split_005.html#p259)

[saving, 409](#index_split_008.html#p430)

deleting

**D**

[arrays, 158](#index_split_003.html#p179)

[cookies, 245–247](#index_split_005.html#p266)

database code, placement of[, 351](#index_split_007.html#p372)

[data in databases, 366–371](#index_split_007.html#p387)

[database information, setting, 346](#index_split_007.html#p367)

[directories, 326](#index_split_006.html#p347)

[database management system (DBMS), 335](#index_split_006.html#p356)

[files, 314](#index_split_006.html#p335)

database records

[sessions, 254–255](#index_split_005.html#p275)

CRUD[, 396](#index_split_007.html#p417)

[deprecated functions, listing in PHP manual, 21](#index_split_000.html#p42)

[editing in databases, 373–374](#index_split_007.html#p394)

**die()**[, calling in MySQL, 342](#index_split_006.html#p363)

[inserting via MySQL, 357](#index_split_007.html#p378)

**die**[, language construct, 144](#index_split_003.html#p165)

[paginating returned, 365](#index_split_007.html#p386)

directories

[database resources, 439](#index_split_008.html#p460)

[deleting, 326](#index_split_006.html#p347)

database tables

finding contents of[, 315](#index_split_006.html#p336)

[columns in, 347](#index_split_007.html#p368)

finding parts of[, 319](#index_split_006.html#p340)

[creating, 347–351](#index_split_007.html#p368)

[navigating, 315–319](#index_split_006.html#p336)

creating for sample site[, 380–381](#index_split_007.html#p401)

[parent folders, 293](#index_split_006.html#p314)

[emptying of records, 371](#index_split_007.html#p392)

permissions for[, 320](#index_split_006.html#p341)

entries example[, 347](#index_split_007.html#p368)

referring to[, 293](#index_split_006.html#p314)

[primary keys, 347](#index_split_007.html#p368)

[saving, 320–326](#index_split_006.html#p341)

[using commas in, 347](#index_split_007.html#p368)

**scandir()** [function, 315](#index_split_006.html#p336)

[searching files in, 319](#index_split_006.html#p340)

Index 449

[directory control panel, creating, 316–319](#index_split_006.html#p337)

Call to undefined function... [, 441](#index_split_008.html#p462)

**display\_errors** setting. See also errors

[database queries, 350](#index_split_007.html#p371)

[enabling for debugging scripts, 63](#index_split_002.html#p84)

**DELETE** [queries, 371](#index_split_007.html#p392)

[turning on, 29, 62](#index_split_001.html#p50)

[displaying in scripts, 61–63](#index_split_002.html#p82)

[viewing, 61](#index_split_002.html#p82)

[file permissions, 300](#index_split_006.html#p321)

division ( **/** ) operator[, using, 77–80](#index_split_002.html#p98)[, 129](#index_split_002.html#p101)

**$FILES** variable[, 308](#index_split_006.html#p329)

[documents, creating for XHTML pages, 4](#index_split_000.html#p25)

Headers already sent[, 441](#index_split_008.html#p462)

dollar sign (**$**[), preceding variables with, 36](#index_split_001.html#p57)

[parsing, 442](#index_split_008.html#p463)

[dollar sign ($), printing, 79](#index_split_002.html#p100)

related to **foreach** loop[, 181](#index_split_004.html#p202)

double quotation marks ( **"** )

[related to functions, 264](#index_split_005.html#p285)

error caused by[, 22](#index_split_000.html#p43)

related to **header()** [call, 222](#index_split_005.html#p243)

[using with strings, 39](#index_split_001.html#p60)

Supplied argument is not valid MySQL result

[using with variables, 45–47](#index_split_001.html#p66)

resource[, 442](#index_split_008.html#p463)

Dreamweaver Web site[, 4](#index_split_000.html#p25)

Undefined index[, 441](#index_split_008.html#p462)

**DROP** [command in SQL, 334](#index_split_006.html#p355)

Undefined variable[, 44](#index_split_001.html#p65)

drop-down menu. See also menu

Undefined variable[, 441](#index_split_008.html#p462)

[creating for form, 118](#index_split_003.html#p139)

[escape sequences, using with files, 293](#index_split_006.html#p314)

[for day of month, 147–148](#index_split_003.html#p168)

[escaping characters, 59](#index_split_002.html#p80)

[selecting options from, 181](#index_split_004.html#p202)

**event.html** script

[creating, 177](#index_split_004.html#p198)

**E**

[saving, 178](#index_split_004.html#p199)

**event.php** script

**edit\_entry.php** script

[creating, 179–181](#index_split_004.html#p200)

[creating, 373](#index_split_007.html#p394)

[saving, 181](#index_split_004.html#p202)

[saving, 376](#index_split_007.html#p397)

**exit()**, alias for[, 342](#index_split_006.html#p363)

**edit\_quote.php** script

**exit**[, language construct, 144](#index_split_003.html#p165)

[creating, 400](#index_split_007.html#p421)

**explode()** [function, 172, 174](#index_split_004.html#p193)

[saving, 405](#index_split_007.html#p426)

[extensions, explained, 9](#index_split_000.html#p30)

EditPlus Web site[, 4](#index_split_000.html#p25)

external files

**else** [conditional, 126–128](#index_split_003.html#p147)

[placing error settings in, 196](#index_split_004.html#p217)

**elseif** [conditional, 138–141](#index_split_003.html#p159)

using with W[eb applications, 192–196](#index_split_004.html#p213)

[email, sending, 217–221](#index_split_004.html#p238)

writing to[, 296–300](#index_split_006.html#p317)

email address

adding text input for[, 52](#index_split_001.html#p73)

[adding to HTML form, 93](#index_split_002.html#p114)

**F**

creating inputs for[, 117](#index_split_003.html#p138)

F[ALSE versus TRUE conditionals, 133, 137](#index_split_003.html#p154)

email body[, creating lines in, 221](#index_split_005.html#p242)

FA[Qs (frequently asked questions), 440–442](#index_split_008.html#p461)

**empty()** [validation function, 122–123](#index_split_003.html#p143)

**fclose()** [function, 295, 302](#index_split_006.html#p316)

[encoding, selecting, 5](#index_split_000.html#p26)

**feedback.html** script

equality operator[, 129](#index_split_003.html#p150)

adding **method** attribute to[, 55–56](#index_split_001.html#p76)

error handling

[creating, 51](#index_split_001.html#p72)

[applying to PHP scripts, 70](#index_split_002.html#p91)

[saving, 53](#index_split_001.html#p74)

in **handle\_calc.php** [document, 78](#index_split_002.html#p99)

[using with HTML forms, 60](#index_split_002.html#p81)

error messages

**fgetcsv()** [function, 331](#index_split_006.html#p352)

for sample site[, 390](#index_split_007.html#p411)

**fgets()** [function, 327](#index_split_006.html#p348)

[trusting, 440](#index_split_008.html#p461)

file access, returning time of[, 319](#index_split_006.html#p340)

error reporting. See also **display\_errors** setting

**file()** [function, 304](#index_split_006.html#p325)

adjusting level of[, 65–66](#index_split_002.html#p86)

[file navigation, 194](#index_split_004.html#p215)

[constants, 64](#index_split_002.html#p85)

file owner[, returning, 319](#index_split_006.html#p340)

[error settings, placing in external files, 196](#index_split_004.html#p217)

[file paths, 293, 319](#index_split_006.html#p314)

Error type[, 64](#index_split_002.html#p85)

file permissions

error types

[versus database permissions, 343](#index_split_006.html#p364)

Error[, 64](#index_split_002.html#p85)

[for directories, 320](#index_split_006.html#p341)

Notice[, 64](#index_split_002.html#p85)

error[, 300](#index_split_006.html#p321)

Parse error[, 64](#index_split_002.html#p85)

overview[, 288–289](#index_split_006.html#p309)

W[arning, 64](#index_split_002.html#p85)

**quotes.txt** file[, 289–290](#index_split_006.html#p310)

[error-handling techniques, 340](#index_split_006.html#p361)

[returning, 319](#index_split_006.html#p340)

errors. See also **display\_errors** setting

[setting, 291–292](#index_split_006.html#p312)

Access denied[, 441](#index_split_008.html#p462)

File T[ransfer Protocol (FTP), using, 10–11](#index_split_000.html#p31)

“Call to undefined function, [” 264](#index_split_005.html#p285)

450 Index

file uploads

functions. See also PHP functions;

configuring PHP for[, 307](#index_split_006.html#p328)

user-defined functions

**file** [tag, 307](#index_split_006.html#p328)

[calling, 17](#index_split_000.html#p38)

**$FILES** variable[, 308](#index_split_006.html#p329)

[deprecated, 21](#index_split_000.html#p42)

**form** [tag, 307](#index_split_006.html#p328)

[looking up in PHP manual, 18](#index_split_000.html#p39)

hidden input type[, 307](#index_split_006.html#p328)

**functions.php** script, creating for sample

using PHP for[, 310–314](#index_split_006.html#p331)

site[, 384–385](#index_split_007.html#p405)

writable directory[, 309](#index_split_006.html#p330)

**fwrite()** [function, 295](#index_split_006.html#p316)

**file\_get\_contents()** [function, 304](#index_split_006.html#p325)

**file\_put\_contents()** [function, 293–294](#index_split_006.html#p314)

**G**

files

copying on server[, 314](#index_split_006.html#p335)

[garbage collection, 255](#index_split_005.html#p276)

[deleting, 314](#index_split_006.html#p335)

GET method

[locking, 301–303](#index_split_006.html#p322)

[using with HTML forms, 54–56](#index_split_001.html#p75)

modification times of[, 315](#index_split_006.html#p336)

using with **welcome.php** page[, 229](#index_split_005.html#p250)

[opening, 294](#index_split_006.html#p315)

**$\_GET** predefined variable[, 57](#index_split_001.html#p78)

[reading from, 303–306](#index_split_006.html#p324)

**getrandmax()**[math function, 89](#index_split_002.html#p110)

reading incrementally[, 327–331](#index_split_006.html#p348)

**glob()** [function, 319](#index_split_006.html#p340)

writing to[, 293–300](#index_split_006.html#p314)

**global** statement, using with variable

**$FILES** variable

scope[, 279–285](#index_split_006.html#p300)

elements of[, 308](#index_split_006.html#p329)

**$grades** array[, 169, 171](#index_split_004.html#p190)

[error codes, 308](#index_split_006.html#p329)

**GRANT** [command, using in MySQL, 434–435](#index_split_008.html#p455)

[FileZilla, using to upload scripts, 10–11](#index_split_000.html#p31)

greater than operator[, 129](#index_split_003.html#p150)

Firebug extension for Firefo[x, 233, 238](#index_split_005.html#p254)

greater than or equal to operator[, 129](#index_split_003.html#p150)

[firewalls, using, 416](#index_split_008.html#p437)

[greetings, creating in PHP scripts, 70–71](#index_split_002.html#p91)

first name[, adding to HTML form, 93](#index_split_002.html#p114)

**$groceries** array[, 164](#index_split_003.html#p185)

***flag*** variable

[creating for sticky form, 213](#index_split_004.html#p234)

**H**

[using with if conditional, 120–121](#index_split_003.html#p141)

**handle\_calc.php** script

[floating-point numbers and integers, 38](#index_split_001.html#p59)

[creating, 77](#index_split_002.html#p98)

**flock()** [lock types, 301–303](#index_split_006.html#p322)

precedence example[, 85–87](#index_split_002.html#p106)

**floor()**[math function, 89](#index_split_002.html#p110)

[saving, 79, 83](#index_split_002.html#p100)

footer file, creating for W[eb pages, 190–191](#index_split_004.html#p211)

[using to format numbers, 82–83](#index_split_002.html#p103)

**footer.html** script

**handle\_form.php** script

for sample site[, 386–387](#index_split_007.html#p407)

[adjusting error reporting in, 65–66](#index_split_002.html#p86)

[saving, 190](#index_split_004.html#p211)

[creating, 58](#index_split_002.html#p79)

**fopen()** [modes, 294, 446](#index_split_006.html#p315)

[displaying errors in, 62–63](#index_split_002.html#p83)

**for** loop. See also loops

[saving, 59, 62](#index_split_002.html#p80)

ex[ecuting, 146–147](#index_split_003.html#p167)

[slashes displayed in, 60](#index_split_002.html#p81)

[variables in, 149](#index_split_003.html#p170)

**handle\_post.php** script

[writing, 147–149](#index_split_003.html#p168)

[creating, 96](#index_split_002.html#p117)

**foreach** loop[, 146](#index_split_003.html#p167)

[functions in, 101–102](#index_split_002.html#p122)

error related to[, 181](#index_split_004.html#p202)

[saving, 97, 99](#index_split_002.html#p118)

[using to access array elements, 162–163](#index_split_003.html#p183)

string variables sent to[, 95](#index_split_002.html#p116)

[form inputs, quoting attributes in, 216](#index_split_004.html#p237)

substring example[, 109](#index_split_002.html#p130)

[form submission, determining, 204–205.](#index_split_004.html#p225) See also **urlencode()** example[, 103–105](#index_split_002.html#p124)

HTML forms

**handle\_reg.php** script

**form** [tags, 50](#index_split_001.html#p71)

[comparison operators examples, 130–132](#index_split_003.html#p151)

adding to **feedback.html** file[, 51–52](#index_split_001.html#p72)

[creating, 120](#index_split_003.html#p141)

for **calculator.html** [document, 75](#index_split_002.html#p96)

**else** control structure example[, 126–128](#index_split_003.html#p147)

creating for **register.html** [script, 117](#index_split_003.html#p138)

**elseif** example[, 139–141](#index_split_003.html#p160)

for **posting.html** [script, 92](#index_split_002.html#p113)

form validation example[, 123–125](#index_split_003.html#p144)

[frameworks resources, 443](#index_split_008.html#p464)

logical operators example[, 134–137](#index_split_003.html#p155)

frequently asked questions (FA[Qs), 440–442](#index_split_008.html#p461)

[saving, 121, 124](#index_split_003.html#p142)

FTP (File T[ransfer Protocol), using, 10–11](#index_split_000.html#p31)

**switch** conditional example[, 143–145](#index_split_003.html#p164)

[function calls, using spaces between, 83](#index_split_002.html#p104)

[hash, creating, 326](#index_split_006.html#p347)

function definitions, looking up[, 20–21](#index_split_000.html#p41)

header file, creating for W[eb pages, 188–189](#index_split_004.html#p209)

function design theory[, 285](#index_split_006.html#p306)

**header()** [function, 222, 225–229](#index_split_005.html#p243)

**function\_exists()** [function, 264](#index_split_005.html#p285)

Index 451

**header.html** script

[using with databases, 353–357](#index_split_007.html#p374)

**date()** [function, 202–203](#index_split_004.html#p223)

[viewing information in, 56](#index_split_001.html#p77)

[modifying, 199–200](#index_split_004.html#p220)

HTML pages

[output, 222](#index_split_005.html#p243)

[creating to receive data, 67–69](#index_split_002.html#p88)

[printing constants, 199–200](#index_split_004.html#p220)

[with input types, 51](#index_split_001.html#p72)

for sample site[, 385](#index_split_007.html#p406)

sending data to manually[, 67–71](#index_split_002.html#p88)

[saving, 199, 203](#index_split_004.html#p220)

[HTML syntax, 2–4](#index_split_000.html#p23)

**headers\_sent()** [function, 229](#index_split_005.html#p250)

[HTML tags, using PHP functions with, 100–101.](#index_split_002.html#p121)

Hello, world! greeting

See also PHP tags; tags

enhanced version of[, 23](#index_split_000.html#p44)

**html\_entity\_decode** [function, 102](#index_split_002.html#p123)

sending to browser[, 16–17](#index_split_000.html#p37)

**htmlspecialchars()** [function, 100, 102](#index_split_002.html#p121)

**hello2.php** script

[HTTP headers, manipulating, 225–226](#index_split_005.html#p246)

adding comments to[, 26](#index_split_001.html#p47)

HTML (HyperText Markup Language)

[saving, 23](#index_split_000.html#p44)

[outside of PHP tags, 24](#index_split_001.html#p45)

source code[, 24](#index_split_001.html#p45)

[versus PHP documents, 7](#index_split_000.html#p28)

**hello3.php** file[, saving, 26](#index_split_001.html#p47)

resource[, 6](#index_split_000.html#p27)

**hello.html** [script, creating, 68](#index_split_002.html#p89)

sending to browser[, 22–24](#index_split_000.html#p43)

**hello.php** file[, saving, 17](#index_split_000.html#p38)

[versus XHTML, 6](#index_split_000.html#p27)

**hello.php** script

[creating, 70](#index_split_002.html#p91)

**I**

versus **hello.html**[, 71](#index_split_002.html#p92)

running directly[, 71](#index_split_002.html#p92)

**id** primary key, [using in databases, 377](#index_split_007.html#p398)

[hidden input, using with HTML forms, 60](#index_split_002.html#p81)

**if** conditional. See also conditionals

home page, creating for sample site[, 410–413](#index_split_008.html#p431)

**\=** versus **\==** [operators in, 132](#index_split_003.html#p153)

HTML (HyperText Markup Language)

[creating, 119–121](#index_split_003.html#p140)

[outside of PHP tags, 24](#index_split_001.html#p45)

[for validating form data, 124](#index_split_003.html#p145)

[versus PHP documents, 7](#index_split_000.html#p28)

**if-else** [conditional, 126–127](#index_split_003.html#p147)[, 135](#index_split_003.html#p148)

resource[, 6](#index_split_000.html#p27)

**if-else** [statements, troubleshooting, 137](#index_split_003.html#p158)

sending to browser[, 22–24](#index_split_000.html#p43)

**if-elseif** [conditionals, simplifying, 142–144](#index_split_003.html#p163)

[versus XHTML, 6](#index_split_000.html#p27)

**if-elseif-else** [conditional, 138–141](#index_split_003.html#p159)

HTML code[, spacing, 23](#index_split_000.html#p44)

**implode()** [function, 172, 174](#index_split_004.html#p193)

HTML comments, location of[, 27](#index_split_001.html#p48)

**include()** [function, 192–193, 196](#index_split_004.html#p213)

**html entities()** [function, 100–102](#index_split_002.html#p121)

increment (**++**) operator[, using, 86–87](#index_split_002.html#p107)[, 129](#index_split_002.html#p108)

HTML form data

[incrementing numbers, 86–87](#index_split_002.html#p107)

[accessing, 60](#index_split_002.html#p81)

**index.php** script

receiving in PHP[, 57–60](#index_split_001.html#p78)

[creating, 193](#index_split_004.html#p214)

[validating, 120–121, 123–125](#index_split_003.html#p141)

running in browser[, 195](#index_split_004.html#p216)

HTML forms. See also form submission

for sample site[, 410–413](#index_split_008.html#p431)

adding menus to[, 52](#index_split_001.html#p73)

[saving, 194, 410–413](#index_split_004.html#p215)

adding radio buttons to[, 52](#index_split_001.html#p73)

inequality operator[, 129](#index_split_003.html#p150)

adding submit buttons to[, 53](#index_split_001.html#p74)

**ini\_set()** [function, using with scripts, 62](#index_split_002.html#p83)

[for control structures, 116–118](#index_split_002.html#p137)

**INSERT** [command in SQL, 334](#index_split_006.html#p355)

[creating, 50–53](#index_split_001.html#p71)

**INSERT INTO** command, using with

[creating arrays from, 176–181](#index_split_004.html#p197)

[queries, 352, 357](#index_split_007.html#p373)

[GET method, 54–56](#index_split_001.html#p75)

**INSERT** query[, using form data in, 355](#index_split_007.html#p376)

handling with PHP[, 204–209](#index_split_004.html#p225)

installation

[hidden input, 60](#index_split_002.html#p81)

[on Mac OS X, 419–422](#index_split_008.html#p440)

making sticky[, 210–216](#index_split_004.html#p231)

[on Windows, 415–418](#index_split_008.html#p436)

**method** attribute[, 54–56](#index_split_001.html#p75)

[integers and floating-point numbers, 38](#index_split_001.html#p59)

[for numbers, 74–76](#index_split_002.html#p95)

**is\_numeric()** [validation function, 123, 125](#index_split_003.html#p144)

POS[T method, 54–56](#index_split_001.html#p75)

**is\_readable()** [function, 306](#index_split_006.html#p327)

preset values cut off[, 442](#index_split_008.html#p463)

**is\_writable()** [function, 295](#index_split_006.html#p316)

[printing out user data from, 60](#index_split_002.html#p81)

**isset()** [validation function, 122–123, 125](#index_split_003.html#p143)

redisplaying immediately[, 209](#index_split_004.html#p230)

**select** [element, 52](#index_split_001.html#p73)

**J**

[for strings, 92–94](#index_split_002.html#p113)

[JavaScript resources, 443–444](#index_split_008.html#p464)

[for strings and arrays, 173–174](#index_split_004.html#p194)

**join()** [function, 174](#index_split_004.html#p195)

**textarea**[, 53](#index_split_001.html#p74)

452 Index

**K**

**make\_date\_menus()** [function, 263](#index_split_005.html#p284)

**make\_text\_input()** [function, 269](#index_split_005.html#p290)

[key-value pairs, using with arrays, 40](#index_split_001.html#p61)

**krsort()**

MAMP[, installing on Mac OS X, 420–422](#index_split_008.html#p441)

[function, 168](#index_split_004.html#p189)

**ksort()**

mathematical functions

[function, 168–171](#index_split_004.html#p189)

**abs()**[, 89](#index_split_002.html#p110)

**cell()**[, 89](#index_split_002.html#p110)

**L**

**floor()**[, 89](#index_split_002.html#p110)

language constructs

**getrandmax()**[, 89](#index_split_002.html#p110)

**break**[, 144](#index_split_003.html#p165)

**mt\_rand()**[, 89](#index_split_002.html#p110)

**die**[, 144](#index_split_003.html#p165)

**rand()**[, 89](#index_split_002.html#p110)

**exit**[, 144](#index_split_003.html#p165)

**round()**[, 89](#index_split_002.html#p110)

**print**[, 144](#index_split_003.html#p165)

[mathematical operators, 84–85, 87](#index_split_002.html#p105)[.](#index_split_002.html#p108)

last name[, adding to HTML form, 93](#index_split_002.html#p114)

See also operators

layout model, creating for W[eb pages, 185–187](#index_split_004.html#p206)

mathematics, principles of[, 77](#index_split_002.html#p98)

**layout.html** script, footer file[, 190–191](#index_split_004.html#p211)

**mcrypt\_encrypt()** [function, using with strings, 106](#index_split_002.html#p127)

less than operator[, 129](#index_split_003.html#p150)

**md5()** [function, 326](#index_split_006.html#p347)

less than or equal to operator[, 129](#index_split_003.html#p150)

[menu, adding to HTML form, 52.](#index_split_001.html#p73) See also

links

drop-down menu; pull-down menu

[creating to PHP scripts, 68–69](#index_split_002.html#p89)

menu variables, values of[, 60](#index_split_002.html#p81)

[using to send values to scripts, 71](#index_split_002.html#p92)

**menus.php** script

**list()** [function, 181](#index_split_004.html#p202)

[creating, 260](#index_split_005.html#p281)

[list of words, alphabetizing, 172](#index_split_004.html#p193)

[saving, 263](#index_split_005.html#p284)

**list\_dir.php** script

message, printing in browser[, 16](#index_split_000.html#p37)

[creating, 316–317](#index_split_006.html#p337)

**method** attribute[, using with HTML forms, 54–56](#index_split_001.html#p75)

[displaying, 315–319](#index_split_006.html#p336)

MIME type[, finding, 319](#index_split_006.html#p340)

[saving, 319](#index_split_006.html#p340)

**mkdir()** [command,, 320](#index_split_006.html#p341)

**list.html** script

modulus operator[, 129](#index_split_003.html#p150)

[creating, 173–174](#index_split_004.html#p194)

**money\_format()** [function, 83](#index_split_002.html#p104)

[saving, 174](#index_split_004.html#p195)

[month pull-down menu, creating, 260](#index_split_005.html#p281)

**list.php** script

[monthly payment, calculating, 79](#index_split_002.html#p100)

[creating, 174](#index_split_004.html#p195)

**move\_uploaded\_file()** [script, 310–311](#index_split_006.html#p331)

[saving, 175](#index_split_004.html#p196)

**mt\_rand()**[math function, 89](#index_split_002.html#p110)

[locking files, 301–303](#index_split_006.html#p322)

multidimensional arrays

**$loggedin** [flag, 330](#index_split_006.html#p351)

[using, 164–167](#index_split_003.html#p185)

[logical operators, using, 133–137](#index_split_003.html#p154)

[viewing, 167](#index_split_003.html#p188)

login form

multilingual page[, creating, 5](#index_split_000.html#p26)

[checking for hidden input, 209](#index_split_004.html#p230)

multiplication (**\***) operator[, using, 77–80](#index_split_002.html#p98)[, 129](#index_split_002.html#p101)

creating for Web page[, 205–209](#index_split_004.html#p226)

My Blog example. See blog entry

[login script, creating, 327–331](#index_split_006.html#p348)

My Site of Quotes, setting up[, 380](#index_split_007.html#p401)

**login.php** script

MySQL

[creating, 206, 328–329](#index_split_004.html#p227)

alias for **exit()**[, 342](#index_split_006.html#p363)

**header()** [function, 226](#index_split_005.html#p247)

[auto-incrementing primary keys, 357](#index_split_007.html#p378)

**$loggedin** [flag, 330](#index_split_006.html#p351)

calling **die()**[, 342](#index_split_006.html#p363)

for sample site[, 388–391](#index_split_007.html#p409)

connecting to[, 336–340](#index_split_006.html#p357)

[saving, 209, 331, 391](#index_split_004.html#p230)

**DELETE** [queries, 366–371](#index_split_007.html#p387)

[sessions, 250–251](#index_split_005.html#p271)

[error handling, 340–342](#index_split_006.html#p361)

**logout.php** script

[extensions, 339](#index_split_006.html#p360)

[creating, 254–255](#index_split_005.html#p275)

**GRANT** [command, 434–435](#index_split_008.html#p455)

for sample site[, 392](#index_split_007.html#p413)

[inserting records, 357](#index_split_007.html#p378)

[saving, 255](#index_split_005.html#p276)

***localhost*** value[, 339](#index_split_006.html#p360)

loops. See also control structures; **for** loop

[paginating returned records, 365](#index_split_007.html#p386)

[debugging, 442](#index_split_008.html#p463)

**REVOKE** [command, 436](#index_split_008.html#p457)

[nesting, 149](#index_split_003.html#p170)

**SELECT** [queries, 361](#index_split_007.html#p382)

support for[, 334–335](#index_split_006.html#p355)

**M**

**TRUNCATE TABLE** [command, 371](#index_split_007.html#p392)

[Mac OS X, installation on, 419–422](#index_split_008.html#p440)

**WHERE** [clauses, 361](#index_split_007.html#p382)

[Magic Quotes, 59–60](#index_split_002.html#p80)[.](#index_split_002.html#p81) See also quotation marks

[MySQL client, using, 425–427](#index_split_008.html#p446)

**mail()** [function, 218–221, 424](#index_split_004.html#p239)

[MySQL errors, showing, 358](#index_split_007.html#p379)

[mailing lists, 439](#index_split_008.html#p460)

[MySQL privileges, creating, 433–436](#index_split_008.html#p454)

Index 453

MySQL symbols

**O**

**;** [(semicolon), 358](#index_split_007.html#p379)

**ob\_clean()** [function, 224](#index_split_005.html#p245)

**@** [(at sign), 342](#index_split_006.html#p363)

**ob\_end\_clean()** [function, 222](#index_split_005.html#p243)

**'** [(apostrophe), 358, 360](#index_split_007.html#p379)

**ob\_end\_flush()** [function, 222, 224](#index_split_005.html#p243)

MySQL users

**ob\_flush()** [function, 224](#index_split_005.html#p245)

[creating, 433–436](#index_split_008.html#p454)

**ob\_get\_contents()** [function, 224](#index_split_005.html#p245)

[setting root user password, 430–432](#index_split_008.html#p451)

**ob\_get\_length()** [function, 224](#index_split_005.html#p245)

**mysql\_connect.php** script

**ob\_start()** [function, 222–223](#index_split_005.html#p243)

[creating, 337](#index_split_006.html#p358)

[object-oriented programming resources, 443](#index_split_008.html#p464)

[creating databases, 344–346](#index_split_006.html#p365)

**$okay** conditional, using with **else**[, 126–127](#index_split_003.html#p147)

[error-handling, 341](#index_split_006.html#p362)

online resources. See also Web sites

sample site[, 382](#index_split_007.html#p403)

[code repositories, 438](#index_split_008.html#p459)

[saving, 338, 342, 382](#index_split_006.html#p359)

[newsgroups, 439](#index_split_008.html#p460)

[selecting databases, 344–346](#index_split_006.html#p365)

[PHP manual, 437–438](#index_split_008.html#p458)

**mysql\_error()** [function, 340](#index_split_006.html#p361)

W[eb sites, 438](#index_split_008.html#p459)

**mysql\_fetch\_array()** [function, 365](#index_split_007.html#p386)

operators. See also mathematical operators

**mysql\_num\_rows()** [function, 365, 377](#index_split_007.html#p386)

[arithmetic, 129](#index_split_003.html#p150)

**mysql\_query()** function

[comparison, 129–132](#index_split_003.html#p150)

[invoking, 348, 350](#index_split_007.html#p369)

[logical, 133–137](#index_split_003.html#p154)

returning **TRUE**[, 350](#index_split_007.html#p371)

precedence of[, 84–85, 445](#index_split_002.html#p105)

[using, 356](#index_split_007.html#p377)

table of[, 129, 445](#index_split_003.html#p150)

**mysql\_real\_escape\_string()** [function, 377](#index_split_007.html#p398)

[using, 77–80](#index_split_002.html#p98)

**OR** operator[, 129, 133](#index_split_003.html#p150)

**N**

**ORDER BY** clause, contents of[, 399](#index_split_007.html#p420)

name[, adding to HTML form, 93](#index_split_002.html#p114)

[output buffering, 222–224, 238](#index_split_005.html#p243)

**name** value[, using with greetings, 70–71](#index_split_002.html#p91)

**$name** variable[, creating via concatenation, 96](#index_split_002.html#p117)

**P**

**natcasesort()** [function, 171](#index_split_004.html#p192)

**natsort()**

pages. See HTML pages; Web pages

[function, 171](#index_split_004.html#p192)

[parameters, using with functions, 265–270](#index_split_005.html#p286)

negation operator[, 129](#index_split_003.html#p150)

parentheses ( **()**)

nesting

[conditionals, 133](#index_split_003.html#p154)

[using in calculations, 84–85](#index_split_002.html#p105)

[conditionals for login form, 207](#index_split_004.html#p228)

[using in conditionals, 125](#index_split_003.html#p146)

[loops, 149](#index_split_003.html#p170)

[parse errors, 64](#index_split_002.html#p85)

newline character (**\\n**[), using with HTML, 23](#index_split_000.html#p44)

[debugging, 442](#index_split_008.html#p463)

newlines

[for variable values, 44](#index_split_001.html#p65)

[converting to breaks, 98–99](#index_split_002.html#p119)[, 102](#index_split_002.html#p120)

[password values, validating, 130–133](#index_split_003.html#p151)

[inserting into strings, 99](#index_split_002.html#p120)

passwords

[newsgroups, 439](#index_split_008.html#p460)

[assigning to root user in MySQL, 431–432](#index_split_008.html#p452)

**nl2br()** function. See also functions

creating inputs for[, 117](#index_split_003.html#p138)

[in PHP manual, 18](#index_split_000.html#p39)

[validating for sticky forms, 214](#index_split_004.html#p235)

using with HTML in PHP[, 101–102](#index_split_002.html#p122)

permissions. See databases; file permissions

[using with newlines, 99](#index_split_002.html#p120)

PHP. See also sample site

not equal to operator[, 130](#index_split_003.html#p151)

case-insensitivity of[, 17](#index_split_000.html#p38)

Not Found server response[, receiving, 13](#index_split_000.html#p34)

[configuring, 423–424](#index_split_008.html#p444)

**not** operator[, 133–134](#index_split_003.html#p154)

as server-side technology[, 203](#index_split_004.html#p224)

Notice error type[, 64](#index_split_002.html#p85)

PHP code[, placing in files, 224](#index_split_005.html#p245)

***number*** class, using with **handle\_calc.php**

**.php** [extension, 9](#index_split_000.html#p30)

[document, 77](#index_split_002.html#p98)

[PHP function list, 20](#index_split_000.html#p41)

[number variables, 38](#index_split_001.html#p59)

PHP functions. See also arguments; functions;

**number\_format()** [function, 81–83](#index_split_002.html#p102)

**nl2br()** function; sorting functions;

numbers. See also random numbers

validation functions

creating HTML forms for[, 74–76](#index_split_002.html#p95)

[with arguments, 265–270](#index_split_005.html#p286)

[decrementing, 86–87](#index_split_002.html#p107)

**array()**[, 154–155, 157](#index_split_003.html#p175)

[formatting, 81–83](#index_split_002.html#p102)

**count()**[, 160](#index_split_003.html#p181)

[incrementing, 86–87](#index_split_002.html#p107)

[creating and calling, 260–264](#index_split_005.html#p281)

[integers and floating-point, 38](#index_split_001.html#p59)

**crypt()**[, 106](#index_split_002.html#p127)

**round()** [function, 81, 83](#index_split_002.html#p102)

**date()**[, 201–203, 446](#index_split_004.html#p222)

[valid versus invalid, 38](#index_split_001.html#p59)

**explode()**[, 172, 174](#index_split_004.html#p193)

454 Index

**fclose()**[, 295, 302](#index_split_006.html#p316)

**strlen()**[, 109](#index_split_002.html#p130)

**fgetcsv()**[, 331](#index_split_006.html#p352)

**strnatcasecmp()**[, 107](#index_split_002.html#p128)

**fgets()**[, 327](#index_split_006.html#p348)

**strnatcmp()**[, 107](#index_split_002.html#p128)

**file()**[, 304](#index_split_006.html#p325)

**strpos()**[, 107](#index_split_002.html#p128)

**file\_get\_contents()**[, 304](#index_split_006.html#p325)

**strstr()**[, 107](#index_split_002.html#p128)

**file\_put\_contents()**[, 293–294](#index_split_006.html#p314)

**strtok()**[, 107](#index_split_002.html#p128)

**flock()** [lock types, 301–303](#index_split_006.html#p322)

**strtolower()**[, 111](#index_split_002.html#p132)

**fopen()** [modes, 294, 446](#index_split_006.html#p315)

**substr()**[, 108](#index_split_002.html#p129)

[formatting, 259](#index_split_005.html#p280)

**trim()**[, 111–113, 132](#index_split_002.html#p132)

**function\_exists()**[, 264](#index_split_005.html#p285)

**ucfirst()**[, 111](#index_split_002.html#p132)

**fwrite()**[, 295](#index_split_006.html#p316)

**ucwords()**[, 111](#index_split_002.html#p132)

**glob()**[, 319](#index_split_006.html#p340)

**unlink()**[, 314](#index_split_006.html#p335)

**header()**[, 222, 225–229](#index_split_005.html#p243)

**unset()**[, 158](#index_split_003.html#p179)

**headers\_sent()**[, 229](#index_split_005.html#p250)

**urldecode()**[, 105](#index_split_002.html#p126)

**html entities()** [function, 100–102](#index_split_002.html#p121)

**urlencode()**[, 103–105](#index_split_002.html#p124)

**html\_entity\_decode**[, 102](#index_split_002.html#p123)

[user-defined, 258](#index_split_005.html#p279)

**implode()**[, 172, 174](#index_split_004.html#p193)

[using concatenation with, 106](#index_split_002.html#p127)

**include()**[, 192–193, 196](#index_split_004.html#p213)

[using conditionals in, 125](#index_split_003.html#p146)

**is\_readable()**[, 306](#index_split_006.html#p327)

[using with HTML tags, 100–101](#index_split_002.html#p121)

**is\_writable()**[, 295](#index_split_006.html#p316)

**var\_dump()**[, 157](#index_split_003.html#p178)

**join()**[, 174](#index_split_004.html#p195)

**wordwrap()**[, 102](#index_split_002.html#p123)

**list()**[, 181](#index_split_004.html#p202)

PHP installation

**mail()**[, 218–221, 424](#index_split_004.html#p239)

[on Mac OS X, 419–422](#index_split_008.html#p440)

**make\_date\_menus()** [function, 263](#index_split_005.html#p284)

[on Windows, 415–418](#index_split_008.html#p436)

**make\_text\_input()**[, 269](#index_split_005.html#p290)

PHP manual

**mcrypt\_encrypt()**[, 106](#index_split_002.html#p127)

[accessing, 18](#index_split_000.html#p39)

**md5()**[, 326](#index_split_006.html#p347)

[deprecated functions in, 21](#index_split_000.html#p42)

**move\_uploaded\_file()**[, 310](#index_split_006.html#p331)

[looking up function definitions, 20–21](#index_split_000.html#p41)

**mysql\_error()**[, 340](#index_split_006.html#p361)

**nl2br()** function page[, 18](#index_split_000.html#p39)

**mysql\_fetch\_array()**[, 365](#index_split_007.html#p386)

**print** function page[, 18](#index_split_000.html#p39)

**mysql\_num\_rows()**[, 365, 377](#index_split_007.html#p386)

[using, 18–19](#index_split_000.html#p39)[, 437–438](#index_split_000.html#p40)

**mysql\_query()**[, 348, 356](#index_split_007.html#p369)

PHP scripts

**mysql\_real\_escape\_string()** [function, 377](#index_split_007.html#p398)

[accessing via URLs, 14](#index_split_000.html#p35)

[naming, 258](#index_split_005.html#p279)

adding comments to[, 25–27](#index_split_001.html#p46)

**ob\_clean()**[, 224](#index_split_005.html#p245)

[blank pages displayed in, 63](#index_split_002.html#p84)

**ob\_end\_clean()**[, 222](#index_split_005.html#p243)

[creating, 8–9](#index_split_000.html#p29)

**ob\_end\_flush()**[, 222, 224](#index_split_005.html#p243)

[creating for HTML pages, 70–71](#index_split_002.html#p91)

**ob\_flush()**[, 224](#index_split_005.html#p245)

creating links to[, 68–69](#index_split_002.html#p89)

**ob\_get\_contents()**[, 224](#index_split_005.html#p245)

[debugging, 28–29](#index_split_001.html#p49)

**ob\_get\_length()**[, 224](#index_split_005.html#p245)

[displaying errors in, 61–63](#index_split_002.html#p82)

**ob\_start()**[, 222–223](#index_split_005.html#p243)

ex[ecuting, 9](#index_split_000.html#p30)

[omitting spaces from, 258](#index_split_005.html#p279)

as open source software[, 10](#index_split_000.html#p31)

**readfile()**[, 306](#index_split_006.html#p327)

passing data to[, 67](#index_split_002.html#p88)

**require()**[, 192–193, 196](#index_split_004.html#p213)

passing preset values to[, 60](#index_split_002.html#p81)

[returning values, 274–278](#index_split_005.html#p295)

[running, 10](#index_split_002.html#p81)

**rmdir()**[, 326](#index_split_006.html#p347)

[running through URLs, 28, 440](#index_split_001.html#p49)

**scandir()** [function, 315](#index_split_006.html#p336)

sending to server via FTP[, 10–11](#index_split_000.html#p31)

**session\_start()**[, 222, 249](#index_split_005.html#p243)

[testing in browsers, 12–14](#index_split_000.html#p33)

**setcookie()**[, 222, 234, 238](#index_split_005.html#p243)

[PHP scripts, running through URLs, 7](#index_split_000.html#p28)

**sizeof()**[, 160](#index_split_003.html#p181)

[PHP syntax, 7–8](#index_split_000.html#p28)

**srtoupper()**[, 111](#index_split_002.html#p132)

[PHP tags, 7,](#index_split_000.html#p28) [16.](#index_split_000.html#p37) See also HTML tags; tags **str\_ireplace()**[, 111–113](#index_split_002.html#p132)

[PHP version, confirming, 28, 440](#index_split_001.html#p49)

**str\_word\_count()**[, 109](#index_split_002.html#p130)

[PHP versus HTML documents, 7](#index_split_000.html#p28)

**strcasecmp()**[, 107](#index_split_002.html#p128)

PHP W[eb sites, 438](#index_split_008.html#p459)

**strcmp()**[, 107](#index_split_002.html#p128)

PHP-enabled server[, obtaining, 10](#index_split_000.html#p31)

**strip\_tags()** [function, 100–102](#index_split_002.html#p121)

**phpinfo()** function

**stripos()**[, 107](#index_split_002.html#p128)

[calling, 8](#index_split_000.html#p29)

**stristr()**[, 107](#index_split_002.html#p128)

[running to display errors, 61](#index_split_002.html#p82)

Index 455

**/phpinfo.php**[, adding to URL, 13](#index_split_000.html#p34)

displaying randomly[, 304–306](#index_split_006.html#p325)

**phpinfo.php** script

[editing, 400–405](#index_split_007.html#p421)

[creating, 8](#index_split_000.html#p29)

storing in text file[, 296–300](#index_split_006.html#p317)

[saving, 9](#index_split_000.html#p30)

**quotes.php** file[, saving, 47](#index_split_001.html#p68)

uploading to server[, 11](#index_split_000.html#p32)

**quotes.txt** file

phpMy[Admin, 335](#index_split_006.html#p356)

[creating, 289–290](#index_split_006.html#p310)

assigning root user[, 432](#index_split_008.html#p453)

[referencing, 297](#index_split_006.html#p318)

[creating users in, 432](#index_split_008.html#p453)

[using, 428–429](#index_split_008.html#p449)

**R**

**$\_POST** elements, adding to calculator[, 78](#index_split_002.html#p99)

POS[T method, using with HTML forms, 54–56](#index_split_001.html#p75)

radio buttons

**$\_POST** predefined variable[, 57–59](#index_split_001.html#p78)

[adding to HTML forms, 52](#index_split_001.html#p73)

**posting.html** script

presetting status of[, 216](#index_split_004.html#p237)

[creating, 92](#index_split_002.html#p113)

values of[, 60](#index_split_002.html#p81)

[saving, 94](#index_split_002.html#p115)

**rand()** [function, invoking, 89](#index_split_002.html#p110)

[string variables in, 95](#index_split_002.html#p116)

[random numbers, generating, 88–89](#index_split_002.html#p109)[.](#index_split_002.html#p110) See also

**<pre></pre>** [tags, using with variables, 35](#index_split_001.html#p56)

numbers

[precedence of operators managing, 84–85, 445.](#index_split_002.html#p105)

**random.php** [script, creating, 88](#index_split_002.html#p109)

See also operators

**range()** [function, using to create arrays, 157](#index_split_003.html#p178)

[predefined variables, 32–35, 57](#index_split_001.html#p53)[.](#index_split_001.html#p78) See also **readfile()** [function, 306](#index_split_006.html#p327)

variables

[reading from files, 304–306](#index_split_006.html#p325)

**predefined.php** file[, saving, 34](#index_split_001.html#p55)

records

**print** statement

CRUD[, 396](#index_split_007.html#p417)

[language construct, 144](#index_split_003.html#p165)

[editing in databases, 373–374](#index_split_007.html#p394)

[in PHP manual, 18](#index_split_000.html#p39)

[inserting via MySQL, 357](#index_split_007.html#p378)

[typing, 15](#index_split_000.html#p36)

[paginating returned, 365](#index_split_007.html#p386)

[using on variable types, 41](#index_split_001.html#p62)

**register.html** script

[using over multiple lines, 17](#index_split_000.html#p38)

[creating for control structures, 116–118](#index_split_002.html#p137)

using to send HTML to browser[, 22](#index_split_000.html#p43)

**for** loop example[, 147–149](#index_split_003.html#p168)

using with HTML in PHP[, 101](#index_split_002.html#p122)

[saving, 118](#index_split_003.html#p139)

using with sales cost calculator[, 79](#index_split_002.html#p100)

**register.php** script

[using with substrings, 110](#index_split_002.html#p131)

[directories, 321–326](#index_split_006.html#p342)

using with **urlencode()** [function, 104](#index_split_002.html#p125)

**mail()** [function, 218](#index_split_004.html#p239)

**print\_r()** [function, calling, 33, 35](#index_split_001.html#p54)

[saving, 216](#index_split_004.html#p237)

**printf()** [function, using to format numbers, 83](#index_split_002.html#p104)

[sticky form, 212](#index_split_004.html#p233)

printing

registration form, creating shell of[, 211–216](#index_split_004.html#p232)

[$ (dollar sign), 79](#index_split_002.html#p100)

registration script, creating for directory[, 321–326](#index_split_006.html#p342)

[constants, 199–200](#index_split_004.html#p220)

relative paths

message in browser[, 16](#index_split_000.html#p37)

start of[, 293](#index_split_006.html#p314)

[predefined variables, 33–35](#index_split_001.html#p54)

[using with external files, 193–194](#index_split_004.html#p214)

[values of arrays, 162–163](#index_split_003.html#p183)

**require()** [function, 192–193, 196](#index_split_004.html#p213)

[variable values, 41–42](#index_split_001.html#p62)

resources

projects, identifying goals of[, 380](#index_split_007.html#p401)

[Ajax, 443–444](#index_split_008.html#p464)

pull-down menu. See also menu

[books, 444](#index_split_008.html#p465)

[creating for form, 260–261](#index_split_005.html#p281)

[code repositories, 438](#index_split_008.html#p459)

[preselecting, 216](#index_split_004.html#p237)

[frameworks, 443](#index_split_008.html#p464)

[JavaScript, 443–444](#index_split_008.html#p464)

**Q**

[newsgroups, 439](#index_split_008.html#p460)

[object-oriented programming, 443](#index_split_008.html#p464)

queries, ex[ecuting, 352](#index_split_007.html#p373)

[PHP manual, 437–438](#index_split_008.html#p458)

[query data, securing, 358–360](#index_split_007.html#p379)

security[, 443](#index_split_008.html#p464)

[query statement, 353–354](#index_split_007.html#p374)

W[eb sites, 438](#index_split_008.html#p459)

quotation marks. See also Magic Quotes

[reverse conditionals, 132](#index_split_003.html#p153)

[using, 45–47](#index_split_001.html#p66)

**REVOKE** [command, using in MySQL, 436](#index_split_008.html#p457)

[using with strings, 39](#index_split_001.html#p60)

**rmdir()** [function, 326](#index_split_006.html#p347)

[using with variables, 45](#index_split_001.html#p66)

**round()** [function, using with numbers, 81, 83, 89](#index_split_002.html#p102)

quotations

**$row** reference[, explained, 361](#index_split_007.html#p382)

adding to sample site[, 393–396](#index_split_007.html#p414)

**rsort()**[function, 168](#index_split_004.html#p189)

[deleting, 406–409](#index_split_008.html#p427)

456 Index

**S**

sorting functions. See also PHP functions

**arsort()**[, 168, 170](#index_split_004.html#p189)

sales cost calculator[, creating, 77–80](#index_split_002.html#p98)

**asort()**[, 168–170](#index_split_004.html#p189)

sample site. See also databases; PHP; Web sites

**krsort()**[, 168](#index_split_004.html#p189)

[adding quotes, 393–396](#index_split_007.html#p414)

**ksort()**[, 168–171](#index_split_004.html#p189)

connecting to database[, 382](#index_split_007.html#p403)

**natcasesort()**[, 171](#index_split_004.html#p192)

creating database for[, 380](#index_split_007.html#p401)

**natsort()**[, 171](#index_split_004.html#p192)

creating home page[, 410–413](#index_split_008.html#p431)

**rsort()**[, 168](#index_split_004.html#p189)

creating tables for[, 380](#index_split_007.html#p401)

**shuffle()**[, 168](#index_split_004.html#p189)

creating template[, 385–387](#index_split_007.html#p406)

**sort()**[, 168](#index_split_004.html#p189)

[deleting quotes, 406–409](#index_split_008.html#p427)

**uasort()**[, 171](#index_split_004.html#p192)

[editing quotes, 400–405](#index_split_007.html#p421)

**ursort()**[, 171](#index_split_004.html#p192)

[listing quotes, 397–399](#index_split_007.html#p418)

**usort()**[, 171](#index_split_004.html#p192)

[logging in, 388–391](#index_split_007.html#p409)

**sort.php** file

[logging out, 392](#index_split_007.html#p413)

[creating, 169](#index_split_004.html#p190)

[organizing, 381](#index_split_007.html#p402)

**quote\_id**

[saving, 171](#index_split_004.html#p192)

primary key, [381](#index_split_007.html#p402)

**$soups** array[, 155, 162](#index_split_003.html#p176)

structure of[, 381](#index_split_007.html#p402)

**soups1.php** script

[writing user-defined function, 383–384](#index_split_007.html#p404)

[creating, 159](#index_split_003.html#p180)

scalar variable[, defined, 152.](#index_split_003.html#p173) See also variables **scandir()**

[opening, 159](#index_split_003.html#p180)

[function, 315](#index_split_006.html#p336)

[saving, 156](#index_split_003.html#p177)

scripts. See PHP scripts

**soups3.php** script

[security resources, 443](#index_split_008.html#p464)

**select**

[creating, 162](#index_split_003.html#p183)

[element, using with HTML forms, 52](#index_split_001.html#p73)

**SELECT**

[saving, 163](#index_split_003.html#p184)

[queries, 334](#index_split_006.html#p355)

[spaces, using between function calls, 83](#index_split_002.html#p104)

[defining, 361, 363](#index_split_007.html#p382)

spacing HTML code[, 23](#index_split_000.html#p44)

[running, 363](#index_split_007.html#p384)

**sprintf()** [function, using to format numbers, 83](#index_split_002.html#p104)

semicolon (**;** [), using in MySQL, 358](#index_split_007.html#p379)

SQL (Structured Query L[anguage), 334–335](#index_split_006.html#p355)

server

[SQL injection attack, 358](#index_split_007.html#p379)

[configuring to send email, 221](#index_split_005.html#p242)

[SQL keywords, writing, 351](#index_split_007.html#p372)

[requesting information from, 55](#index_split_001.html#p76)

[sticky forms, making, 210–216](#index_split_004.html#p231)

setting time zone[, 203](#index_split_004.html#p224)

**sticky1.php** script

uploading **phpinfo.php** script to[, 11](#index_split_000.html#p32)

**$\_SERVER**

[creating, 268](#index_split_005.html#p289)

predefined variable[, 57](#index_split_001.html#p78)

[functions with default values, 272](#index_split_005.html#p293)

server-side technology[, 7](#index_split_000.html#p28)

**$\_SESSION**

[saving, 270](#index_split_005.html#p291)

array[, 252](#index_split_005.html#p273)

**sticky2.php** [script, saving, 273](#index_split_005.html#p294)

[session values, deleting, 255](#index_split_005.html#p276)

**str\_ireplace()** [function, 111–113](#index_split_002.html#p132)

session variables

**str\_word\_count()** [function, 109](#index_split_002.html#p130)

[accessing, 252–253](#index_split_005.html#p273)

**strcasecmp()** [function, 107](#index_split_002.html#p128)

[verifying, 253](#index_split_005.html#p274)

**strcmp()**

**session\_start()**

[function, 107](#index_split_002.html#p128)

[function, 222, 249](#index_split_005.html#p243)

string case[, adjusting, 111](#index_split_002.html#p132)

sessions

string operator[, 129](#index_split_003.html#p150)

[versus cookies, 248](#index_split_005.html#p269)

[string values, comparing, 132](#index_split_003.html#p153)

[creating, 249–251](#index_split_005.html#p270)

[string variables, 39](#index_split_001.html#p60)

[deleting, 254–255](#index_split_005.html#p275)

strings. See also substrings

overview[, 248](#index_split_005.html#p269)

[comparing, 107](#index_split_002.html#p128)

[using without cookies, 255](#index_split_005.html#p276)

**setcookie()**

[concatenating, 95–97](#index_split_002.html#p116)

 [function, 222, 234, 238](#index_split_005.html#p243)

[counting words and characters in, 109](#index_split_002.html#p130)

[short tags, 9](#index_split_000.html#p30)

**shuffle()**

[decrypting, 106](#index_split_002.html#p127)

[function, using with arrays, 168](#index_split_004.html#p189)

empty[, 39](#index_split_001.html#p60)

single quotation marks (**'** )

[encoding and decoding, 103–106](#index_split_002.html#p124)

[using with arrays, 160](#index_split_003.html#p181)

[encrypting, 106](#index_split_002.html#p127)

[using with strings, 39](#index_split_001.html#p60)

HTML form for[, 92–94](#index_split_002.html#p113)

[using with variables, 45–47](#index_split_001.html#p66)

inserting newlines into[, 99](#index_split_002.html#p120)

site structure[, 194](#index_split_004.html#p215)

[linking via concatenation, 97](#index_split_002.html#p118)

sites. See sample site; Web sites

**sizeof()**

replacing parts of[, 111–113](#index_split_002.html#p132)

[function, 160](#index_split_003.html#p181)

**sort()**

using for array index[es, 161](#index_split_003.html#p182)

 [function, 168](#index_split_004.html#p189)

using in **switch** [conditionals, 145](#index_split_003.html#p166)

Index 457

[strings and arrays, transforming between, 172–175](#index_split_004.html#p193)

**U**

**strip\_tags()** [function, 100–102](#index_split_002.html#p121)

**uasort()** [function, 171](#index_split_004.html#p192)

**stripos()** [function, 107](#index_split_002.html#p128)

**ucfirst()** [function, using with strings, 111](#index_split_002.html#p132)

**stristr()** [function, 107](#index_split_002.html#p128)

**ucwords()** [function, using with strings, 111](#index_split_002.html#p132)

**strlen()** [function, 109](#index_split_002.html#p130)

Undefined variable error[, 44](#index_split_001.html#p65)

**strnatcasecmp()** [function, 107](#index_split_002.html#p128)

underscore ( **\_** ) , [using with variables, 36](#index_split_001.html#p57)

**strnatcmp()** [function, 107](#index_split_002.html#p128)

[Unicode encoding, 5](#index_split_000.html#p26)

**strpos()** [function, 107](#index_split_002.html#p128)

**unlink()** [function, 314](#index_split_006.html#p335)

**strstr()** [function, 107](#index_split_002.html#p128)

**unset()** [function, 158](#index_split_003.html#p179)

**strtok()** [function, 107](#index_split_002.html#p128)

**UPDATE** [command in SQL, 334](#index_split_006.html#p355)

**strtolower()** [function, 111](#index_split_002.html#p132)

**UPDATE** queries

Structured Query L[anguage (SQL), 334–335](#index_split_006.html#p355)

**LIMIT 1** clause[, 377](#index_split_007.html#p398)

**strupper()** [function, 111](#index_split_002.html#p132)

[using with databases, 372–377](#index_split_007.html#p393)

[subdirectories, listing, 318](#index_split_006.html#p339)

**upload\_file.php** script

submit button

[creating, 310](#index_split_006.html#p331)

[adding to HTML forms, 53](#index_split_001.html#p74)

[saving, 314](#index_split_006.html#p335)

creating for **register.html script**[, 118](#index_split_003.html#p139)

**uploads** folder[, creating, 309](#index_split_006.html#p330)

**substr()** [function, 108](#index_split_002.html#p129)

**urldecode()** [function, 105](#index_split_002.html#p126)

substrings. See also strings

**urlencode()** [function, 103–105](#index_split_002.html#p124)

[finding, 107–110](#index_split_002.html#p128)

URLs

[replacing, 111–113](#index_split_002.html#p132)

[accessing scripts from, 13](#index_split_000.html#p34)

subtraction (**−**) operator[, using, 77–80](#index_split_002.html#p98)[, 129](#index_split_002.html#p101)

adding **/phpinfo.php** to[, 13](#index_split_000.html#p34)

[superglobals, 153, 285.](#index_split_003.html#p174) See also arrays

[running PHP scripts through, 28](#index_split_001.html#p49)

[support forum, 6](#index_split_000.html#p27)

**ursort()** [function, 171](#index_split_004.html#p192)

**switch** [conditional, using, 142–145](#index_split_003.html#p163)

user-defined functions. See also functions

[creating, 258–259](#index_split_005.html#p279)

**T**

[memory requirements, 264](#index_split_005.html#p285)

tables. See database tables

writing for sample site[, 383–384](#index_split_007.html#p404)

[tags, 9.](#index_split_000.html#p30) See also HTML tags; PHP tags

**users** folder[, creating, 320](#index_split_006.html#p341)

tax rate

**users.txt** file

[calculating, 79](#index_split_002.html#p100)

[displaying, 326](#index_split_006.html#p347)

[recalculating, 86–87](#index_split_002.html#p107)

[login script, 327–331](#index_split_006.html#p348)

[template system, files in, 196](#index_split_004.html#p217)

[saving, 320](#index_split_006.html#p341)

**template.html** script

**usort()** [function, 171](#index_split_004.html#p192)

[creating, 185–187](#index_split_004.html#p206)

[UTF-8 encoding, using, 5](#index_split_000.html#p26)

header file[, 188–189](#index_split_004.html#p209)

[saving, 187](#index_split_004.html#p208)

**V**

templates. See also CSS templates; Web

validating

applications; Web pages

[form data, 120–121, 123–125](#index_split_003.html#p141)

[creating, 184](#index_split_004.html#p205)

[password values, 130–133](#index_split_003.html#p151)

creating for sample site[, 385–387](#index_split_007.html#p406)

[variables, 141](#index_split_003.html#p162)

footer file[, 190–191](#index_split_004.html#p211)

[year values, 130–133](#index_split_003.html#p151)

header file[, 188–189](#index_split_004.html#p209)

[validation, repeating for sticky form, 213–214](#index_split_004.html#p234)

[layout model, 185–187](#index_split_004.html#p206)

validation functions. See also PHP functions

[using with external files, 193–194](#index_split_004.html#p214)

**checkdate()**[, 128](#index_split_003.html#p149)

text, sending to browser[, 15–17](#index_split_000.html#p36)

**empty()**[, 122–123](#index_split_003.html#p143)

text area, presetting value of[, 216](#index_split_004.html#p237)

**is\_numeric()**[, 123, 125](#index_split_003.html#p144)

[text input, adding to email address, 52](#index_split_001.html#p73)

**isset()**[, 122–123, 125](#index_split_003.html#p143)

**textarea** form element

[values, assigning to variables, 129](#index_split_003.html#p150)

[adding to HTML forms, 53](#index_split_001.html#p74)

**var\_dump()** [function, 157](#index_split_003.html#p178)

[using with newlines, 98–99](#index_split_002.html#p119)

variable names

TextMate Web site[, 4](#index_split_000.html#p25)

case sensitivity of[, 36](#index_split_001.html#p57)

time zone, setting for server[, 203](#index_split_004.html#p224)

[conventions, 37](#index_split_001.html#p58)

[token substring, explained, 107](#index_split_002.html#p128)

variable scope

**trim()** [function, using with strings, 111–113, 132](#index_split_002.html#p132)

**$arg** and **$var** [values, 280](#index_split_006.html#p301)

TRUE versus F[ALSE conditionals, 133, 137](#index_split_003.html#p154)

**global** [statement, 279–285](#index_split_006.html#p300)

**TRUNCATE TABLE** [command, 371](#index_split_007.html#p392)

overview[, 279–281](#index_split_006.html#p300)

458 Index

[variable syntax, 36–37](#index_split_001.html#p57)

[header area, 186](#index_split_004.html#p207)

variable types

header file[, 188–189](#index_split_004.html#p209)

[arrays, 40](#index_split_001.html#p61)

[layout model, 185–188](#index_split_004.html#p206)

[numbers, 38](#index_split_001.html#p59)

[login form, 205–209](#index_split_004.html#p226)

[strings, 39](#index_split_001.html#p60)

[sidebars, 187](#index_split_004.html#p208)

using **print** [statement on, 41](#index_split_001.html#p62)

Web root directory[, 288](#index_split_006.html#p309)

variable values

Web sites. See also online resources; sample site

[assigning, 41–44](#index_split_001.html#p62)

Apache[, 10](#index_split_000.html#p31)

[incrementing, 86–87](#index_split_002.html#p107)

[BBEdit, 4](#index_split_000.html#p25)

[parse errors, 44](#index_split_001.html#p65)

Crimson Editor[, 4](#index_split_000.html#p25)

[printing, 35, 41–42](#index_split_001.html#p56)

Dreamweaver[, 4](#index_split_000.html#p25)

variables. See also predefined variables;

[EditPlus, 4](#index_split_000.html#p25)

scalar variable

identifying goals of[, 380](#index_split_007.html#p401)

**$\_SERVER**[, 34–35](#index_split_001.html#p55)

[support forum, 6](#index_split_000.html#p27)

assigning values to[, 129](#index_split_003.html#p150)

TextMate[, 4](#index_split_000.html#p25)

documenting purpose of[, 37](#index_split_001.html#p58)

W[eb-page extensions, 9](#index_split_000.html#p30)

[minimizing bugs in, 37](#index_split_001.html#p58)

**welcome.html** file[, saving, 6](#index_split_000.html#p27)

[nonexisting, 60](#index_split_002.html#p81)

**welcome.php** page

overview[, 32](#index_split_001.html#p53)

[creating, 227–229](#index_split_005.html#p248)

[predefined, 32–35](#index_split_001.html#p53)

[session variables, 252](#index_split_005.html#p273)

referring to[, 37](#index_split_001.html#p58)

**WHERE** [clauses, using in queries, 361](#index_split_007.html#p382)

[valid versus invalid, 37](#index_split_001.html#p58)

**while** loop[, 146, 149](#index_split_003.html#p167)

[validating, 141](#index_split_003.html#p162)

white space[, using, 23](#index_split_000.html#p44)

[without values, 441](#index_split_008.html#p462)

[Windows, installation on, 415–418](#index_split_008.html#p436)

**variables.php** file[, saving, 44](#index_split_001.html#p65)

[word list, alphabetizing, 172](#index_split_004.html#p193)

**view\_blog.php** [script, 366, 369–371, 376–377](#index_split_007.html#p387)

**wordwrap()** [function, 102](#index_split_002.html#p123)

**view\_entries.php** script

[creating, 362](#index_split_007.html#p383)

**X**

[saving, 365](#index_split_007.html#p386)

**view\_quote.php** script

XAMPP[, installing on Windows, 417–419](#index_split_008.html#p438)

[creating, 305–306](#index_split_006.html#p326)

XHTML

for sample site[, 397–399](#index_split_007.html#p418)

[attributes, 2](#index_split_000.html#p23)

[saving, 306](#index_split_006.html#p327)

[CSS, 2](#index_split_000.html#p23)

**view\_settings.php** script

[versus HTML, 2](#index_split_000.html#p23)

[saving, 241](#index_split_005.html#p262)

resource[, 6](#index_split_000.html#p27)

[using with cookies, 239](#index_split_005.html#p260)

[rules, 50–51](#index_split_001.html#p71)

[tags, 2–3](#index_split_000.html#p23)

[XHTML code sample document, 4](#index_split_000.html#p25)

**W**

XHTML page

Warning error type[, 64](#index_split_002.html#p85)

[body section, 5–6](#index_split_000.html#p26)

[weakly typed, explained, 97](#index_split_002.html#p118)

**body** [tags, 6](#index_split_000.html#p27)

Web applications. See also templates

**<br />** [tag, 6](#index_split_000.html#p27)

[constants, 197–200](#index_split_004.html#p218)

[creating, 4–6](#index_split_000.html#p25)

date and time[, 201–203](#index_split_004.html#p222)

[head section, 5](#index_split_000.html#p26)

[external files, 192–196](#index_split_004.html#p213)

[header lines, 4–5](#index_split_000.html#p25)

[HTTP headers, 225–229](#index_split_005.html#p246)

[saving, 6](#index_split_000.html#p27)

[output buffering, 222–224](#index_split_005.html#p243)

[testing, 6](#index_split_000.html#p27)

[sending email, 217–221](#index_split_004.html#p238)

**XOR** operator[, 133–134](#index_split_003.html#p154)

[sticky forms, 210–216](#index_split_004.html#p231)

[XSS (cross-site scripting) attacks, 100](#index_split_002.html#p121)

W[eb document root, 12](#index_split_000.html#p33)

Web pages. See also templates

**Y**

adding CSS to[, 3](#index_split_000.html#p24)

[banners, 186](#index_split_000.html#p24)

[year pull-down menu, creating, 262](#index_split_005.html#p283)

[blank, 440–441](#index_split_008.html#p461)

[year validation, 137](#index_split_003.html#p158)

[content, 187](#index_split_004.html#p208)

[year values, validating, 130–133, 135](#index_split_003.html#p151)

defining titles for[, 198](#index_split_004.html#p219)

year variable[, checking digits in, 135–136](#index_split_003.html#p156)

footer[, 187, 190–191](#index_split_004.html#p208)

Index 459

![Image 534](index-481_1.jpg)

WATCH

READ

CREATE

Meet Creative Edge.

A new resource of unlimited

books, videos and tutorials for

creatives from the world’s

leading experts.

Creative Edge is your one

stop for inspiration, answers to

technical questions and ways to

stay at the top of your game so

you can focus on what you do

best—being creative.

All for only $24.99 per month

for access—any day any time

you need it.

peachpit.com/creativeedge

# Document Outline

*   [Table of Contents](#index_split_000.html#p6)
*   [Introduction](#index_split_000.html#p10)
*   [Chapter 1 Getting Started with PHP](#index_split_000.html#p22) 
    *   [Basic HTML Syntax](#index_split_000.html#p23)
    *   [Basic PHP Syntax](#index_split_000.html#p28)
    *   [Using FTP](#index_split_000.html#p31)
    *   [Testing Your Script](#index_split_000.html#p33)
    *   [Sending Text to the Browser](#index_split_000.html#p36)
    *   [Using the PHP Manual](#index_split_000.html#p39)
    *   [Sending HTML to the Browser](#index_split_000.html#p43)
    *   [Adding Comments to Scripts](#index_split_001.html#p46)
    *   [Basic Debugging Steps](#index_split_001.html#p49)
    *   [Review and Pursue](#index_split_001.html#p51)
*   [Chapter 2 Variables](#index_split_001.html#p52) 
    *   [What Are Variables?](#index_split_001.html#p53)
    *   [Variable Syntax](#index_split_001.html#p57)
    *   [Types of Variables](#index_split_001.html#p59)
    *   [Variable Values](#index_split_001.html#p62)
    *   [Understanding Quotation Marks](#index_split_001.html#p66)
    *   [Review and Pursue](#index_split_001.html#p69)
*   [Chapter 3 HTML Forms and PHP](#index_split_001.html#p70) 
    *   [Creating a Simple Form](#index_split_001.html#p71)
    *   [Choosing a Form Method](#index_split_001.html#p75)
    *   [Receiving Form Data in PHP](#index_split_001.html#p78)
    *   [Displaying Errors](#index_split_002.html#p82)
    *   [Error Reporting](#index_split_002.html#p85)
    *   [Manually Sending Data to a Page](#index_split_002.html#p88)
    *   [Review and Pursue](#index_split_002.html#p93)
*   [Chapter 4 Using Numbers](#index_split_002.html#p94) 
    *   [Creating the Form](#index_split_002.html#p95)
    *   [Performing Arithmetic](#index_split_002.html#p98)
    *   [Formatting Numbers](#index_split_002.html#p102)
    *   [Understanding Precedence](#index_split_002.html#p105)
    *   [Incrementing and Decrementing a Number](#index_split_002.html#p107)
    *   [Creating Random Numbers](#index_split_002.html#p109)
    *   [Review and Pursue](#index_split_002.html#p111)
*   [Chapter 5 Using Strings](#index_split_002.html#p112) 
    *   [Creating the HTML Form](#index_split_002.html#p113)
    *   [Concatenating Strings](#index_split_002.html#p116)
    *   [Handling Newlines](#index_split_002.html#p119)
    *   [HTML and PHP](#index_split_002.html#p121)
    *   [Encoding and Decoding Strings](#index_split_002.html#p124)
    *   [Finding Substrings](#index_split_002.html#p128)
    *   [Replacing Parts of a String](#index_split_002.html#p132)
    *   [Review and Pursue](#index_split_002.html#p135)
*   [Chapter 6 Control Structures](#index_split_002.html#p136) 
    *   [Creating the HTML Form](#index_split_002.html#p137)
    *   [The if Conditional](#index_split_003.html#p140)
    *   [Validation Functions](#index_split_003.html#p143)
    *   [Using else](#index_split_003.html#p147)
    *   [More Operators](#index_split_003.html#p150)
    *   [Using elseif](#index_split_003.html#p159)
    *   [The Switch Conditional](#index_split_003.html#p163)
    *   [The for Loop](#index_split_003.html#p167)
    *   [Review and Pursue](#index_split_003.html#p171)
*   [Chapter 7 Using Arrays](#index_split_003.html#p172) 
    *   [What Is an Array?](#index_split_003.html#p173)
    *   [Creating an Array](#index_split_003.html#p175)
    *   [Adding Items to an Array](#index_split_003.html#p179)
    *   [Accessing Array Elements](#index_split_003.html#p182)
    *   [Creating Multidimensional Arrays](#index_split_003.html#p185)
    *   [Sorting Arrays](#index_split_004.html#p189)
    *   [Transforming Between Strings and Arrays](#index_split_004.html#p193)
    *   [Creating an Array from a Form](#index_split_004.html#p197)
    *   [Review and Pursue](#index_split_004.html#p203)
*   [Chapter 8 Creating Web Applications](#index_split_004.html#p204) 
    *   [Creating Templates](#index_split_004.html#p205)
    *   [Using External Files](#index_split_004.html#p213)
    *   [Using Constants](#index_split_004.html#p218)
    *   [Working with the Date and Time](#index_split_004.html#p222)
    *   [Handling HTML Forms with PHP, Revisited](#index_split_004.html#p225)
    *   [Making Forms Sticky](#index_split_004.html#p231)
    *   [Sending Email](#index_split_004.html#p238)
    *   [Output Buffering](#index_split_005.html#p243)
    *   [Manipulating HTTP Headers](#index_split_005.html#p246)
    *   [Review and Pursue](#index_split_005.html#p251)
*   [Chapter 9 Cookies and Sessions](#index_split_005.html#p252) 
    *   [What Are Cookies?](#index_split_005.html#p253)
    *   [Creating Cookies](#index_split_005.html#p255)
    *   [Reading from Cookies](#index_split_005.html#p260)
    *   [Adding Parameters to a Cookie](#index_split_005.html#p263)
    *   [Deleting a Cookie](#index_split_005.html#p266)
    *   [What Are Sessions?](#index_split_005.html#p269)
    *   [Creating a Session](#index_split_005.html#p270)
    *   [Accessing Session Variables](#index_split_005.html#p273)
    *   [Deleting a Session](#index_split_005.html#p275)
    *   [Review and Pursue](#index_split_005.html#p277)
*   [Chapter 10 Creating Functions](#index_split_005.html#p278) 
    *   [Creating and Using Simple Functions](#index_split_005.html#p279)
    *   [Creating and Calling Functions That Take Arguments](#index_split_005.html#p286)
    *   [Setting Default Argument Values](#index_split_005.html#p292)
    *   [Creating and Using Functions That Return a Value](#index_split_005.html#p295)
    *   [Understanding Variable Scope](#index_split_006.html#p300)
    *   [Review and Pursue](#index_split_006.html#p307)
*   [Chapter 11 Files and Directories](#index_split_006.html#p308) 
    *   [File Permissions](#index_split_006.html#p309)
    *   [Writing to Files](#index_split_006.html#p314)
    *   [Locking Files](#index_split_006.html#p322)
    *   [Reading from Files](#index_split_006.html#p325)
    *   [Handling File Uploads](#index_split_006.html#p328)
    *   [Navigating Directories](#index_split_006.html#p336)
    *   [Creating Directories](#index_split_006.html#p341)
    *   [Reading Files Incrementally](#index_split_006.html#p348)
    *   [Review and Pursue](#index_split_006.html#p353)
*   [Chapter 12 Intro to Databases](#index_split_006.html#p354) 
    *   [Introduction to SQL](#index_split_006.html#p355)
    *   [Connecting to MySQL](#index_split_006.html#p357)
    *   [MySQL Error Handling](#index_split_006.html#p361)
    *   [Creating and Selecting a Database](#index_split_006.html#p364)
    *   [Creating a Table](#index_split_007.html#p368)
    *   [Inserting Data into a Database](#index_split_007.html#p373)
    *   [Securing Query Data](#index_split_007.html#p379)
    *   [Retrieving Data from a Database](#index_split_007.html#p382)
    *   [Deleting Data in a Database](#index_split_007.html#p387)
    *   [Updating Data in a Database](#index_split_007.html#p393)
    *   [Review and Pursue](#index_split_007.html#p399)
*   [Chapter 13 Putting It All Together](#index_split_007.html#p400) 
    *   [Getting Started](#index_split_007.html#p401)
    *   [Connecting to the Database](#index_split_007.html#p403)
    *   [Writing the User-Defined Function](#index_split_007.html#p404)
    *   [Creating the Template](#index_split_007.html#p406)
    *   [Logging In](#index_split_007.html#p409)
    *   [Logging Out](#index_split_007.html#p413)
    *   [Adding Quotes](#index_split_007.html#p414)
    *   [Listing Quotes](#index_split_007.html#p418)
    *   [Editing Quotes](#index_split_007.html#p421)
    *   [Deleting Quotes](#index_split_008.html#p427)
    *   [Creating the Home Page](#index_split_008.html#p431)
    *   [Review and Pursue](#index_split_008.html#p435)
*   [Appendix A: Installation and Configuration](#index_split_008.html#p436)
*   [Appendix B: Resources and Next Steps](#index_split_008.html#p458)
*   [Index](#index_split_008.html#p468) 
    *   [A](#index_split_008.html#p468)
    *   [B](#index_split_008.html#p469)
    *   [C](#index_split_008.html#p469)
    *   [D](#index_split_008.html#p470)
    *   [E](#index_split_008.html#p471)
    *   [F](#index_split_008.html#p471)
    *   [G](#index_split_008.html#p472)
    *   [H](#index_split_008.html#p472)
    *   [I](#index_split_008.html#p473)
    *   [J](#index_split_008.html#p473)
    *   [K](#index_split_008.html#p474)
    *   [L](#index_split_008.html#p474)
    *   [M](#index_split_008.html#p474)
    *   [N](#index_split_008.html#p475)
    *   [O](#index_split_008.html#p475)
    *   [P](#index_split_008.html#p475)
    *   [Q](#index_split_008.html#p477)
    *   [R](#index_split_008.html#p477)
    *   [S](#index_split_008.html#p478)
    *   [T](#index_split_008.html#p479)
    *   [U](#index_split_008.html#p479)
    *   [V](#index_split_008.html#p479)
    *   [W](#index_split_008.html#p480)
    *   [X](#index_split_008.html#p480)
    *   [Y](#index_split_008.html#p480)