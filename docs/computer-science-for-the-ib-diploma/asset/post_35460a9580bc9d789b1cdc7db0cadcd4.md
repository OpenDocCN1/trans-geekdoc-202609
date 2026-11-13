

> Set subset: a set where all elements of this set are also elements of another set, indicating that the first set is entirely contained within the second set.

## Check whether subset or superset

A subset or superset describes the relationship between two sets.

Set A is considered a subset of B if all of A’s elements are present in B – which would be considered the superset. All elements of the subset can be found in the superset.

To check whether set A is a subset of set B, or whether B is a superset of A:

```
# Define two new sets
A = {1, 4, 7}
B = {1, 2, 3, 4, 5, 6, 7}
# Check if A is a subset of B
# Both of these methods are acceptable
print(A.issubset(B)) # True
print(A <= B) # True

# Check if B is a superset of A
# Both of these methods are acceptable
print(B.issuperset(A)) # True
print(B >= A) # True
```

```
// Define two new sets
Set<Integer> A = new HashSet<>();
A.add(1);
A.add(4);
A.add(7);
Set<Integer> B = new HashSet<>();
B.add(1);
B.add(2);
B.add(3);
B.add(4);
B.add(5);
B.add(6);
B.add(7);
// Check if A is a subset of B
System.out.println(B.containsAll(A)); // True
// Check if B is a superset of A by checking if A is contained within B, but B
// is not contained within A
System.out.println(B.containsAll(A) && !A.containsAll(B)); // False
```

## B4.1.6 Core principles of abstract data types

## Hash tables

Hash tables are a particularly important data structure in Computer Science. They offer rapid retrieval and insertion capabilities into an array-like structure. However, rather than an abstract integer being used by the programmer for the index, a key can be provided instead.

Hashing algorithm: a function that converts input data of any size into a fixed-size string of characters, which typically represents the data in a compressed and seemingly random format and is used primarily for indexing and retrieving items in databases more efficiently.

O(1) time complexity: describes an algorithm that takes the same amount of time to execute regardless of the size of the input data set.

ASCII (American Standard Code for Information Interchange): a character-encoding standard used to represent text in computers and other devices, defining a numerical value for each symbol and character commonly used in the English language.

This key is then processed through a hashing algorithm to find which array index to store the data in. This allows the data to be stored in an array-like structure that provides an O(1) average-time complexity for search, insert and delete operations under ideal conditions.

For example, "name" could be used as the key by the developer. A hashing algorithm then processes this with the aim of producing an integer so that where the data this key is linked to can be stored in the array. One example method where this could be achieved is by adding up the ASCII values of all the letters and then using modulus and the size of the table to determine the index.

```
# Hash table size
table_size = 10
# ASCII values for letters
'n' = 110
'a' = 97
'm' = 109
'e' = 101
110 + 97 + 109 + 101 = 417
417 % table_size = 7
```

This data would then be stored at index 7.

## Hash tables: Creating, inserting and retrieving data

This is how we can create a hash table, as well as insert, delete and retrieve items:

```
Python
# Creating a hash table as a Python dictionary
hash_table = {}
# Inserting two items
hash_table["key1"] = "value1"
hash_table["key2"] = "value2"
# Retrieving and printing one item
value = hash_table["key1"]
print("The value for 'key1' is:", value)
# Deleting an item
del hash_table["key2"]
```

```
Java
import java.util.HashMap;

public class Main {
  public static void main(String[] args) {
    // Creating a hash table using HashMap
    // The first data type is for the key, the second is for the data
    HashMap<String, String> hashTable = new HashMap<>();
    // Inserting two items
    hashTable.put("key1", "value1");
    hashTable.put("key2", "value2");
  }
}
```

```
// Retrieving and printing one item
String value = hashTable.get("key1");
System.out.println("The value for 'key1' is: " + value);
// Deleting an item by key
String removedValue = hashTable.remove("key2"); // Returns the value
// associated with the key
```

## Collision factors

As you may have already guessed, the hashing algorithm demonstrated above is not foolproof. There could be other example keys that also generate the number 7 for the index – when this happens it is called a “collision”. Ideally, our hashing algorithm should generate a unique index for each key and, while there are some more complex algorithms than the one we looked at that are better at doing this, there is no complete solution available. We cannot store two data items in an array at the same index, so how do we get around this problem? There are two main methods used: “chaining” and “open addressing”. Before we look at these methods, it is important to understand the impact of the number of items we are trying to store in the hash table. This is called the “load factor”.

