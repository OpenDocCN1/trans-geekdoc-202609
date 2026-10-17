
| `Pair` || indexed collection that holds two values |

These types handle common ways in which we have to deal with lists, but they take the weight off us to implement them as you would in PHP. To create a new collection you would define something like:

```
$vector = Vector {1, 2};
$vector->add(3);
// Vector(1, 2, 3)
```

For compatibility, you can still use arrays just as you would in PHP, but you can also make it more specific. The type of an array can be defined in terms of both its value and its key/index.

The key and value are simply defined:

```
array<int, string>
```

Where the array has an integer key and the value is a string, if you just want to specify the type of the value and not the key use:

```
array<string>
```

This allows the array to be type checked by the parser and stops the list from becoming a grab bag of values. When you operate on a list you want to be able to treat all the values in the same way with as little difficulty as possible. By specifying the type signature like this you can be assured that you will always get a string (or the type you specify).

```
class HackArray {
   public array<int, string> $array = [
      1 => 'ibizo',
      2 => 'umuntu',
      3 => 'inja',
   ];
}
```

Should you desire to have an immutable array then Hack makes this possible through the use of a `tuple` that can be defined as:

```
$t = tuple(1, 2, 3);
$sum = array_sum($t); // 6
```

As an immutable type once the `tuple` is defined it cannot be changed and it would result in an error to do so.

These arrays serve as a simple collection or the basics of more custom application targeted collection classes. If you need a collection such as `Set` then it is better to use the `Set` collection Hack provides than write your own. This is for two reasons, both primarily being efficiency; it is an easily recognizable structure to any Hack programmer and as it is part of the language it is optimized by default.

In addition to collections and arrays, Hack also defines other useful types such as `Enum`, `Generic`, `Shape`. In the case of `Enum` you can define an enumeration type which allows only a value specified with in the definition to be assigned to any variable. This is demonstrated as a blog post publication state in Listing 5.1.

**Listing 5.1**

```
enum BlogPostState: int {
   Published = 1;
   Queued = 0;
   Draft = -1;
}

class BlogPost {
   public BlogPostState $state = BlogPostState::Published;
   public function getState(): BlogPostState {
      return $this->state;
   }
}
```

There are numerous uses for `Enum` type and it gives you a very simple storage mechanism for when Booleans are simply not enough.

Slightly less exciting is the addition of a `nullable` type hint for function parameters in the form of prepending them with a question mark (`?`). This allows you to indicate what parameters can accept a `null` value when defining a function. Generally, it would not feature heavily in functional code as it allows a `null` to be passed in where the application would be expecting solid type.

```
function spit(?string $rhyme) {
   return (string) $rhyme;
}
```

You could now call the `spit()` function with a parameter of `null` instead of the specified `string` and it would parse this without complaint.

```
$r1 = spit('Ibizo');
$r2 = spit(null);
```

### Type Aliasing

Hack allows developers to alias internal types to new more specific names which can be used for more accurate type checking when dealing with function parameters and annotations. Sometimes this can be very useful, especially when dealing with strings. What are strings? Well they could be a date, a URL, an ISBN, a phone number or some other structured string it would be helpful to type, so they can be handled slightly differently.

```
type PhoneNumber = string;
```

Once the type is aliased it can then be used in normal type hinting situations like function arguments and return types.

```
$phoneNumber = '+44.790 000 0000';
function removePhoneNumberFormatting(PhoneNumber $pn) {
   return str_replace(
      ['+', '.', ' '], 
      ['00', '', ''],
      $pn
   );
}
$dialable = removePhoneNumberFormatting($phoneNumber);
```

This is what Hack calls a type alias, but it also supports opaque type aliasing which is a more guarded version of the aliasing we have already seen. It hides the underlying type meaning which in strict mode it would not be able to be manipulated as a `string` in the case of the phone number above.

One small caveat is in the file that `newtype` is declared you can use the type/value as if it were the underlying type. In the case of a string you could concatenate it in the originating file, but in any other file also using the type you would not be able to. If you have a file called `types.php` declaring an alias using the `newtype` keyword and subsequently a `blog_post.php` file using the type as in the example below, you would not be able to manipulate the URL slug from within `blog_post.php` as if it were string.

I have yet to find a use for the `newtype` keyword as I have always wanted access to the underlying implementation and it seems to be akin to using `private` methods when writing code in a library class. It makes the code more difficult to use and adds little to no benefit in most situations. That is until you combine it with the `as` keyword; now you have what a plain `newtype` always should have been! A new type which cannot be type checked to its underlying type, but can be used with the underlying types operators. In the case of a new type based upon an integer this would mean you would then have access to the arithmetic operators such as `+`, `*`, `/` and `-` amongst others. Unlike `newtype` you now actually have a usable type!

**Listing 5.2**

```
// in `types.php`
newtype PostId as int = int;

function getPostId(int $id): PostId {
   return $id;
}

// in `blog_post.php`
function validateId(PostId $id): bool {
   return ($id > 1);
}

function main(): void {
   $id = getPostId(10);
   validateId($id); // true
}
```

There are a few items of note in Listing 5.2 beginning with the use of a function (`getPostId()`) to obtain a value of type `PostId` from an `int`. The function accepts an `int`, but its return type is specified as `PostId` and this is enough to convince Hack any integer value passed through it is now a `PostId`.

In the `validateId()` function a comparison operator is used to check that the `PostId` is greater than one. This comparison operator would not work without the `as` keyword section in the original `newtype` definition.

This is also the first time we have seen the `main()` function in use with Hack. This is the default function the type checker bootstrap process will call when the project is built. Any top level code should go into this function or the Hack type checker will throw an error stating only `require` requests are allowable at the top level. Note a new type of `void` has been specified as the return type of this function as well. This means no value will be returned by the function in question.

Now let’s break something! The type checker will get upset if you try to treat a Boolean return value as a `PostId` as shown below. It will not allow you to effectively convert a Boolean value to a `PostId` (an `int` underneath).

Now we have a type which is usable with operators, but cannot be treated as its underlying type when type checking. This prevents an `integer` value from incorrectly being evaluated as a `PostId`.

### Generics

Hack also allows the definition of generics which allow you to approach your work in a way previously impossible with PHP. You can define a data agnostic handling class which will be typed via inference at the point it is used—much like the `Vector` we reviewed earlier.
