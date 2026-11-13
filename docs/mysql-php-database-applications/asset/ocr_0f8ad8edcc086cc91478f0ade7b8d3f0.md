Instead, product_style_map has only the minimal number of records needed to represent your actual stock. If there's a standard set of colors for all shirts, you can just map Shirts to Colors. That way when you add a new color it automatically shows up as available for all your shirts. If you don't want the color to apply to plain V-neck T-shirts you can go to that product and mark it "not available" there.

As you'll see, this puts the onus on the application code to interpret the data correctly. You can take an alternate approach to this kind of data that can make coding a bit simpler, but that carries a correspondingly increased risk of inaccurate information showing up on your Web pages. You can add another table to the database – something like derived_product_style_map, for example, that never gets directly updated by the administrators of the site. Instead, the application rebuilds it every time the main tables change. You can think of this kind of table as something like a cache – it stores the results of applying all the varying hierarchies of styles to all of the products, and ends up looking like the very simple mapping table described earlier. The advantage of this approach is probably clear: All the work has been done, and all the Web site has to do is go read the database. The disadvantage is in the process of building it. If anything goes wrong in that process, you end up displaying different information on the site than you see in your administration screens, which is the kind of thing that drives site administrators nuts. Plus, while you're rebuilding it, what do your pages show? There are ways to solve those problems, of course. It's a perfectly legitimate approach to take.

> The thing is, every problem we had to solve in our example, which displays pages directly from the source products and styles tables, is one you'd have to solve to create those kinds of derived tables anyway. So if it sounds like a good approach, consider it left as an exercise for you.

The code in Listing 12-1 shows how the Catalog application's database tables are set up. Pay attention to the datatypes – they restrict what we can do later.

# Listing 12-1: create Statements for the Catalog Application

```
# ----------------------------------
create table products
(
    product_id          integer not null auto_increment
,   parent_id           integer not null default 0
,   product             varchar(255) not null
,   description         text null
,   price               decimal(10,2) null
,   price_type_id       smallint null
```