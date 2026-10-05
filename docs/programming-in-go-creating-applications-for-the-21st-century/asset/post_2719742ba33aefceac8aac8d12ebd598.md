
## 6.2. Custom Types

The Count type's method set consists of the three methods, Increment(), Decre(), and IsZero(); whereas the Count type's method set is the single method, IsZero(). All these methods can be called on a Count—and on a Count value, providing that it is addressable, as we saw in the snippet earlier ◄ The Part type's method set consists of the four methods, LowerCase(), Upper(), String(), and HasPrefix(); while the Part type's method set consists of just the String and HasPrefix() methods. However, the LowerCase() and UpperCase() methods can also be used on addressable part values, as the earlier snippet illustrates (260 ◄).

Defining methods that accept value receivers works for types that are small, such as numbers. Such methods cannot modify the value they are called on since they get a copy of the value as their receiver. If we have values of large types or values we want to modify we need to use methods that accept pointer receivers. This makes method calls as cheap as possible (since the receiver is passed as a 32- or 64-bit pointer, no matter large the value is called on).

### 6.2.1.1. Overriding Methods

As we will see later in this chapter, it is possible to create struct types that include or more types (including interface types) as embedded fields (§6.4.1– 275). A particular convenience of this approach is that any methods on the embedded type can be called on the custom struct as if they were the struct's own methods, and they will be passed the embedded field as their receiver.

```go
type Item struct {
	id string // Named field (aggregation)
	price float64 // Named field (aggregation)
	quantity int // Named field (aggregation)
}

func (item *Item) Cost() float64 {
	return item.price * float64(item.quantity)
}
type SpecialItem struct {
	Item // Anonymous field (embedding)
	catalogID int // Named field (aggregation)
}
```

Here, the SpecialItem embeds an Item type. This means that we can call the Item's Cost() method on a SpecialItem.

```go
special := SpecialItem{"Green", 3, 5, 207}
fmt.Println(special.id, special.price, special.quantity, special.catalogID)
fmt.Println(special.Cost())
```

When we call special.Cost(), since the SpecialItem type does not have its own Cost() method, Go uses the Item.Cost() method—passes it the embedded Item value, **not the entire SpecialItem** that the method was originally called on.

As we will see later, if any of the embedded Item's fields have the same name as one of the SpecialItem's fields, we can still access the embedded Item's fields by using the type as part of the name—for example, `special.Item.price`. 

It is possible to override the methods of an embedded field simply by creating a new method for the embedding struct that has the same name as one of embedded fields. For example, suppose we have a new item type:

```go
type LuxuryItem struct {
    Item // Anonymous field (embedding)
    markup float64 // Named field (aggregation)
}
```

As it stands, if we call the Cost() method on a LuxuryItem, the embedded Item.Cost() method will be used, just like for SpecialItems. Here are three different implementations that override the embedded method (only one of may be used, or of course!).

```go
/*
func (item *LuxuryItem) Cost() float64 { // Needlessly verbose
    return item.Item.price * float64(item.Item.quantity) * item.markup
}

func (item *LuxuryItem) Cost() float64 { // Needless duplication!
    return item.Item.price * float64(item.quantity) * item.markup
}

func (item *LuxuryItem) Cost() float64 { // Ideal ✓
    return item.Item.Cost() * item.markup
}
```

The last implementation takes advantage of the embedded Cost() method. Of course, there is no requirement that overriding methods make any use of the embedded fields they override if we don't want them to. (Embedding fields in structs is covered later; $6.4.1., ➤275.)

### 6.2.1.2. Method Expressions

Just as we can assign and pass functions, we can also assign and pass method expressions. A method expression is a function that must be passed a value of the method's type as its first argument. (The term unbound method is often used in other languages for this concept.)

We have created four method expressions: asStringV() which takes a Part value as its sole argument, hasPrefix() which takes a Part as its first argument and a string as its second argument, and asStringP() and lower() which both take a Part as their sole argument.

Method expressions are an additional feature which can be very useful on the uncommon occasions when they are needed.