## Load factors

The load factor is a measure that indicates how full the hash table is. The load factor is defined as the ratio of the number of elements currently stored in the table to the total number of slots available. The formula for load factor is:
Load factor = \frac{number of entries in the table}{total number of slots}

The load factor can heavily affect the performance of the hash table. A hash table with a high load factor will have more collisions, which will impact performance when performing operations on the table.

![](img/7f4ba44df9c5a19373dcc3ecd776c43a_486_0.png)

## Rehashing

When the load factor exceeds a certain threshold, rehashing is necessary to maintain efficient performance. Rehashing involves creating a new, larger array and redistributing the existing elements using a new hash function or the same hash function applied to the new array size. This process reduces the load factor and minimizes collisions, ensuring that the hash table operations remain efficient.

![](img/7f4ba44df9c5a19373dcc3ecd776c43a_486_1.png)

- Steps involved in rehashing:
  1. Monitor the load factor of the hash table and, when this exceeds 0.7 (70 per cent), trigger rehashing.
  2. Prepare a new array that is at least double the size of the current array. Ideally, the new size should be a prime number to help reduce collisions.
  3. For each element already in the hash table, all new hash values need to be computed based on the new array size.
  4. Insert the elements into the new, larger array, ensuring that any collisions are handled appropriately.

- Hash table chaining: a collision-resolution technique in hash tables where each bucket or index in the array can store multiple elements in the form of a linked list, allowing more than one entry to be stored at the same index.
- High load factors (hash tables): a condition where a sizeable portion of the hash table's slots are filled, leading to increased collisions and potentially degraded performance, due to more frequent need for collision resolution mechanisms.
- Open addressing: a collision resolution method in hash tables where, instead of using structures like linked lists to store multiple items at the same index, any colliding item is placed into the next available open slot in the hash table itself, according to a probing sequence.

## Chaining

Chaining utilizes linked lists (or a similar structure) to be able to store more than one item of data at a single index. When a collision occurs, and two keys hash to the same index, the new key-value pair is added to the end of the list at that index.

Let us consider a simple hash function as "key mod 6" and a sequence of keys as 35, 800, 82, 92, 122 and 94.

### Empty table
| Index | Value |
|---|---|
| 0 | |
| 1 | |
| 2 | |
| 3 | |
| 4 | |
| 5 | |

### Insert 35
| Index | Value |
|---|---|
| 0 | |
| 1 | |
| 2 | |
| 3 | |
| 4 | |
| 5 | 35 |

### Insert 800 and 82
| Index | Value |
|---|---|
| 0 | |
| 1 | |
| 2 | 800 |
| 3 | |
| 4 | 82 |
| 5 | 35 |

### Insert 122: Collision, so it is added to a chain
| Index | Value |
|---|---|
| 0 | |
| 1 | |
| 2 | 800 92 122 |
| 3 | |
| 4 | |
| 5 | 35 |

### Insert 94: Collision, so it is added to a chain
| Index | Value |
|---|---|
| 0 | |
| 1 | |
| 2 | 800 92 122 |
| 3 | |
| 4 | 82 94 |
| 5 | 35 |

## Advantages:

- **Simplicity**: It is relatively easy to implement.
- **Handles high load factors well**: If the number of items you are inserting is greater than the amount of spaces in the table, it will still operate efficiently. However, lookup times may become slower when having to access a linked list.
- **Good for unknown data sizes (connected to the point above)**: If you do not know in advance how many items you will be inserting into the table, chaining will have an advantage as you will not need to rehash the table to resize it.

## Disadvantages:

- **Memory overhead**: As it is utilizing a linked list, the more items there are in the chain, the more memory it will require.
- **Complexity for deletion**: If the deletion is within a linked list, performance will degrade due to the need to adjust pointers.
- **Variable performance**: When accessing an index with a linked list, this will perform worse than one without, which can impact search and delete actions.

## Open addressing

Open addressing only stores data within the hash table itself. When a collision occurs, it will find another empty slot in the hash table, according to a predefined sequence, and store the data there.

Several methods can be used to achieve this:

- **Linear probing** sequentially checks the next spot until a space is found. However, this can lead to clustering, where a group of adjacent slots get filled, increasing the search time for these elements in particular.

