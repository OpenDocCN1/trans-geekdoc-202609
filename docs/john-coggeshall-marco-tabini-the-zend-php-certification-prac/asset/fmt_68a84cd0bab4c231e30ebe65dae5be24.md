
# Introduction

WRITING AN EXAM IS never an easy task. Socrates is quoted as saying that “an unexamined life is not worth living,” but (although he wasn’t really referring to taking technical tests) we’re sure that most people sitting in an examination room would gladly exchange places with the legendary philosopher and drink his hemlock rather than take a test.

Luckily, writing an exam doesn’t *have* to be such a traumatic experience. Given enough preparation and experience, you should be able to successfully pass it without much in the way of problems. The Zend exam itself is designed with two goals in mind: first, to test your knowledge of PHP and, second, to do so with as much of a practical approach as possible.

The idea of testing only your knowledge of PHP is based on a simple assumption: that your experience as a PHP programmer is not measured by your knowledge of external technologies. As we will reiterate in Chapter 9, you may go all your life developing PHP without ever having to interface to a MySQL database and, therefore, testing your knowledge of MySQL would be an unfair way to gauge your familiarity with PHP. Besides, MySQL AB (as well as most other relevant vendors of third-party software) already has its own certification program.

As far as the practicality of the questions goes, none of the Subject Matter Experts (SMEs) believed that a good programmer should be a walking PHP reference book. The truth is that PHP provides in excess of 1,500 different functions—and knowing each one of them, together with all its nuances, would be not only practically impossible, but useless as well. The PHP Manual is promptly available online from anywhere in the world; therefore, unless someone is going to lock you in a room with no Internet access, the chances that you won’t be able to access it are quite minimal. Still, you can’t program if you have to consult the manual every thirty seconds and, therefore, the exam does feature questions that test your knowledge of some basic PHP functionality in a very didactic way.

For the most part, however, the exam tests your ability to understand, interpret and write proper PHP code. Prepare to be asked to analyze plenty of code examples to find out what they do, how they work and whether they have any bugs. Some of the questions may seem a little tricky and unduly complex, but, if you think about it, having to deal with less-than-perfect code (written by someone else, of course!) is not that uncommon for anyone who has ever worked in the real world.

## Why a Book of Practice Questions?

It’s always best to go into an exam as prepared as possible. Your experience, as well books like the Zend PHP Certification Study Guide, published by SAMS, will be an invaluable tool in ensuring that you will pass, but sitting down and taking the exam itself is unlike anything you’re likely to do as part of your daily routine.

This book provides with you a highly structured series of questions designed to mimic (without reproducing) the actual questions that you will find in the exam. It will help you “get in the spirit” of the exam and learn how the questions are phrased and what they expect you to be able to do.

We worked hard at building questions that, while close to the real ones, are usually slightly more difficult to answer correctly. The reasoning behind this is simple: if you can get the hard ones right, the real exam will be a breeze!

## How is this Book Organized?

The Zend PHP Certification Practice Test Book is designed to work as a companion to the Official Zend PHP Certification Study Guide (ISBN 0672327090) published by SAMS Publishing. As a result, its chapters closely reflect those of the guide in order to facilitate your learning process as much as possible. You can read a chapter of the guide, then turn to the corresponding chapter in the Practice Questions Book and take a mini-exam centered exclusively on that particular topic. As an alternative, you can use this book as a testing resource together with the PHP Manual. Our table of contents will give you the basic layout of the topics covered by the exam, which you can use to study directly from the manual, as well as many of the other resources available on the Internet. Once you think you’re ready to try your hand at some questions, you can use this book again for that purpose.

Each chapter contains fifteen questions, with the exclusion of Chapters 1, 2, 5 and 6, which contain twenty. The reason for this is that these chapters discuss the most fundamental aspects of PHP; therefore, we thought that a few additional questions per chapter might have helped you better gauge your preparedness. You’ll find the answers to all the questions, together with an explanation, at the end of each chapter.

While you are, of course, free to use this book any way you like, we’d like to suggest a simple approach that can help you maximize its effectiveness. First of all, you should try your hand at practicing your test when you actually have time to do so—allow at least ninety minutes for answering the questions, and then another thirty to sixty minutes to check your answers.

Start by answering five questions from each fifteen-question chapter, and six from the twenty-question ones. Take care of each chapter in sequence, without stopping to check your answers. This will add up to around sixty-five questions, a very close approximation of the actual exam, which contains seventy. Give yourself around eighty minutes to complete the entire set—again, a good approximation of the ninety minutes allocated in the real exam.

At the end of this process, you can go back and check the answers you gave against the correct ones reported at the end of each chapter. This will give you an opportunity to determine how prepared you are in each different area and to focus your studies on those topics where your results were less than brilliant.

Once you feel ready, you can try again using the same technique. This will make it possible for you to answer a fresh batch of questions every time and test your knowledge anew.

## Finding Errata and Discussing Your Concerns

A *lot* of work went into writing, reviewing, editing and then reviewing some more the questions in this book, as well as their answers. Yet, we are but mere mortals and, as such, prone to making mistakes.

If you think you’ve found something wrong with the contents of the book, come and discuss it on the php|architect forums at this URL:

`http://forums.phparch.com/162`

Of course, the same is also true if one of the questions has you stumped and you want to chat with other PHP enthusiasts about the how’s and the why’s of the answers we provide. Both of us visit the forums regularly, and we are always happy to help out.

## Acknowledgements

Writing a book—no matter how small—is always a monumental task that involves the assistance and expertise of many different people.

We’d like to extend our thanks to Derick Rethans, who has spent considerable time performing a ruthless technical review of each question, pointing out errors and suggesting ways to improve the overall quality of the practice tests. It’s thanks to him that so many questions are understandable and technically accurate—and entirely our responsibility if some others are not.

Our thanks also go to Daniel Kushner over at Zend for his unwavering support and invaluable contribution to the Zend Certification Program—without him, there would be no questions to write about.

John Coggeshall

Marco Tabini

New York City

Toronto

# Chapter 1: PHP Programming Basics

THE ZEND EXAM IS designed so that you need a reasonable amount of experience in order to pass it. This doesn’t mean that you have to be Superman—it simply means that, in order to pass the exam, you’ve had to have a good amount of exposure to PHP in your daily life.
