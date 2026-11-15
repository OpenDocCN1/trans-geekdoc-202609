# ## 13.2 Forms with PHP

Many people, especially Microsoft employees, ask themselves: How could PHP achieve its incredible market share? There are certainly many reasons for this, but one is mentioned particularly often: In the beginning, it was particularly easy to work with form data.

The authors of this book have written several more general titles on web publishing and have also introduced Perl in earlier editions. The following excerpt from one of these books, from 2004, is a Perl script that accesses and outputs data in the form:

```
#!/usr/bin/perl
print "Content-type: text/html\n\n";
if ($ENV{"REQUEST_METHOD"} eq "POST") {
read(STDIN, $data, $ENV{"CONTENT_LENGTH"});
} else {
$data = $ENV{"QUERY_STRING"};
}
@pairs = split(/"&", $data);
foreach $pairs (@pairs) {
$pairs =~ tr/+/ /;
$pairs =~ s/%(..)/pack("C", hex($1))/eg;
($name, $value) = split("=", $pairs);
$form{$name} = $value;
}
foreach $name (keys($form))
{
print "<b>$name: </b>$form{$name}<br />\n";
}
```

Compared to the original, the code has been shortened somewhat. The problem with this listing is that it is not exactly easy to understand without knowledge of Perl. PHP was seen as a Perl competitor, especially in the early days, and had a powerful advantage: It was much simpler. Nowadays, Perl has long since been left behind by PHP in the web sector.

Nevertheless, we would like to take up the cudgels for Perl at this point. We used to use it a lot, especially in the past. Perl is often derisively referred to as the Swiss chainsaw because it can do a lot. PHP is of course the better choice for web use as it was developed specifically for the web and therefore has a lot of functionality that has to be retrofitted to Perl. One example is the previous code, which outputs all form data. There is also the well-known CGI.pm module for Perl, which greatly simplifies this. In principle, everything is possible with Perl—but that is probably the subject for another book.