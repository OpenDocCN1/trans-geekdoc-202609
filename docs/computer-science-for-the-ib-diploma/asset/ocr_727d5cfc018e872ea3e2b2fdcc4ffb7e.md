```
**Java**

```java
class Main {
    public static void main(String[] args) {
        Flight cx619 = new Flight("CX 619", 280); // Cathay - HKG-SIN
        Flight aa6914 = new Flight("AA 6914", 266);
        // American - JFK-LHR
        Flight ek89 = new Flight("EK 89", 354); // Emirates - DBX-GVA
        Ticket jordan = Ticket("Jordan Deckard");
        cx619.addTicket(new Ticket("Taylor Ripley"));
        cx619.addTicket(jordan);
        cx619.addTicket(new Ticket("Casey Neo"));
        aa6914.addTicket(new Ticket("Cameron Quaid"));
        aa6914.addTicket(new Ticket("Phoenix Andor"));
        cx619.printPassengerList();
        System.out.println(cx619.getSeatsAvailable());
        cx619.removeTicket(jordan);
        cx619.printPassengerList();
        System.out.println(cx619.getSeatsAvailable());
    }
}
```
```

Anticipated output:

```
Flight CX 619 has passengers:
Taylor Ripley
Jordan Deckard
Casey Neo
277
Flight CX 619 has passengers:
Taylor Ripley
Casey Neo
278
```

# 3 School enrolments and grade book

Implement the students and grades example as provided in the end of Section B3.1, and debug any transcription errors to ensure it behaves as expected before continuing.

Extend the scenario to include a new class called "Course" that contains an array of students who are enrolled in it.

+   [ ] Course should contain an addStudent() and removeStudent() method.

+   [ ] Course should have the following additional functions:

+   * printClassList() generates a list of all student names (in name sort order)

+   * getClassAverage() returns the average of all student scores.