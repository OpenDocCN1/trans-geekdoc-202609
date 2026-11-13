
an abbreviation because the quoted expression looks more complicated than its translation. The key is that ' is a short-hand for quote. Here are some short examples, then:

```
> '(1 2 3)
(list 1 2 3)
> '("a" "b" "c")
(list "a" "b" "c")
> '(#true "hello world" 42)
(list #true "hello world" 42)
```

As you can see, the use of ' creates the promised lists. In case you forgot what (list 1 2 3) means, reread chapter 11.1; it explains that this list is short for (cons 1 (cons 2 (cons 3 '()))) .

So far quote looks like a small improvement over list, but look:

```
> '(("a" 1)
("b" 2)
("d" 4))
(list (list "a" 1) (list "b" 2) (list "d" 4))
```

With ' we can construct lists as well as nested lists.

To understand how quote works, imagine it as a function that traverses the shape it is given. When ' encounters a plain piece of data—a number, a string, a Boolean, or an image—it disappears. When it sits in front of an open parenthesis, (, it inserts list to the right of the parenthesis and puts ' on all the items between ( and the closing ). For example,

'(1 2 3) is short for (list '1 '2 '3)

As you already know, ' disappears from numbers so the rest is easy. Here is an example that creates nested lists:

'(("a" 1) 3) is short for (list '("a" 1) '3)

To continue this example, we expand the abbreviation in the first position:

```
(list '("a" 1) '3) is short for (list (list "a" 1) 3)
```

We leave it to you to wrap up this example.

## Exercise 231. Eliminate quote in favor of list from these expressions:

- '(1 "a" 2 #false 3 "c")
- '()
- and this table-like shape:
  ```
  '(("alan" 1000)
   ("barb" 2000)
   ("carl" 1500))
  ```

Now eliminate list in favor of cons where needed.

## Quasiquote and Unquote

The preceding section should convince you of the advantages of ' and quote. You may even wonder why the book introduces quote only now and didn’t do so right from the start. It seems to greatly facilitate the formulation of test cases that involve lists as well as for keeping track of large collections of data. But all good things come with surprises, and that includes quote.

When it comes to program design, it is misleading for beginners to think of lists as quoted or even list-constructed values. The construction of lists with cons is far more illuminating for the step-wise creation of programs than short-hands such as quote, which hide the underlying construction. So don’t forget to think of cons whenever you are stuck during the design of a list-processing function.

Let’s move on, then, to the actual surprises hidden behind quote. Suppose your definitions area contains one constant definition:

```
(define x 42)
```

Imagine running this program and experimenting with

```
'(40 41 x 43 44)
```

in the interactions area. What result do you expect? Stop! Try to apply the above rules of ' for a moment.

Here is the experiment

```
> '(40 41 x 43 44)
(list 40 41 'x 43 44)
```

At this point it is important to remember that DrRacket displays values. Everything on the list is a value, including 'x. It is a value you have never seen before, namely, a Symbol. For our purposes, a symbol looks like a variable name except that it starts with ' and that **a symbol is a value**. Variables only stand for values; they are not values in and of themselves. Symbols play a role similar to those of strings; they are a great way to represent symbolic information as data. Part IV illustrates how; for now, we just accept symbols as yet another form of data.

To drive home the idea of symbols, consider a second example:

```
'(1 (+ 1 1) 3)
```

You might expect that this expression constructs (list 1 2 3). If you use the rules for expanding ', however, you discover that

```
'(1 (+ 1 1) 3) is short for (list '1 '(+ 1 1) '3)
```

And the ' on the second item in this list does not disappear. Instead, it abbreviates the construction of another list so that the entire example comes out as

```
(list 1 (list '+ 1 1) 3)
```

What this means is that '+ is a symbol just like 'x. Just as the latter is unrelated to the variable x, the former has no immediate relationship to the function + that comes with BSL+. Then again, you should be able to imagine that '+ could serve as an elegant data representation of the function + just as '(+ 1 1) could serve as a data representation of (+ 1 1). Part IV picks up this idea.

In some cases, you do not want to create a nested list. You actually want a true expression in a quoted list and you want to evaluate the expression during the construction of the list. For such cases, you want to use quasiquote, which, like quote, is just a keyword for a compound sentence: `(quasiquote (1 2 3))`. And, like quote, quasiquote comes with a short-hand, namely the ` character, which is the “other” single-quote key on your keyboard.

At first glance, ` acts just like ' in that it constructs lists:

```
> `(1 2 3)
(list 1 2 3)
> `("a" "b" "c")
(list "a" "b" "c")
> `(#true "hello world" 42)
(list #true "hello world" 42)
```

The best part about ` is that you can also use it to unquote, that is, you can demand an escape back to the programming language proper inside of a quasiquoted list. Let’s illustrate the idea with the above examples:

```
> `(40 41 ,x 43 44)
(list 40 41 42 43 44)
> `(1 ,(+ 1 1) 3)
(list 1 2 3)
```

As above, the first interaction assumes a definitions area that contains `(define x 42)`. The best way to understand this syntax is to see it with actual keywords instead of ` and , short-hands:

```
(quasiquote (40 41 (unquote x) 43 44))
(quasiquote (1 (unquote (+ 1 1)) 3))
```

The rules for expanding a quasiquoted and an unquoted shape are those of quote supplemented with one rule. When ` appears in front of a parenthesis, it is distributed over all parts between it and the matching closing parenthesis. When it appears next to a basic piece of data, it disappears. When it is in front of some variable name, you get a symbol. And the new rule is that when ` is immediately followed by unquote, both characters disappear:

```
`(1 ,(+ 1 1) 3) is short for (list `1 `(+ 1 1) `3)
```
and
```
(list `1 `(+ 1 1) `3) is short for (list 1 (+ 1 1) 3)
```

And this is how you get (list 1 2 3) as seen above.

From here it is a short step to the production of web pages. Yes, you read correctly—web pages! In principle, web pages are coded in the HTML and CSS programming languages. But nobody writes down HTML programs directly; instead people design programs that produce web pages. Not surprisingly, you can write such functions in BSL+, too, and there is a simplistic example in figure 83. As you can immediately see, this function consumes two strings and produces a deeply nested list—a data representation of a web page.

```
; String String -> ... deeply nested list ...
; produces a web page with given author and title
(define (my-first-web-page author title)
  (html
   (head
    (title ,title)
    (meta ((http-equiv "content-type")
           (content "text-html"))))
   (body
    (h1 ,title)
    (p "I, " ,author " made this page."))))
```

### Figure 83: A simplistic HTML generator

A second look also shows that the title parameter shows up twice in the function body: once nested in a nested list labeled with 'head and once nested in the nested list labeled with 'body. The other parameter shows up only once. We consider the nested list a page template, and the parameters are holes in the template, to be filled by useful values. As you can imagine, this template-driven style of creating web pages is most useful when you wish to create many similar pages for a site.

To understand how the function works, we experiment in DrRacket's interactions area. Given your knowledge of quasiquote and unquote, you should be able to predict what the result of

```
(my-first-web-page "Matthias" "Hello World")
```

is. Then again, DrRacket is so fast that it is better to show you the result: see the left column in figure 84. The right column of the table contains the equivalent code in HTML. If you were to open this web page in a browser you would see something like this:

| Nested List Representation | Web Page Code (HTML) |
|---|---|
| '(html
 (head
  (title "Hello World")
  (meta
   ((http-equiv "content-type")
    (content "text-html")))
 (body
  (h1 "Hello World")
  (p "I, "
     "Matthias"
     ", made this page."))) | <html>
<head>
<title>
Hello World
</title>
<meta
http-equiv="content-type"
content="text-html" />
</head>
<body>
<h1>
Hello World
</h1>
<p>
I,
Matthias,
made this page.
</p>
</body>
</html> |

### Figure 84: A data representation based on nested lists

Note that "Hello world" shows up twice again: once in the title bar of the web browser—which is due to the <title> specification—and once in the text of the web page.

![](img/19fbe4068996ced0ce42cec7fb82a834_487_0.png)

You can use show-in-browser from the web-io.rkt library to display the result in a web browser.

If this were 1993, you could now sell the above function as a Dot Com company that generates people's first web page with a simple function call. Alas,
