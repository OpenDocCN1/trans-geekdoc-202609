
![cover-image](graphics/0132117932.jpg)

# Adobe`Dreamweaver`CS5`with`PHP

Training from the Source

David Powers

![Image](graphics/pub.jpg)

**Adobe`Dreamweaver`CS5`with`PHP: Training from the Source**  
David Powers

![Image](graphics/adobe.jpg)Adobe Press books are published by:  

**Peachpit**  

1249 Eighth Street  

Berkeley, CA 94710  

510/524-2178  

800/283-9444

For the latest on Adobe Press books, go to [`www.adobepress.com`](http://www.adobepress.com)  

To report errors, please send a note to [`errata@peachpit.com`](mailto:errata@peachpit.com)  

Peachpit is a division of Pearson Education.  

Copyright © 2011 David Powers

Acquisitions Editor: Victor Gavenda  

Project Editor: Rebecca Freed  

Development Editor and Copyeditor: Anne Marie Walker  

Production Editor: Becky Winter  

Technical Editor: Tom Muck  

Compositor: Danielle Foster  

Indexer: Rebecca Plunkett  

Cover Design: Charlene Charles-Will

***Notice of Rights***

All rights reserved. No part of this book may be reproduced or transmitted in any form by any means, electronic, mechanical, photocopying, recording, or otherwise, without the prior written permission of the publisher. For information on getting permission for reprints and excerpts, contact [`permissions@peachpit.com`](mailto:permissions@peachpit.com).

***Notice of Liability***

The information in this book is distributed on an “As Is” basis, without warranty. While every precaution has been taken in the preparation of the book, neither the author nor Peachpit shall have any liability to any person or entity with respect to any loss or damage caused or alleged to be caused directly or indirectly by the instructions contained in this book or by the computer software and hardware products described in it.

***Trademarks***

Adobe, the Adobe logo, and Dreamweaver are registered trademarks of Adobe Systems in the United States and/or other countries.

Many of the designations used by manufacturers and sellers to distinguish their products are claimed as trademarks. Where those designations appear in this book, and Peachpit was aware of the trademark claim, the designations appear as requested by the owner of the trademark. All other product names and services identified throughout the book are used in an editorial fashion only and for the benefit of such companies with no intention of infringement of the trademark. No such use, or the use of any trade name, is intended to convey endorsement or other affiliation with this book.

ISBN-13: 978-0-321-71984-3  

ISBN-10:          0-321-71984-0  

9 8 7 6 5 4 3 2 1  

Printed and bound in the United States of America

## Bio

David Powers has been writing about Dreamweaver, PHP, CSS, and web development since 2003. This is his twelfth book on the subject. David started developing websites in 1994, shortly after assuming the role of Editor, BBC Japanese TV. He needed a way of advertising the fledgling channel in Japan but had no budget. So, he begged the IT department for a corner of server space and singlehandedly developed an 80-page bilingual website, which he regularly maintained for the next five years.

After a career spanning three decades in radio and TV news, David left the BBC in 1999 to work independently. He’s an Adobe Community Professional and Adobe Certified Instructor for Dreamweaver. You’ll often find him giving help and advice in the Dreamweaver forums and Adobe Developer Center—to which he has contributed many popular tutorials and training videos. He greatly enjoys traveling and taking photos—all the photos used in this book were taken by him.

David has also translated a number of musical plays from Japanese into English, and he likes nothing better than sushi with a glass or two of cold sake.

## Acknowledgments

For several years I’ve bent the ears of the long-suffering Dreamweaver engineering team to improve support for PHP. Wow! They certainly came up trumps. My thanks to Devin Fernandez, Scott Fegette, Don Booth, Randy Edmunds, Chris Bank, Virgil Palanciuc, Jon Michael Varese, and the many others who have helped me dig deeper into Dreamweaver over the past few versions to understand the program’s strengths and weaknesses (yes, there are some—and I’m sure the team is already working on eliminating them).

I’m particularly grateful to Scott, one of the Dreamweaver product managers, whose idea it was to get me to write this book. I hope it’s not too far removed from what he was hoping for. Scott passed my name to Victor Gavenda, the Executive Editor at Adobe Press, while attending Adobe MAX at Los Angeles in 2009. For those of you who don’t know, MAX is an annual geekfest that’s a mixture of presentations by leading web professionals, sneak peeks into Adobe’s future technology, and wild parties (Scott plays a mean guitar).

Victor welcomed me into the Adobe Press/Peachpit family with grace and courtesy. My thanks go to him and to the two editors who worked directly with me on the book, Rebecca Freed and Anne Marie Walker. Thanks also to the production team for going the extra mile to make the code easier to read.

Finally, I mustn’t forget Tom Muck, a true Dreamweaver and PHP expert who checked the text and code for technical accuracy. This is the third book we’ve worked on together. Tom always manages to keep me on the straight and narrow, spotting important details I’ve missed and suggesting ways to improve the text. Any mistakes that remain are my responsibility alone.

## Contents

[**Introduction**](#pref03.html#pref03)

[**LESSON 1 Why PHP and Why Dreamweaver CS5?**](#ch01.html#ch01)

[A Rich Mix of PHP Features](#ch01.html#ch01lev1)

[What Is PHP? What Does It Do?](#ch01.html#ch01lev2)

[A Tour of the Main PHP Features in Dreamweaver CS5](#ch01.html#ch01lev3)

[**LESSON 2 Getting Ready to Develop with PHP**](#ch02.html#ch02)

[Setting Up a Local Testing Environment](#ch02.html#ch02lev1)

[Checking Your PHP Installation](#ch02.html#ch02lev2)

[Using Virtual Hosts](#ch02.html#ch02lev3)

[Setting Up a PHP Site in Dreamweaver CS5](#ch02.html#ch02lev4)

[**LESSON 3 A Quick Crash Course in PHP**](#ch03.html#ch03)

[How PHP Makes Pages Dynamic](#ch03.html#ch03lev1)

[Taming the Unknown with Variables](#ch03.html#ch03lev2)

[Grouping Related Values in Arrays](#ch03.html#ch03lev3)

[Using Conditions to Make Decisions](#ch03.html#ch03lev4)

[Using Functions to Perform Tasks](#ch03.html#ch03lev5)

[Using Objects and Resources](#ch03.html#ch03lev6)

[Using Operators for Calculations and Joining Strings](#ch03.html#ch03lev7)

[Automating Repetitive Tasks](#ch03.html#ch03lev8)

[Including External Files](#ch03.html#ch03lev9)

[Understanding Error Messages](#ch03.html#ch03lev10)

[**LESSON 4 Restyling a WordPress Site**](#ch04.html#ch04)

[Understanding the Structure of a CMS](#ch04.html#ch04lev1)

[Installing WordPress](#ch04.html#ch04lev2)

[Creating a WordPress Theme](#ch04.html#ch04lev3)

[**LESSON 5 Designing and Building Your Own Database**](#ch05.html#ch05)

[Working with MySQL](#ch05.html#ch05lev1)

[Creating a Database and Tables](#ch05.html#ch05lev2)

[Creating MySQL User Accounts](#ch05.html#ch05lev3)

[Importing Existing Data](#ch05.html#ch05lev4)

[**LESSON 6 Generating PHP Automatically with Server Behaviors**](#ch06.html#ch06)

[What Server Behaviors Do](#ch06.html#ch06lev1)

[Connecting to the Database](#ch06.html#ch06lev2)

[Inserting Records into a Table](#ch06.html#ch06lev3)

[Creating a Login System](#ch06.html#ch06lev4)

[Displaying, Updating, and Deleting Records](#ch06.html#ch06lev5)

[Evaluating the Server Behaviors](#ch06.html#ch06lev6)

[**LESSON 7 Validating Input on the Server**](#ch07.html#ch07)

[Introducing the Zend Framework](#ch07.html#ch07lev1)

[Improving the Registration Form](#ch07.html#ch07lev2)

[Authenticating User Credentials with Zend\_Auth](#ch07.html#ch07lev3)

[**LESSON 8 Zending Email**](#ch08.html#ch08)

[How PHP Handles Email](#ch08.html#ch08lev1)

[Stopping Spam with a CAPTCHA](#ch08.html#ch08lev2)
