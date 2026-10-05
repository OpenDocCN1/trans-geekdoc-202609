
Creating Applications for the 21st Century

Developer’s Library

![](img/005bb569dac79e0facc29f476bd67ade_0_0.png)

# Programming in Go

# Developer’s Library Series

![](img/005bb569dac79e0facc29f476bd67ade_2_0.png)
![](img/005bb569dac79e0facc29f476bd67ade_2_1.png)
![](img/005bb569dac79e0facc29f476bd67ade_2_2.png)
![](img/005bb569dac79e0facc29f476bd67ade_2_3.png)
![](img/005bb569dac79e0facc29f476bd67ade_2_4.png)

Visit **developers-library.com** for a complete list of available products

**The Developer’s Library Series** from Addison-Wesley provides practicing programmers with unique, high-quality references and tutorials on the latest programming languages and technologies they use in their daily work. All books in the Developer’s Library are written by expert technology practitioners who are exceptionally skilled at organizing and presenting information in a way that’s useful for other programmers.

Developer’s Library books cover a wide range of topics, from open-source programming languages and databases, Linux programming, Microsoft, and Java, to Web development, social networking platforms, Mac/iPhone programming, and Android programming.

# Programming in Go

Creating Applications for the 21st Century

Mark Summerfield

Addison-Wesley
Upper Saddle River, NJ · Boston · Indianapolis · San Francisco
New York · Toronto · Montreal · London · Munich · Paris · Madrid
Capetown · Sydney · Tokyo · Singapore · Mexico City

Many of the designations used by manufacturers and sellers to distinguish their products are claimed as trademarks. Where those designations appear in this book, and the publisher was aware of a trademark claim, the designations have been printed with initial capital letters or in all capitals.

The author and publisher have taken care in the preparation of this book, but make no expressed or implied warranty of any kind and assume no responsibility for errors or omissions. No liability is assumed for incidental or consequential damages in connection with or arising out of the use of information or programs contained herein.

The publisher offers excellent discounts on this book when ordered in quantity for use of bulk purchases or special sales, which may include electronic versions and/or custom covers and content particular to your business, training goals, marketing focus, and branding interests. For more information, please contact:

- U.S. Corporate and Government Sales
- (800) 382-3419
corpsales@pearsongroup.com

For sales outside the United States, please contact:

- International Sales
international@pearsonsed.com

Visit us on the Web: informit.com/aw

# Library of Congress Cataloging-in-Publication Data

Summerfield, Mark.

Programming in Go : creating applications for the 21st century / Mark Summerfield.

p. cm. Includes bibliographical references and index.

ISBN 978-0-321-77463-7 (pbk. : al. publisher) 2. Computer programming language 3. Application software—Development 1. Title.

QA76.73.G63S86 2012
005.13—dc23

2012001914

Copyright © 2012 Qtrac Ltd.

All rights reserved. Printed in the United States of America. This publication is protected by copyright, and permission must be obtained from the publisher prior to any reproduction, storage in a retrieval system, or transmission in any form or by means, electronic, mechanical, photocopying, recording, or likewise. To obtain permission to use material from this work, please submit a written request to Pearson Education, Inc., Permissions Department, Lake Street, Upper Saddle River, New Jersey 07458, or you may fax your request to (201) 236-3290.

ISBN-13: 978-0-321-77463-7
ISBN-10: 0-321-77463-9

Text printed in the United States on recycled paper at RR Donnelley in Crawfordville, Indiana.
First printing, April 2012

*This book is dedicated to*
**Jasmin Blanchette and Trenton Schulz**

This page intentionally left blank

# Contents at a Glance

- Tables | xv
- Introduction | 1
- Chapter 1. An Overview in Five Examples | 7
- Chapter 2. Booleans and Numbers | 51
- Chapter 3. Strings | 81
- Chapter 4. Collection Types | 139
- Chapter 5. Procedural Programming | 185
- Chapter 6. Object-Oriented Programming | 253
- Chapter 7. Concurrent Programming | 315
- Chapter 8. File Handling | 361
- Chapter 9. Packages | 407
- Appendix A. Epilogue | 435
- Appendix B. The Dangers of Software Patents | 437
- Appendix C. Selected Bibliography | 441
- Index | 443

