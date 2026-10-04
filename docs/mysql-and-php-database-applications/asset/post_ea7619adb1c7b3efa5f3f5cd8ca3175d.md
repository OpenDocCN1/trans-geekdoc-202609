
## Chapter 10
## Catalog

IN THIS CHAPTER

- Working with object-oriented code
- Looking at database schemas
- Working around MySQL limitations
- Running shell commands from within PHP

IN THE COURSE OF THIS chapter we are going to show one way of creating an on-line catalog. You'll see how to present and administer an application that presents some typical retail items. 

We, the authors of this book, feel that you are an intelligent person, as well as someone with great taste in technical literature. We also believe that you picked up this book because you want to learn as much as you can about applications development with PHP and MySQL. That's why we're not wasting any time. Each chapter introduces additional challenges, or at least presents something new and different. This chapter will be no exception.

If this chapter were to use the functions presented in the survey application in Chapter 9, there would be little new material to present. All the application would need a simple database schema, a few queries with some joins, and calls to the HTML functions in the /functions/folder.

To keep things interesting, this application uses a completely different way of organizing code. This survey makes use of object-oriented, or OO programming. However, we're not giving up on all of those functions. Some of them are just too convenient (safe_query() comes to mind).

![](img/245156cc770929860a3ede93c01f9981_277_0.png)

> Chapter 7 covers the concepts and nomenclature associated with object-oriented programming. In this chapter we assume that you read and understand that information.

## Determining the Scope and Goals of the Application

The goals we have in mind for this application are pretty modest. Imagine for a moment that you own some sort of retail establishment that has goods you wish to hawk. Further, assume that you have no interest in actually transactions over the Web. Maybe you are just paranoid about this new-fangled method of processing credit cards. Or perhaps you are running an elaborate tax-fraud scheme that requires you to deal solely in unmarked twenties.

![](img/245156cc770929860a3ede93c01f9981_278_0.png)

```
The code used in this catalogue will be re-used in the shopping cart application, where we will show how to process credit-card transactions.
```

Whatever the circumstance, all this site needs to show your wares in logical categories and breakdowns. You will hear more about the breakdown of the information when we discuss the database schema.

The chief goal of this chapter is to create code that makes the best use of the object-oriented approach. The classes must use of inheritance and encapsulation, and should make the task of writing individual scripts a whole lot easier. It's also important to think about modularity. The code created here will be reused in Chapter 14, so we want to write code in a way that it becomes easily reusable elsewhere. 

We also wanted to throw in something really cool. One day on the PHP mailing list some guy named Rasmus mentioned a set of free software utilities that run on Unix that can be used to resize and otherwise manipulate all sorts of images. The PHP scripts in this application will interface with these utilities (called PBMplus) to automatically create thumbnails of the images of the catalogue items. We think you'll have to admit that this is pretty cool.

![](img/245156cc770929860a3ede93c01f9981_278_1.png)

Rasmus Lerdorf started the language that would evolve into PHP. He is one of the core developers, an active member of the mailing list, and an effective advocate of PHP software. The history of PHP is actually pretty interesting. You have an MP3 player you can hear all about it from Rasmus and other core developers at: http://hotwired.lycos.com/webmonkey/radio/php.html.

## Chapter 10: Catalog
251

ON THE CD PBMplus can be found on the CD.

![](img/245156cc770929860a3ede93c01f9981_279_0.png)

Tip: Subscribe to the PHP mailing list. You'll learn about all sorts of groovy things you never would have guessed existed. If you are going to subscribe, be ready for the volume. The list can generate over 100 emails on a given day. Check Appendix H for a list of some of the other mailing lists.

![](img/245156cc770929860a3ede93c01f9981_279_1.png)

## Necessary Pages

The pages that display the catalogue aren't very extravagant. For navigational purposes there is a simple page that displays a list of categories. Figure 10-1 shows the category list.

![](img/245156cc770929860a3ede93c01f9981_279_2.png)

## BagO'Stuff Catalog

Here at BagO'Stuff, we've got so much stuff we don't know what to do with it. So buy some and help us clear out some space.

## What're We Got?

- T-Shirts
- Geometric Shapes

Figure 10-1: Category list page

## Part IV: Not So Simple Applications

From the list of categories, the viewer of the page will click to see a listing of products without that overwhelming. Figure 10-2 shows that rather overwhelming.

![](img/245156cc770929860a3ede93c01f9981_280_0.png)

Figure 10-2: Products list page

Finally, there is a page that lists the actual items for sale. Notice that a thumbnail of each item is shown, and alongside each item is a listing of variants of the item. In Figure 10-3, the items are t-shirts, and specific sizes are listed. Like all applications in this book, one has a series of administrative pages. Given what you have seen in the previous paragraphs and figures, it should be no surprise that the administrative pages create, delete, and alter information on the following levels: categories, products, items, and sub-items, the pages for which are shown in Figures 10-4, 10-5, and 10-6 respectively.

![](img/245156cc770929860a3ede93c01f9981_280_1.png)

Sub-items represent the specific variations of an item. Sub-items is the term that is applied to, for example, the t-shirt sizes.

 Chapter 10: Catalog

![](img/245156cc770929860a3ede93c01f9981_281_0.png)

BagO'Stuff: T-Shirts
Description The essential all-purpose item for any wardrobe.

Price: 10.00

Style Details
black Available in S, M, L
white Available in S, M, L

Figure 10-3: Items list

![](img/245156cc770929860a3ede93c01f9981_281_1.png)

## Admin: Edit Category

- Save Changes
- Delete Category
- Reset
- Add Product

Figure 10-4: Category administration page

## Part IV: Not So Simple Applications

![](img/245156cc770929860a3ede93c01f9981_282_0.png)

Figure 10-5: Products administration page

![](img/245156cc770929860a3ede93c01f9981_282_1.png)

Figure 10-6: Item and sub-item administration page

## What Do We Need to Prevent?

Unlike the survey and the guestbook, there is no user interaction in this application. To the world at large the catalog is read-only. So we don't need to be quite as concerned with bored people adding tags and scripts to our pages.

In this application there are more general concerns, the type of things that come up in every application: there are bugs, the code efficient, are our data properly, and other questions of that ilk.

## The Data

For this application, it is useful to spend a few paragraphs discussing why we did not use what might seem to be the easiest and most obvious schema.

## A flawed data design

If you were attentive reading the previous pages, you will remember the breakdown of the data. There are one or more categories, and each category will contain many products. Each product will have many styles, and each style can have a number of subtitles.

This might lead to believe that a simple hierarchical structure of our tables would work just fine. Figure 10-7 shows the one-to-many relationships that would create this hierarchical effect.

| categories | | styles | substyles |
| --- | --- | --- | --- |
| category_id description | product_id category_id product description price image_src | style_id product_id style description price image_src | subtitle_id style_id subtitle price |

Figure 10-7: Flawed catalog schema

Now consider what would happen if we were to add data to these tables. Let's take the example of t-shirts. There is a category for t-shirts, and a number of products (different clever stencils on the t-shirts) for this category. Each product will come in a number of styles (colors), and each color will come in a number of subtitles (sizes). what what data in the hierarchical table form might look like. (Note that the tables have been simplified).
