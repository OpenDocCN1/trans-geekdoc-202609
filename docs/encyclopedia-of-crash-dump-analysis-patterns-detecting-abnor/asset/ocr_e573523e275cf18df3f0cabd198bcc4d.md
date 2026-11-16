```
puts("Allocate: p3");
void *p3 = malloc(100);

puts("Free: p1");
free(p1);
puts("Free: p2");
free(p2);
puts("Double-Free: p2");
free(p2);
puts("Double-Free: p3");
free(p3);

Sleep(100);
}
return 0;
}
```

The output of the program:

```
Allocate: p1
Allocate: p2
Allocate: p3
Free: p1
Free: p2
Double-Free: p2
Free: p3
Allocate: p1
Allocate: p2
Allocate: p3
Free: p1
Free: p2
Double-Free: p2
Free: p3
Allocate: p1
Allocate: p2
Allocate: p3
Free: p1
Free: p2
Double-Free: p2
Free: p3
Allocate: p1
Allocate: p2
Allocate: p3
Free: p1
Free: p2
Double-Free: p2
Free: p3
Crash!
```