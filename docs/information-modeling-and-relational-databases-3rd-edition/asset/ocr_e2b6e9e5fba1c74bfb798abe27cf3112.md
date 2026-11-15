As the second phase of reengineering, use the conceptual optimization procedure to transform the conceptual schema into one that Rmaps to a more efficient relational schema. Compare your solution with Fig. 14.80. The specialization of the chairperson and diagram predicates into functional binaries is straightforward.

![](bbox=[0.18, 0.19, 0.85, 0.7])

+   *Each AcceptedPaper is a Paper that has Status 'accept'.
+   *Each LabOrLecRoom is a Room that is of RoomType in {'lab', 'lec'}.
+   *Each Lab is a Room that is of RoomType 'lab'.
+   *Each LecRoom is a Room that is of RoomType 'lec'.
+   *Each AcceptedAuthoring is a (Person authors AcceptedPaper).

# FIG. 14.80 The optimized conceptual schema.

In nesting the referee and author predicates, we could instead have united these exclusive but compatible predicates. Although this alternative move would lead to one less table, nesting these exclusive predicates would detract from the readability and lead to awkward constraint patterns.