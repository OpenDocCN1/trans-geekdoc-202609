# Listing 6.15

Output:

```
Start Goroutines
Waiting To Finish
A B C D E F G H I J K L M N O P Q R S T U V W X Y Z A C D E F G H I K L
M a b d e f g h i j k l m n o p Q R S T U V W X Y z A C D E F G H I
J L M N O P Q R S T U V W X Y Z p q r s t u v w x y z a b c d e f g h i j
k l m n o p q r s t u v w x y z a b c d e f g h i j k l m n o p q r s t u v
w x z
Terminating Program
```

What I see is that the concurrency of the program is now fine grained. The output to the letter is undefined and out of order.

# 6.4 Data Races

A data race is when two or more Goroutines are trying to access the same memory location at the same time where at least one Goroutine is performing a work. When this happens it is impossible to predict the result. These types of bugs are difficult to find because they cause issues that always appear random.

~8 minutes from Scott Meyers is great to listen to here:

CPU Caches and Why You Care 30:09-38:30
https://youtube.be/WDIqkP4JbkEt=1809

# 6.5 Data Race Example

This is a great example of a data race and how they can be hidden for years and eventually up at odd times and cause data corruption.

# Listing 6.16

```
var counter int

func main() {
  const grs = 2

  var wg sync.WaitGroup
  wg.Add(grs)

  for g := 0; g < grs; g++ {
    go func() {
      for i := 0; i < 2; i++ {
        value := counter
        value++
        counter = value
      }
      wg.Done()
    }()
  }

  wg.Wait()
  fmt.Println("Counter:", counter)
}
```