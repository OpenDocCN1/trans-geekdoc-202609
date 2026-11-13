# Java

```
public static void main(String[] args) {
    Transaction[] t = new Transaction(250, "Special deal");
    Customer[] customers = new Customer[10];
    customers[0] = new Customer(0, "Ava");
    customers[1] = new Customer(1, "Brian");
    customers[2] = new Customer(2, "Cherry");
    customers[0].addItem(50, "Burger meal deal*");
    customers[0].addItem(new Transaction(100, "Birthday bonus"));
    customers[1].addItem(200, "Bluetooth earphones");
    customers[1].spendPoints(50, "Discount for shopping");
    customers[2].spendPoints(80, "Discount for shopping");
    customers[2].addItem(t);
    System.out.println(customers[0].getBalance());
    System.out.println(customers[1].getBalance());
    System.out.println(customers[2].getBalance());
    System.out.println(customers[3].getBalance());
}
```

# 2 Animal shelter

An animal rescue shelter requires a computer system to manage the animals under its care and the adoption process.
When an animal is brought to the shelter, it is given an ID, and its species, age, health status and other relevant details are
recorded in the system. When an animal is adopted, its record is updated to reflect the change in status.
Animals are identified by a unique ID, which is a combination of letters and numbers (e.g. C4T00123). This is used to track
their information in the system.
A programmer created the classes AnimalShelter and Animal to model the situation above.

# Python

```
class AnimalShelter:
    def __init__(self, location, capacity):
        self.location = location
        self.animals = [ None for _ in range(capacity) ]
    def get_location(self):
        return self.location
    def get_capacity(self):
        return len(animals)
    def find_animal(self, id:str):
        # Method to find an animal by an ID in the list and return the index
class Animal:
    def __init__(self, id, species):
        # Missing code to initialize _id, _species, _age, _is_healthy
    def set_age(self, age):
        self._age = age
    def set_health_status(self, is_healthy):
        self._is_healthy = is_healthy
```