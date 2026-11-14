![](images/cover.jpg)

![Cover: Every Bit Counts: Posit Computing, Chapman & Hall/CRC Computational Science, written by John L. Gustafson, published by CRC Press, Taylor and Francis Group, Boca Raton, London, New York, CRC Press is an imprint of the Taylor and Francis Group, an informa business, a Chapman and Hall book.](images/cover.jpg)

# Chapman & Hall/CRC

**Computational Science Series**

***Series Editor: Horst Simon and Doug Kothe***

**Methods and Applications of Autonomous Experimentation**

*Daniela Ushizima, Marcus M. Noack*

**Data-Intensive Science**

Terence Critchlow, Kerstin Kleese van Dam

**Grid Computing**

Techniques and Applications

*Barry Wilkinson*

**Scientific Computing with Multicore and Accelerators**

*Jakub Kurzak, David A. Bader, Jack Dongarra*

**Introduction to the Simulation of Dynamics Using Simulink**

*Michael A. Gray*

**Introduction to Scheduling**

*Yves Robert, Frederic Vivien*

**Introduction to Modeling and Simulation with MATLAB^® and Python**

*Steven I. Gordon, Brian Guilfoos*

**Fundamentals of Multicore Software Development**

*Victor Pankratius, Ali-Reza Adl-Tabatabai, Walter Tichy*

**Programming for Hybrid Multi/Manycore MPP Systems**

*John Levesque, Aaron Vose*

**Exascale Scientific Applications**

Scalability and Performance Portability

*Tjerk P. Straatsma, Katerina B. Antypas, Timothy J. Williams*

**GPU Parallel Program Development Using CUDA**

*Tolga Soyata*

**Parallel Programming with Co-arrays**

*Robert W. Numrich*

**Contemporary High Performance Computing**

From Petascale toward Exascale, Volume 3

*Jeffrey S. Vetter*

**Unmatched**

50 Years of Supercomputing

*David Barkai*

