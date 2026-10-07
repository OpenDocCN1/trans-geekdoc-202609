# Listing 3.29

```
// Append a new user to the collection. Use the pointer again
// to update likes.

users = append(users, user())
ptrUsr0.likes++

for i := range users {
    fmt.Printf("User: %d Likes: %d\n", i, users[i].likes)
}

Output:
User: 0 Likes: 1
User: 1 Likes: 0
```

However, since the append function replaced the backing array with a new one, the pointer is updating the old backing array and the likes are lost. The output shows the likes for the first user did not increase.

# Figure 3.13

![](bbox=[0.125, 0.386, 0.875, 0.56])

I have to be careful to know if a slice is going to be used in an append operation during the course of a running program. How I share the slice needs to be considered. Sharing individual indexes may not be the best idea. Sharing an entire slice value may not work when appending is in operation. Probably using a slice as a field in a struct, and sharing the struct value is a better way to go.

# 3.20 Linear Traversal Efficiency

The beauty of a slice is its ability to allow for performing linear traversals that are mechanically sympathetic while sharing data using value semantics to minimize heap allocations.