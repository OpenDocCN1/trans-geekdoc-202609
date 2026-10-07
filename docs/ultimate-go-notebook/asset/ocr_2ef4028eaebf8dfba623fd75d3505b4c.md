case, I am asking if there is a bike value stored inside of m at the moment the code is executed. If there is, the variable b is given a copy of the bike value stored. Then the copy can be copied inside of the ml interface variable.

If there isn't a bike value stored inside of the interface value, then the program panics. I wait if there absolutely should have been a bike value stored. What if there is a chance it isn't and that is valid? Then I need the second form of the type assertion.

# Listing 5.33

```
b, ok := m.(bike)
```

In this form, if ok is true, there is a bike value stored inside of the interface. If ok is false, then there isn't and the program does not panic. The variable b however is still of type bike, but it is set to its zero value state.

# Listing 5.34

```
func main() {
	rand.Seed(time.Now().UnixNano())

tmvs := []fmt.Stringer{
	Car(),
	Cloud(),
	}

for i := 0; i < 10; i++ {
	rn := rand.Intn(2)
	if v, ok := mvs[rn].(Cloud); ok {
		fmt.Println("Got Lucky:", v)
		continue
	}

mt.Println("Got Unlucky")
}
}
```

Assuming the program does declare two types named Car and Cloud that each implement the fmt.Stringer interface, I can construct a collection that allows me to store a value of both Car and Cloud. Then 10, I randomly choose a number from 0 to 1, and perform a type assertion to see if the value at that random index contains a Cloud value. Since it's possible it's not of type Cloud, the second form of the type assertion is critical here.

# 5.9 Interface Pollution

I spot interface pollution from a mile away. It mostly comes from the fact that people are designing software with interfaces instead of discovering them. I should design a concrete solution to the problem first. Then I can discover where the program needs to be polymorphic, if at all.