*For more information about this series please visit:* [https://www.crcpress.com/Chapman--HallCRC-Computational-Science/book-series/CHCOMPUTSCI](https://www.crcpress.com/Chapman--HallCRC-Computational-Science/book-series/CHCOMPUTSCI)

Designed cover image: Sumei Chew

MATLAB® and Simulink® are trademarks of The MathWorks, Inc. and are used with permission. The MathWorks does not warrant the accuracy of the text or exercises in this book. This book's use or discussion of MATLAB® or Simulink® software or related products does not constitute endorsement or sponsorship by The MathWorks of a particular pedagogical approach or particular use of the MATLAB® and Simulink® software.

First edition published 2025

by CRC Press

2385 NW Executive Center Drive, Suite 320, Boca Raton FL 33431

and by CRC Press

4 Park Square, Milton Park, Abingdon, Oxon, OX14 4RN

*CRC Press is an imprint of Taylor & Francis Group, LLC*

© 2025 John L. Gustafson

Reasonable efforts have been made to publish reliable data and information, but the author and publisher cannot assume responsibility for the validity of all materials or the consequences of their use. The authors and publishers have attempted to trace the copyright holders of all material reproduced in this publication and apologize to copyright holders if permission to publish in this form has not been obtained. If any copyright material has not been acknowledged please write and let us know so we may rectify in any future reprint.

Except as permitted under U.S. Copyright Law, no part of this book may be reprinted, reproduced, transmitted, or utilized in any form by any electronic, mechanical, or other means, now known or hereafter invented, including photocopying, microfilming, and recording, or in any information storage or retrieval system, without written permission from the publishers.

For permission to photocopy or use material electronically from this work, access [www.copyright.com](https://www.copyright.com) or contact the Copyright Clearance Center, Inc. (CCC), 222 Rosewood Drive, Danvers, MA 01923, 978-750-8400. For works that are not available on CCC please contact [mpkbookspermissions@tandf.co.uk](mailto:mpkbookspermissions@tandf.co.uk)

*Trademark notice:* Product or corporate names may be trademarks or registered trademarks and are used only for identification and explanation without intent to infringe.

*Library of Congress Cataloging-in-Publication Data*

Names: Gustafson, John L., 1955-author.

Title: Every bit counts : posit computing / John L. Gustafson.

Description: First edition. | Boca Raton, FL : CRC Press, 2025. | Series: Chapman & Hall/CRC computational science | Includes bibliographical references and index. | Summary: “Written by one of the foremost experts in high-performance computing and the inventor of Gustafson's law, Every Bit Counts: Posit Computing explains the foundations of a new way for computers to calculate that saves time, storage, energy, and power by packing more information into every bit than do legacy approaches. Both the AI and HPC communities are increasingly using the posit approach that Gustafson introduced in 2017, which may be the future of technical computing. What may seem like a dry subject is made engaging by including the human and historical side of the struggle to represent numbers on machines. The book is richly illustrated in full color throughout, with every effort made to make the material as clear and accessible as possible, and even humorous. Starting with the simplest form of the idea, the chapters gradually add concepts according to stated mathematical and engineering design principles, building a robust tool kit for creating application-specific number systems. There is also a thorough explanation of the Posit Standard (2022), with motivations and examples that expand on that terse 12-page document”-- Provided by publisher.

Identifiers: LCCN 2024036235 (print) | LCCN 2024036236 (ebook) | ISBN 9781032738062 (hbk) | ISBN 9781032738055 (pbk) | ISBN 9781003466024 (ebk)

Subjects: LCSH: Computer science--Mathematics.

Classification: LCC QA76.9.M35 G84 2025 (print) | LCC QA76.9.M35 (ebook) | DDC 004.01/51--dc23/eng/20240910

LC record available at [https://lccn.loc.gov/2024036235](https://lccn.loc.gov/2024036235)

LC ebook record available at [https://lccn.loc.gov/2024036236](https://lccn.loc.gov/2024036236)

ISBN: 978-1-032-73806-2 (hbk)

ISBN: 978-1-032-73805-5 (pbk)

ISBN: 978-1-003-46602-4 (ebk)

DOI: [10.1201/9781003466024](https://doi.org/10.1201/9781003466024)

Typeset in Source Sans Pro

by KnowledgeWorks Global Ltd.

*Publisher's note:* This book has been prepared from camera-ready copy provided by the authors.

*For Nan Ripley,*

*who is definitely not a number.*

# Preface

![](images/pgxv_1.jpg)

In 1920, a chemist might write a scientific paper with language like this:

By around 1960, the wording would be more like this:

In the present day, I would not be surprised to see it written like this:

Technical writing seems to have acquired a style designed not so much to communicate to you as to impress you with how intelligent the author is. This is not that kind of book. Einstein once said, “You do not really understand something unless you can explain it to your grandmother.” So I wrote this book with that in mind and tested it. I had a grandmother (not mine) with no math training read it, and it passed. She totally gets it. (Thank you, Ms. Levitt!)

Even though this is a book about computer arithmetic, it is aimed at a general audience. It presents the human side of things using the historical record along with my own personal experiences. You do not need calculus or anything more advanced than a K-12 math background to read this book. I have done everything in my power to make this very dry subject as clear and interesting as possible. And sometimes funny. Borderline outrageous.

The publisher has generously consented to the use of four-color printing on every page. Perhaps the hardest thing is all the binary numbers, which even computer science majors struggle to read. Color-coding the 0 and 1 bits in long bit strings makes them much easier to figure out. Most people are visual learners, and I spent more than half the time creating this book in crafting the illustrations that explain the concepts. Text backgrounds also are color-coded as guideposts to inform you of when there is math, computer code, important points, pitfalls, and so on.

There is at least one Exercise for the Reader in every chapter, for those who are ambitious. If you do not attempt them, you still might want to read the Answers to Exercises section because there is new material there that is not found elsewhere in the book.

There are no footnotes, end notes, or even References. Modern web search has made it so easy to find a source from the author's name and subject that a References section seems obsolete. There is also no “Theorem-Proof” structure. The opposite approach has been used, that of building up to an idea one step at a time, even allowing you to see mistakes made along the way. I speak from experience when I say that mathematicians will hate this book and its informal style. “Where are the Greek letters? Where is the cryptic notation? I feel like you are talking down to me.” They are certainly entitled to their opinion.

# Acknowledgments

![The governments of the US and Singapore, my two favorite nations, made this book possible.](images/pgxvii_1.jpg)

The governments of the US and Singapore, my two favorite nations, made this book possible.

Three people stand out as having enabled the research that led to the discovery of posit format and thus the contents of this book:

*   Dr. Marek Michalewicz, former Director of Singapore's A\*STAR Computational Resource Centre (A\*CRC),
    
*   Professor Tin Wee Tan, Director of the Singapore National Supercomputing Centre (NSCC), and
    
*   Professor Weng-Fai Wong of the National University of Singapore's School of Computing.
    

After seeing the potential in my earlier efforts to find something better than floating-point arithmetic, they set up an incredible arrangement for me to move to Singapore and continue the research. Professor Wong also let me co-advise his two brilliant graduate students, Elavarasi Manogaran and Himeshi De Silva, who did hundreds of hours of experimental computational studies that steered the choices made in the design of posit arithmetic.

I am also at a loss to express my gratitude for those who reviewed my drafts and provided detailed (and much-needed) feedback. Hauke Rehr, besides being a crack mathematician with a sharp sense of correctness, has a seemingly superhuman ability to tell when a comma is in a font one point size too small, that sort of thing. Laslo Hunhold not only provided great feedback, but he advanced the state of the art with his own “takum” format in time for it to be included in the final chapter. My daughter, Janice Marquardt, was of immense help spotting things no other reviewer noticed.

The creation of posit format was triggered by a request from MIT's Kurt Keville, who told me in November 2016 that the RISC-V committee wanted a real number format that wasn't IEEE Std 754, and asked me to design one for them. After three weeks of struggling with modifications to Type II unums, I made the hardware-friendly break-through on December 3. I am also grateful to Kurt for detailed feedback for the draft of this book. Like my Singapore supporters, he is another *raison d'être* for the posit arithmetic format.

Dr. Siew Hoon (Cerlane) Leong of NSCC led the development of the SoftPosit library, the establishment of the [posithub.org](http://posithub.org) website, and the establishment of the Conference on Next-Generation Arithmetic (CoNGA) series. She also helped make many key decisions in the *Posit Standard (2022)*, including how the quire should handle exceptions. I do not know how I could have established a beachhead for the posit format without her boundless energy and keen eye for what needs to be done.

The cover artwork was done by a remarkable and multitalented Singapore artist, Sumei Chew. Without being a mathematician, she managed to capture the sense of wonder and genuine fun that exists in mathematics and that I hope readers will find in this book. She was a great friend to me during my years in Singapore and made my experience even better than it already was.

To my surprise and delight, cartoonist Sidney Harris allowed me to use his excellent cartoons that you will find scattered throughout the book. It is remarkable how perfectly many of his punchlines line up with the topic of the section where they appear. For a cartoonist, he somehow seems to know an awful lot about how scientists act when they're next to blackboards. Thank you, Sidney.

# How to Read this Book

When jargon is introduced (some of it industry-wide and some of it coined in this book), the first use is explained in a light-cyan **Definition** box, like this:

If you forget a definition, check the Glossary (pages 353–361).

When someone else's writing or historical work is being cited, it is displayed in a parchment-colored box, like this:

A light red background color is used to signal the reader that something is mathematical, like

It is usually possible to skip over those formula displays without losing the flow of the main body text.

Similarly, you can usually skip over computer code, unless you're interested. It has a light green background. There are two kinds of computer code; one is something like C or C++ to show how something might be programmed in general, like this:

```
unsigned reverse (unsigned x) {
      x = ((x & 0 x55555555) << 1) | ((x >> 1) & 0 x55555555);
      x = ((x & 0 x33333333) << 2) | ((x >> 2) & 0 x33333333);
      x = ((x & 0 x0F0F0F0F) << 4) | ((x >> 4) & 0 x0F0F0F0F);
      x = (x << 24) | ((x & 0 xFF00) << 8) |
              ((x >> 8) & 0 xFF00) | (x >> 24);
      return x;
 }
```

The other kind is live code that actually executes. This book was not created with a word processing program or LATEX; this entire book is a computer program written in *Mathematica*. For example, this code

```
morris8 = Union[morris8];
Print[“morris8 has ”, Length[morris8], “ unique numbers.”]
```

morris8 has 144 unique numbers

actually executes; it generates what follows in the text. The input commands to *Mathematica* are in boldface **Courier**, a typewriter-like typeface, and the text output is in regular Courier, not bold. Sometimes the output is graphical.

Single-letter variables are concise, but sometimes longer names are better reminders of what is being represented. Words or shortened words in phrases are concatenated, with capital letters informing you about where a new word begins, a system called CamelCase. There is also lower-case camelCase where the first letter is always lower-case, and that is what is used in coining variable names like *maxPos* (for maximum posit value) and *eS* (for exponent size). Reserved words in *Mathematica* use CamelCase, so by using lower-case camelCase there is no chance of colliding with a reserved word.

While the purpose of this book is certainly not to teach *Mathematica*, it is helpful to understand that everything is computed with symbolic mathematics until you ask for it to be turned into a number with the **N****\[**…\] command, like this:

```
Print[π]
Print[N[π]]
Print[N[π, 16]]
```

```
π
3.14159 2654
3.14159 26535 89793
```

Boldfaced **Courier** font is used to display binary numbers like **0101101**. Decimal numbers are left in the same font as the main text, like 1000.

Boxed text with this light blue background is important, not to be skipped:

In contrast, boxed text with a light yellow background is a warning that the text expresses a bad or fallacious idea, even if the idea seems reasonable at first glance:

Finally, text highlighted with a gray background is an **Exercise for the Reader**, like this one:

If you choose not to try the Exercises, Answers to Exercises is still worth reading since it contains ideas that are not in the main text.

# 1 The Posit Number Format

## 1.1 The Essence of the Idea

![Whatever x turns out to be, there is a way to represent it on a computer using only three bits.](images/pg1_1.jpg)

Whatever *x* turns out to be, there is a way to represent it on a computer using only three bits.

Most books about mathematical ideas build up a foundation of definitions and make the reader wait to see where it is all going. Instead, this first chapter will get you to the punchline in as few pages as possible. Later, we can look at the underlying details and reasons for why the thing works the way it does.

Here is a common misconception:

Suppose a computer uses three bits to represent numbers. There are eight possible bit patterns, and if we treat them as normal base-2 *unsigned* integers, their meanings on any conventional modern computer would be as follows:

![](images/pg2_1.jpg)

That is all you get. You can count from zero to seven with three bits, adding **1** to the last bit and propagating any carry bits, just like in grade school addition but with base-two (binary) instead of base-ten (decimal). If you try to add 1 to the representation of seven, **111**, you get overflow because you cannot store the carry bit **1000** so it wraps back to zero, **000**.

When computers need *signed* integers, the most commonly-used system is that the numbers flip from positive to negative as soon as the leftmost bit hits **1**, and then they count upward back to zero, like this:

![](images/pg2_2.jpg)

The leftmost bit (the most significant bit, or MSB) quickly informs us if a number is negative, so it is often called the *sign bit*, and the convention here is to color it **red** since accountants have used that color to indicate negative amounts of money for so long that “being in the red” is a synonym for being in debt.

The unsigned integers overflow if you count up from **111**, but the signed integers overflow if you count up from **0****11**, so it is a matter of where you put the discontinuity. If you count up from negative one, **1****11**, you ignore the carry bit overflow and get **0****00**, so the system automatically does the right thing.

*However*: Suppose you instead assigned the following meanings to the bit patterns:

 
| **00****0** || 0 |
| --- | --- |
| **0****0****1** || Real *x* such that 0 < *x* < 1 |
| **0****1****0** || 1 |
| **0****1****1** || Real *x* such that 1 < *x* < ∞ |
| **100** || Anything that is not a real |
| **1****01** || Real *x* such that -∞ < *x* < -1 |
| **1****1****0** || \-1 |
| **1****1****1** || Real *x* such that -1 < *x* < 0 |

That covers the entire real number line, -∞ < *x* < ∞, and if *x* is not even a real number, it provides a way to represent that as well. We abbreviate that as NaR for “Not a Real” and it includes forms of infinity, indeterminate forms like $\\frac{0}{0},$ complex numbers like $\\sqrt{- 1},$ and even things that are not numbers at all, like if a computer programmer tries to convert the character string “zebra” into this number format. It is *not a real*.

It is not a very precise system, but it *does* provide a unique representation for every *x*.

The rightmost bit (least-significant bit, or LSB) is color-coded **magenta** and is called the *ubit* (short for **u**ncertainty **bit**, which rhymes with cubit). Exact numbers are represented with bit strings that end in **0**. Bit strings that end in a **1** mean the *open interval* between exact values (or between an exact value and ±∞). The open interval between *a* and *b* is written (*a, b*). Like, $\\sqrt{2}$ and π are both represented by **0****1****1** since they satisfy 1 < *x* < ∞. The ubit is the fundamental idea underlying *unum* arithmetic, where *unum* is a shortening of “**u**niversal **num**ber.” For that reason, it is pronounced “yoo-num” and not Latin “oo-num” as in *E Pluribus Unum*.

Including the ubit is exactly like writing $\\sqrt{2} = 1.414$ ⋯ where the “⋯” means, “There are more nonzero digits after the last one shown: 1.414 <$\\sqrt{2}$ < 1.415.” That is mathematically true. If you say $\\sqrt{2}$ = 1.414, you are making an error just the same as you would be making an error to say 2 + 2 = 5. The presence or absence of the “⋯” takes only one bit to represent, and that is the ubit, just like the sign of a number takes only one bit to represent.

Notice that we do not color-code the sign bit for **00****0**, as a reminder that zero has no sign. We also do not code it for the **100** = NaR exception since exceptions are also unsigned. Nor do we color-code the ubit of NaR since it makes no sense to regard “Not a Real” as an exact quantity.

Notice that the unums map to a ring, because just as with the signed integer format, **1****1****1** being right next to **000** makes perfect sense. The real values and NaR are shown in **violet** on the outside of the ring, with the bit strings shown on the inside.

![This unum ring plot shows the entire real number line mapped to only three bits.](images/pg4_1.jpg)

This unum *ring plot* shows the entire real number line mapped to only three bits.

There is a concept called the *projective reals*, which means thinking of the real number line as a projection of a circle onto a line, with the source of light at the top of the circle:

![The projective reals concept maps the infinite line to a finite circle.](images/pg4_2.jpg)

The *projective reals* concept maps the infinite line to a finite circle.

I have added two things to this very old concept. First is the observation that signed integers map elegantly to the circle in the same way, flipping sign at the top of the circle. The second is that placing −1 and 1 at the east and west points on the circle allows symmetry about the horizontal axis when we take the *reciprocal* of a number.

To save space, (*a, b*) means the open interval *a* < *x* < *b*. The three-bit system has a *vocabulary* of eight items: {NaR, (−∞, –1), –1, (–1, 0), 0, (0, 1), 1, (1, ∞)}. As an ordered set, we treat NaR as if it were −∞, less than all the other items, though it also serves as the dumping ground for anything else that is not a real number.

We can do arithmetic on both the exact numbers and the ranges. For instance, the square of the interval (0, 1) is exactly the same set of values, (0, 1). That may not seem like a big deal, but it actually means that this system is more powerful than what any calculator can do. Try entering a number between 0 and 1 into a calculator app (or a real calculator, which at this point is something of an antique) and square it. Square the result. Keep doing that over and over, and eventually one of two things will happen: The display will erroneously say the result is exactly 0, or it will say it is “Not a number.” I tried it just now on my laptop, and got the second case.

![](images/pg5_1.jpg)

The software for the calculator app is certainly using a lot more than three bits. Yet it cannot produce a mathematically correct answer to “What is the square of 1e–50?” because the power-of-ten notation only has two digits so it goes as small as 1e–99 (that is, 10^(\-99)). The calculator is saying that 10^(\-100) is “Not a number”; I beg to differ.

Here is another example that does not involve underflow or overflow. Enter 2 and take the square root. Apply the square root button over and over and you get closer and closer to 1.

After entering 2 and pressing the square root 49 times, I see this result:

![](images/pg6_1.jpg)

I took the square root one more time, and it did not change, which is interesting. It has some “guard digits” and knows more about the answer than it shows on the display. But take the square root yet one more time, and I get this:

![](images/pg6_2.jpg)

The display shows exactly 1. But that *is not true*.

What would the three-bit system do? The square root of (1, ∞) is the same set of real numbers, (1, ∞). You can take the square root of (1, ∞) as many times as you like and it will never produce the mathematically incorrect result 1.

## 1.2 Raising the Precision

If we use four bits instead of three, we can now insert exact values between the ones we had before. There are many possible value choices, but here is a logical one:

![Appending a bit to the unum ring plot shows how specificity increases for the open intervals.](images/pg7_1.jpg)

Appending a bit to the unum ring plot shows how specificity increases for the open intervals.

Insert ½ between 0 and 1, and reflect that to the negative side. But we can also reflect about the *horizontal* axis by taking the reciprocal, so 2 goes between 1 and ∞. Notice that reciprocation also works for the open intervals, too. The one exception is that while the reciprocal of 0 is NaR, the reciprocal of NaR should stay NaR. Once you land on an invalid or indeterminate result, it is vital that NaR is preserved under every operation, so that it shows up in the final result to alert that things went awry.

In most number systems, negation is perfect, so once you have a way to add *a* and *b*, you also have a way to subtract *b* from *a*, by computing *a* × ( − *b*). With the system shown above, once you have a way to multiply *a* and *b*, you also have a way to divide *a* by *b*, by computing $a + (\\frac{1}{b}).$ That does the right thing if *b* is NaR, because $\\frac{1}{b}$ is also NaR and anything multiplied by NaR is NaR, preserving the information that something went wrong in the computation.

How do you negate a signed binary integer? The rule is this: *Flip all the bits and add 1, and ignore any overflow*. For example, if the integers are of size eight bits, the integer 5 in binary is

```
00000101.
```

Flip all the bits to get

```
11111010.
```

Then add 1 and we are done. For 8-bit signed integers, this is the bit pattern for -5:

```
11111011
```

The only case where you get carry overflow is if you try to negate zero. For example, **00000000** flips to **11111111**, and adding 1 to that should be **100000000** (nine bits), but you only have eight bits so the leftmost bit is discarded. This is why zero has no sign; if you try to negate zero this way, you get back zero.

NaR has the same lack of sign, and the same charming property: In the ring, treat the four-bit values as integers so NaR is **1000**. Flip the bits to **0111**, add 1 to get **1000**, and you are back to NaR.

To “flip about the vertical axis” to turn *x* into -*x*, treat the bit string as a signed integer and negate it. To “flip about the horizontal axis” to turn *x* into $\\frac{1}{x},$ ignore the sign bit and negate the other bits (that is, flip them and add 1). If there is a carry, do a logical OR with the sign bit. That way, zero = **0000** reciprocates to NaR = **1000**. The rule also turns NaR back into NaR, so there are no exception cases.

The reason we should care about minimizing exception cases is that exception cases make hardware for computer arithmetic wasteful and messy (and slower), and harder to prove correct in all cases.

## 1.3 Rigor or Guesswork? The Tough Decision

![“Perfect is the enemy of good.” — Voltaire](images/pg9_1.jpg)

“Perfect is the enemy of good.” — Voltaire

This brings us to a difficult choice. For a system that lets us work with real numbers on computers, we can continue refining this *perfect* system of exact numbers and open ranges between exact numbers, or we can settle for a *good* system where there are only exact numbers and we round every real number to one of them, creating and accumulating mathematical errors in doing so.

This is a battle between two schools of thought, one that sometimes resembles a religious war. The “good enough” system came first in computing, which is to represent real numbers in imitation of scientific notation, like 6.022 × 10^(23) where we have some fixed amount of storage for a digit followed by a fraction, times a number base raised to a power. The amount of storage for the power is also fixed. The digit-fraction part can be negative, zero, or positive, and so can the exponent. A number represented by such a format is called a *floating-point number*, or “float,” for short. Unlike integer computations, which are exact so long as you stay within the representable range, float computations are almost always inexact. But users find them “good enough” for many things we want to do with computers. Usually.

The term *interval arithmetic* is used for an approach introduced some sixty years ago where all quantities are treated as closed sets of real numbers \[*a, b*\], that is, real *x* such that *a* ≤ *x* ≤ *b*. Exact values are expressed as \[*a, a*\]. The endpoints are expressed with floats, and in doing arithmetic, the rule is always to rigorously *bound* the result and hope that the bound is tight enough to have practical value.

If you had a choice between using a computer to get mathematically correct answers as opposed to guessing its way through a calculation and *probably* being good enough, who would ever pick the latter? The answer is: *Almost everybody*. In the marketplace of ideas, approximate arithmetic with rounding errors has beaten out interval arithmetic. The main reason is that unless you *really* know what you are doing, using intervals in a computation may produce something like \[-∞, ∞\] for the result. The set of experts who know how to stop interval bounds from becoming ridiculously conservative (much wider than they should be) is not a large group, but it is a zealous one that sometimes argues for rigorous computing with the passion of a tent revivalist minister. In all the technical computing that gets done in the world, I would be surprised if the amount done with interval arithmetic is more than one percent.

For that reason, most of this book is going to do something that resembles what floats do and assume that we *round* after performing arithmetic on the quantities. But they will use the projective reals framework described above and *not* be floats. What should we call them? My first thought was to call them a *guess*, since rounded quantities are a way of guessing your way through a computation. However, “guess” can be pejorative, so let's use a more optimistic term: *posit*. When used as a noun, it is defined as follows:

## 1.4 The Posit Format

With that justification, we now replace the open intervals in the ring plot with exact values, so that the last bit is no longer a ubit. No more magenta **0** or **1** bits at the end, but we introduce two new bit colors, **gold** and **brown** for reasons explained below. We also go back to color-coding the sign bit of 0 and NaR, because it turns out we can eliminate regarding them as “exceptions.”

Here is a ring plot for 4-bit posits:

![The posit ring plot replaces open intervals with a single point in the interval.](images/pg11_1.jpg)

The posit ring plot replaces open intervals with a single point in the interval.

The “in-between” rules are as follows when the last bit is a **1**, where we used to have an open interval:

*   Between NaR and a real number, insert twice the real number.
    
*   Between 0 and a real number, insert half the real number.
    
*   Otherwise, between *x* and *y*, insert their average, (*x* + *y*)/2.
    

For example, between 2 and NaR, we insert 4, by the first rule. Between −½ and 0, we insert $- \\frac{1}{4},$ by the second rule. And between ½ and 1, we insert ¾, by the last rule. Notice how this set of rules keeps the largest magnitude numbers the exact reciprocals of the smallest magnitude numbers.

The “Flip to Reciprocate” part of the diagram is removed because it is not true when the number is not a power of 2. The reciprocal of ³⁄4 = 0.75 is ⁴⁄3= 1.33 ⋯, but the mirror image in the ring is ³⁄2 = 1.5 instead. There is a way to fix that, but it can make the computer hardware more complicated, and that idea will be shown later.

## 1.5 The Regime

![Steel wool grades getting finer and shirt sizes getting larger resemble regime notation.](images/pg12_1.jpg)

Steel wool grades getting finer and shirt sizes getting larger resemble *regime* notation.

The *regime* of a posit is the bits that follow the sign bit that are identical, shown in **gold**, until they hit the opposite bit, shown in **brown**.

For the four-bit posits, their meaning as an integer *r* is as follows (sign bit not shown):

 
| regime || *r* |
| --- | --- |
| **000** || −∞ |
| --- | --- |
| **00****1** || −2 |
| **0****1**. || −1 |
| **1****0**. || 0 |
| **11****0** || 1 |
| **111** || 2 |

The regime value *r* is determined by the number of identical bits in a row, *k*, before hitting an opposite bit, if it occurs in the stored bits. You see, all bits after the last bit in a posit are implied **0** bits. Just like when you say a number is 1.53, with no other information, you have to treat it as meaning 1.5300000000⋯. So, if the regime bits are **111** which means they go all the way to the last bit, the implied bits that lie beyond are all **0** bits; call them *ghost bits*. The very next ghost bit is a **0** that serves as the stop bit for the run of **1** bits.

What if the regime is **000**, going all the way to the end without an opposite bit to end the run? Then it represents an *infinitely small integer*, –∞, because it never reaches its opposite bit and is an infinite string of **0** bits.

If there are *k* identical bits in a row, the value of *r* is

Remember the rule for negating an integer, where you flip all the bits and add one to the LSB? It works for the regime notation as well, but in a completely different way. Like, if you negate regime **11****0** = 1, flip bits to **00****1**, add 1 but read the result as a regime **0****1** **·** where the “**·**” bit is not part of the regime since it is after the opposite bit. Or try negating regime **1****0** **·** = 0. Flip the regime bits to **0****1** **·** and add 1 to the last bit of the regime (which is the second bit, not the third), and you get back **1****0** **·**, that is, 0 in regime notation. Similarly, if you try to negate the regime for -∞, you get back the same bit pattern, so -∞ acts exactly like NaR. It is “the point at infinity.”

Regime notation works a lot like clothing sizes: L, XL, XXL, XXXL for large, extra-large, and so on. Or for small sizes, sizes 0, 00, and 000 indicate smaller and smaller clothing sizes.

The “.” bits after the opposite bit are *fraction bits* representing the fraction *f*. There is an implied radix point “.” after the last bit of the regime. So far, we only have the possibility of one fraction bit, and in binary, **.0** means *f* = 0 and **.1** in binary means *f* =½. “But what if there aren't any fraction bits?” you might ask. The answer is, “There are *always* fraction bits. If they are beyond the end of the number, they all have value **0**.” And there is nothing wrong with having a fraction value of *f* = 0.

The value of the sign bit is *s*, that is, 0 if the sign bit is **0** and 1 if the sign bit is **1**. We can now give the formula for the value *x* represented by a posit from its bit string:

Let's practice by decoding **1****0****1****1**. The sign bit is **1**, so *s* = 1. The regime is **0****1**, so *k* is one bit in a row and *r* = -1. The fraction has one bit showing (a **.1** followed by an implied infinite string of **0** bits) so *f* =½. Apply the formula:

But does the formula work for the case of *x* = 0? Surprisingly, it does. The bit string is **0****000**, so *s* = 0, *r* = -∞, and *f* = 0. The formula simplifies to 1 × 2^(\-∞), which is 0.

What happens for NaR, though? Its bit string **1****000** means *s* = 1, *r* = −∞, and *f* = 0. The formula simplifies to (−1) × 2^∞ = −∞. That is certainly not a real. We simply make the rule that −∞ is our stand-in for anything that is not a real, not just −∞.

That really is the punchline of this chapter, and it works for any posit precision. A 1-bit posit is possible, but all it can represent is 0 or NaR.

As a taste of what is to come, let's take the format out for a spin, with 16-bit posits. What is the largest and smallest magnitude posit values we can represent with the same number of bits? Call those extremes *maxPos* and *minPos. maxPos* is **0****111111111111111** with *k* = fifteen **1** bits in a row, so *r* = 14; *maxPos* = 2^(14) ≈ 1.6 × 10⁴. Reciprocation is perfect; *minPos* is **0****000000000000001** with *k* = fourteen **0** bits in a row, so *r* = -14 and *minPos* = 2^(\-14) ≈ 6 × 10^(\-5). More than 8 orders of magnitude.

If you decode **0****11****0****100100100010** you get the rational number $\\frac{3217}{1024} \\approx 3.1416,$ that is, *π* accurate to about five decimal places. To put this in perspective, the closest that IEEE Standard 16-bit floats can get to π is $\\frac{201}{64} = 3.140625,$ with only about three decimals of accuracy. This is a small sampling of the advantages of the posit format.

If we are going to be examining and comparing *error* and *accuracy*, we had better do so with careful thinking and clarity. That is the subject of [Chapter 2](#chapter2.xhtml).

# 2 Inaccuracy Done Right

![This did not actually happen. It is a computer-generated image.](images/pg15_1.jpg)

This did not actually happen. It is a computer-generated image.

## 2.1 Absolute versus Relative Error

Like so many things in numerical analysis, we have become accustomed to some concepts that are widely accepted but are actually rather sloppy in their logic. The way we measure *error* of various types is one of those concepts. For instance, here is a widely-used way of measuring the error of a result computed with real numbers:

There is nothing wrong with this; if the values are identical, their difference is 0 so there is no error. Absolute error is what to use when someone lies about their age, say, or how fast they were driving, or how many glasses of wine they have had. But if a calculation produces 315 instead of 314, doesn't the error look very similar to returning 3.15 instead of 3.14? A number system designed for *real* numbers usually spans a large dynamic range. Simply subtracting numbers may be the best measure when the values being compared are within an order of magnitude of one another.

For situations with many orders of magnitude, the *relative error* of a computed value is traditionally defined this way:

There are some reasons you should be dissatisfied with this definition. If you compute −1 when the correct answer is 100, then the above relative error formula would only be 1.01. If you do not even know the sign of a number, then you know essentially nothing about the answer since the sign is the most significant part of a number. An error formula should return “indeterminate” in such cases. Even declaring the relative error to be infinite is too flattering.

If you did an experimental measurement that produced two different values *x*[1] and *x*[2], you might want to talk about the relative error in the measurement. But you do not know the *x*[exact] value. Depending on whether you put *x*[1] or *x*[2] in the denominator, you get a different relative error. That does not seem right.

For another, the formula is quite different for numbers and their inverses. Suppose *x*[computed] = 0.001 but *x*[exact] = 0.0001. Then the relative error is 9. But if we were instead computing the reciprocals of the numbers, the relative error would take *x*[computed] = 1000 and *x*[exact] = 10 000 as inputs, and the above formula would reassure us that the relative error is only 0.9. It makes no sense that an answer can be made to look ten times more accurate simply by taking reciprocals. If you knew a wavelength with a relative error of 0.1, would it not bother you to know the frequency (inversely related to wavelength) of the same component with a relative error of 0.2? These problems go away if instead of taking the differences between two numbers, we take the difference of the *logarithm* of the two numbers.

## 2.2 Three Types of Logarithms

Engineers who work with signals that have a wide dynamic range (like sound) have long had a solution when comparing numbers with ratios, which is to use *decibels*. A ratio of 10 is 10 decibels (10 dB), also known as a *bel*, though that word is not used very often. A ratio of 1 dB means the ratio is 10^(1/10) = 1.2589 ⋯. Decibels measure the difference of the logarithms (base 10) of two (positive) quantities *x*[1] and *x*[2], which is the same as the logarithm of their ratio:

The absolute value makes *x*[1] and *x*[2] interchangeable. Hence, it can be used to measure experimental errors. Also, it produces the same result whether you use *x*[1] and *x*[2] as inputs, or 1 / *x*[1] and 1 / *x*[2]. So *that* looks like a mathematically sound definition. But if *x*[exact] is 100, say, and we compute *x* = 110, the error is about 4 dB, which looks nothing like the traditional relative error value of 0.1. Can we have it both ways, with the elegance of logarithms of ratios but also something that resembles traditional relative error?

There are three types of logarithms we will be using here. Base 10 logarithms are good for human understandability since we tend to think in powers of 10 like hundreds, thousands, billions, etc. Computer scientists tend to use base 2 logarithms more than any other type, so much so that a base 2 logarithm has its own abbreviation: log[2](*x*) is often written as lg(*x*). For example, if told that “The memory address space is 4096 items,” then a computer scientist immediately infers that there are lg(4096) = lg(2^(12)) = 12 bits in the address.

A third kind, *natural logarithms*, uses *e* = 2.71828 ⋯ as the base because that base simplifies expressions that arise in higher math. It also has its own abbreviation: log*e*(*x*) = ln(*x*). Here are graphs of those three kinds of logarithm:

![log2 is computer-friendly, loge is math-friendly, and log10 is human-friendly.](images/pg17_1.jpg)

log[2] is computer-friendly, log*e* is math-friendly, and log[10] is human-friendly.

The decibel-type approach would work with any base logarithm, because log(*a*) − log(*b*) = log(*a* / *b*) for any kind of logarithm. There is a subtle reason for choosing the *natural logarithm* base *e* = 2.718 ⋯ instead of base 10 to measure relative error: as an error becomes small, natural log error becomes close to traditional relative error. As the figure shows, the slope of ln(*x*) near *x* = 1 is 1.

The log definition meets the other requirements of being immune to measuring inverses or interchanging the two values. So, here is the definition we will use:

Suppose the exact answer is 3.00 but we compute 3.03; the traditional relative error is $\\frac{0.03}{3.00} = 0.01$but the formula above is $\\ln(\\frac{3.03}{3}) = 0.00995$ ⋯ which is very close, so this means traditionalists should not be too unhappy with the updated definition. We have Peter Lindstrom to thank for this perceptive observation.

What if *x*[exact] is zero? Unless *x*[computed] is also zero, the relative error is ∞, which makes some people very uncomfortable because it certainly seems like a computed value like 0.000001 should get credit for *some* resemblance to zero. Sorry, but no. In the world of real numbers, the log of zero is infinitely far from the log of any nonzero value, just as the log of infinity is infinitely far from the log of any finite value. There is a human tendency to mentally flip back to wanting absolute error when thinking about the relative accuracy of very small values; resist that tendency, because it can land you in trouble.

What if *x*[computed] does not even have the right *sign*? Then the relative error is NaR. Literally. The formula takes the log of a negative number, which is a complex number and Not-a-Real. Otherwise, we have the desired symmetry and **relErr**(*x, y*) = **relErr**(*y, x*) = **relErr**$(\\frac{1}{x},\\frac{1}{y}).$

Usually, we care about the amount of error and not whether it is too low or too high. If we leave out the absolute value |…| in the expressions, we get *signed relative error*. The graph on the next page shows signed traditional relative error, traditional relative error of the reciprocals, and the natural log relative error used here:

![The ln(x/xexact) relative error is between the traditional and traditional reciprocal relative error.](images/pg19_1.jpg)

The ln(*x/x*[exact]) relative error is between the traditional and traditional reciprocal relative error.

The | ln(*x/x*[exact])| case is “inaccuracy done right,” a definition that has mathematical self-consistency but also bears a close resemblance to the traditional definition of relative error when the amount of error is small.

## 2.3 Accuracy as the Inverse of Error

That is, the more tightly we can provably bound what a result can be numerically, the more knowledge we have about its true value.

Similarly, *accuracy* is the inverse of relative error, and we already use this when we say, “The answer is accurate to five decimals.” If the relative error is about 0.001, then we know the answer to about 3 decimals; if the relative error is 0.0000001, then we know the answer to 7 decimals. Mathematically:

A computer scientist or numerical analyst might sometimes want to know, instead, the number of *bits* to which an answer is correct. That is easy. Just use logarithms base 2 instead of base 10 to find *binary accuracy*. Or compute the decimal accuracy and multiply by log[2](10) = 3.32…, to get the same thing.

It looks peculiar to have expressions that mix two different logarithm types, but the natural log makes traditional relative error resemble our ratio-based relative error. Then, the log of *that* shows the accuracy in a form suited for humans (log base 10) or for computers (log base 2).

[Appendix A](#appA.xhtml#appA) has the code for a *Mathematica* function, **decAcc**\[*x, y*\], based on the above definition of decimal accuracy. Let's try it on approximations to π:

```
decAcc[3.14, π]
decAcc[3.1416, π]
decAcc[π, π]
```

```
3.29491844
5.63107 5206
∞
```

That is *π* accurate to about three decimals, about five decimals, and infinitely accurate. *Mathematica* uses symbolic methods, so π can be written exactly.

## 2.4 The Accuracy of a *Number System*

Now that we have a definition of accuracy, we can also analyze the accuracy of a number system. Suppose we are using 8-bit posits, as described in [Chapter 1](#chapter1.xhtml). We only need to consider the accuracy of non-negative values, since accuracy of negative representations is the same. Here are all 128 non-negative 8-bit posits, shown on a ring plot. Call the values they represent the **posit8** set.

To make the figure easier to read, the radial lines indicate changes in the regime value, which occur at integer powers of 2. Notice that half the values are between 0.5 and 2, where the spacing is closest, so accuracy is highest.

![The right half of an 8-bit posit ring plot. The radial lines indicate regime changes.](images/pg21_1.jpg)

The right half of an 8-bit posit ring plot. The radial lines indicate regime changes.

The rule for rounding can be summarized as “round a real *x* to the nearest posit; if two posits are equally near, choose the one ending in a **0** bit.” There are some important additional details, but it will serve for now. Let's first study three consecutive values in the **posit8** set: {7.5, 8, 10}. The tie point between 7.5 and 8 is 7.75. The tie point between 8 and 10 is 9.

If we happen to compute a value that is exactly 7.5, 8, or 10, then the accuracy is infinite. Between those exactly-representable values, accuracy dips to a minimum at the tie point.

![The peaks actually go to infinity, since accuracy is infinite at exact points 7.5, 8.0, and 10.0.](images/pg22_1.jpg)

The peaks actually go to infinity, since accuracy is infinite at exact points 7.5, 8.0, and 10.0.

Notice the slight discontinuity at the two minima. That is caused by the difference between the *geometric* mean of two values *x* and *y*, $\\sqrt{x \\cdot y},$ and the *arithmetic* mean, (*x* + *y*)/ 2. The discontinuities are at the halfway points, but those are *not* the places where the decimal error (defined as a logarithmic distance) is minimized. The minimum error would happen at the geometric means, $\\sqrt{7.5 \\times 8} = 7.7459669\\cdots$and $\\sqrt{8 \\times 10} = 8.944\\cdots$instead of the arithmetic means, 7.75 and 9, which at this very low 8-bit precision is a large enough discontinuity to see in the graph, barely.

Hence, the accuracy of a number system depends on the rounding policy. By our definition of relative error, the worst-case decimal accuracy between adjacent values *x[k]* and *x[k]*[+1] occurs at their arithmetic mean, (*x[k]* + *x[k]*[+1])/ 2, relative to the smaller magnitude *x*.

At the arithmetic mean, the worst-case decimal accuracy is

In other words, the worst-case decimal accuracy of a numerical vocabulary is very close to the decimal accuracy of the adjacent points and adding log[10](2) ≈ 0.3.

Here is a decimal accuracy plot for a range of real values rounded to the **posit8** vocabulary:

![8-bit posits have a dynamic range of almost 4 orders of magnitude, but at most 6 significant bits.](images/pg23_1.jpg)

8-bit posits have a dynamic range of almost 4 orders of magnitude, but at most 6 significant bits.

The graph is thorough in showing the accuracy of the entire number system over its dynamic range, but the vertical spikes to infinity at the exact points make it difficult to read. Let's instead be pessimistic and look at the *worst case decimal accuracy* for each point in the number set.

The following graph shows just the bottom of each trough. If you ignore the jaggedness of the right half, it makes a symmetrical tent shape. The relative accuracy is tapered away from zero.

![This is the usual form of an accuracy plot: Decimal relative accuracy as a function of magnitude.](images/pg24_1.jpg)

This is the usual form of an accuracy plot: Decimal relative accuracy as a function of magnitude.

For posits of higher precision, the jaggedness is less pronounced and the decimal accuracy looks even more like a symmetrical triangular shape that peaks in the center.

A sequence of calculations that depend on previous rounded results is generally only as accurate as the least-accurate calculation, like a chain being only as strong as its weakest link. That is why it makes sense to use the pessimistic minimum accuracies and assume a chain of calculations will stumble into something near the bottom of each trough.

There is another way to plot the decimal relative accuracy, and that is as a function of the *bit pattern* treated as a binary integer instead of as the real value it represents by posit format rules. This illustrates how half the bit patterns are in the highest-accuracy region, defined in the next Section.

![Accuracy can also be graphed as a function of the bit pattern, shown here for positive 8-bit posits.](images/pg24_2.jpg)

Accuracy can also be graphed as a function of the *bit pattern*, shown here for positive 8-bit posits.

## 2.5 The *Fovea*

The highest-accuracy region has for years been called the “sweet spot” by posit users, but Will Wray came up with a clever, short word for it: The *fovea*, like the part of the retina of an eye that has the highest resolution:

Half of all posits are in the fovea, as is evident from the ring plot. One-fourth of all posits have a regime length of three bits (**00****1** or **11****0**) and thus have one less bit of significance than the fovea posits. One-eighth of all posits have a regime length of four bits, and so on.

To get the most accurate results with posits, it helps to try to stay in the fovea or not too far away from it. Wandering into very large or very small magnitudes, even temporarily, causes loss of relative accuracy that might propagate to the final answer and make it less accurate. Fortunately, most modern numerical methods are already carefully designed to avoid overflow and underflow and thus stay near the center of the dynamic range. Those methods are already well-designed for posits.

![The fovea for 8-bit posits is where ½ ≤ |x| ≤ 2.](images/pg25_1.jpg)

The *fovea* for 8-bit posits is where ½ ≤ |*x*| ≤ 2.

## 2.6 Fixed-Point Accuracy

Scaling a number by an integer power of two is like moving the radix point. What if you did not have to do that, but could simply assume a fixed location for the radix point? That would free up the bits that we use to indicate scaling, for more signific and bits. Fixed-point formats are like dollars and cents, where there are two digits to the right of the radix point. You can treat every dollar amount as an integer multiple of the number of cents, $\\frac{1}{100}$ of a dollar.

Suppose we have an 8-bit format regarded as a signed integer, representing multiples of $2^{- 4} = \\frac{1}{16}.$ That is, it has four bits to the right of the radix point, and the 256 different values it could represent would be

  
$$\\begin{matrix} {\\mathbf{0000}\\mathbf{.0000}} & \\text{0} \\\\ {\\mathbf{0000}\\mathbf{.}\\,\\mathbf{0001}} & {\\frac{1}{16} = \\text{0}\\text{.0625}} \\\\ {\\mathbf{0000}\\mathbf{.0010}} & {\\frac{1}{8} = \\text{0}\\text{.125}} \\\\ \\vdots & \\vdots \\\\ {\\mathbf{0111}\\mathbf{.1111}} & {\\text{7~+}\\frac{15}{16} = \\text{7}\\text{.9375}} \\\\ {\\mathbf{1000}\\mathbf{.0000}} & {- 8} \\\\ {\\mathbf{1000}\\mathbf{.0001}} & {- \\left( {7 + \\frac{15}{16}} \\right) = - \\text{7}\\text{.9375}} \\\\ \\vdots & \\vdots \\\\ {\\mathbf{1111}\\mathbf{.1111}} & {= - \\frac{1}{16} = - 0.0625} \\\\ \\end{matrix}$$  

Call the positive values the **fixed8** set. The points are equispaced. What would the decimal accuracy plot look like for the set of positive values, compared with the one for **posit8**? Here they are on a single plot:

![Accuracy plot of 8-bit posits versus 8-bit fixed point](images/pg26_1.jpg)

Accuracy plot of 8-bit posits versus 8-bit fixed point

The plot shows that fixed-point format does not support a wide dynamic range and represents small-magnitude values with much less accuracy than large-magnitude values. That is usually not what you want for technical computing. There are applications where fixed-point format is exactly what you want (like financial programs), which is also where absolute error might be more useful than relative error.

## 2.7 ULPs and Relative Accuracy “Wobble”

The term *ULP* is for Unit in the Last Place, and it has some uses for measuring inaccuracy. It is usually pronounced to rhyme with “gulp,” not as “you-ell-P.” Measuring ULPs assumes that as you count up in binary, the real number that is represented also increases in value. This is not true for all real number formats. It is one way to measure the distance between a computed result and a (correctly rounded) exact result: How far apart are their bit strings?

Suppose we use **fixed8** and the correct answer is $\\frac{1}{8}$\= **0****000.0010**, but the calculation misses and produces $\\frac{3}{16}$\= **0****000.0011** instead. That is an error of one ULP. As a relative error, though, it is $\\left| {\\log(\\frac{3}{16}/\\frac{1}{8})} \\right| \\approx 0.41,$ which is a rather poor result. The result has only about 0.38 decimals of relative accuracy.

At the other extreme, suppose the correct answer is $\\frac{127}{16}$\= 7.9375 = **0****111.1111** but the calculation is too low by just one ULP, so that we instead get $\\frac{126}{16}$\= 7.875 = **0****111.1110**. The resulting relative error is a much smaller number: $\\left| {\\log\\left( {\\frac{127}{16}/\\frac{126}{16}} \\right)} \\right| \\approx 0.008$ and we have about 2.1 decimals of relative accuracy. So, fixed-point format suffers a wide range of relative accuracy that becomes smaller for small magnitude results.

In scientific notation, an ULP is an error in the last decimal of the significand, assuming the exponent is correct. Like, 2.99 × 10⁸ versus 3.00 × 10⁸ for the speed of light in meters per second.

So “decade” in this context has nothing to do with a 10-year span of time. It is a numerical range that spans 10 dB. If a number format has a minimum positive value of 10^(−6) and a maximum positive value of 10⁶, we might say, “the format covers twelve decades of dynamic range.” Another common term is *order of magnitude*, so if something is off by a factor of a thousand, either too small or too large, it is off by “three orders of magnitude” (log base 10 of a thousand).

Back to the subject of ULPs: If we have three significant decimals in our scientific notation system, a 1-ULP error near the bottom of the decade is 1.01 versus 1.00, which has a relative error of about 0.01 and a decimal accuracy of about 2 decimals. But at the top of the decade, 9.98 versus 9.99 is instead a relative accuracy close to 0.001, ten times smaller, and the decimal accuracy is close to 3 decimals. The decimal accuracy ramps up from 2 to 3 decimals for every power of ten in the scale factor 10*^n*, producing a decimal accuracy that looks like this sawtooth shape:

![The “wobble” in relative decimal accuracy for scientific notation is a full decimal from worst to best.](images/pg28_1.jpg)

The “wobble” in relative decimal accuracy for scientific notation is a full decimal from worst to best.

But that is a misnomer. The *precision* is not wobbling at all. The precision is a constant three decimals. This phenomenon should be called *wobbling relative accuracy* or *wobbling relative error*. Notice that the wobble is not from 2 to 3 decimals, but from about 2.3 to 3.3 decimals since when used as a number system, the worst error happens midway between two representable numbers, as explained in [Section 2.4](#chapter2.xhtml#sec2_4).

One way to reduce wobble is to use base 2 for the scale factor, not base 10 or base 16. That reduces the wobble to log[10](2) ≈ 0.3 decimals.

With some number systems, including posits, the significand digits always represent a value between 1 and 2, ignoring the 2*^n* scaling factor and the sign.

Early IBM mainframes used a form of scientific notation with powers of 16 instead of powers of 10, to be more suited to binary computers. But base-16 exponents make the wobble even worse than base-10 exponents. A real number slightly greater than 1 would be expressed with 16 times less accuracy than a real number slightly less than 1. Base-2 has much less wobble, as this figure shows:

![Using base 16 reduces relative accuracy and makes the wobble four times worse than using base 2.](images/pg29_1.jpg)

Using base 16 reduces relative accuracy and makes the wobble four times worse than using base 2.

Posits do not work like scientific notation, but they still represent binades times scale factors, so you see similar notches in their relative accuracy plots.

For example, the shape of the sawtooth in the fovea region of **posit8** is exactly like the sawtooth shape in the previous accuracy plots:

![This is a close-up view of the fovea, overlayed by part of the usual accuracy plot.](images/pg30_1.jpg)

This is a close-up view of the fovea, overlayed by part of the usual accuracy plot.

## 2.8 Losing Something in Translation

Here is the picture to keep in mind when using a computer to do calculations on real numbers:

![These are the three layers to remember when using computers to work with real numbers.](images/pg30_2.jpg)

These are the three layers to remember when using computers to work with real numbers.

The diagram shows three layers: Human, Computer, and Mathematical. It also shows an example of how a simple-looking calculation like “1.1 + 1.2” can wind up pretty butchered by the three rounding steps. The example in the diagram uses the **posit8** set for the compute layer, but the same thing would happen with fixed-point or floating-point or any other representation with binary representation. The reason is that 1⁄10 = 0.1 in decimal becomes an infinite repeating pattern in binary, **0.0001100110011**⋯ the same way ⅓ becomes the infinite repeating pattern 0.333333⋯ when expressed as a decimal.

Input rounding occurs when decimals get turned into binary. Here, the closest binary to 1.1 is **1.00011** =$\\frac{35}{32}$\= 1.09375. The closest binary to 1.2 is **1.0011** = $\\frac{19}{16}$\= 1.1875. The only time there is no rounding is when a decimal just happens to be exactly expressible as a finite binary string, like 0.375 = **0.011**. It is not just fractions that suffer input rounding. If you try to add 9 and 11, for example, neither integer is in the vocabulary of **posit8**, and a computation will round those inputs. Any number system that has a decent dynamic range will have this problem: Large values *sample* the space of integers, skipping over swaths of them instead of including all of them in an interval by simply counting up.

The translation *to* the Math Layer is perfect. If you've got the time, God's got the integers. The computation in the Math Layer does not need to be perfect.

That is, the Math Layer takes into account that there will be rounding to go back to the Compute Layer and therefore it can perform the *finite* amount of work necessary to reach that result. In the example, the rational numbers are added correctly to be $\\frac{73}{32}$\= 2.28125. The Math Layer is extra registers with more bits, hidden algorithms, and other techniques working with data that are not accessible to the user.

*Compute rounding* is what happens whenever the result of an operation requires more bits to express than are available in the Compute Layer. The closest number in our vocabulary to $\\frac{73}{32}$ is $\\frac{9}{4}$\= 2.25.

The final blow to correctness comes in *output rounding*, where a binary number is expressed in decimal. It is always possible to do that exactly, but it can be quite bulky, and doing so can give you the misimpression that you have far more significance in the answer than you actually have. For example, $\\frac{1}{1024}$\= 0.0009765625 exactly, but if the $\\frac{1}{1024}$ was the result of a calculation involving rounding errors, then an output rounding of $\\frac{1}{1024}$≈ 0.001 conveys the inaccuracy in the output. As a rule of thumb, the significance expressed in the output should not exceed (at least not by much) the significance expressed in the input, and “1.1 + 1.2” uses two-digit inputs. Hence, rounding the result 2.25 to a two-digit output would become 2.2 in the Human Layer if we use banker's rounding (ties go to the nearest even).

You may be thinking, “Why not have the computer do the extra work of computing in decimal, eliminating the input and output rounding errors?” It is a great question. Sometimes, that is indeed what should be done. There are computer number formats that support exact decimal representation. However, the argument for computing in binary format goes like this: Typically, you do vastly more compute rounding than input rounding or output rounding. Computing with decimal formats is at least twice as slow as computing in binary formats. If you enter a number, perform thousands of (rounded) calculations, and format the result for output, then using decimal format protected you for only two of all of those thousands of calculations. And decimal format slowed you down by at least a factor of two. Usually, that is not a good tradeoff.

Before leaving the topic of translation error, there is an important question to answer for every binary number format: What is the minimum number of decimals needed to express a binary result such that it converts back to that same binary result? For example, the smallest positive value in **posit8** is $\\frac{1}{64}$\= 0.015625, but do you need all those decimals to ensure that when it is converted back to a **posit8** value, it converts to $\\frac{1}{64}$? Would 0.0156 suffice? How about 0.016?

It turns out that all you need is 0.02, just a single decimal of significance, to make sure it converts back to $\\frac{1}{64}.$ That is economical, *if* you are sure that “0.02” in the Human Layer will be converted back to that same low-precision format the next time that value is needed.

Near the middle of the range where **posit8** values have more significance, you need as many as three decimals to express them such that they convert back to the correct posit. For example, consecutive **posit8** values $\\frac{33}{32},\\frac{17}{16},\\frac{35}{32}$ are expressible as exact decimals 1.03125, 1.0625, 1.09375, but all you need is 1.03, 1.06, and 1.09 to make sure they convert back to $\\frac{33}{32},\\frac{17}{16},$ and $\\frac{35}{32}.$

A small program lets us test every value to see how many decimals are needed. It is related to the decimal accuracy, but it is not the same. It is much more chaotic, and it is difficult to find a closed-form equation for how many decimals are needed. Here is an empirical plot for the **posit8** values:

![For each 8-bit posit, a dark magenta dot shows the number of decimals needed to specify it uniquely.](images/pg33_1.jpg)

For each 8-bit posit, a dark magenta dot shows the number of decimals needed to specify it uniquely.

Perhaps 8 bits is somewhat too low of a precision to show the pattern. Here is the plot for the 16-bit posits mentioned at the end of [Chapter 1](#chapter1.xhtml):

![For 16-bit posits, a range of 1 to 5 decimals suffice to specify each one.](images/pg33_2.jpg)

For 16-bit posits, a range of 1 to 5 decimals suffice to specify each one.

That shows that five decimals suffice to express a **posit16** in a way that re-encodes as the same posit. But it also shows one of the advantages of tapered accuracy: For large-magnitude and small-magnitude values, it is more economical to express numbers with scientific notation, like “−6e−5” (five characters) instead of “−0.00006” (eight characters). Even though the “e” notation takes extra characters, it saves space for extreme magnitudes. With tapered accuracy, the more you need scientific notation, the fewer decimals need to be displayed. The smallest positive **posit16** value is $\\frac{1}{16384},$which can be expressed as “+6e−5”. For the higher-accuracy values like the ones in the fovea, five decimals are needed but not the “e” notation, like 1.0001, 1.0002, 1.0004 for the three **posit16** values that follow 1.0.

## 2.9 Defining *Overflow* and *Underflow*

### 2.9.1 The Overflow Fallacy

A common misconception is this one:

That is not quite true, because a result can legitimately *round down* to the largest representable value and thus stay in range. So we offer this definition instead:

For an example with an 8-bit fixed-point format, the negative number of greatest magnitude is −8. Numbers are spaced $\\frac{1}{16}$\= 0.0625 apart, so tie points are $\\frac{1}{32}$\= 0.03125 from each value in the vocabulary. Any result *x* where *x* is in the interval (-8.03125, -8) rounds to -8 without being an “overflow.” For positive values, the largest value in **fixed8** is 7.9375, and $\\frac{1}{32}$ beyond that is 7.96875, so values in (7.9275, 7.95875) do not overflow even though they are larger than the maximum representable real number in the format.

There is a similar definition for underflow. Here we use “too small” to mean “too low in magnitude” (that is, too close to zero) and not “too close to −∞.”

Again using **fixed8**, we could multiply $\\frac{1}{16}$ and $\\frac{9}{16}$ which has the exact result $\\frac{9}{256},$ but that has to be rounded to the smallest positive value $\\frac{1}{16}$ or be classified as underflow. The tie point is $\\frac{1}{32} = \\frac{8}{256},$ so it rounds up to $\\frac{1}{16}$ and does *not* underflow. The relative error is rather high, however, the same as the relative error of rounding 9 up to 16. That is a relative error of |ln(16 / 9)| ≈ 0.58.

The following diagram summarizes the careful definition of underflow and overflow that takes into account rounding. Relative widths are not to scale.

![Underflow and overflow need to take rounding into account.](images/pg35_1.jpg)

Underflow and overflow need to take rounding into account.

Notice that the result has to be signed. If the result of a calculation is correctly expressable as zero, that is not underflow. Whether the endpoints of the Expressible Results range are open or closed depends on the specific rounding rules, like “ties go to even” or “ties go towards zero” and so on.

### 2.9.2 Infinite Relative Error or Saturate?

In some legacy formats for real numbers, there are representations of ∞, and −∞, and overflow can return the appropriate signed infinity. Similarly, underflow returns zero. Notice that this creates an infinitely large relative error; if the correct answer is a signed value *x* and we instead return 0 or ±∞, the relative error is |ln(±∞/*x*) = |ln(0/*x*)| = ∞.

Legendary computer scientist Donald Knuth weighs in on the underflow issue in his *The Art of Computer Programming* series:

Volume 2, *Seminumerical Algorithms*, 2nd edition, page 206.

Posit arithmetic instead *saturates* to the nearest signed posit. This preserves information about the sign of the result, and while the relative error can be large, at least it is known and it is *finite*. The “certain cases” Knuth mentioned can be handled in software for posit calculations.

## 2.10 The Inaccuracy of Operations

Another thing we need to be able to measure is the amount of error caused by rounding after an operation, like addition or squaring or any other function. When adding or multiplying *integers* on a computer, you either get the exact answer or you overflow/underflow the range you can represent. When working with *real* numbers, you have no such luxury.

A figure of merit for a real number format is the fraction of the cases it actually *is* possible to represent the result of an operation without rounding. And if you do have to round, the relative error of rounding should be as small as possible. We can look at the worst-case rounding error and the average rounding error. If we compute all the errors and sort them from smallest to largest, it helps us visualize the overall inaccuracy of an operation.

### 2.10.1 An Easy Example: The Square Root Function

The square root operation is easy to evaluate because there is no possibility of overflow or underflow. It reduces the set of representable (nonnegative) real numbers to a subset of those numbers. Let's apply the error assessment to the square root function for the **posit8** set and the **fixed8** set:

![Square root rounding error for 8-bit posits (magenta) and 8-bit fixed-point (blue)](images/pg36_1.jpg)

Square root rounding error for 8-bit posits (magenta) and 8-bit fixed-point (blue)

While this shows posits to be superior for square root operations for accuracy, remember that the hardware for fixed-point arithmetic is simpler and faster than that for posits, so there is an engineering tradeoff.

### 2.10.2 A Two-Input Example: Multiplication

For two-input functions (like *a + b, a − b, a × b, a / b*, and *a^b*) and small sets of possible inputs, we can exhaustively tabulate the errors for all possible pairs of inputs. Let's try that with multiplication, again comparing **fixed8** and **posit8**. It is sufficient to test the nonnegative numbers since negating an input does not change the error. But unlike the square root, it is possible for multiplication to overflow or underflow. We can count the number of times that the result

*   overflows
    
*   underflows
    
*   is exactly representable in the format
    
*   is rounded to the nearest number in the format
    

In the last case, we compute the relative error from rounding, and find the worst-case relative error, and the average error including results with no error (exact). Start with **fixed8**.

![Sorted errors for 8-bit fixed-point multiplication (much of the graph is off-scale)](images/pg37_1.jpg)

Sorted errors for 8-bit fixed-point multiplication (much of the graph is off-scale)

If we lay out the multiplication table graphically, using colors to indicate what happens to this imperfect representation of real values, it looks like this:

 
| **Exact** || **Rounded** || **Underflow** || **Overflow** |
| --- | --- | --- | --- |
| 1197 || 10 503 || 20 || 4664 |
| --- | --- | --- | --- |
| 7% || 28% || 0.12% || 64% |

![Closure plot for 8-bit fixed-point multiplication](images/pg38_1.jpg)

Closure plot for 8-bit fixed-point multiplication

The **black** pixels indicate an exact result, that is, cases where the product just happens to be exactly representable as a fixed-point number. **Light Blue** indicates overflow, which occurs for an alarmingly large fraction of the multiplication table. **Red** indicates underflow. Both use the careful definition that the number cannot legitimately round to the nearest representable real. The **green** pixels are where the result is rounded to a number that the format can represent; the brighter the color, the larger the relative error.

For the **posit8** set, the average relative error appears to be greater at first glance:

![Sorted errors for 8-bit posit multiplication](images/pg39_1.jpg)

Sorted errors for 8-bit posit multiplication

However, that is a small price to pay for a massive increase in the resilience to overflow, as the graphical table of errors from multiplication shows:

 
| **Exact** || **Rounded** || **Underflow** || **Overflow** |
| --- | --- | --- | --- |
| 1992 || 14151 || 119 || 122 |
| --- | --- | --- | --- |
| 12% || 86% || 0.73% || 0.74% |

![Closure plot for 8-bit posit multiplication](images/pg39_2.jpg)

Closure plot for 8-bit posit multiplication

The area of overflow has been reduced to a tiny fillet in the table, very similar (but not identical) to the area of underflow.

Now that we are armed with tools for measuring inaccuracy accurately, we can start comparing number formats and ways to use them for calculations.

![](images/pg40_1.jpg)

# 3 More Power!

![Exponentially increasing power in the classic 1956 sci-fi movie Forbidden Planet](images/pg41_1.jpg)

Exponentially increasing power in the classic 1956 sci-fi movie *Forbidden Planet*

The first explanations of the full posit format were published in 2017, and in the intervening years much has improved about how to explain it more clearly. If you have already seen explanations of the posit format, do not be surprised if the following differs slightly from the early papers on the subject.

## 3.1 Increasing Posit Dynamic Range

Start with a three-bit posit ring, but instead of the regime bits representing a power of 2, let them represent a power of 2² = 4. That doubles the dynamic range:

![Squaring the northwest value (and adjusting the reflected values) doubles dynamic range.](images/pg41_2.jpg)

Squaring the northwest value (and adjusting the reflected values) doubles dynamic range.

It also creates a new rule for inserting values when we append bits. As usual, appending a **0** bit does not change the value; but when we append a **1** bit we now can insert an integer power of 2 between the values.

![Between powers of 2 that differ by more than 1 in the exponent, insert the geometric mean.](images/pg42_1.jpg)

Between powers of 2 that differ by more than 1 in the exponent, insert the geometric mean.

When a bit is appended after a regime termination bit, we call that an *exponent bit* and color code it in **blue**. If it is a **1** bit, the flanking values are 2*^k* and 2*^m* and the inserted value is 2^((^(*k*+*m*))/2). The regime bits now serve as a kind of super-exponent, where the value they represent is a power of 4 scaling, not a power of 2. The exponent bit then lets us fill in the gap between 1 and 4, or between 1/4 and 1. To make it clearer, we can append one more bit so that some fraction bits appear for magnitudes 1/4 to 3 (shown in **black** as usual). The exponent bit lets us fill the gap between 4 and 4² = 16 with 4² ·2¹ = 8. Integer powers of 2 still have perfect reciprocals, their mirror image about the horizontal axis. The mapping to 2's complement integers is still monotone, as shown in this ring plot:

![Ring plot of 5-bit posits with 1 exponent bit](images/pg42_2.jpg)

Ring plot of 5-bit posits with 1 exponent bit

Suppose we want still more dynamic range. We can square the meaning of each regime bit again, to 4² = 16, so the value in the northeast position is 16. To fill in between 16⁰ = 1 and 16¹ = 16 means scaling by 1, 2, 4, or 8, that is, 2*^e* where *e* ranges from 0 to 3. As an unsigned binary, we can do that with exponent bits **00**, **01**, **10**, and **11**. Here is the ring plot for a 5-bit posit with a 2-bit exponent field:

![Ring plot of 5-bit posits with 2 exponent bits](images/pg43_1.jpg)

Ring plot of 5-bit posits with 2 exponent bits

The number of bits in the exponent field is *eS*, short camelCode for *exponentSize*. The value in the northeast position is called the *uSeed*, and it is equal to 2²*eS*. Every time *eS* goes up by 1, the *uSeed* is squared and the dynamic range doubles in size, at the expense of taking away one bit from the significant bits in the fraction part. As *eS* increments starting at 0, *uSeed* is 2, 4, 16, 256, 65 536,… a *very* rapidly-increasing series. Be careful with it.

[Chapter 1](#chapter1.xhtml) introduced the simplest form of posit with no exponent bits (*eS* = 0), but by introducing exponent bits we have considerably more power. Here are the complete rules for introducing new values on the posit ring as the precision *n* grows:

*   Appending a **0** bit to an existing posit does not change the represented value.
    
*   Between NaR and a real number, insert the real number times *uSeed*.
    
*   Between 0 and a real number, insert the real number divided by *uSeed*.
    
*   Between 2*^k* and 2*^m* where *k* and *m* differ by more than one, insert 2^((*k*+*m*)/2).
    
*   Otherwise, between *x* and *y*, insert their average, (*x* + *y*)/ 2.
    

We also generalize the formula for a posit value. With *eS* = 0 in [Chapter 1](#chapter1.xhtml), we had

where *s* is the sign bit value, *f* is the value of the fraction bits, and *r* is the value represented by the regime. Each increment in the *r* value makes the exponent part of the above formula larger by 2*^(eS)*. The exponent bits then represent an unsigned integer that fills in all the integers between those regime strides, from 0 to 2*^(eS)* - 1. This seems weird at first, because it mixes two different ways to write a number. Imagine writing counting numbers with Roman numerals for the ten's place and 0–9 numerals for the one's place, so twenty-three would be “**XX**3” and thirty-nine would be “**XXX**9”. Or we could use Roman numerals for the hundred's place and 00–99 numeral for the ten's and one's place, so two hundred seventy-one would be “**CC**71”. That is similar to how the regime bits and exponent bits work together.

For example, if *eS* = 2, each increment of *r* raises the power of two by a stride of 2*^(eS)* = 4, and the two exponent bits **00**, **01**, **10**, **11** represent *e* = 0, 1, 2, 3 to fill in the gaps between those multiples of 4. The formula for *x* generalizes to

The function above is the **pToX** function (for posit-to-*X*) and the code for it is in [Appendix A](#appA.xhtml#appA). If the formula produces –∞, it returns **Indeterminate** to accommodate all the cases where the result is not a real number, as the Not-a-Real (NaR) value.

The tent-shaped relative accuracy curves double in width with each increase in *eS*, but the top of the fovea drops by about 0.3 decimals because the fraction has one less bit.

Here is a plot of 16-bit posit decimal accuracy with *eS* set to 0, 1, 2, and 3.

![Accuracy plots for 16-bit posits as eS ranges from 0 to 3](images/pg45_1.jpg)

Accuracy plots for 16-bit posits as *eS* ranges from 0 to 3

In that figure, the wobble is simplified as a bar, and the annotated accuracy refers to the *minimum* accuracy.

## 3.2 *Ghost Bits* and the *Twilight Zone*

As an example, let's look at the posit ring for 6-bit precision and *eS* = 2:

![Ring plot for 6-bit posits with 2 exponent bits](images/pg45_2.jpg)

Ring plot for 6-bit posits with 2 exponent bits

We need a notation for the number of bits of precision *n* and the exponent size *eS*. Let's use angle brackets 〈*n, eS*〉, so the above ring shows “posit〈6, 2〉” format.

The ring plot shows 2 exponent bits, shown in **blue**. But wait, you say; some of the values do not have *any* exponent bits, and some have *only one* exponent bit. Not true; there are always 2 exponent bits, but any bits beyond the end of the number are **0** bits, just as we did for the fraction bits. Ghost bits can be exponent bits.

The area where the exponent bits are partly or entirely beyond the least significant bit (LSB) is called the *Twilight Zone* because years of experience has shown this slightly-weird region to be the source of most of the bugs in creating a posit environment.

Consider the value 1024 in the ring, with posit representation **011101**. The right way to think of that is as six stored (explicit) bits followed by an infinite string of ghost bits, and in this case, the first ghost bit is the second bit of the two-bit exponent field:

```
011101|000000⋯
```

It is even possible for regime bits to be ghost bits, implied **0** bits beyond the stored bits. For example, look at the representation of -1 / 65 536:

```
111111|000000⋯
```

The opposite bit that ends the regime is in the trailing **0** bits, not shown explicitly.

As an example of the kind of mistake that is easy to make, suppose we want to encode the number 600 in the closest posit〈6, 2〉 form, properly rounded. We have a choice between 256 or 1024, both of which are in the Twilight Zone. The halfway point between the two numbers is (256 + 1024) / 2 = 640, which might make it seem like 600 should round down to 256 as the closer point. However, that is not the way rounding works. You instead ask, “If we had posit〈*n* + 1, *eS*〉 format instead of posit〈*n, eS*〉 format, what would be the new halfway point and which side would the value be on?” Bit *n* + 1 might be an exponent bit, not a fraction bit.

If we had seven bits instead of six, we could represent **0111011**, which would decode as 512. Since 600 is greater than 512, the nearest representation as a posit is to round *up*, to 1024. This is consistent with our definition of relative error, since the relative error of choosing 1024 is |ln(1024 / 600)| ≈ 0.5 but the relative error of choosing 256 is |ln(256 / 600)| ≈ 0.9. On a logarithmic scale, 600 is closer to 1024. In the Twilight Zone, the tie point is also a point where relative accuracy is continuous instead of having a slight discontinuity (see [Section 2.4](#chapter2.xhtml#sec2_4)).

## 3.3 Is the Opposite Bit in the Regime “Wasted”?

Another common initial reaction to the posit format is that the terminating bit of the regime is a “wasted” bit, and there ought to be a way to define it differently so that every bit counts. So, *is* it wasted?

In the posit〈6, 2〉 format, suppose we have *x* = **010111** representing 12, and we add 2 to that. The result of 14 is midway between representable values 12 and 16 and the nearest even binary is 16 = **011000**. We need to round *up*. Notice what happens to the last four bits when we increment the posit representation for 12. Taking the color-coding away, **010111** increments to **011000**. The amazing thing is that the carry extends the regime by one more bit, the most-significant exponent bit turns into the opposite bit terminating the regime, and the exponent shifts over by one place to form the last two represented bits of the posit. All fraction bits become ghost bits. This happens *automatically*. The result, 16 = **011000**, is exactly what it should be. There is no need to check for carry overflow in each field. Everything just works.

The terminating bit of the regime is essential for this to work. It is definitely not wasted. Every bit counts.

A common mistake is to worry about rounding the fraction part, and once that is rounded, assemble the parts of the posit (sign bit, regime, exponent, and fraction). This will create more bugs than you find in a tropical rainforest. Always assemble the parts of the posit, computed with extra bits of precision, and *then* apply rounding.

## 3.4 Converting Real Numbers to Posits

[Section 3.1](#chapter3.xhtml#sec3_1) showed how to turn a posit bit string *p* into a real number *x* (or NaR). This section explains the algorithm that converts a real number *x* (in any format) into a posit string *p*. This routine is called **xToP**, and the code for it is in [Appendix A](#appA.xhtml#appA). For clarity, this method takes the absolute value of the input, but it is also possible to directly convert a real value without doing that. Assume the following quantities have been defined or computed as global variables based on the requested precision *n* and exponent size *eS*:

*   *uSeed* is 2²*eS*.
    
*   *minPos* is the smallest positive posit value, *uSeed*^(2-*n*).
    
*   *maxPos* is the largest positive posit value, *uSeed^n*^(\-2).
    

In the following, assume *n* > 2. The algorithm for *n* = 2 can be expressed in a single sentence: “Any non-real becomes NaR, **10**; zero becomes **00**; positive reals become **01**; and negative reals become **11**.”

### 3.4.1 Check for Non-Real Inputs

The first step is to determine if the input *x* represents a real number. If it is stored in integer format, that works. Integers are real numbers. It could also be a complex number *a* + *b i* where *b* happens to be zero. It could be an input string like **“1.6e-19”** that follows the rules of a computer language for expressing a real number in scientific notation. If it fails the test of being a real number, return the *n*\-bit string for NaR, **1000**⋯**000**.

### 3.4.2 Take the Absolute Value and Check for Special Cases

Setting *y* = |*x*| makes some steps simpler. That does not lose the information about whether *x* is positive or negative (or zero), since we do not alter the input value *x* and can always refer back to it.

If *y* = 0, return the *n*\-bit string consisting of all 0 bits, **0000**⋯**000**. It is important to take care of possible NaR or 0 cases before trying to find the regime bits. This also takes care of the cases where *y* ≥ *maxPos* or *y* ≤ *minPos*:

```
If y ≥ maxPos,
         Return the posit for maxPos times the sign of x,
Else if y ≤ minPos,
         Return the posit for minPos times the sign of x,
End if.
```

This also takes care of one of the rounding rules, that magnitudes outside the dynamic range saturate to the (signed) largest or smallest value. Also, handling these special cases assures that the opposite bit ending the regime will fit in the *n*\-bit string built in the next subsection.

### 3.4.3 Encode the Regime Bits

Since computer environments usually support unsigned integer types, it is easy to treat the posit bit string as an unsigned *n*\-bit integer. Having already dealt with the NaR and 0 cases, the regime can be at most *n* - 1 bits long. With an *n*\-bit unsigned integer *p* we can store the regime starting in the Most Significant Bit (MSB) since we do not need a sign bit, and that will leave an extra bit at the end that we can use to do proper rounding.

```
If y ≥ 1, the regime will be a string of 1 bits:
         Set p = 1 and i = 2. The number of posit bits found so far is i.
         While y ≥ uSeed and i < n,
                 shift p left by one place and set the LSB to 1 (lengthen the regime).
                 Divide y by uSeed and increment i.
         End while.
         Shift p left by one place to prepare for the next phase, and increment i.
Else y < 1, so the regime will be a string of 0 bits:
         Set p = 0 and i = 1 (off by 1 from the y ≥ 1 case, since we seek 1 ≤ y < uSeed).
         While y < 1 and i ≤ n,
                 multiply y by uSeed and increment i.
         End while.
         Set p = 1 (the opposite bit ending the regime) and increment i.
End if.
```

The “Shift *p* left by one place” creates a **0** as the LSB, which is the opposite bit ending the regime in the case where the regime is a string of **1** bits.

### 3.4.4 Encode the Exponent Bits

Converting *x* to the posit format has proceeded from left to right, and finding the exponent bits is no different. We know that 1 ≤ *y* < *uSeed*. If the format uses *eS* = 0 then there is nothing to do, so skip to finding the fraction bits. Otherwise, continue bisecting to find the exponent bits from most significant to least significant. Computing *uSeed* = 2²*eS* is actually an easy thing for a computer to do, because a **1** bit shifted left by *eS* places is the unsigned integer for 2*^(eS)*, and then a **1** bit shifted left by that unsigned integer is 2²*eS*. In the C computer language, it would be concisely expressed as 1 << (1 << eS).

So the algorithm for extracting the exponent bits looks like this:

```
Set e = eS − 1.
While i < n and e > 0,
        Shift p left by one place to make a place for an exponent bit.
        Set scale = 1 << (1 << e).
        If y ≥ scale, set the LSB of p to 1 and set y = y / scale.
        Increment i, since we have used another posit bit for the exponent.
        Set e = e − 1.
End while.
Shift p left by one place to prepare for the next phase, and increment i.
```

If the bit counter *i* actually reaches *n* before *e* decrements to 0, the exponent bits will be clipped off and the posit will be in the “Twilight Zone.” Otherwise, we will be left with the significand *y*, with 1 ≤ *y* < 2.

### 3.4.5 Encode the Fraction Bits

Since *y* is now a fixed-point number between 1 and 2, its binary bit string always begins with a **1** bit, so there is no need to store that. The **1** is implied. Hence, we first find the fraction by subtracting 1 from *y*. Then each bit of the fraction is found by doubling the fraction and testing if it is larger than 1; if it is, install a **1** bit in the posit bit string, subtract 1 from *y*, and repeat until there is no more room for fraction bits.

Once all *n* + 1 bits are populated, the test of whether the conversion was exact is very simple: Is *y* > 0? If it is, then the ubit is **1** because there are more bits after the last one. But if *y* = 0, then the conversion landed exactly on a posit value, so the ubit is **0**. Remember, the ubit is needed for the banker's rounding.

```
Set y = y − 1.
While i < n,
        Shift p left by one place. This puts a 0 in the LSB position.
        Set y = 2 × y.
        If y ≥ 1, set the LSB of p to 1 and set y = y − 1.
        Increment i, since we've used another posit bit for the fraction.
End while.
```

After this step, *i = n*, so we have a bit string with *n* bits. But it does not have the sign bit, so we have one more bit than will be in the rounded value. Call it *b*[−1].

### 3.4.6 Round and Apply the Sign of *x*

*Banker's rounding* is rounding a value *x* to the nearest representable number *p*, and if there are two possibilities for *p* equally close to *x*, the rule is to choose the one that has *even* representation. In binary, even numbers end in **0** and odd numbers end in **1**. The reason for the “ties go to even” rule is that it makes the rounding *unbiased*. Imagine a bank that needs to calculate interest to the penny on billions of dollars of transactions; even the slightest bias up or down could quickly amount to a fortune. There have been schemes to do this, using rounding to get something for nothing.

Banker's rounding is the rounding mode for the posit format, and it is the *only* rounding mode. No matter whether you are rounding integer format, fixed-point, floats, or posits, the principle is the same. The algorithm for banker's rounding needs just *three bits*, shown in the following figure for the case of an 8-bit format:

![The three bits needed for banker's rounding](images/pg51_1.jpg)

The three bits needed for banker's rounding

For an *n*\-bit format, our convention is to label bits with subscripts from 0 for the LSB up to *n* - 1 for the MSB. The three bits we need are the LSB, a “*b*[\-1]” bit we can call the *rounding bit*, and a bit we saw in [Chapter 1](#chapter1.xhtml), the ubit. If ubit = **1**, that indicates there are more significant digits after *b*[\-1], like writing “⋯” after the last digit of a number.

If *b*[\-1] is **1** and the ubit is **0**, the value is at the tie point; it is the value that would be represented if there were one more bit. To make the rounded value even, if *b*[0] is 0, do nothing (that is, round down by ignoring *b*[\-1]); but if *b*[0] is **1**, add **1** to the LSB and propagate the carry to the left. With posit format, there is no possibility of overflow.

If *b*[\-1] is **1** and the ubit is **1**, meaning there are some **1** bits after bit *b*[\-1], then the value is above the tie point and needs to be rounded up. The four cases for rounding a value *x* to a posit are as follows:

*   If *x* is 0 or NaR, return the respective posit representing that value.
    
*   If |*x*| ≥ *maxPos*, return the posit for *maxPos* with the same sign as *x.*
    
*   If |*x*| ≤ *minPos*, return the posit for *minPos* with the same sign as *x*.
    
*   If *minPos* < |*x*| < *maxPos*, encode *x* to *n* + 1 bits; if that representation is exact, set the ubit to **0**, else set the ubit to **1**. If *b*[\-1] is **1** and (*b*[0] is **1** or the ubit is **1**), add 1 to the *b*[0] position and propagate any carry.
    

If you like digital hardware design and can read circuit diagrams, the figure below shows what banker's rounding looks like for a number with the extra *b*[\-1] bit and some trailing bits in temporary storage.

![Logic circuit for banker's rounding](images/pg52_1.jpg)

Logic circuit for banker's rounding

The structure under the trailing bits is an “OR tree” that produces a ubit of **1** if any trailing bits are nonzero, or **0** if all trailing bits are zero. Even if you do not read circuits, you can see that banker's rounding does take logic gates and logic delays. If you did not care about bias in rounding, you could simply drop all the bits after *b*[0]. Some processors opt to do that with legacy formats, which can lead to an insidious problem that goes beyond biased errors accumulating in the result: Lack of *portability* and *reproducibility*. When a programmer discovers that a program produces different results on different computers, it leads to many unproductive hours spent trying to figure out why, culminating in the discovery that rules were bent in an invisible way. That is why there is only one rounding mode for the posit format.

```
If b−1 (the LSB of p) is 1,
         If b0 (the next-to-last bit of p) is 1 or y > 0, set p = p + 1.
Shift p right by one place to discard the b-1 bit and make room for the sign bit.
If x < 0, return -p, else return p.
```

### 3.4.7 An Example

Code-like descriptions can be tedious to read; an example should make it easier to see how to turn a real number into posit representation. Let's convert the decimal number *x* = −0.003 into an 8-bit posit with *eS* = 2. The *uSeed* is 2^(2²) = 16.

Since *x* is a real number and not zero, we do not have to worry about those special cases with an infinitely long regime of **0** bits. Its magnitude is also between *minPos* and *maxPos*, so there is no saturation.

Set *y* = |*x*| = 0.003. Begin by noticing that the regime will start with a **0** bit because *y* is less than 1. In other words, the posit for *y* is in the southeast quadrant of the ring. That consumes our first bit, so set *i* = 1 to keep track of the number of bits used in *p*.

  
$$\\begin{matrix} p & y \\\\ {\\bullet \\bullet \\bullet \\bullet \\bullet \\bullet \\bullet \\underset{\\begin{matrix} \\uparrow \\\\ {i = 1} \\\\ \\end{matrix}}{0}} & 0.003 \\\\ \\end{matrix}$$  

Shift *p* left to make room for the next bit. Scale *y* by multiplying by *uSeed* = 16 and check if it is still less than 1. It is, so we have another **0** regime bit. Increment *i*.

  
$$\\begin{matrix} p & y \\\\ {\\bullet \\bullet \\bullet \\bullet \\bullet \\bullet \\underset{\\begin{matrix} \\uparrow \\\\ {i = 2} \\\\ \\end{matrix}}{00}} & 0.048 \\\\ \\end{matrix}$$  

Again shift *p* and scale *y* by *uSeed*; 0.048 times 16 is 0.768, which is still less than 1:

  
$$\\begin{matrix} p & y \\\\ {\\bullet \\bullet \\bullet \\bullet \\bullet \\underset{\\begin{matrix} \\uparrow \\\\ {i = 3} \\\\ \\end{matrix}}{000}} & 0.768 \\\\ \\end{matrix}$$  

Shift *p* left to make room for the next regime bit; this time, when we scale *y* by *uSeed*, the result 0.768 × 16 = 12.288 is larger than 1, so terminate the regime with the opposite bit and move on to finding the exponent bits.

  
$$\\begin{matrix} p & y \\\\ {\\bullet \\bullet \\bullet \\bullet \\underset{\\begin{matrix} \\uparrow \\\\ {i~ = ~4} \\\\ \\end{matrix}}{0001}} & 12.288 \\\\ \\end{matrix}$$  

The first exponent bit is a scale factor of 2²*eS*\-1 = 2²1 = 4, and since *y* is larger than 4, the most significant exponent bit will be a 1. Shift *p* left and OR in the 1 bit. Divide *y* by the scale factor of 4; 12.288 / 4 = 3.072.

  
$$\\begin{matrix} p & y \\\\ {\\bullet \\bullet \\bullet \\underset{\\begin{array}{l} \\uparrow \\\\ {i\\operatorname{~=~}5} \\\\ \\end{array}}{00011}} & 3.072 \\\\ \\end{matrix}$$  

The next (and last) exponent bit is a scale factor of 2²*eS*\-2 = 2²0 = 2. Since *y* > 2, the next exponent bit will again be a 1. Shift *p* left and OR in the 1 bit. Divide *y* by the scale factor of 2; 3.072 / 2 = 1.536, and now we know the significand: *y* = 1.536. We are done with the regime and exponent bits that determine the power-of-2 scaling.

  
$$\\begin{matrix} p & y \\\\ {\\bullet \\bullet \\underset{\\begin{array}{l} \\uparrow \\\\ {i = 6} \\\\ \\end{array}}{000111}} & 1.536 \\\\ \\end{matrix}$$  

To find the fraction bits, first subtract the implicit 1 from the significand *y* = 1.536 to get just the fraction part, 0.536. Double the fraction to get 1.072; since that is greater than 1, the first fraction bit is a **1**:

  
$$\\begin{matrix} p & y \\\\ {\\bullet \\underset{\\begin{array}{l} \\uparrow \\\\ {i = 7} \\\\ \\end{array}}{0001111}} & 1.072 \\\\ \\end{matrix}$$  

That last bit will be in the *b*[0] position in the final posit bit string, but we need one more bit for banker's rounding, the *b*[−1] “rounding bit.” Subtract 1 from *y* and double it to get *y* = 0.144. That is not greater than 1, so the next fraction bit is **0**, which is in gray to remind us that it is a temporary bit beyond the last bit of the posit. And that is the *n*^(th) bit, so now we are ready to round.

  
$$\\,\\,\\begin{matrix} p & y \\\\ \\underset{\\begin{array}{l} \\uparrow \\\\ {i = 8} \\\\ \\end{array}}{00011110} & 1.144 \\\\ \\end{matrix}$$  

The *b*[−1] is **0**, so there is no need to round up. Shift *p* one place to the right, which does two necessary things at once: It discards the *b*[−1] and makes *b*[0] the LSB, and it shifts in a sign bit **0** on the left indicating a positive number.

  
$$\\begin{matrix} p \\\\ {0000\\text{1111}} \\\\ \\end{matrix}$$  

The final step is to apply the sign of *x*. If *x* were positive, we would be done, but since *x* = −0.003, we need to negate *p*. Flip all the bits to **11110000** and add 1 to the LSB:

  
$$\\begin{matrix} p \\\\ {\\text{1111}000\\text{1}} \\\\ \\end{matrix}$$  

That is the closest posit representation to *x* = -0.003. The posit decodes as $- \\frac{3}{1024} = - 0.0029296875$ which is −0.003 to one significant digit.

The thing to notice about encoding a posit is that it progresses from MSB to LSB, one bit at a time. That seems like the logical and obvious thing to do, but be aware that it is *not* the way reals are commonly encoded using legacy formats.

### 3.4.8 Some Advice for Anyone Building a Posit Environment

If you presently have a way to work with real values (such as IEEE floats, which will be described in the next chapter), make sure they have enough precision to do exact posit calculations. For example, here is a common pitfall:

The problem, and this is perhaps surprising, is that 64-bit floats have insufficient precision. The 32-bit posits have significands with as many as 28 bits. When multiplied, the product can have 56 significant bits. But a 64-bit IEEE float has only 53 significant bits. There are situations where the final conversion back to a posit will be off by one in the last bit and that will create incorrect experimental results.

A much safer approach is to use integer arithmetic. After checking for NaR, convert a posit to a number of the form *k* × 2*^m* where *k* and *m* are signed integers with enough precision to cover the necessary dynamic range, so that you can stay in the Math Layer long enough to go back to the Compute Layer with the correct rounding.

Another piece of advice is to test the round-trip conversion **pToX** and then **xToP** exhaustively and plot **pToX**(**xToP**(*x*)) as a function of *x* with graphics tools. Start with very low precision, like *n* = 4 bits, debug, and work up with *eS* values from 0 to, say, 3. Also plot the discrete function **xToP**(**pToX**(*p*)) for all possible *p* up to a precision *n*, beyond which exhaustive testing becomes impractical. Experience shows that this is a quick and effective way to find bugs.

The **pToX**(*p*) function is the easiest to code and to get right; there are 2*^n* possible bit patterns for an *n*\-bit posit, so for small *n* you can generate and display the real *x* value and check that the routine is decoding every *p* correctly. You do not have to worry about rounding. But the **xToP**(*x*) function is more challenging since there are many more possible inputs *x* than the number of possible outputs *p*, and there are many opportunities to create off-by-one programming errors. Here are example plots of a posit〈6, 1〉 environment using the **pToX** and **xToP** functions in [Appendix A](#appA.xhtml#appA).

![](images/pg56_1.jpg)

The plot on the left should always look like a discrete version of *y = x*, where the input and output posit bit strings are treated as signed integers. The plot on the right is a log-log plot; it uses the log[2] of *x* values from *minPos* to *maxPos* (in this case, $2^{- 16} = \\frac{1}{65536}\\,\\text{to}\\, 2^{16} = 65536$ ). It should look like a staircase wobbling about the line *y = x*, with increased wobble at the smallest and largest magnitudes. If there is a bug in either **xToP** or **pToX**, it usually shows up instantly in these “round-trip” plots.

## 3.5 A Simple Notation for Rounded Arithmetic

When FORTRAN was introduced in the 1950s, it was touted as “FORmula TRANslation,” hence the name. It allowed you to write algorithms with a notation very similar to algebraic notation, albeit with an asterisk “**\***” for the multiplication operator, and a few other tweaks. You could declare variables a, b, and c to be of REAL type and then write a line of code like

```
c=a+b
```

and it looked for all the world like you were computing with real-valued variables. But that was a deception. If the variables are *integers*, then it is a fairly honest thing to do because you really will get the correct integer unless there is underflow or overflow. But with *real* values? Not likely.

For most of the many possible input values a and b, you will not get a REAL that exactly expresses “a + b” nor will the computer tell you anything about how far off it is from the correct value. FORTRAN has lost its all-caps look and become Fortran, and it is now fading as a computer language. But it made more than one generation of programmers highly vulnerable to the surprise that what looks like real-number math on a computer is not exact math at all, but instead is an approximation that can sometimes go horribly wrong without warning.

One can imagine a rigorous programming language where you have to write

```
c=ROUND (a+b)
```

or else you get an error message from the language compiler. But that would make code look pretty ugly.

Here is an idea that might at least find its way into Integrated Development Environments (IDEs) if not actual source code for a language. IDEs can color-code your program with different colors for comments, keywords, and so on, even if that is not part of the official language you are programming in. An IDE that understands rounding error and makes the hazards visible could be a huge help to the programmer.

Suppose we compute a value with exact math, convert that to an expressible (exact) posit using correct rounding, then convert the posit back to its mathematical value? In other words,

This assumes that the **a** *op* **b** on the right hand side is computed in the Math Layer, that is, exactly. Throughout this book, the overbar operator is assigned to that composite function **pToX**(**xToP**(…)). So

means that exact inputs *a* and *b* will be added exactly, rounded to the nearest real that posits can represent, and then presented back to the programmer as a value that can be expressed without rounding error.

That is much less intrusive than having to type “**ROUND**” everywhere. Some papers on rounding error put a circle around the + - × / operators for their rounded versions, like “⊕” for “rounded addition.” But how would you do that for square root, or cosine? The overbar works for every operator. And you can use it on constants and single-argument operators as well. For example,

instructs a computer to round the real value 3.1 to the nearest representable posit value, then compute the log base 10 of that to enough accuracy that the nearest representable posit is known. It still looks a lot like log[10](3.1), but the overbar decorations remind you that *you need to be suspicious*. This definition of the overbar as an operator is part of the code in [Appendix A](#appA.xhtml#appA), and you will see a lot of it in this book.

## 3.6 As Simple as Possible, But No Simpler

![“The supreme goal of all theory is to make the irreducible basic elements as simple as possible without having to surrender the adequate representation of a single datum” ¶ —Albert Einstein, 1933](images/pg59_1.jpg)

“The supreme goal of all theory is to make the irreducible basic elements as simple as possible without having to surrender the adequate representation of a single datum” ¶ —*Albert Einstein*, 1933

The folk paraphrasing of Einstein's words is usually something like, “A theory should be as simple as possible, but no simpler.” Which is more succinct, though not his exact words.

Posits are designed with Einstein's viewpoint. It would be wonderful if we could do an entire calculation in the Math Layer and never have to worry about the finite nature of physical computers, but that is usually either impossible or is so complicated to do (by using symbolic methods, not just numerical methods) that it would run very slowly. Given that we *must* use finite precision in the Compute Layer and the Human Layer, and that we want the distribution of representable numbers to resemble the distribution of values that would occur if all computations are exact, posits are about as simple as possible. But no simpler.

## 3.7 Not the Current State of Things

So far, we have presented the positive message that *it is possible* to represent real numbers, either as exact values or ranges between exact values (using the ubit), and it is also possible to round after operations and sacrifice provable error bounds for speed. The unum and posit approach is derived through logical steps starting from low precision and working up, resulting in an exception-free definition.

But at the time of publication, this is not what we see offered to us in processor hardware for working with real numbers. Not even close. Which means we need the backstory on how we got to where we are now. In the next chapter, I can almost guarantee the reader a few surprises, and some information you will not find anywhere else.

![Please keep this in mind as you read Chapter 4.](images/pg60_1.jpg)

Please keep this in mind as you read [Chapter 4](#chapter4.xhtml).

# 4 How We Got Into This Mess

![A robot vacuum as envisioned in the 1960s, and what robot vacuums actually look like, lately. We similarly make the mistake of trying to get machines to mimic humans in our number format designs.](images/pg61_1.jpg)

A robot vacuum as envisioned in the 1960s, and what robot vacuums actually look like, lately. We similarly make the mistake of trying to get machines to mimic humans in our number format designs.

There is a strong human tendency to design technology to behave the way people do, instead of figuring out what is *optimal for the technology*. That is why some of the earliest digital computers wasted huge amounts of hardware to operate on decimal numerals instead of in binary, for example, when the only reason humans use base-10 is the physiological accident that our hands have ten fingers.

![A few cultures used base 20 (fingers and toes?) and numerals in Maharashtra were base 5, suggesting one-handed counting. Bases 60 and 12 are still in modern use for time and degrees.](images/pg61_2.jpg)

A few cultures used base 20 (fingers and toes?) and numerals in Maharashtra were base 5, suggesting one-handed counting. Bases 60 and 12 are still in modern use for time and degrees.

This chapter examines a sampling of the vast history of how humans have recorded and used numbers, and how those methods have proved to be far from optimal for *machines*. It also will tell the story of where the present-day IEEE Std 754 definition of floating-point formats actually came from; it's not what most people think.

## 4.1 The Amazing Babylonians

The ancient Babylonians were no slouches at mathematics, even going back as far as 1800 BC. They recognized the merits of using 60 as a number base, which persists to the present day in the form of 60 seconds per minute and 60 minutes per hour, as well as 360° per circle. The Egyptians may have been just as capable, but they used ink on papyrus instead of clay tablets left to bake in the sun, so we have much less surviving evidence of their skills. Here is a particularly impressive Babylonian relic, redrawn for clarity and annotated with modern numbers in white:

![Ancient Babylonians knew the square root of 2 to seven decimals.](images/pg62_1.jpg)

Ancient Babylonians knew the square root of 2 to seven decimals.

First, notice how logical the Babylonian number notation is. At the lowest level, it is unary in that it repeats the ![](images/inline1.jpg)symbol for ten and the  symbol for one to notate two-digit positional numbers between 1 and 59. If they needed a zero, they left that position blank. At the level above that, the system uses positional notation from left to right like our modern decimals, but base 60 instead of base ten. The side of a square is labeled 30 in the upper left. Across the diagonal of the square is their notation for $1 + \\frac{25}{60} + \\frac{51}{60^{2}} + \\frac{10}{60^{3}}$, which in decimal works out to 1.414213…, which is the square root of 2 correct to the first seven decimals! The side of the square is labeled as 30, so the length of the diagonal is $30 \\times \\sqrt{2} \\approx 42 + \\frac{25}{60} + \\frac{35}{60^{2}} \\approx 42.4264$, again uncanny accuracy to six decimal places.

The relic is not a “tablet” but someone's scratch work from almost four thousand years ago. They knew how to find the diagonal of a right triangle, so maybe what we call the Pythagorean Theorem should be called the Babylonian Theorem. The backside of that block of clay has been partly erased but seems to show a 3-4-5 right triangle, the simplest case where the diagonal is an integer, $\\sqrt{3^{2} + 4^{2}} = 5$.

The Babylonians also knew how to solve the quadratic equation and compute compound interest rates (exponentials), and they could approximate the area under a curve by using close-fitting trapezoids (integral calculus). They knew how to solve systems of linear equations. I could go on. Somehow, though, their knowledge and well-designed number system was lost instead of spreading to the empires that followed, like that of the Romans.

## 4.2 Roman Numerals

![](images/pg63_1.jpg)

It is amazing that a civilization as successful as the Roman Empire was able to thrive with one of the most cumbersome number systems ever devised. Since we still see Roman numerals everywhere, from the hour labels on analog clocks to their use in numbering sections of publications, perhaps they do not seem that painful. But ask yourself this: How would you *multiply* **XIV** by **LXV** by hand, without first translating to some other number system?

Here is a question: Are Roman numerals positional notation, or are they more like tally marks and numeral systems that do not use position? I argue that they are *slightly* positional, but not all the way there. For example, suppose we write the integer 1984 in Roman numerals. The conventional way would be **MCMLXXXIV**, with big numbers mostly on the left and small numbers mostly on the right.

However, if we break that up as **M CM L X X X IV**, they could be written in any pattern and it would still mean 1984:

![Roman numerals are not positional notation.](images/pg64_1.jpg)

Roman numerals are not positional notation.

The only positional thing about Roman numerals is the subtractive pairs **IV, IX, XL, XC**, and so on where the value of the first letter is subtracted from the value of the second. Otherwise, they might as well be coins thrown on a table and added up. Hence, *slightly* positional. There are examples, say of the twenty-second Roman Legion writing their number as **IIXX**, since the way they described themselves in Latin translates as “the two and twentieth”. Sometimes a scribe would write **VXL** for 45 instead of **XLV**, probably an indication that scribes of the era found the rules just as confusing and error-prone as we do today.

It's not commonly known, since in modern times we only use Roman numerals to write positive integers, but the Romans *did* have a way to write fractions.

![](images/pg64_2.jpg)

The system actually almost makes sense, like the pips on dice or dominos. However, besides integers divided by 12, they had special fractions with their own symbols, like ℈ for $\\frac{1}{288}$ and Ƨ for $\\frac{1}{72}$. This type of thing is what you get when number systems form organically like human language, with people making it up as they go along, instead of being *designed* from first principles.

So how *did* the ancient Romans perform such common tasks as adding up the cost of items in a transaction? They converted Roman numerals to an abacus-type representation. Not necessarily beads on wires the way we usually picture an abacus, but as simple as pebbles lying in a groove that can be slid back and forth. And that's definitely positional and fairly well-suited to adding and subtracting.

We have no record of their pebble-in-groove type of abacus, but the British Museum has an excellent example of a portable Roman mechanical abacus:

![Roman abacus](images/pg65_1.jpg)

Roman abacus

The results could then be converted back to Roman numerals. The abacus indicates symbols for a thousand, ten thousand, one hundred thousand, and a million. The rightmost two columns show the fraction counter as the number of twelfths, and a way to indicate how many thirds of $\\frac{1}{12}$ after that. *That* is positional notation, and it is even ordered the same way as our positional numeral system today.

The design of Roman numerals suggests they originated in a medium where it took a lot of work just to make a line. Carving **IV** in stone takes three chiseled lines, instead of **IIII**. Writing **X** takes only two chisel lines, instead of four lines for **VV**. Obviously an **L** is far easier to carve than **XXXXX**. Considering how difficult it is to chisel a curve, the notation **C** for one hundred and **D** for five hundred suggests they did not expect to use such large-magnitude integers very often. For a thousand, Romans eventually used **M** (the most common form today) but earlier used this symbol: ↀ. That symbol is clearly not chisel-friendly, so it is easy to see how **M** (short for *mille*, Latin for thousand) came to be substituted when carving stone. There is also a symbol ↁ for five thousand, and ↂ for ten thousand (a ↂ is visible on the abacus above) which appear in the present-day Unicode character set.

Sometimes it is said that the Indians invented the concept of zero. They may have been the first to use zero as a numeral, but the above abacus shows a zero: all beads down. Any culture that uses an abacus has a representation for zero, and it is the starting point for any calculation. The Romans could certainly communicate zero as *nullus*, the Latin adjective for “none.”

When we use modern computers, the computer converts our decimal input into binary, performs the operations, then converts the result back to decimal so we can more easily read and understand it. That seems to be how Europe worked for hundreds of years; they would *communicate* numbers with Roman numerals, but if they had to do any actual *arithmetic*, they converted to abacus format with positional notation, did the operation, then converted back to Roman numerals. The Romans were not as arithmetically challenged as their numeral system suggests. They obviously had all the powers of 10 they needed to engineer the Colosseum.

## 4.3 Almost Binary Encoding: Cistercian Numerals

![Cistercian Numerals were probably killed by Gutenberg's invention of movable type.](images/pg66_1.jpg)

Cistercian Numerals were probably killed by Gutenberg's invention of movable type.

If tally marks are one of the bulkiest ways to express numbers, *Cistercian numerals* have to be one of the most compact ways humans have ever developed to write numbers. They were introduced around 1200 AD by the Cistercian monastic order as an alternative to Roman numerals, and were used for a few hundred years. They originated in a form of shorthand used by English shopkeepers, because they were economical not only for area but also for pen strokes.

Their definition varied from monastery to monastery, but the most common original form for digits 1 to 9 looked like this:

![](images/pg67_1.jpg)

For the number of tens, reflect about the horizontal axis:

![](images/pg67_2.jpg)

For the number of hundreds, flip the unit symbols about the *vertical* axis:

![](images/pg67_3.jpg)

There is one corner left, and they used it for the thousands place:

![](images/pg67_4.jpg)

But instead of treating these symbols as numerals, they combined them into a single glyph, like this:

![](images/pg67_5.jpg)

If you want a zero in any place, you simply leave that corner unadorned. While a plain bar would represent zero, there is no evidence that a plain, unadorned bar was ever used. Cistercian numerals were used for numbering things, not for arithmetic, and it did not occur to them to start numbering with 0 instead of starting with 1.

For early hand-copied books, paper was precious and they made the most use they could of the space it offered. Imagine writing a page number like 1368 above in Roman numerals: **MCCCLXVIII**, ten characters. In Cistercian, you can write 1368 with four or five pen strokes, picking the pen off the paper three times, but if you write it in Roman numerals, you need eleven pen strokes, picking the pen off the paper ten times. Cistercian is about three times more efficient. Once you get used to them, Cistercian numerals are also easier and faster to read.

As they evolved, their users started writing them vertically, and the 5 was often written as a combined 1 and 4 instead of as a dot:

![Later form of Cistercian numerals, with four examples](images/pg68_1.jpg)

Later form of Cistercian numerals, with four examples

It is a positional notation, with up to four places. In fact, it is *two-dimensional* positional, not the one-dimensional left-to-right positional notation we are used to.

There are elements of binary-coded decimal (BCD) in Cistercian numerals. They were *so close*. Like, the symbols for 7, 8, and 9 are just the symbol for 6 combined with the symbol for 1, 2, and both 1 and 2. They were tantalizingly close to discovering a *logical binary encoding*. Suppose the inventors had instead decided to define 1 through 9 like this, where the new line segments are shown in red and the line segments that are dropped are shown in gray:

![](images/pg69_1.jpg)

So, what happened to Cistercian numerals? They are very easy to write, and with a little practice, easy to read (certainly easier than reading Roman numerals for integers that large). What happened was this man and his invention, around 1450 AD:

![Gutenberg and his invention](images/pg69_2.jpg)

Gutenberg and his invention

Johannes Gutenberg's world-changing invention of a printing press with movable type for characters cast in lead. How many bins would be needed to hold every Cistercian numeral? *Ten thousand*.

Unlike the hand-copied Bibles produced by the Cistercian monks, none of the Gutenberg Bibles have page numbers. When Hindu-Arabic numerals finally spread throughout Europe, printing with just ten characters 0–9 was a thousand times easier than printing Cistercian numerals with movable type. Cistercian numerals fell into extreme obscurity.

They had an unusual resurgence among French Freemasons, around 1780. Tight secrecy of special knowledge is a hallmark of Freemasonry, and knowledge of how to write numbers in a concise way that was utterly baffling to non-members fitted perfectly into a group with secret handshakes, secret passwords, and secret oaths.

Another resurgence almost happened in the 1930s, in Nazi Germany. Perhaps Nazi scholars noticed that the 0–9 system came from India via Arab traders and felt that system therefore went against German nationalism, whereas Cistercian numerals are entirely European in origin. The resurgence did not get far. Besides being very impractical to print, just try to imagine how difficult it would be to invent a *typewriter* for them. Even with backspacing and over-typing, you would need an additional 36 keys to type each of the four corner digits plus a key for the central bar.

Amusingly, Cistercian on a modern display made with light segments would fit the (revised) Cistercian system beautifully. Imagine going to an airport and seeing flight numbers shown with a single character on a display with just 16 on-off segments (in addition to the always-on center stem), yet able to represent any of ten thousand flight numbers.

![What 4-digit flight numbers would look like had Cistercian survived](images/pg70_1.jpg)

What 4-digit flight numbers would look like had Cistercian survived

Who knows; perhaps someday Cistercian will be added to Unicode using a set of *composable* characters, which would take up just one Unicode slot (64 characters).

## 4.4 Hindu-Arabic Numerals Spread to Europe

In the 1st century AD, Indian notation for numbers 1–9 looked like this:

![](images/pg71_1.jpg)

Like so many number systems, it starts out as tally marks and switches to something easier to write when it reaches four tally marks. It was a positional system like we use today. We do not have a record of them using a circle for zero that long ago, so they probably used a blank to indicate a zero in a position like the ten's place or the hundred's place.

Imagine trying to write those numerals as quickly as possible; that means switching to cursive where you avoid taking the marker off the writing medium while writing a single numeral. Also, there seems to be some human preference for making characters similar in height, so the first three numerals need some vertical padding.

That would explain how the numerals evolved in India to look like this by the 9th century, with every numeral taking only a single squiggle to write:

![](images/pg71_2.jpg)

By then there was definitely a small circle to indicate a zero, and it is easy to see the tally marks for one, two, and three turned into cursive. It is confusing to us that the symbol for five looks exactly like a modern 4, but no, that really does mean five.

Arab traders picked up the Indian system, and as it spread from east to west, by the 11th century the numerals evolved into this:

![](images/pg71_3.jpg)

Perhaps because these are recognizable to us now (though the 4 is a little peculiar), the numerals became known as “Arabic” despite being an Indian invention. “Hindu” used to refer to the region and culture, and only later meant the religion.

The first European to realize and publicize the power of positional notation with 0–9 numerals was an Italian named Leonardo Bigollo Pisano (“Leonardo, traveler from Pisa”), an accomplished mathematician who published *Liber Abaci* (Book of Calculation) in about the year 1200 AD, very close to the time the Cistercian monks created their numeral system. Never heard of him, you say?

![Leonardo Bigollo Pisano](images/pg72_1.jpg)

Leonardo Bigollo Pisano

He was the son (fi, in Italian) of a man named Bonacci, so he is today better known by his patronymic name:

*Fibonacci*.

Yes, *that* Fibonacci. Besides bringing us the 0–9 positional system, he introduced Europe to the “Fibonacci series” 1, 1, 2, 3, 5, 8, 13,… which was known to the Indians, where each number is the sum of the two previous numbers.

The techniques we learn in elementary school for pencil-and-paper arithmetic spread quickly, and those using those techniques were called *algorists*, as opposed to the *abacists* who still used an abacus to calculate. It was as if a cult of warriors trained in Asian martial arts had arisen among a population that only knew how to fist-fight, and they knew how much advantage it gave them. Being able to use a writing instrument to add, subtract, multiply, and divide very large numbers much faster than can be done with an abacus felt like a superpower to those who took the time to learn the algorist art. The algorists understood the secret power of being able to notate zero in particular, for which the word was one that sounds like “cipher”; to this day that word conveys a clandestine way of doing things.

Finally, Western civilization had a number system with mathematical underpinnings and one that was easy to write by hand, no pebbles or beads needed. A string of numerals *d[i]* that could be any symbol from 0 to 9 was a shorthand for a polynomial of the number ten:

Isaac Newton and Leibniz share credit for the invention of calculus in the 1600s, but Leibniz also did something no one else did. He noticed that positional notation also worked for bases other than ten, and in particular he found great elegance in using just the symbols 0 and 1 to represent any number. Binary arithmetic. Leibniz invented it in 1689, though he gave ample credit to the Chinese for ancient notations that used a similar idea. An English translation of his introduction to the idea follows:

Explication de l'Arithmétique Binaire, Die Mathematische Schriften, volume 7, page 223.

In seeing the concept of binary, I think Leibniz was the first person who “got it” and realized it was a game-changer. It took a few hundred years for the rest of the world to catch up with him. But again, binary notation is *not* human-friendly, nor is it economical to set in type. To write a number like 72 in decimal is **1001000** in binary, seven characters instead of just two characters. The human eye is better at pattern-matching alphabet-like symbols than it is at traipsing over a long sequence of just two symbols and keeping track of which **0** or **1** digit in the list is being viewed. Binary is not as bulky as using tally marks, but still bulky compared to decimal.

Cistercian numerals are super-compact, but were once impractical for typesetting. So the Hindu 0–9 positional system won out as the practical middle ground. Perhaps, hundreds of years from now, humans will have evolved to use hexadecimal as their primary digit system, eliminating the errors in human-computer number conversion.

## 4.5 Scientific Notation and Automatic Computing

The word “anthropomorphize” describes a recurring theme in this chapter. Here is the usual dictionary definition:

It could also mean “to design human characteristics into nonhuman things,” like when robots are made to look as much like humans as possible (androids) instead of being optimized for their intended purpose. We can talk about doing so as *anthropo-morphization*. A seven-syllable mouthful, but a useful word.

Charles Babbage proposed the Analytical Engine in 1837, and it was to have an ingenious (and ambitious) system of mechanical gears that could perform programmable computations with *decimal* positional notation. He anthropomorphized the human 0–9 numeral system into the machine. That made the machine so ambitious that Babbage's plan to actually build it never got off the ground. It was to have had a memory of 1000 decimal numbers, with 50 digits each. Why so many digits? Because that gives you *dynamic range* of from 1 to 10^(50), using simple integer odometer-like hardware. The design predated scientific notation or the concept of a floating decimal point, and it greatly complicated the gear-based design.

It was commonplace to avoid the use of large numbers of zeros in a number using phrases like “One followed by twenty zeros,” but what we now call *scientific notation* was first specified carefully by Leonardo Torres Quevedo in 1914. He wrote a remarkable paper in French, the title of which translates as “Essays on Automatics,” about the use of machines to imitate not just the physical actions of humans but their reasoning powers as well (that is, he was anthropomorphizing).

Here is a translated excerpt that laid out a potent idea:

Reprinted in *The Origins of Digital Computers*, Brian Randell ed., page 102.

There it is. The invention of floating-point format, and also the invention of scientific notation of the form *n* × 10*^m* where the significant digits are *n*, and *m* is the exponent. He perceptively said the number of significant digits should be six, or eight at most, matching what we now call “single precision” floats. What he writes as “341862;–5” is what a modern program would print as “0.341862e-5”, very close to current notation. He did not propose a method of representing *negative* values, notice; his “n” is a fraction ranging from 0.100000 to 0.999999, not a signed value. Some people will stop at nothing to avoid dealing with negative numbers.

The “quantities involved in the calculations” correspond to the temporary use of higher precision to minimize rounding error, but not as high as double precision. He could not have anticipated that programmers would want to over-insure against rounding error by using double-precision floats with 15-decimal accuracy for *every* real variable.

Notice that there is no provision for storing the number zero, nor does he consider any exceptions that arise, such as dividing by zero.

Quevedo also accurately estimated the dynamic range needed for conventional calculations as well within 10^(−99) to 10^(99). He knew that 10^(−9) to 10⁹ would not be sufficient, so he elected a two-digit (decimal) exponent representation, and then it became overkill, but sufficient to do the job. There is nothing to indicate that he considered number bases other than the number of fingers that humans have.

In the late 1930s, Konrad Zuse conceived the Z-1 computer as a *mechanical* binary computer that stored its **0** or **1** states using sheet-metal and pin linkages. He built it on the family dining room table. Remarkably, it implemented the Quevedo idea of a separate significand (15 bits) and exponent (7 bits). Zuse could not get the representation of zero working, though he knew it was needed; he fixed that in a later version, the Z-3, that used electromechanical relays instead of linkages. Both the Z-1 and Z-3 computers worked, so they were history's first binary computers capable of floating-point calculations. The only thing they lacked was electronic switching speed.

John Atanasoff, in late 1937 (independently of Zuse) realized the need for binary representation and Boolean arithmetic, but he wanted an all-electronic machine so he used vacuum tubes. The machine used 50-bit (equivalent to 15-decimal) integers, not floating-point, to solve systems of linear equations. Atanasoff conceived of the idea of a data store separate from whatever device performs arithmetic, and coined the term “memory” for that part of a computing device.

![The reconstructed 1942 Atanasoff-Berry Computer with its unprecedented ideas](images/pg76_1.jpg)

The reconstructed 1942 Atanasoff-Berry Computer with its unprecedented ideas

A scaled-down prototype was finished in 1938, and the full-scale design for solving up to 29 equations in 29 unknowns was finished in 1942. World War II effectively ended the efforts of both Atanasoff and Zuse.

In 1940, John Mauchly and J. Presper Eckert were planning an *analog* device at University of Pennsylvania, but when Atanasoff communicated to Mauchly the idea of “true” computing, as he called it (what we now call *digital* computing), Mauchly and Eckert pivoted from building an analog Electronic Numerical Integrator (ENI) to building a digital Electronic Numerical Integrator And Computer (ENIAC), finished in February 1946. Instead of true binary with Boolean logic, they wanted the ENIAC to do arithmetic the way people do, so they used the on-off states of vacuum tubes to count from 0 to 9 and then do a carry operation, imitative of the classic algorithms for elementary school arithmetic that Fibonacci had conveyed from the Indians. Constants were ten-digit decimal integers, set by mechanical rotary dials; it held twenty such constants.

## 4.6 The Emergence of Bit-Field Mentality

*Bit-field mentality* is a line of reasoning that goes something like this:

That is what Quevedo and Zuse did. Had Quevedo actually built his design, he would have realized that the devil lies in the details. Zuse noticed that representing zero was hard, creating an exception to the rules of scientific notation. Bit field design stems from the urge to anthropomorphize, and it leads to inefficiency and nonmathematical behavior.

In the early 1950s, when IBM was just introducing electronic (vacuum tube) computing, they used bit-field mentality to design their *integers*. “Let's use the first bit to represent the sign of the integer, and the rest of the bits to represent the magnitude.” At the time, it seemed as good a way as any. Engineers could look at bit patterns and (almost) read the binary, with a little practice, since the signmagnitude representation mimicked the human way of writing integers with a “+” or “-” in front of positional-notation digits. Like, in six-bit precision, **0****00101** means +5 and **1****00101** means -5.

But what about two ways to write zero, as “positive zero” **0****00000** and “negative zero” **1****00000**? Do they represent the same real number, zero? Or is there something else going on? If I test **1****00000** < **0****00000**, will the computer return True or False? The workaround is, *if the magnitude bits are zero, the sign bit does not count.* That means the hardware has to test for a special case, which slows things down; it also means “every bit counts” is not true, at least not always. It was one of the first cases of a redundant bit pattern: more than one bit pattern to represent the same number.

That was just the beginning of problems with the humanlike sign-magnitude representation. Think back to grade school, probably around 5th grade, when you first learned about negative numbers and how to add and subtract signed integers. You had to master, in your mind, a flowchart that looks like this:

![How to add signed integers, elementary school style](images/pg78_1.jpg)

How to add signed integers, elementary school style

It was not long before more careful thinkers realized that using 2's complement arithmetic (described in [Chapter 1](#chapter1.xhtml)) makes this entire flowchart go away and avoids “negative zero.” The circuits for adding unsigned integers and signed integers become one and the same, except for defining where they overflow. It was a less human-friendly way to encode integers, but much more computer-friendly, and every computer now uses 2's complement format to store integers.

When you combine bit-field mentality with anthropomorphized scientific notation, you get *floating-point format*. This is quite different from an engineering approach of first setting out desirable properties of a format as design goals. It is also different from the mathematical approach of asking what is a logical mapping of a set of bits to a vocabulary of real numbers.

The most successful scientific computers of the 1950s were from IBM and a “word” of data was 36 bits, not 32 bits. The IBM 704 was the first commercial system to support floating-point arithmetic, with vacuum tubes as switching elements.

![The IBM 704 was a 1950s vacuum tube computer that supported floating-point arithmetic. Photo from Unità Centrale-Museo Scienza Tecnologia Milano](images/pg79_1.jpg)

The IBM 704 was a 1950s vacuum tube computer that supported floating-point arithmetic. Photo from Unità Centrale-Museo Scienza Tecnologia Milano

It could perform a floating-point add or subtract in 84 microseconds, which was quite a respectable speed for that era; to do a multiply or divide took about five times as long.

That model and its more reliable transistor-based successors used this 36-bit format for single-precision floating-point numbers:

![Early IBM floating-point format](images/pg80_1.jpg)

Early IBM floating-point format

The word “Characteristic” is in quotation marks because it was IBM's term for the exponent, but it is not the correct mathematical term. In the days when logarithm tables were used to multiply and divide numbers, the fraction part of log(*x*) was called the *mantissa*, and if you subtracted the fraction from log(*x*), the integer part that was left was the *characteristic*. So if the log(*x*) was 2.30, the mantissa was 0.30 (the part you looked up in the tables) and the characteristic was 2 (for which you were expected to be able to add or subtract with pencil-and-paper). But if the log(*x*) was -2.30, the mantissa was 0.70 and the characteristic was -3, always keeping the mantissa as a value between 0 and 1. As the above figure shows, that is *not* how IBM's floating-point worked. The “Characteristic” bit field should have been called “Biased Exponent” where the bias is 128. To make matters worse, Arthur Burks started calling the fraction part the “mantissa,” again confusing floats with logarithms, and the confusion over terminology persists to this day.

In the above example, the exponent bits represent *m* = 6 and the fraction bits represent $n = \\frac{18513}{2^{16}} \\approx 0.\\text{282486}$. The sign bit being **1** means the value is negative (sign-magnitude representation, like IBM used for signed integers in the 1950s). So the value is $- n \\times \\text{2}^{m} = - \\text{2}^{\\text{6}} \\times \\frac{18513}{2^{16}} = - \\frac{18513}{1024} \\approx - \\text{18}.0\\text{791}0\\text{1}$ (the accuracy was slightly more than 8 decimals). The documentation for the computer uses the above example and states that the value represented is -18.0790, which suggests that its author worked it out manually and made a transcription error or a rounding error.

Because IBM also introduced Fortran in 1956, the first commercial language of higher level than Assembler and one that recognized the floating-point instructions, IBM began its path to dominance of scientific computing, with Sperry (the UNIVAC series) and Burroughs as its main rivals.

IBM's format looks much like the one proposed by Quevedo, with two exceptions:

*   There is a way to represent negative values.
    
*   The base of the scale factor is 2, not 10.
    

Like Quevedo's proposal, there are a lot of different ways to represent the same value, and that is never a good thing. Every bit should count, but if the fraction bits are all zero, then the exponent bits do not count. Nor does the sign bit.

To make matters worse, you can divide the fraction by two (shift the bits right by one place) and increase the exponent by one, and it is *exactly the same number* (if the rightmost bit of the fraction was a **0**). Similarly with shifting left and decreasing the exponent. So, instead of having 2^(36) different real values, there are far fewer. The “information per bit” is reduced by redundant ways to represent the same value.

## 4.7 The Rise and Fall of IEEE Std 754

There were dozens of small companies (or small divisions of large companies like General Electric) trying to enter and succeed in the computer business in the 1960s and 1970s, with names that are mostly forgotten. They had wildly different floating-point formats. The number of bits for exponent and fraction (and where they were placed) were different; the way of encoding the signs of exponent and fraction were different; some were base-2, some base-8, and some base-10.

One base, that used by the biggest player in the industry, was base-16. IBM switched from the 704 format described above to “Hexadecimal Floating Point” (HFP) when it introduced its highly successful System/360 family of mainframes in 1964, and the word size was changed from 36-bit to 32-bit; the wobbling accuracy caused by using 16 as the number base (see [Section 2.7](#chapter2.xhtml#sec2_7)) caused their format to wobble between about 6.3 and 7.5 decimals of relative accuracy, effectively making the accuracy only 6.3 decimals in calculations of any length. The IBM 704's single precision at least produced over 8 decimals of relative accuracy as the outputs of plus-minus-times-divide, which was frequently sufficient. Many scientific applications produced unacceptably inaccurate results when ported to IBM's new design.

The solution was obvious: Use double-precision (64-bit) float format, which was supported on the System/360 from its inception. That was back in the days when fetching and storing data to memory was *much* faster than doing an arithmetic operation on a floating-point number, so switching to double-precision was a no-brainer. It became routine for programmers of technical codes to make all the real variables double precision, without thinking about which variables actually needed to have around 15 decimals of accuracy.

Arithmetic operations got dramatically faster over time, but memory access over physical distances improved slowly. “The Memory Wall,” where it takes hundreds of times longer to fetch or store a float than to do arithmetic with it, did not become obvious until the late 1970s. Rewriting software is extremely expensive, so we are now trapped in our use of overkill precision for many applications involving real numbers, largely because of that one decision by IBM to use HFP in the design of the System/360.

Why did some kind of *de facto* standard not form to coalesce around a single way to represent real numbers? Having a unique format means it is very difficult to switch vendors, and vendors liked that. The data files computed with the existing machine might contain a mix of integer and character and float data, and while you might be able to port integer and character data to a different computer brand, extracting the float data and converting it could be a nightmare. If the destination format had a smaller dynamic range, that would cause overflow and underflow. If it had fewer bits of fraction, that could cause accuracy to drop below what was acceptable. It was what marketing people call a “lock”; once a customer, always a customer.

### 4.7.1 The Computing Industry Gets Emancipated

Chip designer Intel was on a roll in the 1970s, having pivoted from making the first commercial DRAM memory chips to making the first microprocessors. Their first microprocessor, the Intel 4004, operated on four bits of data at a time, and the chip had about 2300 transistors; it took considerable innovation to squeeze the design into a single chip. It became practical for the first time to put some smarts into microwave ovens and traffic light controllers, and perhaps build four-function calculators. Intel co-founder Gordon Moore speculated that the optimal density of transistors would double every year; he later revised that to every *two* years, and chip designer Carver Mead dubbed that prediction “Moore's law.” Engineers were designing much more capable microprocessors like the Intel 8080, which could make computers so cheap that they could one day become *personal computers*.

But there was another plot arc going on, between the heavy-hitters in the computing industry: Sperry, IBM, Honeywell, and other makers of the large-scale “mainframe” computers of the 1960s. Mauchly and Eckert had used their experience with the government-funded ENIAC to develop computers practical enough to sell commercially through Sperry. Sperry had patented the idea of an electronic digital computer and was charging royalties from other computer makers. IBM brokered a patent-sharing agreement with Sperry, so IBM actually benefited from the barrier to entry into the market created by the royalty charges much the way Sperry did.

At Honeywell, someone stumbled on the fact that Atanasoff's 1937–1942 electronic digital computer was shown to Mauchly well before Mauchly and Eckert decided to switch from analog to digital and begin building the ENIAC, and that perhaps it was possible to break the Sperry patents. A federal case began, one of the longest and most expensive in US history. After seven years, 32,000 exhibits, and a 20,000-page transcript of testimonies, Judge Earl Larson ruled that the patents were *invalid*. An excerpt from his ruling:

Cited by Clark Mollenhoff in *Atanasoff: Forgotten Father of the Computer*, 1988, page 210.

The news of the verdict was buried by the timing; it came out the same day as the “Saturday Night Massacre” of the Watergate Scandal.

Eckert and Mauchly certainly deserve credit for the massive amount of work they did to commercialize Atanasoff's ideas, and Sperry remained a powerful contender among the largest computer companies, but the barrier to entry was gone. Whether you agree with Judge Larson's conclusion or not, you have to admit that the result was that *no one* owned the broad patent on electronic digital computing; anyone could enter the market without fear of infringement or having to pay hefty royalty payments. And here were Intel and Motorola and other companies making increasingly capable microprocessors with transistor counts doubling every two years.

Besides the legal barriers to entry, the technical problem of designing an entire computer had been just as daunting for a small company. But with microprocessors, that barrier was also gone. The skill set needed to hook together the processor and memory and keyboard and display was something an electrical engineering student could do as a senior project. The computing industry was emancipated as it had never been before.

### 4.7.2 The True Origin of IEEE Std 754

![John Palmer, 1946–2017](images/pg84_1.jpg)

John Palmer, 1946–2017

Rivals Motorola and Intel continued to improve their microprocessors, with transistor density improving to the point where they could consider working with more than 8 bits of data at a time. Intel started work on a 16-bit processor called the i8086 that could address more than the 2^(16) (“64K”) bytes of memory that limited the first generation of personal computers from Apple, Commodore, and Radio Shack (Tandy). Bruce Ravenel was the lead architect of both the i8086 and a slower version called the i8088 that had the same instruction set but worked with 8 bits at a time to lower costs.

Everyone wondered how IBM could enter the personal computing market; it certainly did not fit their traditional sales model. IBM did something unprecedented in its history: It outsourced both the processor design (Intel) and the creation of an operating system (Microsoft). Work began in the late 1970s to create what would become the IBM PC.

In 1976 an Intel engineer, John Palmer, proposed that the i8086 and i8088 could have a coprocessor, one designed specifically to perform floating-point operations, to make the IBM PC more suitable for workstation-style technical computing.

Intel executives expressed strong skepticism that there was a viable market for such a chip, but Palmer was so convinced that he said if he were paid one dollar for every such chip sold, he would forgo his salary. The project was finally given the green light in 1977, and Palmer frequently told me he wished they had taken his offer because it would have made him a very wealthy man.

The IBM PC was designed with an empty socket for an optional i8087 right next to its main processor, the i8088. Microsoft's Bill Gates expressed his opinion to Intel, “You're not going to fill many of those sockets.” But the i8087 floating-point copro-cessor sold many millions of copies for $150 each, continued selling for years (unlike most chips), and held its price instead of having to drop in price with Moore's law (also unlike most chips).

Berkeley professor William “Velvel” Kahan had given a guest lecture at Stanford ten years earlier, about the outrageously bad results possible in the floating-point arithmetic of some computer makers. It made an impression on Palmer, who heard the lecture as a student. Palmer hired Kahan as a consultant for the i8087 project.

![William “Velvel” Kahan, ca. 1980](images/pg85_1.jpg)

William “Velvel” Kahan, ca. 1980

Kahan (rhymes with “John”; the “h” is silent) had consulted for Hewlett-Packard on the algorithms for their scientific handheld calculators that used decimal scientific notation with ten decimals of accuracy, and an exponent that ranged from 10^(−99) to 10^(99). Decimal arithmetic is the right choice for calculators because it eliminates the problem of rounding error when converting numbers from decimal (the Human Layer) to binary (the Compute Layer), and although it runs slower, speed is not an issue with handheld calculators.

In his consulting role, Kahan immediately and adamantly set down three ground rules for the number format:

*   It would use a decimal scientific notation, not binary.
    
*   All operations and functions would be reproducible across computer systems.
    
*   The higher-precision version of the 64-bit format would be 128 bits wide.
    

He lost all three arguments. Ravenel and Palmer said they were already too far down the design path to make design changes. The 64-bit format would be binary, with a sign bit, biased exponent, and a fraction with a hidden bit that is always **1** just left of the radix point. The higher-precision version of the format would be 80 bits wide, and all calculations would covertly be done with that 80-bit “extended double” precision. That way, Intel could claim that any differences between their 64-bit computations and that of other vendors was because Intel's were *better*, and this would be a selling point. So, irreproducibility and unportability were a key part of Intel's strategy.

As Intel's consultant, Intel tasked Kahan not with making design choices but instead with becoming their paid advocate for every design choice that Palmer and the chip designers had made. Kahan was stubborn and not given to compromise, and the discussions were exasperating to Palmer, but Palmer eventually prevailed.

Palmer and Kahan published the i8087 design choices as a proposed “standard” way to do floating-point in 1979, and announced the i8087 chip in April 1980. Because of Kahan's reputation as an expert in computer arithmetic, everyone incorrectly assumed he was the architect of the design.

![The Intel i8087 floating-point coprocessor chip](images/pg87_1.jpg)

The Intel i8087 floating-point coprocessor chip

Motorola began designing its own floating-point coprocessor chip, the Motorola 68881, to follow that proposed standard. But computer companies like IBM, Digital Equipment Corporation, and others saw the proposal as a threat and asked IEEE to form a Standards Committee so they could have input into the proposed standard and level the playing field. That was the origin of what we now call IEEE 754 (the official name is IEEE Std 754™).

### 4.7.3 The Two Kahans

It is an interesting exercise to go through Kahan's writings and his (unrefereed) web postings to classify his position statements into two categories that are perfect opposites. They are:

*   *Anything less than perfection in computer arithmetic is not to be tolerated.*
    
*   *Perfection is an impractical goal; speed and low cost are more important.*
    

To pick a few from the first category in his writings:

> “Almost all True is altogether a Lie.”
> 
> “Every violation of Mathematics is always punished sooner or later. (The punishment does not always befall the perpetrator.)”
> 
> “This is no place to list all the corrections *Excel* needs. It was cited here only to exemplify Errors Designed Not To Be Found.”
> 
> “Routine use of far more precision than deemed necessary by clever but numerically naive programmers, provided it does not run too slowly, is the best way available, with today's mixture of popular programming languages with overtaxed underfunded education, to diminish the incidence of roundoff-induced anomalies below any level of commercial significance even if we knew about every anomaly.”

And in the second category,

> “A machine whose every function rounds correctly is impractical.”
> 
> “Faster matrix multiplication is usually too valuable to forego for unneeded exact reproducibility.”
> 
> “Rather than waste time testing every element for troubles that almost never happen, a program can run faster on average by testing one or two flags after the array has been computed and, if a flag was raised, recompute the array some better way.”
> 
> “Consequently numerical anomalies go mostly unobserved or, if observed, routinely misdiagnosed. Fortunately, most of them don't matter. Most computations don't matter.”
> 
> from [https://people.eecs.berkeley.edu/~wkahan/](https://people.eecs.berkeley.edu/~wkahan/)

By flipping between the two extremes, Kahan was able to defeat both those who criticized Palmer's choices for being too-perfect as well as those who thought things could be made better (such as by making the math functions correctly rounded, as Kahan originally wanted). He was a very effective “hired gun.” His lengthy epistle mocking Microsoft *Excel* for using hidden extra precision to reduce rounding error in visible digits is followed, on the next page, by a touting of Intel's use of 80-bit hidden extra precision to reduce rounding error in visible digits.

### 4.7.4 The i8087 Design Becomes the IEEE Standard at Last

![kludge \[klo͞oj\] NOUN  A workaround or quick-and-dirty solution that is clumsy, inelegant, difficult to extend and hard to maintain.](images/pg88_1.jpg)

**kludge** \[klo͞oj\] NOUN  A workaround or quick-and-dirty solution that is clumsy, inelegant, difficult to extend and hard to maintain.

After many years of intense argument (mostly over Kahan's insistence on subnormal number support, also called “gradual underflow”), IEEE Std 754 was approved and published in 1985. It is not free; anyone wanting to use it has to pay $100 to IEEE for a copy of the Standard. Palmer once told me, chortling, that “Whatever was in the 8087, that's what's in the IEEE Standard.” Intel had won its battle. While IBM and Cray resisted following the Standard for the next decade, most vendors adopted (most of) the Standard, believing it would lead to data portability (which it did), and identical results on different computer systems (which it did not).

When a format starts with a few dubious choices, such as underflow to zero, that leads to the need for other dubious choices such as “gradual underflow” that complicate the circuitry and create numerical hazards. The format ignored the 1950s lesson of *not* using sign-magnitude arithmetic, so once again there was “positive zero” and “negative zero.” Are they equal? Yes, they decided. The two kinds of zero should test as equal. But their reciprocals should be *positive infinity* and *negative infinity*, so now you have a format where *x* can equal *y* but a function *f* (*x*) can be as far different from *f* (*y*) as you can get. When an engineer creates a hasty solution with flaws and then adds more hasty solutions to patch those flaws, it is called a *kludge*.

Palmer decided to have a special bit pattern for indeterminate results like $\\frac{0}{0},\\log( - 2)$, and he called it “NaN” for “Not a Number,” even though imaginary numbers and complex numbers are, well, numbers. The bit test only applied to the exponent bits, however, leaving a vast set of bit patterns representing the same NaN. Two of the patterns were carved out to mean –∞ and ∞. Here are how many bit patterns were wasted saying a result is a NaN (IEEE half was added to the Standard in 2008):

 
| **Precision** || **Number of NaN Patterns** ||  |
| --- | --- | --- |
| IEEE half (16 bits) || 4094 || (over 6 percent of the bit patterns) |
| --- | --- | --- |
| IEEE single (32 bits) || 16 777 214 ||  |
| IEEE double (64 bits) || 9 007 199 254 740 990 || (slightly over 9 trillion) |

How would NaN work in comparison operations if it was not a specific bit string? The first axiom of Aristotelian logic is that A is A; a thing is equal to itself. But incredibly, the decision was made that NaN is *not* equal to itself. The web got ever more tangled. The mathematically absurd concepts of “positive zero” and “negative zero” created a mess of contradictory statements about how they should be handled. The 754 Standard is almost 100 pages long.

To support the Standard in hardware, the logic circuitry has to handle this set of exception cases:

![](images/pg90_1.jpg)

The IEEE Std 754 format, 32-bit example, and the exception cases in a nutshell

While I suspect Kahan was initially appalled at being tasked with defending signed zero, he eventually did the mental gymnastics required and pronounced it a Good Thing because it could help with a concept called “branch cuts” in complex arithmetic. To make this work, the Standard requires yet another counterintuitive exception that the square root of “negative zero” should be “negative zero.” I am not making this up.

There were originally four rounding modes; more have been added in revisions of the Standard, but once you have multiple rounding modes, you remove any hope of guaranteeing the same results across different computing systems, even if all you do is plus-minus-times-divide. Scientific computing favors banker's rounding (round to nearest, with ties to even), but graphics accelerators favor truncation (round toward zero) since it is faster and usually has an imperceptible effect on image quality.

Another guarantee of Never Twice the Same Answer was that the *transcendental* math library functions (logarithms, exponentials, trigonometric and inverse trigonometric functions) do not have to be correctly rounded, according to the Standard. Correct rounding would mean different computing systems would get the same result down to the last bit, if they used the same rounding mode.

Kahan reversed his initial demand for reproducibility and wrote position papers about how difficult and utterly impractical it would be to have such a requirement. Like a lawyer, he proved able to take either side of any design decision. He advocated for Intel by citing mathematics when Intel's choice improved accuracy or correctness, and by citing practicality when the choice worsened either one.

### 4.7.5 A Bold Claim of Round-Trip Perfection

In his 1983 commentary “Mathematics Written in Sand,” Kahan boasts that you can square an IEEE float, and if it does not overflow or underflow, you can then take the square root and get back the absolute value of the original number exactly. *Always*. What a marvelous property! Here is the relevant text from that commentary:

[https://people.eecs.berkeley.edu/~wkahan/MathSand.pdf](https://people.eecs.berkeley.edu/~wkahan/MathSand.pdf)

An overflow would produce infinity and remain infinity when we take the square root, letting us know that something went wrong. Similarly, an underflow would presumably produce zero, and remain zero when we then take the square root, also informing the user that the value is wrong.

Shall we give it a try?

Let's set *x* = 2.646978 × 10^(−23) as a single-precision IEEE float. Now square it and round it with the default rounding mode (banker's rounding), and you get

  
*y* = *x*² ≈ 1.401298 × 10^( − 45).  

So it did not underflow to zero. The Standard states that square roots must be correctly rounded, so now try taking the square root and see if we get back 2.646978 × 10^(−23), the *x* we started with, down to the last decimal:

  
$$z = \\sqrt{y} = 3.743392 \\times 10^{- 23}$$  

,Not a single decimal in the answer is right. How could a mathematician like Kahan be *that* wrong? The explanation reveals something about IEEE floats that very few computer technologists seem to know: IEEE floats have *tapered accuracy*. Not the same kind of tapered accuracy as posits, but it is there.

Remember the decimal accuracy plots from [Chapter 2](#chapter2.xhtml)? Here is what the decimal accuracy plot looks like for IEEE single precision:

![Accuracy plot for IEEE standard 32-bit precision floats, with tapered accuracy on the left](images/pg92_1.jpg)

Accuracy plot for IEEE standard 32-bit precision floats, with tapered accuracy on the left

For most of the range (from about 10^(−38) to 10^(38)), decimal accuracy wobbles between about 7.2 to 7.5 decimals. But what is that ramp over on the left, from about 10^(−45) to 10^(\-38)? The accuracy ramps down to almost nothing, with no decimal digits correct. Those are the *subnormal* floats, and every IEEE precision has them. So the *x* that I chose has its square at the low end of that ramp, which is why not a single decimal digit was correct in computing $\\sqrt{x^{\\text{2}}}$.

Realizing this could happen, Kahan came up with a “read the fine print” workaround: He created his own definition of what “underflow” means. To every other computer programmer and user I have known, “underflow” means “what happens when a result is too small to represent” and you know it happens by looking at the output, zero. But the IEEE Standard says that the underflow flag must also be set if the result of an operation lands in the subnormal region *and is not exact*. But it is *not* too small to represent; it simply had to be rounded. So now that is “underflow”? How is anyone supposed to know that a processor flag was set? By using a low-level debugging tool and stepping through the compiled code one machine instruction at a time, watching the processor flags?

For decades, Kahan raged that computer language standards should provide access to the processor flags, and he was ignored. It did not happen. Only in the last few years have the C and C++ language standards committees entertained the idea of supporting viewable processor flags, but it is probably too late. Legions of C and C++ programmers have no idea that there are versions of their language that let them know about processor flags. The Java programming language specifically *forbids* the use of processor flags, which led Kahan to write an amusing but not very mathematical diatribe titled, “How Sun's Java Hurts Everyone Everywhere.”

Some have objected to the tapered accuracy of posit format, saying tapered accuracy spoils classic theorems about accuracy that apply to floats. The objectors appear to be completely ignorant of the fact that IEEE float format has tapered accuracy. It is a strange tapering because it is only on one side, and it is steep.

Researchers at Argonne National Laboratory, late in the 1990s, figured out an elegant way to have symmetrical tapered accuracy for large-magnitude numbers instead of wasting bit patterns on all the ways to represent NaN, and wrote a very cogent proposal to the IEEE 754 Committee to consider for their next revision: “gradual overflow.” The committee rejected it immediately. It would spoil backward compatibility. The only revisions that tended to be accepted in the 2008 and the 2019 revisions of IEEE Std 754 were the inclusions of new precisions, like half-precision and quadruple precision. Those were completely new, so they would not spoil the behavior of the float types previously specified.

Speaking of overflow, let's try Kahan's $\\left. \\sqrt{x^{2}} = ~ \\middle| x \\right|$ claim out on *large* magnitude numbers. Suppose we write a short program with *x* = 10^(160) with all variables in IEEE 64-bit (double) precision, something resembling this:

```
double x, y, z;
x = 1.0e160;
y = x * x;
z = sqrt(y);
print z;
end
```

If you run it a few times on a machine with an Intel or AMD processor, you might very well get 1.0e160 for z, that is, 10^(160) as hoped, but you might find that it occasionally instead produces Inf to indicate that the answer overflowed to infinity.

*What in the world*? So you might try the quickest type of debugging, that of inserting a print statement to see what could possibly be going wrong.

```
double x, y, z;
x = 1.0e160;
y = x * x;
print y;
z = sqrt(y);
print z;
end
```

Now you run it, dozens of times, and it *always* gives the answer Inf. You take the “print y” statement out, and it goes back to producing 1.0e160 most of the time, but not always. So you get out the low-level debugger and step through the code, carefully. It always produces Inf.

This is one of the most dreaded and exasperating types of programming bugs: The act of debugging, that is, observing what is going on, *changes how the program behaves*. The bug has a slang term, a “heisenbug,” named after physicist Werner Heisenberg who stated the quantum mechanical principle that the act of observing an event can change the event. To use an image from the early PC era when the electronics were big and clunky:

![A 1980s programmer experiencing a heisenbug.](images/pg94_1.jpg)

A 1980s programmer experiencing a heisenbug.

As with underflow, finding the source of this bug reveals another consequence of the choices Palmer made in designing the i8087. The squaring of 10^(160) is being done, *covertly*, in the 80-bit registers even though all the variables are declared to be 64-bit precision. The 80-bit registers can handle the square, which is 10^(320), and the square root then returns 10^(160) and converts it back to 64-bit precision.

But if you try to observe what is happening, the processor will convert the temporary result back to 64-bit precision. IEEE 64-bit precision can only store numbers up to about 1.8 × 10^(308), so 10^(320) overflows to infinity. Both print statements and debuggers conceal the use of covert 80-bit precision, the feature that was supposed to make Intel arithmetic “better” than the competition that actually uses 64 bits and 32 bits when that is what the program specifies.

Why would the original program sometimes produce 10^(160) and sometimes infinity? Operating systems occasionally have to swap out a running piece of code by saving the state of the processor, doing some housekeeping function, and then restoring the state. That state includes the register contents, but anything in the 80-bit temporary register is converted on-the-fly to a 64-bit float, causing it to overflow. Hence, IEEE arithmetic is not only unportable across systems, but it can also produce *different answers on the same computer with the same data*.

When Sun Microsystems was creating the Java programming language in the 1990s, an absolute design requirement was that it produce the same answer on *any* computer. A lead engineer on the project, James Gosling, figured that real number operations were easily made to behave identically by stating that they follow IEEE Std 754, done. After all, it says “Standard” right there on the label. He was horrified to discover that it was not that kind of standard at all; the only thing it really standardized were the locations and meanings of the bit fields so that float data could be interchanged between computers. When it comes to performing arithmetic, it should have been called the IEEE 754 *Guidelines*. This forced the Java designers to build their own floating-point arithmetic out of integer operations, bypassing the IEEE-float-specific hardware in everyone's processor. Kahan was livid about this, but it could have been avoided had he won his argument with Palmer in the first place, stipulating that results should be perfectly reproducible.

### 4.7.6 Postlude: Farewell to IEEE Floats

Not many computer technologies last more than a few years, and by the year 2005, the IEEE version of scientific notation was looking very long in the tooth, indeed. The major chip-makers decided that the exceptions were rare, so they could be handled in software instead of hardware. This simplified the hardware to processing only *normal* floats, saving chip area and execution time. Sun Microsystems made the mistake of trapping NaN exceptions to the operating system, which could take millions of times longer to handle NaN than previous versions of their processors. High-frequency stock traders found the new processors unusable, since NaN exceptions are common when the trading algorithm is missing some vital data and thus no trade should occur.

Intel, AMD, and ARM did better, trapping exceptions to be handled with microcode in their processors, which could take 200 clock cycles instead of the usual 3–8 clock cycles for normal floats. However, taking longer to do something is externally viewable, so a third party can use timers to figure out the data being processed without having permission to do so. That is called a *side-channel attack*, and researchers at UC San Diego were able to use the disparate timing to hack into web sites and steal data.

A fatal blow to IEEE floats was struck with the rise of Graphic Processing Units (GPUs), because those not only tend to turn off any exception handling, they flush subnormal numbers to zero. That meant that when you port an IEEE float to a GPU, it represents a *different number*. The data interchange part of the Standard broke.

There was nothing left to make the word “Standard” applicable.

The next stage of the farewell to IEEE floats was the rise of Machine Learning (ML), and Artificial Intelligence (AI) that actually lived up to its decades-old promise. But 32-bit IEEE floats were overkill for what was needed, and the 16-bit IEEE floats had insufficient dynamic range. Thus began a free-for-all with companies designing their own ways to represent real numbers, very much like the days before the 1985 Standard came out and every vendor had its own way of doing things. That is where things stand as I type this; full support for IEEE Std 754 in hardware is almost extinct. We need not mourn the loss, because we are once again open to a clean-slate, *mathematical* design for a real number format.

Much of the preceding history is not in previously-published form. It is from the many hours of conversations I have had with John Palmer, William Kahan, and others who were part of the process.

## 4.8 Lessons Learned

The mismatch between how humans like to record and process numbers and how machines can best store and manipulate them has been going on for hundreds of years, with the machines eventually becoming optimized. The most recent episode was trying to use the bits on a computer to mimic human scientific notation, instead of taking the approach that every bit counts.

Standards committees should avoid any members who have a conflict of interest, like large manufacturers of existing products. This seems like common sense, but IEEE does just the opposite and *requires* the presence of such manufacturers. The result is that we have a floating-point “standard” that is actually a proprietary Intel design from the 1970s, one that includes a raft of choices made by biased parties.

Any engineering effort should begin with a list of design goals. They often compete with each other, but at least the tradeoffs can be decided with clarity. What should be the design goals for a system of representing real numbers with a string of bits in a modern electronic computer? There should be very little objection to the following goals, starting with the most important ones:

1.  The distribution of the values represented should resemble the distribution of numbers needed in calculations. That is, each bit pattern should be used approximately the same number of times (this is the principal of “maximum entropy” from information theorist Claude Shannon).
    
2.  There should be no redundant bit patterns to mean the same thing; every bit counts.
    
3.  The output of a program should be deterministic based on the source code and the input data, not affected by invisible “modes” of operation. The precision used must be exactly what is specified in the source code, no more and no less.
    
4.  All math operations should be correctly rounded. This, together with **3**, ensures perfect reproducibility and portability across computer systems.
    
5.  It should be easy to change precisions, like it is to change integer precisions.
    
6.  If a result is not a real number, it should have a representation that propagates that condition through every operation that follows so that the final output reflects the condition.
    
7.  It should be simple to build in hardware, and fast.
    
    In the “Nice to Have” category:
    
8.  It should be easy to scale the precision to any number of bits.
    
9.  Real numbers should map monotonically to signed integers so that they can use the same hardware for comparison operations.
    
10.  Similarly, the bit operation for negating a real representation should be exactly the same as for negating an integer, so they can use the same hardware.
     
11.  The results of application computations should be as close to results for exact computations as possible.
     

Remarkably, the i8087 and thus IEEE Std 754 *failed every single one of these goals*.

The next chapter is an annotated presentation of the 12-page *Posit™ Standard (2022)* that was ratified by the Posit Working Group. That Standard meets the first ten goals above and does a better job than floats on number **11**.

# 5 The Posit Standard, Annotated

![That is the entire Posit Standard (2022), simple and concise enough to fit on twelve pages.](images/pg99_1.jpg)

That is the entire Posit Standard (2022), simple and concise enough to fit on twelve pages.

Writing a standard is very different from writing an explanation, because the standard should be as concise as possible, and that means leaving out examples and the reasons that the decisions were made the way they were. Peter Lindstrom recommended that we write a document to accompany the Posit Standard that supplies those examples and reasons, which is the function of this chapter. Since the previous chapter explained the origins of IEEE Std 754, it is only fair to give the backstory on where the Posit Standard came from.

The chapters that follow do not depend on this chapter, so the reader should feel free to skim this chapter if it seems to be getting dull.

## 5.1 Singapore Backstory

![Downtown Singapore (the Marina Bay Sands in the foreground), and Fusionopolis, home of Singapore's supercomputer centre and also the birthplace of the posit number format and its standard document.](images/pg99_2.jpg)

Downtown Singapore (the Marina Bay Sands in the foreground), and Fusionopolis, home of Singapore's supercomputer centre and also the birthplace of the posit number format and its standard document.

Singapore has an amazing record of introducing big ideas to the rest of the world. The flash drive. Cell phone cameras. Ketchup. In 2015, there were two technology visionaries in Singapore, physicist Marek Michalewicz and the director of Singapore's NSCC supercomputer centre Tin Wee Tan, who saw promise in the *unum* number format I had just published. They arranged with Singapore's Agency for Science, Technology, and Research (A\*STAR) and the National University of Singapore (NUS) to bring me to that country to continue development of next-generation arithmetic to replace the outdated IEEE Std 754. We knew there was a disadvantage to overcome in unum format: The unum format was *not* hardware-friendly. The unum format was a “peace offering” to IEEE floats, an attempt to patch the flaws in that design by creating a *superset* of IEEE floats with three new fields:

![The original unum format was an IEEE-style float with metadata appended](images/pg100_1.jpg)

The original unum format was an IEEE-style float with metadata appended

It was a form of interval arithmetic, but extended to allow interval endpoints to be closed or open, and for the size of the exponent and fraction fields to vary as needed by the calculation. The ubit was described in [Chapter 1](#chapter1.xhtml): the presence or absence of a “⋯” to indicate there are more nonzero bits after the last one shown. This self-descriptive bit allowed the management of floating-point error to be automated (or eliminated). While they were fully supported in software and one group in China managed to build a custom chip to use unum arithmetic, working with unums proved to be much like working with character strings of varying length, with a need to allocate and free memory dynamically.

One way to use unums was to fix the exponent and fraction size and round after every operation, which allowed them to mimic, perfectly, IEEE floats. But that “backward compatibility” also prevented unums from meeting the design goals listed at the end of [Chapter 4](#chapter4.xhtml). There were redundant bit patterns, two ways of expressing the same real value. They did not map monotonically to signed integers.

The efforts in Singapore soon led to the realization that the last two properties could be achieved by discarding IEEE Std 754 altogether and beginning with the ring plots shown in [Chapter 1](#chapter1.xhtml). There were elegant ways to keep the property that flipping the ring about its horizontal axis produced the reciprocal of a number perfectly, making division as easy as multiplication. In early 2016, these were introduced as “Type II unums,” rebranding the original as “Type I unums.”

Type II unums always use the same number of bits, solving the objection to Type I, but introducing another difficulty: arithmetic required table look-up instead of the usual logic circuits. While Kahan had been characteristically critical of the original unum idea, in a public debate (June 2016) he stated this about Type II unums:

[http://www.johngustafson.net/pdfs/DebateTranscription.pdf](http://www.johngustafson.net/pdfs/DebateTranscription.pdf), pages 17–18.

Type II unums have their uses, and [Chapter 8](#chapter8.xhtml) will present one version. But it was the idea shown in [Chapter 1](#chapter1.xhtml) (giving up the idea of perfect reciprocals), that led to “Type III unums” that map to signed integers, are fixed size, and use all the standard logic circuits that chip designers presently use to design IEEE floating-point arithmetic. If the ubit is used to indicate the open interval between exact values, that is branded as a *valid* type, which have the error-free capability of Type I unums. If they are rounded after every operation, using the default banker's rounding of IEEE floats, they are branded as *posits*. I invented posits in December 2016 with the geometrical approach in [Chapter 1](#chapter1.xhtml), with insight from Isaac Yonemoto in figuring out how regime bits are decoded, and presented them at Stanford University in February 2017. They appeared to be particularly well-suited for Machine Learning, as Yonemoto demonstrated live at the end of the Stanford lecture. Credit for the creation of posits also goes to DARPA, which provided funding for linear algebra solutions using next-generation arithmetic. Hence the footnote in the Posit Standard:

The result was an international movement. The first paper, *Beating Floating Point at its Own Game: Posit Arithmetic* accumulated hundreds of citations as people tested the idea and designed hardware and software environments to support it. Without experimental data, that first paper made this initial guess:

Initial guess (2017) regarding how many exponent bits would be best for different posit precisions

A Posit Working Group was formed to establish a standard. It included experts from the US, Singapore, Canada, Germany, and the UK, all from universities or national research institutions; it *excluded* anyone with a commercial interest in selling computing hardware, to avoid the conflicts of interest evinced by IEEE committees:

It took five years to make sure the Posit Standard was as simple as possible, but no simpler. During the five years, hundreds of papers were published testing posits of various precisions on a wide variety of applications, and they all pointed to the same empirical conclusion: The best results are usually for exponent size *eS* = 2 or *eS* = 3, for all precisions. That was especially important in testing 8-bit posits for AI; an exponent size of 0 does not usually have enough dynamic range for the Machine Learning part of AI. So we changed the Draft Standard to this instead:

Years of experiments showed all precisions should use the same *eS*.

Then we realized a huge benefit to always having *eS* = 2 for all precisions: Conversion between precisions becomes trivial. Simply append zeros to raise precision, or round the least significant bits (as a binary fraction) to lower precision. There is no need to pull apart the pieces of a posit into sign, regime, exponent, and fraction. It is like changing a 16-bit integer to a 32-bit integer by right-shifting 16 places; there is really nothing to do. That means posits can “right-size” their precision in a fine-grained way without any performance penalty.

## 5.2 Overview Section of the Posit Standard

A primary goal was bitwise-perfect reproducibility, the goal that floats had failed and still fail to achieve. The last sentence is important because the Posit Standard does not specify *how* the requirements are to be met, only what the behavior must be. One designer might decide to put everything into hardware, including all the log and trig and other math library functions. Another may choose to create posit compliance entirely through software that uses integer data. Both extremes are acceptable, and so is everything in between.

That section is self-explanatory, but the reader may wonder why the ™ trademark symbol is used after the first use of the word “posit.” This was done on the excellent advice of Dutch-American computer scientist Peter Braam, developer of the Lustre™ parallel file system. While posits are open-source, there is always the chance that a large company will come up with their own version of posit format that corrupts its underlying principles yet still claims to be “posit” format. The trademark provides some measure of legal protection against that happening.

The last sentence is a potent one, and it is crucial for portability. Suppose there are multiple rounding modes, and those modes are optionally set by a user through an operating system call. That means a program, running on a single system and using a fixed set of input data, can produce multiple answers for reasons that are *invisible* in the source code and input data. This is why posits have only one rounding mode.

Another thing that can happen is that the programmer can invoke an “optimizing compiler” that changes the operations as if the laws of algebra apply. Because of rounding, they do not. For example, an optimizer might change

to

to save a multiplication operation. Such optimizations can still be offered, but with the warning that they make the resulting compiled program non-compliant with the Posit Standard. Computer languages generally specify the order of operations (like what to do when there are no parentheses), which leads to deterministic outcomes for the arithmetic.

The binary number formats have already been explained in [Chapters 1](#chapter1.xhtml) and [3](#chapter3.xhtml).

Listing addition, subtraction, multiplication, and so on means the Posit Standard includes specification of how to produce results of operations. The rule is very simple: If any input is NaR, return NaR as the output; otherwise, treat the inputs as exact real numbers, and return what the correctly-rounded result would be if performed with infinite-precision arithmetic. It is always possible to know what the correctly-rounded result would be using a finite amount of work; you simply compute to the point where you know how to round the result.

*Fused* expressions are interesting, and fused multiply-add was added to the 2008 version of the IEEE 754 Standard. It means returning round(*a* × *b* + *c*) instead of the usual round(round(*a* × *b*) + *c*). You can think of fused expressions as staying in the Math Layer for two (or more) operations instead of returning to the Compute Layer after every operation. A key part of the Posit Standard is that it specifies quite a few often-used functions that are fused, made of multiple operations evaluated with rounding only as the very last step. For example, it requires support for

  
$$\\text{hypot}(x,y) = \\text{round}\\left( \\sqrt{x^{\\text{2}} + y^{\\text{2}}} \\right)$$  

because it occurs quite often in technical computing. If it is programmed as individual operations, you would accumulate *four* rounding errors instead of $\\text{round}\\left( \\sqrt{x^{\\text{2}} + y^{\\text{2}}} \\right),$ with a single rounding only at the end. Writing code like

```
h = sqrt((x*x) + (y*y))
```

actually means asking the computer to do the following:

  
*h* = round(sqrt(round(round(*x* ⋅ *x*) + round(*y* ⋅ *y*))))).  

That can be written more concisely using the overbar notation ([Section 3.6](#chapter3.xhtml#sec3_6)):

  
$$h = \\overline{sqrt(\\overline{\\overline{x\\cdot x}+\\overline{y\\cdot y}}}).$$  

Whatever the rules for a computer language, if it supports posits, then the use of fused operations or non-fused operations must be visible in the code, never done covertly. We will see later why this prevents disasters.

The Posit Standard requires support for the functions you find on a scientific calculator: logs, exponentials, trig and inverse trig functions. We stopped short of mandating support for some of the more sophisticated functions like Bessel functions. Those can always be added to a future version of the Posit Standard.

While posits can replace floats in a program, it seems likely that both formats may coexist for a while, and there needs to be a way to convert posits to IEEE 754 floats and vice versa. So, the Posit Standard specifies how to do that for the various rounding modes and exception types of IEEE 754 floats.

The Standard also solves a subtle and long-standing issue: How should an indeterminate result (NaR for posits, NaN for floats) be converted into an integer, and back? Posits can do it properly, preserving the fact that a NaR result occurred.

It is extremely easy to convert between two posit precisions with the same exponent size *eS*, much like converting between two integer precisions. There is no need to decode the number. This is one of the reasons that Draft Posit Standard 4.0 changed to specifying that *eS* = 2 for any precision. Earlier Draft versions required that the precisions be restricted to *n* = 8, 16, 32, 64, … with corresponding *eS* values *eS* = 0, 1, 2, 3, …, in other words, *eS* = log[2](*n*) - 3. The ratified version of the Posit Standard described here does not restrict *n* that way. Strange precisions like 5-bit posits have proved useful for the *inference* task of AI, for example. A fixed *eS* also simplifies the work of the hardware designer.

The approach to explaining when any operation or function should return NaR is to apply a single mathematical principle, uniformly. This contrasts with using different rules for different functions, as is presently done for IEEE 754.

Because this is not a language standard, nor does it say how the functions in a math library are to be labeled, we refer to well-known math functions but only describe how they should behave, not how they should be spelled or parsed. A computer language will of course allow the writing of something like a = b + c, not the form *a* = **addition**(*b, c*) used in the Posit Standard.

There are no “recommendations” in the document because following recommendations or not following them leads to irreproducibility. Including recommendations makes a document a guideline, not a standard.

If someone wants to build a computing environment for 9-bit posits because they work well for AI, say, there is no need to support any other precision to be posit-compliant. The entire environment could be done in software, written using native integer operations, or (what seems more likely) the kernel operation of multiply-accumulate would be done with hardware that is as fast as possible, and most of the lesser-used operations like logarithms could be done in software.

## 5.3 Definitions Section of the Posit Standard

[Chapter 3](#chapter3.xhtml) introduced the concept of “ghost bits” beyond the end of a posit, which always have value **0**. Here is another figure illustrating the concept, where an “**x**” is an explicit bit and may be a **0** or a **1**:

![](images/pg107_1.jpg)

As the figure shows, while ghost bits are always **0**, they can play different roles depending on the explicit bits. Case 1 is the two exception values, either zero or NaR depending on the value of the sign bit. Case 2 is *maxPos* if the sign bit **x** is **0**, or −*minPos* if **x** is **1**. Case 3 is the “Twilight Zone” where exponent bits can be pushed off the end of the explicit bits by the length of the regime. Case 4 is the normal situation where the ghost bits are like the unexpressed bits of a decimal like “3.75”, which is the same thing as “3.7500000"”. The term “ghost bit” helps explain posit format, but for the sake of brevity, that phrase is not defined in the Posit Standard.

[Chapter 4](#chapter4.xhtml) disparaged the design of a number format by carving a word into bit fields resembling scientific notation. Posit arithmetic was invented by the geometric reasoning of [Chapter 1](#chapter1.xhtml) (the ring plots and the projective reals), which then *dictated* the bit fields, including one with a new and variable-length meaning, the regime.

For posits, an “exception” does not mean “throw control to an exception handler.” It means the software or the circuit must do something different since the regime value, –∞, is not representable with positional notation. Although the formula for zero correctly works out to 2^(\-∞), obviously the way to actually handle it is with a conditional branch for the case of all bits **0**.

For the case of NaR, this definition and its footnote represent one of the most profound departures from IEEE Std 754, which specifies that the arithmetic must also play the role of a debugger, constantly monitoring calculations for bad behavior and then either halting the calculation (“signaling NaN”) or continuing (“quiet NaN”). But that is what debugging tools do; they can set a breakpoint when a particular value occurs as a result. Once a program is debugged, you can turn off “debug mode” and compile it for maximum speed; that is standard practice, because compiling to enable debug mode can make a program many times slower than the optimal compilation. With IEEE floats, however, you have a debugger you cannot turn off. It spends energy on every clock cycle to check for exceptions even after the programmer has guaranteed that they cannot occur.

A side bit of history, while we are on the subject of bugs:

This is a fun story, and Grace Hopper later became an Admiral and one of the most respected computer pioneers of the 20th century.

![Grace Hopper (1906–1992), inventor of the concept of a programming language](images/pg108_1.jpg)

Grace Hopper (1906–1992), inventor of the concept of a programming language

Years before IBM introduced Fortran, she conceived of programs written in a high-level language that would run on any computer, and built a language environment that later evolved into COBOL.

We even have the actual moth, taped to a logbook that recorded the event:

![Literally the first computer bug](images/pg109_1.jpg)

Literally the first computer bug

The etymology (and entomology) is not quite right, however. Thomas Edison, decades earlier, used to write about getting the “bugs” out of his electrical inventions, so that slang was already in popular use. The log entry shows that they found it quite funny that the bug turned out to be, literally, a bug. It almost certainly is not Grace Hopper's logbook, but her team found it amusing and she (and her team) deserve credit for spreading the term “debuggers” for the software tools used to find errors in programs.

In preventing a program from stumbling into indeterminate nonsense, there are three lines of defense:

1.  The programmer is careful to think about all the possible ways things could go wrong, and makes sure the program handles exceptions in an intelligent way. Tools like debuggers and automated language analyzers assist the programmer with this task. Good compilers also issue warnings when the software does something dubious, like using a variable before it has been assigned a value.
    
2.  Failing that, modern languages like C will check inputs to mathematical operations and produce error messages when, say, the computer is asked to take the square root of a negative number or divide by zero, and the message (via the operating system) informs the user what went wrong.
    
3.  As a last line of defense, if somehow a processor is asked to do something that cannot produce a real number as a result, that can be handled by calling it NaR and propagating that invalidity through to the final output. It might happen that a programmer, confident the program will never misbehave, asks the compiler to disable all the exception handling of line-of-defense **2**, allowing it to run slightly faster since the math library routines do not have to first test if inputs are valid.
    

This is why posits make NaR the only exception that is part of the definition of the arithmetic. Some have said they really need positive and negative infinity, but that again confuses debugging and computing. It is hard to imagine anyone using a finished production code to “compute” infinity as a useful result. Line-of-defense **2** will generally provide the information when a result would be some kind of infinity, and why it happened. Nothing in the Posit Standard prevents a programmer from inserting constructs like

```
   if x = 0, print “-Inf”; halt;
   else y = log(x);
```

If you use the *valid* data type where posits ending in a 1 represent the real open interval between two exact numbers as described in [Chapter 1](#chapter1.xhtml), then you have a way to represent and compute with (*maxPos*, ∞) and (−∞, −*maxPos*).

Why not allow the number of exponent bits to vary, independently of the precision? The main reason is that it makes hardware more complicated, more power-hungry, and after years of experimenting with various sizes of the exponent field, the value “2 bits” turned out to be optimal for a remarkably large fraction of the experiments. Software for posit arithmetic can have this flexibility, and many open-source libraries exist that support a variable number of exponent bits.

In later chapters, we will see quite a few parameters that can be used to make posit format more general, not just the precision and number of exponent bits. There is a place for both standard posits and generalized posits; standard posits always have two exponent bits; they could be explicit bits or ghost bits, but as Yoda says, always two there are.

We are careful not to use *mantissa*, which would be the appropriate term if the represented values were logarithms, but within a binade, the values are equispaced so the correct mathematical term is *fraction*.

The fovea, where relative accuracy is maximum, is when there are only two regime bits (**0****1** or **1****0**); that happens for fully half of all the bit patterns. In that case, taking into account the sign bit and two exponent bits, all but 5 bits are available for expressing the fraction. If *n* is the precision, the fraction has *n −* 5 explicit bits for the central-magnitude values, which is almost always the region where most of the computing takes place.

This may be a place where the Posit Standard is a little *too* terse. Exact evaluation is not always necessary nor even possible, because it could require that an infinite number of digits be evaluated. Perhaps a better wording would be, “rounded the way an exact evaluation of an expression involving more than one operation would round” since that means the evaluation need only be accurate enough to determine how it rounds. Recall that this was the way the Math Layer was defined.

There are many more fused operations for posits than there are for IEEE floats, which allows calculations to stay in the Math Layer for more of the calculation and therefore accumulate less rounding error.

Binary float formats use a “hidden bit” to the left of the fraction bits; it is **1** for normal floats, and **0** for subnormal IEEE floats. But because posits are based on 2's complement arithmetic, the significant digits being scaled represent a value that ramps from 1 up to almost 2 for positive values, and from −2 to almost −1 for negative values. In 2's complement, **0****1** is 1 and **1****0** is −2.

For example: If the fraction bits are **011**, that means **0.011** = $0 \\times \\frac{1}{2} + 1 \\times \\frac{1}{4} + 1 \\times \\frac{1}{8} = \\frac{3}{8},$ regardless of the sign. If the sign is positive, the implicit value plus the fraction is $1 + \\frac{3}{8} = \\frac{11}{8},$ but if the sign is negative, the implicit value plus the fraction is $- 2 + \\frac{3}{8} = - \\frac{5}{8}.$ This is a very machine-friendly way to do things, but just as with 2's complement integers, it is not very human-friendly.

The LSB and MSB need no further explanation. The formulas for *maxPos* and *minPos* as a function of the precision *n* are easily explained. The largest positive value *maxPos* is **0****111**⋯**111**, where the **1** bits in the regime go all the way to the end of the explicit bits (and are then terminated by a **0** ghost bit). The *n* - 1 regime bits represent the integer one less than the run length, or *n* - 2. The *uSeed* value for standard posits is 2^(2²) = 2⁴, so *maxPos = uSeed^n*^(\-2) = 2^(4 ()*^n*^(\-2)) = 2⁴ *^n*^(\-8). We could similarly derive the smallest positive value, *minPos*, represented by **0****000**⋯**001**, or simply observe that *minPos* = 1 / *maxPos* = 2^(8-4) *^n*.

Much has already been said about NaR. “Not a Real” corrects the error in the Intel i8087 of calling it “Not a Number” when it really means not a *real* number. I was amused to see this exceptionally honest airport signage for a time of boarding:

![The airport is (unintentionally, I assume) informing us that they have absolutely no idea when the plane is going to board. Apparently their software uses IEEE floats and converts them to integers for display.](images/pg112_1.jpg)

The airport is (unintentionally, I assume) informing us that they have *absolutely no idea* when the plane is going to board. Apparently their software uses IEEE floats and converts them to integers for display.

The word “NaN” (rhymes with “ran”) is a homophone with a woman's name “Nan” and a child's name for a grandmother, “nan.” But “NaR” (rhymes with “far”) has the advantage of being a unique word in proper English; it has no homophones.

The Posit Standard refers to the number of (explicit) bits in a posit so often, the variable *n* always has that meaning throughout. If you go as low as *n* = 1, all you have is zero and NaR; that does not seem very useful; there is no *minPos* nor *maxPos* value. Hence, the Posit Standard sets 2 as the smallest possible number of posit bits.

As the magnitude of a posit becomes large, the consecutive value spacings become larger than 1 and that means skipping over integers. This happens with floats as well; for example with 16-bit IEEE floats, you can count from 0 up to 2048, but the next larger value is 2050. There is no way to represent 2049. There is a non-obvious general formula for *pIntMax* as a function of *n*:

Let's plot the exponent, ⌊4(*n*−3)/5⌋, as a function of *n* for *n* from 2 to 32:

![The power of 2 where standard posits start skipping over integers, as a function of posit precision](images/pg113_1.jpg)

The power of 2 where standard posits start skipping over integers, as a function of posit precision

That shows why you need the ceiling function ⌈⋯⌉ in the formula; for the case of *n* = 2, it goes to −1 and then $2^{\\lfloor{4(n - 3)/5}\\rfloor} = 2^{- 1} = \\frac{1}{2},$ which is not an integer. Rounding that up to 1 with the ceiling function gives the correct *pIntMax* for the extreme case of the smallest possible number of bits in a posit.

This is consistent with terms like “single precision” and “double precision” or “8-bit precision”: it is the number of bits available to express a number and is **not** the same as “accuracy.” This was covered in [Chapter 2](#chapter2.xhtml), but it bears repeating because many people who should know better still confuse precision and accuracy. For example, the sawtooth pattern of relative accuracy in float formats was first called “wobbling precision,” and the term stuck even though the *precision* is steady as a rock. The precision of the significant bits is also constant; no wobble there. It is the *relative accuracy* that wobbles. This was explained in [Chapter 2](#chapter2.xhtml).

The *quire* is a fixed-point format with enough precision to compute posit dot products (a sum of products) **exactly**. It is sufficiently powerful, and important, that it has an entire chapter dedicated to the ways it can be used. The idea of hardware support for an exact dot product, sometimes called a *scalar* product, comes from Karlsruhe professor Ulrich Kulisch, who introduced it in the 1970s but has been unsuccessful at getting it into any of the IEEE standards.

Notice the distinction between *quire* and *quire value*. Whereas *quire* is a format (a set of bit fields and their meanings), a *quire value* is the real number represented by a bit pattern in quire format. Similar care is taken in the Posit Standard to distinguish *posit* (a number format) from *posit value*. Our Working Group member Hauke Rehr deserves credit for noticing inconsistent wording in early drafts and making sure the wording is consistent. In this book, I frequently use “posit” to mean “posit value” where context makes it clear, like “the product of two posits.”

If the quire can store a dot product *a*[1] · *b*[1] + *a*[2] · *b*[2] + … + *a[m]* · *b[m]* of two vectors of length *m* (up to some maximum length, which here is about two billion elements), then it can also compute sums exactly up to some maximum length. Just think of one of the vectors being all 1 values: *b*[1] = *b*[2] = … = *b[m]*; then the dot product is the sum of the *a[i]* values. Summing numbers is much less demanding than summing *products* of numbers, so the maximum length of a sum that can guarantee no possibility of overflow or rounding errors is much larger than two billion. You would have to add *maxPos* to the sum, over and over, 2^(23+4) *^n* times, to get the sum to overflow. Even for 8-bit posits, the quire sum limit is about 36 quadrillion summations. One of the largest sources of cumulative rounding error in floating-point programs is summations of many numbers, so the Posit Standard makes clear that the quire can eliminate that accumulation of rounding error, and also enables parallel processors to perform accumulation perfectly so the result matches that of serial execution.

[Chapters 1](#chapter1.xhtml) and [3](#chapter3.xhtml) have already explained the regime and regime bits, but since the Posit Standard fixes the number of exponent bits at 2, there is no need to define the *uSeed*, and many of the definitions are greatly simplified. In the Posit Standard, the *uSeed* value is always 2^(2²) = 16.

There is no need to use the phrase “correctly rounded” in the Posit Standard, since all rounding is required to be correct. Every real number rounds to exactly one posit value, and there is only one way to do it.

Note the distinction between *sign*, which is –1, 0, 1, or NaR, and the *sign bit*, which can be **0** or **1**. The Posit Standard avoids oversimplifications like treating the sign as (−1)*^s* where *s* is the value of the sign bit.

Because the implicit value is −2 for negative posit values and 1 for positive posit values, the implicit value plus a fraction in \[0, 1) produces a significand in either \[−2, −1) or \[1, 2). Unlike floats, the significand includes the sign of the value.

## 5.4 Posit and Quire Formats Section

There is a simple reason why computers are usually designed with datum sizes that are integer powers of 2, like 16, 32, and 64: It eliminates the cost of multiplying two integers when you index into an array. All you have to do is shift the index left and add the base address. This is likely to continue to be the case, so the Posit Standard gives example sizes of 8, 16, and 32 bits, even though it also applies to strange sizes like posit5, for example.

The 64-bit example is conspicuously absent; this is because there is far less need for such high precision with posit format. For the case of two exponent bits, the quire is always 16*n* bits long, and every bit counts as a significand bit because it is a fixed-point number. That means posit16, which has about 5 decimals of accuracy in the fovea, is backed by a quire with 16 × 16 = 256 bits of accuracy, which is about 76 decimals. That is more accuracy than an octuple-precision IEEE float. When more accuracy is needed, the quire can do more than exact dot products; it can also do extended-precision divides and square roots through a technique described later on.

While it is typical to describe a float or a posit as ±(1 + *f*) × 2*^e* where *f* is a *fraction* in the range \[0, 1), it is also true that they can be expressed with two *integers* as *K* × 2*^M*. Unlike IEEE floats, posits have the elegant property that the ranges for *K* and *M* are always symmetric about 0. For example, for posit16, *K* goes from -4095 to 4095 and *M* goes from −56 to 56. For precision *n* posits with *n* > 4,

If *n* = 2, 3, or 4, *K* goes from −1 to 1 because the fraction bits are always ghost bits, **0**. The *M* range shown above still holds for *n* = 2, 3, or 4. The *K* range is important for hardware design because, among other things, it tells how large the integer multiplier will have to be. The multiplier is often one of the more expensive parts of the arithmetic logic in terms of chip area.

In contrast, for IEEE binary16 (half-precision floats), *K* goes from −2047 to 2047 and *M* goes from −24 to 15, and there really is no pattern for the ranges for different precisions since the number of exponent bits is not designed as a simple mathematical function of the precision.

One way to describe a fixed-point format with *m* bits to the right of the radix point is to say it is an integer that represents a multiple of 2^(\-)*^m*. That is like the explanation in the Posit Standard. The footnote was prompted by one researcher asking the interesting question, “Does the product of two *n*\-bit posits always fit into a posit with 2 *n* bits?” It does, though the proof is tricky.

Some numerical analysts claim dot products of single-precision floats can—*almost* always—be made accurate by using double precision to hold the pairwise products and for the accumulated sum, then converting the sum back to single precision. The argument is, a double-precision IEEE float always has enough fraction bits and exponent bits to hold the product of two IEEE single-precision floats, which is true, but what about the accumulation?

Consider the dot product of these two single-precision vectors ***a*** and ***b***:

Every element of each vector can be expressed with a single-precision float without rounding. In fact the values are whole numbers. For example, “8.0 × 10⁷” is just the scientific notation for “eighty million.” The pairwise products *a[i]* · *b[i]* are

Try summing the numbers in single precision, and you get 0.0 exactly. Just for the sake of caution, use double precision to hold the products, and sum them in double precision as well. The straightforward way to add is left to right,

Again, you get 0.0 exactly. Doing it left-to-right takes three addition steps. If there are two hardware adders that we can use in parallel, we might instead evaluate it pairwise to do the sum in only two steps:

and again, using IEEE double precision, we get 0.0 for the sum. Getting 0.0 for a dot product of two vectors is often very important because it means the vectors are *orthogonal*. That is, the vectors are exactly at right angles to each other.

There is only one problem, however. The correct answer is **2**.

For this simple calculation, rounding led to *infinite* error. The vectors are **not** orthogonal.

The word panacea comes from the Greek for “cure-all,” so it literally means the first definition, but because things claimed to be cure-alls almost never actually work for *all* ailments, the word has come to mean an *overclaim*, something to be suspicious of. “Perpetual motion machine” is the same way; while it means a machine that runs forever, it has come to mean “a false claim of perpetual motion.” In numerical computing, double precision is a panacea… the second definition. It cannot make sums of products free of error, as the example shows. So the footnote is intended to point the reader away from “double-precision posits” and instead to the quire, which can do exact sums of products up to at least two billion such products.

This table is intended as explanatory, not essential to the definition of the format. All the entries can be derived from the other parts of the document, but it seemed too useful to be able to see the dynamic ranges and significant bits and other properties of the example sizes, and in the rightmost column, formulas for the properties as a function of a general precision *n*.

This section is the first to use color-coding, similar to the color-coding used in this book to make bit fields clearer. We toyed with the idea of making the colors part of the Posit Standard, but decided against it.

The table below shows the red-green-blue (RGB) and cyan-magenta-yellow-black (CMYK) components I *recommend* to those writing papers on posits, as a guideline. These colors were determined with the help of readers who have the most common form of color blindness (red-green).

 
| Field, Color || R    G    B || C    M    Y    K |
| --- | --- | --- |
| Sign, red || 1.00 0.33 0.33 || 0.00 0.67 0.67 0.00 |
| --- | --- | --- |
| Regime repeating part, gold || 0.80 0.60 0.40 || 0.00 0.25 0.50 0.20 |
| Regime termination, brown || 0.60 0.40 0.20 || 0.00 0.33 0.67 0.40 |
| Exponent, blue || 0.25 0.50 1.00 || 0.75 0.50 0.00 0.00 |
| Fraction: black || 0.00 0.00 0.00 || 0.00 0.00 0.00 1.00 |

RGB and CMYK color values for the color-coding of posit bits

[Chapter 1](#chapter1.xhtml) explained the case of *eS* = 0, and [Chapter 3](#chapter3.xhtml) introduced general *eS* values; the “explicit bit” and “ghost bit” methods were used there. The Posit Standard uses a slightly different explanation that is specific to the case of *eS* = 2.

The observation that a string of all 0 bits, together with an infinite string of ghost bits, represents an *r* value of -∞, did not occur to me until after the Posit Standard was ratified; otherwise this section could have been simplified. From the point of view of a designer, however, it is still best to call attention to the fact that special handling is needed when *r* = -∞.

Spelling out the fraction bits with Σ summation notation makes unambiguous what they mean, for anyone not familiar with “decimals” that use a base other than ten.

The formula *p* = ((1 − 3 *s*) + *f*) × 2^((1−2) *^s*^()×(4) *^r*^+*^e*^+*^s*^) looks quite different from the formula you usually see for a normal float, which looks like (−1)*^s* ×(1 + *f*) × 2*^e*^(−bias), so those familiar with floats often react with puzzlement. Because the implicit value is 1 for positive posits and −2 for negative posits, (1 − 3 *s*) is a simple formula that reproduces those two values as a function of the sign bit. The scaling 2^((1−2) *^s*^()×(4) *^r*^+*^e*^+*^s*^) could have been written 2^((−1))*s*×(4 *r*+*e*+*s*), but the convention of writing (−1)*^s* is a little silly since it implies you actually have to call a power function to raise −1 to the power of *s*. All you need is a function that returns 1 if *s* = 0 and -1 if *s* = 1; the function (1 − 2 *s*) is a simple way to accomplish that. The *s* value also shows up in the (4 *r* + *e* + *s*) term, and that is because posits are based on 2's complement. To negate, flip all the bits and add 1.

Eleven people spent an enormous amount of time on this document, and not one of us noticed that “integal” should be “integral”; our brains tend to fill in that missing “r” so those who have studied the Posit Standard also have not noticed this typo. Or at least, no one has reported it to us. Also, if *n* = 2, the *I* and *F* fields disappear completely and we have nothing but the sign and carry guard bits. So we should have noted that, since bit annotations *I*[8] *[n]*[\-17] and *F*[8] *[n]*[\-17] make no sense when *n* = 2.

The sign *S* is the usual red color-coding, but the remainder of the fields are all shown in black, because they are simply positional notation like the fraction bit field. The “8 *n −* 16 bits” deserves an explanation. The smallest positive posit, *minPos*, is always **0****00**⋯**00****1** where the run length *k* is *n −* 2 bits (the precision, less 1 for the sign bit and 1 for the regime termination bit). That bit string represents a regime value of *r = −* (*n −* 2) = 2 *− n*. Recall that the *uSeed* is 2^(2²) = 16 when *eS* = 2, so *minPos* = 16^(2−)*^n* = 2^(4·(2−)*^n*^) = 2^(8−4) *^n*. In computing a dot product, we might have to accumulate products that are as small as *minPos*² = (2^(8−4) *^n*) ² = 2^(16−8) *^n*. Similarly, *maxPos*² = 2⁸ *^n*^(−16). Hence, the integral part *I* and fractional part *F* are 8 *n −* 16 bits long.

The quire is always 16*n* bits total, so if we subtract the sizes of the *I* and *F* fields, we are left with something that does not depend on *n*:

After allowing for the sign bit, that leaves 31 bits for protection from carry overflow. The worst-case scenario is that you accumulate *maxPos*² over and over; you could do that up to 2^(31) − 1 = 2 147 483 647 (call it two billion) times with no possibility of overflow.

This is a first in number formats: The “exact dot product” idea also can represent NaR, and it is the same way posits do it: a **1** bit followed by all **0** bits. IEEE floats are ill-suited to something like a quire because of all their exception conditions; how would you represent all of the possible IEEE exceptions in a *fixed-point* number?

Saying the value represented by the quire *q* is an integer times 2^(16−8) *^n* is the same as saying the quire is a fixed-point format with the radix point 8 *n −* 16 bits to the left of the last bit. Here are some examples of quire values for a tiny posit, *n* = 3. The quire is 3 × 16 = 48 bits long, and the entire posit vocabulary is just eight items: {NaR, −16, −1, −1 / 16, 0, 1 / 16, 1, 16}:

 
| **Value** || **Quire bits (48-bit fixed point)** |
| --- | --- |
| 1 || **0****0000000 00000000 00000000 00000000 00000001.00000000** |
| --- | --- |
| \-1 || **1****1111111 11111111 11111111 11111111 11111111.00000000** |
| *maxPos*\=16 || **0****0000000 00000000 00000000 00000000 00010000.00000000** |
| *maxPos*²\=256 || **0****0000000 00000000 00000000 00000001 00000000.00000000** |
| *minPos*\=1/16 || **0****0000000 00000000 00000000 00000000 00000000.00010000** |
| *minPos*²\=1/256 || **0****0000000 00000000 00000000 00000000 00000000.00000001** |
| NaR || **1****0000000 00000000 00000000 00000000 00000000.00000000** |

Examples of 48-bit quire representations of various values when the posits have only 3 bits

The quire for 3-bit posits has its radix point just 8 bits left of the LSB.

## 5.5 Rounding Section of the Posit Standard

This is a formal algorithm for posit rounding, and it expresses the process slightly differently from the description in [Chapter 3](#chapter3.xhtml). If *x* is exactly expressible as a posit, there is nothing to do. If *x* is outside the dynamic range, saturate to signed *minPos* or *maxPos*. Otherwise, *x* lies between two adjacent *n-*bit posit values *u* and *w*. A diagram may be helpful in visualizing the above algorithm. Recall the projective reals and the ring plots of [Chapters 1](#chapter1.xhtml) and [3](#chapter3.xhtml), and zoom in on just one part of the ring:

![The real value in question, x, lies between posit values represented by U and one ULP higher](images/pg124_1.jpg)

The real value in question, *x*, lies between posit values represented by *U* and one ULP higher

The real values are on the outside of the ring. Values *u* and *w* are successive posit values (no other posits lie between them). We need to round to either *u* or *w*.

When you append a **0** bit to a posit, it does not change what it represents, but appending a 1 bit represents a new in-between value; the algorithm appends a **1** bit to *U* and writes it as *U***1**. The real value represented by *U***1** is *v*, as shown below:

![If there were n + 1 bits instead of n, the introduced new point tells us which way to round x.](images/pg125_1.jpg)

If there were *n* + 1 bits instead of *n*, the introduced new point tells us which way to round *x*.

In the figure, that determines that *x* should round to *u* since *x* is between *u* and *v*. If *x* had been between *v* and *w*, it should round to *w*. If *x = v*, the tie case goes to whichever of *u* or *w* is represented by a bit string ending in a 0 bit (“round to even”).

Many essential operations in scientific computing can make use of the quire to stay in the Math Layer as long as possible. If we use *i* to represent the imaginary number $\\sqrt{- 1},$ then multiplying two complex numbers *a + b i* and *c + d i* requires evaluating two expressions for the real and imaginary parts:

Both (*a·c* − *b·d*) and (*a·d* + *b·c*) are dot products. Doing them in the quire and then converting back to posit format reduces the number of roundings from three to one.

Using the quire also solves a classic problem when using complex arithmetic based on pairs of floats: Programmers discover that if they declare a variable to be complex and let the computer take care of operations like the above multiplication, it runs significantly and inexplicably slower than writing out the product as shown above, with real variables instead of complex variables. Why? It is because routines for complex numbers are trying to avoid catastrophic underflow or overflow when computing *a* · *c, b* · *d*, and so on. The programmer may know that there is no danger of overflow, but the math library routines do not know that and assume the worst, so they go through considerable machinations to avoid overflow and underflow and produce a correctly-rounded answer.

When computing a fused operation in parallel, it might be tempting to round the intermediate results before sending them to another processor. That is not permitted, because it leads to irreproducibility. For example, a single processor might compute a sum of posits *a* + *b* + *c* + *d* using a quire variable *q*, then round *q* to a posit *s*. That is, $s = \\overline{a+b+c+d}.$ If one processor computes *a* + *b* and another computes *c* + *d* in respective quire variables *q*[0] and *q*[1], they need to exchange *q*[0] and *q*[1], and not first round them to a local sum. That keeps fused parallel operations in the Math Layer until they are complete. Posits can restore the associative property of addition, up to some extremely large number of additions (the quire sum limit).

That said, the quire can be overkill. Doing a fused multiply-add, for example, requires fewer than 16*n* bits, so a system designer may choose to do fused multiply-add operations by some other means that is more economical. This is explicitly permitted in the Posit Standard, in the last sentence of the quoted paragraph.

The footnote points out that any operation in the list of math functions (the next section of the Posit Standard) made of composite operations must behave like a fused function. For example, computing **rSqrt**(*x*) means $\\overline{1/\\sqrt{x}}$ and not $\\overline{1/\\overline{\\sqrt{x}}}.$

Many language environments offer optimizations that increase speed at the expense of portability (and compliance with a standard). Sometimes portability is much less important than going as fast as possible, and the Working Group recognized that. However, for a computing environment to be posit-compliant, there has to be at least one mode of operation that follows the Posit Standard. The Posit Standard does not specify, for example, the order of operations when expressions are not parenthesized, but it does require that there be at least one mode where the ordering is *deterministic* by the source code and the grammar rules of the language, and only those modes are posit-compliant.

## 5.6 Posit Standard Functions

It was difficult to write this section without bringing in concepts from calculus; our goal was to keep everything understandable to anyone with a secondary school mathematics education. The phrase “arbitrarily close to a unique real number” evokes the concept of a *limit*. One way to express the rule in simple English is this: We are comfortable saying 2 times 3 is 6 for real numbers because approximately 2 times approximately 3 is approximately 6. But what is zero divided by zero? Approximately zero divided by approximately zero is *indeterminate*. If “approximately zero” means, say, between −0.001 and 0.001, that would include $\\frac{- 0.001}{0.001} = - 1,$ and $\\frac{- 0.0001}{0.000001} = 100,$ and $\\frac{- 0.001}{0} = \\pm \\infty.$ It could be any real number, as well as ±∞. That is why $\\frac{0}{0}$ must evaluate to NaR. The divide operation is not *continuous* in its inputs when the denominator is zero.

The math gets a little heavy here. Instead of “approximately” we say “in an *open neighborhood* of the value in the complex plane.”

The figure below shows the neighborhoods to be circles, but they can be any connected region that is open, that is, does not include its boundary.

![A function f of input arguments x and y, with their open neighborhoods in the complex plane](images/pg128_1.jpg)

A function *f* of input arguments *x* and *y*, with their open neighborhoods in the complex plane

If we cannot make the Result region arbitrarily small about a real-valued result by making the input neighborhoods arbitrarily small, then the result is NaR. Call it “the neighborhood rule.” It is not the same as saying “the function must be continuous” because it might be continuous in the complex plane yet not be real, like the arcsin function for a value greater than 1.

The power function is **pow**(*x, y*) = *x^y*. By the neighborhood rule, **pow**(0, 0) must return NaR. In any open neighborhood containing 0, *y* has both negative and positive values. Zero to a negative power is ±∞.

The IEEE Std 754 has a very different philosophy. It says **pow**(*x*, ±0) = 1, even if *x* is a (quiet) NaN. That is one of several ways that an indeterminate NaN result with floats can be made to disappear in a computation, and the user will never know anything went wrong. The IEEE Standard lists no fewer than *twenty* exception cases to the power function, things like, “**pow**(±0, *y*) is ±0 for finite *y* > 0 an odd integer.” The Posit Standard handles all those exceptions with the simple rule above, which is much more careful to propagate a NaR value and not regard inputs as exact numbers, since they will in general *have come from a rounded result*.

Graphs show the reason for “except for discontinuous functions of [Section 5.2](#chapter5.xhtml#sec5_2)”:

![Functions designed to be discontinuous for which the neighborhood rule does not apply](images/pg129_1.jpg)

Functions designed to be discontinuous for which the neighborhood rule does not apply

The neighborhood rule does not apply to these; they should not return NaR for real input because the behavior at the discontinuity is *well-defined*.

The **next** and **prior** functions are also not covered by the neighborhood argument, because they are functions of *bit patterns*, not real numbers. As such, there is no guarantee that a NaR will propagate correctly if a programmer really wants to do something as dangerous as manipulate posit bit patterns. If you think of the posits on the ring of projective reals, **next** moves one position counterclockwise, and **prior** moves one position clockwise. So, **next**(NaR) is -maxPos and prior(NaR) is maxPos, up at the top of the ring of posits.

This is another example of drawing the line between being an arithmetic standard or a language standard. Most languages require that inputs are promoted to the precision of the highest-precision input, to preserve as much information as possible. However, one could argue that that is like putting lipstick on a pig; if there is just one low-precision input, all inputs should be *demoted* to that low precision since the low accuracy will propagate to the output anyway. The Posit Standard does not take a side but merely says all posit inputs have to be the same precision, and whatever it is, that is the precision of the output.