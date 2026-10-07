required to solve the business problem of pulling data out of Xenia and storing that data into Pillar.

# Listing 5.13

```
func Pull(x *Xenia, data []Data) (int, error) {
	for i := range data {
	if err := x.Pull(&data[i]); err != nil {
		return i, err
	}
	}
	return len(data), nil
}

func Store(p *Pillar, data []Data) (int, error) {
	for i := range data {
	if err := p.Store(&data[i]); err != nil {
		return i, err
	}
	}
	return len(data), nil
}
```

The next layer of code is represented by these two functions, Pull and Store. They build on the primitive layer of code by accepting a collection of data values to pull or store in the respective systems. These functions focus on the concrete types of Xenia and Pillar since those are the systems the program needs to work with at this time.

# Listing 5.14

```
func Copy(sys *System, batch int) error {
	data := make([][]Data, batch)

for {
	i, err := Pull(&sys.Xenia, data)
	if i > 0 {
		if _, err := Store(&sys.Pillar, data[:i]); err != nil {
			return err
		}
	}

	if err != nil {
		return err
	}
}
```

The Copy function builds on top of the Pull and Store functions to move all the data that is pending for each run. If I notice the first parameter to Copy, it's a type called System.