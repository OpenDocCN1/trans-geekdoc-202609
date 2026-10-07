# Figure 11.4

![](bbox=[0.105, 0.091, 0.875, 0.545])

The call graph makes it clear that the call to strings.ToLower is causing all the allocations.

# 11.6 Removing Allocations

Knowing this, I need to find a way to remove the call to strings.ToLower.

# Listing 11.20

```
118 for i, item := range d.Channel.Items {
119     if strings.Contains(strings.ToLower(item.Description), 
120         strings.ToLower(term)) {
121         results = append(results, Result{
122             Engine: engine,
123             Title: item.Title,
124             Link: item.Link,
125             Content: item.Description,
126         }))
127     }
128 }
```

On closer inspection there are two things I can do.