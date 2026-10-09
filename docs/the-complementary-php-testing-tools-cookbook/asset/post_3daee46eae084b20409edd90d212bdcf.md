
# The Complementary PHP Testing Tools Cookbook

by Chris Hartjes

Contents Copyright ©2021 Chris Hartjes—All Rights Reserved

Book and cover layout, design and text Copyright ©2021 PHP Architect, LLC. and its predecessors—All Rights Reserved. Print and Digital copies available from https://www.phparch.com/books/.

php[architect] edition published: November 2021

Print ISBN: 978-1-957147-00-0  
PDF ISBN: 978-1-957147-01-7  
ePub ISBN: 978-1-957147-02-4  
Kindle ISBN: 978-1-957147-03-1

Produced & Printed in the United States

No part of this book may be reproduced, stored in a public retrieval system, or publicly transmitted in any form or by means without the prior written permission of the publisher, except in the case of brief quotations embedded in critical reviews or articles.

# Disclaimer

Although every effort has been made in the preparation of this book to ensure the accuracy of the information contained therein, this book is provided "as-is" and the publisher, the author(s), their distributors and retailers, as well as all affiliated, related or subsidiary parties take no responsibility for any inaccuracy and any and all damages caused, either directly or indirectly, by the use of such information. We have endeavored to properly provide trademark information on all companies and products mentioned in the book by the appropriate use of capitals. However, we cannot guarantee the accuracy of such information.

PHP Architect, php[architect], the php[architect] logo are trademarks or registered trademarks of PHP Architect, LLC, its assigns, partners, predecessors and successors. All other trademarks are the property of the respective owners.

Written by  
Chris Hartjes

Published by  
PHP Architect, LLC.  
9245 Twin Trails Dr #720503  
San Diego, CA 92129 USA

Editor  
Kara Ferguson

Layout  
John Congdon

406-PHP-ARCH (406-747-2724)  
info@phparch.com  
www.phparch.com

# Table of Contents

- 1. Getting Started
  - Audience
  - Why Make All This Effort?
  - The Application
  - Our Tools
  - Initial Set Up
- 2. Static Code Analysis Tooling
  - What Is It?
  - Why Should I Use It?
  - Who Should Be Using It?
  - How Do I Do It?
  - Bonus Round!
- 3. Mutation Testing
  - What Is It?
  - Why Should I Use It?
  - How Do I Use It?
- 4. Linting and Formatting Your Code
  - What
  - Why
  - How
  - When
- 5. Continuous Integration
  - Integrate Via Pull Request
  - Integrate Via Flags
  - Automating Integration and Testing
- 6. What's Next?
  - Editor/IDE Integration
  - Containerized Development Environments

# Foreword by Marco Pivetta

(Marco is a long-time and prolific contributor to Open Source PHP projects. I’ve been lucky enough to work with Marco for several years and I learn how to do something better almost every single time we go a code review or have a discussion surrounding software development. I asked him to take a look at this book and reflect on the changes he has seen in the PHP development community in the decade we’ve known each other.)

I’ve known Chris, the “grumpy programmer”, since almost a decade now: he and I share most of our views around how teams should keep control over software complexity and stability.

His long career around software testing, automation tooling and general betterment of developers that he managed to reach is showing its impact over our industry: a decade ago, testing was looked upon with skepticism within the PHP ecosystem, sometimes even frowned upon, “an expensive exercise.”

Where there was skepticism, there is now clear interest in testing on many levels, and the discussion shifted from “should I write tests?” to “what are the best testing techniques?”.

The community at large has clearly adopted software testing, and so probably have you, since you are reading this book.

The next step lies in understanding whether our tests are good, are verifying all the important details of our projects, and whether we are writing code that is to the point. We want to avoid useless complexity, embracing brevity, and improve expressiveness of our work, to the benefit of ourselves and our peers.

As a code-quality evangelist myself, I suggest you to try the tools and techniques presented in the next chapters, make them your own.

You will learn about practices that I personally made part of my own daily engineering work, and they will have a deep impact on how you write software.

By mixing and leveraging them, you may be able to find your level of comfort in code quality, as well as the knowledge needed to convince others about their value.

# Chapter 1: Getting Started

## Audience

The topic of testing is tough to explain to people who are just learning to program. “I'm going to write code that tests other code I write? That seems really hard!” I have yet to see a tutorial that teaches programmers how to use a programming language from a test-centric position.

With that in mind, I wrote this book for PHP programmers who already have experience writing tests but want to improve. I have been doing this since 2005 and still go through the process of learning new things and reinforcing older habits that can lead to better outcomes.

My book “The Grumpy Programmer’s Guide To Testing PHP Applications” (available via LeanPub[1] or php|architect[2]) goes over the basic technical and core skills you need to learn, and hopefully master, to make your tests effective and turn writing tests into just something you do instead of a rare event.

- [1] https://leanpub.com/grumpy-guide
- [2] https://phpa.me/grumpy-testing-book

Throughout this book, I am going to show you how I am adding targeted test coverage to my oldest, still-in-use PHP-based web application. It has been running since 2004, with me updating the base framework (CakePHP[3]) every few years.

## Why Make All This Effort?

The application began as a PHP 5 codebase and has been updated over the years. It now runs fine on PHP 7.4 and hopefully PHP 8.0 soon. It’s extremely rare in the current phase of the software industry to work on an application for so long. The skillset needed to build something from scratch, and the skillset needed to maintain an existing codebase are quite different! I believe that more and more developers understanding this has led to all these great tools available in multiple languages, making testing and code analysis easier.

After all, if you’re going to build something and never touch it again after deployment, then you probably have no need for automated tests and code linting and static code analysis. However, if you are building something that is going to be the long-lived core of a business or project, it is worth exploring automated testing, code linting, and static code analysis to find out how they can help you.

## The Application

The application itself is a website for a league that uses a tabletop baseball simulation game to play out a full season using rosters made up of players from existing Major League Baseball teams. We make the game ourselves and distribute it to league members and other interested parties for free.

When it comes to verifying the application is behaving as expected, some of the things that can be visually confirmed are:

- league standings
- scheduled games
- pitching rotations teams will use
- injuries

To be perfectly clear–knowledge of the sport of baseball is not a requirement to understand the approach I am using in this book! It certainly helps, but the key point I want to emphasize is that without some domain knowledge of the problem you are trying to solve you might create tests that have no impact.

- [3] https://cakephp.org
