
type Address struct {
    city   string
    street string
    postal string
}

type Person struct {
    name    string
    address Address
}

person := Person{
    name: "chris",
    address: Address{
        city: "Stockholm",
    },
}
