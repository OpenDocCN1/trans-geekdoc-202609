**categories**
| category_id | category |
|---|---|
| 1 | t-shirts |
| 2 | shoes |

**products**
| product_id | product | category_id |
|---|---|---|
| 1 | Just Say Oops | 1 |
| 2 | I Love Milk | 1 |

**styles**
| style_id | style | product_id |
|---|---|---|
| 1 | blue | 1 |
| 2 | green | 1 |
| 3 | red | 2 |
| 4 | blue | 2 |

**sub-styles**
| sub-style_id | sub-style | style_id |
|---|---|---|
| 1 | S | 1 |
| 2 | M | 1 |
| 3 | L | 1 |
| 4 | XL | 1 |
| 5 | S | 2 |
| 6 | M | 2 |
| 7 | L | 2 |
| 8 | XL | 2 |
| 9 | S | 3 |

Figure 10-8: Sample hierarchical data

Take a look at the substyles table in Figure 10-8. It is already starting to get a bit messy. Even with just a couple of t-shirts there is some repeating data. As you can see, size small (S) appears several times, and as we add to the catalog, more rows will be inserted and this table will get even messier.

Thinking about the data a bit more carefully, you might notice something interesting: In the case of the t-shirts, the sizes are not dependent on the color of the t-shirts at all. If you remember back to Chapter 1, you will remember that a lack of a dependency is a bad thing. So the above data really aren't properly normalized.

In fact, the sizes in which a t-shirt is available are not dependent on the color (style table) or the phrase on the t-shirt (products table). Size is, in fact, dependent