All the custom types we created so far potentially suffer from a critical flaw. None of them provide any means of ensuring that the data they are initialized with is valid (or forced to be valid), nor any means of ensuring the type's data (or fields in the case of struct types) cannot be given invalid data. For example, the Part.Id and Name can be set to any values. But if we wanted to apply constraints—for example, only allow IDs to be positive integers greater than zero, or only allow names that had a specific format?—will address these issues in the next subsection where we create a small custom type with validated fields.

### 6.2.2. Validated Types

For many simple types, no validation is necessary. For example, we might have type Point (X, Y), for which any values of X and Y are valid. Furthermore, since Go guarantees to initialize all variables (including struct fields) to their zero values, the need for explicit constructors is reduced. For those situations where the default zero-value initialization is insufficient, we can create a construction function. Go does not support constructors, so we must call construction functions explicitly. To support this the type as having an invalid value and provide one or more construction functions that can be used to create valid values, we can use a similar approach when it comes to fields that must be validated. We can make such fields unreported and provide exported accessor methods in the package. Let's look at a small but complete custom type that illustrates these points:

```go
type Place struct {
	latitude, longitude float64
	Name string
}
func New(latitude, longitude float64, name string) *Place {
	return &Place{saneAngle(0, latitude), saneAngle(0), name}
}
func (place *Place) Latitude() float64 { return place.latitude }
func (place *Place) SetLatitude(latitude float64) {
	place.latitude = saneAngle(place.latitude)
}
func (place *Place) Longitude() float64 { return place.longitude }
func (place *Place) SetLongitude(longitude float64) {
	place.longitude = saneAngle(place.longitude)
}
func (place *Place) String() string {
	return fmt.Sprintf("%.3f, %.3f %q", place.latitude, place.Name)
}
func (original *Place) Copy() *Place {
	return &Place{original.latitude, original.longitude, original.Name}
}
```

The Place type is exported (from the package), but its latitude and longitude fields are unreported because they require validation. We have provided a construction function, New(), to ensure that we always create valid *Place. It is a Go convention to call construction functions, or if there is more than one, for their names to begin with "New". (We haven't shown saneAngle() since it takes the old angle and the new angle and returns the new if it is in range; otherwise it returns the old). Recall that in Go, identifiers are unreported (i.e., only visible within the package in which they are) if they start with a lowercase letter, and identifiers are exported (i.e., visible in any package imports) if they start with an uppercase letter.

By providing getters and setters for the exported fields, we have ensured that only valid values can be. The String() method means that *Place values fulfill the fmt.Stringer interface, so *Places will print the value we want rather than using Go's default formatting. We have also provided a Copy() method—and not used any validation for it we know that the original is already valid.

```go
newYork := place.New(40.71667, -74, "New York") // newYork is a *Place
fmt.Println(newYork)
baltimore := newYork.Copy() // baltimore is a *Place
baltimore.SetLatitude(newYork.Latitude() - 1.43333)
baltimore.SetLongitude(newYork.Longitude() - 2.61667)
baltimore.Name = "Baltimore"
fmt.Println(baltimore)
```

```
(40.717, -74.000) "New York"
(39.283, -76.617) "Baltimore"
```

We put the Place in the package and call place.New() to create *Places. Once we have a *Place we can call its methods in the same way as we do for the standard library's custom types.

## 6.3. Interfaces

In go an interface is a custom type that specifies a set of one or more method signatures. Interfaces are however abstract, so it is not possible to instantiate an interface. However, it is possible to create a variable type that is of an interface—and which can be assigned a value of any concrete type that has the methods it requires.

The interface{} is the type that specifies the empty set of methods. Every value satisfies the interface{} whether the value has methods or not—after all, if a value does methods, its set of methods includes the empty set of methods as the methods it actually has. This is why the interface{} can be used for any value. We cannot call methods directly on a value passed as an interface(even if it has some), the interface is fulfilling no methods. So, in general, it is better to pass values either as their actual type or an interface that has the methods we want to use. Of course, if we use the interface{} type for values with methods, we can access methods by using a type assertion (§5.2.1, 191 ►) or a type switch (§5.2.2.2, 197 ➤), or even by using introspection (§9.4.9, ➤ 427).

Here is a very simple interface.
