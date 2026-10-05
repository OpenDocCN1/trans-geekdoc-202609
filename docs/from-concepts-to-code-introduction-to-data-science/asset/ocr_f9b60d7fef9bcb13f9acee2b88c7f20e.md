('Bono Hewon',\n'Dublin, Ireland',
"['rock', 'pop']")

('Rihanna',
'Saint Michael, Barbados',
None)

Since we are treating hometown as the left table, we get back each record
from this table. Since Rihanna was not in the artist table, we don't have the
associated data for genre, and it appears as None.

# 7.5 Houses, Lakes, and Lake Houses

As organizations grow, the quantity of data tends to grow with it. This can be
driven by factors including more products, more teams, and more customers.
A single database often won't be sufficient. A data strategy that will support
the business should take these data requirements into account:

+   * Variety: The data may come from a variety of sources and it may have
different levels of structure. There may be a needs to collect transactional
data, which is very structured, as well as documents, images, and videos,
which are unstructured.
* Volume: There may be a massive amount of data to store and retrieve. It is
import to support these requirements at the necessary scale.
* Access: Data teams and users will have different permissions. A team
performs analytics on home equity loans might not need access to student
ent loan. A business intelligence team might need to compute analytics
across all the lines of business. An ideal system would make it easy for
an administrator to grant and monitor access.
* Catalog: It is valuable for permitted users to browse datasets at a
high level, and request access to what they need. Metadata saved with the
dasets can help users find what they need.

There may be many organizational requirements as well. Even with this
short list, however, a single database likely won't be sufficient. In response,
several objects and concrete services have emerged. A very brief overview
follows next, but bear mind that each of these topics could be their own
book. Let's start with the data warehouse.