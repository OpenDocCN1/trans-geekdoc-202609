
# Mock Dependencies

## Introduction to Mocking

When it comes to unit testing, the concept of mocking is a game-changer. It involves simulating the behavior of real-world objects or systems, such as databases, external APIs, or third-party services, which might be impractical or cumbersome to incorporate directly into unit tests. The essence of mocking lies in its ability to create a controlled environment for tests, isolating the unit of work from external dependencies and interactions. This isolation is crucial as it ensures that tests focus solely on the functionality they are meant to evaluate, without being affected by the behavior or state of external systems.

## Why Mock Dependencies?

Suppose you're crafting tests for a function that fetches book details from a database. Integrating a real database into these tests would not only complicate the testing process but also transform it into more of an integration test rather than a unit test. This is because the outcome of the tests would then depend on the database's state and behavior. Mocking steps in as a powerful tool in such situations. By simulating the database, you can focus on testing the function's logic independently, ensuring that the tests are reliable, faster, and more focused.

## Creating Mock Database

A practical approach to mocking in Go involves the use of interfaces. For example, if your GitforGits application interacts with a database, you would typically define a `Database` interface that outlines the operations like fetching a book by its ID. In a testing scenario, instead of using a real database, you can implement a `MockDatabase` that adheres to this `Database` interface. However, unlike the real database, the `MockDatabase` doesn't perform actual database operations. Instead, it uses internally stored data to simulate these operations.

```go
type Database interface {
    FetchBookByID(id int) (Book, error)
}
type MockDatabase struct {
    books []Book
}
func (m *MockDatabase) FetchBookByID(id int) (Book, error) {
    for _, book := range m.books {
        if book.ID == id {
            return book, nil
        }
    }
    return Book{}, fmt.Errorf("Book not found")
}
```

In this setup, the `MockDatabase` operates on an internal slice of books, mimicking a real database's behavior. This method allows developers to test the functionality of the `FetchBookByID` function independently of a live database environment. By returning predefined data, the mock ensures that the test's behavior is predictable and consistent, which is crucial for accurate testing outcomes.

## Using Mock in Tests

When writing tests, instead of creating an instance of the real database, you'd instantiate the `MockDatabase`, preload it with data, and pass it to the functions or methods you're testing.

```go
func TestFetchBookDetails(t *testing.T) {
    mockDB := &MockDatabase{
        books: []Book{
            {ID: 1, Name: "Go Basics", Author: "A. Developer"},
        },
    }
    book, err := FetchBookDetails(mockDB, 1)
    if err != nil || book.Name != "Go Basics" {
        t.Fail()
    }
}
```

Similarly, for mocking external services or APIs, you can create interfaces that represent the operations you perform on those services. Then, for tests, create mock implementations that return predefined data.

Let us say you have a function that fetches book reviews from an external API:

```go
type ReviewAPI interface {
    FetchReviewsForBook(bookID int) ([]Review, error)
}
```

A mock might look like:

```go
type MockReviewAPI struct {
    reviews map[int][]Review
}
func (m *MockReviewAPI) FetchReviewsForBook(bookID int) ([]Review, error) {
    return m.reviews[bookID], nil
}
```

Mocking provides a controlled environment for your tests. You don't have to worry about external services being down or the internet being slow. Every test run is consistent, making failures easier to diagnose. However, it's crucial to remember that while mocks simulate external behaviors, they might not capture every nuance of the real thing. It's still essential to have integration tests, in addition to unit tests, to ensure all parts of your system work together correctly.

# Tracing and Logging

Every application, no matter how well coded, can run into unexpected scenarios or erroneous states. For a complex web app like the GitforGits Bookstore, having visibility into application behavior is essential. This is where tracing and logging come into play. While errors give immediate feedback about a problem, logs provide a narrative of the application's operation, helping developers understand events leading up to an issue.

## Performing Logging with Go's log

Go's standard library offers a simple logging package, `log`. This package provides basic logging functionalities that can be easily incorporated into any Go application.

```go
import "log"
func fetchBookDetails(bookID int) (Book, error) {
    // ... fetch operation ...
    if err != nil {
        log.Printf("Error fetching book with ID %d: %v", bookID, err)
        return Book{}, err
    }
    return book, nil
}
```

In the above, if the fetch operation encounters an error, a log entry is created detailing the book ID and the error message. For a web application, it's beneficial to include request-specific details in logs, such as request ID, user ID, or IP address. This contextual information aids in narrowing down issues and understanding user-specific anomalies. You can use context values to pass this data. For instance, middleware can be used to attach a unique request ID to every incoming request. This ID can then be used in subsequent logging throughout the request's lifecycle.

## Integrating Advanced Logging Libraries

While Go's native `log` package is sufficient for basic logging, the ecosystem offers advanced logging libraries like `logrus` and `zap`. These libraries offer structured logging, where logs are created as structured data (like JSON), making them easily parseable and more informative.

For instance, with `logrus`:

```go
import log "github.com/sirupsen/logrus"
func init() {
    log.SetFormatter(&log.JSONFormatter{})
    log.SetLevel(log.InfoLevel)
}
func fetchBookDetails(bookID int) (Book, error) {
    // ... fetch operation ...
    if err != nil {
        log.WithFields(log.Fields{
            "bookID": bookID,
            "error":  err,
        }).Error("Failed to fetch book details")
        return Book{}, err
    }
    return book, nil
}
```

This approach yields logs in JSON format, which can be ingested by modern log aggregation tools or platforms like ELK stack or Splunk.

## Error Tracing

Beyond logging, tracing allows you to follow a request's path through various microservices or internal functions. Tracing libraries like OpenTracing can be used in Go to establish spans, which represent units of work. When an error occurs, not only can you log the error, but you can also capture a trace of all operations leading up to the error. This holistic view enables developers to pinpoint bottlenecks, latency issues, or failures in the system.

As the Bookstore app grows, logs can become voluminous. Centralized log management solutions, such as Logstash or Fluentd, help aggregate, filter, and analyze logs. They offer dashboards, alerts, and insights into application behavior. When integrating such solutions, ensure that the log format (e.g., JSON) from your application matches what these tools expect. Middleware can be utilized to forward logs from the app to these management solutions.
