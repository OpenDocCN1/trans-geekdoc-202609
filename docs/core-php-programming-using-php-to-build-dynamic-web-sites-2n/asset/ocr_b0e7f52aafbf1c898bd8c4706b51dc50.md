# Core PHP Programming

This function wraps the C function of the same name, so it's a good idea to check out the man page. PHP accepts categories that have no effect on PHP itself. Also, PHP does not necessarily accept all the valid categories your operating system offers.

Location codes differ with operation systems. In general they take the form of language_country—that is, a language code followed by an optional underscore and a country code. If you are using Windows, Visual C's help file lists all the languages and countries.

```
<?
  // change locale in Windows NT
  print("Changing to Russian: ");
  print(set_locale(LC_ALL, "russian"));
  print("<BR>\n");
  print("Dos vedanya!");
?>
```

| Category | Description |
|---|---|n| LC ALL | All aspects of locale |
| LC COLLATE | Comparison of strings (not used by PHP) |
| LC CTYPE | Conversion and classification of characters |
| LC MONETARY | Monetary formatting (not used by PHP) |
| LC NUMERIC | Number separation |
| LC TIME | Time formatting |

# set_time_limit(integer seconds)

Use set_time_limit to override the default time script is allowed to run, which is usually set to 30 seconds inside php.ini. If this limit is reached, an error occurs and the script stops executing. Setting seconds argument to zero causes the time limit to be disabled.

Each time the set_time_limit function is called, the counter is reset to zero. This means that calling set_time_limit(30) gives you fresh 30 seconds of execution time.

The time-limit functionality does not operate in Windows. Scripts will execute until finished.

```
<?
  // allow this script to run forever
  set_time_limit(0);
?>
```