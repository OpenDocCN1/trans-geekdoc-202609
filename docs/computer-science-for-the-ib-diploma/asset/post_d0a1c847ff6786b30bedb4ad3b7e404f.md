
## 5 Social-media platform (HL)

Use the following UML as the basis for creating an OOP application for a social-media platform.

```
User                                     Post                                     Comment
- username : String                    - comments : Comment[]                    - comment : String
- displayName : String                 - likeCount : int                         - author : User
- profilePic : String                                            + Comment(String, User)
- posts : Post[]                       + Post()                                + getters and setters
+ User(String, String, String)         + getters and setters
+ newTextMessage( ... )                + newComment(String, User)
+ newPictureMessage( ... )             + newLike() : void
+ newVideoMessage( ... )
+ newPostCount() : int
+ getPost( int ) : Post
+ newComment( int, String, User )
+ newLike( int )

       Extends                    Extends                    Extends

TextMessage                     PictureMessage                 VideoMessage
- message : String              - pictureURL : String           - youtubeLink : String
+ TextMessage(String)           + PictureMessage(String)        + VideoMessage(String)
+ getters and setters           + getters and setters           + getters and setters
```

### UML social-media platform

For a Java implementation, you may assume the maximum number of posts per user is ten, and the maximum number of comments per post is ten.

Your final program should be able to:

- [ ] create a new user
- [ ] allow a user to create a post, via their user object's `.newTextMessage()`, `.newPictureMessage()` or `.newVideoMessage()` function
- [ ] allow a comment to be added to any post via the user object's `.newComment()` function, where the integer value represents the index of the relevant item in the posts array, and the `String`, `User` parameters are then passed to the `posts[i].newComment(String, User)` function.

The user object's `.newLike()` works similarly, using the integer as the index of the post, to then call the `.newLike()` on the relevant item in the posts array.

The following code is test code for your main function:

```python
import random

if __name__ == "__main__":
    frodo = User("frodo", "Frodo Baggins", "frodo.png")
    gandalf = User("gandalf", "Gandalf the Grey", "gandalf.png")
    samwise = User("samwise", "Samwise Gamgee", "samwise.png")
    aragorn = User("aragorn", "Aragorn", "aragorn.png")

    # Create posts
    frodo.new_text_message("Just finished my quest to destroy the One Ring. What an adventure! #MissionAccomplished #RingBearer")
    frodo.new_picture_message("Pic of me after the quest! #MountDoom #Mordor")
    aragorn.new_text_message("Reunited with my love, Arwen. Forever grateful for her love and support. ❤️ #Elessar #LoveAndDestiny")
    gandalf.new_video_message("Just having some fun with my staff and showing off a little wizardry on the dance floor! 💃🕺 #GandalfTheDancer #WizardGrooves")
    # Create comments
    frodo.new_comment(0, "Mr. Frodo! I'm so proud of you! You're the bravest hobbit I know. #TrueFriendship #HobbitHeroes", samwise)
    frodo.new_comment(0, "Frodo, you have my gratitude and respect. Your sacrifice has saved Middle-earth. #KingOfGondor #HeroicDeeds", aragorn)
    frodo.new_comment(0, "Well done, Frodo! You've shown incredible strength and determination. The world is safer because of you. #RingDestroyer #WizardPride", gandalf)
    frodo.new_comment(1, "Who's that great looking bloke next to you?", samwise)
    frodo.new_comment(1, "Amazing!", aragorn)
    aragorn.new_comment(0, "Aragorn, may your love with Arwen be as enduring as the light of the Silmarils. #LoveAndHope #FellowshipForever", frodo)
    aragorn.new_comment(0, "Aragorn, you have found true love. Cherish it always. #Shieldmaiden #HappilyEverAfter", gandalf)
    gandalf.new_comment(0, "Love it! #WizardsCanDance", frodo)
    gandalf.new_comment(0, "rofl", samwise)
    # Create likes
    frodo.new_like(1)
    frodo.new_like(1)
    aragorn.new_like(0)
    r = random.randint(1001, 2000)
    for i in range(r):
        gandalf.new_like(0)
)
```

