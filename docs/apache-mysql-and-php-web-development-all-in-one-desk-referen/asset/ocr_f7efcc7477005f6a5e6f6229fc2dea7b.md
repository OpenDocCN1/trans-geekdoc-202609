# Listing 6-1 (continued)

```
sub getInkAmount {
  my $self = shift;
  return $self->{ 'InkAmount' };
}

sub Write {
  my $self = shift;
  my $words = shift;
  print $words;
  $self->{ 'InkAmount' } -= length($words);
}

sub ReplaceInkCartridge {
  my $self = shift;
  $self->{ 'InkAmount' } = 100;
}

return 1;
```

Listing 6-1 is the code for the class. To try out the class, type in Listing 6-2, which uses the class. Save Listing 6-2 as filename testpen.pl (this time you use the filename extension .pl, as usual) and put the file in the same directory as the Pen.pm file.

# Listing 6-2: A File That Demonstrates Using the Pen.pm Class

```
use Pen;

$redpen = Pen->new();
print $redpen->getInkAmount();
print "\n";
$redpen->Write("Hello\n");
print $redpen->getInkAmount();
print "\n";
```

To try this out, type the following:

```
perl testpen.pl
```

Here's the output:

```
100
Hello
94
```