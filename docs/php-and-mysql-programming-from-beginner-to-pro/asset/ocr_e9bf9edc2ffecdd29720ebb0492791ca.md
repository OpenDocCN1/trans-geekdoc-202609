+   • Horizontal Segmentation (Sharding): This technique divides a database table row-wise, with each segment containing a portion of the rows. This method can significantly boost query efficiency by minimizing the data scanned during query execution.

+   • Vertical Segmentation: This approach splits a table column-wise, with each segment holding a subset of the columns, beneficial when certain columns are accessed more frequently.

```
-- Illustration of sharding key usage in SQL
CREATE TABLE user_profiles (
    user_id INT AUTO_INCREMENT,
    shard_key INT,
    username VARCHAR(100),
    PRIMARY KEY (user_id)
);
```

# Replication of Data

Replicating data involves creating data copies across different nodes or locations to enhance availability and fault tolerance. Various replication strategies include: