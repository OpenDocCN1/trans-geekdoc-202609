
## WICKED COOL PHP

REAL-WORLD SCRIPTS THAT SOLVE DIFFICULT PROBLEMS

WILLIAM STEINMETZ WITH BRIAN WARD

COVERS PHP VERSIONS 5 AND 6

![](img/19183d2b75bf6b509317c631c0e7b817_0_0.png)

![](img/19183d2b75bf6b509317c631c0e7b817_0_1.png)

## WICKED COOL PHP

## WICKED COOL PHP

## Real-World Scripts That Solve Difficult Problems

by William Steinmetz
with Brian Ward

![](img/19183d2b75bf6b509317c631c0e7b817_4_0.png)

NO STARCH PRESS

San Francisco

WICKED COOL PHP. Copyright © 2008 by William Steinmetz with Brian Ward.

All rights reserved. No part of this work may be reproduced or transmitted in any form or by any means, electronic or mechanical, including photocopying, recording, or by any information storage or retrieval system, without the prior written permission of the copyright owner and the publisher.

Printed on recycled paper in the United States of America

12 11 10 09 08 1 2 3 4 5 6 7 8 9

ISBN-10: 1-59327-173-5
ISBN-13: 978-1-59327-173-2

- Publisher: William Pollock
- Production Editor: Megan Dunchak
- Cover and Interior Design: Octopod Studios
- Developmental Editor: Tyler Ortman
- Technical Reviewer: Scott Gilbertson
- Copyeditor: Linda Recktenwald
- Composer: Riley Hoffman
- Proofreader: Jeanne Hansen
- Indexer: Karin Arrigoni

For information on book distributors or translations, please contact No Starch Press, Inc. directly:
No Starch Press, Inc.
555 De Haro Street, Suite 250, San Francisco, CA 94107
phone: 415.863.9900; fax: 415.863.9950; info@nostarch.com; www.nostarch.com

Library of Congress Cataloging-in-Publication Data
Steinmetz, William.
Wicked cool PHP : real-world scripts that solve difficult problems / William Steinmetz and Brian
Ward. -- 1st ed.
p. cm.
Includes index.
ISBN-13: 978-1-59327-173-2
ISBN-10: 1-59327-173-5
1. PHP (Computer program language) I. Ward, Brian, 1972- II. Title.
QA76.73.P224574 2008
005.13'3--dc22
2005033702

No Starch Press and the No Starch Press logo are registered trademarks of No Starch Press, Inc. Other product and company names mentioned herein may be the trademarks of their respective owners. Rather than use a trademark symbol with every occurrence of a trademarked name, we are using the names only in an editorial fashion and to the benefit of the trademark owner, with no intention of infringement of the trademark.

The information in this book is distributed on an “As Is” basis, without warranty. While every precaution has been taken in the preparation of this work, neither the author nor No Starch Press, Inc. shall have any liability to any person or entity with respect to any loss or damage caused or alleged to be caused directly or indirectly by the information contained in it.

## BRIEF CONTENTS

- Introduction . . . . . . . . . . . . . . . . . . . . . . . . . . . . xiii
- Chapter 1: The FAQs of Life—The Scripts Every PHP Programmer Wants (or Needs) to Know . . . . . . . . . . . . . . . . . . . . . 1
- Chapter 2: Configuring PHP . . . . . . . . . . . . . . . . . . . . . . 19
- Chapter 3: PHP Security . . . . . . . . . . . . . . . . . . . . . . . . 33
- Chapter 4: Working with Forms . . . . . . . . . . . . . . . . . . . . . .45
- Chapter 5: Working with Text and HTML . . . . . . . . . . . . . . . . . . .59
- Chapter 6: Working with Dates . . . . . . . . . . . . . . . . . . . . . .81
- Chapter 7: Working with Files . . . . . . . . . . . . . . . . . . . . . .91
- Chapter 8: User and Session Tracking . . . . . . . . . . . . . . . . .103
- Chapter 9: Working with Email . . . . . . . . . . . . . . . . . . . . . .119
- Chapter 10: Working with Images . . . . . . . . . . . . . . . . . . . . .129
- Chapter 11: Using cURL to Interact with Web Services . . . . . . . . . . .141
- Chapter 12: Intermediate Projects . . . . . . . . . . . . . . . . . . . .155
- Appendix . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .183
- Index . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .185

## CONTENTS IN DETAIL

### INTRODUCTION xiii

### 1 THE FAQS OF LIFE—THE SCRIPTS EVERY PHP PROGRAMMER WANTS (OR NEEDS) TO KNOW 1

- #1: Including Another File as a Part of Your Script ........................................................................ 2
- What Can Go Wrong? .................................................................................................................... 3
- #2: Highlighting Alternate Row Colors in a Table ........................................................................ 4
- Hacking the Script ....................................................................................................................... 5
- #3: Creating Previous/Next Links ................................................................................................... 7
- Using the Script ........................................................................................................................ 10
- #4: Printing the Contents of an Array ........................................................................................... 11
- #5: Turning an Array into a Nonarray Variable That Can Be Restored Later .............................. 12
- What Can Go Wrong? .................................................................................................................... 12
- #6: Sorting Multidimensional Arrays ............................................................................................ 13
- Hacking the Script ....................................................................................................................... 14
- #7: Templating Your Site with Smarty ........................................................................................... 14
- Installing Smarty ......................................................................................................................... 14
- A Brief Smarty Tutorial ................................................................................................................ 15
- What Can Go Wrong? .................................................................................................................... 16
- Hacking the Script ....................................................................................................................... 17

### 2 CONFIGURING PHP 19

- Configuration Settings and the php.ini File .............................................................................. 20
- Locating Your php.ini File ........................................................................................................... 20
- #8: Revealing All of PHP’s Settings ............................................................................................ 21
- #9: Reading an Individual Setting ................................................................................................ 21
- #10: Error Reporting ...................................................................................................................... 22
- Common Error Messages .............................................................................................................. 23
- #11: Suppressing All Error Messages ............................................................................................ 24
- #12: Extending the Run Time of a Script ...................................................................................... 24
- What Can Go Wrong? .................................................................................................................... 25
- #13: Preventing Users from Uploading Large Files ........................................................................ 25
- #14: Turning Off Registered Global Variables .............................................................................. 25
- #15: Enabling Magic Quotes ......................................................................................................... 26
- What Can Go Wrong? .................................................................................................................... 26
- #16: Restricting the Files that PHP Can Access ............................................................................ 26
- What Can Go Wrong? .................................................................................................................... 27
- #17: Shutting Down Specific Functions ......................................................................................... 27
- #18: Adding Extensions to PHP ..................................................................................................... 27
- Adding PHP Extensions ................................................................................................................. 28
- Installing Extensions with a Web-Based Control Panel .............................................................. 29
- What Can Go Wrong? .................................................................................................................... 32
