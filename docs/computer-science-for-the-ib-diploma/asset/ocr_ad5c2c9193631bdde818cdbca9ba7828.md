```
public void takeExam() {
    System.out.println("Student A prefers taking exams in a quiet
classroom.");
})
class StudentB implements School {
    public void attendClass() {
        System.out.println("Student B attends class in person at the school.");
    }
    public void doHomework() {
        System.out.println("Student B does homework late at night with music
playing.");
    }
    public void takeExam() {
        System.out.println("Student B takes exams online with open book
resources.");
    }
}
public class Main {
    public static void main(String[] args) {
        StudentA studentA = new StudentA();
        StudentB studentB = new StudentB();
        studentA.attendClass();
        studentA.doHomework();
        studentA.takeExam();
        studentB.attendClass();
        studentB.doHomework();
        studentB.takeExam();
    }
}
```

# Application of design patterns

# Singleton example

The following code is an example of a singleton pattern that can be used to provide access to application settings that have been stored into a settings.json file. The example content of such a file follows:

```
{
   "databaseUrl": "postgresql://user:password@host:port/database",
   "timeout": 10
}
```

Note: Java users, if you plan to implement this, you will need to add the org.json library. Your IDE should allow you to easily add dependencies to other libraries.