```
CREATE TABLE users (
  id INT AUTO_INCREMENT PRIMARY KEY,
  username VARCHAR(50) NOT NULL,
  email VARCHAR(50) NOT NULL,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

+   - Relationship Formation: Forging connections between tables using foreign keys is integral to preserving data consistency and enabling efficient data queries.

# Interacting with Data

With the database and its schema established, inserting and querying data become the core interactions that facilitate dynamic communication between the application and the database.

+   - Inserting Data: New records can be added to the tables using the `INSERT INTO` command.

```
INSERT INTO users (username, email) VALUES ('john_doe', 'john@example.com');
```

+   - Querying Data: The `SELECT` statement allows for the extraction of data from the database, with various clauses available to filter, order, and aggregate the data for precise query results.