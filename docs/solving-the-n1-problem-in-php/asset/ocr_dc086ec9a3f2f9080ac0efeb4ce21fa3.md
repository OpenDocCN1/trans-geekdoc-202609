(There is no need to return $posts since $posts was passed by reference.)

The presentation logic can then become something more like this:

/path/to/templates/show_$posts.php

```
<?php
$comments_mapper->fetchCommentsIntoPosts($posts);
foreach ($posts as $post) {
    // display the post, and then
    foreach ($post->comments as $comment) {
        // display each comment
    }
}
?
```

With this, we have removed the N+1 problem. However, we still have layer-separation issues. As a further refactoring, we would probably want to unify the query-and-stitch logic in the domain layer and build the collection of Post entities in a better-separated way.

# Test, Commit, Push, Notify QA

After making our changes, we need to make sure the application still works. We do this by running our pre-existing unit or characterization tests. If we do not have tests in place, we must browse to or otherwise invoke the changed code.

If these tests fail, we rejoice! We have discovered that the refactoring has errors. We now have a chance to fix them before we deploy to production.

If the tests pass, we likewise rejoice. We can now commit all of our new work and push it to the central repository. Then we can notify the QA team that our better-performing code is ready for them to review.

# Do ... While

Once we have solved that occurrence of one N+1 problem, we can start over again and look for remaining ones, and apply the process again.