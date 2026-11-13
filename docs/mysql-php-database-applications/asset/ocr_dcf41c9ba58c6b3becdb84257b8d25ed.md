| topic_id | topic_date | topic_author | topic_subject | topic_text |
|---|---|---|---|---|
| 1 | 08/20/2003 | Ellen | Re: Snacks Rule | You betcha |
| 2 | 08/20/2003 | Erners | Re: Snacks Rule | Indeed |

Now we move away from this ill-considered idea and move toward a more sound plan. Think about what information needs to be stored for each post to the mailing list. Start with the obvious stuff. You need a column that stores the subject of the thread (for example, “Nachos, food of the gods”), one that stores the author’s name, and one that records the date the item was posted. So the table starts with these columns–we’ve thrown in some sample information in Table 10–3 and an auto_increment primary key just to keep it clear.

| topic_id | subject | author | date |
|---|---|---|---|
| 1 | Nachos rule | Jay | 3/12/2003 |
| 2 | Cheetos are the best | Brad | 3/12/2003 |

But of course this isn’t enough. Somehow you need a way to track the ancestry and lineage of any specific topic. (Look again at Figure 10–1 if you are not sure what we mean.) So how are you going to do this? If you are looking to track the ancestry of any particular thread, it probably makes sense to add a field that indicates the topic that started the thread–the root topic.

Take a close look at Table 10-4. Start with the first row. Here the root_id (1) matches the same as the topic_id. Now look at the third row. Here the root_id matches the topic_id of the first row. So you know that the thread to which row 3 belongs started with topic_id 1–“Nachos rule.” Similarly, row 6 must be a reply to row 2.

Now look at rows 1, 2, and 5. Notice that in these rows the topic_id and the root_id are identical. At this point you can probably guess that whenever these two are the same, it indicates a root-level topic. Easy enough, right? The following SQL statement retrieves all the root-level topics:

```
select * from topics where root_id=topic_id.
```