can appear before or after the array name:

```
```java
int grades []; //an array called grades of integers
int [] grades; //grades array of integers
```
```

After deciding where you want to place the square brackets (most often, the first example is used), you need to specify the size of the array, as it is a static data structure.

# Declaration:

```
```java
int grades []=new int [5]; //grades array can store maximum 5
//elements
```
```

If the array is of integer or double or float type, and there is no further initialization of the array elements, Java automatically initializes all its elements to 0.

# Initialization:

```
```java
grades [0]=75;
grades [1]=64;
grades [2]=95;
grades [3]=50;
grades [4]=34;
```
```

At this point, the elements of the array are given specific values, the value 0 being overwritten. Another way to declare and initialize the array is like this:

```
```java
int grades []= new int [] {75,64,95,50,34};
```
```

But this can also be rewritten in a simpler way, like this:

```
```java
int grades []={75, 64, 95, 50, 34};
```
```

Sometimes, the developer will have to allow the user to initialize the array. In such cases, you can simply declare the array and use a loop to allow the user to populate the array.

```
```java
read = new Scanner(System.in);
int grades []=new int [5];
for(int i=0;i<5;i++) {
System.out.printIn("Enter a number: ");
int value = read.nextInt ();
grades [i]=value;
}
```
```

The loop repeats five times, and it requires the user to enter an integer value that will be stored into the array indicated by index i (from 0 to 4).