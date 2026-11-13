+   * **No pointers:** There are no pointers available in PHP, although the typeless variables play a similar role. PHP does support variable references. You can also emulate function pointers to some extent, in that function names can be stored in variables and called by using the variable rather than a literal name.

+   * **No prototypes:** Functions do not need to be declared before their implementation is defined, as long as the function definition can be found somewhere in the current code file or included files.

+   * **Memory management:** The PHP engine is effectively a garbage-collected environment (reference-counted), and in small scripts there is no need to do any deallocation. You should freely allocate new structures - such as new strings and object instances. IN PHP5, it is possible to define destructors for objects, but there is no free or delete. Destructors are called when the last reference to an object goes away, before the memory is reclaimed.

+   * **Compilation and linking:** There is no separate compilation step for PHP scripts.

+   * **Permissiveness:** As a general matter, PHP is more forgiving than C (especially in its type system) and so will let you get away with new kinds of mistakes. Unexpected results are more common than errors.