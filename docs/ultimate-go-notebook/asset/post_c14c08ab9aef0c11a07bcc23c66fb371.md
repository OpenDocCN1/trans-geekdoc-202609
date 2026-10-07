
# Listing 5.4

```go
func (d *Dog) Speak() {
    fmt.Println("Woof!", d.Name,
    "My name is,", it is,", d.IsMammal,
    "I am a mammal with a pack factor of,", d.PackFactor)
}
```

In the implementation of the Speak method, I can change out how it works for Woof. This is specific to how a dog speaks.

# Listing 5.5

```go
type Cat struct {
    Animal
    ClimbFactor int
}
```

If I'm going to have a Dog that represents an Animal, then I have to have a Cat. Using embedding, a Cat is everything Animal is plus more.

# Listing 5.6

```go
func (c *Cat) Speak() {
    fmt.Println("Meow!", c.Name,
    "My name is,", it is,", c.IsMammal,
    "I am a mammal with a climb factor of,", c.ClimbFactor)
}
```

In the implementation of the Speak method, I can change out how it works for Meow. This is specific to how a cat speaks.

Everything seems fine and it looks like embedding is providing the same functionality as inheritance does in other languages. Then I try to go ahead and group dogs and cats by the fact they have a common DNA of being an Animal.

```go
// Listing 5.7
animals := []Animal{
  Dog(
    Animal{
      Name: "Fido",
      IsMammal: true,
      PackFactor: 5,
    },
  Cat(
    Animal{
      Name: "Milo",
      IsMammal: true,
    },
    ClimbFactor: 4,
  }),
}

for _, animal := range animals {
  animal.Speak()
}
```

When I try to do this, the compiler complains that a Dog and Cat are not an Animal and this is true. Embedding isn't the same as inheritance and this is the pattern I need to stay away from. A Dog is a Dog, a Cat a Cat, and an Animal an Animal. I can't pass Dog's and Cat's as if they are Animals because they are not.

This kind of mechanic is also not very flexible. It requires configuration by the developer and unless I have access to the code, I can't make configuration changes over time.

If this is not how we can construct a collection of Dog's and Cat's, how can we do this in Go? It's not about grouping through common DNA, it's about grouping through common behavior. Behavior is the key.

```go
// Listing 5.8
type Speaker interface {
  Speak()
}
```

If I use an interface, then I can define the common method set of behavior that I want to group different types of data against.

```go
// Listing 5.9
speakers := []Speaker{
  &Dog{
    Animal: Animal{
      Name: "Fido",
      IsMammal: true,
    },
    PackFactor: 5,
  },
  &Cat{
    Animal: Animal{
      Name: "Milo",
      IsMammal: true,
    },
    ClimbFactor: 4,
  },
}
for _, speaker := range speakers {
    speaker.Speak()
}
```

In the new code, I can group Dogs and Cats together based on their common set of behavior, which is the fact that Dogs and Cats can speak.

In fact, the Animal type is really type pollution because declaring a type just to share a set of common states should be avoided.

```go
// Listing 5.10
type Dog struct {
    Name string
    IsMammal bool
    PackFactor int
}

type Cat struct {
    Name string
    IsMammal bool
    ClimbFactor int
}
```

In this particular case, I would rather see the Animal type removed and the fields copied and pasted into the Dog and Cat types. Later I will have notes about patterns that eliminate these scenarios from happening.

Here are the code smells from the original code:

- The Animal type provides an abstraction layer of reusable state.
- The program never needs to create or solely use a value of Animal type.
- The implementation of the Speak method for the Animal type is generalized.
- The Speak method for the Animal type is never going to be called.

Guidelines around declaring types:

- Declare types that represent something new or unique.
- Don't create aliases just for readability.
- Validate that a value of any type is created or used on its own.
- Embed types because I need the state, but because we need the behavior.
- If I am not thinking about behavior, I'm locking myself into the design that I can't grow in the future without cascading changes.
- Question types that are aliases or abstractions for an existing type.
- Question types whose sole purpose is to share a common set of states.

## 5.2 Don't Design With Interfaces

Unfortunately, too many developers attempt to solve problems in the abstract first. They focus on interfaces right away and this leads to interface pollution. As a developer, I exist in one of modes: a programmer and then an engineer.

When I am programming, I am focused on getting a piece of code to work. Trying to solve the problem and break down walls. Prove that my initial ideas work. That is all I care about. This programming should be done in the concrete and is never production ready.

Once I have a prototype of the code that solves the problem, I need to switch to engineering mode. When I am engineering, I am focused on quality, maintainability, and scalability.

## 5.3 Composition

The best way to handle this in Go is through composition. Instead of using inheritance, we compose types to build functionality.

```go
// Listing 5.11
type Xenia struct {
  Host string
  Timeout time.Duration
}

func (x *Xenia) Pull(d *Data) error {
  switch rand.Intn(10) {
  case 9:
    return io.EOF
  case 5:
    return errors.New("Error reading from Xenia")
  default:
    d.Line = "Data"
    fmt.Println("In:", d.Line)
    return nil
  }
}
```

```go
// Listing 5.12
type Pillar struct {
  Host string
  Timeout time.Duration
}

func (p *Pillar) Store(d *Data) error {
  fmt.Println("Out:", d.Line)
  return nil
}
```

```go
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

```go
// Listing 5.13
type System struct {
    Xenia
    Pillar
}

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
}
```

By using composition, we can create a System that satisfies the interface by aggregating the behaviors of Xenia and Pillar. This approach is much more flexible and easier to test.

```go
type Speaker interface {
  Speak()
}

func (s *System) Speak() {
    fmt.Println("System is speaking")
}
```