# Java

```java
import java.util.Random;
class Main {
    public static void main(String[] args) {
        User frodo = new User("frodo", "Frodo Baggins", "frodo.png");
        User gandalf = new User("gandalf", "Gandalf the Grey", "gandalf.png");
        User samwise = new User("samwise", "Samwise Gamgee", "samwise.png");
        User aragorn = new User("aragorn", "Aragorn", "aragorn.png");
        // Create posts
        frodo.newTextMessage("Just finished my quest to destroy the One Ring. What an adventure! #MissionAccomplished #RingBearer");
        frodo.newPictureMessage("Pic of me after the quest! #MountDoom #Mordor");
        aragorn.newTextMessage("Reunited with my love, Arwen. Forever grateful for her love and support. ❤️#Elessar #LoveAndDestiny");
        gandalf.newVideoMessage("Just having some fun with my staff and showing off a little wizardry on the dance floor! 💃🕺 #GandalfTheDancer #WizardGrooves");
        // Create comments
        frodo.newComment(0, "Mr. Frodo! I'm so proud of you! You're the bravest hobbit I know. #TrueFriendship #HobbitHeroes", samwise);
        frodo.newComment(0, "Frodo, you have my gratitude and respect. Your sacrifice has saved Middle-earth. #KingOfGondor #HeroicDeeds", aragorn);
        frodo.newComment(0, "Well done, Frodo! You've shown incredible strength and determination. The world is safer because of you. #RingDestroyer #WizardPride", gandalf);
        frodo.newComment(1, "Who's that great looking bloke next to you?", samwise);
        frodo.newComment(1, "Amazing!", aragorn);
        aragorn.newComment(0, "Aragorn, may your love with Arwen be as enduring as the light of the Silmarils. #LoveAndHope #FellowshipForever", frodo);
        aragorn.newComment(0, "Aragorn, you have found true love. Cherish it always. #Shieldmaiden #HappilyEverAfter", gandalf);
        gandalf.newComment(0, "Love it! #WizardsCanDance", frodo);
        gandalf.newComment(0, "rofl", samwise);
        // Create likes
        frodo.newLike(1);
        frodo.newLike(1);
        aragorn.newLike(0);
        Random random = new Random();
        int randomNumber = random.nextInt(1001) + 1000;
        for (int i = 0; i < randomNumber; i++) {
            gandalf.newLike(0);
        }
    }
}
```

## EXAM PRACTICE QUESTIONS

### 1 Customer loyalty system

A chain of stores has launched a new customer loyalty program, where each dollar customers spend accrues loyalty points that can be exchanged for discounts on future purchases. An object-oriented program has been created to manage the loyalty program.

- Customer: Represents customer information, including a list of all their purchase history items
- Transaction: Represents the purchase of a single item by a customer.

The UML diagram for the Customer class is provided below:

| Customer |
| :--- | :--- |
| - int | id |
| - String | name |
| - long | balance |
| - Transaction[] | history |
| - long | historyItemCount |
| + | Customer(int id, String name) |
| + void | addTransaction(Transaction item) |
| + void | spendPoints(String description, int points) |
| + Boolean | getTransactionById(int id) |
| + Transaction | getTransactionByDesc(String description) |
| + long | getBalance() |
| + String | getName() |

### UML Customer class

- a State the relationship between Customer and Transaction.
- b Construct a simplified UML diagram showing the relationships between Customer and Transaction.
- c Outline the significance of the minus sign in front of long balance in the UML diagram.
- d Construct the code for the constructor of Customer.

A Transaction object has two properties: a string containing a description of the item purchased and a long integer containing the cost / value of the item in dollars (you can assume cents are not used). The following code forms the basis of the Transaction class:

```python
class Transaction:
    def __init__(self, description, points):
        self.description = description
        self.points = points
    # Getters and setters for description and points
```

```java
public class Transaction {
    private String description;
    private int points;
    public Transaction(String description, int points) {
        this.description = description;
        this.points = points;
    }
    // Getters and setters for description and points
}
```

Additionally, the following code describes the functionality of the addItem(Transaction item) function in the Customer class:
