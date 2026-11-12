I did, however, decide to do multiple regular expressions. The entire code, in Perl, is shown in Listing 7-3; save this as HTMLtoTXT.pl.

# Listing 7-3: Code That Extracts the Text from HTML

```
undef $/;
$_ = <>;
($_) = /<body.*?>(.*)<\/body>/s;
s/<p.*?>\n\n/sg;
s/<br.*?>\n/n/sg;
s/<.*?>//sg;
print $_;
```

The first two lines read in the file as a single string and place it in the default variable, $_. The next line yanks out the text between the body tags.

Any HTML tag can have parameters inside it. Even though some don’t offer parameters (such as <hr>), technically you’re still allowed to put parameters in them (as in <hr a="b">) even though the browser will ignore those parameters. Therefore, you can see in my code that for each pattern for an HTML tag I put a .*? after the tag name. The ? will prevent greediness, stopping at the first >.

![](bbox=[0.04, 0.38, 0.12, 0.46])

After extracting the text outside of the body, you replace each <p> tag with two newlines and each <br> tag with a single newline. Then simply remove the remaining tags. You do each replacement with a separate regular expression.

Finally, you print the resulting string. Here’s a sample input file you can use; save this as words.html:

```
<html><head><title>Opportunity</title></head>
<body>
<h1>An Opportunity for You</h1><p>
Like most people, I was born at a <i>very</i> young age. I then went to school, where I learned all the skills to make <b>millions</b> of dollars. Soon after school, I started my own multinational corporation, and to my delight I didn’t just make <i>millions</i>, but I made <i>billions</i>! And now, if you send me only $100, I can share with you this secret of how you can make a lot of money. (And please don’t think that the secret is getting unsuspecting people to send you $100 as I’m doing to you. Really! That’s not the scam. I mean <i>plan</i>. <b>Trust me!</b></p>
```