www.qtrac.eu/gobook.html

This page intentionally left blank

# Contents

- Tables ..................................................................................................................................................... xv
Introduction ................................................................................................................................................ 1
Why Go? ..................................................................................................................................................................... 1
The Structure of the Book ................................................................................................ 4
Acknowledgments ........................................................................................................................ 5
Chapter 1. An Overview in Five Examples ................................................................ 7
1.1. Getting Going. ................................................................................................................................. 7
1.2. Editing, Compiling, and Running ................................................................ 9
1.3. Hello Who? ....................................................................................................................... 14
1.4. Big Digits—Two-Dimensional Slices ............................................................ 16
1.5. Stack—Custom Types with Methods ................................................................ 21
1.6. Americanise—Files, Maps, and Closures ................................................ 29
1.7. Polar to Cartesian—Concurrency ............................................................. 40
1.8. Exercise .......................................................................................................................... 48

- Chapter 2. Booleans and Numbers ................................................................... 51
2.1. Preliminaries ................................................................................................... 51
2.1.1. Constants and Variables .......................................................................... 53
2.1.1.1. Enumerations ............................................................................................ 54
2.2. Boolean Values and Expressions ................................................................ 56
2.3. Numeric Types ................................................................................................... 57
2.3.1. Integer Types ........................................................................................ 59
2.3.1.1. Big Integers ........................................................................................ 61
2.3.2. Floating-Point Types ........................................................................... 64
2.3.2.1. Complex Types ................................................................................. 70
2.4. Example: Statistics ............................................................ 72
2.4.1. Implementing Statistics ................................................................. 73
2.4.2. Implementing a Server ................................................................ 75
2.5. Exercises ................................................................................................. 78

# Chapter 3. Strings ................................................................................ 81
3.1. Literals, Operators, and Escapes ...................................................... 83
3.2. Comparing Strings ....................................................................... 86
3.3. Characters ................................................................................. 87
3.4. Indexing and Slicing Strings ................................................ 90
3.5. Formatting with the Fmt Package ................................... 93
3.5.1. Formatting Booleans ................................................................. 97
3.5.2. Formatting Integers ....................................................... 98
3.5.3. Formatting Characters ....................................................... 99
3.5.4. Formatting Floating-Point Numbers ................................. 100
3.5.5. Formatting Strings and Slices ........................................ 101
3.5.6. Formatting for Debugging ................................................. 103
3.6. Other String-Related Packages ................................... 106
3.6.1. The Strings Package ................................................ 107
3.6.2. The Strconv Package ........................................ 113
3.6.3. The Utf8 Package ................................................ 117
3.6.4. The Unicode Package ....................................... 118
3.6.5. The Regexp Package ........................................ 120
3.7. Example: M32pls ................................................... 130
3.8. Exercises ................................................................... 135

# Chapter 4. Collection Types ................................................. 139
4.1. Values, Pointers, and Reference Types ................................ 140
4.2. Arrays and Slices ....................................................... 148
4.2.1. Indexing and Slicing Slices ................................ 153
4.2.2. Iterating Slices ......................................... 154
4.2.3. Modifying Slices ....................................... 156
4.2.4. Sorting and Searching Slices ................... 160
4.3. Maps ................................................................... 164
4.3.1. Creating and Populating Maps ................... 166
4.3.2. Map Lookups ......................................... 168
4.3.3. Modifying Maps ....................................... 169
4.3.4. Key-Ordered Map Iteration ...................... 170
4.3.5. Map Inversion ......................................... 170
4.4. Examples ............................................................... 171
4.4.1. Example: Guess Separator ........................ 171
4.4.2. Example: Word Frequencies ................... 174
4.5. Exercises ................................................................... 180
