# Collection Types

+   4.1. Values, Pointers, and Reference Types ▷ 140

+   4.2. Arrays and Slices ▷ 148

+   4.2.1. Indexing and Slicing Slices ▷ 153

+   4.2.2. Iterating Slices ▷ 154

+   4.2.3. Modifying Slices ▷ 156

+   4.2.4. Sorting and Searching Slices ▷ 160

+   4.3. Maps ▷ 164

+   4.3.1. Creating and Populating Maps ▷ 166

+   4.3.2. Map Lookups ▷ 168

+   4.3.3. Modifying Maps ▷ 169

+   4.3.4. Key-Ordered Map Iteration ▷ 170

+   4.3.5. Map Inversion ▷ 170

+   4.4. Examples ▷ 171

+   4.4.1. Example: Guess Separator ▷ 174

+   4.4.2. Example: Word Frequencies ▷ 174

This chapter's first section explains Go's values, pointers, and reference types since an understanding of these is necessary for the rest of the chapter and for subsequent chapters. Go's pointers work just like those in C and C++, both syntactically and semantically—except that Go does not support pointer arithmetic, thus eliminating a whole category of potential bugs that can affect C and C++ programs. Nor does Go free/delete since Go has a garbage collector and manages memory automatically.* Values of Go of reference types are created in a unique and simple way and once created used rather like Java or Python object references. Go's values work like those in most other mainstream languages.

This chapter's other sections are devoted to Go's built-in types. All the built-in collection types are covered—arrays, slices, and maps. These are

> * Go delete() function is used to delete keys from maps as we will see later in this chapter.