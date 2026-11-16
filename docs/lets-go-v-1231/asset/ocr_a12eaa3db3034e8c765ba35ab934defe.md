In this file let's create a newTestDB() helper function which:

+   * Creates a new *sql.DB connection pool for the test database;
+   * Executes the setup.sql script to create the database tables and dummy data;
+   * Register a ‘cleanup’ function which executes the teardown.sql script and closes the connection pool.